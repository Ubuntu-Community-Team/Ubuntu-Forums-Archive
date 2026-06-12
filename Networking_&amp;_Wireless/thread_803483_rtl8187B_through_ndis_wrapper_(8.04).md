---
title: "rtl8187B through ndis wrapper (8.04)"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by mishaonline on 2008-05-22
Hi. I've seen a lot of threads on this subject but none about my specific problem.

I'm using a Toshiba A210 with Realtek's RTL8187B wireless card (internal usb). I'm trying to get the wireless working with the ndiswrapper v1.52 on ubuntu 8.04. 

ndiswrapper installed fine, so did the win98 modified driver (that I got from this forum, which is the original win98 driver with ID8197 mapping line added to it) and when I go "ndiswrapper -l" it shows:

net8187b : driver installed
	device (0BDA:8197) present


So far so good. BUT the wireless network is not showing up on the network manager and if I go "iwconfig" there is no wlan0. Furthermore, there is no mention of the ndiswrapper in dmesg.

I need help. Any ideas?

If I left some info out, ask me and I'll post it.

Thanks.

---

### Post by mishaonline on 2008-05-22
Nevermind. I solved that part but I'm stuck at a different thing right now.

Ndiswrapper is working now and wireless network appears in the network manager. When I go 'configure' it even detects my network and networks that are around me (neigbours) showing the signal strength. I'm using 128-bit hex WEP key on my network, so I choose "WEP (hexadecimal)", type in my security key and choose automatic (DHCP) for the IP settings. Then it says "changing configuration" for about 10 seconds, that disappears and everything seems that it should be working, but internet does not work and when I try to ping my router's ip it cannot be found.

I should also mention that even though ndiswrapper seems to be working, there is still no mention of it in dmesg.

This is really frustrating, it seems I'm so close to getting wireless working, but still not there :(

Please help

---

### Post by game_plan on 2008-05-25
I have not been able to get WEP to work with the modified .inf file through ndiswrapper either. However, it does work in WPA & WPA2 modes, and the modified drivers mentioned else where work perfectly in WEP apparently.

I'm still working on wireless myself so I'll let you know if I find anything that will be of use to you.

---

