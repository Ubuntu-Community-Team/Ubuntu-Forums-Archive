---
title: "linksys wpc54gxv2 doesnt work after reboot"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by pjvandehaar on 2008-07-17
I'm using Ubuntu 8.04, and a Linksys wpc54gx v2 wireless card. After unsuccesfully following a couple tutorials, i tried this one:
[http://ubuntuforums.org/showthread.php?t=573551]("http://ubuntuforums.org/showthread.php?t=573551")
It got my wireless working, but after rebooting, it didnt work. It recognized my router, but wouldn't load any pages. I followed these instructions again to get it working:
sudo ndiswrapper -i NETANI.INF
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
dmesg
sudo ndiswrapper -m
echo "ndiswrapper" | sudo tee -a /etc/modules
ifconfig
and put my password into system->administration->network again, and it worked.
So after rebooting a second time, i tried this a second time, but it didn't fix the problem. my wireless card had power, but didnt get a link until i did this and put in my router password a second time. however, it still wont work. any help?

i put "nshw" in terminal, and here's the network part:
 *-network
          description: Wireless interface
          product: AGN100 802.11 a/b/g True MIMO Wireless Card
          vendor: Airgo Networks Inc
          physical id: 0
          bus info: pci@0000:07:00.0
          logical name: wlan0
          version: 03
          serial: 00:13:10:52:32:58
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper+netani driverversion=1.52+Linksys,02/04/2005, 1.4.4.1 latency=248 maxlatency=255 mingnt=24 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

im using ethernet right now, so it may be incorrect.

---

### Post by pjvandehaar on 2008-07-21
*bump*
I think if i don't get an answer, I'll try uninstalling Ndiswrapper and starting over with the wireless, but if anyone has any ideas it'd be really nice...

---

### Post by danb0087 on 2008-07-21
I have a linksys wireless card (wmp54gx4) that uses an airgo chipset; got it working with a guide similar to this
[URL="http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html"]
guide
[/URL]
In part two (steps 1-4), I used the windows driver *.inf file for my card instead of netani.inf, ndiswrapper did the rest.

---

