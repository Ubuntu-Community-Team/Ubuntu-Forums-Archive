---
title: "Ubuntu 8.1 64-bit, Atheros AR928X &amp; ATH9K Problems ..."
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by oxsyn on 2008-11-02
I have an Asus M70 laptop with an Atheros AR928X Atheros card.  It uses the ATH9K wireless driver.  I installed 8.1 RC x64, but check my system for updates/patches every day.

When I attempt to connect to an access point, I get time out error messages.  I've tried several different access points.

> $ dmesg | grep wlan0
[ 29.762849] wlan0: authenticate with AP 00:02:8a:78:c0:08
[ 29.764550] wlan0: authenticated
[ 29.764552] wlan0: associate with AP 00:02:8a:78:c0:08
[ 29.766273] wlan0: RX AssocResp from 00:02:8a:78:c0:08 (capab=0x421 status=0 aid=233)
[ 29.766274] wlan0: associated
[ 30.953073] wlan0: disassociating by local choice (reason=3)
[ 35.424125] wlan0: No ProbeResp from current AP 00:02:8a:78:c0:08 - assume out of range
[ 95.628523] wlan0: authenticate with AP 00:1c:10:19:86:c7
[ 95.828043] wlan0: authenticate with AP 00:1c:10:19:86:c7
[ 96.028104] wlan0: authenticate with AP 00:1c:10:19:86:c7
[ 96.228081] wlan0: authentication with AP 00:1c:10:19:86:c7 timed out
[ 120.653270] wlan0: authenticate with AP 00:1c:10:19:86:c7
[ 120.852076] wlan0: authenticate with AP 00:1c:10:19:86:c7
[ 121.052082] wlan0: authenticate with AP 00:1c:10:19:86:c7
[ 121.252122] wlan0: authentication with AP 00:1c:10:19:86:c7 timed out
[ 139.517262] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 214.836220] wlan0: authenticate with AP 00:1c:10:19:86:c7
[ 215.032079] wlan0: authenticate with AP 00:1c:10:19:86:c7
[ 215.232079] wlan0: authenticate with AP 00:1c:10:19:86:c7
[ 215.432078] wlan0: authentication with AP 00:1c:10:19:86:c7 timed out 
> $ dmesg | grep wlan0
[ 27.427978] wlan0: authenticate with AP 00:02:8a:78:c0:08
[ 27.437924] wlan0: authenticated
[ 27.437927] wlan0: associate with AP 00:02:8a:78:c0:08
[ 27.439474] wlan0: RX AssocResp from 00:02:8a:78:c0:08 (capab=0x421 status=0 aid=225)
[ 27.439477] wlan0: associated
[ 27.451352] wlan0: disassociating by local choice (reason=3)
[ 48.243550] wlan0: No ProbeResp from current AP 00:02:8a:78:c0:08 - assume out of range
[ 120.436805] wlan0: authenticate with AP 00:02:8a:78:c0:08
[ 120.637044] wlan0: authenticate with AP 00:02:8a:78:c0:08
[ 120.846574] wlan0: authenticate with AP 00:02:8a:78:c0:08
[ 121.044072] wlan0: authentication with AP 00:02:8a:78:c0:08 timed out
[ 162.700688] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14806.247910] wlan0: authenticate with AP 00:02:8a:78:c0:08
[14806.445045] wlan0: authenticate with AP 00:02:8a:78:c0:08
[14806.644083] wlan0: authenticate with AP 00:02:8a:78:c0:08
[14806.844074] wlan0: authentication with AP 00:02:8a:78:c0:08 timed out 
> $ lspci | grep Ath
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
> $ lsmod | grep ath9k
ath9k 296120 0
mac80211 253440 1 ath9k

---

### Post by oxsyn on 2008-11-06
Turns out that this has something to do with the Wireless & Bluetooth being on the same chip (or perhaps not, still working on it).  In /sys/devices/platform/asus-laptop/ there are two files that I had to modify in order to make this work:

/sys/devices/platform/asus-laptop/bluetooth
/sys/devices/platform/asus-laptop/wlan

They each contain a single boolean value.  The bluetooth value contained a 1 and the wlan contained a 0.  You cannot modify this values while your system is running, therefore, the solution was to add two lines to my /etc/rc.local file:

echo 0 > /sys/devices/platform/asus-laptop/bluetooth # disable bluetooth
echo 1 > /sys/devices/platform/asus-laptop/wlan # enable wireless

As soon as I restarted, it came up with absolutely no problems.  

Now, it may be that they can both be enabled at the same time, I haven't tested that far yet.

---

### Post by godsbane on 2008-12-25
Whoo, kickass. Worked out great on a new laptop I bought my fiancée for Christmas.

Thanks a lot for figuring this out.

Her laptop is an Asus N50v for future reference.

---

