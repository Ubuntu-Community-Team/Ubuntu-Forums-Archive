---
title: "[SOLVED] Weird wireless problem"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by amedac on 2008-08-17
Hello to everyone on this forum. I have very weird wireless problem. Network card is 3945ABG.

My situation is: i'm connected to my wireless network, i can see that in iwconfig and in Network Manager, but i can't ping my router, nor access internet. I was check everything with great help of chili555, but we didn't manage to solve this problem.

Does anyone have similar problem and know how to solve this?

---

### Post by amedac on 2008-08-17
Here is some posts: 
> amedac@amedac-laptop:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1b:77:bd:14:29
Sending on   LPF/eth1/00:1b:77:bd:14:29
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.31 from 192.168.1.1
DHCPREQUEST of 192.168.1.31 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.31 from 192.168.1.1
bound to 192.168.1.31 -- renewal in 126857 seconds.


amedac@amedac-laptop:~$ iwconfig eth1
eth1      IEEE 802.11g  ESSID:"amedac"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:02:CF:A5:EE:52   
          Bit Rate=54 Mb/s   
          RTS thr=1600 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:96/100  Signal level:-34 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Here you can see, i have ip adress and i'm connected on my wireless network, but i don't have internet connection, and i can't ping my router... any sugestions?

---

### Post by pytheas22 on 2008-08-17
Please post the output of these commands:
```

cat /etc/resolv.conf
dmesg | grep -e eth -e iwl
lspci -nn | grep -i intel
```

so that we can figure out what's going on.

---

### Post by amedac on 2008-08-17
Here is outputs: 
> amedac@amedac-laptop:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
**amedac@amedac-laptop**:~$ dmesg |grep -e eth -e iwl
[   14.199817] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[   17.166341] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:1a:4b:61:75:0e
[   17.166615] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[0]
[   17.166678] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   17.227540] Driver 'sd' needs updating - please use bus_type methods
[   17.228107]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   36.694045] wlan0: ethernet device 00:1b:77:bd:14:29 using NDIS driver: netw4x32, version: 0x1000f, NDIS version: 0x501, vendor: 'Intel(R) Wireless WiFi Link 3945ABG Driver', 8086:4222.5.conf
[   37.073219] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   37.073326] udev: renamed network interface wlan0 to eth1
[   37.820259] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   37.820261] tg3: eth0: Flow control is on for TX and on for RX.
[  229.652306] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  229.740318] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=149 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=129 
[  229.992134] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=149 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=129 
[  230.245514] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=149 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=129 
[  230.442556] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=137 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=117 
[  230.530107] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=150 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=130 
[  230.781942] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=150 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=130 
[  231.034774] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=150 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=130 
[  231.234785] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=211 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=191 
[  231.438057] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=121 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=101 
[  232.232656] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=211 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=191 
[  233.471183] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=137 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=117 
[  233.500918] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  233.737889] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=211 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=191 
[  234.385609] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  250.533699] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
[  250.965341] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
[  252.790624] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
[  255.131643] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=149 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=129 
[  255.379494] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=149 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=129 
[  255.628863] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=149 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=129 
[  255.829534] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=210 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=190 
[  256.781139] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
[  256.925293] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=210 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=190 
[  259.015908] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=210 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=190 
[  264.745381] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
[  279.926848] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
[  295.270039] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
[  317.688868] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
[  345.023503] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
[  381.247340] IN=eth0 OUT= MAC= SRC=192.168.1.32 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
**amedac@amedac-laptop:**~$ lspci -nn | grep -i intel
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03)
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)


---

### Post by pytheas22 on 2008-08-17
I see that you're using ndiswrapper to drive your card.  Is there a reason you're not using iwl3945, the native Linux driver, instead?  If not, please try running these commands to switch to the native driver:
```

sudo rmmod ndiswrapper
sudo rmmod iwl3945
suduo modprobe iwl3945
sudo eth1 up
```

Wait a few seconds, then see if you can connect again with better results.  If not, please post:
```

cat /etc/modprobe.d/blacklist | grep iwl
lshw -C Network
dmesg | grep -e iwl
```

---

### Post by amedac on 2008-08-17
when i run > sudo modprobe iwl3945 my laptop is not responding anymore, only thing i can do is to shut it down, and after restart everything is normal, but i still have ndiswrapper, and eth1 interface

---

