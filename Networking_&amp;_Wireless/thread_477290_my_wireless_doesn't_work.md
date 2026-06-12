---
title: "my wireless doesn't work"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by paolo.komninidis on 2007-06-18
i have an acer travelmate 292LMi laptop. my problem is that i cant access to internet with wireless. here are the outputs that should be needed:

iwconfig:

eth1 radio off ESSID:"SpeedTouch" Nickname:"paulkom"
          Mode:Managed Channel:0 Access Point: Not-Associated
          Bit Rate=0 kb/s Tx-Power=off Sensitivity=8/0
          Retry limit:7 RTS thr:off Fragment thr:off
          Encryption key:7061-7373-776F-7264-0000-0000-00 Security mode:open
          Power Management:off
          Link Quality:0 Signal level:0 Noise level:0
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ifconfig:

eth1 Link encap:Ethernet HWaddr 00:0E:35:1B:49:6A
          UP BROADCAST MULTICAST MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xc000 Memory:d0000000-d0000fff

ifdown eth1:

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:0e:35:1b:49:6a
Sending on LPF/eth1/00:0e:35:1b:49:6a
Sending on Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.254 port 67

ifup eth1:

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:0e:35:1b:49:6a
Sending on LPF/eth1/00:0e:35:1b:49:6a
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

iwlist eth1 scan:

eth1 No scan results

dhclient eth1:

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:0e:35:1b:49:6a
Sending on LPF/eth1/00:0e:35:1b:49:6a
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

i think you dont need anything else.

i have a SpeedTouch router and use ubuntu 6.10.
i cannot understand what the problem might be. thanks in advance

---

### Post by paolo.komninidis on 2007-06-18
found the problem....but not resolved:(

dmesg:

ipw2200: Radio Frequency Kill Switch is On:
Kill switch must be turned off for wireless networking to work

---

### Post by charleseddy on 2007-06-18
> **paolo.komninidis said:**
> 
iwconfig:

eth1 radio off ESSID:"SpeedTouch" Nickname:"paulkom"
          Mode:Managed Channel:0 Access Point: Not-Associated
          Bit Rate=0 kb/s Tx-Power=off Sensitivity=8/0
          Retry limit:7 RTS thr:off Fragment thr:off
          Encryption key:7061-7373-776F-7264-0000-0000-00 Security mode:open
          Power Management:off
          Link Quality:0 Signal level:0 Noise level:0
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0


The part that says "radio off"?  That means your hardware switch is off, and you need to turn it on.

---

### Post by paolo.komninidis on 2007-06-18
i know that i need to turn it on. but how???

---

### Post by charleseddy on 2007-06-18
It's a hardware switch.  You should have a function button or a physical button to turn wireless on. . . .  Not sure on your exact model where it's located.

---

### Post by paolo.komninidis on 2007-06-18
ok now the problem is this:

 dmesg:

Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!

no more problems with radio switch kill.the only thing i had to do is to install acer hot keys
[http://folk.uio.no/krisvh/linux/cl56.html](http://folk.uio.no/krisvh/linux/cl56.html)

---

### Post by charleseddy on 2007-06-18
Pulled this from a similar problem:

> **flixer said:**
> Try this:

1.[Download this file]("http://downloads.sourceforge.net/fsam7440/fsam7440-0.4.tar.bz2?modtime=1177886562&big_mirror=0") unpack it to your home directory /home/username


2. ```

cd fsam7440-0.4 && make && sudo make install

```

3.Read README

Important: You have to do this everytime your kernel changes.

As well as this:

> **automatthias said:**
> Try this:

sudo modprobe acerhk
sudo su -c "echo 1 > /proc/driver/acerhk/wirelessled"

It it works, you can make it permanent by creating hitting alt+f2 and typing 
gedit /etc/modprobe.d/ipw2200 
Then add the two following lines:

options ipw2200 led=1
install ipw2200 /sbin/modprobe acerhk; sleep 1; echo 1 > /proc/driver/acerhk/wirelessled; /sbin/modprobe --ignore-install ipw2200


Save it.


Try these on for size, and get back to me.

---

