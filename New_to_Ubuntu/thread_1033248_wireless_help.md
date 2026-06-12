---
title: "wireless help"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by dsmcginn on 2009-01-07
i updated to 8.10 last week...while using 8.04 i used this thread to help me with my wireless and it worked like a charm!
[http://ubuntuforums.org/showthread.p...ghlight=AR242x](http://ubuntuforums.org/showthread.p...ghlight=AR242x)

but now it doesn't work, and i can't figure it out. i tried this thread..but it didn't work either.
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

any suggestions?

here's what i get when i run a few commands...maybe they'll help you out:

doug@doug-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11g ESSIDff/any
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Bit Rate:54 Mb/s
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

pan0 no wireless extensions.

doug@doug-laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:1b:24:16:be:ac
inet addr:192.168.1.6 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::21b:24ff:fe16:beac/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:5132 errors:0 dropped:0 overruns:0 frame:0
TX packets:4891 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4863529 (4.8 MB) TX bytes:891560 (891.5 KB)
Interrupt:16

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:6 errors:0 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:376 (376.0 B) TX bytes:376 (376.0 B)

wlan0 Link encap:Ethernet HWaddr 00:19:7e:3f:6d:d3
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:17 Memory:54100000-54110000
doug@doug-laptop:~$ sudo lshw -C network
[sudo] password for doug:
*-network
description: Ethernet interface
product: 88E8038 PCI-E Fast Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 14
serial: 00:1b:24:16:be:ac
size: 100MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.6 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
*-network
description: Wireless interface
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0
version: 01
serial: 00:19:7e:3f:6d:d3
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,06/21/2007,5.3.0.56 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 52:eb:49:b9:82:27
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
doug@doug-laptop:~$

ps i'm kinda new to ubuntu, so bare with me!
=)
thanks in advance!!!

---

### Post by moore.bryan on 2009-01-07
your links didn't work for me, so i might be going back over things, but i do have a question: why are you using ndiswrapper if you have an atheros chipset, which is now supported natively in the linux kernel released for intrepid?

---

### Post by dsmcginn on 2009-01-07
hmmm...that's a good question...i'm not too sure. i was just doing what the threads told me to do. haha.

so what should i do?

---

### Post by dsmcginn on 2009-01-07
ps try these links!
=)

[http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x)

and 

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

### Post by ugm6hr on 2009-01-07
You useed ndiswrapper in Hardy (link broken in your post).  The upgrade has broken that driver.

The Intrepid How-to you used (I edited the link above) assumes a "fresh" install - hence it doesn't work.

You can use that 2nd how-to, if you blacklist ndiswrapper, ath_hal and ath_pci, and ensure ath5k is not blacklisted.

EDIT:
I realise you are just following instructions. Post the output from:
```
cat /etc/modprobe.d/blacklist
```

We'll take it from there.

---

### Post by dsmcginn on 2009-01-07
doug@doug-laptop:~$ cat /etc/modprobe.d/blacklist
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
doug@doug-laptop:~$

---

### Post by moore.bryan on 2009-01-07
i couldn't put it better myself! once again, a cheer for ubuntu forum staff!

---

### Post by ugm6hr on 2009-01-07
To add the ndiswrapper to blackilst (and others):
```
echo 'blacklist ndiswrapper' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist ath_hal' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist ath_pci' | sudo tee -a /etc/modprobe.d/blacklist

```

Then install the new driver:
```
sudo apt-get install linux-backports-modules-intrepid
echo ath5k | sudo tee -a /etc/modules
```

EDIT:
Post results from:
```
cat /etc/modules
```
Make sure ndiswrapper isn't there.  If it is:
```
gksudo gedit /etc/modules
```
Remove it and save.

Then reboot, and keep fingers crossed.

---

### Post by dsmcginn on 2009-01-07
it was there, so i deleted and saved and this is what it showed:

doug@doug-laptop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ath5k
doug@doug-laptop:~$ 