### Post by amedac on 2008-08-17
Ignore last post, problem was ndisswrapper, i have removed it with Synaptic and now i have loaded iwl3945 driver, but everything is same, no internet

---

### Post by amedac on 2008-08-17
here is outputs: > amedac@amedac-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:18:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:4b:61:75:0e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 ip=192.168.1.32 latency=0 module=tg3 multicast=yes

amedac@amedac-laptop:~$ dmesg | grep -e iwl
amedac@amedac-laptop:~$

 amedac@amedac-laptop:~$ cat /etc/modprobe.d/blacklist | grep iwl
amedac@amedac-laptop:~$ 




Now after laptop restarting i don't have internet at all, i don't have it with ethernet cable nor wireless, and now i don't have any wireless interfaces anymore

---

### Post by pytheas22 on 2008-08-17
Alright, now that you're using iwl3945 again, please reboot your computer.  Then immediately after it restarts, please post the output of these commands (in this order):
```

dmesg | grep -e iwl -e eth1 -e wlan -e ndis
iwlist scan
sudo modprobe iwl3945
iwlist scan
```

---

### Post by amedac on 2008-08-17
Here is output:
> amedac@amedac-laptop:~$ dmesg | grep -e iwl -e eth1 -e wlan -e ndis
[   41.749834] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   41.761980] usbcore: registered new interface driver ndiswrapper

amedac@amedac-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

amedac@amedac-laptop:~$ sudo modprobe iwl3945
[sudo] password for amedac: 

amedac@amedac-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      No scan results

amedac@amedac-laptop:~$ 





---

### Post by pytheas22 on 2008-08-17
Your wired ethernet looks like it should be working, according to the stuff you're posting above, which says that you have an IP address on the wired connection.  Is it still broken?

As for the wireless, ndiswrapper is still being loaded at boot instead of the iwl3945 driver, which is the first part of the problem.  To make sure ndiswrapper is removed completely, run:
```

sudo apt-get remove --purge ndiswrapper*
```

After that, reboot.  If you still don't have any wireless interfaces, please run these commands, in this order, and post the output:
```

lsmod | grep iwl
dmesg | grep -e iwl -e ndis -e eth1
sudo modprobe --verbose iwl3945
cat /etc/modprobe.d/blacklist | grep iwl
```

If you do have wireless again, try connecting, obviously!

By the way, do you recall why you installed ndiswrapper in the first place?  The iwl3945 driver is installed on Hardy by default (you are using Ubuntu Hardy 8.04, right?) so your wireless should have "just worked" out-of-the-box.  Did you have a problem with iwl3945 in the past?

---

### Post by amedac on 2008-08-18
Yes, i'm using 8.04 ubuntu. I have ndiswrapper because i did not make fresh install of ubuntu hardy, i have upgraded it from gutsy.

I don't know how ndis modul is loaded every time, ndis is completely removed from computer...

Here are outputs you asked for, and thank you for helping me:
> amedac@amedac-laptop:~$ sudo apt-get remove --purge ndiswrapper
[sudo] password for amedac: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper
amedac@amedac-laptop:~$ lsmod |grep iwl
amedac@amedac-laptop:~$ dmesg | grep -e iwl -e ndis -e eth1
[   38.554689] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   38.723741] usbcore: registered new interface driver ndiswrapper
amedac@amedac-laptop:~$ sudo modprobe --verbose iwl3945
insmod /lib/modules/2.6.24-19-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko 
insmod /lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko 


> cat /etc/modprobe.d/blacklist | grep iwl don't have output

---

### Post by pytheas22 on 2008-08-18
I don't know why ndiswrapper is being loaded either; it's weird.  But try adding it to the blacklist:
```

sudo -s
echo 'blacklist ndiswrapper' >> /etc/modprobe.d/blacklist
```

After a reboot, ndiswrapper should no longer load and the commands "dmesg | grep ndis" and "lsmod | grep ndis" should return nothing.

If ndiswrapper still seems to be loaded, try running:
```

sudo rmmod ndiswrapper
```

to get rid of it.  Then wait a few seconds and see if wireless works again.

---

### Post by amedac on 2008-08-19
ndiswrapper is tough one on my laptop... After blacklisting, ndis was still showing in ```
lsmod | grep ndis and dmesg |grep ndis
```. 

