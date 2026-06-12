---
title: "[SOLVED] NdisWrapper &amp;amp; drive installed w/o problem, still no net"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-07-14
I have never had wireless until a friend loaned me his laptop to install Ubuntu as a complete replacement for XP. The XP had an umountable_boot_volume error.

I have just re-installed Dapper on his Toshiba laptop model 1905-s304. I used Canonical's cd, not the alternate install cd.

I can't use Feisty, the cd-rw can't be mounted. I had to deprecate from Feisty to Dapper on the laptop.

KevDog, of this forum, was helpful in getting the Linksys WUSB11v4 adapter set up on my desktop so that I would know how to proceed to add it to the laptop.

I did the various steps necessary to build the ndiswrapper and the .exe driver into the laptop.

NO errors where reported. I have an extensive log of all the various processes, from the unzip to the (un)tar. 

I cold booted, but before powering up I added the usb wireless adapter. The system booted but System/Administation/Network has no wireless "entity", only eth0 and dial-up modem (internal to the laptop).

I looked at Applications/Add-Remove and found the Network Manager Applet, but when I asked for it to install itself, I received a: "no software channel available" message, even though I have the Dapper Drake (Canonical) cd in the drive.

a sudo ndiswrapper -l  returns:

ls: /etc/ndiswrapper: No such file or directory.

I apologize for asking such a broad question, but : What do I do next?

---

### Post by kevdog on 2007-07-14
Again check
lshw -C network

This will tell you the network adapters on your system.  Look for the drivers associated with each adapter.  There could possibly be the wrong driver or even no driver associated with the device you want.

---

### Post by Mark_in_Hollywood on 2007-07-15
Reading some other post, I see that the file /etc/network/interfaces is supposed to have operational, only the loopback: lo. 

All other entries were commented out. Text of that file follows at end of:

lshw -C network

returned:


james@Maplewood:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:02:3f:7c:22:27
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 multicast=yes
       resources: iomemory:e8104000-e8104fff ioport:4000-403f irq:11
james@Maplewood:~$ sudo lshw -C network
Password:
  *-network DISABLED
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:02:3f:7c:22:27
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
       resources: iomemory:e8104000-e8104fff ioport:4000-403f irq:11
james@Maplewood:~$

/etc/iftab

eth0 mac 00:02:3f:7c:22:27 arp 1

======

/etc/network/interfaces:

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#face eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

KevDog:

by the way: the 

sudo echo 'ndiswrapper' | tee -a something or other

did work, after I googled the line and found it had to be run as superuser, or sudo su

Although the above seems to indicate no wlan; ndiswrapper - shows (if my memory is OK) 

wusb11v4 driver present device present

but I can't get network manager to manage. It was difficult to install, I had to get the file from Ubuntu online and xfer via thumb. It installed but balked needing dependency:

libnl1-pre6 

I'm working on the How-To idea some more. Some ideas are getting clearer, some less so. Thanks for looking it over & adding criticism.

---

### Post by kevdog on 2007-07-15
Hold on, of the devices listed above, I dont see your usb device even listed.

There was only one device shown twice.  Where is the USB device??

Also you only want to comment out all the entries in the interfaces file if you want network manager to control all the interfaces.  Adding the devices to the interfaces file lets you set up the devices manually.  Its good to get everything manually up and running first usually in this order if you are having problems:

At command line
In interfaces file
Then by a third program such as
   network manager
   wifi rada
   wicd
   etc

---

### Post by Mark_in_Hollywood on 2007-07-15
> **kevdog said:**
> Hold on, of the devices listed above, I dont see your usb device even listed.

There was only one device shown twice.  Where is the USB device??

Also you only want to comment out all the entries in the interfaces file if you want network manager to control all the interfaces.  Adding the devices to the interfaces file lets you set up the devices manually.  Its good to get everything manually up and running first usually in this order if you are having problems:

At command line
In interfaces file
Then by a third program such as
   network manager
   wifi rada
   wicd
   etc

output of lsusb:

james@Maplewood:~$ lsusb
Bus 001 Device 003: ID 045e:0053 Microsoft Corp.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 004: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter
Bus 002 Device 001: ID 0000:0000

I'm cmnted out the lo lines in /etc/network/interfaces

I can't get net-mgr to work. Sys/Admin/Network shows eth0 and ppp0 both disabled. I did many posts ideas about nm-applet but as yet, no "go".

You mean to link net-mgr to wif rada wicd and etc? Sorry I'm lost

GOOD MORNING.

---

### Post by Mark_in_Hollywood on 2007-07-15
Found WiFi-Radar and wicd. xfred both to laptop. Installed Radar. All seems to have gone well with install from GDebi.

google shows no how-to for config.

I set WiFi options as follows

Mode: auto
Channel: auto
Key: blank
Security: open

No WPA

Auto network config (DHCP)

Connection commands - blank

clicking "connect" fails

My Preferred Wi-Fi network shows: connected to none. ip 127.0.0.1

still no google.com

Sys/Admin/Network shows eth0, ppp0, no lan0 (wlan0)

Sys/Admin/Networking tools/Devices shows lo and nothing else.

iwconfig shows:

lo 0 no wireless extensions
eth0 no wireless extensions
sit0 no wirless extensions

---

### Post by Mark_in_Hollywood on 2007-07-15
Wi-Fi Radar  couldn't connect.

Uninstalled it and installed wicd

it shows no wireless card, but output of lsusb shows wusb11 adapter and ndiswrapper -l shows driver present hardware present wusb11v4, too.

---

### Post by kevdog on 2007-07-15
If your device doesnt show up with 
lshw 

then network manager, wicd, wifi radar wil not work.

---

### Post by Mark_in_Hollywood on 2007-07-15
Nothing shows up with words like: Linksys, usb wireless, or anything indicating the computer is "wireless aware"

for the record: I did a clean install of Dapper on Saturday. I spent the better part of the day getting the wusb driver and ndis up and running and have the logs of all the outputs, which seem to indicate no problems, until

sudo echo 'ndis ... | -a . . .

which had to be invoked with sudo su and then the command.

The net-mgr. has only eth0 and ppp0 nothing wireless.

Any ideas?

PS you misunderstood my post of friday night, I got the wirelss running on the desktop, the laptop is still down. THNX

---

### Post by kevdog on 2007-07-15
If the computer can not see the device I can not help you all that much.  Do you know what kind of chipset is in your USB device.  You might have to google for this one since linux doesnt seem to tell you anything.  All check your logs such as /var/log/dmesg and /var/log/syslog /var/log/boot to see if there is any error in identifying the device.

---

### Post by Mark_in_Hollywood on 2007-07-24
The first pci card was defective. Another has been installed. lspci shows it as well.

---

