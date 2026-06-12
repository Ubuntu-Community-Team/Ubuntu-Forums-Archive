---
title: "does lynx actually text only"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by ja660k on 2010-04-10
Hey guys, 
hopefully from the title ive roped in some views...

SO what i mean by actually
does it download the images and video content etc..?
as im typing this im realizing how dumb im being. but i like to be reassured. 

im alreay 70% of my download quota and its only the 11th.
my guess is it doesnt eval the content path's so therefor doesnt get the image... is this right

---

### Post by WinterRain on 2010-04-10
I would like to help, but I'm not sure what you are talking about. Could you re-word it to make it more understandable?

---

### Post by DrMelon on 2010-04-10
Lynx is a text-only browser - it will not download videos/images etc.

---

### Post by ja660k on 2010-04-10
> **DrMelon said:**
> Lynx is a text-only browser - it will not download videos/images etc.

... thats what i meant.
when your browser looks at html, it see's the img or the embed or whatever the tags are and it will fetch that video/picture, i was wondering if lynx did the same... just not display it.

---

### Post by DrMelon on 2010-04-10
It does not download them - it ignores them. No need to worry. :D

---

### Post by @rizz on 2010-04-10
[SIZE=2]I think you should be able to download files

lynx -[/SIZE][SIZE=2]source url > filename

 Replace URL with the URL of the page or image that you want to download.  Replace filename with a filename that you want to give to what you are downloading.[/SIZE]


[http://kb.iu.edu/data/aczi.html](http://kb.iu.edu/data/aczi.html)

---

### Post by takisan on 2010-04-10
As most likely posted before, Lynx only renders text. It does render different styles for different tags. Copy and paste this to get an example:
[HTML]<html>
<head>
     <title>PAGE TITLE</title>
     <link rel="stylesheet" href="default.css"> <!-- Is completely ignored -->
</head>
<body>
<h1 align="center">HEADING<!--That still appears in the center and headerish --></h1>
<p>
<b>BOLD <!-- Appears in red --></b>
<i>ITALICS <!-- Appears in seafoam green --></i>
<code>CODE <!-- Appears in a dark green --></code>
<blockqoute>BLOCKQUOTE</blockquote>
<table>
     <tr>
          <td rowspan="3">I Hate:</td>
          <td>Steve Ballmer</td>
     </tr>
     <tr><td>and</td></tr>
     <tr><td>iPads</td></tr>
</table>[/HTML]

---

