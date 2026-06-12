---
title: "Updated DHCP and eth0 vanished?????"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by Tuxgrrrl on 2007-01-25
Morning ALL.
I started to set up a straight ethernet connect between a Kubuntu Edgy laptop and an Ubuntu Edgy desktop via their working [verified] rj45 connectors.
Satisfied the NICs worked I tasked Synaptic with bringing on the latest DHCP and went to tea.
I returned and went right to Network-admin and [viola] no NIC???? I went to network tools found lo and wlan0, ppp0 and wmaster0 but eth0 is nowhere to be found?????

I get: ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device

dhclient eth0
eth0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
xxxx@xxxxx:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8276 (8.0 KiB)  TX bytes:8276 (8.0 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:209.206.169.139  P-t-P:69.29.184.32  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:5457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:3987991 (3.8 MiB)  TX bytes:692013 (675.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:13:D3:70:AB:80
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:108 (108.0 b)
          Base address:0xb000

wmaster0  Link encap:UNSPEC  HWaddr 00-13-D3-70-AB-80-00-B0-00-00-00-00-00-00-00             -00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xb000

/etc/network/interfaces:
# The primary network interface - use DHCP to find our address

auto eth0
iface eth0 inet dhcp

iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto lo

iface ppp0 inet ppp
provider ppp0

auto ppp0



Searching for eth0 in Konqueror I dont find /dev/eth0
and I dont know enough to tell it to undo what was done nor how to create the device eth0 ....


I have searched the forum and google but not found how. They all say find it in Network Manager but of course it isnt there and ....


Thanks for your time.

---

### Post by Nik_Doof on 2007-01-25
sounds like either a module isn't configured for device.

Try this:

```

modprobe eth0
ifup eth0
```

---

### Post by Tuxgrrrl on 2007-01-26
Greetings Nik, thanks for your time.

 No and I dont know how to undo it either.
I think I can remember the packages that were installed/updated but I doubt that will restore everything even if I could ....

I searched for a couple hours on how to make or create a new eth0 but didnt find out how.

lspci shows it there so Im guessing some file some place got stompED some wA....

Id be greatful for a lead or instuctions to recreate the ?device files?

modprobe eth0:

FATAL: Module eth0 not found.



sudo ifup eth0:

There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth0.



Thanks again.

---

### Post by Mattihan on 2007-02-08
Hi-

I know it's been a week since the last post, but I thought since I found this and had the same problem, others might as well.

I had almost exactly the same problem, though my eth0 went funky after a crash which might or might not have been caused by automatic updates. I was getting the same errors for modprobe and ifup. I'm also using the same dhcp client version.

I was able to fix this by moving the nic onto a different pci slot. It then redetected it and set it up again automatically thru dhcp. If you have an onboard nic, I might suggest trying to disable it from the bios, start into ubuntu, restart and reenable the nic again and see if that doesn't make a difference. 

Good luck, and I hope if you are reading this that it has helped.

---

### Post by Tuxgrrrl on 2007-02-09
Greetings Mattihan.
Thank you very much for your time

My partner says we tried that but we will try it again and see if we get any thing.
We will post back if it works.

EDIT - It turns out the reason it didnt work is that the BIOS dosent have any function to interact with the NIC or any other components! Can you believe that? Calls to the manufacturer and their web sites got us nowhere. They wont even tell you the make or model of the NIC! Grrrrrr  As far as they are concerned we should only use windows. Back to bit zero.... - EDIT

Thanks again for your time.

---

