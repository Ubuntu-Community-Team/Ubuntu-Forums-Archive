---
title: "WPA and IPW2200 Drivers"
date: 2005-11-25
forum: Networking &amp; Wireless
---

### Post by cpsalvestrini on 2005-11-25
ok, here's the deal: I get this error from doing a standard dmesg | grep ipw after seting up as per the HOWTOs the latest drivers and firmware for my Intel Proset/Wireless adapter:

carlos@charlielaptop:~$ dmesg | grep ipw [4294739.273000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.8
[4294739.273000] ipw2200: Copyright(c) 2003-2005 Intel Corporation
[4294739.279000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294743.449000] ipw2200: Can't set TKIP countermeasures: crypt not set!
[4294818.863000] ipw2200: Unknown notification: subtype=40,flags=0xa0,size=40
[4294886.772000] ipw2200: Unknown notification: subtype=40,flags=0xa0,size=40
[4294949.497000] ipw2200: Unknown notification: subtype=40,flags=0xa0,size=40
[4295019.617000] ipw2200: Unknown notification: subtype=40,flags=0xa0,size=40
[4295089.726000] ipw2200: Unknown notification: subtype=40,flags=0xa0,size=40
[4295139.247000] ipw2200: Firmware error detected.  Restarting.
[4295139.247000] ipw2200: Sysfs 'error' log captured.
[4295169.562000] ipw2200: Firmware error detected.  Restarting.
[4295169.562000] ipw2200: Sysfs 'error' log already exists.
[4295245.250000] ipw2200: Firmware error detected.  Restarting.
[4295245.250000] ipw2200: Sysfs 'error' log already exists.
[4295247.296000] ipw2200: Firmware error detected.  Restarting.
[4295247.296000] ipw2200: Sysfs 'error' log already exists.
[4295250.462000] ipw2200: Firmware error detected.  Restarting.
[4295250.462000] ipw2200: Sysfs 'error' log already exists.
[4295253.436000] ipw2200: Firmware error detected.  Restarting.
[4295253.436000] ipw2200: Sysfs 'error' log already exists.
[4295257.947000] ipw2200: Firmware error detected.  Restarting.
[4295257.947000] ipw2200: Sysfs 'error' log already exists.
[4295274.235000] ipw2200: Firmware error detected.  Restarting.
[4295274.235000] ipw2200: Sysfs 'error' log already exists.
[4295280.377000] ipw2200: Firmware error detected.  Restarting.
[4295280.377000] ipw2200: Sysfs 'error' log already exists.
[4295281.815000] ipw2200: Firmware error detected.  Restarting.
[4295281.815000] ipw2200: Sysfs 'error' log already exists.
[4295289.910000] ipw2200: Firmware error detected.  Restarting.
[4295289.910000] ipw2200: Sysfs 'error' log already exists.
[4295334.234000] ipw2200: Firmware error detected.  Restarting.
[4295334.234000] ipw2200: Sysfs 'error' log already exists.
[4295350.938000] ipw2200: Firmware error detected.  Restarting.
[4295350.938000] ipw2200: Sysfs 'error' log already exists.
[4295394.270000] ipw2200: Firmware error detected.  Restarting.
[4295394.270000] ipw2200: Sysfs 'error' log already exists.

Any ideas for connectivity?

---

### Post by audax321 on 2005-11-25
Have you tried the solution here:
[http://ubuntuforums.org/showthread.php?t=75612](http://ubuntuforums.org/showthread.php?t=75612)

Look for the post by xMetaRidley on the first page. It got rid of the firmware errors for me, but I was using the driver that shipped with Breezy.

---

### Post by UJones on 2007-02-10
Hey all!

I'm a little newbie in the linux world but so far I fixed all problems by myself using google. But now I don't know what to do.
Since the beginning I have problems with my internet connection. It's not that often and I had exams so I hold off on it until now when I have a bit time to get busy with it.
I already searched a lot but it seems many things can cause my error so what is the reason in my case??!?
Maybe you guys can help me to find it *hopefully*

I get the same error messages as cpsalvestrini:
```
johannes@mobile:~$ dmesg | grep ipw
[17179586.576000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17179586.576000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179586.576000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[17179587.256000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[17179587.552000] ipw2200: Detected geography ZZE (13 802.11bg channels, 19 802.11a channels)
[17183442.160000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[17183443.168000] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[17183449.308000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[17183450.316000] ipw2200: Failed to send CARD_DISABLE: Command timed out.
.................
[17184986.128000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[17184987.136000] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[17184991.320000] ipw2200: Firmware error detected.  Restarting.
[17184991.460000] ipw2200: Radio Frequency Kill Switch is On:

```
So generally my internet is working for a unregular period of time and then the signal strength of my wireless connection gets weaker second by second then it's zero and you see how it is trying to restart (signal bar gets a bit green and then empty again).

I tried to fix it as xMetaRidley described it but I don't have a file *ipw2200* in /etc/modprobe.d/ !! I only have this:
```
johannes@mobile:~$ sudo gedit /etc/modprobe.d/
aliases                blacklist-framebuffer  ibm_acpi.modprobe
alsa-base            blacklist-modem        ipw3945
apm                   blacklist-oss               isapnp
arch/                  blacklist-scanner       nvidia-kernel-nkc
arch-aliases        blacklist-watchdog     options
blacklist              bluez                        toshiba_acpi.modprobe
```

I'm using Ubuntu 6.06 Dapper Drake. Here some system information:
**/etc/network/interfaces**
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
	address 192.168.1.3
	netmask 255.255.255.0
	gateway 192.168.1.1
	dns-nameserver 192.168.1.1
	wpa-driver wext
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
auto eth0

```
**/etc/wpa_supplicant/wpa_supplicant.conf**
```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=2

network={
	ssid="essid_of_my_router"
	scan_ssid=1
	proto=WPA2
	key_mgmt=WPA-PSK
	pairwise=TKIP
	group=TKIP
        psk=well.my.key.;)
}
```
**The wireless card I'm using:**
```
johannes@mobile:~$ lspci | grep Wireless
0000:01:07.0 Network controller: Intel Corporation PRO/Wireless 2915ABG MiniPCI Adapter (rev 05) 
johannes@mobile:~$ uname -r
2.6.15-28-386
```

I would be very glad if someone can help out!!!

---

