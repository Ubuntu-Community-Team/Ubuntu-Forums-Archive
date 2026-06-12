---
title: "PLEASE HELP!! sudo modprobe ndiswrapper problem"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by ianb72 on 2007-04-22
Hi I have follow the how to at [wireless networks]("http://ubuntuforums.org/showthread.php?t=31926")

but when I type [HTML]sudo modprobe ndiswrapper[/HTML]

The system just sits there doing nothing!!

I am tring to install a wireless Dongles, when I type [HTML]ian@ian-desktop:~$ sudo ndiswrapper -l
Installed ndis drivers:
zd1211u         driver present
[/HTML]

What am I doing wrong???

---

### Post by spd106 on 2007-04-22
Can you please post the output of these commands?
```
ndiswrapper -v
```
```
sudo lshw -class network
```

---

### Post by ianb72 on 2007-04-22
[HTML] ian@ian-desktop:~$ ndiswrapper -v
utils version: 1.7
driver version:        1.42
ian@ian-desktop:~$ sudo lshw -class network
Password:
  *-network DISABLED
       description: Ethernet interface
       product: 3c905 100BaseTX [Boomerang]
       vendor: 3Com Corporation
       physical id: b
       bus info: pci@00:0b.0
       logical name: eth0
       version: 00
       serial: 00:60:08:5b:81:e2
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100b t-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=3c59x driverversio n=LK1.1.19 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:ec00-ec3f irq:11
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:72:53:f8:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g NIC
ian@ian-desktop:~$
[/HTML]

I managed to get another linux driver installed but even thou it sees the essid it still wont connect to the router or internet!!!! :confused:

---

### Post by ianb72 on 2007-04-22
I also forgot to point out the pc with the wireless dongle is only about 5 feet away from the router.

I am trying to set it up on my old pc before I install it on my laptop, just so I know what I am doing first. lol

---

### Post by spd106 on 2007-04-22
Could you please tell us the make and model of the device? 
Is it listed on this wiki page [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)?

This website also has a list of devices that work [http://www.qbik.ch/usb/devices/](http://www.qbik.ch/usb/devices/)

Could you post the output of this command?
```
lsusb
```

---

### Post by ianb72 on 2007-04-23
OK it says 

[HTML] ian@ian-desktop:~$ lsusb
Bus 001 Device 003: ID 08ec:0015 M-Systems Flash Disk Pioneers
Bus 001 Device 002: ID 0ace:1215 ZyDAS
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000[/HTML]

I have a Linux driver on the CD that came with the dongle, it has a file called "sta" which is a shell script but I have tried
[HTML] sh /home/ian/Desktop/sta.sh and
sh /home/ianl/Desktop/sta [/HTML]

But it doesn't work!!

---

### Post by kolibri on 2008-02-28
Computer:  new Dell inspiron 1525 with the default dell wireless minicard.  I downloaded the appropriate windows driver from Dell for this computer after I reformated the disk and reinstalled windows and Ubuntu on parallel partitions.  The wireless card is working fine on the windows side.

I removed the default ndiswrapper that came with my recent Gutsy install.

I downloaded the latest ndiswrapper version, then followed the instructions in the install file (and this page: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

(I had problems with not having the linux headers, but found that answer here after many hours)

Now the install seemed to go well, I got through to:
 ndiswrapper -l
bcmwl6 : driver installed
        device (14E4:4315) present

everything looks ok, but after:
sudo modprobe ndiswrapper

I queried:
tail /var/log/messages
and got:

Feb 27 22:55:22 Fruhling dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Feb 27 22:55:22 Fruhling dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Feb 27 22:55:22 Fruhling dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Feb 27 22:55:23 Fruhling kernel: [  163.020000] NET: Registered protocol family 10
Feb 27 22:55:23 Fruhling kernel: [  163.020000] lo: Disabled Privacy Extensions
Feb 27 22:56:18 Fruhling kernel: [  216.560000] UDF-fs: No VRS found
Feb 27 23:00:19 Fruhling kernel: [  458.324000] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Feb 27 23:00:20 Fruhling loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwl6 
Feb 27 23:00:20 Fruhling kernel: [  458.432000] usbcore: registered new interface driver ndiswrapper

Note the error message: couldn't load driver bcmwl6.  
when i run iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

I'm kind of stuck now at how to get the wireless working here- any ideas?

thanks

---

### Post by myddewji13 on 2008-02-28
> 
Note the error message: couldn't load driver bcmwl6
the bcmwl6 driver is a vista driver....it wont work...you need a bcmwl5 driver
...

---

### Post by 2GooD on 2008-02-29
It works fine for me, see the [Dell category of my blog](http://www.divideandconquer.se/category/dell/) for my experiences.

\David

[http://www.divideandconquer.se/](http://www.divideandconquer.se/)

---

