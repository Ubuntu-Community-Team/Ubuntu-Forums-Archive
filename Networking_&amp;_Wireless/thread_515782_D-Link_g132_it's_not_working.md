---
title: "D-Link g132 it's not working"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by DardDiablo on 2007-08-02
Hi everybody, I'm new in the forum and I'm also new to ubuntu :). Please frogive my english it's not so good :S, but the important it's what appears on the console! :lolflag:

My problem is that I've done all the steps i read in many posts but nothing has worked :( (my wireless connection still isn't working). Here I report some commands, hope they'll be useful for the soltuion. I've installed [those drivers](http://support.dlink.com/products/view.asp?productid=DWL%2DG132#).

[b]
iwconfig[/b]
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

**lsusb**
```

Bus 005 Device 004: ID 2001:3a03 D-Link Corp. [hex]
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c216 Logitech, Inc. Dual Action Gamepad
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 03f0:1904 Hewlett-Packard DeskJet 3820
Bus 001 Device 001: ID 0000:0000

```

**ndiswrapper -v**
```

utils version: 1.8
driver version:        1.38
vermagic:       2.6.20-15-generic SMP mod_unload 586

```

**ndiswrapper -l**
```

Installed drivers:
neta5agu                driver installed, hardware present

```

Thank you so much for any reply :)

p.s: I've already posted in the italian forum, but I don't know why nobody is answearing me :(
p.p.s: I'm on the last version of Kubuntu

---

### Post by DardDiablo on 2007-08-02
Please let me know if you're interested in the output of the comand **dmesg**, I have it but it's very long, so I'll post it only if it's necessary.

Thanks in advance for the replies ;)

Good night :guitar:

---

### Post by kevdog on 2007-08-02
Can you post the following

Only the part about the wireless usb needs to be included:
lshw -C network

modprobe -l ndiswrapper

Make sure that the word ndiswrapper appears on a single line in the /etc/modules file

Please also post /etc/iftab

Is there a file /etc/modprobe.d/ndiswrapper with the following contents:
alias wlan0 ndiswrapper

Thanks

---

### Post by DardDiablo on 2007-08-02
> **kevdog said:**
> 
Only the part about the wireless usb needs to be included:
lshw -C network

  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth0
       version: 10
       serial: 00:50:8d:f5:85:a9
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1                00bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driververs                ion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes                 port=MII speed=10MB/s
       resources: ioport:a000-a0ff iomemory:f2000000-f20000ff irq:18

> **kevdog said:**
> 
modprobe -l ndiswrapper

/lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko

> **kevdog said:**
> 
Make sure that the word ndiswrapper appears on a single line in the /etc/modules file
alias wlan0 ndiswrapper

excuse me I didn't understand this line :S, sorry I'm new to linux.

> **kevdog said:**
> 
Please also post /etc/iftab

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:50:8d:f5:85:a9 arp 1
> **kevdog said:**
> 
Is there a file /etc/modprobe.d/ndiswrapper with the following contents:
alias wlan0 ndiswrapper

Yes it appers like this "alias wlan0 ndiswrapper"
> **kevdog said:**
> 
Thanks

Thank you so much for the reply, I was very sad nobody was answearing to my problem. Excuse me if I didn't undestand what you were asking about.
I'm the only one who must say thanks to you :)

---

### Post by kevdog on 2007-08-02
Inside the /etc/modules file,  is there a line in the file that says:
ndiswrapper


When you did the lshw -C network statement -- was the usb device plugged in??
The following references a network card not a usb device:
> *-network
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 2
bus info: pci@02:02.0
logical name: eth0
version: 10
serial: 00:50:8d:f5:85:a9
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1 00bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driververs ion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
resources: ioport:a000-a0ff iomemory:f2000000-f20000ff irq:18

You can not used wired and wireless at the same time!!

---

### Post by DardDiablo on 2007-08-02
> **kevdog said:**
> Inside the /etc/modules file,  is there a line in the file that says:
ndiswrapper

Here I am. There wasn't any line (except 2 or three names), I just added "ndiswrapper" at the end of the file is that ok?

> **kevdog said:**
> 
When you did the lshw -C network statement -- was the usb device plugged in??
The following references a network card not a usb device:
You can not used wired and wireless at the same time!!
Yes the device is plugged in. The network card I think it's on the motherboard (I don't know how to say that, it's included on the mobo :S).
My device it's a usb adaptor, connect to a wireless key.

