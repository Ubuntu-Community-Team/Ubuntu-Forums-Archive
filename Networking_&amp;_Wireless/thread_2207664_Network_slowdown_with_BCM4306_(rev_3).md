---
title: "Network slowdown with BCM4306 (rev 3)"
date: 2014-02-24
forum: Networking &amp; Wireless
---

### Post by James_Marvin on 2014-02-24
Hello,

I am using the b43 driver on ubuntu 13.10 to run my BCM4306 (rev 3). I got it running using the instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Switching_between_drivers").

My issue is that when I am using the wireless on this computer, often the performance is poor - downloads restricted to 34kpbs where realistically they could be as high as 1,300. Beyond this, other devices suffer internet slowdowns when this computer is connected - Confirmed through shutting the computer off.

lspci -vnn -d 14e4: reveals:

```
01:07.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
Subsystem: Linksys WMP54G v1 802.11g PCI Adapter [1737:0013]
Flags: bus master, fast devsel, latency 32, IRQ 19
Memory at efcfe000 (32-bit, non-prefetchable) [size=8K]
Kernel driver in use: b43-pci-bridge
```

Is there anything I can do (beyond replacing this card)?

Thanks

---

### Post by varunendra on 2014-02-25
Welcome to the forums James!

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It will give us a detailed information about your wireless setup, so we can see if there are things we can tweak to optimize the performance.

And are you sure the current speed is 34 K**b**ps, not K**B**ps? That is indeed terribly slow!

---

### Post by James_Marvin on 2014-02-26
Thanks for the response. 

As requested: [http://pastebin.com/uKK2eKqn](http://pastebin.com/uKK2eKqn)

---

### Post by varunendra on 2014-02-26
A few suggestions, try them one at a time, going from point 1 to the last. You may revert any of the changes that don't help, but it is recommended to keep the encryption type as suggested, unless it is causing more trouble (which I believe it won't).

**1)** Please change the encryption type in the router from WPA-TKIP to WPA**2**-AES(CCMP).
**2)** Try changing the channel to 1 or 11. Currently it is set to channel 2 (and the other one at 10).
**3)** In Network Manager, make sure the 'Method' for **IPv6** is set to "**Ignore**".
**4)** In Network Manager, set the 'Method' for **IPv4** to "**Automatic (DHCP) address only**", and then in the "DNS servers" field, enter **8.8.8.8, 8.8.4.4** as DNS servers. Save & Close.
**5)** As a test, try disabling UFW -
```
sudo ufw disable
```
*(by the way, are you sure it is configured properly? There seems to be a lot of blocked traffic.)*

Make sure to reboot the router after making any changes, and either reboot the computer too or give it 5 to 10 minutes before judging whether the change helped or not.
If none of these seem to help, please post back a fresh report of the wireless_script with all the suggestions implemented.

---

### Post by James_Marvin on 2014-02-28
Hello and thanks again for your help!

I have tried the IPv6 set in the instructions you gave but have not yet been able to properly gauge if this has made a difference. However...

I recently ran DMESG regarding a completely separate issue and saw and number of UFW-related entries regarding blocked connection attempts from the only other desktop on the network - my friend's Mac:

```
[10041.037446] [UFW BLOCK] IN=wlan0 OUT= MAC=MACREMOVED SRC=192.168.2.13 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=12624 PROTO=UDP SPT=59744 DPT=8612 LEN=24 
```

Infact, the dmesg output was absolutely filled with these. Is this a possible explanation for the network issues? The issue also seems to affect HIS computer when mine is online.

Thanks

---

### Post by varunendra on 2014-02-28
> **James_Marvin said:**
> Infact, the dmesg output was absolutely filled with these. Is this a possible explanation for the network issues?

Quite possibly. The 5th point in my previous post addresses that issue. The firewall (ufw) is disabled by default in Ubuntu. So if you didn't turn it on deliberately, then it most probably IS the cause. Just try what I suggested in the previous post and see if it makes a difference.

---

