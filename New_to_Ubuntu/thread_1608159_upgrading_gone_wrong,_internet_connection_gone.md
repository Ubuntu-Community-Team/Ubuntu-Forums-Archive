---
title: "upgrading gone wrong, internet connection gone"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by Fordo on 2010-10-28
dear people
 
I am a noob (I think) who was lured into using ubuntu recently. It was mostly a good choice untill I was advised by my less nuby friends to upgrade to the newest version (I was using 10.04 and upgraded to 10.10)
it went fairly well untill the restart.
Then I found out that I didn't come any further then the terminal. After long phone sessions I discovered that the driver of the videocard wasn't downloaded & installed. Further investigation showed that the internet connection was gone too for no particular reason, so simple command lines couldn't get the driver from the net.
 
hence the question: how to regain the internet connection via the terminal.
 
The problem is nót the network card or the connection itself: I am using both at the moment by another computer.
My less-noob friends couldn't help me so far despite numerous attempts.
Thanks a million if anyone could help solve this.

---

### Post by cariboo on 2010-10-28
It would help, if you told us how you connect to the internet, wired or wireless, and if wireless, what is the make/model of your wireless device?

---

### Post by Fordo on 2010-10-29
Alright, I connect wirelessly to a Speedtouch modem using a SMCWPCI-G 54mbps wireless PCI adapter.

---

### Post by MoebusNet on 2010-10-29
Are you able to boot from a Ubuntu Live-CD and get online? You may be able to repair your /home partition from the Live-CD using GParted, then finish your upgrade after rebooting. Just a suggestion, but I'm not an expert. Perhaps someone will chime in with more information.

---

### Post by Fordo on 2010-10-31
How would I use Gparted to fix things?

---

### Post by Fordo on 2010-11-02
Dear people
 
ehm
 
:(
 
help?

---

### Post by mastablasta on 2010-11-02
as for the graphics driver - before upgrade you were supposed to uninstall the old driver. i am guessing you didn't do this. not sure how to solve this, there are a few commands somewhere here on the forum for that i believe. but you would need to give your graphics card model so that someone can help you. but getting online first to get a new driver would be a good start.
 
Next mentioned issue is getting online. you say you connect wirelessly - try to connect by wire as usually no additional drivers are needed for that and then continue from there on.
 
Edit: Have a look here on how to get the required and necessary information:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
 
Note you could maybe use live CD if you need a nicer interface.

---

### Post by idefix_7 on 2011-01-27
Hi, I have a similar problem.
Wireless working fine, but after a maintenance update (I usually check once per week) now it seems I can not get connected !?
Wireless sources are found ... but a pop up screen comes after a while asking for WPA security key.
Now I did not change anything and other windows PC is still connecting fine wireless :confused:
What to do ?

---

