---
title: "[SOLVED] RTL8187 alfa network awus036h"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Arcnsparc on 2008-07-24
UGH!  Ive been trying to get this wireless card to work for almost 8 or 9 months now!  I must be just dumb or something! Can anyone show me where I can find a step by step guide to get this card to work on my IBM R60 with Hardy?  Ive read so much stuff on it and I ALMOST had it working with gutsy (it could see networks but wouldnt connect).  THANKS!!!

---

### Post by Arcnsparc on 2008-07-27
So i found everything I needed to do here:

[http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)

VERY GOOD instructions!!

---

### Post by bionnaki on 2008-09-24
so, the alfa is working good on your system now? 

do you recommend the card?

---

### Post by Arcnsparc on 2008-09-25
Yeah it works very well.  I got a 9db antenna to go with it and I can get wireless from pretty damn far.  It is sturdy (lives at the bottom of my back pack) and cheap ( I paid around 80 for the card and the antenna I think).  I wouldnt recommend it to some one new to linux as it is a little tricky to get it up and running.  Backtrack got it up right away though, so other OSes might work better than ubuntu.  Good luck!

---

### Post by Jackie999 on 2008-09-28
I've been trying to use the AWUS036H for a few months now...linux comes with native rtl8187 driver. My personal experience is (with Hardy and Intrepid) the device doesn't stay connected..if I get a minute or two out of it I'm lucky. It drops connection and won't reconnect without a LOT of messing around-sometimes it just won't reconnect - although network manager argues that it is connected. There is a bug report about it. I'll have a look at the link you've posted there..see if it's any better than the native driver. I wouldn't recommend the AWUS036H.

---

### Post by dioltas on 2008-09-30
> **Jackie999 said:**
> I've been trying to use the AWUS036H for a few months now...linux comes with native rtl8187 driver. My personal experience is (with Hardy and Intrepid) the device doesn't stay connected..if I get a minute or two out of it I'm lucky. It drops connection and won't reconnect without a LOT of messing around-sometimes it just won't reconnect - although network manager argues that it is connected. There is a bug report about it. I'll have a look at the link you've posted there..see if it's any better than the native driver. I wouldn't recommend the AWUS036H.

I have the same problem. Major headache...
I've tried a few things, compiling different drivers etc...
It says its connected, but actually only works for less than a minute. Still searching for a solution. It works fine in backtrack for WEP cracking using different methods (on my own network of course), but haven't tried using it to browse the web in backtrack...

---

### Post by TrenTech on 2008-10-06
Yeah I had the same problem with it saying it was connected but sropping the connection. I found a little how to [COLOR="Blue"][http://globalsyzygy.wordpress.com/2007/12/30/fixing-your-rtl8187-netgear-wg111v2-in-ubuntu/#comment-19]("http://globalsyzygy.wordpress.com/2007/12/30/fixing-your-rtl8187-netgear-wg111v2-in-ubuntu/#comment-19")[/COLOR] When I complete all the steps the card works great but after I reboot It hangs during the login process and displays a blank grey box in the top corner of the screen. Can anybody tell me what's causing this? Or maybe a different way of getting the wifi to work? This one is the closest I've gotten to getting it to work.

---

### Post by prizzy on 2010-01-02
I recently purchased the awus036h usb card.  I have a dell 1727 and cannot for the life of me get it to work with Backtrack 4.  Do you have any suggestions?  I am still a newbie at linux, I hope it's not something really, stupid.

Edit:  It works with Ubuntu, and Kubuntu.  Backtrack will not even recognized it.

---

### Post by ~zenr on 2011-03-02
> **Arcnsparc said:**
> So i found everything I needed to do here:

[http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)

VERY GOOD instructions!!

The link is now broken, I check new one but none. If anyone knows please update this topic. Thanks!

---

### Post by panurgebr on 2011-05-27
> **~zenr said:**
> The link is now broken, I check new one but none. If anyone knows please update this topic. Thanks!

Can be accessed via [http://sourceforge.net/projects/rtl-wifi/](http://sourceforge.net/projects/rtl-wifi/) and downloaded on CODE -> SVN Browse -> Download GNU tarball


Cant say it is working... :p

---

### Post by skiet078 on 2011-12-11
i want to purchase Alfa AWUS036H card for backtrack5.
Is it suitable for compatiblty with backtrack 5?
which version of a Alfa AWUS036H is good?
i have seen this version of Alfa AWUS036H 1000mW USB Wireless WiFi Adapter.
My Budget is 2000 Rs . 
which version is best for long term use

---

### Post by ajmc on 2011-12-13
I am using awus036h on backtrack 5.  Last month it worked well when I tried cracking my wifi but last week I updated my the kernel to 2.6.39.4 and I have now problems using it.  It won't connect to my wireless network and I tried searching their site and found an update for 2.6.x ([http://www.alfa.com.tw/in/front/bin/ptlist.phtml?Category=105397#b](http://www.alfa.com.tw/in/front/bin/ptlist.phtml?Category=105397#b)) but I have no idea how to do it.  I read the readme file but the directions doesn't work.  The make command sends an error...

---

