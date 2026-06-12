---
title: "Teething Troubles and Wireless"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by GaryTheCat on 2011-05-29
I've just installed xubuntu on an old desktop for my son - it works OK but I can't get any sound out of it - I must have missed something?

Also sometimes when it starts the screen looks like the attached pic - what might be causing it and how do I fix it?

On another note, can anyone suggest a USB wireless adapter that works straight from the box with ubuntu - or at least with minimum messing around?

---

### Post by 4Orbs on 2011-05-29
I'm not sure my solutions will translate well to your situation, but here they are.

Sound: I have two sound cards and could not get any sound when I selected my preferred card in the xubuntu mixer preferences. The problem is that the xubuntu mixer doesn't provide an option to turn-off the other sound device. So I installed the gnome-media package which includes the gnome mixer and makes available a second dropdown menu from which I could turn-off the second sound device. Doing this made the sound begin working immediately, but it also adds a second volume icon on the xfce panel. A small price to pay for functioning sound.

I don't know about usb wireless adapters, but I can point you to an inexpensive pci wireless card that works for me with no problems or required configuration [HERE]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3246388&CatId=2688").

The scrambled screen might be because you need to activate the proprietary driver for your video card. Go to the System Menu > Additional Drivers and see if there is a recommended driver available for you graphics card. If so, activate it and reboot.

---

### Post by wolfen69 on 2011-05-29
We need specs about the computer.

---

### Post by Gye50 on 2011-05-29
First time i installed Xubuntu 11.04 my laptop was not connected to the Internet during the install so had no sound.  Then i remembered an install screen that said to be connected so that sound drivers could be installed.  Reinstalled with an ethernet connection on.  That worked for my onboard Intel sound and no problem since.

Can recommend not to use any wireless USB with a Broadcom chip inside because that requires special files installed from the Synaptic Package Manager.  So no Linksys unless you want to play around.

---

### Post by GaryTheCat on 2011-05-29
Thank you - that's fixed the sound :D

---

### Post by GaryTheCat on 2011-05-29
> **wolfen69 said:**
> We need specs about the computer.

Which specs? Sound problem seems to be fixed by using the gnome mixer method

---

### Post by 4Orbs on 2011-05-29
Using 11.04 I have encountered two other sound problems which may also affect you. If I log out and then login to another user account, there will be no sound. The only solution found so far is to reboot and login to the account. The other problem: sometimes sound is horribly distorted and the fix for that can be found on [This Thread]("http://ubuntuforums.org/showpost.php?p=9948061&postcount=2"). Both of these problems are probably related to Pulseaudio and the fact that I'm running sound through an HDMI output, so you might not ever need to deal with them.

---

### Post by walt.smith1960 on 2011-05-29
> **GaryTheCat said:**
> 

On another note, can anyone suggest a USB wireless adapter that works straight from the box with ubuntu - or at least with minimum messing around?

I'm glad you were able to get your sound fixed.  I have two wireless adapters that became plug & play in 11.04.  One is the Netgear WNA1100.  It uses an an Atheros chip and supports N150 speed.  Here's one source: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833122366&Tpk=netgear%20wna1100]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833122366&Tpk=netgear%20wna1100").  I don't know that price is great,  you can do some searching and you might do better.

A second adapter I've found to be plug & play is the TrendNet tew-649ub. There may be a problem with newer versions however.  Mine is an N150, the one posted on Amazon is N300.  There was a poster recently that was having trouble with an 8192SU based device running at 300Mb./sec.  TrendNet offers a tew-64**8** running at 150 Mb./sec but I seem to recall the chipset in the tew648 being problematic.  I hope others will chip in with WiFi adapters that are plug & play.  It might be worth your while to do a little searching in the networking & wireless forum to get a feel for what works and what's problematic.

Edit: in looking at the Amazon reviews, this device may indeed only run at 150 Mb./sec

---

