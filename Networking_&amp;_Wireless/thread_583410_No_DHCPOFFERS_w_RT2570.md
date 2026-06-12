---
title: "No DHCPOFFERS w/ RT2570?"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by Mr. Ksoft on 2007-10-20
I just installed Gutsy on an older computer of mine.  Being the cheapskate I am, I'm trying to get it onto my wireless network using a Nintendo Wi-Fi USB Adapter (it is a modified RT2570/RT2500USB device and with normal drivers it will work as a receiver.)  I had it working great on my old install of Feisty using the serialmonkey's RT2570 driver (before the thing toasted itself trying to upgrade to the Gutsy RC) but on this new install it's being weird.

I was happy to see that when I first booted up, it recognized my adapter with the rt2500usb driver (which should be the correct driver because the rt2500usb is the same as the rt2570).  It shows a list of wireless networks in my neighborhood, including mine.  However, I cannot connect to my network.  I enter my WEP key and it accepts it, but it fails to connect.  I checked the system log and apparently the problem is that there are "No DHCPOFFERS recieved".

I don't really know what to do.  Any ideas?

---

### Post by Architeuthis on 2007-10-20
There are more people (like me) having a very similar issue, check out this thread: [http://ubuntuforums.org/showthread.php?t=582033](http://ubuntuforums.org/showthread.php?t=582033)

---

### Post by Mr. Ksoft on 2007-10-20
I have looked over that topic and others and I'm not too sure what exactly to do...

I don't think I can use the [ndiswrapper solution]("http://ubuntuforums.org/showthread.php?t=564419") linked to that thread because the Nintendo thing doesnt' actually have any kind of official driver, and I don't know which Windows driver on the Linksys page linked to in THAT topic is an rt2570/rt2500usb.

I also tried compiling the rt2570 driver from serialmonkey and I got a number of errors while trying to make it.  Therefore it would not compile.

Finally, the topic said to try Wicd and dhcpcd. Dhcpcd didn't make any difference.  I attempted to install Wicd by downloading the package on this Windows computer I'm on right now and taking it over there using a flash key.  It said it conflicted with network-manager, so I removed network-manager.  Wicd made GNOME freeze up when it was started, so I removed Wicd but then couldn't get network-manager to reinstall because it would only allow me to do it via the internet.  This computer CANNOT connect to the internet without wireless because I don't have an ethernet card for it (just a dial-up modem that hasn't been used in years), so I had to wipe the hard drive and start over -_-

Yeah, not much is working.

---

### Post by Whateverist on 2007-10-20
> **Mr. Ksoft said:**
> I have looked over that topic and others and I'm not too sure what exactly to do...

I don't think I can use the [ndiswrapper solution]("http://ubuntuforums.org/showthread.php?t=564419") linked to that thread because the Nintendo thing doesnt' actually have any kind of official driver, and I don't know which Windows driver on the Linksys page linked to in THAT topic is an rt2570/rt2500usb.

I also tried compiling the rt2570 driver from serialmonkey and I got a number of errors while trying to make it.  Therefore it would not compile.

Finally, the topic said to try Wicd and dhcpcd. Dhcpcd didn't make any difference.  I attempted to install Wicd by downloading the package on this Windows computer I'm on right now and taking it over there using a flash key.  It said it conflicted with network-manager, so I removed network-manager.  Wicd made GNOME freeze up when it was started, so I removed Wicd but then couldn't get network-manager to reinstall because it would only allow me to do it via the internet.  This computer CANNOT connect to the internet without wireless because I don't have an ethernet card for it (just a dial-up modem that hasn't been used in years), so I had to wipe the hard drive and start over -_-

Yeah, not much is working.

The driver for the Nintendo USb stick should be on Buffalo's site (it's a Buffalo WLI-U2-KG54-AI with a new sticker).

---

### Post by Vorticity on 2007-10-20
I'm having a similar problem with a straight wired ethernet connection, dhclient is pinging, but it doesnt get any reply, I've tried editing the /etc/network/interfaces file, but the problem is that I don't know what its supposed to look like for just a regular eth0 dhcp connection. The DHCP protocol seems to be working fine, but I'm wondering if I'm missing something?
thanks in advance

---

### Post by Mr. Ksoft on 2007-10-20
> **Whateverist said:**
> The driver for the Nintendo USb stick should be on Buffalo's site (it's a Buffalo WLI-U2-KG54-AI with a new sticker).
You're right.  I'd forgotten that.

However, I installed said driver with ndiswrapper and I'm in the exact same place I was before-- no DHCPOFFERS.

---

### Post by Whateverist on 2007-10-20
While this may not work for everyone, I've found that blacklisting *all* Ralink drivers and using ndiswrapper got me a working wireless connection. wicd can't see it, but I can browse normally.

---

### Post by Mr. Ksoft on 2007-10-20
I have all of them blacklisted-- no difference.

---

### Post by Mr. Ksoft on 2007-10-22
Bump.

I've been poking around topics here and it looks like the RT2570 is just plain borked.  =/

I ended up being able to compile and use serialmonkey's RT2570 drivers but I'm still stuck at the same spot-- a lack of DHCPOFFERS.  From what I can tell, everything else works great-- it sees my networks, takes my encryption key, and attempts to connect.  However the DHCP bit stops it.  As an alternative I tried setting a static IP but in that case it didn't work either-- I got Firefox to just sit with the little spinner in the upper right corner spinning infinitely. (As opposed to instantly saying "Can't Find Server" in other situations)

Any kind of possible solution yet?

---

### Post by Mr. Ksoft on 2007-10-23
Hey, I can turn this into a success story.

It seems that when I installed the serialmonkey driver, something was wonky about it.  I restarted and Ubuntu stopped recognizing that I had ANY wireless hardware.  Then, I checked /etc/network/interfaces and it was trying to find a wlan0 device, while the driver uses rausb0.  I changed the device name to rausb0 and restarted the networking service and BAM, it connects and gets a DHCPOFFER within seconds.  It works great now-- in fact I'm typing from it.

---