---

### Post by kevdog on 2007-08-02
Ok, you are doing everything right.

Can you reboot, and then post the following

```
iwlist -a scan
```

---

### Post by DardDiablo on 2007-08-02
> **kevdog said:**
> 
```
iwlist -a scan
```
Here I am. I've some new stuff:

**iwlist -a scan**
```
-a        Interface doesn't support scanning.
```

I didn't on purpose but I gave this comand :P

**modprobe -l ndiswrapper**
```
/lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
diablo@diablo-pc:~$ /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
bash: /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko: Permission denied
```

I also tried this:

**iwlist scan**
```
 lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

I think this aren't good news isn't it? Again thanks for your time and help.

p.s: I'm going to sleep I'm very tried :P, I'll read the answear tomorrow. Good night!

---

### Post by DardDiablo on 2007-08-03
I've read many other topcis but nothing that has a solution for my problem. I have to say that if i start kubuntu with the device already plugged in one of the leds is green, but if I plug the device when I'm already on kubuntu nothing happens, is that normal? :eek:

---

### Post by cmp1988 on 2007-08-03
Ah, that one.  Everytime I tried it on any Ubuntu version Edgy and beyond (had troubles with it using Knoppix livecd too), it froze my computer.  That was with the right drivers for mine, which is H/W Ver: A2.  I'm hoping you can get yours to work without a hitch.  Oh, did you try setting up the networking card with the GUI interface for setting up network cards?

---

### Post by DardDiablo on 2007-08-03
> **cmp1988 said:**
> Ah, that one.  Everytime I tried it on any Ubuntu version Edgy and beyond (had troubles with it using Knoppix livecd too), it froze my computer.  That was with the right drivers for mine, which is H/W Ver: A2.  I'm hoping you can get yours to work without a hitch.  Oh, did you try setting up the networking card with the GUI interface for setting up network cards?
What a bad news :(! My versione is A2 too, but why is this key getting so many problems? :confused:.
Ehm, I don't know how to explain it, but I don't need to configure the network card, because I have my wireless key connected with usb to the computer (or probably I didn't undestand what you both are saying :lolflag:).
Is network-manager the GUI interface? If it is so, i can't load it and I don't know why! When I click on it, just nothing happens...

How did you solved the problem? Did you use another device?

Thanks men for the replies :) ( I'm just happy for this)

p.s: I read posts about user that are using this key without problems, but I did all of the steps they have done, so I think this is a curse! :D

---

### Post by DardDiablo on 2007-08-03
I read someone has solved this problem by using network-manager, but when I'm trying (by the menu) to start it nothing happens. Probably this info will be useful, when I start Kubuntu a green button is on the right side near the clock, but immediately it disappears, what does it mean? :confused:

Someone has also adviced me to install the wireless-tools, but when i tried to compile them I got many errors...:(

I don't know what to do...

---

### Post by DardDiablo on 2007-08-04
Yesterday evening I've updated the ndiswrapper-utils from versione 1.18 to 1.19. But now when i type **ndiswrapper -l** it only says 
```
driver installed
```

and while installing the drivers it says something like this:

```
forcing from 256 to 64
``` (pr 32 I don't remember)

The only good news is that if I start Kubuntu without plugging in the device, and I do it after the login the LNK led is on. Previously when I started kubuntu without  the key plugged, and I plugged it afterwards the two led were both off.

I've finally installed wireless-tools from [this link]("http://packages.ubuntu.com/feisty/net/wireless-tools"). Now I can access to network-manager by clicking an icon near the clock (from the menu it doesn't open anything), I tried to able and disable the wireless, but it didn't work. In the menù, I've also found a program in Settings that's called Windows driver or something like that, but when I click that nothing happens, as the network-manager.

Ah finally, I also disablec the ethernet interface (from network-manager), I don't know if that may caused some kind of problem.

Now what to do? I think I've done almost everything I could do :cry:

Thanks in advice for any kind of help :(

---

### Post by DardDiablo on 2007-08-04
IT WORKSSSSSSSSSSSSS!!!! :guitar:. Probably you won't believe me, but I started kubuntu ( don't know why I did...I was so frustrated), I opened the terminal, after that I don't know why I unplugged the device and plugged it immediately...and....NOW IT RECOGNIZES! This is what I did after plugging in the device:

```

