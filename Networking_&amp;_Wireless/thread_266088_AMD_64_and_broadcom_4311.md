---
title: "AMD 64 and broadcom 4311"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by capnrick on 2006-09-26
Finally switched over to Ubuntu, not so new to linux.  I am trying to solve a few problems with the wife's laptop.  The main one that I want to get working consistently is her wireless card.  The laptop is in the Pavilion v3000 series, and for some reason HP desides to throw in the imresively linux unfriendly broadcom 4311, which also show up in some instances as a Dell 1390.  

**Problem:** Wireless connectivity starts out great, at 54 mbps, where I would like it to stay.  Unfortunately, the wireless card has it's own ideas.  It will work well for a while, then it will drop down to the next lowest rate, 36, then 24, then 18, then whatevr, until it gets to 1.  Sometimes it will bring itself back up to 36 or 54, and sometimes it will drop the network.  ALso, it likes to stay near the 1 mbps too long, and that is no speed for networking.

Here are some steps I have already taken:
[LIST=1]
[*]Broadcom 43xx kernel drivers - I know these exist, I've tried the bcm-firmware cutter, and no matter what I do, this driver will not recognize the hardware.  I guess the 4311 falls through the cracks here.  I have tried as many of the different accepted firmware as I could get the cutter to recognize.
[*]Ndiswrapper with compaq's latest driver ( 3308 )- This is the only way I can use the network card.  I deleted the module that came with the latest ubuntu kernel and compiled the latest version (1.23).  I used the latest compaq drivers as they actually have support for 64bit OS in there, so they actually work.  
[*]Not a router issue - moved the laptop near the router, no change.  Other wireless in the house works fine.    
[/LIST]

From iwconfig , I have taken a few notes.  These may or may not be relevant.  
```
          Bit Rate=36 Mb/s   Tx-Power:24 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:6C65-726F-79   Security mode:open
          Power Management:off
          Link Quality:100/100  Signal level:-32 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:894  Invalid misc:559836   Missed beacon:0
```

Then, a short while later:
```
          Bit Rate=11 Mb/s   Tx-Power:24 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:6C65-726F-79   Security mode:open
          Power Management:off
          Link Quality:100/100  Signal level:-25 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1084  Invalid misc:620828   Missed beacon
```

This same behavior has exhibited itself on kubuntu as well as my last distro.  This is all while the laptop is plugged in to the AC outlet, so it's not a power-saving issue.  We are using a simple wep ascii-based key, so I know it is not a problem revolving around WAP.  I tried no wireless key,(a wide open network), and no change.  

  If anyone has any help to offer, that would be great.  Am I missing a configuration file somewhere *(stable networking=yes)*?  Or is this one of the joys of being an unkowing broadcom customer?

---

### Post by Fully216 on 2006-09-26
Unfortunately I am not sure what is going on with the wireless internet.  I wonder if you however can help me.

I have a compaq r3000 laptop, which is very similar to your hp machine.  I am curious as to where you got the new 64 bit driver.  Could you provide a link.

---

### Post by capnrick on 2006-09-26
Well, this one is oficially compaq too, just mentioned HP because I tend to think of them as the same company.

Here is the current (9/26/06) link to the page with the drivers:
[http://h10025.www1.hp.com/ewfrf/wc/softwareList?lc=en&cc=us&dlc=en&tool=softwareCategory&product=3210693&os=228](http://h10025.www1.hp.com/ewfrf/wc/softwareList?lc=en&cc=us&dlc=en&tool=softwareCategory&product=3210693&os=228)

after download, you will need to use cabextract to get the drivers out of there.

---

### Post by Fully216 on 2006-09-27
Ah, most helpful.  Thanks!

---

### Post by eco751 on 2006-10-28
THANKS!

That was the driver version I finally used to get things working.  I have a Dell e1405 and the Dell 1390 wireless card (a Broadcom 4311), and finally used this driver and ndiswrapper 1.27 to get things working in Ubuntu Edgy (amd64).

My description is posted [on my wiki, here]("http://wiki.waningsun.net/index.php?title=Dell_E1405_%26_Linux_HOWTO").

---

### Post by teaker1s on 2006-11-10
hp dv6116eu (a Broadcom 4311 rev 01),and to get things working in Ubuntu Edgy bcm43xx-fwcutter-the amount of different tutorials is staggering 6hours later and network "managerapplet" i have wireless of sorts. 

when its set up it will login and I can only get 11mbit  on b or g
oddly it will drop out after an hour and dchp lease time or static ip make no difference

any suggestions please
(*,)

---

### Post by Fully216 on 2006-11-20
The fwcutter package will only allow 11Mbps.  To go any higher, you will have to try ndiswrapper.

---

### Post by FrodoB on 2006-11-20
I did finally get the BCM4311 working on my Compaq Presario just this last Saturday.  Here is the procedure that I followed:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

---

