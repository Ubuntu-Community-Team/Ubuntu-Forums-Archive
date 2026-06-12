---
title: "[SOLVED] WPA TKIP PSK contains a space -- IP manager won't change it"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by DrJohn999 on 2008-09-21
Ubuntu 8.04 running on a Dell Latitude 610. No problems with wireless connections using the Network Manager tool from the main toolbar, except @ work where the key contains a space character. IP Dept refuses to change the password (who can blame them -- there are maybe 50 other users).

WPA PSK works just fine @ home (either Hardy or WinXP) on my personal wireless net; the laptop works fine under WinXP @ work. I tried manual configuration with the Network Settings tool and also manual configuration from this forum ([http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)), which I couldn't get to work at all with anything and seems to be very much in the way when moving around from one spot to another.

I did manage to translate the ASCII key string to its HEX equivalent, but cannot get the Manager tool to accept the HEX values: it takes this as an ASCII string and thus fails.

My Question: Where are the network settings stored for remembered connections, and is it possible to replace the cached keys there with the HEX version?

Thanks,

DJ

---

### Post by DrJohn999 on 2008-09-21
Just to clarify, this is an Intel Pro 2200BG wireless adapter, not Broadcom:
> ~$ sudo lshw -C network
:
:
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:01:31:2e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated

-- DJ

---

### Post by DrJohn999 on 2008-09-24
Password was updated, space removed, now no problems. But I was ultimately unable to get the hex equivalent of the old (with space) pw to work. NetManager didn't help, nor did gedit.

Oh well, now it's fixed.

---

