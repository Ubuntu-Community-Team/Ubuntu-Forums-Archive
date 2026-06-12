---
title: "ugh, more issues, WIFI"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by Wall86 on 2006-12-17
ok, during my install, ubuntu detected my wifi card, a D-Link wda-1320, recognized as Ath0, in the hardware support list this device is supported, and it configured properly during install, the issue im running into now, is the fact that now, that i am all installed and ready to go, i have no internet, 

I was hoping in this being semi-painless, but all i have been having is problems with ubuntu this is just starting to get frustrating.

ubuntu 6.10

---

### Post by Wall86 on 2006-12-17
any help at all? i forgot to add that it is 6.10 AMD64, any help on even narrowing down this problem would be helpful.

---

### Post by thefirehead on 2007-01-03
I really need help with this too. Same exact problem. ndiswrapper doesn't seem to work. I tried a fix I found here

[http://eureka.emmgee.com/2006/12/ubuntu-610-setting-up-wireless-network.html](http://eureka.emmgee.com/2006/12/ubuntu-610-setting-up-wireless-network.html)

It shows that I have a wired card, and a modem, but my wireless card isn't showing up in the list of network hardware ...

I'm brand new to linux and have no clue what else to do

- sean

---

### Post by oranguman on 2007-01-03
hey.

I was just having this problem until a minute ago. 

First, download WiFi Radar (appropriate for your version of Ubuntu) and install it. If you're anything like me you will breathe a sigh of relief at finding a GUI that shows the different networks in range. Try it out. If your problem is that you have no problems (and that the threads full of driver problems have given you wifi hypochondria), you'll be set. 

I don't know if there's dependencies on that package but if there are d/l and install those too until you get the program working. 

but if you try that and ubuntu really isn't seeing your card, go to the terminal. type in 

     iwconfig

and it will show you the current configuration of your ethernet and wifi ports. copy that and post it on this thread and it will help people help you. also type in 

    ifconfig 

and put the output up. also post the model of your wireless card. 


 check out this thread in the meantime: 

[http://www.ubuntuforums.org/showthread.php?t=329642](http://www.ubuntuforums.org/showthread.php?t=329642)

---

### Post by haiku99 on 2007-01-03
also post the contents of /etc/network/interfaces     
 Sounds like you are almost there, probably just something minor needs to be fixed...

---

