---
title: "wireless problem: interface does not exist"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by iltuje on 2008-05-01
Hi, 

I've been having a few issues since I upgraded to Hardy. 

First, On boot I get 

Error 18: Selected cylinder exceeds maximum supported by bios


I bypass this by selecting the second ubuntu entry (an earlier version) in GRUB. Then all works fine, but I figure that's not good.

My main problem now is with wireless. Yesterday I couldn't get my home wireless to work, and got error messages such as 

"Could not find info on interface 'ath0:avahi' in proc/net/dev

Aftew three hours of fiddling, I could get both my wireless and wired connections at work to function properly, but it seems like any settings modification brings down everything.

If I try to configure eth0 or ath0, I still get the error message "the interface does not exist.

So I will stop fiddling now, since things are currently working, but if someone has an idea of what might be the problem I'd be curious. 

All the problems started after I plugged in a new external hard drive (which otherwise worked fine, I don't know that this is related)


here are a few diagnostic calls:

```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"ccmr.cornell.edu"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:06:25:3C:2B:28   
          Bit Rate:18 Mb/s   Tx-Power:14 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/94  Signal level=-54 dBm  Noise level=-91 dBm
          Rx invalid nwid:125170  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.


```

```
~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 17009
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/ath0/00:05:4e:47:20:07
Sending on   LPF/ath0/00:05:4e:47:20:07
Listening on LPF/eth0/00:0d:60:c9:90:9d
Sending on   LPF/eth0/00:0d:60:c9:90:9d
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 8
DHCPREQUEST of 132.236.95.112 on ath0 to 255.255.255.255 port 67
DHCPACK of 132.236.95.112 from 128.84.231.24
bound to 132.236.95.112 -- renewal in 1761 seconds.

```



```
~$ more /etc/network/interfaces
auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```


```

:~$ more /proc/interrupts
           CPU0       
  0:    1709599    XT-PIC-XT        timer
  1:         10    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  6:          5    XT-PIC-XT        floppy
  7:          4    XT-PIC-XT        parport0
  8:          3    XT-PIC-XT        rtc
  9:       5389    XT-PIC-XT        acpi
 11:    1083658    XT-PIC-XT        uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3,
 ehci_hcd:usb4, yenta, yenta, wifi0, Intel 82801DB-ICH4, radeon@pci:0000:01:00.0
, eth0
 12:       2337    XT-PIC-XT        i8042
 14:      86968    XT-PIC-XT        libata
 15:      74823    XT-PIC-XT        libata

```

Any help appreciated!

S

---

### Post by Jack Waugh on 2008-08-26
I don't know about the wireless problem (I came across your message while looking for information about the "the interface does not exist" problem); however, in respect of your getting the message about a cylinder beyond the reach of the BIOS when you try to boot, I'm thinking you might be able to solve it, if you can figure out a way to repartition your disk without loosing any files, by moving all of /boot to a little partition at the beginning of your disk, then whatever magic it takes to convince Grub to install itself in the master boot record, etc., so it will run from the little partition and get the kernel and initrd from there as well (I had trouble trying to do that myself, on an external disk, so I haven't quite understood all the aspects of installing Grub).

---

