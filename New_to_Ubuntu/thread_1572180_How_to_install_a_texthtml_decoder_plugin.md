---
title: "How to install a text/html decoder plugin"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by lord_moa@yahoo.ca on 2010-09-10
Hi!

I tried to listen to a radio station in Israel called Arutz Sheva, and when I typed in
the URL of the radio station through the Ubuntu music player, I got a pop up
that said that the text/html decoder was not installed.  The URL of the radio station
 is [http://www.inn.co.il/Radio/Player.htm](http://www.inn.co.il/Radio/Player.htm)    How do I go about doing that? Thanks!

Lyle

---

### Post by bodhi.zazen on 2010-09-10
I can not read that site, you have to use a url that matches the stream.

For example :

On this page :

[http://www.hbr1.com/perl/apax.cgi?Part=Playlist](http://www.hbr1.com/perl/apax.cgi?Part=Playlist)

Select 

[http://www.hbr1.com/playlist/ambient.pls](http://www.hbr1.com/playlist/ambient.pls)

and not [http://www.hbr1.com/perl/apax.cgi?Part=Playlist](http://www.hbr1.com/perl/apax.cgi?Part=Playlist)

---

### Post by lord_moa@yahoo.ca on 2010-09-29
HERE IS ARUTZ SHEVA'S CODE OF RUNNING THE STATION, TOTEM SEEMS TO NEVER BE ABLE TO PLAY IT WITH THEIR KNOWN PLUGINS....

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  <html dir=rtl xmlns="http://www.w3.org/1999/xhtml"> <head>     <script>sStaticURL="http://a7.org/";</script> <script src="[http://a7.org/Combine.ashx?js=JQuery.js,Main.js,Dates.js,ga.js,Player.js&css=Global.css&h=player]("http://ubuntuforums.org/view-source:http://a7.org/Combine.ashx?js=JQuery.js,Main.js,Dates.js,ga.js,Player.js&css=Global.css&h=player")"></script> <title>&#1506;&#1512;&#1493;&#1509; 7 &#1512;&#1491;&#1497;&#1493;</title> <meta  http-equiv=Content-Type content="text/html; charset=windows-1255" /> </head> <style> body {background-color:black;width: 377px} #divMain {padding-top:79px;width: 377px; background:black url([http://a7.org/images/radio/bg.png](http://a7.org/images/radio/bg.png)) no-repeat scroll top right} #divPlayer {margin: 0px 39px;width:300px} #divVidTitle0 {height:34px;margin:0px 53px} .VVideoT  {display:none} .GenericWindow {border-color:#c00;} .GenericWindow  .Ttl {background-image:url(http://a7.org/images/special/child/menu2bg.gif)} .X:hover {background-color: #c00}  #divListContent { max-height: 300px; overflow-y:auto}  #DTabs {margin: 0px 20px; } .DTabsL {text-align:left;color:White} #DTabs a {color:White; text-decoration: underline} .CTabs {margin-top:26px;height:26px} .TabsContent {height:170px;overflow-y:scroll;border-color:black;position: relative; border-bottom:1px solid #B6BBBE } .TabContent {background-color: Transparent; position: absolute; top: 0px;width:318px } .CTabs #tab {background-color: transparent; color: White; border-width:0px} #tab span {background: transparent none;padding:0px;margin:0px; border-width: 0px; color: White } #tab.selected span {background: #c00 none;} .CTabs .tab01,.CTabs .tab02 {display:none} #tab .tabcontent {padding: 2px 5px}  .Live {color:White; color:#eee; padding:15px} .Live strong {display:block; color:#524f4f; font-weight: normal ;margin-bottom:10px; font-size:30pt}  .Item  {height:74px;padding:6px; color: White;  background: transparent url([http://a7.org/images/radio/bgc.jpg](http://a7.org/images/radio/bgc.jpg)) black repeat-x left top } .Item img {float:right;height:70px; cursor: pointer;margin-left:7px} .Item .Content {height:34px; cursor: pointer;} .Item  strong {display:block;  cursor: pointer;font-weight:bold; color:#c00;} .Item .Buttons span { cursor: pointer;background-repeat: no-repeat;margin-right:2px; background-image:url([http://a7.org/images/radio/red.png);width:18px;height:18px;float:right;](http://a7.org/images/radio/red.png);width:18px;height:18px;float:right;) cursor: pointer}  #divTInf {font-size:8pt;margin-right:15px;} #divTInf img {display:none} #divTInf a {color:White; text-decoration: underline} #divInf948  {height:40px; overflow:hidden; margin-top:10px} #divInf948 iframe,#divInf948 object, #divInf948 embed, #divInf948 img {width:340px;height:45px} </style> <body>  <div id=divMain> <div id=divVidTitle0></div> <div id=divPlayer>  </div> <div id=DTabs> <script> var oTabs = Tabs.CreateTwoTabs(["",""],["<span onclick=oPlayer.SetVideo(Live)>&#1513;&#1497;&#1491;&#1493;&#1512; &#1495;&#1497;</span>","<div class=Live><strong>&#1513;&#1497;&#1491;&#1493;&#1512; &#1495;&#1497;</strong>&#1506;&#1512;&#1493;&#1509; 7 &#1502;&#1513;&#1491;&#1512; 24 &#1513;&#1506;&#1493;&#1514; &#1489;&#1497;&#1502;&#1502;&#1492; &#1513;&#1497;&#1512;&#1497;&#1501; &#1488;&#1492;&#1493;&#1489;&#1497;&#1501; &#1502;&#1499;&#1500; &#1492;&#1505;&#1493;&#1490;&#1497;&#1501;, &#1514;&#1499;&#1504;&#1497;&#1493;&#1514; &#1508;&#1504;&#1488;&#1497; &#1493;&#1488;&#1511;&#1496;&#1493;&#1488;&#1500;&#1497;&#1492; &#1493;&#1497;&#1493;&#1502;&#1503; &#1495;&#1491;&#1513;&#1493;&#1514; &#1502;&#1491;&#1497; &#1497;&#1493;&#1501; &#1495;&#1493;&#1500; &#1489;&#1513;&#1506;&#1492; 13:00.<br>&#1504;&#1497;&#1514;&#1503; &#1500;&#1492;&#1488;&#1494;&#1497;&#1503; &#1500;&#1506;&#1512;&#1493;&#1509; 7 &#1489;&#1513;&#1497;&#1491;&#1493;&#1512; &#1495;&#1497; &#1490;&#1501; &#1489;&#1496;&#1500;&#1508;&#1493;&#1503; 050-8888888</div><div id=divTInf></div>"],["&#1514;&#1493;&#1499;&#1504;&#1497;&#1493;&#1514; &#1512;&#1491;&#1497;&#1493;","<div id=divIn0></div>"],["&#1514;&#1497;&#1489;&#1514; &#1504;&#1490;&#1497;&#1504;&#1492;","<div id=divIn1></div>"]) </script> <div class=DTabsL> <a href=[/Radio/]("http://ubuntuforums.org/view-source:http://www.inn.co.il/Radio/")>&#1514;&#1493;&#1499;&#1504;&#1497;&#1493;&#1514; &#1502;&#1493;&#1511;&#1500;&#1496;&#1493;&#1514;</a> | <a href=[/Radio/Jukebox.aspx]("http://ubuntuforums.org/view-source:http://www.inn.co.il/Radio/Jukebox.aspx")>&#1514;&#1497;&#1489;&#1514; &#1504;&#1490;&#1497;&#1504;&#1492;</a> | <a href=[/Radio/Parade.aspx]("http://ubuntuforums.org/view-source:http://www.inn.co.il/Radio/Parade.aspx")>&#1502;&#1510;&#1506;&#1491; &#1495;&#1505;&#1497;&#1491;&#1497;</a> </div> <div id=divInf948></div> </div> <script> var aJukeboxCats= ["&#1506;&#1489;&#1512;&#1497;", "&#1495;&#1505;&#1497;&#1491;&#1497;", "&#1502;&#1494;&#1512;&#1495;&#1497;", "&#1495;&#1490;&#1497;&#1501;", "&#1502;&#1493;&#1506;&#1491;&#1497;&#1501; &#1488;&#1495;&#1512;&#1497;&#1501;", "&#1502;&#1497;&#1493;&#1495;&#1491;&#1497;&#1501;", "&#1495;&#1494;&#1504;&#1493;&#1514;", "&#1504;&#1506;&#1497;&#1502;&#1493;&#1514;"] var aStarts ={19:'a7radio/',20:'a7radio/',3:""} var Live = {type:null,id:0,url:'a7live',title:'&#1513;&#1497;&#1491;&#1493;&#1512; &#1495;&#1497;'}; var oPlayer = Players.New(Live,0,{width:303,height:0},{forceTextAd:1}); oPlayer.SetVideo2=oPlayer.SetVideo; oPlayer.SetVideo= function(e){ 	$(".Item").css("background-position","left top"); $("#divItem"+e.type+"-"+e.id).css("background-position","right bottom"); 	e=$.extend(e,{title:"<b style=color:#c00>&#1502;&#1514;&#1504;&#1490;&#1503; &#1499;&#1506;&#1514;:</b> "+(e.type==19?'&#1512;&#1510;&#1507; '+aJukeboxCats[e.cat]+" - "+e.num+" - ":"")+ e.title+(e.author?" - "+ e.author:'')}) 	this.SetVideo2(arguments[0],arguments[1])} 	 $("#divPlayer").html(oPlayer.html); oPlayer.Writed3=oPlayer.Writed2; oPlayer.Writed2 = function() {oPlayer.Writed3(); oPlayer.Play();} oPlayer.Writed();   function GetInfo() {ExecuteJS("JS.ashx?act=list&func=GetInfo2&_" + new Date().getTime());} function GetInfo2(arr,usr) {aLists=[[],[]];iUser=usr; for (var i=0;i<arr.length;i++){arr[i].url=aStarts[arr[i].type]+arr[i].url; aLists[arr[i].tab].push(arr[i]);} UpdateLists();} function UpdateLists() { 	for (i2=0;i2<2;i2++) 	{	var s=[]; 		for (i=0;i<aLists[i2].length;i++) {var element=aLists[i2][i], click="onClick=oPlayer.SetVideo(aLists["+i2+"]["+i+"])"; 			s.push("<div class=Item id=divItem"+element.type+"-"+element.id+"><img "+click+" src="+(i2==1?"http://a7.org/images/radio/mini"+element.cat+".jpg":GetImage(element.image,100,70))+"><strong  "+click+">"+(i2==1?element.num:"")+" "+element.title+"</strong> <div  "+click+" class=Content>"+(i2==1?aJukeboxCats[element.cat]+ " "+element.name.replaceStr(aJukeboxCats[element.cat],""):i2==0?element.author+"<div style=font-size:8pt;padding-top:3px><b>&#1506;&#1493;&#1491;&#1499;&#1503;:</b> "+element.lastdate.hebDate()+'</div>':'')+"</div>"); 			s.push("<div class=Buttons><span title='&#1504;&#1490;&#1503;' "+click+" style=\"background-position:-42px 0px\"></span>") 			if (element.list) s.push("<span title='&#1512;&#1513;&#1497;&#1502;&#1514; &#1513;&#1497;&#1512;&#1497;&#1501;' style='background-position: -20px -20px' onmouseover=\"$(this).unbind('click').click(function(e){Left.List("+element.id+",'"+element.title.toHTML()+"',{y:40,x:$(document.body).width()/2-150,w:400})})\"></span>") 			if(iUser) s.push("<span title='&#1492;&#1493;&#1505;&#1507;/&#1492;&#1505;&#1512; &#1502;&#1492;&#1502;&#1493;&#1506;&#1491;&#1508;&#1497;&#1501;'  style=\"background-position:-104px "+(element.fav?-1:-18)+"px\" class='star"+element.id+"' onclick=Fav("+i2+","+element.id+",(!aLists["+i2+"]["+i+"].fav)*1);aLists["+i2+"]["+i+"].fav=!aLists["+i2+"]["+i+"].fav></span>") 			s.push("</div></div>");} 		document.getElementById("divIn"+i2).innerHTML = s.join(""); 	} 	setTimeout(GetInfo,900000); } GetInfo()  function AddOne(e) {e.url=aStarts[e.type]+e.url; oPlayer.SetVideo(e); if(e.tab==2)e.tab=1; oTabs.SetActive(e.tab+1);}  function Fav(type,id,value) {	 	ExecuteUrl("JS.ashx?act=fav&type="+type+"&item="+id+"&value="+value) 	$(".star"+id).css("background-position","-104px "+(value?1:-18)+"px"); } var sLastLocation; function CheckLoc() { 	if (sLastLocation!=location.href) { 		s=location.href.replace("%23","#").split("#") 		if (s.length>1) ExecuteJS("JS.ashx?act=one&func=AddOne&type="+s[1]*1+"&item="+s[2]*1); 		sLastLocation=location.href;} 	setTimeout(CheckLoc,4000) } CheckLoc();   $("#divTabs1 > span").mousemove(null);  Info.Add(211,"divTInf"); Info.Add(948,"divInf948"); Info.Final();  var pageTracker = _gat._getTracker("UA-3358878-1");pageTracker._initData();pageTracker._trackPageview(); </script></div> </body> </html>

---

### Post by lord_moa@yahoo.ca on 2010-09-29
[http://www.inn.co.il/Radio/Jukebox.aspx](http://www.inn.co.il/Radio/Jukebox.aspx)


Is the other plugin for Arutz Sheva if that helps in understanding why Totem or another player for Firefox and Ubuntu users cannot play the music, even though the picture of the radio player still comes up.

---

### Post by wmcbrine on 2010-09-29
"text/html" is the MIME type for ordinary web pages. So, instead of looking for a plugin for Totem, put the URL into your browser.

---

