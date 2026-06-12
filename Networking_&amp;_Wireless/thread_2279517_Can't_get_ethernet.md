---
title: "Can't get ethernet"
date: 2015-05-23
forum: Networking &amp; Wireless
---

### Post by moktar2 on 2015-05-23
Hello Ubuntu people :)
I've installed Ubuntu 14.04 LTS Desktop
I cant see my eth0 in connections and I had to install a usb wifi piece to solve this

I get this 
```
lspci | grep Ether
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)


```

```
sudo lshw -C network
[sudo] password for alamya: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:f0180000-f019ffff memory:f01a5000-f01a5fff ioport:1100(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:3
       logical name: wlan0
       serial: 00:0f:55:bc:05:28
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.16.0-30-generic firmware=0.29 ip=192.168.1.16 link=yes multicast=yes wireless=IEEE 802.11bgn

```


```
cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

```

cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


```

```


cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


```



```
dmesg | grep e100
[    2.917145] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    2.917148] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    2.917671] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    2.917688] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[    3.025169] e1000e 0000:00:19.0: The NVM Checksum Is Not Valid
[    3.058932] e1000e: probe of 0000:00:19.0 failed with error -5
```

---

### Post by moktar2 on 2015-06-01
any help plz?

---

### Post by QIII on 2015-06-01
Hello!

Waiting a week to bump your thread is not helpful.  Your post got pushed down so far nobody could see it any longer.

If you have not gotten an answer in 12 hours, feel free to bump.

---

### Post by Bashing-om on 2015-06-01
moktar2; Hello;

Regret that this thread is just now coming to my attention.
But to the situation at hand:
Are you using 'network manager' to mange your network abilities ?
I see:
> 
cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
[color=red]managed=false[/color]


If you do want 'network manager' then change the above " managed=false " to true in your favorite text editor ( make a back up 1st, SOP).

I prefer to reboot the system and see if networking comes up, rather then a simple restart.

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by moktar2 on 2015-06-04
Sorry, I did not want to be annoying :)


[Bashing-om]("http://ubuntuforums.org/member.php?u=1111508")[COLOR=#000000] , Thanks a lot for respond

[/COLOR]I did what you suggested but still cant get ethernet working !



```
cat /etc/NetworkManager/NetworkManager.conf[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=true



```

---

### Post by slickymaster on 2015-06-04
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by moktar2 on 2015-06-04
Ethernet still not working, currently I'm using usb-wifi , but i need to get the ethernet working.
any help please>?

---

### Post by Bucky Ball on 2015-06-04
> **Bashing-om said:**
> 
If you do want 'network manager' then change the above " managed=false " to true in your favorite text editor ( make a back up 1st, SOP).

I prefer to reboot the system and see if networking comes up, rather then a simple restart.

You tried this, disabled wireless and pulled the USB wireless dongle out then rebooted the machine? Make sure the wireless dongle is not plugged in on reboot. If the system picks up the wireless first it should default to that, not the ethernet.

When you've done this, if still not working, show us the result of 'sudo lshw -C network' again to see if anything's changed.

---

### Post by moktar2 on 2015-06-04
Bucky Ball, thanks again for your help 
I've pulled the usb dongle out then reboot my system withuot it 

here is 
[COLOR=#000000]sudo lshw -C network[/COLOR]
```
*-network UNCLAIMED            description: Ethernet controller
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:f0180000-f019ffff memory:f01a5000-f01a5fff ioport:1100(size=32)



```

---

### Post by Bashing-om on 2015-06-04
moktar2; Welll !

I am surprised, as Intel just works !

Let's start at the start and see if we can find out where the failure is.

Does the system pick up the hardware ?
```

lspci | grep Ethernet
ip link ls
ls /sys/class/net

```

Does the driver see the  gateway ?
```

sudo ip link show eth0
ip route list

```

And for now, what is configured for the interface ?
```

cat /etc/network/interfaces
cat /var/lib/NetworkManager/dhclient-eth0.conf
ls -l /etc/resolv.conf

```

That should give us a bit to look over and then see where we look next.

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by moktar2 on 2015-06-05
Many thanks for you all, 
Thanks Bashing-om

```

alamya@Alamya-PC:~$ lspci | grep Ethernet
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
alamya@Alamya-PC:~$ ip link ls
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 00:0f:55:bc:05:28 brd ff:ff:ff:ff:ff:ff
alamya@Alamya-PC:~$ ls /sys/class/net
lo  wlan0

```

sudo ip link show eth0
```

sudo ip link show eth0




```

---

### Post by Bashing-om on 2015-06-05
moktar2l Humm ...

Strange .

No module available to load ???

With the WIFI dongle unplugged and WIFI physically switched off, what now results from terminal command - and the wired connection connected to the internet ; and on a fresh re-boot :
```

lspci -nnk | grep -iA2 net

```

[INDENT]got to identify the module and find out why it is not loading
[INDENT][INDENT][INDENT]got to be a cause
[/INDENT][/INDENT][/INDENT][/INDENT]

---

