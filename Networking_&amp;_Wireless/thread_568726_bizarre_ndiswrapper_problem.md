---
title: "bizarre ndiswrapper problem"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by philtbelfast on 2007-10-06
Sorry to keep posting about my wireless problems...

Installed ndiswrapper, installed my WPN111 drivers and everything worked. Went online for about 30 seconds then the computer locked up.

When i restarted the lights on the wireless usb flash but theres no wireless available on ubuntu.

When i type iwconfig it doesnt find any wireless card. 

When i type ndiswrapper -l everything seems to be fine.

Does anyone have any suggestions?

Cheers,

Phil

---

### Post by kevdog on 2007-10-06
Is the ndiswrapper module loaded?? You can check by

lsmod | grep ndiswrapper

If it is not you can load the module with
sudo modprobe ndiswrapper

And you can ensure the module is being loaded at boot if it is listed in the /etc/modules file.  If ndiswrapper is not mentioned in this file, you can add it by:

echo ndiswrapper | sudo tee -a /etc/modules

---

### Post by philtbelfast on 2007-10-06
Thanks for the suggestion

it wasnt there, so i added it manually with sudo gedit then restarted. exactly the same situation now.

lights still flashing on the usb stick but still no recognition from ubuntu that its attached.

any other ideas?

cheers

---

### Post by kevdog on 2007-10-06
Post the lsmod statement as in the previous post.

---

### Post by philtbelfast on 2007-10-06
cheers for persisting with this kev,

unfortunately i am literally 2 days into linux and am learning as i go along.

do you mean post the content of the modules file or what?

sorry for being so ignorant!

many thanks

---

### Post by kevdog on 2007-10-06
Type this in the terminal and post the output:


lsmod | grep ndiswrapper
modinfo ndiswrapper
ndiswrapper -v

---

### Post by philtbelfast on 2007-10-06
kev these are the results of each command

lsmod | grep ndiswrapper

ndiswrapper           193116  0 
usbcore               134280  7 ndiswrapper,usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd

mod info ndiswrapper

filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
license:        GPL
version:        1.48
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     3C6A9B2C518323EF6FE1A9D
depends:        usbcore
vermagic:       2.6.20-15-generic SMP mod_unload 586 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

ndiswrapper -v

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.48
vermagic:       2.6.20-15-generic SMP mod_unload 586 

Cheers

---

### Post by kevdog on 2007-10-06
Everything looks good there, I should have asked for a couple of more things:

lshw -C network
ndiswrapper -l
iwlist scan

---

### Post by philtbelfast on 2007-10-06
lshw -C network

*-network               
description: Ethernet interface       
product: RTL-8139/8139C/8139C+       
vendor: Realtek Semiconductor Co., Ltd.       
physical id: 5       
bus info: pci@02:05.0       
logical name: eth0       
version: 10       
serial: 00:16:e6:12:ef:99       
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
resources: ioport:dc00-dcff iomemory:fddff000-fddff0ff irq:21

ndiswrapper -l

netwpn111 : driver installed
device (1385:5F01) present

iwlist scan

lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

cheers

---

### Post by kevdog on 2007-10-06
Yes Im slightly confused right now -- sorry - the ndiswrapper module is loaded, however basically your network device isnt showing up (I forgot it was a USB device).

Can you post the following
lsusb
cat /etc/iftab
cat /etc/network/interfaces
ifconfig

---

### Post by philtbelfast on 2007-10-06
Yea its really confusing me especially since the light on the USB stick flashes away to itself. Anyway here are the other responses

lsusb

Bus 001 Device 003: ID 413c:3200 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 058f:9360 Alcor Micro Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 007: ID 05ac:1209 Apple Computer, Inc. 
Bus 002 Device 003: ID 1385:5f01 (This is my wireless, a WPN111)
Bus 002 Device 001: ID 0000:0000 

cat /etc/iftab

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:e6:12:ef:99 arp 1

cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:16:E6:12:EF:99
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x8000

eth0:avah Link encap:Ethernet  HWaddr 00:16:E6:12:EF:99            
inet addr:169.254.8.210  Bcast:169.254.255.255  Mask:255.255.0.0          
UP BROADCAST MULTICAST  MTU:1500  Metric:1         
Interrupt:21 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3298 (3.2 KiB)  TX bytes:3298 (3.2 KiB)

Cheers

---

### Post by kevdog on 2007-10-06
I see that you have a wired connection.

Please reboot with the wire disconnected. 

After starting I want you to pipe the results of these commands to a file:

cd ~
touch network.txt
lshw > network.txt
dmesg >> network.txt

Plug in you network cable, you might have to reboot to get a connection, maybe not.  But I want you to post the network.txt file here.

---

