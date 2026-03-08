<!DOCTYPE html>
<html>
<head>
<title>SPL 5 Auction</title>

<style>
body{font-family:Arial;background:#f2f2f2;text-align:center;}
button{padding:10px 15px;margin:5px;font-size:16px;}
table{margin:auto;border-collapse:collapse;background:white;}
td,th{border:1px solid black;padding:8px;}
</style>

</head>

<body>

<h1>SPL 5 Auction</h1>

<h2 id="player"></h2>

<p>Base Price: 20</p>

<p>Current Bid: <span id="bid">20</span></p>

<p>Team: <span id="team">None</span></p>

<button onclick="bid('Aneek')">Aneek Bid</button>
<button onclick="bid('Aamir')">Aamir Bid</button>
<button onclick="bid('Ayan')">Ayan Bid</button>
<button onclick="bid('Sufiyan')">Sufiyan Bid</button>

<br><br>

<button onclick="sold()">SOLD</button>
<button onclick="unsold()">UNSOLD</button>

<h2>Team Purse</h2>

<table>
<tr><th>Team</th><th>Points</th></tr>

<tr><td>Aneek</td><td id="p1">1500</td></tr>
<tr><td>Aamir</td><td id="p2">1500</td></tr>
<tr><td>Ayan</td><td id="p3">1500</td></tr>
<tr><td>Sufiyan</td><td id="p4">1500</td></tr>

</table>

<h2>Sold Players</h2>

<table id="soldTable">

<tr>
<th>Player</th>
<th>Team</th>
<th>Price</th>
</tr>

</table>

<script>

let players=[

"Atahar","Divyang","Rehan H","Jaadubhai","Navedbhai",
"Rayan","Jiyan","Rehan K","Aman S","Prathmesh",
"Hamza","Akil","Arhan","Naeem","Muhmmad",
"Al bax","Prince","Aaditya","Saan","Sohan",
"Hasim Raj","Zaki","Sejan","Muin","Arsh",
"Jigar","Prateej","Sohan D","Aman R"

]

let unsoldPlayers=[]

let purse={
"Aneek":1500,
"Aamir":1500,
"Ayan":1500,
"Sufiyan":1500
}

let currentPlayer=""
let bidPrice=20
let team="None"

function randomPlayer(){

if(players.length==0){

if(unsoldPlayers.length>0){

players=[...unsoldPlayers]
unsoldPlayers=[]

}else{

document.getElementById("player").innerHTML="Auction Finished"
return

}

}

let index=Math.floor(Math.random()*players.length)

currentPlayer=players.splice(index,1)[0]

bidPrice=20
team="None"

document.getElementById("player").innerHTML=currentPlayer
document.getElementById("bid").innerHTML=20
document.getElementById("team").innerHTML="None"

}

function bid(t){

if(team=="None"){
bidPrice=20
}else{
bidPrice+=10
}

team=t

document.getElementById("bid").innerHTML=bidPrice
document.getElementById("team").innerHTML=team

}

function sold(){

if(team=="None") return

purse[team]-=bidPrice

document.getElementById("p1").innerHTML=purse["Aneek"]
document.getElementById("p2").innerHTML=purse["Aamir"]
document.getElementById("p3").innerHTML=purse["Ayan"]
document.getElementById("p4").innerHTML=purse["Sufiyan"]

let table=document.getElementById("soldTable")

let row=table.insertRow()

row.insertCell(0).innerHTML=currentPlayer
row.insertCell(1).innerHTML=team
row.insertCell(2).innerHTML=bidPrice

randomPlayer()

}

function unsold(){

unsoldPlayers.push(currentPlayer)

randomPlayer()

}

randomPlayer()

</script>

</body>
</html>
