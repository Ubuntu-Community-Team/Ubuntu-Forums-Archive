---
title: "Radio Station"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by theozzlives on 2009-02-15
Can someone do me the favor of going to [http://www.katt.com](http://www.katt.com) and tell me how to get that station in Rhythm Box???

---

### Post by Tim Sharitt on 2009-02-16
View the source of the players page look for the link to the stream. It may be something like 
```
source=http://something.com/somestream.asx
```
or
```

mms://something.com/somestream
```

---

### Post by theozzlives on 2009-02-16
I tried what I think it was but it said I don't have a decoder installed. Here's the source:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>



<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>KATT-FM</title>
<style type="text/css">
<!--
#apDiv1 {
	position:absolute;
	width:760px;
	height:393px;
	z-index:1;
	background-image: url(stationlogos/2964.jpg);
}
body {
	margin-left: 0px;
	margin-top: 0px;
	margin-right: 0px;
	margin-bottom: 0px;
}
#apDiv2 {
	position:absolute;
	width:361px;
	height:19px;
	z-index:1;
	left: 43px;
	top: 170px;
}
#apDiv3 {
	position:absolute;
	width:342px;
	height:17px;
	z-index:2;
	left: 52px;
	top: 172px;
}
.style2 {
	color: #54b4f1;
	font-family: tahoma;
	font-size: 11px;
}
#apDiv4 {
	position:absolute;
	width:71px;
	height:22px;
	z-index:1;
	left: 41px;
	top: 205px;
}
#apDiv5 {
	position:absolute;
	width:55px;
	height:22px;
	z-index:2;
	top: 205px;
	left: 112px;
}
#apDiv6 {
	position:absolute;
	width:119px;
	height:22px;
	z-index:3;
	left: 287px;
	top: 205px;
}
#apDiv7 {
	position:absolute;
	width:416px;
	height:26px;
	z-index:4;
	left: 14px;
	top: 243px;
}
.style7 {
	font-size: 11px;
	font-family: tahoma;
}
-->
</style>
<link href="style.css" rel="stylesheet" type="text/css" />
<style type="text/css">
<!--
.style8 {
	font-size: 10px
}
#apDiv8 {
	position:absolute;
	width:300px;
	height:250px;
	z-index:5;
	left: 445px;
	top: 18px;
	background-color: #FFFFFF;
}
#apDiv9 {
	position:absolute;
	width:728px;
	height:90px;
	z-index:6;
	left: 17px;
	top: 291px;
	background-color: #FFFFFF;
}
#apDiv10 {
	position:absolute;
	width:37px;
	height:22px;
	z-index:7;
	left: 167px;
	top: 205px;
}
#apDiv11 {
	position:absolute;
	width:23px;
	height:22px;
	z-index:8;
	left: 204px;
	top: 205px;
}
#apDiv12 {
	position:absolute;
	width:25px;
	height:22px;
	z-index:9;
	left: 227px;
	top: 205px;
}
-->
</style>
<script type="text/javascript">
<!--
function MM_preloadImages() { //v3.0
  var d=document; if(d.images){ if(!d.MM_p) d.MM_p=new Array();
    var i,j=d.MM_p.length,a=MM_preloadImages.arguments; for(i=0; i<a.length; i++)
    if (a[i].indexOf("#")!=0){ d.MM_p[j]=new Image; d.MM_p[j++].src=a[i];}}
}

function MM_swapImgRestore() { //v3.0
  var i,x,a=document.MM_sr; for(i=0;a&&i<a.length&&(x=a[i])&&x.oSrc;i++) x.src=x.oSrc;
}

function MM_findObj(n, d) { //v4.01
  var p,i,x;  if(!d) d=document; if((p=n.indexOf("?"))>0&&parent.frames.length) {
    d=parent.frames[n.substring(p+1)].document; n=n.substring(0,p);}
  if(!(x=d[n])&&d.all) x=d.all[n]; for (i=0;!x&&i<d.forms.length;i++) x=d.forms[i][n];
  for(i=0;!x&&d.layers&&i<d.layers.length;i++) x=MM_findObj(n,d.layers[i].document);
  if(!x && d.getElementById) x=d.getElementById(n); return x;
}

function MM_swapImage() { //v3.0
  var i,j=0,x,a=MM_swapImage.arguments; document.MM_sr=new Array; for(i=0;i<(a.length-2);i+=3)
   if ((x=MM_findObj(a[i]))!=null){document.MM_sr[j++]=x; if(!x.oSrc) x.oSrc=x.src; x.src=a[i+2];}
}
//-->
</script>



</head>
<body onload="MM_preloadImages('images/button_play_on.jpg','images/button_stop_on.jpg','images/button_tuner_on.jpg');">
<div id="apDiv1">
  <div id="apDiv4"></div>
  <div id="apDiv5"></div>
