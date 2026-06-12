---
title: "Network Manager locks up"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by Martym on 2007-04-22
Hello:

I am fairly new to Linux (started out in IT on AIX but had not touched it in six years or more) and after a bit of trial and error decided on Ubuntu.  The 7.04 is nice so far, my wireless was detected on setup which is a big +.  I do however have an issue that started when I attempted to set up my network printer (hooked up to a Vista machine).  I installed Samba via Synaptix and all went OK I guess.  the problem I am having is with Network Manager (System > Administration > Network).  I can open it up just fine but as soon as I click on anything in the window it locks up every time.  Most of the time I can do other things even though I cannot close the window.  Sometimes however it affects other apps like gedit or the terminal. 

The only way I can find so far to close the window is to reboot

Any suggestions?

Need more info?

---

### Post by Floppyjoe on 2007-04-22
I know this is a lame suggestion but you could log out and then log back into Ubuntu instead of rebooting.

---

### Post by Martym on 2007-04-22
did that and it sometimes works but more often than not doesn't.  

I now noticed that I cannot view, nor close the useless windows for services, user and group settings and who knows what else *sigh*, just when I get the ting set up the way I like it too.  At least this time I can use a terminal and gedit 


It's rather frustrating.

---

### Post by Martym on 2007-04-22
Well I was able to kill the processes once I found their PIDs using ps -ef.  Now to just figure out what is causing the issue to begin with.  Nothing jumps out at me looking in the logs from /etc/var but then again it's been a LONG time since I touched this stuff and in the mean time I have been stuck with AS400's

---

