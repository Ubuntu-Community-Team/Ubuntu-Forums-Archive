---
title: "USB Installation...Internet not working..."
date: 2010-07-12
forum: New to Ubuntu
---

### Post by phatdaz on 2010-07-12
Hiya All,

Alright, so i'm a complete and utter novice at Linux in general and i thought i'd give it a go. I downloaded Ubuntu 10.4 and installed it on a usb hdd. I'm using it on a Lenovo 3000 N200 laptop btw.

I did the usual...reboot and run off the usb and worked fine. 

The problem starts when i try to connect to the net. the 'network manager' finds the connection...default name as 'auto eth0.' no worries there. When i start the already installed Firefox, it doesnt do anything..it just keeps on 'looking for...' and thats it!

I googled and found the command 'ifconfig'  Tried that, and it finds the ip of the laptop and such. so it should be working!...i think.  Soooo.......

Any...ABSOLUTELY! Any!! comments/suggestions would be welcome to solve this issue. (go easy on me tho :D) 

thanks a lot!
daz

---

### Post by mikewhatever on 2010-07-12
Start with the basics:
1. provide info about the connection (wired/wireless, modem/router).
2. post the outputs of the following:
ifconfig
sudo lshw -C network

---

### Post by phatdaz on 2010-07-13
Hello Mike,

Here's what i have/use.
1) Its a wired connection, straight from the wall socket to my laptop. Works fine with Windows, DHCP is enabled, so no static IP n all that.

2) ifconfig results...
ubuntu@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:08:24:e9  
          inet addr:192.168.15.113  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fe08:24e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2756 (2.7 KB)  TX bytes:4469 (4.4 KB)
          Interrupt:19 

3) sudo lshw -C network results
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:ae:b5:d5
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:29 memory:f8000000-f8000fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:08:24:e9
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v3.03 ip=192.168.15.113 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:c8000000-c800ffff


appreciate the reply.

---

### Post by phatdaz on 2010-07-13
Alright!!! its working now! :D  tbh was browsing thru the forums and found some thread about something similar as well. followed the command set given...
mtr -n -c3 -r 4.4.4.4
mtr -c3 -r ubuntu.com
wget ubuntu.com  

dont know what it did but it worked!!  now i just gotta read up on all the commands for the terminal! 

cheers mike for taking the time to reply though!

---

