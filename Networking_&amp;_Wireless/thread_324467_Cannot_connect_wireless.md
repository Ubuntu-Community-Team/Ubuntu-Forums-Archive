---
title: "Cannot connect wireless"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by tugh on 2006-12-23
Hi,

I'm a new Ubuntu user and I cannot connect to internet thru wireless connection. I was able to connect until couple days ago, and then the Ath0 option suddenly disappeared.:-k 

Under network settings, I can see the Essid name recognized and the password is already entered under properties. However, when I go to Connection Properties, "lo" is the only option to select. Ath0 used to be there before for selection.

I know the router works because my desktop, which has Windows, is already connected.

Is there anybody out there who has a suggestion?

Thank you!

---

### Post by scrooge_74 on 2006-12-23
sudo ifdown ath0
sudo ifup ath0

---

### Post by dbott67 on 2006-12-23
Also, can you post the output of the following commands:
```
ifconfig -a
```
and
```
cat /etc/network/interfaces
```

Thanks,
Dave

---

### Post by tugh on 2006-12-25
I tried ifdown and ifup, but didn't work. It says "No dhcpoffers received". Ath0 still doesn't show up.

ifconfig -a brings:

ath0
link encap:Ethernet HWaddr 00:0e:9b:1f:50:AA
inet6 addr: fe80::20e:9bff:felf:50aa/64 scope:link
up broadcast running multicast mtu:1500 metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0

eth0
link encap:Ethernet HWaddr 08:00:46:E7:DD:10
up broadcast running multicast mtu:1500 metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 b)
interrupt:3 base address:0x2c00

lo
link encap: local loopback
inet addr:127.0.0.1 mask:255.0.0.0
inet6 addr: ::1/128 scope:host
up loopback running mtu:16436 Metric:1
RX packets:2 errors:0 dropped:0 overruns:0 frame:0
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:100 (100.0 B) TX bytes:100 (100.0 b)

sit0
link encap:IPv6-in-IPv4
NOARP MTU:1480 metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 b)

wifi0
Link encap:UNSPEC HWaddr 00-0e-9b-1f-50-aa-00-00-00-00-00-00-00-00-00-00
up broadcast running multicast mtu:1500 metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:199
RX bytes:0 (0.0 B) TX bytes:630531 (615.7 Kib)
interrupt:11 memory:dca40000-dca50000

====

cat /etc/network/interfaces brings:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface ah0 inet dhcp
wireless-essid 2W-DOMU
wireless-key 1a1a1a1a1b1b1b1b1c1c1c1c1d

auto ath0

=====

That's it. What does these mean?

---

### Post by tugh on 2006-12-25
Btw, when I type sudo iwlist scan, it says "no scan results" for ath0

---

### Post by spd106 on 2006-12-25
Check that the linux-restricted-modules package is installed in the Synaptic Package Manager. Also try checking the output of running these commands **lsmod | grep ath** and **dmesg | grep ath**

---

### Post by Floppyjoe on 2006-12-25
When you listed the reply to the cat command:
> cat /etc/network/interfaces brings:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface ah0 inet dhcp
wireless-essid 2W-DOMU
wireless-key 1a1a1a1a1b1b1b1b1c1c1c1c1d

auto ath0


It looks like it should say:
> cat /etc/network/interfaces brings:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface ath0 inet dhcp
wireless-essid 2W-DOMU
wireless-key 1a1a1a1a1b1b1b1b1c1c1c1c1d

auto ath0

I added a letter t into the ah0 interface in the line:
> iface ah0 inet dhcp

so you need to enter into the terminal:
```
sudo gedit /etc/network/interfaces
```
and change it to ath0

Then restart the computer.

I hope this helps.

---

### Post by tugh on 2006-12-25
linux-restricted-modules look installed. There are 3 of them, 2.6.17.10-generic, common, and generic.

lsmod|grep ath shows:
ath_pci                 100000  0
ath_rate_sample     16512  1 ath_pci
wlan                     207580  5 wlan_wep_wlan_scan_sta,ath_pci,ath_rate_sample
ath_hal                 192976  3 ath_pci,ath_rate_sample

dmesg|grep ath shows:
[17179589.068000] ath_hal: module license 'proprietary' taints kernel
[17179589.072000] ath_hal: 0.9.17.2 (ar5210, ar5211, ar5212, rf5111, rf5112, rf2413, rf5413)
[17179589.260000] ath_rate_sample: 1.2 (0.9.2)
[17179589.264000] ath_pci:0.9.4.5 (0.9.2)
[17179620.424000] ath0: no IPv6 routers present
[17180721.592000] ath0: no IPv6 routers present

---

### Post by tugh on 2006-12-25
Floppyjoe, it actually was Ath0. That was just my typo, since i'm keying these in manually.

---

### Post by Floppyjoe on 2006-12-25
What is the result of:
```
iwconfig
```
can you post this?

---

### Post by tugh on 2006-12-25
This is iwconfig:

lo       no wireless extensions
eth0   no wireless extensions
wifi0  no wireless extensions
ath0  ieee 802.11g essid:"2W-DOMU"
        mode:managed  frequency:2.432ghz access point:not-associated
      bit rate:0 kb/s tk-power:17dbm sensitivity:0/3
      retry:off  rts thr:off fragment thr:off
   power management:off
     link quality: 0/94  signal level:=-95 dbm
   rx invalid nwid:0 rx invalid crypt:0 rx invalid frag:0
    tx excessive retries:0 invalid misc:0 missed beacon:0

site0  no wireless extensions

---

### Post by tugh on 2006-12-25
I don't know how but after my last reboot, now it works!!! 

Thank you to all of you who take time to solve the problem.

---