</div>
  <div id="apDiv6"><!--<a href="frame.aspx?thepage=selector.aspx?nid=2920" target="b300"><img src="images/button_tuner_off.jpg" id="tuner" name="tuner" width="119" height="22" border="0" id="tuner" onmouseover="MM_swapImage('tuner','','images/button_tuner_on.jpg',1)" onmouseout="MM_swapImgRestore()" /></a>--></div>
  <div id="apDiv7">
  <table width="416" border="0" cellspacing="0" cellpadding="0">

      <tr>
        <td width="104" height="22" align="center" valign="middle"><span class="style7 style8"> <a href="http://www.katt.com/" target=_blank>HOME</a></span></td>
        <td width="104" align="center" valign="middle"><span class="style7 style8"><a href="http://katt.com/contactus.asp" target=_blank>CONTACT</a></span></td>
        <td width="104" align="center" valign="middle"><span class="style7 style8"><a href="http://katt.tunegenie.net" target=_blank>MUSIC STORE</a></span></td>
        <td width="104" align="center" valign="middle"><span class="style7 style8" style="visibility:hidden;" id="favdiv"><a name="favorites" id="favorites" href="frame.aspx?thepage=myfavs.asp?sid=2964&nid=2920" target="b300">MY FAVORITES</a></span></td>
      </tr>

    </table>
  </div>
  <div id="apDiv8">

      <iframe src="banners/300.aspx?zoneid=210" height=250 width=300 framborder=0 name="b300" scrolling=no></iframe>
    
  </div>
  <div id="apDiv9">
  <iframe src="banners/728.aspx?zoneid=211" height=90 width=728 framborder=0 scrolling=no name="b728"></iframe>

  </div>
  <div id="apDiv10">&nbsp;<a target="b300" onclick="if (confirm('Add this channel as a favorite?'))this.href='frame.aspx?thepage=myfavs.asp?addsid=2964&nid=2920';return true" href="javascript:void();"><img src="images/favadd16.png" border="0" /></a>&nbsp;</div>
  <div id="apDiv12"></div>
  <div id="apDiv11"></div>
 

<div id="apDiv3">
  <table width="100%" border="0" cellspacing="0" cellpadding="0">
    <tr>
      <td width="100%" valign=top>
<EMBED TYPE="application/x-mplayer2"  
PLUGINSPAGE="http://microsoft.com/windows/mediaplayer/en/download/" 
ID="WM"  
Name="WM"  
Width="230"  
Height="70"  
Src="http://citadelcc-KATT-FM.wm.llnwd.net/citadelcc_KATT_FM"  
AutoSize="1"  
AutoStart="1"  
ClickToPlay="1" 
DisplaySize="0"  
EnableContextMenu="1" 
EnableFullScreenControls="1" 
EnableTracker="0"  
Mute="0" 
PlayCount="1" 
ShowControls="1"  
ShowAudioControls="1"  
ShowDisplay="0"  
ShowGotoBar="0"  
ShowPositionControls="0"  
ShowStatusBar="1"  
ShowTracker="0">  

</EMBED>
</td>
      <td width="12%"><span class="style2" id="playertimer" name="playertimer"></span></td>
    </tr>
  </table>
</div>

<script type="text/javascript">
var gaJsHost = (("https:" == document.location.protocol) ? "https://ssl." : "http://www.");
document.write(unescape("%3Cscript src='" + gaJsHost + "google-analytics.com/ga.js' type='text/javascript'%3E%3C/script%3E"));
</script>
<script type="text/javascript">
var pageTracker = _gat._getTracker("UA-398386-10");
pageTracker._initData();
pageTracker._trackPageview();
</script>

<!--start Ando Media WCM Tracking tag © 2008--->
<script language="javascript" type="text/javascript">
  var sid=2964;
  var poid='WM';

</script>
<script language="javascript" type="text/javascript" src="http://m.wcmcs.net/m/pl.js.aspx"></script>
<div id="devs"></div>
<!--end Ando Media WCM Tracking tag © 2007--->

<iframe src="http://api.andomedia.com/geo/posthit.asp?s=2964&flat=1" height=0 width=0></iframe>
</body>
</html>

```

---

### Post by Tim Sharitt on 2009-02-16
[http://citadelcc-KATT-FM.wm.llnwd.net/citadelcc_KATT_FM](http://citadelcc-KATT-FM.wm.llnwd.net/citadelcc_KATT_FM) point to

```
[Reference]
Ref1=http://citadelcc-katt-fm.wm.llnwd.net/citadelcc_KATT_FM?MSWMExt=.asf
Ref2=http://68.142.119.123:80/citadelcc_KATT_FM?MSWMExt=.asf

```

both of which work for me. Does gstreamer suggest any plugins to be installed? I can't say for sure, but I think the pitfall plugin for gstreamer is what you need.

---

### Post by theozzlives on 2009-02-16
> **Tim Sharitt said:**
> [http://citadelcc-KATT-FM.wm.llnwd.net/citadelcc_KATT_FM](http://citadelcc-KATT-FM.wm.llnwd.net/citadelcc_KATT_FM) point to

```
[Reference]
Ref1=http://citadelcc-katt-fm.wm.llnwd.net/citadelcc_KATT_FM?MSWMExt=.asf
Ref2=http://68.142.119.123:80/citadelcc_KATT_FM?MSWMExt=.asf

