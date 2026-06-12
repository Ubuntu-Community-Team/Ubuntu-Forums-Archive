---
title: "[SOLVED] Noob trying to install Broadcom Help please !!!!!!!"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by nickjhs on 2008-08-22
HI folks, I have a VERY basic knowledge of linux. I decided to have a look at Ubuntu, never used linux before and wouldnt you know it I have a broadcom 4303 chipset! I have tried to follow the help guides but feel that I am making the problem worse. I have blacklisted various bcm files as requested and tried to install ndiswrapper and then the .inf file this has not worked. I cannot download the cutter file. Help Please. distro Hardy lts

---

### Post by pytheas22 on 2008-08-22
Please open a terminal (Applications>Accessories menu) and post the output of these commands so that we can help better:
```

lshw -C Network
lspci -nn | grep -i broad
ndiswrapper -l
```

Also, do you have a way to connect Ubuntu to the Internet at all (e.g., an ethernet connection)?

(If you don't have Ubuntu online at all, you can copy-and-paste the outputs from the commands above into a text file and transfer them to a computer that has Internet, in order to make things easier...or you can just copy them over by hand).

---

### Post by nickjhs on 2008-08-22
nick@nick-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0f:20:c9:01:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.0.5 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
nick@nick-laptop:~$ lspci -nn | grep -i broad
00:09.0 Network controller [0280]: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [14e4:4301] (rev 02)
nick@nick-laptop:~$ ndiswrapper -l
nick@nick-laptop:~$




Thanks

---

### Post by pytheas22 on 2008-08-22
Please run these commands; they should make it work:
```

sudo -s
mkdir stuff
cd stuff
apt-get install ndiswrapper*
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist b43 ssb' >> /etc/modprobe.d/blacklist
wget http://burnthesorbonne.com/files/broadcom_4303.tar.gz
tar -xzvf broadcom_4303.tar.gz
ndiswrapper -i bcmwl5.inf
echo 'ndiswrapper' >> /etc/modules
```

That should do it.  Reboot and try connecting again.  If it still doesn't work, please post the output again of:
```

ndiswrapper -l
lshw -C Network
iwlist scan
dmesg | grep ndis
```

---

### Post by nickjhs on 2008-08-22
Not sure that I did this correctly, thanks for your patience

nick@nick-laptop:~$ sudo -s
[sudo] password for nick: 
root@nick-laptop:~# mkdir stuff
root@nick-laptop:~# cd stuff
root@nick-laptop:~/stuff# apt-get install ndiswrapper*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting ndiswrapper-common for regex 'ndiswrapper*'
Note, selecting ndiswrapper-utils for regex 'ndiswrapper*'
Note, selecting ndiswrapper-source for regex 'ndiswrapper*'
Note, selecting ndiswrapper-modules-1.9 for regex 'ndiswrapper*'
Note, selecting ndiswrapper-utils-1.9 for regex 'ndiswrapper*'
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@nick-laptop:~/stuff# echo 'blacklist b43' >> /etc/modprobe.d/blacklist
root@nick-laptop:~/stuff# echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklisecho 'blacklist ssb' >> /etc/modprobe.d/blacklist
root@nick-laptop:~/stuff# echo 'blacklist b43 ssb' >> /etc/modprobe.d/blacklistwget [http://burnthesorbonne.com/files/broadcom_4303.tar.gz](http://burnthesorbonne.com/files/broadcom_4303.tar.gz)
root@nick-laptop:~/stuff# tar -xzvf broadcom_4303.tar.gz
tar: broadcom_4303.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@nick-laptop:~/stuff# ndiswrapper -i bcmwl5.in
install argument must be .inf file
root@nick-laptop:~/stuff# ndiswrapper -i bcmwl5.inf
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
root@nick-laptop:~/stuff# echo 'ndiswrapper' >> /etc/modules
root@nick-laptop:~/stuff#

---

### Post by nickjhs on 2008-08-22
As I thought I must have done something wrong

nick@nick-laptop:~$ ndiswrapper -l
nick@nick-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0f:20:c9:01:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.0.5 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
nick@nick-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

nick@nick-laptop:~$ dmesg | grep ndis
[   58.645361] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   58.733755] usbcore: registered new interface driver ndiswrapper
nick@nick-laptop:~$ 

