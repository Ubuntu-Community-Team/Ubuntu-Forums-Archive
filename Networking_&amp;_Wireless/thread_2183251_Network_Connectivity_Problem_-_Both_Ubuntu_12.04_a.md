---
title: "Network Connectivity Problem - Both Ubuntu 12.04 and Windows 8"
date: 2013-10-24
forum: Networking &amp; Wireless
---

### Post by Simon1049 on 2013-10-24
[COLOR=#333333]Hi,[/COLOR]

[COLOR=#333333]I am having problems with Network Connectivity on my Desktop PC.[/COLOR]
[COLOR=#333333]The PC is about 6 weeks old. I had no problems with networking for the first month or so, and then suddenly networking became non-existent or intermittent.[/COLOR]

[COLOR=#333333]Here are the desktop specs:[/COLOR]
[COLOR=#333333]Gigabyte B85M-DH3 Motherboard[/COLOR]
[COLOR=#333333]Intel Haswell i5 3.2 GHz[/COLOR]
[COLOR=#333333]16GB RAM[/COLOR]
[COLOR=#333333]Nvidia GT640[/COLOR]
[COLOR=#333333]Windows 8 & Ubuntu 12.04 Dual Boot[/COLOR]

[COLOR=#333333]Network Controller:[/COLOR]

Ubuntu Driver/Controller Information: (sudo lshw)
**RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller**
vendor: Realtek Semiconductor Co., Ltd.

Windows Driver/Controller Description:
Realtek PCIe GBE Family Controller
Driver Date: 2012-10-25
Driver Version 8.7.1025.2012

Driver Files:

Provider: Realtek
C:\Windows\system32\DRIVERS\Rt630x64.sys
File Version: 8.007.1025.2012

Provider: Realtek Semiconsuctor Corporation
File Version: 1, 2, 0, 4
C:\Windows\system32\RtNicProp62.dll

(When writing this post I booted into Ubuntu - no network connectivity, I then disconnected and reconnected the networking in the menu and then it connected)

Problem description:
Networking shows "Network Cable Unplugged". Sometimes it shows that it is connected but times out when uploading or downloading.

The problem occurs on BOTH Windows 8 and Ubuntu 12.04 (which originally made me think it was a hardware issue)

I have checked the network cable and router ports, none of which are problematic. (My MacBook Pro works fine using the same cable and port).
I phoned the store where I bought it and the technical guy thinks its a hardware issue.

[COLOR=#333333]Tried Setting the IP Address Manually, no success.[/COLOR]
[COLOR=#333333]Removed the static IP set on the router side (which worked 100% fine for five weeks - no success)[/COLOR]

[COLOR=#333333]I have tried to force 100 Mbps Full Duplex on the Windows machine and the connection worked for a few minutes. I shut the system down to try and do the same thing in Ubuntu. Ethtool in Ubuntu showed that the link speed was 10Mb/s Half Duplex which is strange.[/COLOR]

[COLOR=#333333]I have found that if I connect to my MacBook ethernet port (MacBook WiFi sharing through ethernet enabled), and I disable and renable the network, it connects everytime, on both Ubuntu and Windows. If I run ethtool with the Mac connected I get:[/COLOR]

[COLOR=#333333]Speed: 1000 Mb/s[/COLOR]
[COLOR=#333333]Duplex: Full[/COLOR]
[COLOR=#333333]Auto-negotiation: On[/COLOR]
[COLOR=#333333]Link detected: yes

I am starting to get extremely frustrated. Any ideas?[/COLOR]

---

### Post by ian-weisser on 2013-10-24
Ideas about what? You seem to have defective hardware. There is no useful workaround to that. It must be replaced.

Is your hardware still in warranty? If so, they should probably replace your motherboard.

---

### Post by Simon1049 on 2013-10-25
Yes the hardware is in warranty. I am convinced that it may not be hardware though.

[http://ubuntuforums.org/showthread.php?t=699658&page=2&p=4563390#post4563390](http://ubuntuforums.org/showthread.php?t=699658&page=2&p=4563390#post4563390)

I will try a few things through the weekend and then return it to the supplier. Replacing the mobo (esp if its not actually faulty) is a huge mission. Got an i5 stuck on there. If I have to pull it off, where do you keep it so it can't get dusty while the mobo is away for inspection.

---

### Post by ian-weisser on 2013-10-25
Inidicators that the issue seems to be hardware:

> **Simon1049 said:**
> [COLOR=#333333] [...]
I had no problems with networking for the first month or so, and then suddenly networking became non-existent or intermittent.[/COLOR]
[...]
The problem occurs on BOTH Windows 8 and Ubuntu 12.04 (which originally made me think it was a hardware issue)
[...]


It seems unlikely that you made some change on both Windows and Linux, at the same time, that compromised both sets of drivers to your network hardware.

The forum page you refer to is for a Linux-only issue. Remember also that you used to have the correct drivers.
You can certainly compile fresh drivers for Ubuntu. It won't hurt to try...but it also won't make any difference to your Windows install. 
Don't investigate too long, if the warranty period is short.

---

