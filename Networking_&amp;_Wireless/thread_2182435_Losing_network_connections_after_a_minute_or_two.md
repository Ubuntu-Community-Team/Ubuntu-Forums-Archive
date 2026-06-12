---
title: "Losing network connections after a minute or two"
date: 2013-10-21
forum: Networking &amp; Wireless
---

### Post by EDKJkYT on 2013-10-21
Hey guys, 

   I switched to Ubuntu 12.04 about two weeks ago, and I've had some problems with it. I have a Dell Inspiron 6400, and I'm running a dual boot system with Windows XP and Ubuntu. Since installing, I have updated Ubuntu to 12.10. The wireless has never really worked, but when I tried to fix it, I came close to getting it all fixed. I got to the point where the wireless was actually enabled, but the firmware was not installed for the wireless card. As I was installing the firmware, I got the option to update. I went ahead and updated even though I probably should have waited until I was done with the firmware. The update crashed, and I essentially have lost my ethernet connection now too. Whenever I boot the machine, I have a wired connection for a minute or two and an enabled wireless connection (still no firmware), but then the connection is lost and I can't reconnect.     

I am 100% new to Ubuntu, so I really don't know what I need to do to fix the problem. I've been googling and searching for as much information that I can find, but I just don't know enough about how Ubuntu works to make a lot of progress on my own. My two big goals are to get the wireless and ethernet back up and running. I'll post some of the results from networking terminal commands down below, but please let me know if there's any other stuff that you guys need to see to help me.

    During the first minute or two, while the networks are still working, here are the results for ifconfig and iwconfig.  
The ifconfig:
  ```
 
 eth1       
Link encap:Ethernet  HWaddr 00:19:b9:6e:5a:84             
 inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0            
inet6 addr: fe80::219:b9ff:fe6e:5a84/64 Scope:Link            
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1            
RX packets:323 errors:0 dropped:0 overruns:0 frame:0            
TX packets:123 errors:0 dropped:0 overruns:0 carrier:0            
collisions:0 txqueuelen:1000             
RX bytes:48976 (48.9 KB)  TX bytes:16482 (16.4 KB)            
Interrupt:17    

 lo         
Link encap:Local Loopback             
 inet addr:127.0.0.1  Mask:255.0.0.0           
 inet6 addr: ::1/128 Scope:Host            
UP LOOPBACK RUNNING  MTU:16436  Metric:1            
RX packets:20 errors:0 dropped:0 overruns:0 frame:0           
 TX packets:20 errors:0 dropped:0 overruns:0 carrier:0            
collisions:0 txqueuelen:0            
 RX bytes:1388 (1.3 KB)  TX bytes:1388 (1.3 KB)
  
```

    and the iwconfig:
  ```
 
 lo       
  no wireless extensions.    

eth1      
 no wireless extensions.   

 wlan0      
IEEE 802.11bg  ESSID:off/any             
 Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm               
Retry  long limit:7   RTS thr:off   Fragment thr:off            
Power Management:on 
 
```

    Here's the "sudo lshw -C network" before the ethernet and wireless have been lost:
  ```
   
*-network                        
description: Network controller        
 product: BCM4311 802.11b/g WLAN         
vendor: Broadcom Corporation        
 physical id: 0        
 bus info: pci@0000:0b:00.0        
 version: 01         
width: 32 bits         
clock: 33MHz         
capabilities: pm msi pciexpress bus_master cap_list        
 configuration: driver=b43-pci-bridge latency=0        
 resources: irq:16 memory:ecffc000-ecffffff   

*-network         
description: Ethernet interface        
 product: BCM4401-B0 100Base-TX        
vendor: Broadcom Corporation         
physical id: 0        
 bus info: pci@0000:03:00.0        
 logical name: eth1         
version: 02        
 serial: 00:19:b9:6e:5a:84        
 size: 100Mbit/s         
capacity: 100Mbit/s         
width: 32 bits         
clock: 33MHz         
capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation        
 configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.5 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s        
 resources: irq:17 memory:ecbfe000-ecbfffff     

*-network DISABLED         
description: Wireless interface         
physical id: 2        
 logical name: wlan0        
 serial: 00:19:7e:61:13:f0        
 capabilities: ethernet physical wireless         
configuration: broadcast=yes driver=b43 driverversion=3.2.0-54-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg 
 
``` 

   All of the following results are for after the network connections have been lost.
  ifconfig:
  ```

 lo        
 Link encap:Local Loopback             
 inet addr:127.0.0.1  Mask:255.0.0.0           
 inet6 addr: ::1/128 Scope:Host           
 UP LOOPBACK RUNNING  MTU:16436  Metric:1            
RX packets:16 errors:0 dropped:0 overruns:0 frame:0            
TX packets:16 errors:0 dropped:0 overruns:0 carrier:0            
collisions:0 txqueuelen:0             
RX bytes:1076 (1.0 KB)  TX bytes:1076 (1.0 KB)  

```

    iwconfig:  