ONce again thanks for your help and patience

---

### Post by nickjhs on 2008-08-23
I worked our where I went wrong with teh first set of instructions. Unfortunately this has not fixed the problem

nick@nick-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4301) present (alternate driver: ssb)
nick@nick-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0f:20:c9:01:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.0.5 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
nick@nick-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

nick@nick-laptop:~$ dmesg | grep ndis
[   58.623069] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   58.746543] usbcore: registered new interface driver ndiswrapper
nick@nick-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by pytheas22 on 2008-08-23
> I worked our where I went wrong with teh first set of instructions. Unfortunately this has not fixed the problem

Yeah, the problem is that the native driver (b43) is still trying to control this card, even though it should be on the blacklist.  Sometimes this happens.  Try running these commands:
```

sudo modprobe -r b43 b44 ssb b43legacy ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

If you get an errors during those commands, please post the output.  If you don't get errors, can you connect now?  ndiswrapper itself looks like it should work, so the issue is just figuring out why b43 still wants to control the card.

---

### Post by nickjhs on 2008-08-23
nick@nick-laptop:~$ sudo modprobe -r b43 b44 ssb b43legacy ndiswrapper
[sudo] password for nick: 
nick@nick-laptop:~$ sudo modprobe ndiswrapper
nick@nick-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
nick@nick-laptop:~$ 

Thanks for your continuing help, I really appreciate it

---

### Post by pytheas22 on 2008-08-23
Sorry it's still not working.  What is the output of:
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod ssb
sudo modprobe ndiswrapper
dmesg | grep -e ndis -e wlan
lwhw -C Network
uname -m
```

---

### Post by nickjhs on 2008-08-23
One Day I will know what this all means :)

nick@nick-laptop:~$ sudo rmmod b43
[sudo] password for nick: 
Sorry, try again.
[sudo] password for nick: 
ERROR: Module b43 does not exist in /proc/modules
nick@nick-laptop:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
nick@nick-laptop:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
nick@nick-laptop:~$ sudo modprobe ndiswrapper
nick@nick-laptop:~$ dmesg | grep -e ndis -e wlan
[   54.074450] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   54.141385] usbcore: registered new interface driver ndiswrapper
[  196.770391] usbcore: deregistering interface driver ndiswrapper
[  405.777070] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  405.910571] ndiswrapper: driver bcmwl5 (Broadcom,07/09/2002, 3.08.27.0) loaded
[  405.926086] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: dd045933
[  405.926135] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x104
[  405.926468] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[  405.926503] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[  405.926573] ndiswrapper (mp_halt:259): device dbb1b480 is not initialized - not halting
[  405.926586] ndiswrapper: device eth%d removed
[  405.926749] ndiswrapper: probe of 0000:00:09.0 failed with error -22
[  405.941378] usbcore: registered new interface driver ndiswrapper
nick@nick-laptop:~$ lwhw -C Network
bash: lwhw: command not found
nick@nick-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0f:20:c9:01:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.0.5 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
nick@nick-laptop:~$

---

### Post by pytheas22 on 2008-08-23
ndiswrapper doesn't seem to like the Windows driver that you loaded for some reason.  Please run this; it will install a different Windows driver that according to [this thread]("http://ubuntuforums.org/showthread.php?t=399820") works for your card:

