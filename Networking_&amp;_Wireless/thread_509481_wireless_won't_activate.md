---
title: "wireless won't activate"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by mobz on 2007-07-25
I recently upgraded to Dapper from Badger. My wireless network worked before. I have ndiswrapper installed and it recognizes the broadcom driver (bcmwl5) even now. However I cannot activate the wireless interface anymore. When I activate it (systems->admin->networking) it seems fine but then when I go back it says not active. 
I know this might have already been posted and if so could someone link me to the post. Otherwise could anyone help me with this? 
Thanks in advance

---

### Post by kevdog on 2007-07-25
A little behind the times with Badger.  

Lets just check a few things:
lspci -nn
ndiswrapper -v
ndiswrapper -l
sudo modprobe -l ndiswrapper
sudo modinfo ndiswrapper
lsmod | grep ndiswrapper
lshw -C network

I know thats a lot, but its a start (couldnt think of anything else to add to make it more difficult:))

---

### Post by mobz on 2007-07-25
I know. Just have this tendency to slip into a comfort zone with OS'es and not trusting myself with new stuff. Anyway, here's the diagnostics:

 lspci -nn
0000:00:00.0 0600: 1002:cab0 (rev 13)
0000:00:01.0 0604: 1002:700f (rev 01)
0000:00:02.0 0c03: 10b9:5237 (rev 03)
0000:00:06.0 0401: 10b9:5451 (rev 02)
0000:00:07.0 0601: 10b9:1533
0000:00:08.0 0703: 10b9:5457
0000:00:09.0 0280: 14e4:4320 (rev 02)
0000:00:0a.0 0607: 104c:ac50 (rev 02)
0000:00:10.0 0101: 10b9:5229 (rev c4)
0000:00:11.0 0680: 10b9:7101
0000:00:12.0 0200: 100b:0020
0000:01:05.0 0300: 1002:4336


ndiswrapper -v
utils version: 1.7
driver version:        1.8

ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

sudo modprobe -l ndiswrapper
/lib/modules/2.6.15-28-k7/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

sudo modinfo ndiswrapper
filename:       /lib/modules/2.6.15-28-k7/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
version:        1.8
license:        GPL
vermagic:       2.6.15-28-k7 SMP preempt K7 gcc-4.0
depends:        usbcore
srcversion:     40DD0BF42F95DD26FA6A8B5
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           if_name:Network interface name or template (default: wlan%d) (charp)

lsmod | grep ndiswrapper
ndiswrapper           190996  0
usbcore               139012  3 ndiswrapper,ohci_hcd

 lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth1
       version: 02
       serial: 00:90:4b:5d:0d:88
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:d0000000-d0001fff irq:10
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0f:20:20:f0:5b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi ip=192.168.1.4 multicast=yes
       resources: ioport:8c00-8cff iomemory:d0005000-d0005fff irq:11

---

### Post by kevdog on 2007-07-25
Here is part of your problem -- I think ndiswrapper is OK (not sure), however your card is currently assigned the bcm43xx driver:
> driver=bcm43xx

Blacklist this driver by doing the following:
```
gksu gedit /etc/modprobe.d/blacklist
```

Add the following:
```
blacklist bcm43xx

```
Reboot and then tell me what happens.  You can recheck if ndiswrapper is associated with your card by :
lshw -C network

---

### Post by mobz on 2007-07-25
OK, now it does not recognise the device. I cannot even acces anything via Network Settings (does not respond. )

 lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:d0000000-d0001fff irq:9

---

### Post by kevdog on 2007-07-25
You are making progress.

Try:
sudo modprobe ndiswrapper

Did you do the following which loads the ndiswrapper driver on startup:
echo "ndiswrapper" | sudo tee -a /etc/modules

---

### Post by mobz on 2007-07-25
I did now. The device is recognized now (I think).
This is from iwconfig:
>iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

My network is encrypted. I am guessing that is the reason now (?). Been tryin to use the GUI for networking (to set it up), but it shows nothing.

---

### Post by mobz on 2007-07-25
update: driver associates with ndiswrapper 

 *-network:0
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: wlan0
       version: 02
       serial: 00:90:4b:5d:0d:88
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d0000000-d0001fff irq:10

---

### Post by kevdog on 2007-07-25
Ok, is problem solved now or is something else creating a conflict??

---

### Post by mobz on 2007-07-25
umm..i dont know. my wireless still does not work (connect i.e.)

---

### Post by mobz on 2007-07-25
Little more help still:

My wlan0 intrface is now active. It 'sees' the networks around. I selected my ssid and the password. Everything seems ok theoritically. But when I remove my wired connection, I am not connected to the net anymore. 
Any ideas about what else I could be doing wrong or tests I could run to figure out? 
Thanks

---

### Post by kevdog on 2007-07-25
Wired and wireless unless you do something fancy and have each card on a different subnet can not work together.  Id either boot using one or the other.  If you want to change in the middle of the session, I guess you could try:
sudo /etc/init.d/networking restart

for a command, however I dont know if this will work.

---

