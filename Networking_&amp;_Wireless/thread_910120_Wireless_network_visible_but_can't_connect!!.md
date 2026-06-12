---
title: "Wireless network visible but can't connect!!??"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by daviec on 2008-09-04
Hi,

I've installed Hardy Heron on my desktop computer. I have a wireless USR5416 PCI card installed which worked fine with my previous Edgy Eft install.

Network manager sees my wireless network, but I can't seem to connect to it. So far I've installed ndiswrapper and the windows drivers for the card, and this seems to have worked but I still have the same problem. I can see the network but can't connect. :mad:

Can anyone help? :KS

---

### Post by daviec on 2008-09-04
OK, so I've managed to get it all in working order now.

I downloaded the WICD deb package on my laptop and moved it to my computer using a flash drive. Then used Synaptic to uninstall network manager, then installed wicd.

This allowed me to connect to my wireless network. I still had trouble getting internet, but through luck rather than judgement I happened to change the channel my router is on from 11 to 1 and suddenly my connection works!!

:guitar:

---

### Post by Nattal on 2009-03-14
Hi, sorry for resurrecting an old thread, but I'm having trouble installing the same card.

I should point out that I'm new to Linux, just installed Ubuntu today on a spare rig.  Everything went OK, everything else on the PC works fine.  I have wired connection on it but want to go wireless.

I have 2 problems (I think), the first, if I install the card physically then the PC won't boot.  I'm putting this down to being no drivers for it.

I run the ndswrapper to try and install the windows drivers, but the drivers are in the form of an .exe file.  Under windows you have to run the .exe, power down, install the card and switch on.

How can I get the .inf driver file from the .exe?  Can anybody help me or point me in the direction of a driver that I can install?

Many thanks in advance :)

---

### Post by ugm6hr on 2009-03-14
Have you already installed the driver on Windows?  If so, just retrieve from there:
> The three files required to use this will be extracted to C:\WINDOWS\system32\drivers as "usr11g.sys" and "tiacx111.bin" and to C:\WINDOWS\inf as "usr11g.inf."

---

### Post by Nattal on 2009-03-14
No I didn't, I reformatted the drive when I installed, but I have the same card running in another PC so I guess I can just go copy it from there.  Will try that. many thanks :)

---

### Post by Nattal on 2009-03-15
Well, I made some progress.  I believe I have the card installed correctly, I found the files usr11g inf and sys, but I couldn't find the tiacx.bin.  I used the inf files with ndswrap, all seemed to go well.

The card seems to be installed as far as I can tell, there are no error messsages anywhere that I can see.  I had to blacklist some drivers that were loading to get the PC to boot up first.

My problem at the moment is actually connecting to the network now.  I've selected "connect automatically" entered the SSID, and the security pass, but it won't connect.  The strange thing is, when it can't connect and asks me to enter the pass again, if I display characters, the characters are not what I entered for the key.

So I believe its failing due to having the wrong key, but if I correct the key I just get the same result.  Any ideas would be welcome :)

---

### Post by jobix on 2009-03-15
> **Nattal said:**
> 
...
My problem at the moment is actually connecting to the network now.  I've selected "connect automatically" entered the SSID, and the security pass, but it won't connect.  The strange thing is, when it can't connect and asks me to enter the pass again, if I display characters, the characters are not what I entered for the key.

So I believe its failing due to having the wrong key, but if I correct the key I just get the same result.  Any ideas would be welcome :)

If you are using WPA, the key will look different from what you entered. If you want to verify run the wpa_passphrase command from a Linux shell and see what it gives you. It should be what is getting displayed.

**wpa_passphrase ssid passphrase**

I don't know what your problems with connection could be. Did you see if ndiswrapper -l shows that the device is present?

---

### Post by ugm6hr on 2009-03-16
I would suggest turning off encryption temporarily to ensure it is working first.

I am uncertain whether ACX chipsets suppory WPA (I thought they didn't).

---

