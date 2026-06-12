---
title: "Hello, some help would be appriciated."
date: 2010-04-25
forum: New to Ubuntu
---

### Post by SuspectLogic on 2010-04-25
I'm an absolute beginner to Ubuntu. Just this morning I installed 10.04 64-bit along side windows 7(dual boot). The problem I'm having is that I can't access the Internet via Ubuntu because my wireless adapter (belkin usb with an 8192su chipset) isn't supported with the fresh install. So I've been booting back and forth accessing the internet with windows 7 so I can look for tutorials and then boot again in Ubuntu to work through a long complex solution, have it fail and gain no progress. problem is I'm a newby, and this is getting frustrating because well, the only solutions are long lists of commands who's results may vary. pls help, i know once I'm able to get connected things will start moving a lot faster.

---

### Post by Jive Turkey on 2010-04-25
I dont know the specifics of getting your wireless adapter to work but one thing you could try is saving the web page of a given guide as html file in windows.  Then after you have rebooted to ubuntu you can open the html file in firefox.  If you didn't set up ubuntu to mount your windows partition at startup you might find it helpful to use a USB thumb drive to save the files or to write them to a cd or something.

---

### Post by spiky001 on 2010-04-25
Have you upgraded at all if not I would do that via eth0 cable then check for drivers

---

### Post by mcoleman44 on 2010-04-25
> Have you upgraded at all if not I would do that via eth0 cable then check for drivers
+1
You said you were new to Ubuntu so Im going to guess you dont know how to update and check for drivers.
Applications>accessories>Terminal
```
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```
When your computer restarts go to system>admin>hardware drivers and see if any drivers are listed.

---

### Post by TBerk on 2010-04-25
There is also the Hardware Compat/Incompatibility List to pour over; you might find your USB adapter listed...

[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)


berk

---

### Post by spiky001 on 2010-04-25
Have googled this dos,nt look nice to install
 
[http://ubuntuforums.org/showthread.php?t=1350273](http://ubuntuforums.org/showthread.php?t=1350273)
 
good luck

---

### Post by mechro on 2010-04-25
You can get a Linux driver (zip file) for the 8192su here...

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU)

... the trouble is I have no idea how to install it. Maybe somebody else can advise you.

---

### Post by SuspectLogic on 2010-04-25
thanks you guys. I've saved quite a few tutorials as html, only the tutorials aren't cutting it for me. I really don't comprehend what i'm asking the computer to do when I type anything in to the terminal, so when a tutorial gets a little bit vague(and so far they all have a dip in consistency) i get lost.

Berk, I've searched the incompatibility list and haven't found my adapter.

as for the Internet approach, I don't have access without this adapter at the moment. I might have to wait until I have a direct Ethernet line, but i'll be working on my problem solving installation skills until then. who knows, i might stumble upon something. 

I'll still be checking in periodically for updates on the situation, pls don't give up on me :rolleyes:

---

### Post by SuspectLogic on 2010-04-25
> **mechro said:**
> You can get a Linux driver (zip file) for the 8192su here...

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU)

... the trouble is I have no idea how to install it. Maybe somebody else can advise you.

thanks!!!!! will someone walk me through this?

---

### Post by spiky001 on 2010-04-25
Not done it can you post anything so we can see

---

### Post by themusicalduck on 2010-04-25
I would really really try the method mcoleman44 suggested first. That is, go to System > Administration > Hardware Drivers and see if there is something available.

By running command lines you could be doing anything which might just make things more difficult later on. I would try to get connected through an ethernet or something first so you can get them the proper way before trying other things.

---