After that i have run ```
sudo rmmod ndiswrapper
``` and rerun lsmod and dmesg. Lsmod didn't show it again, but dmesg did. So i have restarted computer, thinkin this is it.. But after restart ndis is again in lsmod and dmesg....

---

### Post by un_polle on 2008-08-19
i've got the same card and a similar problem (my pc notice the internet card but i cannot connect to wireless...everything works with the lan cable) 

but if i write in terminal : lshw -C Network

that's my output: 
> 
WARNING: you should run this program as super-user.
  **_*-network DISABLED   _**   
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:19:55:65
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11a
  *-network
       description: Ethernet interface
       product: NetLink BCM5789 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 21
       serial: 00:16:36:3e:3a:f0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5789-v3.49a ip=37.240.94.77 latency=0 module=tg3 multicast=yes


can u tell me how to enable my network?
i'm new to ubuntu...and as soon as i installed it (just a few weeks ago) everything worked fine..but after some updates the wireless stopped working...

---

### Post by amedac on 2008-08-19
try enable your wireless with ```
sudo ifconfig eth1 up
``` or ```
sudo ifconfig wlan0 up
```

if that doesn't help try ```
modprobe iwl3945 
```and after that rerun ifconfig

---

### Post by pytheas22 on 2008-08-19
> ndiswrapper is tough one on my laptop... After blacklisting, ndis was still showing in
Code:

lsmod | grep ndis and dmesg |grep ndis

.

After that i have run
Code:

sudo rmmod ndiswrapper

and rerun lsmod and dmesg. Lsmod didn't show it again, but dmesg did. So i have restarted computer, thinkin this is it.. But after restart ndis is again in lsmod and dmesg....

This is what is happening: after each reboot, the ndiswrapper module is being loaded by the system for some reason.  When you type "sudo rmmod ndiswrapper," the module gets unloaded.  The "lsmod" command tells you which modules are currently activated on your system.  So if "lsmod | grep ndis" returns nothing, ndiswrapper is not activated.  However after you reboot, it will be activated again until you manually remove it with the "rmmod ndiswrapper" command.  We can make ndiswrapper go away permanently later, but for the time being, please reboot, then run:
```

sudo rmmod ndiswrapper
sudo rmmod iwl3945
sudo modprobe iwl3945
sudo ifconfig eth1 up
```

And see if you can connect then using the iwl3945 driver.

'dmesg' just lists messages that have been sent from the kernel since the last restart of your computer...so it's ok to see 'ndiswrapper' mentioned by dmesg even after you have unloaded the ndiswrapper module. 

@un_polle, it looks like your wireless card maybe is turned off by the switch on the outside of your computer.  Make sure it's on.  If you're sure that it is, try running:
```

sudo ifconfig eth1 up
```

If that doesn't help, please post:
```

dmesg | grep iwl
```

---

### Post by amedac on 2008-08-19
Thank you very much for your help, i have solve my problem with fresh install because wireless wasn't my only problem and i lost my tempers... Iwl module work just fine now

---

### Post by pytheas22 on 2008-08-19
Alright, I'm glad it's fixed at least now and sorry you had to reinstall.

un_polle if you're still having trouble, please post the information that I asked for in my last post.

---

### Post by un_polle on 2008-08-20
if i make:
> sudo ifconfig wlan0 up
SIOCSIFFLAGS: Nessun device

cause my wireless should be on wlan0...i dont know what SIOCSIFFLAGS is...

and for dmesg | grep iwl:
>  dmesg | grep iwl
[   29.866391] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   29.866396] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   29.866554] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   29.975269] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   36.043311] iwl3945: Radio disabled by HW RF Kill switch
[  128.316140] iwl3945: Radio disabled by HW RF Kill switch


thanx for helping =)

---

### Post by pytheas22 on 2008-08-20
un_polle,

This message:
```

Radio disabled by HW RF Kill switch 
```

usually means that the wireless card is turned off by a hardware switch, not software.  Check to make sure that the wireless card is enabled in your BIOS.  If it is, is there a switch or button that you use to turn the wireless on and off?  Or maybe you toggle the wireless on and off using function keys (like function+F2).  Please make sure that it's enabled.  Even if the wireless light is on (if you have a wireless light), please try flipping the switch and see if it helps.  The wireless can't work on Ubuntu until the radio is turned on by the hardware.

---

### Post by un_polle on 2008-08-21
mmm thank you.
i'll check right now...

---

