---
title: "Dell Wireless Problems"
date: 2005-09-24
forum: Networking &amp; Wireless
---

### Post by wisequark on 2005-09-24
I've recently installed Ubuntu on my laptop and am thoroughly enjoying the experience however being tethered to a wired lan is becoming something of a hassle.  I attempted to setup the ndiswrapper utility with the drivers provided by dell but receive the following message on ndiswrapper -l

rmarini@ubuntu:~/wireless$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
r102320.exe     invalid driver!


and when trying iwlist wlan0 scan, I receive the following error

wlan 0   Interface doesn't support scanning.


Does anyone have any experiene with this problem?  And if so, a possible solution/workaround that doesn't require a 100ft cat5 cable.

---

### Post by firecat53 on 2005-09-24
I had to go download the latest drivers from Dell's website and use the bcmwl5a.inf in order for my Inspiron 1150 to work (1350 wireless card, I believe).  Don't know why the bcmwl5.inf didn't work, but it took a while to figure out!

Also, try sudo iwlist scan to actually get the scan results. 

good luck!

Scott

---

### Post by davidknibb on 2005-09-24
Firstly it seems that you tried to install the actual .exe driver through NDSWRAPPER.

It is the .inf file that you need.
Also you should not use the drivers on the provided disk download the one you need instead.  Go to

[Http://ndiswrapper.sourceforge.net/.../Ubuntu#Install](Http://ndiswrapper.sourceforge.net/.../Ubuntu#Install)

and follw the details.. Although they look difficult they seem to work easily.

David

---

### Post by Foaming Draught on 2005-09-24
Wi-fi (and reliable Palm synching) was a killer point for Linux for me, and made me ditch several previous attempts to switch completely away from MS. But everything just seemed to work when I tried Breezy Community.
We're going back 2 months, at my age I can't remember how I did things 2 days ago, but this is what I think happened.
I installed Breezy  using an ethernet cable. At some stage I was presented with an opportunity to configure other network devices, including a wireless card (Breezy had detected that I had a card but not what it was, a Belkin F5D7010au). I had a choice of using a native driver or ndiswrapper. I plumped for the latter, and used a second CD drive to choose bcmwl5.inf from the original Belkin install CD, I didn't go to Sourceforge. (the URL mentioned above is invalid this morning, by the way). Lights flashed on the Belkin card, I removed the ethernet cable and haven't looked back.
Post-install, it seems that one can use Windows Wireless Drivers from the System/Administration drop-down, and remove "wrong" drivers (like the .exe file you mention) and install "right" ones. Or in a terminal window (another reason why I stayed away from Linux for so long  ;-)  ), ndiswrapper will return the arguments you need to remove and install drivers.
Sorry if this smacks of teaching my grandmother to suck eggs.  Anything much more technical than changing a printer cartridge is beyond me, but I got wireless to work with amazing ease.

---

