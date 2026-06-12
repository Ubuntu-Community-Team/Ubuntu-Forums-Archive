---
title: "ipw2100 -- no chance"
date: 2005-04-17
forum: Networking &amp; Wireless
---

### Post by silvercross on 2005-04-17
i nearly lost all my hope.
i won't get my ipw2100 working. no chance... 

**my state:**

```
modprobe ipw2100
```
no error message

```
dmesg grep | ipw 
```
michael@acer:~$ dmesg | grep ipw
ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.0.2
ipw2100: Copyright(c) 2003-2004 Intel Corporation
ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[B]
wpa_supplicant is installed properly.
so are wireless tools.[/B]

```
 cat /etc/wpa_supplicant.conf 
```
network={
       ssid="WINDRUSH"
       proto=WPA
       scan_ssid=1
       key_mgmt=WPA-PSK
       psk="XXX"
}
```

ifconfig eth1 
```

eth1      Link encap:Ethernet  HWaddr 00:04:23:80:BF:72
          inet6 addr: fe80::204:23ff:fe80:bf72/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:85 errors:17 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:3145 (3.0 KiB)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x8000 Memory:d0000000-d0000fff

[COLOR=DarkRed]
no IP adress is assigned to the wlan card.
system: acer aspire 2001 WMLI
centrino ipw2100[/COLOR]

I desperately hope for help, I can't think of any more solutions.

---

### Post by luca_linux on 2005-04-17
Is it just a wpa problem or can't you connect to your access point even without wpa?

---

### Post by silvercross on 2005-04-17
connection without encryption seems to work fine.
i don't have any further knowledge. :(
under win32, fedora and suse no problem emerged with using ipw2100
i was so happy to finall having installed ubuntu.
could there possibly something to check about kernel settings ?
(i am using standard kernel)

---

### Post by silvercross on 2005-04-17
```
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw 
```
Password:
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
michael@acer:~$

---

### Post by luca_linux on 2005-04-18
Try to update your ipw2100 driver to the latest version available at ipw2100.sourceforge.net.
If you want, you can follow my howto at [http://www.ubuntuforums.org/showthread.php?t=26623&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=26623&page=1&pp=10), though it's for ipw2200.

---