```

 lo        
 no wireless extensions.
 
```

sudo lshw -C network:
  ```
  
 *-network                       
 description: Network controller         
product: BCM4311 802.11b/g WLAN        
 vendor: Broadcom Corporation        
 physical id: 0        
 bus info: pci@0000:0b:00.0        
 version: 01        
 width: 32 bits        
 clock: 33MHz        
 capabilities: pm msi pciexpress bus_master cap_list        
 configuration: driver=b43-pci-bridge latency=0        
 resources: irq:16 memory:ecffc000-ecffffff    

 *-network        
 description: Ethernet interface       
  product: BCM4401-B0 100Base-TX       
  vendor: Broadcom Corporation       
  physical id: 0        
 bus info: pci@0000:03:00.0        
 logical name: eth1        
 version: 02        
 serial: 00:19:b9:6e:5a:84         
size: 100Mbit/s        
 capacity: 100Mbit/s         
width: 32 bits         
clock: 33MHz        
 capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation        
 configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.5 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s        
 resources: irq:17 memory:ecbfe000-ecbfffff   

  *-network DISABLED         
description: Wireless interface        
 physical id: 2         
logical name: wlan0         
serial: 00:19:7e:61:13:f0        
 capabilities: ethernet physical wireless       
  configuration: broadcast=yes driver=b43 driverversion=3.2.0-54-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg 
 
```    

rfkill list:
  ```
 
1: hci0: Bluetooth     
 Soft blocked: no      
Hard blocked: no 
 2: dell-wifi: Wireless LAN      
Soft blocked: no      
Hard blocked: no 
 3: dell-bluetooth: Bluetooth      
Soft blocked: no     
 Hard blocked: no 
 
```


      Thanks  Jeff

---

### Post by Hadaka on 2013-10-21
Hi, it looks like you have the correct driver loaded, but
Let's rattle it's cage a bit and see what transpires..
please do..
* you "may" get an error or "not found" on some of these
but do each one anyway.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer

```
BOOT.....the wired side "should be now working.
From the wired connection..connected to the internet plase do..
```
sudo apt-get update
sudo apt-get upgrade
```
once completed..then do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
Working correctly now??

---

### Post by EDKJkYT on 2013-10-21
Ok, I have run into some trouble. I tried running the first two commands that you gave me, but both of them weren't able to complete. Both seemed to be working ok, but then they ran into a "segmentation fault" and stopped running. I left the command terminal open for over an hour on the first command after it ran into the segmentation fault, but it wasn't able to go any farther.

When I ran, ```
sudo apt-get remove --purge bcmwl-kernel-source
```
Here are my results,
```
jeff@jeff-MM061:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for jeff:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
jeff@jeff-MM061:~$ sudo dpkg --configure -a
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Removing old bcmwl-6.20.155.1+bdcom DKMS files...
 
-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.20.155.1+bdcom
Kernel:  3.2.0-54-generic-pae (i686)
-------------------------------------
 
Status: Before uninstall, this module version was ACTIVE on this kernel.
 
wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-54-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
 
depmod.........
 
DKMS: uninstall completed.
 
------------------------------
Deleting module version: 6.20.155.1+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-54-generic-pae
Building for architecture i686
Building initial module for 3.2.0-54-generic-pae
Done.
 
wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-54-generic-pae/updates/dkms/
 
depmod....
 
DKMS: install completed.
Segmentation fault
```

And when I ran,
```
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
```
I got:
```
jeff@jeff-MM061:~$ sudo get-apt remove --purge b43-fwcutterfirmware-b43-installer[sudo] password for jeff:
sudo: get-apt: command not found
jeff@jeff-MM061:~$ sudo apt-get remove --purge b43-fwcutterfirmware-b43-installer
E: dpkg was interrupted, you must manually run 'sudo dpkg--configure -a' to correct the problem.
jeff@jeff-MM061:~$ sudo dpkg --configure -a
Setting up bcmwl-kernel-source(6.20.155.1+bdcom-0ubuntu0.0.2) ...
Removing old bcmwl-6.20.155.1+bdcom DKMS files...
 
-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.20.155.1+bdcom
Kernel:  3.2.0-54-generic-pae(i686)
-------------------------------------
 
Status: Before uninstall, this module version was ACTIVE onthis kernel.
 