sudo apt-get install cabextract
sudo ndiswrapper -r bcmwl5
wget [ftp://ftp.hp.com/pub/softpaq/sp30001-30500/SP30379.exe](ftp://ftp.hp.com/pub/softpaq/sp30001-30500/SP30379.exe)
cabextract SP30379.exe
sudo ndiswrapper -i bcmwl5.inf

Then reboot.  After reboot, please run these commands and post all of the output here:
```

sudo modprobe -r ssb b44 b43 b43legacy
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
dmesg | grep ndis
uname -m
```

I may not be able to respond again till tomorrow but I'll be back as soon as I can...

---

### Post by nickjhs on 2008-08-23
nick@nick-laptop:~$ sudo modprobe -r ssb b44 b43 b43legacy
[sudo] password for nick: 
FATAL: Module ssb is in use.
nick@nick-laptop:~$ sudo rmmod ndiswrapper
nick@nick-laptop:~$ sudo modprobe ndiswrapper
nick@nick-laptop:~$ dmesg | grep ndis
[   50.739441] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   50.847580] usbcore: registered new interface driver ndiswrapper
[  523.217613] usbcore: deregistering interface driver ndiswrapper
[  545.236422] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  545.288762] usbcore: registered new interface driver ndiswrapper
nick@nick-laptop:~$ uname -m
i686
nick@nick-laptop:~$ 

Once again a great many thanks

---

### Post by pytheas22 on 2008-08-23
Please reboot (again, sorry..) and then post:

```
sudo rmmod --verbose b43
sudo rmmod --verbose b44
sudo rmmod --verbose b43legacy
sudo rmmod --verbose ssb
sudo modprobe ndiswrapper
dmesg | grep -e ndis -e wlan
ndiswrapper -l

```

I think we're almost there but we just need to figure out why ssb won't unload.

---

### Post by nickjhs on 2008-08-23
nick@nick-laptop:~$ sudo rmmod --verbose b43
[sudo] password for nick: 
ERROR: Module b43 does not exist in /proc/modules
nick@nick-laptop:~$ sudo rmmod --verbose b44
rmmod b44, wait=no
nick@nick-laptop:~$ sudo rmmod --verbose b43
ERROR: Module b43 does not exist in /proc/modules
nick@nick-laptop:~$ sudo rmmod --verbose b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
nick@nick-laptop:~$ sudo rmmod --verbose ssb
rmmod ssb, wait=no
nick@nick-laptop:~$ sudo modprobe ndiswrapper
nick@nick-laptop:~$ dmesg | grep -e ndis -e wlan
[   52.123953] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   52.245766] usbcore: registered new interface driver ndiswrapper
nick@nick-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4301) present (alternate driver: ssb)
nick@nick-laptop:~$

---

### Post by pytheas22 on 2008-08-23
It looks like it should be working now.  After you run all these commands:

```
sudo rmmod --verbose b43
sudo rmmod --verbose b44
sudo rmmod --verbose b43legacy
sudo rmmod --verbose ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

```

can you see wireless networks and connect?  If not, what is the output after all those commands of:
```

lshw -C Network
iwlist scan
dmesg | grep -e ndis -e wlan
```

Once we get it to work, you can write a script to run those commands automatically.

---

### Post by nickjhs on 2008-08-23
Just bumping. Still no joy, ssb unloaded though

---

### Post by pytheas22 on 2008-08-23
Sorry it's still not working.  If you're sure ssb is unloaded now (in other words, "lsmod | grep ssb" returns nothing), then what is the output of:
```

lshw -C Network
iwlist scan
dmesg | grep -e ndis -e wlan
```

---

### Post by nickjhs on 2008-08-23
nick@nick-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0f:20:c9:01:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.0.5 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
nick@nick-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

nick@nick-laptop:~$ dmesg | grep -e ndis -e wlan
[   56.605131] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   56.727346] usbcore: registered new interface driver ndiswrapper
nick@nick-laptop:~$ 

Thanks for getting back to me

---

### Post by pytheas22 on 2008-08-24
It seems that ssb doesn't want to unload even though it's on the blacklist.  Let's first write a script so that we can make sure ssb is out of the picture once and for all.

First, open up a file to write a script:
```

sudo gedit /etc/init.d/wifi-fix.sh
```

Add to that file these lines:
```

#!/bin/bash
#this script unloads the ssb module so that it doesn't claim the Broadcom card

rmmod b43
rmmod b44
rmmod b43legacy
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
ifconfig wlan0 up
```

Then save and close the file.  Then run these commands to tell the system to run the script at boot:
```

sudo -s
cd /etc/init.d
chmod +x wifi-fix.sh
update-rc.d wifi-fix.sh defaults
```

