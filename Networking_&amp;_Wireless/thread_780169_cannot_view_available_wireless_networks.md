---
title: "cannot view available wireless networks"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by titibreton on 2008-05-03
Hello,

I have just upgraded to Hardy 8.04 hoping this would fix the inability to access wireless. This did not work on 7.04.

My wireless card chip is a "Broadcom Corporation BCM4309 802.11a/b/g (rev 03)". 

I can connect fine wired but cannot see any wireless networks available. 

Hardware Drivers shows that Broadcom B43 wireless driver is enabled and in use.

Can anyone suggest a simple way to fix this?

Thanks

---

### Post by Ayuthia on 2008-05-03
> **titibreton said:**
> Hello,

I have just upgraded to Hardy 8.04 hoping this would fix the inability to access wireless. This did not work on 7.04.

My wireless card chip is a "Broadcom Corporation BCM4309 802.11a/b/g (rev 03)". 

I can connect fine wired but cannot see any wireless networks available. 

Hardware Drivers shows that Broadcom B43 wireless driver is enabled and in use.

Can anyone suggest a simple way to fix this?

Thanks
Can you post the following:
```
lspci -nn
lshw -C network
lsmod|grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e b44
cat /etc/modprobe.d/blacklist|grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e b44
cat /etc/modules
```
I am guessing that bcm43xx is conflicting with the new b43 driver.  Before you post anything you can try the following:
```
modprobe -r bcm43xx b43 ssb
modprobe b43
```
This will remove the bcm43xx, b43, and ssb modules and then load the b43 and ssb driver (b43 needs ssb so it will automatically load it).

If that doesn't work please do the postings that I requested.  Thanks!

---

### Post by titibreton on 2008-05-03
I don't seem to be able to remove b43. See output below.

thierry@thierry-laptop:~$ modprobe -r bcm43xx b43 ssb
FATAL: Error removing b43 (/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/b43/b43.ko): Operation not permitted

With regards to your suggestion, this is the output:

thierry@thierry-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI6515 Cardbus Controller [104c:8036]
02:01.5 Communication controller [0780]: Texas Instruments PCI6515 SmartCard Controller [104c:8038]
02:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 03)


thierry@thierry-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:22:f4:37
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5751-v3.29a ip=192.168.0.156 latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:14:a5:04:34:eb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


thierry@thierry-laptop:~$ lsmod|grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e b44
b43                   115104  0 
rfkill                  8592  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    32260  1 b43


thierry@thierry-laptop:~$ cat /etc/modprobe.d/blacklist|grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e b44
# replaced by b43 and ssb.
blacklist bcm43xx



thierry@thierry-laptop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp

Does it help? Thanks

---

### Post by Ayuthia on 2008-05-03
Thanks for posting your information.  Everything looks right from that information.  b43 and ssb should be running and bcm43xx and ndiswrapper should not be there.

You might try the modprobe commands that I mentioned before to see if does make a difference.  The only change that I am going to make to is to add the word sudo to it.

```
sudo modprobe -r bcm43xx b43 ssb
sudo modprobe b43
```

If it still doesn't work, can you post your ifconfig, iwconfig, and iwlist scan info?  Thanks!

---

### Post by titibreton on 2008-05-04
Thanks for your further suggestions.

Output of modprobe queries are:

thierry@thierry-laptop:~$ sudo modprobe -r bcm43xx b43 ssb
[sudo] password for thierry: 
thierry@thierry-laptop:~$ sudo modprobe b43
thierry@thierry-laptop:~$ 


Further output for ifconfig, iwconfig and iwlist is as follow:

