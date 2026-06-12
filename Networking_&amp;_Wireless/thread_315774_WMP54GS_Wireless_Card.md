---
title: "WMP54GS Wireless Card"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by bourne- on 2006-12-09
I struggled to get my wireless connection to work with ubuntu. But after serveral weeks of no success I gave up and tried on Suse, but I also failed. However, I did make further progress and during quest I came across something I find rather odd, and might explain why I am having such a difficult time getting my wireless to work.

When I am in my console (both in Ubuntu and Suse) and I type:
```
lspci
```
to attempt to figure out the wireless card installed I get this return:
```
00:0c.0 Network Controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev o2)
```
According to the box that my card came in its a WMP54GS. Now on the this site: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L) they have their list of cards and drivers and what not. The WMP54GS if you look it up does not come with the BCM4318 chipset in it. The drivers I am told to use according to that site are the ones off the setup CD: "wmp54gs.inf". So why does my computer tell me that my card is using the "BCM4318 chipset"?These seemed to work fine in suse however for some reason I am just not allowed access to the network even with the password put in. Although my network is detected by my computer. So I guess my question is, what drivers am I supposed to use? I am a little confusted to be honest. If I was trying to do this on a laptop it might be a little easier however I am not. It was a retail linksys card for a desktop. The information I have about the card according to the box and info according to the site doesn't match. So which drivers am I supposed to use? I hope this makes sense, its not toally clear in my head so I am not sure if I am describing it right. 

Additional Info:
Wireless card: Linksys Wireless -G Speed Booster PCI Adapter (box). 
```
00:0c.0 Network Controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev o2)
``` (according to computer)

thanks 
todd

---

### Post by bourne- on 2006-12-10
no body knows what drivers i am supposed to use in this case eh?

---

### Post by mick8759 on 2006-12-10
I am in the same boat.  I installed ubuntu on a desktop machine that only has the wireless card.  I have the same card as yo do.  I hope someone can help us out.:)

---

### Post by mchaggis211 on 2006-12-27
im a bit of a noob when it comes to linux and ive got the same chip set an everything but no success connecting to internet with it.
ive tried many tutorials on how to do this with no success

---

### Post by gcarelli on 2007-03-05
I havent tried it yet and I am new to linux but try this.  I worked for some one.  I am trying to figure out what it means.  It might work for you.

[http://www.ubuntuforums.org/showthread.php?t=95380](http://www.ubuntuforums.org/showthread.php?t=95380)

---

### Post by nauge on 2007-03-07
I've tried all of the above but still had problems. I finally went to this site and tried out the steps and my stuff finally worked, gl. [http://www.ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx-fwcutter](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx-fwcutter)

---

### Post by gcarelli on 2007-03-08
You are right it worked great.

The only thing is that my NetworkManager Applet does not show the wireless network or the bars.  Is there a config in there.  I could live with my Wireless is working.

Thank you for checking back.

---

### Post by nauge on 2007-03-08
gcarelli, This i'm not sure of I already had network manager installed plus other things so i'm not exactly sure what steps i did before installing the firmware. :confused:

---

### Post by gcarelli on 2007-03-09
I tried a few things it worked once. It should the wireless networks when I disabled the network connection be mistake, it did not work. i rebooted and did the same it did not work. The wireless network and my connection is working.  I can live with the no bars, my wireless is working. I can can see my connection via ifconfig.  

I what i did to get it working the first time was disable the wired NIC and rebooted, the bars and wireless networks in range where present.

---

### Post by siciliancasanova on 2007-03-12
Try [here]("http://ubuntuforums.org/showthread.php?t=381594").  It's simple, and you might have tried it already but it worked for me.

---

