---
title: "ASUS X552WE wireless drop"
date: 2015-05-03
forum: Networking &amp; Wireless
---

### Post by alex376 on 2015-05-03
HI, this is my first post on this forum. I hope that we will have a good time here :smile:

So, there is my problem:

I have a couple a diffrent problems with this laptop. First touchpad  didn't work, than bluetooth, than wi-fi indicator, now wi-fi completly :smile:
Wi-fi is conected but there is no signal. I need to manualy recconect by  switching off/on wi-fi. dont use network manager anymore, i am using  now WICD. 

This is iwconfig r

[ http://pastebin.com/Rs2s4iyi]("http://http://pastebin.com/Rs2s4iyi")
          


This is log from rfkill list all.

[ http://pastebin.com/rLef8y4q]("http://http://pastebin.com/rLef8y4q")


for sudo ifdown ra0 && sudo ifup ra0:

[http://pastebin.com/u2r4zxYn](http://pastebin.com/u2r4zxYn)

for lspci:

[http://pastebin.com/fCMQLqKb](http://pastebin.com/fCMQLqKb)


for ifconfig:


[http://pastebin.com/EnJNvi1v](http://pastebin.com/EnJNvi1v)


for iwconfig:

[http://pastebin.com/DY05Pu9Z](http://pastebin.com/DY05Pu9Z)

for sudo iw list scan:

[ http://pastebin.com/1ymDr4bK]("http://pastebin.com/1ymDr4bK")

for sudo iwlist wlan0 scan:

[ http://pastebin.com/JJBjYGNy]("http://pastebin.com/JJBjYGNy")
 
And that is that. Please let me know if u need additional information :smile: I am very pleased to see how this community works :smile:

---

### Post by alex376 on 2015-05-04
There is results from WIreless info script:

[http://pastebin.com/K2BsK6SB](http://pastebin.com/K2BsK6SB)

Also i tried drivers from pined post, #special case 2, dosen't work for me.

---

### Post by alex376 on 2015-05-08
bump.

---

