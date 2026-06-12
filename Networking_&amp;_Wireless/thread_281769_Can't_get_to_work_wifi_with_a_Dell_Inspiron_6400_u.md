---
title: "Can't get to work wifi with a Dell Inspiron 6400 using Kubuntu Dapper"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by Gustavo Narea on 2006-10-21
Hi.

I've been trying to set up the wifi at home, but it doesn't seem to be that easy. I've followed several how-tos, but they don't (completely) work for me ([howto1]("http://www.ubuntuforums.org/showthread.php?t=257684")* and [howto2]("http://ubuntuforums.org/showthread.php?t=274915")): The wifi led is always off and I can't connect to the Internet. In addition, the kubuntu's startup takes about 1 minute at "Configuring network interfaces" (this happens after following the howtos).

I'm using a Dell Inspiron 6400 along with a Broadcom 4311 running Kubuntu 6.06.

Please take a look at these outputs and the attached screenshot:

```
gustavo@valencia:~$  lspci | grep Broadcom\ Corporation
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
gustavo@valencia:~$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present
gustavo@valencia:~$ iwlist wlan0 scanning
wlan0     No scan results
gustavo@valencia:~$ sudo ifup wlan0
Password:
ifup: interface wlan0 already configured
gustavo@valencia:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:A7:F0:19
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fea7:f019/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5634679 (5.3 MiB)  TX bytes:1171302 (1.1 MiB)
          Interrupt:209

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CF:21:17:1F
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Memory:dfdfc000-dfe00000
gustavo@valencia:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid [COLOR="Red"]{my_ssid}[/COLOR]
wireless-key s:[COLOR="Red"]{my_key1}[/COLOR]

```

And, of course, the wireless modem is on and WLAN is active.

Thanks in advance.

* After its step 17 (of the section "wireless"), the wifi led should turn on, but it didn't happen.

---

### Post by Gustavo Narea on 2006-10-21
I don't know what I did, but now it works :confused:!

Thanks anyway!

---

