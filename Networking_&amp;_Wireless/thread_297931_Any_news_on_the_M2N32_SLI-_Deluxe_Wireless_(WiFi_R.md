---
title: "Any news on the M2N32 SLI- Deluxe Wireless (WiFi RTL8187 chip) issue?"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by Gizim on 2006-11-11
Asus M2N32SLI- Deluxe Wireless (WiFi RTL8187 chip) mother board having hardcore disconnects from the network after using ndiswrapper with win98 drivers. r8187 blacklisted.
Any news or change on this? with this problem alone i am not ready to make the full change to Ubuntu from Windows.

---

### Post by jck on 2007-01-19
I've not heard of any, Gizim.

The only thing I read somewhere once was to work with the setting in your router.  I think it was the key refresh time, or something.  I think someone mentioned decreasing it would keep the connection from timing out.

I am putting an add-on PCI card in this weekend to try and get wireless.  If it works, I will let you know...whether here or in another forum topic.

---

### Post by Zer0Nin3r on 2007-01-23
Ref: [http://ubuntuforums.org/showthread.php?t=314352&referrerid=176230]("http://ubuntuforums.org/showthread.php?t=314352&referrerid=176230")


After switching from the 64bit to 32bit and Using the Win98 drivers from Asus, I haven't really had any problems with disconnects.  I only experienced it once.  The above link, I hope will give you some insight.  On there I have two posts about the RTL8187 chipset and my success and failures.

Cheers!

---

### Post by jck on 2007-01-25
Zer0Nin3r,

Well, I am gonna post this here since it's specific to the Realtek RTL8187.

I got the Encore ENLWI-SG 108Mb/s 802.11a/b/g card and installed it.  Of course (as most peripherals do), it loaded into Windows nicely with its driver.  However, it caused connectivity problems with my on-board Realtek USB wifi and the Asus WiFi program.

Upon disabling the Encore device, the on-board Realtek WiFi worked fine.

So, I rebooted the machine with both cards installed.  I tried doing an install of the Kubuntu 7.04 Fiesty Herd Alpha release 2.  However, it didn't want to quite work for me.

So, I rebooted again and did the install with Kubuntu 6.10.  With the Encore PCI wifi card in the box, the configuration of the network devices during installation showed:

eth0: Wired device 1
eth1: Wired device 2
wlan0: Atheros 5212 device
ath0: Atheros 5212 device.

I was puzzled by this.  But, I chose the wlan0 as the default hoping I'd get wireless connectivity installed.  It did configure the "wlan0", but it linked it (for some reason...probably found the first wireless device and linked it by default) to the Realtek device.  I could have probably blacklisted the RTL8187 USB wifi, but I decided to do a new reinstall with the PCI board removed from the box.

After I removed the Encore card and had just the Realtek on-board USB device, I re-installed Kubuntu 6.10 again.  Upon reinstall, the network device configuration process only showed the following network devices:

eth0:  ethernet device
eth1:  ethernet device

So...I had to chose one of the two...I chose eth0.

After the install, I booted into Kubuntu 6.10.  It showed in Network Config to have 2 enabled Ethernet ports and a disabled wireless connection.

At this point, I disabled the ethernet devices, and enabled the wireless.  I then installed KNetwork Manager and went into the options and setup my connection and found that it listed my Realtek device.  So, I set it to WPA Personal (WPA-PSK) and put in my key in ASCII and set it to TKIP.

Now...at this point...I think...it should work.

The configuration did not succeed.  It goes to "Activating device" (I think...I'm trying to remember exact words ) and gets to 28% on the progress bar and freezes...then after a while...the window just closes and KNetwork Manager restarts and the wifi is not active.

This is as close as I've ever gotten.  I've not had the device ever show up in KNetwork Manager before, so I am at least hopeful.

I am going to go back to (hope I get the nick right) Wieman's articles on here about the config settings for network devices in various files.  I think once I get those right and reboot, perhaps the device will begin working properly and sync to my router.

I will let you know as soon as I have more information.

That's all on the Linux learning front in FLA USA.

---

### Post by goofeyfoot on 2007-03-10
Gents:

I have the same wireless problem.

Have 6.10 x386. No drivers work.

I am about to trash the whole linux idea. Without wireless, I can't do anything I want, so what is the point.

Any suggestions would be appreciated.

All my other posts have pretty much dead ended.

Michael

---

### Post by Tlingit on 2008-07-01
Ndiswrapper will work i have done it get the patch from aircrack-ng! and your set.

My problem is learning how to compile my kernel with with out the mac80211 and with the ieee80211. 

That is what i want. so hope i helped.

---

