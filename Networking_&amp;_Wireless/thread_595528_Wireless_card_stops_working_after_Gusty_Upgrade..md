---
title: "Wireless card stops working after Gusty Upgrade."
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by Goda on 2007-10-28
I have a Linksys WUSB54GS usb wireless adapter. I've had it working fine in my last couple of installs when I followed this guide [http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54gs](http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54gs)
So here comes Gutsy, I upgrade and find that I can't connect to the internet anymore.  The power light is still on and it has all the information under the Hardware Info thing. Setting>Administration>Network shows it, with the right SSID and key. iwconfig shows wlan0 but with zeros or "none" in most of the values. Thats all of the information I can think to give. Thanks for any ideas anyone might have.

---

### Post by khughitt on 2007-10-28
Is the driver enabled in the restricted drivers manager? Sometimes it helps simply to disconnect and reconnect (left-click on the network icon and select the network you want to connect to again). You could also try uninstalling and reinstalling the driver via the restricted drivers manager.

---

### Post by Goda on 2007-10-29
Its nots even shown in the restricted manager

---

### Post by MariusSilverwolf on 2007-10-29
Try following this How-To: [http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)

It worked with my WUSB54Gv4, and according to the Hardware List at rt2x00.serialmonkey.com, the RT73 drivers should work with all WUSB54G based cards.  Emphasis on *should*.

---

### Post by Goda on 2007-10-30
The card I have is the Broadcom chipset. I don't think its a driver problem, but I don't know much about hardware in Linux either.

EDIT:
I tried this [http://ubuntuforums.org/showthread.php?t=540942&highlight=wusb54gs](http://ubuntuforums.org/showthread.php?t=540942&highlight=wusb54gs) and at first it didn't until i remembered to uninstall ndiswrapper. I did and at first the link light was flashing, and iwconfig had the right essid. Then it stopped working again. I cant get iwconfig to work right and change some of its values, its not effected by the graphical network manager.

---

### Post by Goda on 2007-11-02
I think this is just a networking software problem and not a driver problem because it recognized the card and shows a wlan0 after its plugged in.

---

### Post by Handssolow on 2007-11-02
> **Goda said:**
> I think this is just a networking software problem and not a driver problem because it recognized the card and shows a wlan0 after its plugged in.

Is your wlan0 showing in ifconfig and not just iwconfig?
Are you using the appropriate and latest broadcom driver/firmware?
What's showing up under the Restricted Driver Manager?
I suspect part of my problems are linked to me still using WEP rather than WPA.  

With our PC running a broadcom chipset we lost wireless after the Gutsy upgrade and needed bcm43xx-fwcutter_006-3_i386.deb to extract the driver from wl_apsta-3.130.20.0.o

Check out my earlier posting if this seems to fit,  [look here](http://ubuntuforums.org/showthread.php?t=580852&page=84)

---

### Post by Goda on 2007-11-05
It does show up in ifconfig. Only my video card is shown in the Restricted Drivers manager.

Those Broadcom drivers arn't for USB devices. Thats what I have.

---

### Post by khughitt on 2007-11-05
If all else fails, one option you could consider would be to try a newer beta kernel. Newer kernel versions sometimes have updated drivers, and this has been enough to save me at least on one occasion.

Ubuntu geek has [a guide]("http://www.ubuntugeek.com/howto-upgrade-kernel2622-9-generic-in-feisty-fawn.html") on how to upgrade the kernel to a newer version in ubuntu. The guide was written for upgrading to 2.6.22 in feisty (which is what ships now with Gusty), but it shouldn't be hard to follow the idea for the newer repos. Check the "sources" settings to enable testing repos.

Goodluck!

---

### Post by blwarburton on 2008-02-20
Here's another thread with similar symptoms in Virtualisation group:
[http://ubuntuforums.org/showthread.php?t=695144](http://ubuntuforums.org/showthread.php?t=695144)

In my case I'm running Ubuntu 7.10 under VMWare Workstation 6.0.2.
VMWare is running under Windows XP.

Ubuntu 7.10 install ok and and VMWare tools are compiled and installed ok - network is ok.
After performing Ubuntu 7.10 update the VMWare network driver (pcnet32) is deactivated and network is lost.

---

