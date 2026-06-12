---
title: "turning on wifi without a working desktop environment"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by ray field on 2014-08-24
Problems arose when my Unity desktop (under Chrubuntu in an Acer 720P Chromebook) became non-functional -- neither the launcher nor the panel would start up. In my haste to fix this problem eventually I started a terminal session and purged Compiz/Unity, with the intention of reinstalling. Unfortunately, I had forgotten that the last time I'd booted, I'd turned off wifi with Network Manager, and this Chromebook hasn't got an ethernet port, so I had no way of reinstalling via apt-get (which will be another headache). 

For now, iwconfig gives

```
wlan0	IEE 802.11abgn ESSID:off/any
	Mode: Managed  Access Point: Non-Associated  Tx-Power=off
	Retry  long limit:7 RTS thr:off  Fragment thr:off
	Power Management:off

```
when I run

```
sudo iwconfig wlano0 essid XXXXXX key s:xxxxxxx
```

first I get "unable to resolve host Xxxxxx" (another issue) but I still don't seem to be connected -- the only difference in the result of iwconfig is ESSID:XXXXXX.

clearly I am flailing around in the dark here.

---

### Post by praseodym on 2014-08-24
> ```
Tx-Power=off
```
The card is turned off. Please run

```
echo "options acer_wmi wireless=1" | sudo tee /etc/modprobe.d/acer_wmi.conf 
```
Reboot and check:
```
sudo rfkill unblock all
rfkill list
```

---

### Post by ray field on 2014-08-24
many thanks.

now I'm a little further along, but I can't seem to get anything out of the connection.

here's what it looks like

```
raphael@Cottard:~$ sudo ifconfig wlan0 up
sudo: unable to resolve host Cottard
SIOCSIFFLAGS: Operation not permitted due to RF-kill
raphael@Cottard:~$ sudo rfkill unblock all
sudo: unable to resolve host Cottard
raphael@Cottard:~$ sudo iwconfig wlan0 essid XXXXX key s:yyyyyyyyyyyy
sudo: unable to resolve host Cottard
raphael@Cottard:~$ sudo dhclient wlan0 &
[1] 2104
```

awesome!  but when I try 

```
sudo apt-get-install unity
```

I keep getting "Could not resolve archive.ubuntu.com"

what am I missing?

---

### Post by praseodym on 2014-08-25
Please check
```

cat /etc/resolv.conf
route -n
arp -v
ifconfig -a
cat /etc/network/interfaces
```

---

### Post by ray field on 2014-08-26
```
$ cat /etc/resolv.conf
nameserver 192.168.1.1
options single-request timeout:1 attempts:5

$ route -n
Kernel IP routing table
Destination 	Gateway	Genmask	Flags Metric Ref	Use Iface

$ arp -v
Entries: 0 	Skipped: 0	Found 0

$ ifconfig -a
io	Link encap:Local Loopback
	inet addr:127.0.0.1 Mask:255.0.0.0
	inet6 addr: ::1/128 Scope:Host
	UP LOOPBACK RUNNING MTU:65536  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wlan0	Link encap:Ethernet HWaddr xxxxxxxxxxxx
	BROADCAST MULTICAST  MTU1500 Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

$ cat /etc/network/interfaces
	#interfaces(5) file used by ifup(8) and ifdown(8)
	#include files from /etc/network/interfaces.d:
	source-directory /etc/network/interfaces.d


```

---

### Post by praseodym on 2014-08-26
The "interfaces" lacks the loopback interface:
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
Reboot.

---

