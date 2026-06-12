---
title: "[SOLVED] Really need help to get Dell Wireless 1390 working in Vostro 1400"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by _Azrael_ on 2008-02-26
Hi all.

I can't get NDISWrapper to correctly load a driver for this Dell 1390 Wireless Adapter.

I've been using several how-tos, but I can't get this thing to move along.

I've compiled NDISWrapper from source on a clean install and I think it's working fine. I think the problem is how the device is being detected:

(lspci)
```
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4310 **USB Controller **(rev 01)
...
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
        Subsystem: Dell Unknown device 000b
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


``` As you see the broadcom device is detected on a USB Controller. It should be Mini-PCI according to the Dell inventory. 

I'm guessing this is the problem esp. since all relevant Dell drivers specifically say " (not USB) ".

BTW I can never get any other output other than the following:

(ndiswrapper -l)
```
azrael@Incinerator:~/bcm43xx/Tried/151517/DRIVER$ ndiswrapper -l
bcmwl5 : driver installed

```
It would be a real breakthrough after the many long hours(:cry:) just to get it to say that the hardware is detected after the last line above. 

The R151517.exe driver is recommended for the Vostro but I've tried a few others, which I unfortunately lost track of after the clean install.

If anyone can help me out of this rut I'd *really* appreciate as I'm breaking under the amount of other things to do at the moment!

---

### Post by JoeLinux117 on 2008-02-26
I can't say that I've tried installing that driver on a 64-bit system (if that's what you're using), but I have attempted it on a 32-bit.  I can honestly say that I've had better luck with the bcm43xx driver than the ndiswrapper driver, it just seems to work better for the Broadcom Wireless 1390.  Try this site and see if it doesn't help you:

[http://www.learnaboutlinux.net/wireless_1390.htm]("http://www.learnaboutlinux.net/wireless_1390.htm")

If you follow the "bcm43xx" section of that site, keep in mind that you'll need a 64-bit .sys file, instead of the 32-bit one.  You can find it in the same .EXE file that you opened up for ndiswapper, I believe the file should be called "bcmwl564.sys" (note the "64" at the end of the filename).  I hope this helps.



--JoeLinux
[Learn About Linux - A World Without Windows]("http://www.learnaboutlinux.net")

---

### Post by Jense on 2008-02-26
I just had simular problems with a bcm4318. For me the solution was in this howto:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) 


It took ten minutes to fix after searching for several days. sombody postet it worked with the bcm4310 both on 32 bit and 64 bit.

Good luck

---

### Post by _Azrael_ on 2008-02-26
Thanks to both above. I'll be sure to try those threads.

 I'm posting from a reinstall I did with openSuse (just to see if I could have it up out the box) but no luck here either. Worse off in some regards actually (touchpad, display quality).

Not too bad really as I'd hate to be left without Guts! Time then for yet another reinstall... *sigh* ](*,)

---

### Post by _Azrael_ on 2008-02-26
No, sadly neither of the above methods work. :frown:

bcm43xx-fwcutter is deprecated and needs to extract from an older driver version which doesn't seem to work.

Using ndiswrapper in the above thread leaves me in the original situation of undetected hardware (i.e., [FONT="Courier New"]ndiswrapper - l[/FONT] never says hardware detected).

I've got a feeling it's because the 1390 device is being picked up as a USB device and not Mini-PCI / Mini-Card. (see lspci readout above)

Does anyone know what's going on here? If it is a USB device what drivers would be used and would I still use bcm43xx or ndiswrapper?

---

### Post by JoeLinux117 on 2008-02-26
Have you tried "b43-fwcutter" instead?  It basically does the same thing as bcm43xx-fwcutter (extracts firmware), except that it looks to use the "b43" driver instead of the "bcm43xx" driver.  A good guide for this (that has worked in the past) can be found here:

[Guide For B43 Driver]("http://linuxwireless.org/en/users/Drivers/b43#b43andb43legacy")

Instructions for download and installation can be found on that page.  I've had people return with good results from there.  Hopefully your case is the same.



--JoeLinux
[Learn About Linux - A World Without Windows]("http://www.learnaboutlinux.net")

---

### Post by _Azrael_ on 2008-02-26
Thanks for the link Joe. I'll follow up on it now. I have a feeling it will work.

Got ndiswrapper working, though as you mentioned it's not ideal. Out of the many drivers I tried only this one could be loaded properly with ndiswrapper:

[_[COLOR="Navy"]R174291.exe[/COLOR]_]("ftp://ftp.us.dell.com/network/R174291.exe")

If anyone has similar problems, the above driver is worth trying as its multi-arch. It's large though.
I noticed two other users who had broadcom devices showing up as a USB device had similar success with this drive and ndiswrapper.

Will look at the b43 guide now. Update later.

---

### Post by _Azrael_ on 2008-02-27
Couldn't get b43-fwcutter working in FC8 and don't want to try it in Gutsy. I'll wait for Hardy stable.

Ndiswrapper is working, though I need to learn how to connect to wireless networks reliably (well actually to connect period). Busy assimilating [[COLOR="Navy"]_ kevdog's howto_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=571188&highlight=howto+without+network+manager") about wireless networks without gui frontend

todo:
enable synaptic touch pad sideways scrolling
enable intel gma 3100 drivers and compiz (love that stuff man...)
flame broadcom because they wasted 16hrs of my life :mad:

Any links / suggestions to assist the above issues would be much appreciated.
Any assassination of broadcom executives will be highly commended!:twisted:

---

### Post by _Azrael_ on 2008-02-28
After watching "The Prestige" magic just isn't the same...

...except when your wireless problems disappear mystically! *flash*

 I've got a question about what happened but I'll ask it elsewhere.

This thread is now dead! :-({|= *Funeral March*

---

