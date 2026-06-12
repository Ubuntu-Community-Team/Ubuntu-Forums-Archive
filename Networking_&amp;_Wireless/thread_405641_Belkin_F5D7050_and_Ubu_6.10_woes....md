---
title: "Belkin F5D7050 and Ubu 6.10 woes..."
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by silverbullet007 on 2007-04-10
Hey all!

Ok I've been battling this for the past two days.. I've read alot of articles and forums posts concerning both the specific USB G device and overall wlan hardware and WPA.. most recently the HOWTO on this site regarding WPA/LEAP.

I'm having what I believe is some sort of special issue, now right before I followed that HOWTO I performed a fresh install last night so hopefully I've still got a clean FS.

Anyway below are some screenies of the most pertinent info I can find.. please if there's anything else that I can post I will surely do so.

[IMG]http://i44.photobucket.com/albums/f26/cockblocker007/linux/lsmod.png[/IMG]

[IMG]http://i44.photobucket.com/albums/f26/cockblocker007/linux/iwlist.png[/IMG]

[IMG]http://i44.photobucket.com/albums/f26/cockblocker007/linux/iwconfig.png[/IMG]

[IMG]http://i44.photobucket.com/albums/f26/cockblocker007/linux/interfaces.png[/IMG]

[IMG]http://i44.photobucket.com/albums/f26/cockblocker007/linux/ifconfig.png[/IMG]

I feel as though the wmaster0 "interface" is causing a problem as I havent seen it on anyone else's screenshots... Any help will be vastly appreciated.

---

### Post by dragomirov on 2007-04-10
never seen anything like the wmaster0 thing, but you can disable it editing your /etc/network/interfaces deleting "auto wmaster0" (this means that this card won't be automatically rise up at boot time or at restart of network interfaces). From the screens you posted I see also that you wmater0 is not configured (no ip appears after ifconfig command).
Then ```
sudo /etc/networking restart
```
To restart your network services.

Another thing: since I don't know if you have a specific routing table configured, having two cards running (even if with different ips) don't let you system to know how to connect. I mean that, for istance, if you try to surf google with you browser, your system doesn't know which card to use (eth0 or wlan0) so, deactivate one of the twos ```
sudo ifdown <cardname>
``` and retry

bye

---

### Post by silverbullet007 on 2007-04-10
Ahh I see now.  Ok could I comment out the eth entries in the interfaces files or should I just unplug it?  I know I tried commenting out the wmaster0 line and still got an error, I will post that image tonight.

---

### Post by spd106 on 2007-04-10
wmaster0 is a kind of master/virtual interface that can be safely ignored. I believe it's a side effect of the new wireless stack. It's like the wifi0 interface found by Atheros card users.

Have you tried running wpa_supplicant in debugging mode? The WPA sticky will show you what to do. Also try the wiki page given in my sig.

---

### Post by silverbullet007 on 2007-04-10
Ooo no I havent tried debug mode on the supplicant.  Thats on the WPA HOWTO?

---

### Post by stchman on 2007-04-10
If it is an Atheros wireless card follow my procedure:

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

---

### Post by silverbullet007 on 2007-04-10
No it's the Belkin F5D7050 USB G adapter..based off what I've read and using the "lsusb" command the usb id refers to it as using the rt73 driver.

---

### Post by spd106 on 2007-04-10
> **silverbullet007 said:**
> Ooo no I havent tried debug mode on the supplicant.  Thats on the WPA HOWTO?

Yes, when you get to the section about testing, swap ath0 for wlan0 and madwifi for wext and use the -dd flags for debugging mode. Don't forget to setup the wpa_supplicant.conf file.

---

### Post by stchman on 2007-04-10
> **silverbullet007 said:**
> No it's the Belkin F5D7050 USB G adapter..based off what I've read and using the "lsusb" command the usb id refers to it as using the rt73 driver.

According to Belkin's website they don't specify the chipset that device uses.

Madwifi currently does not support USB adapters, that is in the works.  Madwifi supports PCI, and PCMCIA.  You can buy Atheros PCMCIA cards for under $20.

If that is a Belkin USB wireless device uses Broadcom chipset then the ndiswrapper procedure I have should work.

[http://www.stchman.com](http://www.stchman.com)

---

### Post by silverbullet007 on 2007-04-11
Ok so last night I installed both the Linux headers for my kernel and the build essentials.  My current config has not changed except for I commented (#) out every other interface other than wlan0.  I can iwlist scan and it shows my ssid, channel, etc but isnt that just because their static'd in the interfaces file?

I've also tried changing wlan0 from static to dhcp and when the networking is restarted I see that int release but doesn't recieve any dhcp offers.  And of course being this is linux for some reason makes me neglect the simple stuff.  I can't ping my router which means I'm not associating, which means something else is still misconfigured and I'm not getting authenticated properly.

According to the ndiswrapper HOWTO, I installed a Wifi Network Manager util that allowed me to graphically install drivers.  At first it displays that the driver was present but not the hardware.  So I totally removed the driver via that util.  Added it back and now both hard and driver were "seen".  But still no authentication.

Is the a CLI method of associating to a WPA enabled AP?

---

