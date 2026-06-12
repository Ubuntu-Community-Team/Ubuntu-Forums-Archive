---
title: "[SOLVED] acx111 wireless not connecting after 8.04 reinstall"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by southerngrey on 2008-11-23
I have just had to reinstall my install of Hardy amd64bit from scratch on the following:

AMD 64bit Athlon 4200+ dual core
2 GB of RAM
ECS nForce4-A939 Socket 939 nVidia nForce4 chipset Motherboard ATX
ATI Radeon X700 3D
Texas Instruments ACX 111 chipset generic wireless card
Dual boot : MS XP 32 and Ubuntu 8.04LTS 64 bit with the default gnome

On my previous install I configured the network manager from the nm-applet and it all worked fine. Now the wireless card is registering and has a driver, plus I can see the networks listed.  Whenever I try to connect however I enter the WEP key and it trys to connect but fails, according to the logs I'm getting

supplication errors
dhcp lease errors

iwconfig and ifconfig confirm the interface is running and I can assign the values via the command line but still cant get any traffic to the network..It all seems like it should be working but it isn't?  If anyone replies I can get more specific over from that system but without the wireless on it I have no connectivity. So if I reboot it'll be for something specific.

Oh and I've read and tried a lot of stuff listed here on the forums including diabling IPv6 etc, so far nothing has really helped.

Thnks for the help.

---

### Post by southerngrey on 2008-11-28
OK solved the issue for anyone who is suffering the same issue..

Apparently netmanager does not interact well with the acx module.  My solution was to use the command line to connect to the wireless.  I had tried this already and it hadn't worked.  The trick was to run dhclient to manually seek the dhcp server.

I still dont understand why netmanager worked before and now it doesnt but whatever, its solved now.

---

