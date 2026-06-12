---
title: "Wireless disappearing act"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by javadiva on 2009-09-15
I lost my wireless connection quite some time ago which hasn't been a problem since the transmitter isn't really much use anywhere else in the house.  However, we went on vacation and about half the hotels only have wireless.  :(  I played around with all of the settings and couldn't get it to work.  Any help would be appreciated because we are going on the road again this week.

---

### Post by HarrisonNapper on 2009-09-15
For some laptops (and by that, I mean mine) do not work well with network manager, so something you might try doing is adding the notification panel to the taskbar. For this, use the following steps:

1. Right-click on the taskbar where you want the notification area to appear (this is similar to a system tray in windows, so many users prefer it on the edge of the taskbar)
2. Click on "Add to Panel..."
3. Scroll down and select "Notification Area"
4. Click "Add"
5. Close the "Add to Panel..." window

Next, you should see that the network is (probably) not connected. Click on the picture of the two PCs (or whatever it is) and select a nearby wireless network. Hopefully, next you'll see a green dot and a gray one, indicating that you are in the process of connecting to a wireless network. Hope that helps!

---

### Post by javadiva on 2009-09-16
Under "Name" in the connection properties window I have lo and eth0 but no wlan0.  How do I get my wireless option back?

---

### Post by mapes12 on 2009-09-16
If it's a built in wifi adapter then in Terminal ```
lspci
``` If it's USB ```
lsusb
``` and post the output back here.

---

### Post by javadiva on 2009-09-16
It's a Pro-Wireless 3945ABG  I figured that much out.
deb@deb-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

---

### Post by achase79 on 2009-09-16
Check out this website [Intel downloads]("http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Wireless+Networking&ProductLine=Intel%C2%AE+WiFi+Products&ProductProduct=Intel%C2%AE+PRO%2fWireless+3945ABG+Network+Connection")

---

### Post by del_diablo on 2009-09-16
I've had some minor trouble with hotspots myself.
I use wicd, which frankly turned out to be useless on connecting to unencrypted hotspots. I've had something similar with gnetwork manager(the one in the tray), it would not behavep properly on hotspots.
Knetwork manager was really good at unencrypted networks for hotspots, but it cannot connect to WEP networks.
Then i came across Wifi-radar, it is really nice. It did not conflict with WICD, nor the network manager. And it really did the trick on unencrypted hotspots.
Ubuntu got it in its package well, so its just sudo apt-get install wifi-radar.

It does need to be started with root powers(sudo, gksu, kesu?), but it is not a deamon so it is just to close after use. The interface on settings is messy on setting up connections, but it does not need any settings for a open network which frankly hotels usually got over here(and so does my school for the matter).
So it is:
1. Install
2. Start it with root powers
3. Select network and select connect
4. It will complain and say the network lacks settings, so click ok there
5. Do not set anything, and hit ok in the settings windows
6. You should now have network.

---