thierry@thierry-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:22:f4:37  
          inet addr:192.168.0.156  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe22:f437/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:816642 (797.5 KB)  TX bytes:138885 (135.6 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:14:a5:04:34:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89700 (87.5 KB)  TX bytes:89700 (87.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-04-34-EB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

thierry@thierry-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


thierry@thierry-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      No scan results

For info, when I click on the network icon on the top right corner, no wireless networks are shown under "Wireless Network". I did set up manually the wireless connection to my wireless router using "Connect to Other wireless networks" and "Create New Wireless Network" but that did time out without connecting.

I also run "sudo ifconfig eth1 up" to make sure the interface was up.

Let me know if you have any other ideas. Thanks.

---

### Post by titibreton on 2008-05-07
Can anyone help on the wireless problem I have? Any help is much appreciated. Thanks.

---

### Post by Ayuthia on 2008-05-07
Did you use ndiswrapper in Gutsy and then upgraded or is this a fresh install of Hardy?  I only ask because most of the fresh installs have the Broadcom cards start with wlan0 instead of eth1.  

If you are not using any encryption, can you post your /etc/network/interfaces and /etc/udev/rules.d/70-persistent-net.rules?  How close are you to the router?  If you are close, you might try changing the channel on your router just to be sure that we are not running into signal interference.

---

### Post by titibreton on 2008-05-11
This is an upgrade from 7 to 8. I don't think I used ndiswrapper but not 100% sure. 


/etc/network/interfaces is

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


/etc/udev/rules.d/70-persistent-net.rules is

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:12:3f:22:f4:37", ATTRS{type}=="1", NAME="eth0"

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:14:a5:04:34:eb", ATTRS{type}=="1", NAME="eth1"

I went very close to the router (1 meter) and have also tried changing channel but without success.

Is there anything that I should change in the files you mentioned?

Thanks

---

### Post by Ayuthia on 2008-05-11
> **titibreton said:**
> This is an upgrade from 7 to 8. I don't think I used ndiswrapper but not 100% sure. 


/etc/network/interfaces is

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


/etc/udev/rules.d/70-persistent-net.rules is

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:12:3f:22:f4:37", ATTRS{type}=="1", NAME="eth0"

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:14:a5:04:34:eb", ATTRS{type}=="1", NAME="eth1"

I went very close to the router (1 meter) and have also tried changing channel but without success.

Is there anything that I should change in the files you mentioned?

Thanks

You could try commenting out everything in /etc/network/interfaces so that it looks like:
```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```
and then restart the network:
```
sudo /etc/init.d/networking restart
```
I am not for sure if it will change anything, but mine is currently set up to only have the first two lines out there.

---

### Post by titibreton on 2008-05-14
Hello,

I have done the couple of things you mentioned but no success. Should I be able to see the available wireless networks as shown on windows or do I need to connect to a specific network? I did try to connect to the network I have set up and which works well with my other laptop running XP.

Thanks.

---

### Post by Ayuthia on 2008-05-14
> **titibreton said:**
> Hello,

I have done the couple of things you mentioned but no success. Should I be able to see the available wireless networks as shown on windows or do I need to connect to a specific network? I did try to connect to the network I have set up and which works well with my other laptop running XP.

Thanks.
You should be able to see most if not all of the wireless networks as shown on windows.  You should be able to connect to a specific network also.

Let's see if the firmware is there for bcm43xx.  We could try and see if we can get that driver up and running.
```
ls /lib/firmware
```You should be able to see bcm43xx* files in that directory.  If you do have it, you can do the following:
```
sudo modprobe -r b43 ssb
sudo modprobe bcm43xx
sudo ifconfig eth1 up
```

Another option to try is to see if this one uses b43legacy.  It can be done by:
```
sudo modprobe -r b43 ssb
sudo modprobe b43legacy
sudo ifconfig eth1 up
```

If we are not able to bring it up using these options, we might need to go the NDISwrapper route.

EDIT:
I just read another post and it is possible that NetworkManager will not see anything using the bcm43xx driver.  You will need to use the Terminal to see if it works.  So after the sudo ifconfig eth1 up, you will also need to do:
```
sudo iwlist scan
```

---

### Post by titibreton on 2008-05-18
ls /lib/firmware gives:

2.6.20-16-generic     bcm43xx_initval03.fw  bcm43xx_initval10.fw
2.6.22-14-generic     bcm43xx_initval04.fw  bcm43xx_microcode11.fw
2.6.24-16-generic     bcm43xx_initval05.fw  bcm43xx_microcode2.fw
b43                   bcm43xx_initval06.fw  bcm43xx_microcode4.fw
b43legacy             bcm43xx_initval07.fw  bcm43xx_microcode5.fw
bcm43xx_initval01.fw  bcm43xx_initval08.fw  bcm43xx_pcm4.fw
bcm43xx_initval02.fw  bcm43xx_initval09.fw  bcm43xx_pcm5.fw

thierry@thierry-laptop:~$ sudo modprobe -r b43 ssb
thierry@thierry-laptop:~$ 
thierry@thierry-laptop:~$ sudo modprobe bcm43xx
thierry@thierry-laptop:~$ sudo ifconfig eth1 up
thierry@thierry-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:22:f4:37  
          inet addr:192.168.0.156  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe22:f437/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1147560 (1.0 MB)  TX bytes:168827 (164.8 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:14:a5:04:34:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1638 (1.5 KB)
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1682 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1682 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84100 (82.1 KB)  TX bytes:84100 (82.1 KB)

It looks like setting eth1 did the trick and wireless is now working. I can indeed see all the wireless networks available. Thanks very much for your help.

Since eth1 was not up by default if a laptop is wireless enabled, is this a problem with the install?

Thanks again for all your help.

---

### Post by Ayuthia on 2008-05-18
> **titibreton said:**
> ls /lib/firmware gives:

2.6.20-16-generic     bcm43xx_initval03.fw  bcm43xx_initval10.fw
2.6.22-14-generic     bcm43xx_initval04.fw  bcm43xx_microcode11.fw
2.6.24-16-generic     bcm43xx_initval05.fw  bcm43xx_microcode2.fw
b43                   bcm43xx_initval06.fw  bcm43xx_microcode4.fw
b43legacy             bcm43xx_initval07.fw  bcm43xx_microcode5.fw
bcm43xx_initval01.fw  bcm43xx_initval08.fw  bcm43xx_pcm4.fw
bcm43xx_initval02.fw  bcm43xx_initval09.fw  bcm43xx_pcm5.fw

thierry@thierry-laptop:~$ sudo modprobe -r b43 ssb
thierry@thierry-laptop:~$ 
thierry@thierry-laptop:~$ sudo modprobe bcm43xx
thierry@thierry-laptop:~$ sudo ifconfig eth1 up
thierry@thierry-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:22:f4:37  
          inet addr:192.168.0.156  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe22:f437/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1147560 (1.0 MB)  TX bytes:168827 (164.8 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:14:a5:04:34:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1638 (1.5 KB)
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1682 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1682 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84100 (82.1 KB)  TX bytes:84100 (82.1 KB)

It looks like setting eth1 did the trick and wireless is now working. I can indeed see all the wireless networks available. Thanks very much for your help.

Since eth1 was not up by default if a laptop is wireless enabled, is this a problem with the install?

Thanks again for all your help.

I don't think that there was a problem with the install, but there is a problem with your card not working with the b43 drivers.  It could be possible that your issue is tied to a patch that could not be applied before the final release of 8.04.

---

