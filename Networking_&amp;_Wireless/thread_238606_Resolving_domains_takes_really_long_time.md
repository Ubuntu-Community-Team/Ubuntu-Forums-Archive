---
title: "Resolving domains takes really long time"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by Greg_L on 2006-08-17
Hi,

I have recently installed Dapper (6.06.1) on my Compaq nc6400 laptop and was very impressed with the fact that all the big things worked out of the box.

The one problem I noticed a couple days after installation is that it takes a long time for a domain to be resolved before any content from that webpages is loaded. This happens both in Firefox and when apt-get is trying to download some pacakge.

It litteraly takes 10 seconds for a page to load sometimes. However, once news.yahoo.com finally loads going to another page within that domain happens at a normal speed.

I've also tried getting the IP address for various domains and loading the IP instead of the domain in Firefox and it loads instantenously.

Rebooting into Windows Xp does not show this problem.

The laptop has Intel/Pro Wireless 3945abg

Here it is being detected:
> greg@nc6400:~$ dmesg | grep ipw
[17179595.996000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.5m
[17179595.996000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179596.668000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[17179597.676000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)


> 
greg@nc6400:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 0106: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 714a
0000:02:06.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:02:06.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:02:06.3 0805: Texas Instruments: Unknown device 803c
0000:02:06.4 Communication controller: Texas Instruments: Unknown device 803d
0000:08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express (rev 21)
0000:10:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)


The problem happens with or without NetworkManager running.

Please let me know if some other information would be helpful.

Thanks,
Greg.

---

### Post by ape on 2006-08-18
Greg,

  Check your /etc/resolv.conf file and verify that the name server(s) listed there are the same that are listed when running under Windows.

  Is your machine getting it's network config via DHCP or are you statically configuring everything?

---

### Post by spd106 on 2006-08-18
It might be worth disabling IPv6 in firefox. Go to about:config and toggle network.dns.disableIPv6 to true.

---

### Post by Greg_L on 2006-08-19
> **ape said:**
> Greg,

  Check your /etc/resolv.conf file and verify that the name server(s) listed there are the same that are listed when running under Windows.

  Is your machine getting it's network config via DHCP or are you statically configuring everything?

At the moment the problem seems to have gone away. All domains that I try seem to resolve almost instantly.

The resolv.conf contains only a single line and no name servers:
```

greg@nc6400:~$ cat /etc/resolv.conf
nameserver 192.168.1.1

```

and yes the config is done using DHCP.

If the problem returns in the future I'll reply to this thread.

(Connected without network-manager right now.)

---