diablo@diablo-pc:~$ ndiswrapper -l
neta5agu : driver installed
diablo@diablo-pc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
         Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
         Bit Rate=108 Mb/s
         Power Management:off
         Link Quality:0  Signal level:0  Noise level:0
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

But still there are two problem:

1) I cant' navigate, access chat, ping ecc.. ( probably something isn't ok when retriewing ip? Or something like that?)
2) If I restart kubuntu I need to login, unplug the device e plug it immediately to make it recognized.

Is there a solution for those problems? Thank you very mach for any help.

p.s: after all I'm just happy for this little progress

---

### Post by DardDiablo on 2007-08-04
I read in some topics that probably there is a problem of DNS. So I edited my etc/resolv.conf file adding my dns (alice's one, I also tried opendns), I also gave chattr +i to avoid modifications, but all this procedure didn't solved my problem :(.

This is the output of two pings:

```
diablo@diablo-pc:~$ ping -c10 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=0.026 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=64 time=0.022 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=64 time=0.021 ms
64 bytes from 192.168.1.2: icmp_seq=4 ttl=64 time=0.024 ms
64 bytes from 192.168.1.2: icmp_seq=5 ttl=64 time=0.023 ms
64 bytes from 192.168.1.2: icmp_seq=6 ttl=64 time=0.023 ms
64 bytes from 192.168.1.2: icmp_seq=7 ttl=64 time=0.027 ms
64 bytes from 192.168.1.2: icmp_seq=8 ttl=64 time=0.023 ms
64 bytes from 192.168.1.2: icmp_seq=9 ttl=64 time=0.024 ms
64 bytes from 192.168.1.2: icmp_seq=10 ttl=64 time=0.025 ms
```

```
diablo@diablo-pc:~$ ping -c5 google.it
ping: unknown host google.it
```

Regarding the problem of pluging and unplugging the device, I think that made mad my computer, sometimes it show me the wireless pen with wlan0, sometimes with wlan1...

I think we can solve this problem, otherwise I will the destroy the pen :lolflag:

---

### Post by DardDiablo on 2007-08-05
Nothing...I've tried so many times but no good news. I'll post the last output and if nobody can help me I think I abadon this little "challenge".


```
diablo@diablo-pc:~$ iwconfig
lo        no wireless extensions.

wlan0     no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"Telsey"
         Mode:Managed  Frequency:2.462 GHz  Access Point: 00:03:6F:90:3D:D0
         Bit Rate=54 Mb/s
         Power Management:off
         Link Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

File **resolv.conf**

```
# generated by NetworkManager, do not edit!

search homenet.telecomitalia.it


# nameserver 192.168.1.1
nameserver 212.216.112.112
nameserver 212.216.172.62
```

File **/etc/iftab**

```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

wlan1 mac 00:50:8d:f5:85:a9 arp 1
```

```
diablo@diablo-pc:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan1.pid with pid 5580
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:50:8d:f5:85:a9
Sending on   LPF/wlan1/00:50:8d:f5:85:a9
Sending on   Socket/fallback
DHCPRELEASE on wlan1 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.wlan1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:50:8d:f5:85:a9
Sending on   LPF/wlan1/00:50:8d:f5:85:a9
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                        [ OK ]
```

file **/etc/network/interfaces**

```

#auto lo
#iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan1
iface wlan1 inet dhcp

iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan1 up # line maintained by pppoeconf
provider dsl-provider


iface lo inet loopback
```


Please I need help :cry:

---

### Post by DardDiablo on 2007-08-05
*bump* :(

---

### Post by sunexplodes on 2007-08-09
I've got this same little device, and it works perfectly for me. 

One thing that's weird is that it needs to be unplugged on reboot, and only plugged back in once i've logged onto the desktop, but that's no big deal (although if anybody knows how to stop that, keep me posted)

Anyway, in regards to your current problem, I've noticed that nm-applet in Feisty causes me all kinds of issues with this thing. Disable it in System>Preferences>Sessions, and try logging back in, then setting your specific wireless info in the Administration>Networking dialog.

Let me know if that helps. I've been using the 132 since Dapper, and I think i've encountered almost every problem in the book with the damn thing.

---