Now reboot.  After a reboot, lshw should tell you that ndiswrapper is controlling the card, and hopefully you should be able to connect.  Does this work?

---

### Post by nickjhs on 2008-08-25
I think we are close. To install the script I opened up the text editor, and wrote 

sudo gedit /etc/init.d/wifi-fix.sh

chmod 755 fix

I saved the file as fix 

I wrote chmod ... so that I could open the script using ./fix
using terminal I typed in ./fix and pasted 


#!/bin/bash
#this script unloads the ssb module so that it doesn't claim the Broadcom card

rmmod b43
rmmod b44
rmmod b43legacy
rmmod ssb
rmmod ndiswrapper

The result is 
nick@nick-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0f:20:c9:01:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
nick@nick-laptop:~$ sudo rmmod b43
[sudo] password for nick: 
ERROR: Module b43 does not exist in /proc/modules
nick@nick-laptop:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
nick@nick-laptop:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
nick@nick-laptop:~$ sudo rmmod ssb
ERROR: Module ssb does not exist in /proc/modules
nick@nick-laptop:~$ sudo modprobe ndiswrapper
nick@nick-laptop:~$ dmesg | grep -e ndis -e wlan
[   51.193155] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   51.314284] usbcore: registered new interface driver ndiswrapper
[   59.427664] usbcore: deregistering interface driver ndiswrapper
[   59.472888] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   59.594294] ndiswrapper: driver bcmwl5 (Broadcom,04/21/2005, 3.100.65.1) loaded
[   59.603657] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: dcc08d9d
[   59.603679] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x10e
[   59.603885] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[   59.603914] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   59.603981] ndiswrapper (mp_halt:259): device d9bc2480 is not initialized - not halting
[   59.607106] ndiswrapper: device eth%d removed
[   59.607272] ndiswrapper: probe of 0000:00:09.0 failed with error -22
[   59.613719] usbcore: registered new interface driver ndiswrapper
nick@nick-laptop:~$ uname -m
i686

modprobe ndiswrapper
ifconfig wlan0 up

Again thanks for your help

---

### Post by pytheas22 on 2008-08-25
I'm sorry it still won't work.  The problem is that ndiswrapper still doesn't seem to want to work using the Windows drivers that you've loaded.  I'm not sure why that is, because the ndiswrapper site says that those drivers should work for your particular chipset.

But since they don't, I'm going to suggest that we try a different route--using bcm43xx, a native Linux driver, instead of ndiswrapper.  I think that bcm43xx supports your card (some quick googling suggests so).  Please run this to get the card up with bcm43xx:

```
sudo -s
sed 's/blacklist bcm43xx/#blacklist bcm43xx/g' /etc/modprobe.d/blacklist
apt-get remove --purge ndiswrapper
apt-get install bcm43xx-fwcutter
```

At this point you should be asked if you want to download firmware automatically; say yes.  Then reboot.  After rebooting, your card should work (I know I've said that before!) but if it doesn't, please post:
```

lshw -C Network
dmesg | grep -e bcm -e eth1 -e ndis
ls /lib/firmware
cat /etc/modprobe.d/blacklist | grep bcm
```

---

### Post by nickjhs on 2008-08-26
Na Still not working 

nick@nick-laptop:~$ lhsw -C network
bash: lhsw: command not found
nick@nick-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0f:20:c9:01:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.0.5 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
nick@nick-laptop:~$ dmesg | grep -e bcm -e eth1 -e ndis
[   50.808335] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   50.916352] usbcore: registered new interface driver ndiswrapper
[   58.987085] usbcore: deregistering interface driver ndiswrapper
[   59.032239] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   59.153974] ndiswrapper: driver bcmwl5 (Broadcom,04/21/2005, 3.100.65.1) loaded
[   59.164601] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: dcc0cd9d
[   59.164625] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x10e
[   59.164828] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[   59.164856] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   59.164911] ndiswrapper (mp_halt:259): device db921480 is not initialized - not halting
[   59.164918] ndiswrapper: device eth%d removed
[   59.165048] ndiswrapper: probe of 0000:00:09.0 failed with error -22
[   59.173391] usbcore: registered new interface driver ndiswrapper
nick@nick-laptop:~$ ls /lib/firmware
2.6.24-19-generic     bcm43xx_initval06.fw    bcm43xx_microcode2.fw
bcm43xx_initval01.fw  bcm43xx_initval07.fw    bcm43xx_microcode4.fw
bcm43xx_initval02.fw  bcm43xx_initval08.fw    bcm43xx_microcode5.fw
bcm43xx_initval03.fw  bcm43xx_initval09.fw    bcm43xx_pcm4.fw
bcm43xx_initval04.fw  bcm43xx_initval10.fw    bcm43xx_pcm5.fw
bcm43xx_initval05.fw  bcm43xx_microcode11.fw
nick@nick-laptop:~$ cat /etc/modprobe.d/blacklist | grep bcm
blacklist bcm43xx
blacklist bcm43xx
nick@nick-laptop:~$

