---
title: "Again Problems with bcm43xx Broadcom"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by jan quark on 2007-12-20
Yea again the Broadcom post I know there are many out there... but

I always manage to enable the firmware via fxcutter, i have a stable internet connection for a while and then the bitrate drops to 1 MBit.
Nothing helps. I have tried many different web browser like FF, Epiphany, Flock and Opera. Its always the same. Inet becomes slow and then stops to load pages at all. I will post here my network settings and hardware information soon when the fresh install of Gutsy on my laptop is finished.

On my other desktop PC with AVM Wlan  usb stick  with  Gutsy installed everything worked out of the box.

Update 1

Fresh install of Gutsy on laptop.
Broadcom firmware installed via fxcutter. Green light ist on everything OK till now.
Dowloading the updates with 160 kB/s. Its a normal avarage download rate for my inet connection. But my problems always started after that so fingers crossed.

---

### Post by GSF1200S on 2007-12-20
> **jan quark said:**
> Yea again the Broadcom post I know there are many out there... but

I always manage to enable the firmware via fxcutter, i have a stable internet connection for a while and then the bitrate drops to 1 MBit.
Nothing helps. I have tried many different web browser like FF, Epiphany, Flock and Opera. Its always the same. Inet becomes slow and then stops to load pages at all. I will post here my network settings and hardware information soon when the fresh install of Gutsy on my laptop is finished.

On my other desktop PC with AVM Wlan  usb stick  with  Gutsy installed everything worked out of the box.

Update 1

Fresh install of Gutsy on laptop.
Broadcom firmware installed via fxcutter. Green light ist on everything OK till now.
Dowloading the updates with 160 kB/s. Its a normal avarage download rate for my inet connection. But my problems always started after that so fingers crossed.

You might consider using ndiswrapper and a windows driver- thats what I did on my second lappie and my bitrate is 54MBps! Just pick any broadcom tutorial for ndiswrapper and we'll help you with any problems...

---

### Post by jan quark on 2007-12-20
Thanks,

wright now iam online with the laptop. But.. (see above)

When the update download is finished  Iam going to try the ndiswrapper thing. One additional remark : I have only a wireless network connection, so I have to download all needed files BEFORE I disable the fxcutter firmware. Or I have to  transport all files via usb stick. Many tutorials start with the sentence: To enable your internet connection type sudo apt-get install blah blah... and I must always laugh because I try to get online and the first thing I must do to get online is to get online. :) You see my point.? :)

---

### Post by GSF1200S on 2007-12-20
> **jan quark said:**
> Thanks,

wright now iam online with the laptop. But.. (see above)

When the update download is finished  Iam going to try the ndiswrapper thing. One additional remark : I have only a wireless network connection, so I have to download all needed files BEFORE I disable the fxcutter firmware. Or I have to  transport all files via usb stick. Many tutorials start with the sentence: To enable your internet connection type sudo apt-get install blah blah... and I must always laugh because I try to get online and the first thing I must do to get online is to get online. :) You see my point.? :)

I would install ndiswrapper and possibly the gui for loading the windows driver- also the windows driver for the card as well.

And dont remove the fxcutter firmware- just disable and reboot, then if things go sour you can enable them and get back online for help.

If the tutorial guide you use doesnt get you online, be sure to copy the results of the following commands to a text file before you revert to the fxcutter:

iwconfig

iwlist scanning

lshw -C network

cat /etc/network/interfaces

---

### Post by fs3rp4 on 2007-12-20
Don't forget to add bcm43xx in to blacklist . Unless it will load togheter with ndiswrapper on boot.

---

### Post by GSF1200S on 2007-12-20
> **fs3rp4 said:**
> Don't forget to add bcm43xx in to blacklist . Unless it will load togheter with ndiswrapper on boot.

Good call- I forgot about the blacklist! Thanks ;)

---

### Post by jan quark on 2007-12-20
Update 3 
Internet stoped working on the laptop. I didnt even have the chance to install build essential to compile ndiswrapper. Iam searching just now for the missing libc6-dev package on packages.ubuntu.com.

---

### Post by jan quark on 2007-12-20
OK here some stats.
```
michal@michal-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Nasza1309siec"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:15:0C:64:1C:BE   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=55/100  Signal level=-79 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

michal@michal-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:15:0C:64:1C:BE
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=80/100  Signal level=-79 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 76ms ago

michal@michal-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:15:0C:64:1C:BE
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=81/100  Signal level=-77 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 172ms ago
          Cell 02 - Address: 00:15:0C:64:1C:BE
                    ESSID:"Nasza1309siec"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=82/100  Signal level=-75 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 212ms ago

michal@michal-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:47:bb:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=192.168.178.23 latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:5d:de:8e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 latency=64 module=b44 multicast=yes
michal@michal-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth1 inet static
address 192.168.178.23
netmask 255.255.255.0
gateway 192.168.178.1
wireless-key s:xxxxxxxxxxxxxx
wireless-essid Nasza1309siec

auto eth1

```

---

### Post by GSF1200S on 2007-12-20
When your networking leaves you, what happens if you put in this command:

sudo /etc/init.d/networking restart


The results you posted use the fxcutter driver. We can see what happens if we try the network from the command line (not that hard), but if youre going the ndiswrapper route, lets see what happens after thats installed. I notice you run a static setup- im used to dhcp, so ill have to read up on that.

---

### Post by jan quark on 2007-12-20
Here we go. I followed these instructions [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
Everything worked fine. I had no failure reports during the installation and compilation whatsoever. I used the newest Ndiswrapper 1.51. And Internet still does not work. I tried to come back to the old bcm43xx cutter thing but with no success. 

The Best Thing Now.

I am online during the live session of Gutsy install process. I decided to make a fresh install and my Inet is working fast and stable. I used the fxcutter method. But I cant stay forever in the live session of Ubuntu.

So it is possible to have a working inet. Could it be that some updates mess something up?
Or that some applications I install are in conflict with the bcm43xx drivers?
Sorry for the very unspecific questions but I cant really figure out whats wrong.

OK I will finish the installation now and hopefully I can still post the outcome of it.

I will post some stats from the Live session just in case. Everything is working now perhaps we will find some changes after the installation.```
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Nasza1309siec"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:15:0C:64:1C:BE   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=60/100  Signal level=-74 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:15:0C:64:1C:BE
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=88/100  Signal level=-68 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 452ms ago
          Cell 02 - Address: 00:15:0C:64:1C:BE
                    ESSID:"Nasza1309siec"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=89/100  Signal level=-65 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 220ms ago

ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:47:bb:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=192.168.178.23 latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:5d:de:8e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 latency=64 module=b44 multicast=yes
ubuntu@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth1 inet static
address 192.168.178.23
netmask 255.255.255.0
gateway 192.168.178.1
wireless-key s:xxxxxxxxxxxxx
wireless-essid Nasza1309siec

auto eth1

```
but it looks pretty much the same

---

### Post by jan quark on 2007-12-20
Gutsy is installed and inet is working like a breeze. It must be something with the updates thats messes things up. But there are now 149 possible updates for me. Can I ignore them? Or should I download them?

---

### Post by jan quark on 2007-12-20
I downloaded them and inet stopped to work.

---

### Post by jan quark on 2007-12-20
Bump, since I am not updating the fwcutter software to a newer version my inet seems to be stable, no crashes or looses of the connection. Can this be the problem?

---

