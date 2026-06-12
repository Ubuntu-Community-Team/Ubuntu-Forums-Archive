---
title: "AR928X trouble"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by steeb on 2009-12-01
Hello all, 2 day old frustrated newb here. Spent the last 2 days searching for a fix to a most popular problem, wish I new about this before "switching" to Ubuntu. After a windows death I installed Ubuntu 9.10 after hearing everyone over the years gushing about how great & effortless Linux was, I haven't had the same great time. My wireless does not work at all, can't even get the button to turn blue when I push it now. "Enable wireless" is greyed out. sudo ifconfig wlan0 up, does not work. I have had the enjoyment of reading page after page of people with the same trouble and alot of stuff that is over my head. I have the Atheros AR928X, drivers are installed/tried using "Windows" drivers/followed some command scripts, nothing has worked so far. Why is there not a "package" to download that fixes this yet? Seems like a pretty big problem.
I am able to ethernet connect to post this.

INFO :
parents@smith6-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

parents@smith6-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

parents@smith6-laptop:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:78:aa:c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.103 latency=0 multicast=yes
       resources: irq:27 ioport:3000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4d:1d:f5:51
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:d2600000-d260ffff

parents@smith6-laptop:~$ uname -a
Linux smith6-laptop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux


parents@smith6-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic

parents@smith6-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:78:aa:c0  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe78:aac0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25810815 (25.8 MB)  TX bytes:1961751 (1.9 MB)
          Interrupt:27 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


parents@smith6-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Smith Extender"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


parents@smith6-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


parents@smith6-laptop:~$ ping -c 3 208.67.219.101
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.

--- 208.67.219.101 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms


parents@smith6-laptop:~$ ping -c 3 [www.opendns.com](www.opendns.com)
PING [www.opendns.com](www.opendns.com) (208.69.38.150) 56(84) bytes of data.
64 bytes from 208.69.38.150: icmp_seq=1 ttl=49 time=68.9 ms
64 bytes from 208.69.38.150: icmp_seq=2 ttl=49 time=65.3 ms
64 bytes from 208.69.38.150: icmp_seq=3 ttl=49 time=69.2 ms

--- [www.opendns.com](www.opendns.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10335ms
rtt min/avg/max/mdev = 65.345/67.845/69.270/1.786 ms

---

### Post by lkraemer on 2009-12-01
I just purchased a Compaq CQ61-313US with that exact same Wifi setup
(AR9285) and when I booted the LiveCD to install to a clean Hard Drive
my Wifi works right from the LiveCD.

Why don't you boot the liveCD and give that a try?  You also might want
to do a MD5SUM on the ISo to VERIFY that your ISO is correct.  I normally
just use K3B and verify the ISO from there.

lk

---

### Post by steeb on 2009-12-02
Booting Live CD does not make a difference. Thanks for the suggestion. I am open to any others. Please.

---

### Post by steeb on 2009-12-02
OK md5sum shows my ISO is incorrect. My question now is how many times do I have to download the file before I get a good one? working on my 4th now!!!!

---

### Post by sandyd on 2009-12-02
> **steeb said:**
> OK md5sum shows my ISO is incorrect. My question now is how many times do I have to download the file before I get a good one? working on my 4th now!!!!
use bittorent.
bittorent automatically md5sums each part and will automatically redownload them if it finds inconsistency)

---

### Post by steeb on 2009-12-02
OK downloaded using bit torrent then md5sum & checked it & still does not match any on the web site. What to do now? Thanks

---

### Post by steeb on 2009-12-02
downloaded another torrent from a different mirror & it checks out good. going to try to burn a good disk now. wish me luck.

---

### Post by 3rdalbum on 2009-12-02
> **steeb said:**
> OK downloaded using bit torrent then md5sum & checked it & still does not match any on the web site. What to do now? Thanks

If the torrent is completed, then it's okay.

Connect your computer to your router with an Ethernet cable. It should get a connection from that. Now go into Synaptic Package Manager and click the Reload button (this will load the list of available packages).

Close Synaptic and go into Hardware Drivers. Is there any driver listed there that you can activate?

---

### Post by bkratz on 2009-12-02
Please see posts 5-7 of this thread, where they seem to have it working

[http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X](http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X)

Hope it helps you.

---

### Post by steeb on 2009-12-02
3rdalbum- reloaded & nothing in the drivers

bkratz- checking it now

When I burn a disk & md5sum it I keep getting "Input/output error"  on 2 tries???

---

### Post by steeb on 2009-12-03
ok I am a newb & trying to learn, so I am unclear about this fix

"I commented the ath_pci blacklist in /etc/modprobe.d/blacklist-ath_pci.conf."
( I assume this means commenting it out with # ) ??

"You check if ath9k (or ath5k) is loaded in /etc/modules"
(I got this)

"echo ath9k | sudo tee -a /etc/modules"
(did this & it is just sitting there with no response now)

"Then you install
linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic (and linux-backports-modules-wireless-karmic-generic-pae if you can but I didn't need it)"
(not sure how to do this part)???


Any suggestions??

---

### Post by steeb on 2009-12-03
ok, re-installed 9.10/updated packages/installed modules listed before & still no wireless. I can push my wifi button, it turns blue for about 7 seconds then turn back to amber. Any other suggestions? need wireless to work, kids are home schooled. even though I hate it I will have to give up and buy Windows7 if I can't get this to work tomorrow.

---

