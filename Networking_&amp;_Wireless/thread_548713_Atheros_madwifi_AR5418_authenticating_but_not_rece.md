---
title: "Atheros madwifi AR5418 authenticating but not receiving DHCP"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by bismark on 2007-09-11
I have been using the svn of the madwifi drivers for a couple of months now and it works "fairly" well (for a Pre-N card I'm not going to complain much).

Recently however I had to rebuild my system.  I installed Xubuntu (previously had straight Ubuntu) and used the same kernel (2.6.20-16-generic) modules I had built before.  My wireless card was detected and would authenticate.  However, it would never get an address through DHCP.

I tried building the newest driver from svn and still the same.  I get authenticated but no DHCP address received.  I have tested this on multiple known working access points both Open, WEP and WPA.

Anyone have any ideas?  I don't know if this is an issue with the madwifi svn or something else.

Here's a copy of my syslog messages
```

Sep 11 15:58:32 mysystem kernel: [27304.004000] ath_hal: 0.9.30.13 (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)
Sep 11 15:58:32 mysystem kernel: [27304.012000] wlan: 0.8.4.2 (svn r2706)
Sep 11 15:58:32 mysystem kernel: [27304.016000] ath_pci: 0.9.4.5 (svn r2706)
Sep 11 15:58:32 mysystem kernel: [27304.016000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Sep 11 15:58:32 mysystem kernel: [27304.016000] PCI: Setting latency timer of device 0000:03:00.0 to 64
Sep 11 15:58:32 mysystem kernel: [27304.152000] ath_pci: switching rfkill capability off
Sep 11 15:58:32 mysystem kernel: [27304.164000] ath_rate_sample: 1.2 (svn r2706)
Sep 11 15:58:32 mysystem kernel: [27304.164000] ath_pci: switching per-packet transmit power control off
Sep 11 15:58:32 mysystem kernel: [27304.164000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Sep 11 15:58:32 mysystem kernel: [27304.164000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Sep 11 15:58:32 mysystem kernel: [27304.164000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Sep 11 15:58:32 mysystem kernel: [27304.164000] wifi0: turboA rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Sep 11 15:58:32 mysystem kernel: [27304.164000] wifi0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Sep 11 15:58:32 mysystem kernel: [27304.164000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Sep 11 15:58:32 mysystem kernel: [27304.164000] wifi0: mac 12.10 phy 8.1 radio 12.0
Sep 11 15:58:32 mysystem kernel: [27304.164000] wifi0: Use hw queue 1 for WME_AC_BE traffic
Sep 11 15:58:32 mysystem kernel: [27304.164000] wifi0: Use hw queue 0 for WME_AC_BK traffic
Sep 11 15:58:32 mysystem kernel: [27304.164000] wifi0: Use hw queue 2 for WME_AC_VI traffic
Sep 11 15:58:32 mysystem kernel: [27304.164000] wifi0: Use hw queue 3 for WME_AC_VO traffic
Sep 11 15:58:32 mysystem kernel: [27304.164000] wifi0: Use hw queue 8 for CAB traffic
Sep 11 15:58:32 mysystem kernel: [27304.164000] wifi0: Use hw queue 9 for beacons
Sep 11 15:58:32 mysystem kernel: [27304.176000] wifi0: Atheros 5418: mem=0xedf00000, irq=22
... snip ...
Sep 11 16:52:10 mysystem dhclient: Internet Systems Consortium DHCP Client V3.0.4
Sep 11 16:52:10 mysystem dhclient: Copyright 2004-2006 Internet Systems Consortium.
Sep 11 16:52:10 mysystem dhclient: All rights reserved.
Sep 11 16:52:10 mysystem dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Sep 11 16:52:10 mysystem dhclient: 
Sep 11 16:52:10 mysystem dhclient: wifi0: unknown hardware address type 801
Sep 11 16:52:10 mysystem ntpdate[26225]: the NTP socket is in use, exiting
Sep 11 16:52:11 mysystem dhclient: wifi0: unknown hardware address type 801
Sep 11 16:52:11 mysystem dhclient: Listening on LPF/ath0/00:16:cf:af:c2:97
Sep 11 16:52:11 mysystem dhclient: Sending on   LPF/ath0/00:16:cf:af:c2:97
Sep 11 16:52:11 mysystem dhclient: Sending on   Socket/fallback
Sep 11 16:52:15 mysystem dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
Sep 11 16:52:21 mysystem dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
Sep 11 16:52:29 mysystem dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
Sep 11 16:52:41 mysystem dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
Sep 11 16:52:46 mysystem dhclient: No DHCPOFFERS received.
Sep 11 16:52:46 mysystem dhclient: No working leases in persistent database - sleeping.
Sep 11 16:52:46 mysystem avahi-autoipd(ath0)[26277]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 109).
Sep 11 16:52:46 mysystem avahi-autoipd(ath0)[26277]: Successfully called chroot().
Sep 11 16:52:46 mysystem avahi-autoipd(ath0)[26277]: Successfully dropped root privileges.
Sep 11 16:52:46 mysystem avahi-autoipd(ath0)[26277]: fopen() failed: Permission denied
Sep 11 16:52:46 mysystem avahi-autoipd(ath0)[26277]: Starting with address 169.254.9.189
Sep 11 16:52:51 mysystem avahi-autoipd(ath0)[26277]: Callout BIND, address 169.254.9.189 on interface ath0
Sep 11 16:52:55 mysystem avahi-autoipd(ath0)[26277]: Successfully claimed IP address 169.254.9.189
Sep 11 16:52:55 mysystem avahi-autoipd(ath0)[26277]: fopen() failed: Permission denied
Sep 11 16:52:55 mysystem ntpdate[26301]: the NTP socket is in use, exiting

```


SOLVED:
The newest version of the madwifi drivers from svn have fixed this problem.

---

### Post by tech_log on 2007-09-12
Hi, I have exactly the same problem. 

I have Atheros chipset 5418. Using madwifi-ng (latest SVN or even older)
IBM Lenovo T60 2007-FVG

I tried: 

Fedora 7.02 (from DVD no update, updated without new kernel and fully updated with new kernel)- will get the same message

Ubuntu Feista - same message

hopelly somebody find answer to this. 

(anyway old version can't find which one was it of madwifi-ng was working fine with Fedora 7.02 no problem with patching for aircrack and working in monitor mode. 

Brian

---

### Post by tech_log on 2007-09-12
Hi, it's working again!!

All you have to do is go for SVN Madwifi-ng ver. 2695 and everything will work again!! I tried always to use the newest one and had a problem.

Brian

---

### Post by bismark on 2007-09-12
> **tech_log said:**
> Hi, it's working again!!

All you have to do is go for SVN Madwifi-ng ver. 2695 and everything will work again!! I tried always to use the newest one and had a problem.

Brian

Thanks, trying that revision to see what I can get working.

---

### Post by bismark on 2007-09-12
Still not working even with svn 2695.  

With 2695 I can't even stay associated.  It connects for a few seconds and then jumps modes\channels\etc.

---

### Post by tech_log on 2007-09-14
I tried to delete my working version and compile the latest  and went back to 2695 as you did and it didn't work. So I reinstall the OS and install with old svn 2695 and it works again. But don't understand why it didn't work when I tried to upgrade and then downgrade. The working kernel for me is: 2.6.21-1.3194
Don't go to newer because with a newer one is problem with packet injection. Brian.

---

### Post by bismark on 2007-09-14
Mine is working again with svn 2695 and the generic 2.6.20-16 kernel.

I deleted all atheros modules then rebuild the svn ones, installed them, rebooted, reinstalled dhclient and now it seems to work.

---

### Post by Narkolas on 2007-10-14
Where/how do you get that version 2695?

i have the same problem with 2.6.22-14-generic

Using madwifi 2744

---

### Post by bolan on 2007-10-21
Hi!
I'm a ubuntunoob.
My wireless network doesn't work and I need a guide to install madwifi and get it to work.
I use the new 7.10 ubuntu.

---

