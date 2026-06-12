---
title: "Kali VM, TP-Link wifi usb adapter issue, Ubuntu Host won't let Guest OS use wifi"
date: 2014-01-06
forum: Networking &amp; Wireless
---

### Post by ahobo on 2014-01-06
I've been trying to get this Wireless USB adapter working in Kali VM with Virtualbox, but I believe the host has a hold of it and won't let it go.
So I would like to know how to unmout the Wireless USB Adapter from Ubuntu so that the guest OS can grab it.

**Info:**
Compy: Acer E1-572 laptop
Host: Ubuntu amd64 13.10
Guest: Kali on Virtualbox 4.3.6
```
$:uname -a
Linux kali 3.7-trunk-amd64 #1 SMP Debian 3.7.2-0+kali8 x86_64 GNU/Linux
```
Virtualbox guest additions and extensions are both installed.

**Wireless USB**: TP-Link [TL-WN722N]("http://wikidevi.com/wiki/TP-LINK_TL-WN722N")

**Issues**:
No wlan* found in Kali, but device is found in *lsusb*.

**Troubleshooting**:
I've tried (in Kali) -- downloading and copying the firmware, compiling the firmware from backports' source, installing the drivers, removing & adding from modprobe, etc...
A lot of users say this adapter is just plug and play with Kali -- and it seems that it already had the firmware and drivers, so I don't think firmware is the issue.
--------------
If I plug in the USB before launching Virtualbox, then the green light comes on the USB adapter and it works fine on the Ubuntu side.
I tried the following: to try and unmount it from Ubuntu, which removes wlan1, but still seems connected to the host:
```
sudo ifconfig wlan1 down
```
--------------
If I plug it in after launching Virtualbox, then it shows up in Kali with *lsusb*, but will not initialize.
*dmesg* says, "ath9k_htc: Target is unresponsive"

logs in Kali:
[dmesg (snipped)]("http://pastebin.com/JzkryiU2")
[dmesg (full)]("http://pastebin.com/2Qt0Yiy4")
[lsusb]("http://pastebin.com/2AYtTjXV")
[lsmod]("http://pastebin.com/aqB1eeJc")
[modinfo ath9k_htc]("http://pastebin.com/mTJ37kuj") --- maybe looks a little weird???
--------------
While VB is running, if I do an *lsusb* on the host (Ubuntu) the wireless USB shows up there as well as in Kali:
```
$: lsusb 
Bus 002 Device 024: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n

```
--------------
If I try and Uncheck the USB Sharing in Virtualbox, Kali / VB tends to freeze for a minute -- then if I try and remount, or check to share the USB, then it gives the following error: 
[USB Devices is busy with a previous request.]("http://pastebin.com/buZipGqi")
--------------
My laptop's built-in wireless card is an Atheros chip, and uses the ath9k driver, so I can't delete it or blacklist as a work-around.
```
$: lspci -nn | grep 'Atheros'
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
```
--------------
I've also added the following line to /etc/network/interfaces
```
iface wlan1 inet manual
```

I'm thinking the hangups are on the Ubuntu Host side, in that it still has a hold of of the Wireless USB adapter.
Any help would be appreciated.

---

