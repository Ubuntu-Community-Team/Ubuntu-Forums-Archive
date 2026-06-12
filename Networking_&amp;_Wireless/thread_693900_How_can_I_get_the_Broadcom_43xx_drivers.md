---
title: "How can I get the Broadcom 43xx drivers?"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by avkhatri on 2008-02-11
I've been using Ubuntu for 2 years now and I just got a new computer. I have Ubuntu installed on my computer but when I go to the restricted drivers area to get the drivers for my broadcom I cant because I don't have internet. I can't get internet because this is a desktop and my router is on the other side of the house so I cant connect VIA ethernet. Is there anyway to get these drivers? This is just ridiculous how am I supposed to get these propriety drivers?

---

### Post by harold4 on 2008-02-11
CD, flash drive, external hard drive, SD card, etc.

You'll need the .sys and .inf file (can get off support.dell.com).  You'll also need ndiswrapper.

---

### Post by avkhatri on 2008-02-11
Thanks, I was searching around and I found this 
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
If you scroll down a bit it shows a download for a .deb that has the drivers for the broadcom card. Could that possibly work?

---

### Post by harold4 on 2008-02-11
Looks like it worked for someone :-P

I got my 4328 rev3 to work from using the section [No luck yet?]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

Above that section, you'll see a link to snag the win driver you'll need.

---

### Post by avkhatri on 2008-02-11
Cool! It found my network. Only problem is that it is WEP encrypted and I've never been able to get WEP to work on Ubuntu. I did get it to work on MEPIS using the network tools on that but I can't connect to WEP secured in Ubuntu, I type the WEP and then nothing happens. I can connect to non-WEP fine. Are there any solutions to this?

---

### Post by harold4 on 2008-02-11
WEP isn't secure anyways.

Try putting your wireless card in roaming mode via "system > network?"  It's just a guess on the location since I run KDE.

Then click the network icon in the system tray, select your ESSID and pop in the key.  That's always worked for me.

---

