---
title: "Internet connection is &quot;loose&quot;"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by gfgodoy on 2006-11-30
I'm having problems with my Internet connection: I've configured it using the  sudo pppoe conf command, setting everything that I could change as default!

It worked and I got really excited since I'm a newbie at Linux :) 
But now, some problems started appearing: after a while, my internet connection fails me :( I can get anywhere on firefox and pinging some sites doesn't work! 
Reseting both my Alcatel modem, and my PC seems to work as a temporary solution :(

I noticed that my modem has 5 LEDs, Power, Line Sync, RX, TX and LAN. When working all of them blinks in green except for the first ones that stay green all the time... When the problems occurs, POWER and Line Sync keep on but only TX blinks (long blinks and some really short blinks).

Does anyone know what I'm doing wrong??? I'm pretty sure that this is not hardware related since it works on Windows XP.

Note: the problem occurs without crashes, but sometimes immediately after a crash my internet connection is gone :(

Also: the commands
sudo poff dsl-provider
sudo pon dsl-provider 

seem to bring my connection up again :( But I really don't want to type that every half an hour or so... 


Thanks in advance,
gfgodoy

---

### Post by zgornel on 2006-11-30
Take a look at /var/log/ppp.log and /var/log/syslog and post anything suspicious (after a disconnect)

---

### Post by gfgodoy on 2006-12-07
How do I do this?? I don't know how the read/edit these files :( 

I have also noted that it might be a DNS problem: web sites stop working but aMUle keeps running (weird :(???)

---

### Post by zgornel on 2006-12-08
Try ```
less /var/log/ppp.log
``` (q to exit, scroll with arrow keys).

---