### Post by philtbelfast on 2007-10-06
I dont have a wired connection. I dont even have a pci modem in my computer. Its literally just the WPN111, i'm online via another laptop.

Do you still want the results of 

cd ~
touch network.txt
lshw > network.txt
dmesg >> network.txt

cheers for sticking with this!

---

### Post by kevdog on 2007-10-06
Ok just to save time, boot without a network cable but with the USB device in place.

Here is what I want you to do -- your going to have to be my eyes.

Type 

more dmesg

One page will scroll by, push the space bar to get the next page.  Look for anything having to do with your USB device -- it should be fairly obvious.  Im looking for anything. 

Same with the lshw section -- any thing having to do specfically with the USB wireless dongle, not specifically with the USB port or USB port driver.

---

### Post by philtbelfast on 2007-10-06
sorry kev im possibly being really stupid but none of those commands get any reaction whatsoever from the terminal.

like I said im new to all this maybe im typing it in wrong?

cheers

---

### Post by kevdog on 2007-10-06
Try this

dmesg | more
sudo lshw

---

### Post by philtbelfast on 2007-10-06
Im really not sure exactly what Im looking for but its quite tricky to find anything specific to my USB under dmesg more.

under sudo lshw theres one reference, 

*-usb UNCLAIMED
description : generic usb device
product : wpn111
vender : atheros communications inc
physical id: 5
bus info : usb@2:5
version: 0.01
serial : 1.0
capabilities : usb-2.00
configuration: maxpower=500mA speed=480.0MB/s

---

### Post by kevdog on 2007-10-06
Oki, here is the problem -- in your last post you see how the device is listed as unclaimed -- that means no kernel module or driver is claiming the device, so hence that is the reason it is not working.

There could be many reasons for this:
1. The ndiswrapper module isnt loading or something.  You can try this:
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

This will unload and reload the ndiswrapper module (cycling the module).  You can check the lshw statement again after doing this to see if the device is claimed after doing this.

2. If the device remains unclaimed, then you need to verify that you have the correct driver loaded within ndiswrapper.  You want the windows xp driver to the best of my knowledge.  You might have to visit the manufacture's website and redownload the driver or use a different driver.  Make sure you unload the old driver similar to this:
sudo rmmod ndiswrapper 
sudo ndiswrapper -r netwpn111

Load new driver and reload kernel module
sudo ndiswrapper ********  <--- new driver listed in place of *****
sudo modprobe ndiswrapper

Recheck with lshw to see if the device is claimed

3. Recheck dmesg again after loading ndiswrapper for any errors.  Again we are looking for feedback why things are not working and a place to focus our efforts.

---

### Post by philtbelfast on 2007-10-07
morning kev & thanks for all your help yesterday,

ok i removed the drivers, got new ones which are more specifically aimed at XP (my last drivers were for 98, me, xp & vista).

Did the whole thing all over again and now have a (slightly) different result.

If I switch my pc on with the wpn111 plugged in, it will not be recognised. However if I switch my pc on and only plug the wpn111 in once ubuntu is logged in and running it will be recognised.

However then Im back to my old problem that any network activity will completely lock up the pc.

Any ideas? I checked and the USB is now claimed.

---

### Post by philtbelfast on 2007-10-07
Update : Removed the network manager and tried to connect purely through the terminal. It seemed to work for about 30-40 seconds longer but frankly I think its just at random when network traffic freezes the computer.

---

### Post by kevdog on 2007-10-07
Looks like you might have a crappy network stick.  Im not sure.  Short of checking the system log, Im not sure what else I can try.  Something tells me that your driver is bad.  Try the win98 driver just for kicks, but if that doesnt work, Im kind of out of ideas.

---

### Post by philtbelfast on 2007-10-07
Its definitly not a crappy network stick, its been fine on xp and then vista for the last year and a bit. Have just given up and bought another stick that says its linux compatible. Hopefully have less problems once it arrives. Cheers for your help anyway.

---

### Post by kevdog on 2007-10-07
Just an FYI -- linux-compatible is a term that is used very loosely.  Dont be surprised if you have to do some monkeying to get it too work.  Some do truly work out of the box, but many dont.  Keep your fingers crossed that you will be lucky!

---

### Post by philtbelfast on 2007-10-07
Cheers for the advice, I had a look on the compatible wifi list and it appears that it requires a much more minimal amount of monkeying. After that I think Ill start having a complain about my graphics card!

---

### Post by jrob2323 on 2007-10-23
Hey --i'm still new to linux but  --  I had the same problem..  
in my case, I ran modprobe 1 too many times... it looks like it keeps creating alias'

Here's what I did to fix it--

ndiswrapper -l
ndiswrapper -e netwpn11
modprobe -r ndiswrapper


then restart installation following previous steps

---

