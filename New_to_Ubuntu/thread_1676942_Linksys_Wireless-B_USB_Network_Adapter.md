---
title: "Linksys Wireless-B USB Network Adapter"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by stalemath on 2011-01-27
Hi, I recently installed xubuntu 10.04 on a system and right now I don't have it connected to my router (need to buy a longer ethernet cord), but I have an old Linksys Wireless-B USB Network Adapter (2.4 GHz) and I was wondering if there are any drivers or any way I can use this device with xubuntu.

BTW, it is model no. WUSB11 ver 2.8

---

### Post by walt.smith1960 on 2011-01-28
Did you try just plugging it in?  Often hardware that's been around for a while is supported out of the box.  While the device is plugged in, you could check is additional software/drivers are available.  There may be something under System>Administration>Hardware Drivers (or something similar).

Edit:  You're using Xubuntu.  I'm not familiar but I assume there's some way to enable additional hardware.

---

### Post by robsoles on 2011-01-28
"Plug it in"
+1


Reboot and give the system a minute after you login and check if the device is up or not, if not then check the network configuration ("System"->"Administration"->"Network Tools") if there is no sign of a 'wlan0' or eth1, check that eth0 doesn't have any traits of being a wireless adapter too - please tell us if anything wireless, or terribly interesting, is there.

If there isn't a fat shiny clue in the Network Tools then please post back the terminal's response to
```
lsusb
```

---

### Post by stalemath on 2011-01-28
I'm not even seeing an "Administration" under "System"

---

### Post by stalemath on 2011-01-28
> **walt.smith1960 said:**
> Did you try just plugging it in?  Often hardware that's been around for a while is supported out of the box.  While the device is plugged in, you could check is additional software/drivers are available.  There may be something under System>Administration>Hardware Drivers (or something similar).

Edit:  You're using Xubuntu.  I'm not familiar but I assume there's some way to enable additional hardware.

Plugging it in didn't do anything noticeable. I went to System>Hardware Drivers and nothing showed up. :confused:

---

### Post by stalemath on 2011-01-28
> **robsoles said:**
> "Plug it in"
+1


Reboot and give the system a minute after you login and check if the device is up or not, if not then check the network configuration ("System"->"Administration"->"Network Tools") if there is no sign of a 'wlan0' or eth1, check that eth0 doesn't have any traits of being a wireless adapter too - please tell us if anything wireless, or terribly interesting, is there.

If there isn't a fat shiny clue in the Network Tools then please post back the terminal's response to
```
lsusb
```

While I couldn't find "Administration" or "Network Tools" (maybe it's different in the xfce for xubuntu 10.04?), inserting "lsusb" in the terminal did recognize my device  (Linksys WUSB11 v2.8 802.11b Adapter).

---

### Post by robsoles on 2011-01-28
So, did you restart the machine with the stick remaining plugged in at all times?

please **show** us the terminal's response to the following two commands:```
lsusb
ifconfig -a
```use 'code' tags like this```
[noparse][code]copy and paste the terminal's output here
```[/noparse][/code]

---

### Post by stalemath on 2011-01-28
> **robsoles said:**
> So, did you restart the machine with the stick remaining plugged in at all times?

please **show** us the terminal's response to the following two commands:```
lsusb
ifconfig -a
```use 'code' tags like this```
[noparse][code]copy and paste the terminal's output here
```[/noparse][/code]

Yeah, I had it plugged in the entire time when I restarted it.

ALSO, I found the network connection settings and there are 5 tabs: Wired, Wireless, Mobile Broadband, VPN, and DSL; all are empty except for "Wired": It has 2 selections - "Auto eth1" and "Auto eth0" (both say never used).

Here is what I get in response:
```

eth0
Link encap:Ethernet  HWaddr 00:12:17:55:62:ee
inet6 addr:  fe80::212:17ff:fe55:62ee/64 Scope:Link
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:3 dropped:0 overruns:0 carrier:6
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Interrupt:5 Base address:0x4000

eth1
Link encap:Ethernet  HWaddr 00:01:02:63:ef:56
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Interrupt:9 Base address:0xc000

lo
Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:68 errors:0 dropped:0 overruns:0 frame:0
TX packets:68 errors:0 dropped:0 overruns:0 carrier:6
collisions:0 txqueuelen:1000
RX bytes:5360 (5.3 KB)  TX bytes:5360 (5.3 KB)

```

---

### Post by walt.smith1960 on 2011-01-28
I wonder if you'd have any luck with NdisWrapper. NdisGTK(I think) is pretty straightforward.   Can you get a temporary wired connection?  Unfortunately Linksys' driver download is an .exe file so you'd need to somehow get W2K/XP .inf and/or .sys files.  Could you copy those files from a Windows install where this adapter works?  You have some homework ahead of you, it seems.

---

### Post by stalemath on 2011-01-29
Now it tells me that networking is disabled. How can I fix this??

---

### Post by presence1960 on 2011-01-29
Why don't you ask an admin to move this thread to the Networking & Wireless section of the forum? You may get more help there.

---

### Post by robsoles on 2011-01-29
> **stalemath said:**
> Now it tells me that networking is disabled. How can I fix this??

Where/what is telling you that?

In Ubuntu 10.xx using Gnome desktop, with panels left where they start from a clean install, the networking icon is in the top panel to the right, left of the time and 'power button'.

That has '[x] enable networking' on it's right click menu. Does that help?

---

### Post by stalemath on 2011-01-30
i fixed it but i still cannot connect to the internet. i don't know how to get my device configured

---

### Post by robsoles on 2011-01-30
Please be more definitive about what you cannot configure;

Is it that the wifi dongle still doesn't appear to be 'picked up' by your system?

Is it that the wifi dongle appears 'picked up' but it doesn't show any nearby wifi networks under the networking icon (left click this time).

Is it that it shows wireless networks but you haven't successfully connected to yours?

---