```

both of which work for me. Does gstreamer suggest any plugins to be installed? I can't say for sure, but I think the pitfall plugin for gstreamer is what you need.

The second one worked for me, thanks! Now I don't have to click on 5000  links to get the KATT. Does Amarock have internet radio or no? I haven't found it.

---

### Post by neu2buntu on 2009-02-16
i use a simpler method ,without having to read so much text in the page source. this works for me on all stations except for streams in .swf
[0] i will presume that you use firefox 
[1] goto your page with radio stream
[2] if its not autoplay press play on the stream
[3] now in firefox  goto > tools > page info > media (there will be a list of images, background and embed)
[4] "embed" is the url we want , there will usually be more than 1
[5] now copy and paste into rhythmbox > radio > new .until you get the actual stream .in most cases it is usually the 1st or 2nd "embed" (embedded stream)
[3b] in some cases where the player has a pop up window you need to right click on a blank space and choose page info from here!!! for some reason it doesnt show is step [3]
   quite simple really   and im listening to your station in rhythmbox with the url= ```
http://citadelcc-katt-fm.wm.llnwd.net/citadelcc_KATT_FM
```:)

---

### Post by wolfen69 on 2009-02-16
is there a specific reason you need to listen to it in rhythmbox? it works for me right in firefox.

btw, love the avatar.

---

### Post by theozzlives on 2009-02-16
> **wolfen69 said:**
> is there a specific reason you need to listen to it in rhythmbox? it works for me right in firefox.

btw, love the avatar.

Just to many links to click.

---

### Post by froller on 2009-03-24
Thanx N2, your steps work nicely.  Now listening to BBC World Service on Rhythmbox.

Just to repeat:

> i use a simpler method ,without having to read so much text in the page source. this works for me on all stations except for streams in .swf
[0] i will presume that you use firefox
[1] goto your page with radio stream
[2] if its not autoplay press play on the stream
[3] now in firefox goto > tools > page info > media (there will be a list of images, background and embed)
[4] "embed" is the url we want , there will usually be more than 1
[5] now copy and paste into rhythmbox > radio > new .until you get the actual stream .in most cases it is usually the 1st or 2nd "embed" (embedded stream)
[3b] in some cases where the player has a pop up window you need to right click on a blank space and choose page info from here!!! for some reason it doesnt show is step [3]

---

### Post by thor.cms on 2009-06-03
Tried all the options and have no luck?  two urls in the embedded section but no love.. no response in pop up trying to right click?  station is air1.com
[http://air1.com/broadcast/playnow.aspx?media=listen&bt=3&](http://air1.com/broadcast/playnow.aspx?media=listen&bt=3&)
is the address in the pop up?  trying to rip stream to put into mp3 player.
Thanks for the help

---

### Post by starcannon on 2009-06-03
I was able to play the stream at KATT.
First I closed Rhythmbox
Second I had to reinstall libmms0 using Synaptic Package Manager.
Then I opened Rhythmbox, 
Then I copy pasted:
mmsh://citadelcc-katt-fm.wm.llnwd.net/citadelcc_KATT_FM?MSWMExt=.asf
into a new radio station dialogue.

Then it worked.

GL have fun

---

### Post by theozzlives on 2009-06-03
> **starcannon said:**
> I was able to play the stream at KATT.
First I closed Rhythmbox
Second I had to reinstall libmms0 using Synaptic Package Manager.
Then I opened Rhythmbox, 
Then I copy pasted:
mmsh://citadelcc-katt-fm.wm.llnwd.net/citadelcc_KATT_FM?MSWMExt=.asf
into a new radio station dialogue.

Then it worked.

GL have fun

Thanks for the work and the PM, but this has been taken care of a long time ago. (wish I can mark as solved)

---

### Post by Gotico_Luks on 2010-01-28
> **neu2buntu said:**
> i use a simpler method ,without having to read so much text in the page source. this works for me on all stations except for streams in .swf
[0] i will presume that you use firefox 
[1] goto your page with radio stream
[2] if its not autoplay press play on the stream
[3] now in firefox  goto > tools > page info > media (there will be a list of images, background and embed)
[4] "embed" is the url we want , there will usually be more than 1
[5] now copy and paste into rhythmbox > radio > new .until you get the actual stream .in most cases it is usually the 1st or 2nd "embed" (embedded stream)
[3b] in some cases where the player has a pop up window you need to right click on a blank space and choose page info from here!!! for some reason it doesnt show is step [3]
   quite simple really   and im listening to your station in rhythmbox with the url= ```
http://citadelcc-katt-fm.wm.llnwd.net/citadelcc_KATT_FM
```:)

THANKS!!!!!! Worked Perfectly!!!!!!! I spent 3 days looking for an answer!!! Thanks again!!! :)

---

### Post by Wataru8675 on 2010-01-28
As you said, .swf doesn't work with this method...  Is there an alternative method to get .swf streams to work?  Specifically the stream at [http://minnesota.publicradio.org/radio/services/the_current/streams.shtml](http://minnesota.publicradio.org/radio/services/the_current/streams.shtml)

---