---

### Post by pytheas22 on 2008-08-26
The problem is that bcm43xx is on the blacklist.  So open the blacklist:
```

sudo gedit /etc/modprobe.d/blacklist
```

and look for lines that say:
```

blacklist bcm43xx
```

(I think there are two lines.)  Either delete those lines or put a # symbol in front of them (the system will ignore lines beginning with #).  Also add to the blacklist this line, just to make sure ndiswrapper keeps quiet:
```

blacklist ndiswrapper
```

Then save the file and reboot.

If it still doesn't work, please post after the reboot:
```

lsmod | grep -e ndis -e bcm -e b43
lshw -C Network
dmesg | grep -e eth1 -e bcm
iwlist scan
cat /etc/modprobe.d/blacklist | grep -e ndis -e bcm
```

Again, sorry it's so complicated, but thanks for remaining positive and responding quickly.  There's nothing in Linux that you can't solve if you try hard enough!

---

### Post by nickjhs on 2008-08-26
G'day. The battle continues, beggining to wonder if Bill Gates has his hand in this. I have included the blacklist



nick@nick-laptop:~$ lsmod | grep -e ndis -e bcm -e b43
ndiswrapper           192920  0 
bcm43xx               127720  0 
ieee80211softmac       30976  1 bcm43xx
ieee80211              35528  2 bcm43xx,ieee80211softmac
usbcore               146028  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
nick@nick-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0f:20:c9:01:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.0.5 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
nick@nick-laptop:~$ dmesg | grep -e eth1 -e bcm
[   32.351470] bcm43xx driver
[   43.871185] ndiswrapper: driver bcmwl5 (Broadcom,04/21/2005, 3.100.65.1) loaded
nick@nick-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

nick@nick-laptop:~$ cat /etc/modprobe.d/blacklist | grep -e ndis -e bcm
blacklist ndiswrapper
nick@nick-laptop:~$ 






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

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54



# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


blacklist ndiswrapper
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist b43
blacklist b43legacy blacklist ssb

---

### Post by samathyr on 2008-08-26
I have been 2 months struggling with this... I have tried every single method and I can't get this working. Right now my concerns are look for different USB Wireless in different retail stores until I get one working out-of-box.

Anyway I will subscribe to this post and see if there is a solution after all and before I spend my money :(

---

### Post by nickjhs on 2008-08-26
the last issue was solved by putting # in front of the blacklisted bcm drivers, the broadcom card is now working

---

### Post by pytheas22 on 2008-08-26
> the last issue was solved by putting # in front of the blacklisted bcm drivers, the broadcom card is now working 

I'm glad it's fixed now, and sorry again that it ended up being so involved.  Broadcom cards are really usually not that bad, but the major problem with yours was that ndiswrapper didn't want to support it for some reason, even though the stuff I was reading said that it should.

samathyr,

You shouldn't need to spend more money to get wireless.  If you post the output of these commands, I'll try to tell you how to get your Broadcom working (assuming that's what you have):
```

lshw -C Network
lspci -nn
cat /etc/modprobe.d/blacklist
ndiswrapper -l
```

---

