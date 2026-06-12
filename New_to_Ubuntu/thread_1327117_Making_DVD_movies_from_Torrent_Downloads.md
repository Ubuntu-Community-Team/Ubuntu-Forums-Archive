---
title: "Making DVD movies from Torrent Downloads"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by pkj on 2009-11-15
Hi,

Have downloaded few movies using Bit Torrent...Files are with following extensions
 1CD Pre-DVDRipXviD xRG.avi

How do i make a movie DVD out of this so that i can play it in a normal DVD player...

pkj

---

### Post by 3rdalbum on 2009-11-15
Go into Brasero and create a Video Project. Drag your file to this window. Click Burn. That's all there is to it.

Alternatively, you can use the Devede program (it gives you a few more options, including a menu) but Brasero is capable of burning a single movie to DVD.

---

### Post by colin.p on 2009-11-15
The absolutely quickest, easiest and most painless answer, is go and buy a "cheap", $30 or so, DVD player from Walmart or some other "cheap" store, that plays DIVX.  Since DIVX uses avi format, you don't need to convert.
I used to struggle converting that took hours (I still use an athlon 1800+), until I went out and bought an upconverting Toshiba DVD player ( paid $69 Canadian) that plays DIVX. Just burn the avi to disk and pop it into the player and I swear it looks pretty good playing on my 47" LG TV.
Of course it will only play in a DVIX player, if you lend it to your mother who doesn't have DIVX....

---

### Post by pkj on 2009-11-15
Hi,

Tried Brasero...but throws up the following error

"It is not possible to write with the current set of Plugins"

pkj

---

### Post by Cheesemill on 2009-11-15
+1 for DeVeDe, it's in the Software Centre

---

### Post by sisco311 on 2009-11-15
Is [dvd+rw-tools]("apt://dvd+rw-tools")(apturl link) installed on your system?

---

### Post by pkj on 2009-11-15
yes dvd+rw-tools is installed

---

### Post by sandyd on 2009-11-15
dvdstyler offers a more professional approach.

---

### Post by pkj on 2009-11-15
Devede is creating image in one of the folders on my PC...After that am i suppose to burn the image on my CD or is there anything more to it

pkj

---

### Post by halitech on 2009-11-15
depending on the settings you selected, you should either get an actual ISO that you can burn as an ISO or you will get 2 folders, burn them as a video disc and it should work. I use K3B for burning as it seems to work better for me.

---

### Post by sisco311 on 2009-11-15
> **pkj said:**
> Hi,

Tried Brasero...but throws up the following error

"It is not possible to write with the current set of Plugins"

pkj

You also need: [dvdauthor, vcdimager and gstreamer0.10-plugins-bad]("apt://dvdauthor,vcdimager,gstreamer0.10-plugins-bad")

---

### Post by mick316 on 2009-11-15
Tovid is another good option you could look at - There is also a GUI version available if you are so inclined:

[http://tovid.wikia.com/wiki/Installing_tovid](http://tovid.wikia.com/wiki/Installing_tovid)

---