i rebooted and nothing. =( network manager shows no WAPs.

---

### Post by ugm6hr on 2009-01-07
Did you install the backports-modules package?

If yes - post the output from:
```
lshw -class network
```

---

### Post by dsmcginn on 2009-01-07
i'm not sure if i did or not...lol. how would i know? or find out?

doug@doug-laptop:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:16:be:ac
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.6 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7e:3f:6d:d3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:a1:45:87:14:29
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
doug@doug-laptop:~$

---

### Post by dsmcginn on 2009-01-07
and yes i did install the backport modules...lol. or at least theyre installed. intrepid and intrepid-generic are the two installed...i don't need the server or virtual ones, do i?

---

### Post by ugm6hr on 2009-01-07
```
configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
```
This suggests the driver is installed.

Now try:
```
iwconfig
```

---

### Post by dsmcginn on 2009-01-07
doug@doug-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

doug@doug-laptop:~$

---

### Post by ugm6hr on 2009-01-07
Try:
```
iwlist scan
```

---

### Post by dsmcginn on 2009-01-07
doug@doug-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

doug@doug-laptop

---

### Post by TrakerJon on 2009-01-07
Procedure to enable WPA Wireless in Ubuntu 8.10

If you have wired Internet connectivity update the software sources list sudo apt-get update

sudo apt-get install wpasupplicant (may already be installed)

sudo apt-get install network-manager-gnome network-manager (may already be installed)

sudo gedit /etc/network/interfaces Comment out the lines without “lo” entries (using #) and save the file, if you have just installed Ubuntu this may not be necessary.

Create a file by: sudo gedit /etc/default/wpasupplicant, add entry ENABLED=0 and save the file.

sudo touch /etc/default/wpasupplicant

Reboot your system.

---

### Post by dsmcginn on 2009-01-08
> **TrakerJon said:**
> Procedure to enable WPA Wireless in Ubuntu 8.10

If you have wired Internet connectivity update the software sources list sudo apt-get update

sudo apt-get install wpasupplicant (may already be installed)

sudo apt-get install network-manager-gnome network-manager (may already be installed)

sudo gedit /etc/network/interfaces Comment out the lines without “lo” entries (using #) and save the file, if you have just installed Ubuntu this may not be necessary.

Create a file by: sudo gedit /etc/default/wpasupplicant, add entry ENABLED=0 and save the file.

sudo touch /etc/default/wpasupplicant

Reboot your system.

that didnt work...
=(

---

### Post by dsmcginn on 2009-01-08
does anyone else have any suggestions?!?! lol. i LOVE linux...but it's really annoying when i have to plug into the modem everytime i wanna do something. lol.

---

### Post by Vantrax on 2009-01-08
I would actually recommend a clean install, your chipset is supported so it should work on a liveCD + the driver so you can test it out before installing.

It seems most of the problems come from trying to fix a fix you used before without really understanding what it was doing. Trying to reverse that will likely be harder than just re installing and configuring again. Just make sure you back up your home first.

---

### Post by ugm6hr on 2009-01-08
> **Vantrax said:**
> I would actually recommend a clean install, your chipset is supported so it should work on a liveCD + the driver so you can test it out before installing.

This is a sensible option, and may prove the least time consuming.

Just install the backports-module package after a fresh install.

---

### Post by dsmcginn on 2009-01-09
okk...so i did a fresh install, got all the updates and did the backport modules. but nothing shows up in my network manager! =( here's some info:
doug@doug-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

doug@doug-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:16:be:ac  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe16:beac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1359 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1421262 (1.4 MB)  TX bytes:221153 (221.1 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:3f:6d:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-7E-3F-6D-D3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

doug@doug-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

doug@doug-laptop:~$ sudo lshw -C network
[sudo] password for doug: 
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:16:be:ac
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.6 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7e:3f:6d:d3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ca:a6:7a:f4:6f:22
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
doug@doug-laptop:~$

---