wl.ko:
 - Uninstallation
   - Deleting from:/lib/modules/3.2.0-54-generic-pae/updates/dkms/
 - Original module
   - No original modulewas found for this module on this kernel.
   - Use the dkmsinstall command to reinstall any previous module version.
 
depmod.........
 
DKMS: uninstall completed.
 
------------------------------
Deleting module version: 6.20.155.1+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-54-generic-pae
Building for architecture i686
Building initial module for 3.2.0-54-generic-pae
Done.
 
wl:
Running module version sanity check.
 - Original module
   - No original moduleexists within this kernel
 - Installation
   - Installing to/lib/modules/3.2.0-54-generic-pae/updates/dkms/
 
depmod....
 
DKMS: install completed.
Segmentation fault

```


I did notice on the second command that my wired internet disappeared almost simultaneously with the segmentation fault. But after rebooting after both commands, my wired internet is still doing the same thing as before.

---

### Post by Hadaka on 2013-10-21
do you have a solid wired connection?

---

### Post by wildmanne39 on 2013-10-21
That means you can not install any applications because you have a problem with the apt system do as it says and run:
```
sudo dpkg--configure -a
```
Then try the commands again it may give another error after that just keep watching.

---

### Post by EDKJkYT on 2013-10-22
Ok, so I ran
```
sudo dpkg --configure -a
```
It ran for a while before it stopped working. I let it run about 30 minutes after it stalled, but it made no further progress. I wasn't able to proceed to the other two commands. Here is what the terminal printed out up to that point.

```

jeff@jeff-MM061:~$ sudo dpkg --configure -a
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Removing old bcmwl-6.20.155.1+bdcom DKMS files...
 
------------------------------
Deleting module version: 6.20.155.1+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-54-generic-pae
Building for architecture i686
Building initial module for 3.2.0-54-generic-pae
Done.
 
wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-54-generic-pae/updates/dkms/
 
depmod........
 
DKMS: install completed.
Segmentation fault
 

```

This seems to be the same place and error that I received before. Maybe it's this command that my pc's having trouble with? 

I rebooted and retried to run
```
sudo dpkg --configure -a
```
just to make sure that the same thing happened. This time when I tried the command, I got
```
sudo dpkg --configure -a
dpkg: error: dpkg status database is locked by another process

```

As far as I know, there aren't any other processes running. I booted the pc and opened the terminal window. Other than that, I haven't touched a thing since booting the machine.


Hadaka, the wired connection should be solid. I had been using it for several days without any problems before all of my problems popped up. Unfortunately, the wired connection is still having the same problem where it drops connectivity, and I can't seem to recover the connection.

---

### Post by Hadaka on 2013-10-22
ok, from the wired connection please do..
```
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a
```
then do..
```
sudo apt-get update
sudo apt-get upgrade
```
BOOT
then do..
```
sudo apt-get install linux-firmware-nonfree 
sudo modprobe b43
```
thanks.

---

### Post by EDKJkYT on 2013-10-23
Thanks for the reply Hadaka.

I have mixed results from this last attempt.

I was successfully able to run the code:
```
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a

```

Unfortunately I no longer have any access to the wired internet. It has totally disappeared somehow. I don't really know what happened to it. On one of my reboots (I had several of them while I was trying these commands), the internet just didn't connect upon booting the pc. The networking option is still enabled, but the pc is just not finding the wired connection. The wireless is also still enabled and missing the firmware, so it has essentially remained the same.

Ultimately, the command
```
sudo apt-get update
```
failed because of the lack of internet connectivity.

---

### Post by Hadaka on 2013-10-23
Hi, please do..
```
sudo modprobe b44
```
is the wired now working?

---

### Post by EDKJkYT on 2013-10-24
Yes, my wired internet is working now as well as the wireless. Since the wired connection turned back on, I tried running the commands you had given me in the previous posts. In all I ran,

```

sudo modprobe b44
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

```

At this point, I rebooted like you suggested. After rebooting, I ran:

```

sudo modprobe b44
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43

```

For some reason, I had to run the "sudo modprobe b44" again to get the wired internet to connect. Other than that though, everything started working perfectly. I rebooted again to double check that everything was indeed working correctly. Neither the wired internet or the wireless was working upon reboot. The command terminal wasn't working for me either, so I just went ahead and rebooted a third time. Upon rebooting this time, I had to run "sudo modprobe b44" again, but everything was (and is) working perfectly. I have wireless and wired internet that are both working now. I think everything is good to go. Thank you so much for your help!

---

### Post by Hadaka on 2013-10-24
Great !, glad that it is working for you.
if you are satisfied with the results,please
mark your thread solved. Thank.
How to->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

