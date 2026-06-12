---
title: "Please me connect to wireless so i can move on!"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by cathdc on 2010-02-10
Hello! I am new to Ubuntu and after 3 days of searching “how to connect wireless internet” I still have had no luck! I am afraid I could have messed something up by entering codes to troubleshoot something I know nothing about. Is there anyone out there who can help and provide me with step by step directions to get me wireless internet? I feel like I can't move on the explore the rest of  the Ubuntu  world until I get this wireless issue resolved. Thank you!
 

 Here are my details:
 Installed Ubuntu 8.04
  on a Toshiba Satellite A205 – S5804 Laptop
 No Windows, Ubuntu is my only OS
 The 1st day I had no wireless network interface, but after clicking this and punching in that it appeared.
 When I go to “connect to other wireless network” I can “connect” to the wireless network, but I am unable to go online. I am also unable to view other available networks.
 

 From what I understand, I need to download a driver (but from where) and install it using ndiswrapper? Is this correct or am I reading waaay too much into this?
 

 Here is also a copy of my attempted troubleshooting effort.


cathdc1001@cathdc1001-laptop:~$ sudo lshw -C newtwork
sudo: unable to resolve host cathdc1001-laptop
[sudo] password for cathdc1001: 
cathdc1001@cathdc1001-laptop:~$ sudo lshw -C network
sudo: unable to resolve host cathdc1001-laptop
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:97:6a:be
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:92:8d:e8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
cathdc1001@cathdc1001-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Channel=20  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

cathdc1001@cathdc1001-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:97:6a:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:38897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30631 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31018274 (29.5 MB)  TX bytes:5252622 (5.0 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57000 (55.6 KB)  TX bytes:57000 (55.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:92:8d:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

cathdc1001@cathdc1001-laptop:~$

---

### Post by The Toxic Mite on 2010-02-10
Hey!

How come you are using 8.04? That version is pretty outdated...

---

### Post by cathdc on 2010-02-10
Hello! I am new to Ubuntu and after 3 days of searching “how to connect wireless internet” I still have had no luck! I am afraid I could have messed something up by entering codes to troubleshoot something I know nothing about. Is there anyone out there who can help and provide me with step by step directions to get me wireless internet? I feel like I can't move on the explore the rest of the Ubuntu world until I get this wireless issue resolved. Thank you!
 

 Here are my details:
 Installed Ubuntu 8.04
  on a Toshiba Satellite A205 – S5804 Laptop
 No Windows, Ubuntu is my only OS
 The 1st day I had no wireless network interface, but after clicking this and punching in that it appeared.
When I go to “connect to other wireless network” I can “connect” to the wireless network, but I am unable to go online. I am also unable to view other available networks.
 

 From what I understand, I need to download a driver (but from where) and install it using ndiswrapper? Is this correct or am I reading waaay too much into this?
 

 Here is also a copy of my attempted troubleshooting effort.


cathdc1001@cathdc1001-laptop:~$ sudo lshw -C newtwork
sudo: unable to resolve host cathdc1001-laptop
[sudo] password for cathdc1001: 
cathdc1001@cathdc1001-laptop:~$ sudo lshw -C network
sudo: unable to resolve host cathdc1001-laptop
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:97:6a:be
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:92:8d:e8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
cathdc1001@cathdc1001-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Channel=20  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:eek:n   Fragment thr:eek:ff
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

cathdc1001@cathdc1001-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:97:6a:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:38897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30631 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31018274 (29.5 MB)  TX bytes:5252622 (5.0 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57000 (55.6 KB)  TX bytes:57000 (55.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:92:8d:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

cathdc1001@cathdc1001-laptop:~$

---

### Post by cathdc on 2010-02-10
8.04 was the only installation disk I had at the time. Is it easy to upgrade and would this solve my wireless internet connection difficulties?

---

### Post by Iowan on 2010-02-10
It appears that you may have changed the host name in either */etc/hostname* or */etc/hosts* (but not both) to cause the "sudo: unable to resolve host..." problem. [This]("http://www.psychocats.net/ubuntu/fixsudo") *might* help with that.
[Here]("http://ubuntuforums.org/showthread.php?t=892678") is a similar **Toshiba Satellite A205 S5804** thread.

BTW, Hardy is old - but still supported through [URL="https://wiki.ubuntu.com/Releases"]April 2011 (Desktop)
[/URL]

---

### Post by cariboo on 2010-02-10
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by cathdc on 2010-02-10
I decided to start over. I am downloading 9.10 at this moment and I plan to install soon. I am still new to Ubuntu so any tips on what I need to do 1st will be helpful. My number#1 priority is to make sure I have wireless internet access. 
If anyone thinks installing 9.10 is a good/bad idea, please let me now why. I am thinking that installing 9.10 before I get sucked in to 8.04 will save me time of learning something new twice.

---

### Post by cathdc on 2010-02-10
> **cariboo907 said:**
> Please don't create multiple threads on the same subject, I have merged your two threads.
Ok. Sorry. I had a hard time figuring out what thread I should post to.

---

