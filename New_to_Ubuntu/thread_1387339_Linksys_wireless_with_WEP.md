---
title: "Linksys wireless with WEP"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by jage on 2010-01-21
Does a linksys with WEP work under Ubuntu? I've changed to a 128bit key as 64 is not supported, but it's still not working... well by not working I mean it says "Connected: Never" or something in the wireless configuration (I know this is windows-thinking but there is no "Connect" or "Test" button when I change the config... I just hit OK and wait and nothing changes, firefox doesn't work etc)
 
The linksys isn't broadcasting and I'm not sure what else to try other than just open it up and see if that works (but I've got 4 other systems on the router as configured and it's a pain enough taking them all to 128bit...)
 
Have also not tried wired connection, so I'm back in Windows to post this.
 
P.S. ubuntu 9.10 boot from CD

---

### Post by Captain_tux on 2010-01-21
You don't want to use **WEP**... it is VERY insecure. 

Use **WPA**.

---

### Post by jage on 2010-01-21
No I'm pretty sure I want to use WEP.  If you want to road trip out to my house, hide behind a bush, discover the network and hack my WEP then you're pretty much welcome to it.  It's not like I'm in downtown NY, I just want the minimum... which is why I was on 64bit WEP.
 
That said on p. 25 of the beginners guide in the last full paragraph it describes setting up for a non-broadcast wireless and the last sentance says: Click the CONNECT button when done.
 
To iterate I don't have a CONNECT button.
 
Thanks!

---

### Post by Psumi on 2010-01-21
> **Captain_tux said:**
> You don't want to use **WEP**... it is VERY insecure. 

Use **WPA**.

Especially when my devices can't use WPA. ;)

---

### Post by llamabr on 2010-01-21
To the original question, it looks like it's handled by the driver that runs your wireless.  What wireless driver are you using?  Or what device?

[http://ubuntuforums.org/archive/index.php/t-78162.html](http://ubuntuforums.org/archive/index.php/t-78162.html)
[https://help.ubuntu.com/community/WifiDocs/WLANHowTo](https://help.ubuntu.com/community/WifiDocs/WLANHowTo)


Btw, you've confirmed with other devices, or OS's, that the wireless is actually there, right?

---

### Post by rogue_0111 on 2010-01-21
Use MAC address filtering instead. Less stress in your life.

If someone wants to hack you they will.

---

### Post by jflaker on 2010-01-21
> **jage said:**
> Does a linksys with WEP work under Ubuntu? I've changed to a 128bit key as 64 is not supported, but it's still not working... well by not working I mean it says "Connected: Never" or something in the wireless configuration (I know this is windows-thinking but there is no "Connect" or "Test" button when I change the config... I just hit OK and wait and nothing changes, firefox doesn't work etc)
 
The linksys isn't broadcasting and I'm not sure what else to try other than just open it up and see if that works (but I've got 4 other systems on the router as configured and it's a pain enough taking them all to 128bit...)
 
Have also not tried wired connection, so I'm back in Windows to post this.
 
P.S. ubuntu 9.10 boot from CD

If you are running from the live cd, go SYSTEM>>ADMINISTRATION>>HARDWARE DRIVERS as you may need to install proprietary drivers where are available, but not included in the livecd or fresh installation...

Once you have your drivers activated, you should be able to see wireless networks and then connect to hidden networks (click on the network icon in the upper bar)...For hidden wireless, just punch in the info.

WEP can be cracked with automated programs in under a minute with VERY LITTLE KNOWLEDGE.  If you are in a populated area, you stand a good chance of someone accessing your internet without permission...Use WPA2 personal for your access point to prevent someone from hijacking your access point

---

### Post by jage on 2010-01-21
The wireless card is Broadcom 802.11b/g WLAN according to windows Device Manager.  It's working fine with Windows before and after switching from 64bit.
 
I'm using whatever driver came with 9.10 as the CD is still warm from burning today... 
 
Browsed through both of your links... since I'm booting from CD I think I'll wait to change the interfaces files or anything else suggested.  I'm going to try opening up the security and broadcasting and see if that gets me connected from the CD boot and go from there.

---

### Post by jage on 2010-01-21
> **jflaker said:**
> If you are running from the live cd, go SYSTEM>>ADMINISTRATION>>HARDWARE DRIVERS as you may need to install proprietary drivers where are available, but not included in the livecd or fresh installation...
 
Just read that, I'll try that too.  Thanks!

---

### Post by jage on 2010-01-22
Posting from Ubuntu via wired connection.

I had to plug in to download the driver for Broadcom B43 wireless driver.  There are no other options in HW Drivers.

"This driver is active and currently in use"

However, in the upper right in the bar under the network symbol I have the following:
Wired Network
 Auth e0
 disconnect
Wireless Network
 device not ready (greyed out)
--------------------------------
VPN connections >

I've tried disabling wireless security and copying the MAC address from the wired connection.  Not sure what to try next.

---

