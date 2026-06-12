---
title: "help with mobile broadband in ubuntu"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by scorpian81 on 2010-09-29
Hello, I have recently installed ubuntu 10.04 on my computer. It looks great and i'm eager to get on using it.  the problem i have is i cannot seem to setup my mobile broadband to work with ubuntu. i have a 3 mobile broadband dongle ( zte mf112 ). it works fine with windows but ubuntu doesn't recognise it. i dont think it does anyway.
i cant seem to find any help with setting it up so hope someone here can!
thanks in advance.

---

### Post by Hippytaff on 2010-09-29
Try having a look at this
 
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
 
Got usb stuff there. I'm sure a superubuntuan will be along shortly though :-)

---

### Post by scorpian81 on 2010-09-29
Thanks. i will check it out

---

### Post by Hippytaff on 2010-09-29
I found this on a thread elswhere on the forums
 
**>  **
[B]1. lsusb gives 19d2:0103

2. 
* sudo aptitude install usb-modeswitch
* sudo gedit /etc/udev/rules.d/zte_eject.rules
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="0103", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"

3. reboot

4. lsusb gives 19d2:0031

5. Using NetworkManager > Edit Connections... > Mobile Broadband, set up the dongle to access 3's network[/B]
****
 
The link to the full thread - [http://ubuntuforums.org/showthread.php?p=9719991#post9719991](http://ubuntuforums.org/showthread.php?p=9719991#post9719991)
 
Good luck

---

### Post by madmax75 on 2010-09-29
I think the problem with many (or most?) USB broadband dongles is that they also double as flash drives. Ubuntu has trouble recognizing them as modems and sees them as flash drives instead.

You need to install usb-modeswitch and usb-modeswitch-data to correct this.

The stupid thing is that they are in fact available in software repositories, but if the freaking USB dongle is your only way to access the net - so how are you supposed to download these files in the first place? :confused:

I keep nowadays at least three different versions of usb-modeswitch and usb-modeswitch-data on a CD and a USB stick. Just in case.

I don't get why they are not included on the Ubuntu .iso as a default? People would have so much less problems with USB broadband modems if this was the case.

---

### Post by torkelsprove on 2011-04-20
Hi,
Being a newcomer to Linux (Ubuntu 10) I have problems installing a mobile broadband-modem (Huawei E122) on my netbook (Samsung NC10). It worked with no problems, when I used Windows XP, but I would
like to use Ubuntu - and now I am completely lost.
What do I have to do?

Hoping someone can help me.
Regards
Torkel

---

### Post by UltraVioletOne on 2011-04-20
> **torkelsprove said:**
> Hi,
Being a newcomer to Linux (Ubuntu 10) I have problems installing a mobile broadband-modem (Huawei E122) on my netbook (Samsung NC10). It worked with no problems, when I used Windows XP, but I would
like to use Ubuntu - and now I am completely lost.
What do I have to do?

Hoping someone can help me.
Regards
Torkel

Hi I am new too, this is what worked for me and it works great, not got into the coding side yet, so there is probably an easier way.  Have used same procedure in both Ubuntu 10.4 and 10.10, tried both versions. I use the   Huawei MF112, so don't know if there is a difference between them; I  had the same problem at first; we are on 3, so don't know for different  networks.

Ubuntu saw it as a flash drive as well as a modem.  N.B. Windows needs  the software installing that comes with the USB modem, but Ubuntu  doesn't.

What worked for me, hope it helps:

1. Plug in dongle, an icon should appear on desktop,

2. if not look for it in  places menu on toolbar, right clicking the icon for your dongle in  places menu, should open a folder on your desktop, close this folder,  and an icon should also be on desktop too. 

3. This next step is only necessary to do once: Go to network manager icon on toolbar, right click, enable mobile broadband.

Toolbar>network manager; (right mouse click): > enable mobile broadband

Next: Toolbar>network manager (right mouse click); > edit connections > mobile broadband > add

Network should take you through step by step everything you need to do, all the settings I needed were automatically there for me.

On the last screen (IP PPP dialing and APN), tick the box at top to connect automatically then > apply

Missing this last step, meant I could not connect

That works for me on 3 network, you didn't mention which network, but would imagine it works the same way.

That is now setup.

4. Finally and I do this every time I want to connect, although occasionally it has a mind of its own and loads, I think that was in 10.10 though, so probably different. 

Go to the icon on your desktop, and mouse rightclick; > eject   its seconds and network access is there. This unmounts the flashdrive part that Ubuntu sees as a drive, and  network manager should kick in a few seconds later, and confirm network  access.   You should then be on the internet.
 
No icon repeat step 2. 

It was imperative for me to have the connection, needed the updates, to be able to boot properly, graphics issues. Which the updates solve immediately. Don't think I have missed anything out, hope it works for you.  If you find a better way, let me know. Good luck :)

---

### Post by spur on 2011-04-21
I am attempting to get mobile broadband (Iinet Huawei E1762 usb stick) to work.
Net work manager asks me for data but not for the network. I am thinking this is why I can't connect.
When Network Manager comes up I put in the number, user-name and password, but thats all.

---

### Post by Fedz on 2011-04-21
Hi,
I've got got 11.04 (Nutty) installed & mobile broadband works flawlessly on it - so maybe consider upgrading if not already - I have the ZTE MF627 dongle & within network connections you can just click 'enable mobile broadband' & click next, next, next on mobile broadband tab :) Done - I was impressed big style Whoop!

---

### Post by Linux_junkie on 2011-04-21
> **Fedz said:**
> Hi,
I've got got 11.04 (Nutty) installed & mobile broadband works flawlessly on it - so maybe consider upgrading if not already - I have the ZTE MF627 dongle & within network connections you can just click 'enable mobile broadband' & click next, next, next on mobile broadband tab :) Done - I was impressed big style Whoop!

Please do not install Natty yet as its only in beta at the moment! Unless you want to simply test it for bugs.

---

### Post by spur on 2011-04-21
Nutty is only a few days away and I will be trying it then, but I do want to sort this problem by then.

---

### Post by MigleM on 2011-07-11
> **Hippytaff said:**
> I found this on a thread elswhere on the forums
 
****
 
The link to the full thread - [http://ubuntuforums.org/showthread.php?p=9719991#post9719991](http://ubuntuforums.org/showthread.php?p=9719991#post9719991)
 
Good luck

Hi,

I have an EEEPC with Ubuntu Linux and need to get a E122 modem working on it. I get as far as where lsusb gives 19d2:0031 (Modeswitch installed). However, my computer does not show the device as a 3G connect drive. How can I get to the point where I can activate the device in order to connect to 3G?

Thank you in advance,
Migle

---

### Post by gandaran on 2011-07-11
> **MigleM said:**
> Hi,

I have an EEEPC with Ubuntu Linux and need to get a E122 modem working on it. I get as far as where lsusb gives 19d2:0031 (Modeswitch installed). However, my computer does not show the device as a 3G connect drive. How can I get to the point where I can activate the device in order to connect to 3G?

Thank you in advance,
Migle
your modem should work just fine, which ubuntu version do you have?
if you have 10.04 then you have to install usb-modeswitch.
have you tried running the mobile broadband setup wizard?

---

