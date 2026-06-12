---
title: "Ethernet cable detection issues (&quot;activation of network connection failed&quot;)"
date: 2019-04-16
forum: Networking &amp; Wireless
---

### Post by vladk2k2 on 2019-04-16
Hello there,

I have a Lenovo Thinkpad W530 which is dual-booting Windows 10 (fully updated) and Ubuntu 18.04.2 LTS

I am getting "Activation of network connection failed" notifications regularly while using Ubuntu and can't really figure out why, since networking works (almost) without issue.
Hardware:
Ethernet - Intel 82579LM Gigabit NIC
WiFi - Intel Centrino Advanced-N 6205

I usually get the notification when I am connected via WiFi and it seems to be a problem with the Intel NIC.

**Scenario 1**
If I boot the laptop with the network cable unplugged, WiFi is connected and going to Settings -> Network shows "Wired - Connecting 10 Mb/s"
When I plug in the cable, it shows "Wired - Connected 10 Mb/s" although I tested the network and it's actually connected at 1000 Mb/s
If I close and reopen the Networking window, it correctly shows "Connected 1000 Mb/s"
If I pull out the cable, it still shows "Connected 1000 Mb/s" although ping no longer works, and I have to manually disable the wired connection to get traffic to go through WiFi

**Scenario 2**
If I boot the laptop with the network cable plugged, it shows "Connected 1000 Mb/s" and I don't get the notification.
If I pull out the cable now, it goes into "Connecting 1000 Mb/s" and switches over to WiFi, and I start getting the "Activation of network connection failed" notification every couple of minutes or so.
After a while, the Wired connection turns off and I get a "permanent" notification (doesn't go away until I click it)
If I plug in the cable after this, the "Wired" connection does not turn back on, although the status LEDs on the ethernet port light up and *ifconfig* shows [FONT=courier new]flags=4163<UP,BROADCAST,RUNNING,MULTICAST>[/FONT] albeit with no IP address (neither IPv4 DHCP address nor IPv6 link-local address). Packet counters do increase. If I turn it on manually, it comes back up normally (full speed, IP addresses etc.)
After a while, it does seem to turn back on by itself, but it takes > 5 minutes to do so.

Seems like the media detection (i.e. Windows' "Network cable unplugged") is not working correctly

P.S.: Windows has hibernation disabled (and consequently fast startup is disabled as well)

---

### Post by vladk2k2 on 2019-04-16
I also have an *ancient *Fujisu-Siemens Esprimo Mobile V5545 with a Realtek RTL8111 NIC running Xubuntu 18.04.2 in which the same cable gets detected when it's plugged/unplugged without issue (unplugging takes ~2 seconds to register)

Also, I've tried booting the Thinkpad with a Ubuntu 18.04.2 Live USB pen drive, and the issue remains (cable is not plugged - connecting - connection failed - wired turns off)

I've also tried booting with Ubuntu 18.10 from USB. When the cable is not plugged during boot, first time I tried, there was no "Wired" connection, second time it behaved exactly like 18.04.2. When the cable is plugged during boot, it connects and works correctly, although when I pull out the cable it remains "Connected" - does not detect that the cable has been unplugged

---

### Post by SeijiSensei on 2019-04-16
If you just want the Ethernet connection to remain idle, find the option in the Network Configuration GUI to turn off the "automatically connect to this network" option for the Ethernet adapter. 

You don't really say what you want the configuration to be.  You don't want to have both the wifi and Ethernet adapters connected to the same router as that can create routing problems and provides no performance improvement.  But I can't tell from your description whether you want just Ethernet or just wifi.  Disable the "automatically connect" option for the interface you want to remain idle.

---

### Post by vladk2k2 on 2019-04-29
So, the laptop is always connected to my home wifi, which would be the same network as the cable connection - which is the way it's always worked for both of my laptops, my wife's work laptop and my work laptop, without any hassle. There's no issue with the actual connectivity, as I really do get the message only when the cable is **not** connected.

What I'm trying to find out is if (a) Ubuntu has a problem interfacing the media presence of my network controller or (b) my network controller has a hardware issue that is surfaced in the way Ubuntu uses it (since it's not happening in Windows).

---

