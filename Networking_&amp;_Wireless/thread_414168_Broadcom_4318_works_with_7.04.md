---
title: "Broadcom 4318 works with 7.04?"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by Baethan on 2007-04-19
I have a Broadcom 4318 desktop card (Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller). I tried everything to get it working with the last version of Ubuntu, but it just wasn't cooperating. Has anyone got this card working in 7.04?

---

### Post by Rudy507 on 2007-04-20
Well, I installed 7.04 just now, and it doesn't appear to be working for me. :( 

It looks like the network manager has been reconfigured though and works a little better - but I still can't get connected. I enter all of the settings into Network manager, I think I'm connected but I'm not. 

iwconfig doesn't report the ESSID settings I enter into Network Manager ... and I'm unable to do anything (in other words, I'm not connected).

So, by default, in answer to your question, I would say no.

Maybe someone can help us out. Hopefully. I've been waiting for over 2 distribution periods, and have tried 3 releases - it's getting rather frustrating. Any help from anyone would be much appreciated.

---

### Post by bdogg64 on 2007-04-20
Here is an ndiswrapper guide that make work for you.  It works for my Broadcom 4311

[http://www.ubuntuforums.org/showthread.php?t=346083](http://www.ubuntuforums.org/showthread.php?t=346083)

---

### Post by keyboard_faceplant on 2007-04-20
Gotta love them Broadcom4318's don't ya?
 I couldn't get it work in Dapper to save my life, could get it to work in Edgy, and got it to work in Feisty Fawn following the same forum post that helped me get it running in Edgy:
[http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318]("http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318")

Hope this helps- had no problems here. Simply  click the hyperlink in the thread for 7.04, double click the package, and your problem should be solved.

---

### Post by groovomata on 2007-04-20
Did you try the following link? It worked perfectly for me with feisty:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by inchaos on 2007-04-21
I booted up Feisty and my Airforce One 54g card worked....for about five minutes.  Now I'm having the same problems I had in Edgy...Anyone else have a similar problem?

---

### Post by santiagozky on 2007-04-21
When I was using edgy I had no big problems with the bcm43xx driver. Actually it worked quite well. But now with feisty and a new laptop (also with the broadcom chip :( ), I havent been able to use the same driver (ndiswrapper works well although), I have read a lot of messages complaining about the driver with feisty (especially people with dell laptops), so I guess it is some kind of bug.

---

### Post by inchaos on 2007-04-21
I got it to work!
My Airforce One 54g Broadcom card now works after removing ndiswrapper and bcmxcutter from my computer.
What was happening, I assume, was that the network manager was firing up my wireless, but before it had a chance to connect to an available network, one of the other programs I'd attempted to use tried to force the driver/firmware...So maybe make sure you've only got one program attempting to do this at a time?  I was able to detect networks but they had no connectivity.
Now I'm enjoying wireless freedom...
:D

---

### Post by santiagozky on 2007-04-22
is it working with ndiswrapper or bcm43xx ?

---

### Post by Floppyjoe on 2007-04-22
I have it working on my laptop(bcm4318 ) with ndiswrapper using feisty upgraded from edgy. all i did was goto system/administration/network and enable roaming. Then click on the nmaplet and choose my wireless router.

---

### Post by equal on 2007-04-22
Forget all that guys. Just install the .deb in my sig, and it'll run fine after you reboot.

---

### Post by NullHead on 2007-04-22
Ok so your trying to get your bcm4318 working well this is what worked for me 1st try in Feisty

____________________________________________________________________________

1st download ndiswrapper 

you need to install ndiswrapper-common first before you install ndiswrapper utils
___________________________________________________________________________________________________

ndiswrapper common download 

[Download Hear]("http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.38-1ubuntu1_all.deb")

ndiswrapper-utils 32bit [Download Hear]("http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb")

ndiswrapper-utils 64bit 

[Download Hear]("http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.38-1ubuntu1_amd64.deb")

-----------------------------------------------------------------------------------------------------------------------------------------------------

Now download the driver for your bcm4318 card from my attachments and save it on your desktop. 
___________________________________________________________________________________________________


Ok now that you have all of that time to begin the fun stuff.
start by opening a terminal  and copy and past into it.

we will start by disabling your built in driver witch doesn't work. so we we will blacklisting it.

```
sudo gedit /etc/modprobe.d/blacklist
``` 

inside the window at the bottom line type in
```
blacklist bcm43xx
```

then save it and overwrite it,

Next install the ndiswrapper.debs that you downloaded by double clicking on them and click on the *install* icon in the top right corner or the window.

After all that go back to the terminal and extract the driver that you downloaded from my attachments by copying each line into your terminal ONE AT A TIME.
```
mkdir ~/wifi 
tar -xf ~/Desktop/drivers-* ~/wifi
sudo ndiswrapper -i ~/wifi/bcmwl5.inf
```

Now you should see some output ... that's a good thing
What you just did was make a drivers directory were your drivers are now stored.

Next lets check the install and see if it worked.
```
ndiswrapper -l
```
You should see some think like this.
```
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
```
Witch means that it worked. But were not done yet.

Next is to tell your computer to start your new drivers to load automatically. So put this into your  
terminal.
```
sudo ndiswrapper -m
```

Restart your computer and your done! The network manager in the top right corner should show your wireless network and you should be able to connect!

Now your done!!!!

---

### Post by Melcar on 2007-04-22
Having the same problem with my 4318 chip.  Worked perfectly with Edgy, but now refuses to work under Feisty.  Followed the same steps with ndiswrapper as before; the module loads correctly and I can scan for networks, but it just refuses to connect.

> **equal said:**
> Forget all that guys. Just install the .deb in my sig, and it'll run fine after you reboot.

That always works for me, but unfortunately it caps my wireless speed to 11Mbps, which is one of the reasons I try to use ndiswrapper.  I'm using the firmware hack right now until I can find a fix for this.

---

### Post by H.E. Pennypacker on 2007-04-25
> **equal said:**
> Forget all that guys. Just install the .deb in my sig, and it'll run fine after you reboot.

This only made matters worse.  It removed by eth1 connection all together.  It wasn't even listed under Networking.

---

### Post by Helmi on 2007-05-08
thanks, equal. My bcm4306 (Dell trumobile 1300) ran instantly after installing your .deb but unfortunately with 11 MBit/s only and with some interruptions in the transfer every half second or sth.

---

