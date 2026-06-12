---
title: "dvd'S want play"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by vincent downey on 2010-09-12
i made a ISO  burn dvd with Brasero it will play on the computer but want play in DVD player do anyone have ideal on what's going on please help a newbie . THANKS .

---

### Post by llamabr on 2010-09-12
What's on it?

Probably, it's not a problem with the disk, or the burn, but with the dvd player.  The dvd player will have to have the appropriate codecs to play whatever it is you want to play, so if you included mpeg or avi in your iso, probably the dvd player just doesn't know how to play it.

---

### Post by vincent downey on 2010-09-12
it's an AVI FILE ITS A MOVIE I always use windows nero when i burn movies it does work but when i burn on Linux mint using Brasero  it does not work when i put it in my dvd player . Thanks for the hit back .

---

### Post by misswham on 2010-09-12
same thing has happened to me.  when i make an iso with devede and burn in brasero, the dvd plays in my computer but not on any of my dvd players.  I hope someone answers this one.

---

### Post by Brandel Valico on 2010-09-12
Nero converts the AVI to the proper DVD Format which an AVI is not.

Bresero doesn't do the converting. 

It's been awhile since I have done it but there is a program called 2ManDVD in the Repo's or you gan get the .deb(.exe) file for it here
[2ManDVD]("http://www.getdeb.net/updates/Ubuntu/10.04/?q=2mandvd")

It does the necessary conversion of the AVI file to DVD format and creates an iso ready to burn to disc. It also has a decent menu creator and other features similar to Nero. Just remember to set it to the proper region. By default it burns the DVD's in PAL (Europe and surrounding country's) while if your in the US like me it's NTSC I believe. There is a simple drop down menu to switch it but it does need to be done every DVD if I recall right.

Unless they have updated devede since I last used it which was longer then I recall right now. It while having a menu feature doesn't do the conversion either. I remeber having to use a script I had to do the converting then using devede to do the burning to get the menu's. There is also a program called todisc or something similar I used to use to do it as well.

---

### Post by vincent downey on 2010-09-12
Thanks but that one is out dated and couldn't be found again Thanks .

---

### Post by misswham on 2010-09-12
i tried also to download that one and it didnt work.  I assumed once the avi file was turned into an ISO file using devede  that it was already converted to be burned and played on a dvd player.  what other software can be used to burn a dvd that can be played in an average home dvd player?

---

### Post by Brandel Valico on 2010-09-12
Try here [http://debian-multimedia.org/pool/main/2/2mandvd/2mandvd.php](http://debian-multimedia.org/pool/main/2/2mandvd/2mandvd.php) it also has a Deb file for it. Other then that my best advice is to do some google work. This is one area where Linux is still a bit behind Windows. There are onle a very few ways to get nice workable Video DVD's. You could also try a search for it in the software center or try typing this in the terminal. "sudo apt-get install 2ManDVD" minus the "".

---

### Post by Brandel Valico on 2010-09-12
Just thought of another issue I have ran into on occasion. It probably isn't the problem but if all else fails give it a shot. Certian players have issues running either + or - dvd formats. So if your using dvdr- disc's try a + disc and see if it works or the reverse. I've only ran into this maybe twice with people who had bought off brand players. Without making sure they played all the formats.

---

### Post by misswham on 2010-09-12
just installed the 2man dvd player and i see it in synaptic but i dont see it in my programs.  how can i find it?

---

### Post by Brandel Valico on 2010-09-13
It should be listed in the sound section of your applications list. But if not open a terminal and type "2ManDVD" to start it. If it fires up. Then you can create a launcher in the menu by right clicking applications -> Edit menu -> Add new item. In the window that opens type the above command into the command box. This will make a launcher you can then click to open it.

---

### Post by misswham on 2010-09-15
i typed in the terminal "2ManDVD" and it says command not found.  what does the problem seem to be?

---

### Post by Brandel Valico on 2010-09-16
Well lets try the easy thing first did you include the "" in the terminal. If so then instead simply type 2ManDVD not "2ManDVD"

If you didn't include them then it's not currently installed properly and you still need to get it installed.

---

### Post by misswham on 2010-09-24
nothing came up when i put it in with the" and without.  I went back to the page and tried to download all software and only one went through again.  it reinstalled and i go to synaptic and it was there but still cant find it.  i know there has to be software that burns dvd movies, avi's to disc that will play in ALL dvd players like NERO.

---

