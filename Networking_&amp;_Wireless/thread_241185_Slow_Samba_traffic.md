---
title: "Slow Samba traffic"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by Johan! on 2006-08-22
Compared to the Windows XP installation on this computer (dual boot), Samba traffic in Ubuntu is much slower.

In XP, transfer speeds (upload & download) are approx. 9 MB/sec.
In Ubuntu, the max. speed is 4, sometimes 5 MB/sec.

The Samba server runs Ubuntu 6.06.

I have a 100 Mbit network, and as far as I know, everything else works fine.
The network interface card is integrated on the motherboard (Asus A8N-E)
```
$ lspci | grep Eth
0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
```


The share is mounted by the following line in /etc/fstab
```
//192.168.1.9/shared-server /media/server smbfs noauto,credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0
```
The noauto option is there to fix a hal bug ([https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874](https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874))
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:17:53:71  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fe17:5371/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2571337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1783601 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3305164564 (3.0 GiB)  TX bytes:336222896 (320.6 MiB)
          Interrupt:50 Base address:0x8000

lo etc...
```

/etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

**Why is it slower than XP?**

---

### Post by jethro10 on 2006-08-22
Until recently I would have had no idea. And I still may not.

But I had a similar thing of performance (and reliability).

Mine was that the linux box set an MTU (Maximum Transfer Unit) size

larger that all the rest of the kit.

Fixing this and my speed more than doubled.

It might help ?

Jeff

---

### Post by Johan! on 2006-08-31
The MTU is ok, it's the same as in XP (1500)

I checked the network interface: it's running at 100 Mbit, full duplex.

Checked harddisk performance: DMA is on, transfer speeds are 60 MB/sec.

A SSH connection to the server is also slow, 4 MB/sec.

Yesterday I installed NFS.
I think it working better now, network transfers are at 7-8 MB/sec.
Still a bit slower than XP, but acceptable.

---

