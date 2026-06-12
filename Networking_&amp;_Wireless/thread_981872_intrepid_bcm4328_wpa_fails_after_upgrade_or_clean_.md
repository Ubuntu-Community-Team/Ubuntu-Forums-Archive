---
title: "intrepid bcm4328 wpa fails after upgrade or clean install"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by Habanero999 on 2008-11-14
Hi all,

I recently upgraded my Dell XPS m1530 from Hardy to Intrepid, whilst mostly smooth my wireless stopped working.

On Hardy I was using ndiswrapper with bcmwl5 as the driver, after I tried both STA wl restricted driver and ndiswrapper bcmwl5 with the same result I have seen in other posts; that Network Manager keeps prompting for the WPA PSK.

Using wpa_passphrase comfirms that the passphrase is correct, the blue LED light is on indicating wireless is active, and I get full signal strength seen in Network Manager - I just installed wicd to see if that would work but see the same thing - except does not prompt again - just fails to connect silently.

excerpt from /var/log/wpa_supplicant.log:
Trying to associate with SSID 'EXAMPLESSID'
Authentication with 00:00:00:00:00:00 timed out.

I haven't been able to try without WPA as the wireless network is in constant use, and I'd rather not, it seems that something broke since upgrade, my suspicion is with wpa_supplicant since the same ndiswrapper driver and config which was working with Hardy no longer does...

Some details:

uname -r
2.6.27-7-generic

lspci -nn | grep -i bcm
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)

lshw -C network
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 03
       serial: 00:23:4d:26:30:7f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11

Any thoughts / suggestions / help would be most appreciated, and any further info required please let me know.

Many thanks 

Hab

---

### Post by akshayas1986 on 2008-11-14
I am having the same problem too. Two things that always get affected by an upgrade are: 1. my nVIDIA display driver 2. my Broadcom Wi-Fi driver.

---

