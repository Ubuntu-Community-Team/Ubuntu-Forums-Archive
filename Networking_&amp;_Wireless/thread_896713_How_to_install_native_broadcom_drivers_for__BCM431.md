---
title: "How to install native broadcom drivers for  BCM4311, BCM4312, BCM4321, and BCM4322"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by mike_l on 2008-08-21
After searching for ways to get wireless working on my HP dv9000, I came across [this thread.]("http://ubuntuforums.org/showthread.php?t=850913") Apparently, Broadcom offers linux drivers for it's 802.11a/b/g/n cards (chipsets BCM4311, BCM4312, BCM4321, and BCM4322, in both 32 and 64 bit).

Figuring that there are other people out there with the same problem: here's the steps I took to install the native drivers:

[LIST=1]
[*]**Download the appropriate driver**
I downloaded the 64 bit version of the driver from [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")
It's important that you get the correct version, as the 32 and 64 bit versions are not compatible. 

[*]**Make the .ko file**
First, make a temporary directory 
```
mkdir wdriver 

```
... and place the downloaded package into it (hybrid-portsrc-_64_5_10_27_6.tar.gz, or hybrid-portsrc-x86_32_5_10_27_6.tar.gz for the 32 bit version)
Then 'cd' into the temporary directory and un-tar the file. 
```
cd wdriver
tar -xzf hybrid-portsrc-x86_64_5_10_27_6.tar.gz 

```
Now, we want to make the wl.ko file, so we enter: 
(<2.6.xx.xx> is your kernel version: mine was "2.6.24-19-generic". Use tab-completion to find yours.)
```
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`

```
You should now have a file "wl.ko" located in the temporary directory you created (wdriver). 
[*]**Make sure that no other wireless drivers are installed**
Enter: (Don't worry if there are any errors returned)
```
sudo rmmod bcm43xx
sudo rmmod b43
sudo rmmod b43legacy

```
I also uninstalled ndiswrapper, just to be sure:
```
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-common 

```

[*]**Test the new wireless driver**
Now, lets test out our new wireless driver. Enter:
```
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko 

``` 

If it worked, and you can see/connect to wireless networks, you'll want to:
[*]**Make your changes permanent.**
First, you may want to blacklist the old b43/b43legacy/bcm43xx drivers. Enter:
```
sudo gedit /etc/modprobe.d/blacklist
```
and add the following to the end of the file:
```
blacklist b43
blacklist b43legacy
blacklist bcm43xx
```

Now, let's move the wireless driver somewhere more permenant:
```
sudo mkdir /lib/modules/<2.6.xx.xx>/wlan
sudo mv wl.ko /lib/modules/<2.6.xx.xx>/wlan
```
Now, lets make it so that the driver and wireless encryption module are loaded on startup. Enter:
```

sudo gedit /etc/modules

```
and add
```
ieee80211_crypt_tkip
```
to the bottom.

Now run:
```
sudo gedit /etc/rc.local
```
and add
```
sudo insmod /lib/modules/<2.6.xx.xx>/wlan/wl.ko

```
at the end of the file, but before the line "exit 0"

That's it. If I've made any errors, please let me know. Thanks.

[/LIST]

---

### Post by Ayuthia on 2008-08-21
> **mike_l said:**
> 
Now, lets make it so that the driver and wireless encryption module are loaded on startup. Enter:
```

sudo gedit /etc/modules

```
and add
```
ieee80211_crypt_tkip
```
to the bottom.

Now run:
```
sudo gedit /etc/rc.local
```
and add
```
sudo insmod /lib/modules/<2.6.xx.xx>/wlan/wl.ko

```
at the end of the file, but before the line "exit 0"

That's it. If I've made any errors, please let me know. Thanks.

[/LIST]

You don't really need to do the stuff I quoted above. What you need to do is the following:
```
sudo depmod -a
echo wl |sudo tee -a /etc/modules
```
The depmod -a command will update your modules list.  After that, you will be able to automatically load the module in /etc/modules or if you want to load it manually:
```
sudo modprobe wl
```

The ieee80211_crypt_tkip will automatically be loaded when the modprobe wl is done.


EDIT:
Another tidbit is that instead of using <2.6.xx.xx>, you can just use `uname -r`.  This will provide your kernel info.  For example:
```
sudo insmod /lib/modules/`uname -r`/wlan/wl.ko
```

One other thing, it does look like this module might be included in the next linux-restricted-modules update.  It is currently being tested.

---

### Post by smalldog on 2008-08-26
The driver seems work well under normal condition. However, it already halted when after ssh session authentication complete. In addition, it never using WPA(1/2) to build the wireless connection. But it still works under WEP mode. I am looking for solution for long time and I will switch to using ndiswrapper instead of wl, since most users reported ndiswrapper haven't above mentioned problem. Good luck:confused:

---

### Post by smalldog on 2008-08-28
The best solution that I find is follow the link to upgrade the kernel [http://ubuntuforums.org/showthread.php?mode=hybrid&t=880218]("http://ubuntuforums.org/showthread.php?mode=hybrid&t=880218"). WPA connection no problem. ssh connection no problem. Good luck to every people. Thanks a lot, superm1

---

### Post by rol801 on 2008-09-08
> **Ayuthia said:**
> You don't really need to do the stuff I quoted above. What you need to do is the following:
```
sudo depmod -a
echo wl |sudo tee -a /etc/modules
```
The depmod -a command will update your modules list.  After that, you will be able to automatically load the module in /etc/modules or if you want to load it manually:
```
sudo modprobe wl
```

The ieee80211_crypt_tkip will automatically be loaded when the modprobe wl is done.


EDIT:
Another tidbit is that instead of using <2.6.xx.xx>, you can just use `uname -r`.  This will provide your kernel info.  For example:
```
sudo insmod /lib/modules/`uname -r`/wlan/wl.ko
```

One other thing, it does look like this module might be included in the next linux-restricted-modules update.  It is currently being tested.



"sudo modprobe wl" cant load it up.. i've try many times but still fail.


but it work while you use " insmod" is fine... very strange actually

---

### Post by Ayuthia on 2008-09-08
> **rol801 said:**
> "sudo modprobe wl" cant load it up.. i've try many times but still fail.


but it work while you use " insmod" is fine... very strange actually

Where did you place the wl.ko file?  The file has to be located in /lib/firmware/`uname -r` in order for it to work.  Also did you run sudo depmod -a after moving the file there?

---

### Post by hajk on 2008-09-08
> **Ayuthia said:**
> Where did you place the wl.ko file?  The file has to be located in /lib/firmware/`uname -r` in order for it to work.  Also did you run sudo depmod -a after moving the file there?
I have a success story for the Broadcom 4328 rev 05 device in my Apple MacBook Pro. I just moved the wl.ko file to the /lib/modules/2.2..../misc/ directory, then ran "depmod -a" and loaded the module through a script:```

#!/bin/sh
rmmod ssb
modprobe wl
modprobe ssb
```
which I've called /usr/local/bin/wireless and put in /etc/rc.local. As you can guess, the ssb module on my computer interferes, so wl.ko must be loaded first. 

Broadcom claim that this module is "version-agnostic", so should work for any 2.6 kernel. Throughput is fine, but the reported signal strenght gets funny readings, the network-manager icon is white most of the time, there is the occasional reconnect after some period of inactivity. I'm using it right now with the AP (an Apple Airport Extreme Base Station) in mixed b/g/n mode using the 2.4GHz band, still to try using pure 802.11n and 5GHz.

Edit: Yes, pure 802.11n (draft) mode in the 5GHz band works, but doesn't show an increase in speed AFAICT. Those disconnects seem to occur after a period of inactivity; reconnecting takes place promptly whenever needed, so probably a feature to preserve battery power.

---

### Post by vibhor goyal on 2008-10-21
[QUOTE=mike_l;5636495]


[*]**Test the new wireless driver**
Now, lets test out our new wireless driver. Enter:
```
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko 

``` 

Hi,
when I get to thsi step, I get this error :

insmod: error inserting 'wl.ko': -1 File exists

Please help me out. I have the temp folder on the desktop. By the error I thought it means that file already exists but wireless doesn't work :(

---

### Post by vibhor goyal on 2008-10-21
ok.. so an update to my previous post. So I did a rmmod to remove the wl.ko drive and then did insmod again and it didn't give any error this time, but sadly the wireless still doesn't work :(

---

### Post by Ayuthia on 2008-10-21
> **vibhor goyal said:**
> [QUOTE=mike_l;5636495]


[*]**Test the new wireless driver**
Now, lets test out our new wireless driver. Enter:
```
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko 

``` 

Hi,
when I get to thsi step, I get this error :

insmod: error inserting 'wl.ko': -1 File exists

Please help me out. I have the temp folder on the desktop. By the error I thought it means that file already exists but wireless doesn't work :(

Can you post the results of the following:
```
lsmod |grep -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
uname -r
lshw -C network
```
It might be possible that the wl driver is already there and other modules are causing a conflict.

---

### Post by vibhor goyal on 2008-10-21
thats what I get:

```


root@vbgoz-laptop:/home/vbgoz/Desktop/hyb# lsmod |grep -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
wl                   1081920  0 
ieee80211_crypt         8192  2 wl,ieee80211_crypt_tkip
root@vbgoz-laptop:/home/vbgoz/Desktop/hyb# uname -r
2.6.24-21-generic
root@vbgoz-laptop:/home/vbgoz/Desktop/hyb# lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:38:aa:fc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:8d:29:c6
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
root@vbgoz-laptop:/home/vbgoz/Desktop/hyb# 

```

---

### Post by Ayuthia on 2008-10-21
> **vibhor goyal said:**
> thats what I get:

```


root@vbgoz-laptop:/home/vbgoz/Desktop/hyb# lsmod |grep -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
wl                   1081920  0 
ieee80211_crypt         8192  2 wl,ieee80211_crypt_tkip
root@vbgoz-laptop:/home/vbgoz/Desktop/hyb# uname -r
2.6.24-21-generic
root@vbgoz-laptop:/home/vbgoz/Desktop/hyb# lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:38:aa:fc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:8d:29:c6
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
root@vbgoz-laptop:/home/vbgoz/Desktop/hyb# 

```

What happens when you do:
```
sudo iwlist scan
```
The information that you show looks like it is fine.  I just want to see if the card can scan wireless sites through the command line.

---

### Post by PinkFloyd102489 on 2008-10-21
Any word whether this module will do monitor mode and/or packet injection? Id really, really like to get injection on my BCM4328 rev03. Currently using the wl driver included in the Ubuntu kernel.

---

### Post by Ayuthia on 2008-10-21
> **PinkFloyd102489 said:**
> Any word whether this module will do monitor mode and/or packet injection? Id really, really like to get injection on my BCM4328 rev03. Currently using the wl driver included in the Ubuntu kernel.

As far as I know, it does not.  I could be wrong though.  I think that you would have better chances that the b43 driver for your card would be done before the wl driver gets that capability.  I say this because the wl driver is proprietary so I can't see this capability being implemented.  Of course, there are no facts behind my words.

---

### Post by vibhor goyal on 2008-10-21
> **Ayuthia said:**
> What happens when you do:
```
sudo iwlist scan
```
The information that you show looks like it is fine.  I just want to see if the card can scan wireless sites through the command line.


that's what I get:
```

lo     Interface doesn't support scanning.

eth0   Interface doesn't support scanning.

eth1   Failed to read scan data : Invalid argument


```

---

### Post by vibhor goyal on 2008-10-23
somebody plz help me out with this bcm4322 issue..

---

### Post by PinkFloyd102489 on 2008-10-23
> **vibhor goyal said:**
> somebody plz help me out with this bcm4322 issue..

You're probably ahead just to use the wl driver that comes with Ubuntu. It works well out of the box on just about every Broadcom chip. It does for my BCM4328.

---

### Post by vibhor goyal on 2008-10-24
> **PinkFloyd102489 said:**
> You're probably ahead just to use the wl driver that comes with Ubuntu. It works well out of the box on just about every Broadcom chip. It does for my BCM4328.

it didn't work for me.

---

### Post by slugicide on 2008-10-24
I have BCM4328 and the driver Ubuntu offers doesn't work.  How'd you do it?

---

### Post by PinkFloyd102489 on 2008-10-24
> **slugicide said:**
> I have BCM4328 and the driver Ubuntu offers doesn't work.  How'd you do it?


System > Administration > Hardware Drivers


If it still doesnt work when enabled, do:

```

sudo lshw -C Network

```

If the wireless interface has wl listed but isnt working, run this script (assuming you have a broadcom ethernet card also).

```

#!/bin/bash
sudo rmmod b44
sudo rmmod ssb
sudo rmmod wl
sudo modprobe wl
sudo modprobe ssb
sudo modprobe b44
sudo ifconfig

```

---

### Post by slugicide on 2008-10-24
ERROR: Module ssb is in use by b43
ERROR: Module wl does not exist in /proc/modules
FATAL: Module wl not found.
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15868 (15.8 KB)  TX bytes:15868 (15.8 KB)

---

### Post by PinkFloyd102489 on 2008-10-24
```

sudo apt-get install linux-restriced-modules-`uname -r`

```

Then run the script.

---

### Post by Ayuthia on 2008-10-24
> **PinkFloyd102489 said:**
> ```

sudo apt-get install linux-restriced-modules-`uname -r`

```

Then run the script.

Just a correction.  It should read:
```
sudo apt-get install linux-restricted-modules-`uname -r`
```

If you did not know already, you will need to have 2.6.24-21 or higher to get the Broadcom STA (wl) driver.  Otherwise it will not be in linux-restricted-modules.

---

### Post by PinkFloyd102489 on 2008-10-24
Sorry, I typo'd. :-P

---

### Post by slugicide on 2008-10-24
linux-restricted-modules-2.6.24-19-generic is already the newest version.

---

### Post by Ayuthia on 2008-10-24
Do you have an internet connection in Ubuntu?  If so, you need to run an update on your computer:
```
sudo aptitude update
sudo aptitude safe-upgrade
```

If you don't, you will need to do the steps in the first post of this thread.

EDIT:  Ok, I might be confused.  This thread says you are trying to get the wl driver in 2.6.24 (Hardy) and this [thread]("http://ubuntuforums.org/showthread.php?p=6028139") shows you are using 2.6.27 (Intrepid).  Are you trying to do both?

---

### Post by slugicide on 2008-10-24
I'm terribly sorry about talking in two threads.  It's kind of rude.
I have never had wireless in 2.6.27 (but I did have fglrx), but was trying to figure out how.  In the course of doing this I was advised to get rid of ndiswrapper, but when I did that I lost wireless in the kernel I had been logging into, 2.6.24 Intrepid (which did not have fglrx).
I'm still just trying to get wireless.  3D effects can totally wait, as long as I can turn my homework in on time.  Thanks for your patience and help!

---

### Post by Ayuthia on 2008-10-25
> **slugicide said:**
> I'm terribly sorry about talking in two threads.  It's kind of rude.
I have never had wireless in 2.6.27 (but I did have fglrx), but was trying to figure out how.  In the course of doing this I was advised to get rid of ndiswrapper, but when I did that I lost wireless in the kernel I had been logging into, 2.6.24 Intrepid (which did not have fglrx).
I'm still just trying to get wireless.  3D effects can totally wait, as long as I can turn my homework in on time.  Thanks for your patience and help!
Don't worry about the two threads.  I was thinking that you were trying to get the wireless working in both versions.  The wl driver comes with Intrepid (2.6.27) and in Hardy it came in the 2.6.24-21 release (for your card).

If you were using Intrepid with 2.6.27, the wl driver should be there for you.  However, if you installed 2.6.27 in Hardy yourself, it will not because Ubuntu packaged the wl driver in linux-restricted-modules-2.6.27.

I have heard that the wl module works better than ndiswrapper for your card, but you should still be able to use either one.

---

### Post by slugicide on 2008-10-25
OK, I'm going to log into 2.6.27 Intrepid right now.  Afer that, what should I do to get the wl driver working?

---

### Post by Ayuthia on 2008-10-25
> **slugicide said:**
> OK, I'm going to log into 2.6.27 Intrepid right now.  Afer that, what should I do to get the wl driver working?

It should just be a matter of going into System->Administration->Hardware Drivers and enabling the Broadcom STA option.

---

### Post by slugicide on 2008-10-25
I'm in 2.6.27-7 Intrepid, and when I go to Hardware Drivers I am told that Broadcom B43 driver is active.  That being the case I still don't have wireless and the wireless light on my laptop is not lit.  There is no Broadcom STA option.

---

### Post by Ayuthia on 2008-10-25
> **slugicide said:**
> I'm in 2.6.27-7 Intrepid, and when I go to Hardware Drivers I am told that Broadcom B43 driver is active.  That being the case I still don't have wireless and the wireless light on my laptop is not lit.  There is no Broadcom STA option.

Try this:
```
sudo /etc/init.d/linux-restricted-modules-common start
```Then see if the Broadcom STA or wl option is available.  If it is not, please do the following:
```
sudo updatedb
locate wl.ko
```

---

### Post by slugicide on 2008-10-25
rodney@rodney-laptop:~$ sudo /etc/init.d/linux-restricted-modules-common start
[sudo] password for rodney: 
 * Preparing restricted drivers...                                                                                                            [ OK ] 
rodney@rodney-laptop:~$ sudo updatedb
rodney@rodney-laptop:~$ locate wl.ko
rodney@rodney-laptop:~$ 
Hardware Drivers still says I have Broadcom B43 installed and active.  There is no STA option, and wireless is still non-functioning.

---

### Post by Ayuthia on 2008-10-25
If that is the case, I would just go ahead and try out the steps in the original post of this thread.

I am not for sure why it is not showing up.  It looks like the restricted modules are there, but for some reason the wl.ko file is not there.

---

### Post by slugicide on 2008-10-25
rodney@rodney-laptop:/opt/wdriver$ make -C /lib/modules/2.6.24-19-generic/build M=`pwd` clean
make: *** /lib/modules/2.6.24-19-generic/build: No such file or directory.  Stop.
rodney@rodney-laptop:/opt/wdriver$ 

As you can see the original post is not working for me.  Ye gods!

---

### Post by Ayuthia on 2008-10-25
> **slugicide said:**
> rodney@rodney-laptop:/opt/wdriver$ make -C /lib/modules/2.6.24-19-generic/build M=`pwd` clean
make: *** /lib/modules/2.6.24-19-generic/build: No such file or directory.  Stop.
rodney@rodney-laptop:/opt/wdriver$ 

As you can see the original post is not working for me.  Ye gods!

Do you have build-essential installed?  Not for sure if that is what is causing the problem.  The actual issue is that /lib/modules/2.6.24-19.generic/build is not pointing to /usr/src/linux-headers-2.6.24-19-generic.  Do you know if linux-headers-2.6.24-19-generic is installed?

---

### Post by slugicide on 2008-10-25
sudo sudo apt-get install linux-headers-2.6.24-19-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.24-19-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-19-generic has no installation candidate

---

### Post by Ayuthia on 2008-10-25
> **slugicide said:**
> sudo sudo apt-get install linux-headers-2.6.24-19-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.24-19-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-19-generic has no installation candidate

Can you post the results of:
```
aptitude search linux-headers
```
I would like to see what versions are available.

---

### Post by slugicide on 2008-10-25
```
rodney@rodney-laptop:~$ aptitude search linux-headers
v   linux-headers                                                      -                                                                             
v   linux-headers-2.6                                                  -                                                                             
i   linux-headers-2.6.24-20                                            - Header files related to Linux kernel version 2.6.24                         
i   linux-headers-2.6.24-21                                            - Header files related to Linux kernel version 2.6.24                         
p   linux-headers-2.6.25-2-386                                         - Linux kernel headers for version 2.6.25 on i386                             
p   linux-headers-2.6.27-3-rt                                          - Linux kernel headers for version 2.6.27 on Ingo Molnar's full real time pree
i   linux-headers-2.6.27-5                                             - Header files related to Linux kernel version 2.6.27                         
i   linux-headers-2.6.27-5-generic                                     - Linux kernel headers for version 2.6.27 on x86/x86_64                       
i   linux-headers-2.6.27-6                                             - Header files related to Linux kernel version 2.6.27                         
i   linux-headers-2.6.27-6-generic                                     - Linux kernel headers for version 2.6.27 on x86/x86_64                       
i   linux-headers-2.6.27-7                                             - Header files related to Linux kernel version 2.6.27                         
i   linux-headers-2.6.27-7-generic                                     - Linux kernel headers for version 2.6.27 on x86/x86_64                       
p   linux-headers-2.6.27-7-server                                      - Linux kernel headers for version 2.6.27 on x86/x86_64                       
p   linux-headers-386                                                  - Linux kernel headers on 386                                                 
i   linux-headers-generic                                              - Generic Linux kernel headers                                                
v   linux-headers-lbm                                                  -                                                                             
v   linux-headers-lbm-2.6                                              -                                                                             
p   linux-headers-lbm-2.6.27-7-generic                                 - Header files related to linux-backports-modules version 2.6.27              
p   linux-headers-lbm-2.6.27-7-server                                  - Header files related to linux-backports-modules version 2.6.27              
p   linux-headers-rt                                                   - Rt Linux kernel headers                                                     
p   linux-headers-server                                               - Linux kernel headers on Server Equipment.                                   
p   linux-headers-virtual                                              - Linux kernel headers for virtual machines                                   
rodney@rodney-laptop:~$ 

```

---

### Post by Ayuthia on 2008-10-25
Did you ugrade from Hardy to Intrepid?  I just noticed that you have 2.6.24 and 2.6.27 in the same system.  That is probably what is causing the problem.  What you might want to do is boot into 2.6.27-7 and try to compile the drivers there.  Check and see what /lib/modules/2.6.27-7-generic/build shows:
```
ls -l /lib/modules/2.6.27-7-generic/build
```If all is correct, it should point to /usr/src/linux-headers-2.6.27-7-generic.  If this is the case, you will need to compile the wl driver in that kernel.

---

### Post by slugicide on 2008-10-25
All is correct.  Following the intructions, I get stopped at step two.  No wl.ko file is created.

```
rodney@rodney-laptop:~/wdriver$ make -C /lib/modules/2.6.27-7-generic/build M=`pwd` clean
make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
rodney@rodney-laptop:~/wdriver$ make -C /lib/modules/2.6.27-7-generic/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/rodney/wdriver/built-in.o
  CC [M]  /home/rodney/wdriver/src/wl/sys/wl_linux.o
  CC [M]  /home/rodney/wdriver/src/wl/sys/wl_iw.o
/home/rodney/wdriver/src/wl/sys/wl_iw.c: In function ‘wl_iw_get_scan’:
/home/rodney/wdriver/src/wl/sys/wl_iw.c:934: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:934: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:934: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/rodney/wdriver/src/wl/sys/wl_iw.c:934: error: too few arguments to function ‘iwe_stream_add_event’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:939: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:939: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:939: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:939: error: too few arguments to function ‘iwe_stream_add_point’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:947: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:947: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:947: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/rodney/wdriver/src/wl/sys/wl_iw.c:947: error: too few arguments to function ‘iwe_stream_add_event’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:955: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:955: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:955: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/rodney/wdriver/src/wl/sys/wl_iw.c:955: error: too few arguments to function ‘iwe_stream_add_event’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:961: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:961: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:961: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/rodney/wdriver/src/wl/sys/wl_iw.c:961: error: too few arguments to function ‘iwe_stream_add_event’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:973: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:973: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:973: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:973: error: too few arguments to function ‘iwe_stream_add_point’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:981: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:981: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:981: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:981: error: too few arguments to function ‘iwe_stream_add_point’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:992: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:992: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:992: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:992: error: too few arguments to function ‘iwe_stream_add_point’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1006: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1006: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1006: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1006: error: too few arguments to function ‘iwe_stream_add_point’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1016: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1016: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1016: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1016: error: too few arguments to function ‘iwe_stream_add_value’
make[1]: *** [/home/rodney/wdriver/src/wl/sys/wl_iw.o] Error 1
make: *** [_module_/home/rodney/wdriver] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
rodney@rodney-laptop:~/wdriver$ ls
built-in.o
hybrid-portsrc-x86_32_5_10_27_6.tar.gz
lib
Makefile
src
rodney@rodney-laptop:~/wdriver$ 
```

---

### Post by Ayuthia on 2008-10-25
> **slugicide said:**
> All is correct.  Following the intructions, I get stopped at step two.  No wl.ko file is created.

```
rodney@rodney-laptop:~/wdriver$ make -C /lib/modules/2.6.27-7-generic/build M=`pwd` clean
make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
rodney@rodney-laptop:~/wdriver$ make -C /lib/modules/2.6.27-7-generic/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/rodney/wdriver/built-in.o
  CC [M]  /home/rodney/wdriver/src/wl/sys/wl_linux.o
  CC [M]  /home/rodney/wdriver/src/wl/sys/wl_iw.o
/home/rodney/wdriver/src/wl/sys/wl_iw.c: In function ‘wl_iw_get_scan’:
/home/rodney/wdriver/src/wl/sys/wl_iw.c:934: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:934: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:934: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/rodney/wdriver/src/wl/sys/wl_iw.c:934: error: too few arguments to function ‘iwe_stream_add_event’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:939: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:939: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:939: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:939: error: too few arguments to function ‘iwe_stream_add_point’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:947: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:947: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:947: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/rodney/wdriver/src/wl/sys/wl_iw.c:947: error: too few arguments to function ‘iwe_stream_add_event’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:955: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:955: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:955: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/rodney/wdriver/src/wl/sys/wl_iw.c:955: error: too few arguments to function ‘iwe_stream_add_event’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:961: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:961: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:961: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/rodney/wdriver/src/wl/sys/wl_iw.c:961: error: too few arguments to function ‘iwe_stream_add_event’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:973: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:973: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:973: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:973: error: too few arguments to function ‘iwe_stream_add_point’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:981: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:981: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:981: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:981: error: too few arguments to function ‘iwe_stream_add_point’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:992: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:992: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:992: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:992: error: too few arguments to function ‘iwe_stream_add_point’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1006: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1006: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1006: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1006: error: too few arguments to function ‘iwe_stream_add_point’
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1016: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1016: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1016: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/rodney/wdriver/src/wl/sys/wl_iw.c:1016: error: too few arguments to function ‘iwe_stream_add_value’
make[1]: *** [/home/rodney/wdriver/src/wl/sys/wl_iw.o] Error 1
make: *** [_module_/home/rodney/wdriver] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
rodney@rodney-laptop:~/wdriver$ ls
built-in.o
hybrid-portsrc-x86_32_5_10_27_6.tar.gz
lib
Makefile
src
rodney@rodney-laptop:~/wdriver$ 
```
I forgot that 2.6.27 needs a patch.  Here is the link to the patch:
[http://jaux.net/uploads/2008/10/hybrid_wl-5.10.27.6_patch-2.6.27](http://jaux.net/uploads/2008/10/hybrid_wl-5.10.27.6_patch-2.6.27)

You will need to copy the patch to the directory where you do the make command.  From there, you will need to enter the following:
```
patch -p1 < hybrid_wl-5.10.27.6_patch-2.6.27
``` and then try to do the make command again.

---

### Post by slugicide on 2008-10-25
That worked in creating the wl.ko file.  Unfortunately when I got to step 4, testing the driver, I found I still had no wireless.  No change.

---

### Post by Ayuthia on 2008-10-25
> **slugicide said:**
> That worked in creating the wl.ko file.  Unfortunately when I got to step 4, testing the driver, I found I still had no wireless.  No change.
Ok.  Stay in the directory where the wl.ko file is and try the following:
```
sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko
sudo /etc/init.d/networking restart
sudo iwlist scan
```

---

### Post by slugicide on 2008-10-25
rodney@rodney-laptop:~/wdriver$ sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
FATAL: Module ssb is in use.

---

### Post by Ayuthia on 2008-10-25
> **slugicide said:**
> rodney@rodney-laptop:~/wdriver$ sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
FATAL: Module ssb is in use.
Can you make sure that you do not have a b44 module for your wired card?  It will be listed in lshw -C network.  You can try the following:
```
sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper wl bcm43xx
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko
```
This should remove all the modules that are using ssb.  If your wired card quits working, it is because it has the b44 module.  To bring it back:
```
sudo modprobe b44
sudo ifconfig eth0 up
sudo dhclient eth0
```

---

### Post by slugicide on 2008-10-25
This is after I ran the above modprobe, etc... commands

```
 *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:59:bd:6c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.15.10.104 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0a:c0:9b:6c:4b:f6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by Ayuthia on 2008-10-25
> **slugicide said:**
> This is after I ran the above modprobe, etc... commands

```
 *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:59:bd:6c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.15.10.104 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0a:c0:9b:6c:4b:f6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

You have all the fun devices!  Can you post the results of:
```
lsmod|grep -e b4 -e ssb -e ndis -e wl -e bcm
```
There must be a either a module that was missed or else we need to check dmesg to see where the wl module failed:
```
dmesg
```
You do have the b44 module (which is why some people need the ssb fix) so that means that you do need the ssb module.  However, the ssb module has to be loaded AFTER the wireless driver has been installed (unless it is the b43 module).

---

### Post by slugicide on 2008-10-25
```
b44                    35984  0 
ssb                    40580  1 b44
mii                    13440  1 b44
wl                   1076356  0 
ieee80211_crypt        13572  2 wl,ieee80211_crypt_tkip

```
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fed3400 (usable)
[    0.000000]  BIOS-e820: 000000007fed3400 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7fed3 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 37822000 - 37fef086
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 7FED39CD, 0040 (r1 DELL    M07     27D60C12 ASL        61)
[    0.000000] ACPI: FACP 7FED4800, 0074 (r1 DELL    M07     27D60C12 ASL        61)
[    0.000000] ACPI: DSDT 7FED5400, 4766 (r1 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7FEE3C00, 0040
[    0.000000] ACPI: HPET 7FED4F00, 0038 (r1 DELL    M07            1 ASL        61)
[    0.000000] ACPI: APIC 7FED5000, 0068 (r1 DELL    M07     27D60C12 ASL        47)
[    0.000000] ACPI: MCFG 7FED4FC0, 003E (r16 DELL    M07     27D60C12 ASL        61)
[    0.000000] ACPI: SLIC 7FED509C, 0176 (r1 DELL    M07     27D60C12 ASL        61)
[    0.000000] ACPI: BOOT 7FED4BC0, 0028 (r1 DELL    M07     27D60C12 ASL        61)
[    0.000000] ACPI: SSDT 7FED3A0D, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [0037822000 - 0037fef086]          RAMDISK ==> [0037822000 - 0037fef086]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007fed3
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fed3
[    0.000000] On node 0 totalpages: 523890
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 292021 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519284
[    0.000000] Kernel command line: root=UUID=6af76e80-7227-40ad-a999-b68eb444e1c2 ro splash vga=794 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1994.963 MHz processor.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2062432k/2095948k available (2572k kernel code, 32252k reserved, 1160k data, 424k init, 1178444k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.92 BogoMIPS (lpj=7979852)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017881] ACPI: Core revision 20080609
[    0.019624] ACPI: Checking initramfs for custom DSDT
[    0.353967] ENABLING IO-APIC IRQs
[    0.354163] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.394225] CPU0: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[    0.396024] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3990.04 BogoMIPS (lpj=7980097)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.480708] CPU1: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[    0.480737] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.484030] Measured 3926369736 cycles TSC warp between CPUs, turning off TSC clock.
[    0.484030] Marking TSC unstable due to check_tsc_sync_source failed
[    0.484052] Brought up 2 CPUs
[    0.484057] Total of 2 processors activated (7979.97 BogoMIPS).
[    0.484082] CPU0 attaching sched-domain:
[    0.484085]  domain 0: span 0-1 level MC
[    0.484087]   groups: 0 1
[    0.484093] CPU1 attaching sched-domain:
[    0.484096]  domain 0: span 0-1 level MC
[    0.484098]   groups: 1 0
[    0.484179] net_namespace: 840 bytes
[    0.484179] Booting paravirtualized kernel on bare hardware
[    0.484305] Time: 11:51:05  Date: 10/25/08
[    0.484333] NET: Registered protocol family 16
[    0.484355] EISA bus registered
[    0.484355] ACPI: bus type pci registered
[    0.484355] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.484355] PCI: MCFG area at f0000000 reserved in E820
[    0.484355] PCI: Using MMCONFIG for extended config space
[    0.484355] PCI: Using configuration type 1 for base access
[    0.484800] ACPI: EC: Look up EC in DSDT
[    0.503838] ACPI: Interpreter enabled
[    0.503844] ACPI: (supports S0 S3 S4 S5)
[    0.504047] ACPI: Using IOAPIC for interrupt routing
[    0.532711] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.536077] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.536084] pci 0000:00:01.0: PME# disabled
[    0.536171] PCI: 0000:00:1b.0 reg 10 64bit mmio: [efffc000, efffffff]
[    0.536225] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.536232] pci 0000:00:1b.0: PME# disabled
[    0.536305] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.536312] pci 0000:00:1c.0: PME# disabled
[    0.536388] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.536395] pci 0000:00:1c.3: PME# disabled
[    0.536447] PCI: 0000:00:1d.0 reg 20 io port: [bf80, bf9f]
[    0.536511] PCI: 0000:00:1d.1 reg 20 io port: [bf60, bf7f]
[    0.536575] PCI: 0000:00:1d.2 reg 20 io port: [bf40, bf5f]
[    0.536638] PCI: 0000:00:1d.3 reg 20 io port: [bf20, bf3f]
[    0.536706] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ffa80000, ffa803ff]
[    0.536764] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.536772] pci 0000:00:1d.7: PME# disabled
[    0.536934] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.536942] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.536989] PCI: 0000:00:1f.2 reg 10 io port: [1f0, 1f7]
[    0.536997] PCI: 0000:00:1f.2 reg 14 io port: [3f4, 3f7]
[    0.537005] PCI: 0000:00:1f.2 reg 18 io port: [170, 177]
[    0.537013] PCI: 0000:00:1f.2 reg 1c io port: [374, 377]
[    0.537021] PCI: 0000:00:1f.2 reg 20 io port: [bfa0, bfaf]
[    0.537053] pci 0000:00:1f.2: PME# supported from D3hot
[    0.537059] pci 0000:00:1f.2: PME# disabled
[    0.537120] PCI: 0000:00:1f.3 reg 20 io port: [10c0, 10df]
[    0.537180] PCI: 0000:01:00.0 reg 10 32bit mmio: [d0000000, dfffffff]
[    0.537189] PCI: 0000:01:00.0 reg 14 io port: [ee00, eeff]
[    0.537198] PCI: 0000:01:00.0 reg 18 32bit mmio: [efdf0000, efdfffff]
[    0.537218] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.537236] pci 0000:01:00.0: supports D1
[    0.537238] pci 0000:01:00.0: supports D2
[    0.537289] PCI: bridge 0000:00:01.0 io port: [e000, efff]
[    0.537293] PCI: bridge 0000:00:01.0 32bit mmio: [efd00000, efefffff]
[    0.537298] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    0.537371] PCI: 0000:0b:00.0 reg 10 64bit mmio: [efcfc000, efcfffff]
[    0.537382] PCI: 0000:0b:00.0 reg 18 32bit mmio: [e0000000, e00fffff]
[    0.537449] pci 0000:0b:00.0: supports D1
[    0.537451] pci 0000:0b:00.0: supports D2
[    0.537507] PCI: bridge 0000:00:1c.0 32bit mmio: [efc00000, efcfffff]
[    0.537515] PCI: bridge 0000:00:1c.0 64bit mmio pref: [e0000000, e00fffff]
[    0.537576] PCI: bridge 0000:00:1c.3 io port: [d000, dfff]
[    0.537581] PCI: bridge 0000:00:1c.3 32bit mmio: [efa00000, efbfffff]
[    0.537589] PCI: bridge 0000:00:1c.3 64bit mmio pref: [e0100000, e03fffff]
[    0.537631] PCI: 0000:03:00.0 reg 10 32bit mmio: [ef9fe000, ef9fffff]
[    0.537685] pci 0000:03:00.0: supports D1
[    0.537686] pci 0000:03:00.0: supports D2
[    0.537688] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.537696] pci 0000:03:00.0: PME# disabled
[    0.537734] PCI: 0000:03:01.0 reg 10 32bit mmio: [ef9fd800, ef9fdfff]
[    0.537789] pci 0000:03:01.0: supports D1
[    0.537791] pci 0000:03:01.0: supports D2
[    0.537793] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.537800] pci 0000:03:01.0: PME# disabled
[    0.537838] PCI: 0000:03:01.1 reg 10 32bit mmio: [ef9fd500, ef9fd5ff]
[    0.537894] pci 0000:03:01.1: supports D1
[    0.537895] pci 0000:03:01.1: supports D2
[    0.537897] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.537905] pci 0000:03:01.1: PME# disabled
[    0.537944] PCI: 0000:03:01.2 reg 10 32bit mmio: [ef9fd600, ef9fd6ff]
[    0.538001] pci 0000:03:01.2: supports D1
[    0.538002] pci 0000:03:01.2: supports D2
[    0.538004] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.538011] pci 0000:03:01.2: PME# disabled
[    0.538051] PCI: 0000:03:01.3 reg 10 32bit mmio: [ef9fd700, ef9fd7ff]
[    0.538106] pci 0000:03:01.3: supports D1
[    0.538108] pci 0000:03:01.3: supports D2
[    0.538110] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.538117] pci 0000:03:01.3: PME# disabled
[    0.538184] pci 0000:00:1e.0: transparent bridge
[    0.538194] PCI: bridge 0000:00:1e.0 32bit mmio: [ef900000, ef9fffff]
[    0.538225] bus 00 -> node 0
[    0.538231] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.538674] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.538785] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.538928] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.539068] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.548156] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *4
[    0.548299] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
[    0.548438] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.548577] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    0.548717] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.548861] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.549005] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.549149] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.549241] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.549241] pnp: PnP ACPI init
[    0.549241] ACPI: bus type pnp registered
[    0.585283] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.585283] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.585283] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.585283] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.585283] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.585283] pnp 00:03: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.585283] pnp: PnP ACPI: found 12 devices
[    0.585283] ACPI: ACPI bus type pnp unregistered
[    0.585283] PnPBIOS: Disabled by ACPI PNP
[    0.585283] PCI: Using ACPI for IRQ routing
[    0.592040] NET: Registered protocol family 8
[    0.592045] NET: Registered protocol family 20
[    0.592063] NetLabel: Initializing
[    0.592063] NetLabel:  domain hash size = 128
[    0.592063] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.592075] NetLabel:  unlabeled traffic allowed by default
[    0.592084] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.592092] hpet0: 3 64-bit timers, 14318180 Hz
[    0.593579] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.593584]    actual entries 65620
[    0.593669] AppArmor: AppArmor Filesystem Enabled
[    0.593697] ACPI: RTC can wake from S4
[    0.596045] Switched to high resolution mode on CPU 0
[    0.596779] Switched to high resolution mode on CPU 1
[    0.600027] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.600033] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.600038] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.600043] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.600049] system 00:00: iomem range 0x100000-0x7fed33ff could not be reserved
[    0.600055] system 00:00: iomem range 0x7fed3400-0x7fefffff could not be reserved
[    0.600060] system 00:00: iomem range 0x7ff00000-0x7fffffff could not be reserved
[    0.600066] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
[    0.600072] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.600078] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    0.600084] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
[    0.600089] system 00:00: iomem range 0xffa80000-0xffa83fff could not be reserved
[    0.600095] system 00:00: iomem range 0xf4000000-0xf4003fff could not be reserved
[    0.600101] system 00:00: iomem range 0xf4004000-0xf4004fff could not be reserved
[    0.600107] system 00:00: iomem range 0xf4005000-0xf4005fff could not be reserved
[    0.600112] system 00:00: iomem range 0xf4006000-0xf4006fff could not be reserved
[    0.600118] system 00:00: iomem range 0xf4008000-0xf400bfff could not be reserved
[    0.600124] system 00:00: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.600134] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.600142] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.600148] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.600153] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.600158] system 00:03: ioport range 0x809-0x809 has been reserved
[    0.600169] system 00:08: ioport range 0xc80-0xcff could not be reserved
[    0.600174] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.600179] system 00:08: ioport range 0x920-0x92f has been reserved
[    0.600184] system 00:08: ioport range 0xcb0-0xcbf has been reserved
[    0.600189] system 00:08: ioport range 0x930-0x97f has been reserved
[    0.600198] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.635510] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.635516] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.635523] pci 0000:00:01.0:   MEM window: 0xefd00000-0xefefffff
[    0.635529] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.635537] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.635541] pci 0000:00:1c.0:   IO window: disabled
[    0.635549] pci 0000:00:1c.0:   MEM window: 0xefc00000-0xefcfffff
[    0.635556] pci 0000:00:1c.0:   PREFETCH window: 0x000000e0000000-0x000000e00fffff
[    0.635567] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0c
[    0.635572] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.635581] pci 0000:00:1c.3:   MEM window: 0xefa00000-0xefbfffff
[    0.635588] pci 0000:00:1c.3:   PREFETCH window: 0x000000e0100000-0x000000e03fffff
[    0.635599] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.635603] pci 0000:00:1e.0:   IO window: disabled
[    0.635611] pci 0000:00:1e.0:   MEM window: 0xef900000-0xef9fffff
[    0.635618] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.635635] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.635641] pci 0000:00:01.0: setting latency timer to 64
[    0.635650] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.635657] pci 0000:00:1c.0: setting latency timer to 64
[    0.635667] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.635675] pci 0000:00:1c.3: setting latency timer to 64
[    0.635684] pci 0000:00:1e.0: setting latency timer to 64
[    0.635688] bus: 00 index 0 io port: [0, ffff]
[    0.635691] bus: 00 index 1 mmio: [0, ffffffff]
[    0.635695] bus: 01 index 0 io port: [e000, efff]
[    0.635699] bus: 01 index 1 mmio: [efd00000, efefffff]
[    0.635703] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.635707] bus: 01 index 3 mmio: [0, 0]
[    0.635710] bus: 0b index 0 mmio: [0, 0]
[    0.635713] bus: 0b index 1 mmio: [efc00000, efcfffff]
[    0.635717] bus: 0b index 2 mmio: [e0000000, e00fffff]
[    0.635721] bus: 0b index 3 mmio: [0, 0]
[    0.635724] bus: 0c index 0 io port: [d000, dfff]
[    0.635728] bus: 0c index 1 mmio: [efa00000, efbfffff]
[    0.635731] bus: 0c index 2 mmio: [e0100000, e03fffff]
[    0.635735] bus: 0c index 3 mmio: [0, 0]
[    0.635738] bus: 03 index 0 mmio: [0, 0]
[    0.635742] bus: 03 index 1 mmio: [ef900000, ef9fffff]
[    0.635745] bus: 03 index 2 mmio: [0, 0]
[    0.635749] bus: 03 index 3 io port: [0, ffff]
[    0.635752] bus: 03 index 4 mmio: [0, ffffffff]
[    0.635762] NET: Registered protocol family 2
[    0.648061] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.648290] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.648641] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.648819] TCP: Hash tables configured (established 131072 bind 65536)
[    0.648824] TCP reno registered
[    0.652069] NET: Registered protocol family 1
[    0.652172] checking if image is initramfs... it is
[    1.001013] Clocksource tsc unstable (delta = 1968151198 ns)
[    1.337125] Freeing initrd memory: 7988k freed
[    1.337349] Simple Boot Flag at 0x79 set to 0x1
[    1.338496] audit: initializing netlink socket (disabled)
[    1.338524] type=2000 audit(1224935465.337:1): initialized
[    1.344473] highmem bounce pool size: 64 pages
[    1.344481] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.347390] VFS: Disk quotas dquot_6.5.1
[    1.347495] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.347614] msgmni has been set to 1743
[    1.347751] io scheduler noop registered
[    1.347756] io scheduler anticipatory registered
[    1.347760] io scheduler deadline registered
[    1.347773] io scheduler cfq registered (default)
[    1.347898] pci 0000:01:00.0: Boot video device
[    1.348028] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.348068] pcieport-driver 0000:00:01.0: found MSI capability
[    1.348105] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.348162] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.348264] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.348314] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.348364] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.348422] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.348475] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.348603] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.348652] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.348702] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.348756] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.348810] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.349255] isapnp: Scanning for PnP cards...
[    1.703765] isapnp: No Plug & Play device found
[    1.743141] hpet_resources: 0xfed00000 is busy
[    1.743251] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.745917] brd: module loaded
[    1.745999] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.746151] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.749137] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.749147] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.752142] mice: PS/2 mouse device common for all mice
[    1.752313] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.752346] rtc0: alarms up to one month, y3k, hpet irqs
[    1.752523] EISA: Probing bus 0 at eisa.0
[    1.752585] EISA: Mainboard [O_FFFF detected.
[    1.752644] Cannot allocate resource for EISA slot 1
[    1.752677] EISA: Detected 0 cards.
[    1.752682] cpuidle: using governor ladder
[    1.752686] cpuidle: using governor menu
[    1.753218] TCP cubic registered
[    1.753248] Using IPI No-Shortcut mode
[    1.753450] registered taskstats version 1
[    1.753568]   Magic number: 12:408:884
[    1.753604] tty ptyx8: hash matches
[    1.753611] tty ptyub: hash matches
[    1.753677] rtc_cmos 00:06: setting system clock to 2008-10-25 11:51:06 UTC (1224935466)
[    1.753684] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.753688] EDD information not available.
[    1.753914] Freeing unused kernel memory: 424k freed
[    1.753955] Write protecting the kernel text: 2576k
[    1.753985] Write protecting the kernel read-only data: 936k
[    1.754723] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.814000] vesafb: framebuffer at 0xd0000000, mapped to 0xf8880000, using 5120k, total 16384k
[    1.814011] vesafb: mode is 1280x1024x16, linelength=2560, pages=5
[    1.814015] vesafb: protected mode interface info at c000:aad8
[    1.814019] vesafb: pmi: set display start = c00cab66, set palette = c00cac28
[    1.814024] vesafb: scrolling: redraw
[    1.814027] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    1.814232] Console: switching to colour frame buffer device 160x64
[    1.854561] fb0: VESA VGA frame buffer device
[    1.943762] fuse init (API version 7.9)
[    1.961023] ACPI: SSDT 7FED4134, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.961351] ACPI: SSDT 7FED3EE9, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.961971] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.962048] processor ACPI0007:00: registered as cooling_device0
[    1.962052] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.962398] ACPI: SSDT 7FED4378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    1.962702] ACPI: SSDT 7FED40AF, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    1.963389] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.963460] processor ACPI0007:01: registered as cooling_device1
[    1.963464] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.969111] thermal LNXTHERM:01: registered as thermal_zone0
[    1.972316] ACPI: Thermal Zone [THM] (60 C)
[    2.373515] usbcore: registered new interface driver usbfs
[    2.373540] usbcore: registered new interface driver hub
[    2.405516] usbcore: registered new device driver usb
[    2.405660] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.405672] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[    2.407543] No dock devices found.
[    2.421885] SCSI subsystem initialized
[    2.455134] USB Universal Host Controller Interface driver v3.0
[    2.472950] libata version 3.00 loaded.
[    2.492107] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[    2.492199] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.492209] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.492214] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.492258] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    2.492295] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    2.492450] usb usb1: configuration #1 chosen from 1 choice
[    2.492479] hub 1-0:1.0: USB hub found
[    2.492485] hub 1-0:1.0: 2 ports detected
[    2.596319] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.596331] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.596335] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.596364] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    2.596403] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    2.596493] usb usb2: configuration #1 chosen from 1 choice
[    2.596520] hub 2-0:1.0: USB hub found
[    2.596526] hub 2-0:1.0: 2 ports detected
[    2.804298] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.804309] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.804314] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.804340] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    2.804380] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    2.804470] usb usb3: configuration #1 chosen from 1 choice
[    2.804497] hub 3-0:1.0: USB hub found
[    2.804504] hub 3-0:1.0: 2 ports detected
[    2.908200] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.908207] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.908211] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.908234] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    2.908267] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    2.908350] usb usb4: configuration #1 chosen from 1 choice
[    2.908379] hub 4-0:1.0: USB hub found
[    2.908385] hub 4-0:1.0: 2 ports detected
[    2.916046] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.090517] usb 2-1: configuration #1 chosen from 1 choice
[    3.116297] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.116311] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.116315] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.116340] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.120262] ehci_hcd 0000:00:1d.7: debug port 1
[    3.120269] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.120275] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    3.136051] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.136139] usb usb5: configuration #1 chosen from 1 choice
[    3.136165] hub 5-0:1.0: USB hub found
[    3.136172] hub 5-0:1.0: 8 ports detected
[    3.252067] usb 2-1: USB disconnect, address 2
[    3.347903] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.400652] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.405783] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.464131] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    3.464155] ata_piix 0000:00:1f.2: version 2.12
[    3.464170] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.464175] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.464218] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.464326] scsi0 : ata_piix
[    3.464549] scsi1 : ata_piix
[    3.465521] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    3.465524] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    3.465556] b44.c:v2.0
[    3.484435] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:59:bd:6c
[    3.604178] usbcore: registered new interface driver hiddev
[    3.604199] usbcore: registered new interface driver usbhid
[    3.604202] usbhid: v2.6:USB HID core driver
[    3.660746] ata1.00: ATA-7: WDC WD1200BEVS-75LAT0, 02.06M02, max UDMA/133
[    3.660750] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/1)
[    3.676587] ata1.00: configured for UDMA/133
[    3.840530] ata2.00: ATAPI: SONY DVD+/-RW DW-Q58A, UDS2, max UDMA/33
[    3.856473] ata2.00: configured for UDMA/33
[    3.856607] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-7 02.0 PQ: 0 ANSI: 5
[    3.857551] scsi 1:0:0:0: CD-ROM            SONY     DVD+-RW DW-Q58A  UDS2 PQ: 0 ANSI: 5
[    3.864048] usb 2-1: new low speed USB device using uhci_hcd and address 3
[    3.870454] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    3.870493] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    3.885620] Driver 'sr' needs updating - please use bus_type methods
[    3.888929] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.888932] Uniform CD-ROM driver Revision: 3.20
[    3.889021] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.890254] Driver 'sd' needs updating - please use bus_type methods
[    3.890336] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    3.890358] sd 0:0:0:0: [sda] Write Protect is off
[    3.890361] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.890398] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.890464] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    3.890484] sd 0:0:0:0: [sda] Write Protect is off
[    3.890487] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.890524] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.890528]  sda: sda1 sda2 < sda5 sda6 >
[    3.972407] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.038760] usb 2-1: configuration #1 chosen from 1 choice
[    4.059777] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input2
[    4.060323] input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.1-1
[    4.300055] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    4.442307] PM: Starting manual resume from disk
[    4.442312] PM: Resume from partition 8:6
[    4.442313] PM: Checking hibernation image.
[    4.442537] PM: Resume from disk failed.
[    4.486448] usb 4-2: configuration #1 chosen from 1 choice
[    4.488355] hub 4-2:1.0: USB hub found
[    4.490320] hub 4-2:1.0: 3 ports detected
[    4.496335] kjournald starting.  Commit interval 5 seconds
[    4.496352] EXT3-fs: mounted filesystem with ordered data mode.
[    4.676159] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[464fc0002b1f4161]
[    4.777331] usb 4-2.1: new full speed USB device using uhci_hcd and address 3
[    4.905386] usb 4-2.1: configuration #1 chosen from 1 choice
[    4.981325] usb 4-2.2: new full speed USB device using uhci_hcd and address 4
[    5.111389] usb 4-2.2: configuration #1 chosen from 1 choice
[    5.118593] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.3/usb4/4-2/4-2.2/4-2.2:1.0/input/input3
[    5.118661] input,hidraw1: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.3-2.2
[    5.193330] usb 4-2.3: new full speed USB device using uhci_hcd and address 5
[    5.323457] usb 4-2.3: configuration #1 chosen from 1 choice
[    5.330624] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.3/usb4/4-2/4-2.3/4-2.3:1.0/input/input4
[    5.330710] input,hidraw2: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.3-2.3
[   16.453725] udevd version 124 started
[   16.864799] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.874759] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.999204] Linux agpgart interface v0.103
[   17.162643] intel_rng: FWH not detected
[   17.184452] ACPI: AC Adapter [AC] (on-line)
[   17.285669] ACPI: Battery Slot [BAT0] (battery present)
[   17.356095] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   17.356548] ACPI: Lid Switch [LID]
[   17.356624] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[   17.380036] ACPI: Power Button (CM) [PBTN]
[   17.380126] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input7
[   17.412023] ACPI: Sleep Button (CM) [SBTN]
[   17.412480] ACPI: WMI: Mapper loaded
[   17.461660] acpi device:25: registered as cooling_device2
[   17.462215] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/device:22/input/input8
[   17.484036] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   17.492593] acpi device:2a: registered as cooling_device3
[   17.493021] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:27/input/input9
[   17.512043] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   17.512230] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2c/input/input10
[   17.519547] iTCO_vendor_support: vendor-support=0
[   17.544024] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   17.623729] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   17.624140] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   17.624267] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.859453] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   17.882520] [fglrx] Maximum main memory to use for locked dma buffers: 1896 MBytes.
[   17.883119] [fglrx]   vendor: 1002 device: 7145 count: 1
[   17.883985] [fglrx] ioport: bar 1, base 0xee00, size: 0x100
[   17.884017] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.884025] pci 0000:01:00.0: setting latency timer to 64
[   17.886142] [fglrx] PAT is enabled successfully!
[   17.886191] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   18.079303] sdhci: Secure Digital Host Controller Interface driver
[   18.079308] sdhci: Copyright(c) Pierre Ossman
[   18.147212] Bluetooth: Core ver 2.13
[   18.148846] NET: Registered protocol family 31
[   18.148849] Bluetooth: HCI device and connection manager initialized
[   18.148853] Bluetooth: HCI socket layer initialized
[   18.255992] usbcore: registered new interface driver lmpcm_usb
[   18.256100] lmpcm_usb: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   18.307273] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   18.309579] usbcore: registered new interface driver btusb
[   18.319361] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[   18.319382] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   18.322442] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   18.332243] input: PC Speaker as /devices/platform/pcspkr/input/input11
[   18.838712] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[   18.876526] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
[   18.923843] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   19.064232] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   19.064258] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.395821] b43-phy0: Broadcom 4321 WLAN found
[   19.436029] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 5, Type 4, Revision 1)
[   19.436059] b43: probe of ssb0:0 failed with error -95
[   19.436094] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   19.672397] input: btnx keyboard as /devices/virtual/input/input13
[   19.684238] input: btnx mouse as /devices/virtual/input/input14
[   20.341456] lp: driver loaded but no devices found
[   20.398476] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   20.446760] usbcore: registered new interface driver ndiswrapper
[   20.593119] Adding 4345540k swap on /dev/sda6.  Priority:-1 extents:1 across:4345540k
[   21.173182] EXT3 FS on sda5, internal journal
[   22.696227] type=1505 audit(1224960687.544:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4471
[   22.868097] type=1505 audit(1224960687.716:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4476
[   22.868277] type=1505 audit(1224960687.716:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4476
[   23.105028] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.192418] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   23.192558] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   23.192560] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   23.192562] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   23.332103] NET: Registered protocol family 10
[   23.332678] lo: Disabled Privacy Extensions
[   23.357414] ip6_tables: (C) 2000-2006 Netfilter Core Team

[   26.140543] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   26.246084] apm: BIOS not found.
[   27.014866] ppdev: user-space parallel port driver
[   34.434188] Bluetooth: L2CAP ver 2.11
[   34.434199] Bluetooth: L2CAP socket layer initialized
[   34.506682] Bluetooth: RFCOMM socket layer initialized
[   34.506709] Bluetooth: RFCOMM TTY layer initialized
[   34.506716] Bluetooth: RFCOMM ver 1.10
[   34.517416] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.517427] Bluetooth: BNEP filters: protocol multicast
[   34.625817] Bridge firewalling registered
[   34.626685] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   34.654997] Bluetooth: SCO (Voice Link) ver 0.6
[   34.655004] Bluetooth: SCO socket layer initialized
[   37.585646] input: btnx keyboard as /devices/virtual/input/input15
[   37.600785] input: btnx mouse as /devices/virtual/input/input16
[   38.947850] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   39.789631] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   39.789645] [fglrx] Reserved FB block: Unshared offset:7fb7000, size:44000 
[   39.789651] [fglrx] Reserved FB block: Unshared offset:7ffb000, size:5000 
[   41.816193] b44: eth0: Link is up at 100 Mbps, full duplex.
[   41.816200] b44: eth0: Flow control is off for TX and off for RX.
[   41.816783] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   41.908633] NET: Registered protocol family 17
[   52.544053] eth0: no IPv6 routers present
[   54.350302] ecryptfs_parse_options: eCryptfs: unrecognized option 'rw'
[   54.350320] ecryptfs_parse_options: eCryptfs: unrecognized option 'user=rodney'
[   54.600129] padlock: VIA PadLock not detected.
[   87.700126] CPU0 attaching NULL sched-domain.
[   87.700141] CPU1 attaching NULL sched-domain.
[   87.702094] CPU0 attaching sched-domain:
[   87.702103]  domain 0: span 0-1 level MC
[   87.702108]   groups: 0 1
[   87.702119] CPU1 attaching sched-domain:
[   87.702123]  domain 0: span 0-1 level MC
[   87.702130]   groups: 1 0
[  173.563562] type=1503 audit(1224960838.408:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6914/net/" pid=6914 profile="/usr/sbin/cupsd"
[  174.833468] type=1503 audit(1224960839.680:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6921/net/" pid=6921 profile="/usr/sbin/cupsd"
[  174.835866] type=1503 audit(1224960839.680:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6921 profile="/usr/sbin/cupsd"
[  174.837874] type=1503 audit(1224960839.684:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6921 profile="/usr/sbin/cupsd"
[  174.839878] type=1503 audit(1224960839.684:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6921 profile="/usr/sbin/cupsd"
[  174.841815] type=1503 audit(1224960839.688:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6921 profile="/usr/sbin/cupsd"
[  174.843741] type=1503 audit(1224960839.688:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6921 profile="/usr/sbin/cupsd"
[  174.845732] type=1503 audit(1224960839.692:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6921 profile="/usr/sbin/cupsd"
[  174.847700] type=1503 audit(1224960839.692:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6921 profile="/usr/sbin/cupsd"
[  174.849739] type=1503 audit(1224960839.696:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6921 profile="/usr/sbin/cupsd"
[  174.897401] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1f:f3:c7:9b:45:08:00 SRC=10.15.10.109 DST=10.15.10.104 LEN=74 TOS=0x00 PREC=0x00 TTL=64 ID=18862 PROTO=UDP SPT=161 DPT=42682 LEN=54 
[  174.897447] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:0d:80:77:08:00 SRC=10.15.5.22 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=21989 PROTO=UDP SPT=161 DPT=42682 LEN=71 
[  174.897472] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:0c:eb:0c:08:00 SRC=10.15.5.26 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=55892 PROTO=UDP SPT=161 DPT=42682 LEN=71 
[  174.897498] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:0c:2f:5e:08:00 SRC=10.15.5.27 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=3706 PROTO=UDP SPT=161 DPT=42682 LEN=71 
[  174.897526] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:0d:2f:67:08:00 SRC=10.15.5.28 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=4760 PROTO=UDP SPT=161 DPT=42682 LEN=71 
[  174.897551] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:2b:f4:fc:08:00 SRC=10.15.5.24 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=56712 PROTO=UDP SPT=161 DPT=42682 LEN=71 
[  174.897575] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:0d:80:39:08:00 SRC=10.15.5.25 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=36909 PROTO=UDP SPT=161 DPT=42682 LEN=71 
[  174.901691] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:14:38:db:c0:61:08:00 SRC=10.15.5.33 DST=10.15.10.104 LEN=83 TOS=0x00 PREC=0x00 TTL=64 ID=2062 PROTO=UDP SPT=161 DPT=42682 LEN=63 
[  174.901894] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:1c:97:4f:08:00 SRC=10.15.5.29 DST=10.15.10.104 LEN=83 TOS=0x00 PREC=0x00 TTL=64 ID=16224 PROTO=UDP SPT=161 DPT=42682 LEN=63 
[  174.902355] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1b:78:13:2f:9c:08:00 SRC=10.15.5.34 DST=10.15.10.104 LEN=83 TOS=0x00 PREC=0x00 TTL=64 ID=24942 PROTO=UDP SPT=161 DPT=42682 LEN=63 
[ 1444.193587] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 1649.762918] __ratelimit: 3 callbacks suppressed
[ 1649.762930] type=1503 audit(1224962314.609:16): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/9116/net/" pid=9116 profile="/usr/sbin/cupsd"
[ 1650.782919] type=1503 audit(1224962315.628:17): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/9128/net/" pid=9128 profile="/usr/sbin/cupsd"
[ 1650.786970] type=1503 audit(1224962315.632:18): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=9128 profile="/usr/sbin/cupsd"
[ 1650.790344] type=1503 audit(1224962315.636:19): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=9128 profile="/usr/sbin/cupsd"
[ 1650.793849] type=1503 audit(1224962315.640:20): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=9128 profile="/usr/sbin/cupsd"
[ 1650.797230] type=1503 audit(1224962315.644:21): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=9128 profile="/usr/sbin/cupsd"
[ 1650.800551] type=1503 audit(1224962315.648:22): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=9128 profile="/usr/sbin/cupsd"
[ 1650.804027] type=1503 audit(1224962315.652:23): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=9128 profile="/usr/sbin/cupsd"
[ 1650.807687] type=1503 audit(1224962315.652:24): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=9128 profile="/usr/sbin/cupsd"
[ 1650.811068] type=1503 audit(1224962315.656:25): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=9128 profile="/usr/sbin/cupsd"
[ 1650.821545] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1f:f3:c7:9b:45:08:00 SRC=10.15.10.109 DST=10.15.10.104 LEN=74 TOS=0x00 PREC=0x00 TTL=64 ID=18871 PROTO=UDP SPT=161 DPT=59724 LEN=54 
[ 1650.822039] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:0c:2f:5e:08:00 SRC=10.15.5.27 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=9540 PROTO=UDP SPT=161 DPT=59724 LEN=71 
[ 1650.822087] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:0d:80:39:08:00 SRC=10.15.5.25 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=42757 PROTO=UDP SPT=161 DPT=59724 LEN=71 
[ 1650.822144] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:0d:2f:67:08:00 SRC=10.15.5.28 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=10608 PROTO=UDP SPT=161 DPT=59724 LEN=71 
[ 1650.822208] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:0d:80:77:08:00 SRC=10.15.5.22 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=27837 PROTO=UDP SPT=161 DPT=59724 LEN=71 
[ 1650.822377] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:0c:eb:0c:08:00 SRC=10.15.5.26 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=61742 PROTO=UDP SPT=161 DPT=59724 LEN=71 
[ 1650.826473] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:14:38:db:c0:61:08:00 SRC=10.15.5.33 DST=10.15.10.104 LEN=83 TOS=0x00 PREC=0x00 TTL=64 ID=2924 PROTO=UDP SPT=161 DPT=59724 LEN=63 
[ 1650.826878] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:1c:97:4f:08:00 SRC=10.15.5.29 DST=10.15.10.104 LEN=83 TOS=0x00 PREC=0x00 TTL=64 ID=16230 PROTO=UDP SPT=161 DPT=59724 LEN=63 
[ 1650.827844] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1b:78:13:2f:9c:08:00 SRC=10.15.5.34 DST=10.15.10.104 LEN=83 TOS=0x00 PREC=0x00 TTL=64 ID=24948 PROTO=UDP SPT=161 DPT=59724 LEN=63 
[ 1650.832924] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:01:e6:a4:78:b4:08:00 SRC=10.15.5.31 DST=10.15.10.104 LEN=83 TOS=0x00 PREC=0x00 TTL=64 ID=172 PROTO=UDP SPT=161 DPT=59724 LEN=63 
[ 1929.065537] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:2b:f4:fc:08:00 SRC=10.15.5.24 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=56898 PROTO=UDP SPT=161 DPT=59724 LEN=71 
[ 2245.486456] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:04:27:b7:49:82:08:00 SRC=209.124.184.136 DST=10.15.10.104 LEN=1420 TOS=0x00 PREC=0x00 TTL=56 ID=35347 DF PROTO=TCP SPT=80 DPT=51682 WINDOW=4190 RES=0x00 ACK URGP=0 
[ 2269.094179] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:04:27:b7:49:82:08:00 SRC=209.124.184.136 DST=10.15.10.104 LEN=1420 TOS=0x00 PREC=0x00 TTL=56 ID=35348 DF PROTO=TCP SPT=80 DPT=51682 WINDOW=4190 RES=0x00 ACK URGP=0 
[ 2318.960235] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:04:27:b7:49:82:08:00 SRC=209.124.184.136 DST=10.15.10.104 LEN=1420 TOS=0x00 PREC=0x00 TTL=56 ID=35349 DF PROTO=TCP SPT=80 DPT=51682 WINDOW=4190 RES=0x00 ACK URGP=0 
[ 2410.732698] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:04:27:b7:49:82:08:00 SRC=209.124.184.136 DST=10.15.10.104 LEN=1420 TOS=0x00 PREC=0x00 TTL=56 ID=35350 DF PROTO=TCP SPT=80 DPT=51682 WINDOW=4190 RES=0x00 ACK URGP=0 
[ 2568.043771] usbcore: deregistering interface driver ndiswrapper
[ 2620.040125] usb 2-1: USB disconnect, address 3
[ 2620.296061] usb 2-1: new low speed USB device using uhci_hcd and address 4
[ 2620.470600] usb 2-1: configuration #1 chosen from 1 choice
[ 2620.521126] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input17
[ 2620.532792] input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.1-1
[ 2621.157969] input: btnx keyboard as /devices/virtual/input/input18
[ 2621.181657] input: btnx keyboard as /devices/virtual/input/input19
[ 2621.189273] input: btnx mouse as /devices/virtual/input/input20
[ 2621.305227] input: btnx mouse as /devices/virtual/input/input21
[ 2627.006553] ieee80211_crypt: registered algorithm 'NULL'
[ 2627.008427] ieee80211_crypt: registered algorithm 'TKIP'
[ 2643.000115] b44: eth0: Link is down.
[ 2745.776133] usb 4-2: USB disconnect, address 2
[ 2745.776145] usb 4-2.1: USB disconnect, address 3
[ 2745.776256] btusb_intr_complete: hci0 urb f668b980 failed to resubmit (19)
[ 2745.780060] btusb_send_frame: hci0 urb eccf6280 submission failed
[ 2746.031048] usb 4-2.2: USB disconnect, address 4
[ 2746.070049] usb 4-2.3: USB disconnect, address 5
[ 2748.324088] usb 4-2: new full speed USB device using uhci_hcd and address 6
[ 2748.499075] usb 4-2: configuration #1 chosen from 1 choice
[ 2748.500666] hub 4-2:1.0: USB hub found
[ 2748.502375] hub 4-2:1.0: 3 ports detected
[ 2748.793882] usb 4-2.1: new full speed USB device using uhci_hcd and address 7
[ 2748.924599] usb 4-2.1: configuration #1 chosen from 1 choice
[ 2749.004361] usb 4-2.2: new full speed USB device using uhci_hcd and address 8
[ 2749.150533] usb 4-2.2: configuration #1 chosen from 1 choice
[ 2749.169522] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.3/usb4/4-2/4-2.2/4-2.2:1.0/input/input22
[ 2749.217246] input,hidraw1: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.3-2.2
[ 2749.296433] usb 4-2.3: new full speed USB device using uhci_hcd and address 9
[ 2749.436848] usb 4-2.3: configuration #1 chosen from 1 choice
[ 2749.446505] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.3/usb4/4-2/4-2.3/4-2.3:1.0/input/input23
[ 2749.500695] input,hidraw2: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.3-2.3
[ 2757.000229] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 2757.000242] b44: eth0: Flow control is off for TX and off for RX.
[ 3303.857626] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:04:27:b7:49:82:08:00 SRC=66.114.48.50 DST=10.15.10.104 LEN=1420 TOS=0x00 PREC=0x00 TTL=52 ID=11265 DF PROTO=TCP SPT=80 DPT=37510 WINDOW=63 RES=0x00 ACK URGP=0 
[ 3328.092602] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:04:27:b7:49:82:08:00 SRC=66.114.48.50 DST=10.15.10.104 LEN=1420 TOS=0x00 PREC=0x00 TTL=52 ID=11266 DF PROTO=TCP SPT=80 DPT=37510 WINDOW=63 RES=0x00 ACK URGP=0 
[ 3376.562073] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:04:27:b7:49:82:08:00 SRC=66.114.48.50 DST=10.15.10.104 LEN=1420 TOS=0x00 PREC=0x00 TTL=52 ID=11267 DF PROTO=TCP SPT=80 DPT=37510 WINDOW=63 RES=0x00 ACK URGP=0 
[ 3474.952901] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:04:27:b7:49:82:08:00 SRC=66.114.48.50 DST=10.15.10.104 LEN=1420 TOS=0x00 PREC=0x00 TTL=52 ID=11268 DF PROTO=TCP SPT=80 DPT=37510 WINDOW=63 RES=0x00 ACK URGP=0 
[ 3680.348241] __ratelimit: 3 callbacks suppressed
[ 3680.348248] type=1503 audit(1224964345.196:27): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/12921/net/" pid=12921 profile="/usr/sbin/cupsd"
[ 3681.615324] type=1503 audit(1224964346.461:28): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/12925/net/" pid=12925 profile="/usr/sbin/cupsd"
[ 3681.615375] type=1503 audit(1224964346.461:29): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=12925 profile="/usr/sbin/cupsd"
[ 3681.615388] type=1503 audit(1224964346.461:30): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=12925 profile="/usr/sbin/cupsd"
[ 3681.615400] type=1503 audit(1224964346.461:31): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=12925 profile="/usr/sbin/cupsd"
[ 3681.615413] type=1503 audit(1224964346.461:32): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=12925 profile="/usr/sbin/cupsd"
[ 3681.615425] type=1503 audit(1224964346.461:33): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=12925 profile="/usr/sbin/cupsd"
[ 3681.615436] type=1503 audit(1224964346.461:34): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=12925 profile="/usr/sbin/cupsd"
[ 3681.615451] type=1503 audit(1224964346.461:35): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=12925 profile="/usr/sbin/cupsd"
[ 3681.615462] type=1503 audit(1224964346.461:36): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=12925 profile="/usr/sbin/cupsd"
[ 3681.623116] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1f:f3:c7:9b:45:08:00 SRC=10.15.10.109 DST=10.15.10.104 LEN=74 TOS=0x00 PREC=0x00 TTL=64 ID=18889 PROTO=UDP SPT=161 DPT=45091 LEN=54 
[ 3681.623558] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:0c:2f:5e:08:00 SRC=10.15.5.27 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=17567 PROTO=UDP SPT=161 DPT=45091 LEN=71 
[ 3681.623765] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:0d:80:39:08:00 SRC=10.15.5.25 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=50807 PROTO=UDP SPT=161 DPT=45091 LEN=71 
[ 3681.623821] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:0d:80:77:08:00 SRC=10.15.5.22 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=35889 PROTO=UDP SPT=161 DPT=45091 LEN=71 
[ 3681.623865] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:0c:eb:0c:08:00 SRC=10.15.5.26 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=4256 PROTO=UDP SPT=161 DPT=45091 LEN=71 
[ 3681.623908] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:0d:2f:67:08:00 SRC=10.15.5.28 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=18662 PROTO=UDP SPT=161 DPT=45091 LEN=71 
[ 3681.627960] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:14:38:db:c0:61:08:00 SRC=10.15.5.33 DST=10.15.10.104 LEN=83 TOS=0x00 PREC=0x00 TTL=64 ID=9472 PROTO=UDP SPT=161 DPT=45091 LEN=63 
[ 3681.628438] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:1c:97:4f:08:00 SRC=10.15.5.29 DST=10.15.10.104 LEN=83 TOS=0x00 PREC=0x00 TTL=64 ID=16238 PROTO=UDP SPT=161 DPT=45091 LEN=63 
[ 3681.629343] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1b:78:13:2f:9c:08:00 SRC=10.15.5.34 DST=10.15.10.104 LEN=83 TOS=0x00 PREC=0x00 TTL=64 ID=24958 PROTO=UDP SPT=161 DPT=45091 LEN=63 
[ 3681.634098] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:01:e6:a4:78:b4:08:00 SRC=10.15.5.31 DST=10.15.10.104 LEN=83 TOS=0x00 PREC=0x00 TTL=64 ID=206 PROTO=UDP SPT=161 DPT=45091 LEN=63 
[ 4129.272790] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:19:b9:59:bd:6c:00:1a:4b:2b:f4:fc:08:00 SRC=10.15.5.24 DST=10.15.10.104 LEN=91 TOS=0x00 PREC=0x00 TTL=64 ID=57229 PROTO=UDP SPT=161 DPT=45091 LEN=71 
[ 4453.740431] b44: eth0: powering down PHY
[ 4454.020166] b44 0000:03:00.0: PCI INT A disabled
[ 4454.066071] b43-pci-bridge 0000:0b:00.0: PCI INT A disabled
[ 4490.116474] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4490.116501] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[ 4490.184194] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[ 4490.244050] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 4490.304185] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[ 4490.304245] b44.c:v2.0
[ 4490.325025] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:59:bd:6c
[ 4494.371201] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4498.000233] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 4498.000244] b44: eth0: Flow control is off for TX and off for RX.
[ 4498.000701] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4508.684040] eth0: no IPv6 routers present
[ 4576.001150] b44: eth0: Link is down.
[ 4593.000223] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 4593.000235] b44: eth0: Flow control is off for TX and off for RX.
```

---

### Post by Ayuthia on 2008-10-25
Ok, I am at a loss.  It looks like the wl module loaded, but is not functioning.  There is nothing that explains why it is not working.  The only thing that I can think that might be causing the problem is the bluetooth device.  I could be completely wrong about this though.  I only say this because it is the second time that I have seen this.  The funny part is that today was the first time that I have ever seen it.

It looks like you might have to go back to ndiswrapper.  Sorry.  I do know that this card does work because people have reported it to work in the sticky.  I am just not for sure why yours is not being activated.  You might try turning off the bluetooth to see if it makes a difference.

---

### Post by slugicide on 2008-10-25
could you point me to a how-to for installing the ndiswrapper.  I don't remember how I did it before?  And thanks for all your help.  I wish it could've turned out better.

---

### Post by Ayuthia on 2008-10-25
> **slugicide said:**
> could you point me to a how-to for installing the ndiswrapper.  I don't remember how I did it before?  And thanks for all your help.  I wish it could've turned out better.

Here is a pretty good one:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Hope it helps.

---

### Post by slugicide on 2008-10-25
Well, I'm back to exactly where I was before. I can have wireless but no fglrx with 2.6.24, or the other way around with 2.6.27.  Thanks again.

---

### Post by Ayuthia on 2008-10-25
> **slugicide said:**
> Well, I'm back to exactly where I was before. I can have wireless but no fglrx with 2.6.24, or the other way around with 2.6.27.  Thanks again.

Out of curiosity, what is happening in 2.6.27 that you cannot have ndiswrapper?

---

### Post by slugicide on 2008-10-25
I don't know.  It just never worked from the instant I upgraded.  If there is some output you want to look at I can log into it and get that.

---

### Post by Ayuthia on 2008-10-25
> **slugicide said:**
> I don't know.  It just never worked from the instant I upgraded.  If there is some output you want to look at I can log into it and get that.

Can you provide the following:
```
ndiswrapper -v
ndiswrapper -l
sudo updatedb
locate ndiswrapper.ko
dmesg|grep ndiswrapper
```
Also are you compiling or using the repositories?  Thanks!

---

### Post by slugicide on 2008-10-25
I generally use the repositories.

```
rodney@rodney-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.53
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 
rodney@rodney-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: ssb)
rodney@rodney-laptop:~$ sudo updatedb
[sudo] password for rodney: 
rodney@rodney-laptop:~$ locate ndiswrapper.ko
/home/rodney/ndiswrapper-1.53/driver/.ndiswrapper.ko.cmd
/home/rodney/ndiswrapper-1.53/driver/ndiswrapper.ko
/lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko
/lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.27-4-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.27-5-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.27-6-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
rodney@rodney-laptop:~$ dmesg|grep ndiswrapper
[   21.721175] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   21.780301] usbcore: registered new interface driver ndiswrapper
rodney@rodney-laptop:~$ 

```

---

### Post by Ayuthia on 2008-10-25
> **slugicide said:**
> I generally use the repositories.

```
rodney@rodney-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.53
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 
rodney@rodney-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: ssb)
rodney@rodney-laptop:~$ sudo updatedb
[sudo] password for rodney: 
rodney@rodney-laptop:~$ locate ndiswrapper.ko
/home/rodney/ndiswrapper-1.53/driver/.ndiswrapper.ko.cmd
/home/rodney/ndiswrapper-1.53/driver/ndiswrapper.ko
/lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko
/lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.27-4-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.27-5-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.27-6-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
rodney@rodney-laptop:~$ dmesg|grep ndiswrapper
[   21.721175] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   21.780301] usbcore: registered new interface driver ndiswrapper
rodney@rodney-laptop:~$ 

```

Does it work if you do the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
sudo iwlist scan
```
The only thing that I can think that would cause the problem is the introduction of the wl driver.

---

### Post by slugicide on 2008-10-25
W00t!  I'm posting via wireless from the 26.27 kernel.  Wireless kicked in after the networking restart command.```
rodney@rodney-laptop:~$ sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
[sudo] password for rodney: 
FATAL: Module bcm43xx not found.
rodney@rodney-laptop:~$ sudo modprobe ndiswrapper
rodney@rodney-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                        [ OK ] 
rodney@rodney-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:00:2E:5E:AA
                    ESSID:"Motorola"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

rodney@rodney-laptop:~$ uname -r
2.6.27-7-generic
rodney@rodney-laptop:~$ apt-get moo
         (__) 
         (oo) 
   /------\/ 
  / |    ||   
 *  /\---/\ 
    ~~   ~~   
...."Have you mooed today?"...
rodney@rodney-laptop:~$ 

```

**Thank you!**

---

### Post by Ayuthia on 2008-10-25
> **slugicide said:**
> W00t!  I'm posting via wireless from the 26.27 kernel.  Wireless kicked in after the networking restart command.```
rodney@rodney-laptop:~$ sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
[sudo] password for rodney: 
FATAL: Module bcm43xx not found.
rodney@rodney-laptop:~$ sudo modprobe ndiswrapper
rodney@rodney-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                        [ OK ] 
rodney@rodney-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:00:2E:5E:AA
                    ESSID:"Motorola"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

rodney@rodney-laptop:~$ uname -r
2.6.27-7-generic
rodney@rodney-laptop:~$ apt-get moo
         (__) 
         (oo) 
   /------\/ 
  / |    ||   
 *  /\---/\ 
    ~~   ~~   
...."Have you mooed today?"...
rodney@rodney-laptop:~$ 

```

**Thank you!**

Just make sure that you blacklist the wl module:
```
echo blacklist wl|sudo tee -a /etc/modprobe.d/blacklist
```

Glad to see it finally working!

---

### Post by slugicide on 2008-10-27
Sorry, one last thing: how do I make it so I don't have to enter in those commands each time I start Ubuntu?

---

### Post by Th3S\/\/@m! on 2008-10-27
When I try to sudo make the wl.ko I receive the following:

user@aries:~/wdriver$ sudo make -C /lib/modules/2.6.24-
2.6.24-16-386/     2.6.24-19-generic/ 2.6.24-21-generic/ 
user@aries:~/wdriver$ sudo make -C /lib/modules/2.6.24-16-386/build M='pwd' clean
make: *** /lib/modules/2.6.24-16-386/build: No such file or directory.  Stop.
user@aries:~/wdriver$ 




> **mike_l said:**
> After searching for ways to get wireless working on my HP dv9000, I came across [this thread.]("http://ubuntuforums.org/showthread.php?t=850913") Apparently, Broadcom offers linux drivers for it's 802.11a/b/g/n cards (chipsets BCM4311, BCM4312, BCM4321, and BCM4322, in both 32 and 64 bit).

Figuring that there are other people out there with the same problem: here's the steps I took to install the native drivers:

[LIST=1]
[*]**Download the appropriate driver**
I downloaded the 64 bit version of the driver from [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")
It's important that you get the correct version, as the 32 and 64 bit versions are not compatible. 

[*]**Make the .ko file**
First, make a temporary directory 
```
mkdir wdriver 

```
... and place the downloaded package into it (hybrid-portsrc-_64_5_10_27_6.tar.gz, or hybrid-portsrc-x86_32_5_10_27_6.tar.gz for the 32 bit version)
Then 'cd' into the temporary directory and un-tar the file. 
```
cd wdriver
tar -xzf hybrid-portsrc-x86_64_5_10_27_6.tar.gz 

```
Now, we want to make the wl.ko file, so we enter: 
(<2.6.xx.xx> is your kernel version: mine was "2.6.24-19-generic". Use tab-completion to find yours.)
```
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`

```
You should now have a file "wl.ko" located in the temporary directory you created (wdriver). 
[*]**Make sure that no other wireless drivers are installed**
Enter: (Don't worry if there are any errors returned)
```
sudo rmmod bcm43xx
sudo rmmod b43
sudo rmmod b43legacy

```
I also uninstalled ndiswrapper, just to be sure:
```
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-common 

```

[*]**Test the new wireless driver**
Now, lets test out our new wireless driver. Enter:
```
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko 

``` 

If it worked, and you can see/connect to wireless networks, you'll want to:
[*]**Make your changes permanent.**
First, you may want to blacklist the old b43/b43legacy/bcm43xx drivers. Enter:
```
sudo gedit /etc/modprobe.d/blacklist
```
and add the following to the end of the file:
```
blacklist b43
blacklist b43legacy
blacklist bcm43xx
```

Now, let's move the wireless driver somewhere more permenant:
```
sudo mkdir /lib/modules/<2.6.xx.xx>/wlan
sudo mv wl.ko /lib/modules/<2.6.xx.xx>/wlan
```
Now, lets make it so that the driver and wireless encryption module are loaded on startup. Enter:
```

sudo gedit /etc/modules

```
and add
```
ieee80211_crypt_tkip
```
to the bottom.

Now run:
```
sudo gedit /etc/rc.local
```
and add
```
sudo insmod /lib/modules/<2.6.xx.xx>/wlan/wl.ko

```
at the end of the file, but before the line "exit 0"

That's it. If I've made any errors, please let me know. Thanks.

[/LIST]

---

### Post by Ayuthia on 2008-10-27
> **Th3S\/\/@m! said:**
> When I try to sudo make the wl.ko I receive the following:

user@aries:~/wdriver$ sudo make -C /lib/modules/2.6.24-
2.6.24-16-386/     2.6.24-19-generic/ 2.6.24-21-generic/ 
user@aries:~/wdriver$ sudo make -C /lib/modules/2.6.24-16-386/build M='pwd' clean
make: *** /lib/modules/2.6.24-16-386/build: No such file or directory.  Stop.
user@aries:~/wdriver$
Can you post the results of:
```
uname -r
ls -l /lib/modules/`uname -r`/build
```
The ` is a backquote and not a single quote '.  If you are in the terminal, type: echo `uname -r`, it should return your kernel version.  If it returns uname -r, then you used the single quote.

My guess is that the kernel version that you have typed in is incorrect.

---

### Post by Th3S\/\/@m! on 2008-10-27
> **Ayuthia said:**
> Can you post the results of:
```
uname -r
ls -l /lib/modules/`uname -r`/build
```
The ` is a backquote and not a single quote '.  If you are in the terminal, type: echo `uname -r`, it should return your kernel version.  If it returns uname -r, then you used the single quote.

My guess is that the kernel version that you have typed in is incorrect.

--------------------------------------------------------------------------
user@aries:~/Desktop$ ls -l /lib/modules/2.6.24-21-generic/build
lrwxrwxrwx 1 root root 40 2008-10-15 13:38 /lib/modules/2.6.24-21-generic/build -> /usr/src/linux-headers-2.6.24-21-generic
user@aries:~/Desktop$ echo `uname -r`
2.6.24-21-generic



Yeah I used ' instead of `, everything seemed to work, but now when I do iwconfig or ifconfig it's not looking good... Anymore ideas?

user@aries:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by Ayuthia on 2008-10-27
> **Th3S\/\/@m! said:**
> --------------------------------------------------------------------------
user@aries:~/Desktop$ ls -l /lib/modules/2.6.24-21-generic/build
lrwxrwxrwx 1 root root 40 2008-10-15 13:38 /lib/modules/2.6.24-21-generic/build -> /usr/src/linux-headers-2.6.24-21-generic
user@aries:~/Desktop$ echo `uname -r`
2.6.24-21-generic



Yeah I used ' instead of `, everything seemed to work, but now when I do iwconfig or ifconfig it's not looking good... Anymore ideas?

user@aries:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

You will now need to build the wl.ko file.  You have to go back to the step:
```
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`
```
and type the following:
```
make -C /lib/modules/`uname -r`/build M=`pwd` clean
make -C /lib/modules/`uname -r`/build M=`pwd`
```
This will build the wl.ko file that you need.

---

### Post by FFe_ on 2008-10-30
hi everyone. Ths is one of my firsts post here and my first experience in linux also. First of all, i wanted to thank and congratulate everyone participating in this community. I'm really glad of been a ubuntu user and i think that all the work made and been made here is awesome. Thank you very much for the help and for sharing all your knowledge.
in second place, i've a Compaq v3000 with a broadcom 4311 (rev 02).
 i've been fighting with my wireless for weeks and I have got no succes in it.
i followed this guide, and it looks like it is almost working.
Basically, i've installed the wl module, i'm quite sure that there's no other module interfering with it. ssb issue only, i've solved it doing: 
sudo rmmod ssb
sudo rmmod wl
sudo modprobe wl
sudo modprobe ssb)

after doing this, the blue light of the wireless card, turns on.
Also, a new interface appears (eth1).
and here comes my two firsts (and probably dumb) questions: where did that interface came from? is that the one that i have to configure in order to connect?

the iwlist scan command returns the info of my home network router (under eth1).
so i conclude that the wireless device it is working (at least it can scan... :P)

but i dont' know how to make it connect to the router.
i tried a lot of things (configuring essid and key with iwconfig, defining eth1 interface in the /etc/network/intefaces file, the ifup, ifdown, ifconfig, restarting network services...)but none had worked. 

anyone can give me a hand? am i doing a lot of mess or this is the right path to follow?

thank you very much, in advance.
Pd: sorry for my english. Ages passed since last time i wrote anything in english.

---

### Post by Ayuthia on 2008-10-30
> **FFe_ said:**
> hi everyone. Ths is one of my firsts post here and my first experience in linux also. First of all, i wanted to thank and congratulate everyone participating in this community. I'm really glad of been a ubuntu user and i think that all the work made and been made here is awesome. Thank you very much for the help and for sharing all your knowledge.
in second place, i've a Compaq v3000 with a broadcom 4311 (rev 02).
 i've been fighting with my wireless for weeks and I have got no succes in it.
i followed this guide, and it looks like it is almost working.
Basically, i've installed the wl module, i'm quite sure that there's no other module interfering with it. ssb issue only, i've solved it doing: 
sudo rmmod ssb
sudo rmmod wl
sudo modprobe wl
sudo modprobe ssb)

after doing this, the blue light of the wireless card, turns on.
Also, a new interface appears (eth1).
and here comes my two firsts (and probably dumb) questions: where did that interface came from? is that the one that i have to configure in order to connect?

the iwlist scan command returns the info of my home network router (under eth1).
so i conclude that the wireless device it is working (at least it can scan... :P)

but i dont' know how to make it connect to the router.
i tried a lot of things (configuring essid and key with iwconfig, defining eth1 interface in the /etc/network/intefaces file, the ifup, ifdown, ifconfig, restarting network services...)but none had worked. 

anyone can give me a hand? am i doing a lot of mess or this is the right path to follow?

thank you very much, in advance.
Pd: sorry for my english. Ages passed since last time i wrote anything in english.

Do you have encryption set on your router?  If so, you might turn off WEP/WPA and see if you can connect.  This driver does not always do too well with WPA/WEP with some of the cards.  So if it does not work with WEP but it works without WEP, you might try using WPA.  If you are using WPA, you will need to figure out how to configure WPA using wpa_supplicant.  I don't know too much about how to configure that though.  As far as I know, WPA cannot be set up using iwconfig essid and key.

---

### Post by FFe_ on 2008-10-30
> **Ayuthia said:**
> Do you have encryption set on your router?  If so, you might turn off WEP/WPA and see if you can connect.  This driver does not always do too well with WPA/WEP with some of the cards.  So if it does not work with WEP but it works without WEP, you might try using WPA.  If you are using WPA, you will need to figure out how to configure WPA using wpa_supplicant.  I don't know too much about how to configure that though.  As far as I know, WPA cannot be set up using iwconfig essid and key.

Hi! thank you for the fast answer! I disabled any kind of security (wep, wpa, mac filtering, etc..) in order to have as few obstacles as posible.
but i have GOOD NEWS!!!
i didn't want to, but, i installed Gnome-network-manager and guess what???
i'm posting this, wireless!
So, the driver works well, and indeed, it uses eth1 interface (the one the wl module creates when it gets loaded).

The thing now is to know/learn what does network-manager do, in order to make it my self, by hand.
Should i post this in a new thread? i`ll look for it first.
i don't understand how is that it can connect. the iwconfig command returs this:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated
```

the ifconfig:

```

eth0      Link encap:Ethernet  direcciónHW 00:16:d3:ae:e1:cb  
          inet dirección:192.168.1.101  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::216:d3ff:feae:e1cb/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:5190 (5.0 KB)  TX bytes:4239 (4.1 KB)
          Interrupción:19 Dirección base: 0x8000 

eth1      Link encap:Ethernet  direcciónHW 00:1a:73:95:a1:ea  
          inet dirección:192.168.1.100  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::21a:73ff:fe95:a1ea/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:619 errors:0 dropped:0 overruns:0 frame:32
          TX packets:545 errors:3 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:642771 (627.7 KB)  TX bytes:128096 (125.0 KB)
          Interrupción:16 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:324 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:16200 (15.8 KB)  TX bytes:16200 (15.8 KB)
```

and my /etc/network/interfaces is:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```
...
theres is something i'm missing...
i don't know. if someone wants/can enlighten me, i would be grateful.

i'll start my new research right now.
thanks again

---

### Post by Ayuthia on 2008-10-30
> **FFe_ said:**
> Hi! thank you for the fast answer! I disabled any kind of security (wep, wpa, mac filtering, etc..) in order to have as few obstacles as posible.
but i have GOOD NEWS!!!
i didn't want to, but, i installed Gnome-network-manager and guess what???
i'm posting this, wireless!
So, the driver works well, and indeed, it uses eth1 interface (the one the wl module creates when it gets loaded).

The thing now is to know/learn what does network-manager do, in order to make it my self, by hand.
Should i post this in a new thread? i`ll look for it first.

Thank you very much,
the guide is very good. I feel i've already learnt a lot.
I am glad to see that you have it working.  Usually if you are doing it manually without encryption you should be able to do the following:
```
sudo ifconfig eth1 up
sudo iwconfig eth1 essid my-router
sudo dhclient eth1
```and it should try to connect.

You might even read this thread:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
kevdog wrote a really good thread about how to connect manually.

EDIT: I just ran the liveCD for Intrepid and tried to connect manually only to find that it would not connect.  It looks like NetworkManager is fighting with the manual connection.  As soon as I killed the NetworkManager process, I was able to connect manually.  That might be your problem.

---

### Post by PinkFloyd102489 on 2008-10-31
/etc/network/interfaces should look like:

```

auto lo
iface lo inet loopback

```

eth0 and eth1 will autoconfigure and autoconnect.

---

### Post by FFe_ on 2008-10-31
thank you! it's indeed a very good thread.
I got rid of network manger, connected manually using WPA encription.
Thank you very much for all the help you gave me. 
with all this information, i'm going to give intrepid a try, to see if everything works.
thanks again.

---

### Post by FFe_ on 2008-11-17
hi! i'm back. with intrepid this time. I had no need of installing the wl sta driver by hand cause it came with the restricted drivers. And it seems to work just as fine. i've noticed a couple of things anyway.

One is that i cannot compile the driver anymore (lots of errors). I tried to follow this wonderful guide once again (for pleasure of doing things by hand only...) and I couldn't get past the second step :( . 

The other thing is that with this version of the driver (the one that comes with intrepid) I cannot make a ```
 iwlist scan 
``` it says that there are no interfaces that support scanning. Its strange, because with the compiled driver in ubuntu 8.04 scanning worked fine and (i suppose) the driver is the same, am i right?

well, that's all for now,
just wanted to learn a litte more :)
thanks again to everyone.

---

### Post by Ayuthia on 2008-11-18
> **FFe_ said:**
> hi! i'm back. with intrepid this time. I had no need of installing the wl sta driver by hand cause it came with the restricted drivers. And it seems to work just as fine. i've noticed a couple of things anyway.

One is that i cannot compile the driver anymore (lots of errors). I tried to follow this wonderful guide once again (for pleasure of doing things by hand only...) and I couldn't get past the second step :( . 

The other thing is that with this version of the driver (the one that comes with intrepid) I cannot make a ```
 iwlist scan 
``` it says that there are no interfaces that support scanning. Its strange, because with the compiled driver in ubuntu 8.04 scanning worked fine and (i suppose) the driver is the same, am i right?

well, that's all for now,
just wanted to learn a litte more :)
thanks again to everyone.

If you are going to compile the driver from scratch in 2.6.27, you will need to apply a patch:
[http://jaux.net/2008/10/14/patch-to-broadcom-80211-linux-sta-driver-for-kernel-2627/](http://jaux.net/2008/10/14/patch-to-broadcom-80211-linux-sta-driver-for-kernel-2627/)

This is a link that conatains the link to the patch along with how to do it at the bottom.

---

### Post by FFe_ on 2008-11-18
> **Ayuthia said:**
> If you are going to compile the driver from scratch in 2.6.27, you will need to apply a patch:
[http://jaux.net/2008/10/14/patch-to-broadcom-80211-linux-sta-driver-for-kernel-2627/](http://jaux.net/2008/10/14/patch-to-broadcom-80211-linux-sta-driver-for-kernel-2627/)

This is a link that conatains the link to the patch along with how to do it at the bottom.



just excellent, as always...

thank you very much.

---

### Post by gunnar123 on 2008-11-20
Hello small question to you Broadcom experienced users;
I'm looking at determining what miniPCI card to get for upgrading a B/G configured laptop to N speeds and get it to work under Ubuntu Intrepid with actual N speeds. I figured from Broadcom threads that those cards stand a good chance of actually reaching above G speed ?  And user support seem superior :) Any particular card to recommend, I see several BCM4321 cards on Ebay ? I'm looking at plugging one into an Eee PC..

Thanks for advice,

---

### Post by brianadkins on 2008-11-20
I am getting errors early on when I execute the MAKE commands...

...any ideas?
[LIST]fresh install of ubuntu 8.1 
[/LIST]
[LIST]
emachines laptop with broadcom bcmwl5.sys drivers
[/LIST]



```
brian@brian-laptop:~/wdriver$ make -C /lib/modules/`uname -r`/build M=`pwd` clean
make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CLEAN   /home/brian/wdriver/.tmp_versions
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
brian@brian-laptop:~/wdriver$ make -C /lib/modules/`uname -r`/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/brian/wdriver/built-in.o
  CC [M]  /home/brian/wdriver/src/wl/sys/wl_linux.o
  CC [M]  /home/brian/wdriver/src/wl/sys/wl_iw.o
/home/brian/wdriver/src/wl/sys/wl_iw.c: In function ‘wl_iw_get_scan’:
/home/brian/wdriver/src/wl/sys/wl_iw.c:934: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:934: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:934: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/brian/wdriver/src/wl/sys/wl_iw.c:934: error: too few arguments to function ‘iwe_stream_add_event’
/home/brian/wdriver/src/wl/sys/wl_iw.c:939: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:939: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:939: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:939: error: too few arguments to function ‘iwe_stream_add_point’
/home/brian/wdriver/src/wl/sys/wl_iw.c:947: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:947: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:947: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/brian/wdriver/src/wl/sys/wl_iw.c:947: error: too few arguments to function ‘iwe_stream_add_event’
/home/brian/wdriver/src/wl/sys/wl_iw.c:955: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:955: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:955: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/brian/wdriver/src/wl/sys/wl_iw.c:955: error: too few arguments to function ‘iwe_stream_add_event’
/home/brian/wdriver/src/wl/sys/wl_iw.c:961: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:961: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:961: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/brian/wdriver/src/wl/sys/wl_iw.c:961: error: too few arguments to function ‘iwe_stream_add_event’
/home/brian/wdriver/src/wl/sys/wl_iw.c:973: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:973: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:973: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:973: error: too few arguments to function ‘iwe_stream_add_point’
/home/brian/wdriver/src/wl/sys/wl_iw.c:981: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:981: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:981: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:981: error: too few arguments to function ‘iwe_stream_add_point’
/home/brian/wdriver/src/wl/sys/wl_iw.c:992: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:992: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:992: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:992: error: too few arguments to function ‘iwe_stream_add_point’
/home/brian/wdriver/src/wl/sys/wl_iw.c:1006: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:1006: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:1006: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:1006: error: too few arguments to function ‘iwe_stream_add_point’
/home/brian/wdriver/src/wl/sys/wl_iw.c:1016: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:1016: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:1016: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/brian/wdriver/src/wl/sys/wl_iw.c:1016: error: too few arguments to function ‘iwe_stream_add_value’
make[1]: *** [/home/brian/wdriver/src/wl/sys/wl_iw.o] Error 1
make: *** [_module_/home/brian/wdriver] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
brian@brian-laptop:~/wdriver$ 
```

---

### Post by Ayuthia on 2008-11-20
> **brianadkins said:**
> I am getting errors early on when I execute the MAKE commands...

...any ideas?
[LIST]fresh install of ubuntu 8.1 
[/LIST]
[LIST]
emachines laptop with broadcom bcmwl5.sys drivers
[/LIST]



```
brian@brian-laptop:~/wdriver$ make -C /lib/modules/`uname -r`/build M=`pwd` clean
make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CLEAN   /home/brian/wdriver/.tmp_versions
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
brian@brian-laptop:~/wdriver$ make -C /lib/modules/`uname -r`/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/brian/wdriver/built-in.o
  CC [M]  /home/brian/wdriver/src/wl/sys/wl_linux.o
  CC [M]  /home/brian/wdriver/src/wl/sys/wl_iw.o
/home/brian/wdriver/src/wl/sys/wl_iw.c: In function &#8216;wl_iw_get_scan&#8217;:
/home/brian/wdriver/src/wl/sys/wl_iw.c:934: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:934: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:934: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/brian/wdriver/src/wl/sys/wl_iw.c:934: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/brian/wdriver/src/wl/sys/wl_iw.c:939: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:939: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:939: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:939: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/brian/wdriver/src/wl/sys/wl_iw.c:947: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:947: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:947: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/brian/wdriver/src/wl/sys/wl_iw.c:947: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/brian/wdriver/src/wl/sys/wl_iw.c:955: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:955: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:955: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/brian/wdriver/src/wl/sys/wl_iw.c:955: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/brian/wdriver/src/wl/sys/wl_iw.c:961: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:961: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:961: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/brian/wdriver/src/wl/sys/wl_iw.c:961: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/brian/wdriver/src/wl/sys/wl_iw.c:973: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:973: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:973: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:973: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/brian/wdriver/src/wl/sys/wl_iw.c:981: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:981: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:981: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:981: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/brian/wdriver/src/wl/sys/wl_iw.c:992: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:992: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:992: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:992: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/brian/wdriver/src/wl/sys/wl_iw.c:1006: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:1006: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:1006: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:1006: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/brian/wdriver/src/wl/sys/wl_iw.c:1016: warning: passing argument 1 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:1016: warning: passing argument 4 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/brian/wdriver/src/wl/sys/wl_iw.c:1016: warning: passing argument 5 of &#8216;iwe_stream_add_value&#8217; makes pointer from integer without a cast
/home/brian/wdriver/src/wl/sys/wl_iw.c:1016: error: too few arguments to function &#8216;iwe_stream_add_value&#8217;
make[1]: *** [/home/brian/wdriver/src/wl/sys/wl_iw.o] Error 1
make: *** [_module_/home/brian/wdriver] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
brian@brian-laptop:~/wdriver$ 
```

You need to apply the patch listed in post #73.

---

### Post by Eeeff on 2008-12-14
Wrong discussion post

---

### Post by Nishya on 2008-12-28
Hello, I've tried following this thread and had no problem. But when I get to this part, something not expected occurs:

> **Ayuthia said:**
> It should just be a matter of going into System->Administration->Hardware Drivers and enabling the Broadcom STA option.

When I check the box to enable the driver, the system asks me to restart. After restarting, when I go to Hardware Drivers, the box is still unchecked. I tried more times but got no success.

Is there any way to enable this driver through command-line? Or at least to get a more verbose output...

Thanks in advance for your help!

---

### Post by Ayuthia on 2008-12-28
> **Nishya said:**
> Hello, I've tried following this thread and had no problem. But when I get to this part, something not expected occurs:



When I check the box to enable the driver, the system asks me to restart. After restarting, when I go to Hardware Drivers, the box is still unchecked. I tried more times but got no success.

Is there any way to enable this driver through command-line? Or at least to get a more verbose output...

Thanks in advance for your help!
If it is asking you to restart, then you are choosing the b43 option.  The Broadcom STA option does not require a reboot.

Can you post the results of:
```
lspci -nn
lsmod |grep -e b43 -e ssb -e wl
```

---

### Post by Nishya on 2008-12-28
Firstly, thank you for your answer!

My output to those commands are as follows:
```

elisabete@touya:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
03:01.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 21)
03:01.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

elisabete@touya:~$ lsmod |grep -e b43 -e ssb -e wl
wl                   1081936  0 
ieee80211_crypt         8192  2 ieee80211_crypt_tkip,wl
```

AFAIK, I've nothing related to b43 installed/loaded/whatever... :confused:

---

### Post by pend on 2008-12-28
I got the driver installed on my lenovo S10e with ubuntu 8.10
and the closed source driver. But it dont work.
I check the status and sees.

#iwlist eth1 txpower
eth1      2 available transmit-powers :
          0 dBm         (1 mW)
          25 dBm        (255 mW)
          Current Tx-Power:off

# iwlist eth1 power
eth1      Current mode:All packets received

So I try to powerup the device.

# iwconfig eth1 txpower on
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Operation not supported.

Did not work. I try something else.

# iwconfig eth1 essid any
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Invalid argument

Some config does not return error.
# iwconfig eth1 mode managed
# iwconfig eth1 channel 2
# iwconfig eth1 bit auto
# iwconfig eth1 power on

# iwlist eth1 scan
eth1      Failed to read scan data : Invalid argument


The driver does not work with the lenovo s10e. (bcm4312 from broadcom)
with the 2.6.27-9-generic ubunto.

Any ideas?

---

### Post by Ayuthia on 2008-12-28
> **Nishya said:**
> Firstly, thank you for your answer!

My output to those commands are as follows:
```

elisabete@touya:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
03:01.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 21)
03:01.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

elisabete@touya:~$ lsmod |grep -e b43 -e ssb -e wl
wl                   1081936  0 
ieee80211_crypt         8192  2 ieee80211_crypt_tkip,wl
```

AFAIK, I've nothing related to b43 installed/loaded/whatever... :confused:

You can try the following to see if it will work:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```
Can you also let us know the make and model of your laptop?

---

### Post by Ayuthia on 2008-12-28
> **pend said:**
> I got the driver installed on my lenovo S10e with ubuntu 8.10
and the closed source driver. But it dont work.
I check the status and sees.

#iwlist eth1 txpower
eth1      2 available transmit-powers :
          0 dBm         (1 mW)
          25 dBm        (255 mW)
          Current Tx-Power:off

# iwlist eth1 power
eth1      Current mode:All packets received

So I try to powerup the device.

# iwconfig eth1 txpower on
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Operation not supported.

Did not work. I try something else.

# iwconfig eth1 essid any
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Invalid argument

Some config does not return error.
# iwconfig eth1 mode managed
# iwconfig eth1 channel 2
# iwconfig eth1 bit auto
# iwconfig eth1 power on

# iwlist eth1 scan
eth1      Failed to read scan data : Invalid argument


The driver does not work with the lenovo s10e. (bcm4312 from broadcom)
with the 2.6.27-9-generic ubunto.

Any ideas?

jron also has a lenovo s10 and he was able to get his compiled manually:
[http://ubuntuforums.org/showthread.php?t=1010751&page=3](http://ubuntuforums.org/showthread.php?t=1010751&page=3)

Here is a set of instructions that can help you compile the Broadcom STA module:
[http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&Itemid=61](http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&Itemid=61)

Since jron mentioned that it is in the alpha 2 for Jaunty, my guess is that the updated wl module will come down to Intrepid soon.

---

### Post by pend on 2008-12-28
Thanks but the patch fails on  2.6.27-9-generic
# patch -p5 -E --dry-run < ../hybrid_wl-5.10.27.11_patch-2.6.27 
patching file src/wl/sys/wl_iw.c
Hunk #1 FAILED at 943.
Hunk #2 FAILED at 956.
Hunk #3 FAILED at 964.
Hunk #4 FAILED at 982.
Hunk #5 FAILED at 990.
Hunk #6 FAILED at 1001.
Hunk #7 FAILED at 1015.
Hunk #8 FAILED at 1024.
8 out of 8 hunks FAILED -- saving rejects to file src/wl/sys/wl_iw.c.rej

But I dont have any problem with compiling. I have problem to get it powerd up.

---

### Post by pend on 2008-12-28
My problem with the lenovo S10e was solved with an update of the bios.
14cn50ww to 15cn51ww and it was starting directly!

---

### Post by Ayuthia on 2008-12-28
> **pend said:**
> Thanks but the patch fails on  2.6.27-9-generic
# patch -p5 -E --dry-run < ../hybrid_wl-5.10.27.11_patch-2.6.27 
patching file src/wl/sys/wl_iw.c
Hunk #1 FAILED at 943.
Hunk #2 FAILED at 956.
Hunk #3 FAILED at 964.
Hunk #4 FAILED at 982.
Hunk #5 FAILED at 990.
Hunk #6 FAILED at 1001.
Hunk #7 FAILED at 1015.
Hunk #8 FAILED at 1024.
8 out of 8 hunks FAILED -- saving rejects to file src/wl/sys/wl_iw.c.rej

But I dont have any problem with compiling. I have problem to get it powerd up.
Can you do me a favor and attach the info from src/wl/sys/wl_iw.c.rej?  I would like to see why it failed.

---

### Post by slugicide on 2009-02-07
A while back I was given a work-around to getting my wireless to work. Unfortunately it involves entering some commands each time I boot. ```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
sudo modprobe ndiswrapper
``` to be specific. Is there any way I can get this done automatically? Like a shell script or something (as if I could write a shell script!) Thanks!

---

### Post by Ayuthia on 2009-02-07
> **slugicide said:**
> A while back I was given a work-around to getting my wireless to work. Unfortunately it involves entering some commands each time I boot. ```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
sudo modprobe ndiswrapper
``` to be specific. Is there any way I can get this done automatically? Like a shell script or something (as if I could write a shell script!) Thanks!

Have you tried the following:
```
echo -e '#ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb wl; modprobe --ignore-install ndiswrapper' | sudo tee -a /etc/modprobe.d/ndiswrapper
```

---

### Post by slugicide on 2009-02-07
> **Ayuthia said:**
> Have you tried the following:
```
echo -e '#ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb wl; modprobe --ignore-install ndiswrapper' | sudo tee -a /etc/modprobe.d/ndiswrapper
```


Is this safe to try if I only have wireless access?

---

### Post by Ayuthia on 2009-02-07
> **slugicide said:**
> Is this safe to try if I only have wireless access?

Yes.  If for any reason you have any problems, you can always edit /etc/modprobe.d/ndiswrapper and remove the last line.  The command only removes the possible wireless modules and then adds ndiswrapper back.  It is placed at the end of /etc/modprobe.d/ndiswrapper.  To edit the file after you add the command:
```
gksu gedit /etc/modprobe.d/ndiswrapper
```

---

### Post by slugicide on 2009-02-07
> **Ayuthia said:**
> Yes.  If for any reason you have any problems, you can always edit /etc/modprobe.d/ndiswrapper and remove the last line.  The command only removes the possible wireless modules and then adds ndiswrapper back.  It is placed at the end of /etc/modprobe.d/ndiswrapper.  To edit the file after you add the command:
```
gksu gedit /etc/modprobe.d/ndiswrapper
```


Worked like a magic charm. Thanks Ayuthia!

---

### Post by aeleneski on 2009-02-21
Well I tried installing this with the latest version of the broadcom driver from 1/21 and 2.6.27-12-generic kernel, and everything seems to install fine. I am able to see my wireless network, but upon trying to connect it never does and eventually times out.

---

### Post by loglogn on 2009-03-11
> **pend said:**
> My problem with the lenovo S10e was solved with an update of the bios.
14cn50ww to 15cn51ww and it was starting directly!

Where exactly did you find version 15CN51WW?
The latest I can find is 14CN51WW.

In fact, googling 15CN51WW returns only your post...

---

### Post by garypeg on 2009-03-23
I have a Broadcom 4311 on an HPdv2000.  I do not have a hard wire connection.  Does anyone know how to install the driver and firmware without an internet connection?   I have another laptop that connects via XP so I can get instructions and download drivers.  Thanks.

---

### Post by infected521 on 2009-04-02
(SOLUCIONADO DRIVERS DE LINUX DI NO AL NDISWRAPPER)

HOLA A TODOS AKI LES DEJO LA SOLUCION PARA INSTALAR WIRELESS BCM4311, BCM4312, BCM4321, and BCM4322  
  

FUNCIONAN A LA PERFECCION 120% DE FUNCIONALIDAD akiles dejo el link para klo  descarguen  adentro va un tutorial el tutorial se llama bcm4311 leanlo primero adjunto todo lonesesario para hacerla funcionar 


[http://www.4shared.com/file/96305718/8ea0810e/drivers_broadcom_bcm4311tar.html](http://www.4shared.com/file/96305718/8ea0810e/drivers_broadcom_bcm4311tar.html)

---

### Post by c_07 on 2009-04-02
Thank you very much -- this worked on the first try! I've used ndiswrapper in the past, for some time, but have never been able to get the native drivers working for my laptop. Since upgrading to 9.04 Beta, I was forced to seek an alternative solution since I could see and connect to normal, unencrypted networks just fine, but not to those with WPA or WPA2. This fixed my problem.

Thanks again!

---

### Post by contractcooker on 2009-04-07
So,
I'm trying to use this tutorial for 64Studio 3.0 Beta 3 which is based on Ubuntu (hardy I believe) I have problems here:

root@64studio:~# make -C /lib/modules/2.6.29-1-multimedia-amd64/build M='pwd'clean
make: Entering directory `/usr/src/linux-headers-2.6.29-1-multimedia-amd64'
scripts/Makefile.build:41: /usr/src/linux-headers-2.6.29-1-multimedia-amd64/pwdclean/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.29-1-multimedia-amd64/pwdclean/Makefile'.  Stop.
make: *** [_module_pwdclean] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.29-1-multimedia-amd64'
root@64studio:~# 

I'm definitely a newb and sort of just copying and pasting into terminal without knowing what I'm doing (I KNOW BAD IDEA but how else am I going to learn?) I'd really appreciate if someone could tell me what is going wrong and why.

thanks in advance tb

---

### Post by Ayuthia on 2009-04-07
> **contractcooker said:**
> So,
I'm trying to use this tutorial for 64Studio 3.0 Beta 3 which is based on Ubuntu (hardy I believe) I have problems here:

root@64studio:~# make -C /lib/modules/2.6.29-1-multimedia-amd64/build M='pwd'clean
make: Entering directory `/usr/src/linux-headers-2.6.29-1-multimedia-amd64'
scripts/Makefile.build:41: /usr/src/linux-headers-2.6.29-1-multimedia-amd64/pwdclean/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.29-1-multimedia-amd64/pwdclean/Makefile'.  Stop.
make: *** [_module_pwdclean] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.29-1-multimedia-amd64'
root@64studio:~# 

I'm definitely a newb and sort of just copying and pasting into terminal without knowing what I'm doing (I KNOW BAD IDEA but how else am I going to learn?) I'd really appreciate if someone could tell me what is going wrong and why.

thanks in advance tb
The 'pwd'clean should have been `pwd` clean.  They are back-quotes instead of single quotes.  If you try it in the Terminal:
```
echo `pwd`
```It should return the current directory that you are in instead of pwd.  You will also need a space after the quote and the word clean.

The other part is that you are trying to compile this under 2.6.29.  If you don't have a patch for it, it will most likely not compile.

---

### Post by outlaw85 on 2009-04-11
Brand new to Ubuntu, so make it idiot proof please.  On step 4, after the command 

sudo insmod wl.ko 

I see

insmod: error inserting 'wl.ko': -1 File exists

This is what I get after following Ayuthia advice from page one

justin@Compaq:~/wdriver$ lsmod |grep -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl 
wl                   1489864  0  
ieee80211_crypt        13572  2 wl,ieee80211_crypt_tkip 
ssb                    40580  0  
justin@Compaq:~/wdriver$ uname -r 
2.6.27-7-generic 
justin@Compaq:~/wdriver$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network:0              
       description: Network controller 
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver 
       vendor: Broadcom Corporation 
       physical id: 2 
       bus info: pci@0000:06:02.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 6 
       bus info: pci@0000:06:06.0 
       logical name: eth0 
       version: 10 
       serial: 00:16:d4:07:cb:bd 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 32:8a:34:ce:3b:48 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 

Can someone please help.  Thank you in advance.

---

### Post by Obituaryfreak on 2009-04-19
hi
I get the following error:
ahid@RockerGeek:~/hybrid_wl$ sudo make -C /lib/modules/`uname -r`/build M='pwd'
make: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
make[1]: *** No rule to make target `pwd/src/wl/sys/wl_linux.o', needed by `pwd/wl.o'.  Stop.
make: *** [_module_pwd] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
 what do you think?
 Intrepid 
 HP2070ee tablet pc.
BCM4312

---

### Post by Ayuthia on 2009-04-19
> **Obituaryfreak said:**
> hi
I get the following error:
ahid@RockerGeek:~/hybrid_wl$ sudo make -C /lib/modules/`uname -r`/build M='pwd'
make: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
make[1]: *** No rule to make target `pwd/src/wl/sys/wl_linux.o', needed by `pwd/wl.o'.  Stop.
make: *** [_module_pwd] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
 what do you think?
 Intrepid 
 HP2070ee tablet pc.
BCM4312

Your 'pwd' needs to be `pwd` (backquote instead of single quote):
```
sudo make -C /lib/modules/`uname -r`/build M=`pwd`
```

---

### Post by Ayuthia on 2009-04-19
> **outlaw85 said:**
> Brand new to Ubuntu, so make it idiot proof please.  On step 4, after the command 

sudo insmod wl.ko 

I see

insmod: error inserting 'wl.ko': -1 File exists

This is what I get after following Ayuthia advice from page one

justin@Compaq:~/wdriver$ lsmod |grep -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl 
wl                   1489864  0  
ieee80211_crypt        13572  2 wl,ieee80211_crypt_tkip 
ssb                    40580  0  
justin@Compaq:~/wdriver$ uname -r 
2.6.27-7-generic 
justin@Compaq:~/wdriver$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network:0              
       description: Network controller 
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver 
       vendor: Broadcom Corporation 
       physical id: 2 
       bus info: pci@0000:06:02.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 6 
       bus info: pci@0000:06:06.0 
       logical name: eth0 
       version: 10 
       serial: 00:16:d4:07:cb:bd 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 32:8a:34:ce:3b:48 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 

Can someone please help.  Thank you in advance.

It looks like you might need to try the following:
```
modprobe -r b43 ssb ndiswrapper wl ieee80211_crypt_tkip
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko
sudo ifconfig eth1 up
sudo iwlist scan
```
Your system is currently trying to use the Ubuntu supplied version instead of the one that you compiled.  These commands will remove the Ubuntu supplied version and replace it with the one that you compiled.

---

### Post by devildoc5 on 2009-06-21
ok dummy and newb combined here.......

I have gotten to the point in the above mentioned steps where I am supposed to "test the driver"  the problem is that sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko don't seem to do anything.  I have tried moving the wl.ko file to all sorts of places and none of the locations seem to work. both the /lib/firmware/ and the lib/modules .  This does not seem to have any affect either.  I decided to try and use the driver locator to do this out of frustration.  I performed the following: sudo ifconfig eth1 down
sudo rmmod wl
sudo modprobe b43

then went into the driver manager, problem being that I have no wired internet service at this time and that obviously I just turned the wireless off.  It does show the b43 as an option, but can't download because of ^^^.  Also I cannot sudo ifconfig eth1 up.  It does not seem to work.  I have to restart my computer to get eth1 working again.

FYI for some reason my wireless is eth1.  IDK why but that is how it happened.  

Does anyone have any idea how I can get this driver working correctly (the b43)?

---

### Post by Ayuthia on 2009-06-21
> **devildoc5 said:**
> ok dummy and newb combined here.......

I have gotten to the point in the above mentioned steps where I am supposed to "test the driver"  the problem is that sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko don't seem to do anything.  I have tried moving the wl.ko file to all sorts of places and none of the locations seem to work. both the /lib/firmware/ and the lib/modules .  This does not seem to have any affect either.  I decided to try and use the driver locator to do this out of frustration.  I performed the following: sudo ifconfig eth1 down
sudo rmmod wl
sudo modprobe b43

then went into the driver manager, problem being that I have no wired internet service at this time and that obviously I just turned the wireless off.  It does show the b43 as an option, but can't download because of ^^^.  Also I cannot sudo ifconfig eth1 up.  It does not seem to work.  I have to restart my computer to get eth1 working again.

FYI for some reason my wireless is eth1.  IDK why but that is how it happened.  

Does anyone have any idea how I can get this driver working correctly (the b43)?

If you are still able to get the wl.ko module to work to get wireless, the best route would be to install b43-fwcutter:
```
sudo apt-get install b43-fwcutter
```Once it is installed you can then test out the native module:
```
sudo modprobe -r b43 ssb wl
sudo modprobe b43
sudo iwlist scan
```

If you are not able to get it to work, try the following:
```
sudo dpkg-reconfigure linux-restricted-modules
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```If it works, then you can do the b43-fwcutter install.

Hope that helps.

---

### Post by devildoc5 on 2009-06-21
ok so I tired an iwconfig scan and got a new interface with wlan0 but it said it was down.  I went to do an ifconfig wlan0 up and it said no such device........  Any ideas?

also I get a bad md5 when I try b43 cutter.  Should I try to make again?

here is the results after I run your commands:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


but if I try to run sudo iwconfig wlan0 up it says not found.....

---

### Post by Ayuthia on 2009-06-21
Ok.  I think I am confused.  I just looked at the original post and saw that it is installing the wl.ko file.  However in your post, you wanted to activate the b43.  Which one do you want to use?  Also which version of Ubuntu are you using (Hardy, Intrepid, Jaunty)?  You probably only need this guide if you are using Hardy.  System->Administration->Hardware Drivers provides the Broadcom STA module (the wl.ko version).

If you are wanting to use the Broadcom STA version, you will need to remove the b43 and ssb modules:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```
This should change the logical name of your wireless card from wlan0 to eth1 and then produce some wireless sites.

---

### Post by devildoc5 on 2009-06-21
ok apparently I am the one that is confused now.  I am currently using the sta driver however does not allow monitor mode (or I cant get it working at least) need to use the b43 driver.  I am using Jaunty 9.04.

---

### Post by kevdog on 2009-06-22
What kind of wireless card do you have (lspci -nnm)?  I'm only asking that because some cards can do a b43/wl crossover, and some can not -- meaning they can only use b43 or wl.

---

### Post by Ayuthia on 2009-06-22
Ok.  I am on the same page as you then.  I would like to get the Broadcom STA module working again so that we can install the b43-fwcutter application.  It is easier to do it this way than to try and build the application.

However, I am in agreement with kevdog.  We should confirm that your card can use the b43 module.  There are a few Broadcom cards that are not compatible withe b43/b43legacy.

---

### Post by Bit101 on 2009-06-22
My Broadcom BCM4312 wireless card stopped working on Jaunty after I updated the kernel. Wireless no longer works, though  i still have ethernet, and the driver didn't seem to help.

---

### Post by Bit101 on 2009-06-22
(bump)

---

### Post by chuckmurphy on 2009-06-26
> **PinkFloyd102489 said:**
> System > Administration > Hardware Drivers


If it still doesnt work when enabled, do:

```

sudo lshw -C Network

```If the wireless interface has wl listed but isnt working, run this script (assuming you have a broadcom ethernet card also).

```

#!/bin/bash
sudo rmmod b44
sudo rmmod ssb
sudo rmmod wl
sudo modprobe wl
sudo modprobe ssb
sudo modprobe b44
sudo ifconfig

```

IT WORKED!  Thank you so much!

UH... well, it did.  No wireless when I rebooted.  Any suggestions?

---

### Post by Ayuthia on 2009-06-26
> **chuckmurphy said:**
> IT WORKED!  Thank you so much!

UH... well, it did.  No wireless when I rebooted.  Any suggestions?

You can try adding it to /etc/rc.local.  Edit rc.local:
```
gksu gedit /etc/rc.local
```
and right before the exit 0 line, add the following:
```
rmmod b43
rmmod b44
rmmod ssb
rmmod wl
modprobe wl
modprobe b44
```Save the file.  This script is run every time the system boots up so it will automatically run those commands for you.

Hope that helps.

---

### Post by NTHQ on 2009-06-27
Hi, very big newb here...
I also have and HP dv9000 and I did everything on the first post but the light is still orange on my wireless switch...
I read some of the replies but I'm not even sure if any of them apply to me...
Please bear with me... :(

---

### Post by Ayuthia on 2009-06-27
> **NTHQ said:**
> Hi, very big newb here...
I also have and HP dv9000 and I did everything on the first post but the light is still orange on my wireless switch...
I read some of the replies but I'm not even sure if any of them apply to me...
Please bear with me... :(
Please go into the Terminal and post the results of:
```
lscpi
lshw -C network
```It will help us see which wireless card you have and what wireless module your card is trying to use.

---

### Post by chuckmurphy on 2009-06-27
> **Ayuthia said:**
> You can try adding it to /etc/rc.local.  Edit rc.local:
```
gksu gedit /etc/rc.local
```and right before the exit 0 line, add the following:
```
rmmod b43
rmmod b44
rmmod ssb
rmmod wl
modprobe wl
modprobe b44
```Save the file.  This script is run every time the system boots up so it will automatically run those commands for you.

Hope that helps.
Sorry, no dice.  Still having to do it through the Terminal.

---

### Post by Ayuthia on 2009-06-27
Can you please post your /etc/rc.local file?

---

### Post by chuckmurphy on 2009-06-27
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sudo insmod /lib/modules/`uname -r`/wlan/wl.ko
rmmod b43
rmmod b44
rmmod ssb
rmmod wl
modprobe wl
modprobe b44
exit 0
Thanks for all the help.  Total n00b here.

---

### Post by NTHQ on 2009-06-27
> **Ayuthia said:**
> Please go into the Terminal and post the results of:
```
lscpi
lshw -C network
```It will help us see which wireless card you have and what wireless module your card is trying to use.

```
nthq@nthq:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
nthq@nthq:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1e:68:5e:60:26
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.101 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7e:e7:fe:f6:65:ed
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
nthq@nthq:~$ 

```

---

### Post by Ayuthia on 2009-06-27
> **NTHQ said:**
> ```
nthq@nthq:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
nthq@nthq:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1e:68:5e:60:26
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.101 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7e:e7:fe:f6:65:ed
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
nthq@nthq:~$ 

```

Try the following to see if anything happens:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```

If it doesn't, please let us know which version of Ubuntu you are using.

---

### Post by Ayuthia on 2009-06-27
> **chuckmurphy said:**
> Thanks for all the help.  Total n00b here.

Let's change it to the following:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#sudo insmod /lib/modules/`uname -r`/wlan/wl.ko
rmmod b44
rmmod ssb
rmmod wl
modprobe wl
modprobe b44
exit 0 
```
I have taken out the rmmod b43 command and commented out the insmod command.  It looks like the modprobe wl works for you so the insmod should not be needed.  I took out the b43 line in case the system is saying that the module does not exist so it bails out of the script.

The only part I am not for sure about is if /lib/modules/`uname -r`/wlan/wl.ko still exists or not.  If you reboot and it still does not work, we might need to put the insmod command back in there or remove the rmmod wl line.

---

### Post by chuckmurphy on 2009-06-27
It lives!  Thanks a bunch.

---

### Post by NTHQ on 2009-06-28
> **Ayuthia said:**
> Try the following to see if anything happens:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```If it doesn't, please let us know which version of Ubuntu you are using.
It works! Thank you so much for your help.

---

### Post by NTHQ on 2009-07-01
> **Ayuthia said:**
> Try the following to see if anything happens:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```If it doesn't, please let us know which version of Ubuntu you are using.
Ok this works but the problem is that I have to enter these commands every time I reboot my computer. I am using Ubuntu 9.04.

---

### Post by Ayuthia on 2009-07-01
> **NTHQ said:**
> Ok this works but the problem is that I have to enter these commands every time I reboot my computer. I am using Ubuntu 9.04.

You should be able to add this to rc.local:
```
gksu gedit /etc/rc.local
```
Add the following before the exit 0 line:
```
modprobe -r b43 ssb wl
modprobe wl
```
That should get those commands to run when the system starts up.

Hope that helps.

---

### Post by fear_bot on 2009-07-17
Ok, I have trie everything her in this thread, but so far, I have gotten no where.

My driver is BCM4312, and I'm using Ubuntu 9.04.

Any help would be thankful.

---

### Post by halalkebabhut on 2009-08-07
I get up to stage 4 okay though I had to use a patched version of the driver from

[http://www.cenolan.com/broadcom-wl/](http://www.cenolan.com/broadcom-wl/)

to do it - got kernel 2.6.28-3-rt

but when I run : sudo modprobe ieee80211_crypt_tkip

I get this

WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.


can you help please (very n00b indeed)

HKH

---

### Post by Ayuthia on 2009-08-07
> **halalkebabhut said:**
> I get up to stage 4 okay though I had to use a patched version of the driver from

[http://www.cenolan.com/broadcom-wl/](http://www.cenolan.com/broadcom-wl/)

to do it - got kernel 2.6.28-3-rt

but when I run : sudo modprobe ieee80211_crypt_tkip

I get this

WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.


can you help please (very n00b indeed)

HKH

They are warning messages and should not hurt anything.  However, you should copy the information in /etc/modprobe.d/blacklist to /etc/modprobe.d/blacklist.conf.  The same should go with /etc/modprobe.d/oss-compat.  It should be copied into /etc/modprobe.d/oss-compat.conf.  You should check to see if /etc/modprobe.d/modprobe.conf exists.  If it does, you should copy the information from /etc/modprobe.conf into it.  If it does not, you might want to create another thread to verify where that file should belong.

---

### Post by jonathanmotes on 2009-08-09
When I run 
```
make -C /lib/modules/`uname -r`/build M=`pwd`
```

I get lines like this: (just a bit of the output)
```

make: Entering directory `/usr/src/linux-headers-2.6.30-02063004-generic'
  CC [M]  /home/motes/wdriver/src/wl/sys/wl_linux.o
/home/motes/wdriver/src/wl/sys/wl_linux.c:57:27: error: net/ieee80211.h: No such file or directory
/home/motes/wdriver/src/wl/sys/wl_linux.c: In function &#8216;wl_attach&#8217;:
/home/motes/wdriver/src/wl/sys/wl_linux.c:362: error: implicit declaration of function &#8216;ieee80211_get_crypto_ops&#8217;
/home/motes/wdriver/src/wl/sys/wl_linux.c:362: warning: assignment makes pointer from integer without a cast
/home/motes/wdriver/src/wl/sys/wl_linux.c:365: warning: assignment makes pointer from integer without a cast
/home/motes/wdriver/src/wl/sys/wl_linux.c: In function &#8216;wl_free&#8217;:
/home/motes/wdriver/src/wl/sys/wl_linux.c:634: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/motes/wdriver/src/wl/sys/wl_linux.c:669: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/motes/wdriver/src/wl/sys/wl_linux.c:685: error: dereferencing pointer to incomplete type
```

As you can see I'm using the 2.6.30.4 kernel....

---

### Post by Ayuthia on 2009-08-09
> **jonathanmotes said:**
> When I run 
```
make -C /lib/modules/`uname -r`/build M=`pwd`
```

I get lines like this: (just a bit of the output)
```

make: Entering directory `/usr/src/linux-headers-2.6.30-02063004-generic'
  CC [M]  /home/motes/wdriver/src/wl/sys/wl_linux.o
/home/motes/wdriver/src/wl/sys/wl_linux.c:57:27: error: net/ieee80211.h: No such file or directory
/home/motes/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_attach’:
/home/motes/wdriver/src/wl/sys/wl_linux.c:362: error: implicit declaration of function ‘ieee80211_get_crypto_ops’
/home/motes/wdriver/src/wl/sys/wl_linux.c:362: warning: assignment makes pointer from integer without a cast
/home/motes/wdriver/src/wl/sys/wl_linux.c:365: warning: assignment makes pointer from integer without a cast
/home/motes/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_free’:
/home/motes/wdriver/src/wl/sys/wl_linux.c:634: error: ‘struct net_device’ has no member named ‘priv’
/home/motes/wdriver/src/wl/sys/wl_linux.c:669: error: ‘struct net_device’ has no member named ‘priv’
/home/motes/wdriver/src/wl/sys/wl_linux.c:685: error: dereferencing pointer to incomplete type
```

As you can see I'm using the 2.6.30.4 kernel....

You are missing a patch that will make it compile for the 2.6.30 kernels.  You will need to figure out which version of the Broadcom STA source you are using and you can try the 2.6.30 patches from this [Gentoo link]("http://bugs.gentoo.org/248450").

---

### Post by jonathanmotes on 2009-08-09
> **Ayuthia said:**
> You are missing a patch that will make it compile for the 2.6.30 kernels.  You will need to figure out which version of the Broadcom STA source you are using and you can try the 2.6.30 patches from this [Gentoo link]("http://bugs.gentoo.org/248450").

OK. Thanks for helping me!

Is all I need the header file from [http://bugs.gentoo.org/attachment.cgi?id=189250](http://bugs.gentoo.org/attachment.cgi?id=189250)? If so, could you help me install it?

Thanks!

---

### Post by Ayuthia on 2009-08-09
> **jonathanmotes said:**
> OK. Thanks for helping me!

Is all I need the header file from [http://bugs.gentoo.org/attachment.cgi?id=189250](http://bugs.gentoo.org/attachment.cgi?id=189250)? If so, could you help me install it?

Thanks!
Just save that page as broadcom-sta.patch and place it where you do the make commands for the Broadcom STA source.  From there:
```
patch -p1 < broadcom-sta.patch
```
If it patches without any errors, you should be able to compile.

---

### Post by jonathanmotes on 2009-08-09
> **Ayuthia said:**
> Just save that page as broadcom-sta.patch and place it where you do the make commands for the Broadcom STA source.  From there:
```
patch -p1 < broadcom-sta.patch
```
If it patches without any errors, you should be able to compile.

Thank you! How long should this take by the way...its been sitting for more than a minute. Also, do I need to chmod the file? (it has 644 permissions).

---

### Post by Ayuthia on 2009-08-09
> **jonathanmotes said:**
> Thank you! How long should this take by the way...its been sitting for more than a minute. Also, do I need to chmod the file? (it has 644 permissions).
I should not take very long and you should not need to change the permissions.

Is it getting stuck in the patch or in the compile?

---

### Post by gwhamilton on 2009-08-09
I am very new to Uuntu and I'm having a hard time getting my wireless to work. I am running from an USB stick and everything else is running well, much quicker than windows. I have tried the windows wireless driver, I got the wireless card to power up, I think  it made the attempt to connect but couldn't.   I came accross this thread and tried to get this driver to work. I got past the first few steps but can't overcome the following error...

ubuntu@ubuntu:~/hybrid_wl$ make -C /lib/modules/<2.6.28.11>/build M=`pwd`
bash: 2.6.28.11: No such file or directory

I made the directory called out in this thread and also tried Broadcom's way. Can anyone get me past this? 
Thanks

---

### Post by Ayuthia on 2009-08-09
> **gwhamilton said:**
> I am very new to Uuntu and I'm having a hard time getting my wireless to work. I am running from an USB stick and everything else is running well, much quicker than windows. I have tried the windows wireless driver, I got the wireless card to power up, I think  it made the attempt to connect but couldn't.   I came accross this thread and tried to get this driver to work. I got past the first few steps but can't overcome the following error...

ubuntu@ubuntu:~/hybrid_wl$ make -C /lib/modules/<2.6.28.11>/build M=`pwd`
bash: 2.6.28.11: No such file or directory

I made the directory called out in this thread and also tried Broadcom's way. Can anyone get me past this? 
Thanks

The problem is because you have the <> in 2.6.28.11.  However, you should try going to System->Administration->Hardware Drivers and activate the Broadcom STA driver first.  It is the same thing, but without the compiling.

---

### Post by jonathanmotes on 2009-08-09
> **Ayuthia said:**
> I should not take very long and you should not need to change the permissions.

Is it getting stuck in the patch or in the compile?

It was getting stuck right from the beginning.

EDIT: I re-downloaded the file, now I'm getting this:
```
motes@laptop-04:~/Desktop$ patch -p1 < broadcom-sta.patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- src/wl/sys/wl_linux.c.orig	2009-04-23 21:16:26.637443671 +0400
|+++ src/wl/sys/wl_linux.c	2009-04-23 21:17:58.842687327 +0400
--------------------------
File to patch:
```

EDIT 2: a friend told me that I need to be in the same directory as the kernel source. I'm going to install the source .deb from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.4/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.4/) and see if I can find where it is extracted. Hopefully that will work....

EDIT 3: never mind, its looking for the driver code. It hangs when "patch" is ran on the file once its in the correct directory. What am I doing wrong?

Thanks!

---

### Post by Ayuthia on 2009-08-09
> **jonathanmotes said:**
> It was getting stuck right from the beginning.

EDIT: I re-downloaded the file, now I'm getting this:
```
motes@laptop-04:~/Desktop$ patch -p1 < broadcom-sta.patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- src/wl/sys/wl_linux.c.orig	2009-04-23 21:16:26.637443671 +0400
|+++ src/wl/sys/wl_linux.c	2009-04-23 21:17:58.842687327 +0400
--------------------------
File to patch:
```


You need to be in the directory where you extracted the Broadcom STA source.  You should be able to see the src directory.  The message that shows on the first line in your code section says that it cannot find the src directory.

---

### Post by jonathanmotes on 2009-08-10
> **Ayuthia said:**
> You need to be in the directory where you extracted the Broadcom STA source.  You should be able to see the src directory.  The message that shows on the first line in your code section says that it cannot find the src directory.

Yeah, I finally figured that out, but it hangs when I'm in the correct directory. I let it sit for several hours, but with no luck. There is no output to the console or anything. Maybe that kernel patch is for an older driver....

---

### Post by halalkebabhut on 2009-08-10
Hi,

I feel I'm nearly there with installing the driver for my BCM4312 on my Vostro 1520 running Ubuntu 9,04. I went through all the posted instructions without error but the wireless driver shows up on eth1 which I can;t seem to set up as wireless on my network tools.

I've tried connecting to my router using the terminal but this doesn't work though I was able to scan for other networks using iwlist scan. Also for all of my networking devices I get the error message "The interface does not exist" when I try to configure it though I'm happily connected to the internet through eth0.  So I'm confused. Could you help me please.

[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by Ayuthia on 2009-08-10
> **halalkebabhut said:**
> Hi,

I feel I'm nearly there with installing the driver for my BCM4312 on my Vostro 1520 running Ubuntu 9,04. I went through all the posted instructions without error but the wireless driver shows up on eth1 which I can;t seem to set up as wireless on my network tools.

I've tried connecting to my router using the terminal but this doesn't work though I was able to scan for other networks using iwlist scan. Also for all of my networking devices I get the error message "The interface does not exist" when I try to configure it though I'm happily connected to the internet through eth0.  So I'm confused. Could you help me please.

[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

Can you post the results of:
```
lsmod|grep -e b43 -e ssb -e wl
lshw -C network
```

It will help us see what your wireless is trying to use.

---

### Post by halalkebabhut on 2009-08-10
> **Ayuthia said:**
> Can you post the results of:
```
lsmod|grep -e b43 -e ssb -e wl
lshw -C network
```It will help us see what your wireless is trying to use.


lsmod|grep -e b43 -e ssb -e wl - gives...

```

wl                   1489748  0 
ieee80211_crypt        13568  2 ieee80211_crypt_tkip,wl

```lshw -C network gives ...

```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:c1:28:e5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.100 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth1
       version: 01
       serial: 00:26:5e:11:0b:2d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:6b:dc:3e:bf:2a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```many thanks

---

### Post by jonathanmotes on 2009-08-10
Ayuthia,

I think that the patch from [http://bugs.gentoo.org/248450](http://bugs.gentoo.org/248450) is only for an older version of the driver (5.10.79.10), while 5.10.91.9 is the version on Broadcom's site.

Could the version mismatch be causing patch to hang? (I did place the patch from Gentoo's site right above the src directory, so I know that I'm doing that part correctly...)

Thanks :)

---

### Post by Ayuthia on 2009-08-10
> **jonathanmotes said:**
> Yeah, I finally figured that out, but it hangs when I'm in the correct directory. I let it sit for several hours, but with no luck. There is no output to the console or anything. Maybe that kernel patch is for an older driver....
You are correct that it is for an older driver.  You should be able to correct it manually though.

Edit src/wl/sys/wl_linux.c:
```
gksu gedit src/wl/sys/wl_linux.c
```
and go to line 56 and you should see:
```
#if LINUX_VERSION_CODE >= KERNEL_VERSION(2, 6, 14)
#include <net/ieee80211.h>
#endif
```

Chnage those three lines to look like this:
```
#if LINUX_VERSION_CODE >= KERNEL_VERSION(2, 6, 29)
#include <net/lib80211.h>
#endif
#if LINUX_VERSION_CODE >= KERNEL_VERSION(2, 6, 30)
#include <linux/ieee80211.h>
#else
#if LINUX_VERSION_CODE >= KERNEL_VERSION(2, 6, 14)
#include <net/ieee80211.h>
#endif
#endif

```

Save the file and then try to compile again.

---

### Post by Ayuthia on 2009-08-10
> **halalkebabhut said:**
> lsmod|grep -e b43 -e ssb -e wl - gives...

```

wl                   1489748  0 
ieee80211_crypt        13568  2 ieee80211_crypt_tkip,wl

```lshw -C network gives ...

```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:c1:28:e5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.100 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth1
       version: 01
       serial: 00:26:5e:11:0b:2d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:6b:dc:3e:bf:2a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```many thanks

That information looks correct.

So if you do the following:
```
sudo ifconfig eth1 up
sudo iwlist scan
```
It does not report any wireless sites?

---

### Post by halalkebabhut on 2009-08-10
yes it shows 4 networks but none of them are mine - there should be about 20 possible wireless connections with mine as the strongest. I've tried connecting through the terminal using the code below but it seems unable to find my router.

sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "ESSID_IN_QUOTES"
sudo iwconfig eth1 key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

when I try and configure eth1 in network tools it says "the interface does not exist"  

when I click on the network manager icon on my panel i get

"Could not find information on interface 'eth1:avahi' in /proc/net/dev"

[IMG]http://ubuntuforums.org/images/icons/icon6.gif[/IMG]

---

### Post by Ayuthia on 2009-08-10
> **halalkebabhut said:**
> yes it shows 4 networks but none of them are mine - there should be about 20 possible wireless connections with mine as the strongest. I've tried connecting through the terminal using the code below but it seems unable to find my router.

sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "ESSID_IN_QUOTES"
sudo iwconfig eth1 key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

when I try and configure eth1 in network tools it says "the interface does not exist"  

when I click on the network manager icon on my panel i get

"Could not find information on interface 'eth1:avahi' in /proc/net/dev"

[IMG]http://ubuntuforums.org/images/icons/icon6.gif[/IMG]

The only other thing I can think of trying is to switch your router to only report g instead of mixed and see if it shows up.  You might also try turning off the encryption just to see if you can connect.

---

### Post by gwhamilton on 2009-08-10
> **Ayuthia said:**
> The problem is because you have the <> in 2.6.28.11.  However, you should try going to System->Administration->Hardware Drivers and activate the Broadcom STA driver first.  It is the same thing, but without the compiling.

Thanks Ayuthia, I went to the above location and no Broadcom drivers were found. I also tried the command without the "<>", still no luck although it took a little longer

ubuntu@ubuntu:~/hybrid_wl$ hybrid_wl$ hybrid_wl$ make -C /lib/modules/2.6.28.11/build M=`pwd`
bash: hybrid_wl$: command not found

Can you tell me my next step?
Thanks

---

### Post by Ayuthia on 2009-08-11
> **gwhamilton said:**
> Thanks Ayuthia, I went to the above location and no Broadcom drivers were found. I also tried the command without the "<>", still no luck although it took a little longer

ubuntu@ubuntu:~/hybrid_wl$ hybrid_wl$ hybrid_wl$ make -C /lib/modules/2.6.28.11/build M=`pwd`
bash: hybrid_wl$: command not found

Can you tell me my next step?
Thanks
Before we try the compile version, can you check /lib/modules/`uname -r`/volatile and see if there is a wl.ko file out there:
```
ls /lib/modules/`uname -r`/volatile
```
If there is, you should be able to do the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```

In response to your message, you have hybrid_wl$ show up three times.  It should not be there.  The command should be:
```
make -C /lib/modules/`uname -r`/build M=`pwd`
```

---

### Post by gwhamilton on 2009-08-11
> **Ayuthia said:**
> Before we try the compile version, can you check /lib/modules/`uname -r`/volatile and see if there is a wl.ko file out there:
```
ls /lib/modules/`uname -r`/volatile
```If there is, you should be able to do the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```In response to your message, you have hybrid_wl$ show up three times.  It should not be there.  The command should be:
```
make -C /lib/modules/`uname -r`/build M=`pwd`
```

Thanks for your help. I didn't have the wl.ko file. I took your advice and re-ran the code. I had some success. I then followed the original directions and came up with this along with your directions to others. I think progress is being made. 

ubuntu@ubuntu:~/hybrid_wl$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:11:43:3f:ec:19
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.10.2 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a2:93:c8:1a:eb:c8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
ubuntu@ubuntu:~/hybrid_wl$ 
 I had power to my network card before I did this and now the power is off.
Thanks,

---

### Post by Ayuthia on 2009-08-11
> **gwhamilton said:**
> 
  *-network UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       configuration: latency=64

You have a 4306 rev 03 card.  This card does not work with the Broadcom STA driver.  You need to be using the b43 option.  If you don't see that option in System->Administration->Hardware Drivers, you should install b43-fwcutter from Synaptic or from the Terminal:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```

---

### Post by gwhamilton on 2009-08-11
> **Ayuthia said:**
> You have a 4306 rev 03 card.  This card does not work with the Broadcom STA driver.  You need to be using the b43 option.  If you don't see that option in System->Administration->Hardware Drivers, you should install b43-fwcutter from Synaptic or from the Terminal:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```

Success !!!, well sort of. I followed the procedure and the driver loaded. I could not connect to my network. I run WPA-PSK security. I changed to an open system on my router and the wireless connection and I was able to connect to the wireless. I know the driver works now. Do you have any ideas if the wpa & wpa2 setting on the security tab will work with wpa-psk?
Thanks for all of your help!

---

### Post by Ayuthia on 2009-08-11
> **gwhamilton said:**
> Success !!!, well sort of. I followed the procedure and the driver loaded. I could not connect to my network. I run WPA-PSK security. I changed to an open system on my router and the wireless connection and I was able to connect to the wireless. I know the driver works now. Do you have any ideas if the wpa & wpa2 setting on the security tab will work with wpa-psk?
Thanks for all of your help!

As far as I know, it should work.  I had a Dell laptop with the 4306 rev 03 card and I thought that it worked.  Of course, I might have just used the manual method of connecting.

---

### Post by mattsticks on 2009-08-12
> **jonathanmotes said:**
> 

I think that the patch from [http://bugs.gentoo.org/248450](http://bugs.gentoo.org/248450) is only for an older version of the driver (5.10.79.10), while 5.10.91.9 is the version on Broadcom's site.

Could the version mismatch be causing patch to hang? (I did place the patch from Gentoo's site right above the src directory, so I know that I'm doing that part correctly...)



Hi Johathan,

I'm in the same boat and had been getting exactly the same errors as you. I've finally managed to get things working by following the steps on [http://jhabib.lebos.org/?p=3](http://jhabib.lebos.org/?p=3)

I followed the instructions to the letter, copying and pasting each command one by one, with the following exceptions:

1. I used the 2.6.30.4 kernel instead of 2.6.30
2. Replaced two instances of `uname -n` with `uname -r`.

The last additional step needed was to run:

```
sudo gedit /etc/rc.local
```and add the lines:

 ```
modprobe -r b43 ssb wl
modprobe wl
```Hope this helps.

Matt.

---

### Post by gwhamilton on 2009-08-12
> **Ayuthia said:**
> As far as I know, it should work. I had a Dell laptop with the 4306 rev 03 card and I thought that it worked. Of course, I might have just used the manual method of connecting.
I really appreciate the help. I must have a security issue that's keeping me from connecting with wpa security. I am getting prompted for a network password but no connection yet. Thanks again.

---

### Post by Ayuthia on 2009-08-12
> **gwhamilton said:**
> I really appreciate the help. I must have a security issue that's keeping me from connecting with wpa security. I am getting prompted for a network password but no connection yet. Thanks again.

You might try using wpa_supplicant from the Terminal:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by halalkebabhut on 2009-08-14
> **Ayuthia said:**
> The only other thing I can think of trying is to switch your router to only report g instead of mixed and see if it shows up.  You might also try turning off the encryption just to see if you can connect.

I finally solved this - nothing wrong with the drivers at all ! Just needed to run sudo apt-get install network-manager to get the proper network manager running (wasn't in my version of ubuntu studio ... hmmm)

then did

sudo gedit /etc/NetworkManager/nm-system-settings.conf
and change settings managed from false to true

then 

sudo killall nm-system-settings
and bingo wireless works like a dream ! 

oh yeah and changed the channel on my router (but not sure if that had much to do with it)

thanks for your help

---

### Post by n00bz on 2009-09-13
all is well except for step 4

john@mobius:~$ make -C /lib/modules/2.6.30.5-ep0/build M=`pwd` clean
make: *** /lib/modules/2.6.30.5-ep0/build: No such file or directory.  Stop.

any help is greatly appreciated

---

### Post by Ayuthia on 2009-09-13
> **n00bz said:**
> all is well except for step 4

john@mobius:~$ make -C /lib/modules/2.6.30.5-ep0/build M=`pwd` clean
make: *** /lib/modules/2.6.30.5-ep0/build: No such file or directory.  Stop.

any help is greatly appreciated

I am guessing that this is the first time that you are trying to compile this source.  If that is the case, this message is normal.  This command is supposed to clean out all the directories if the source has been compiled before.  In this case, it has not been compiled before so the build directory has not been created.

You should be able to go ahead and go to the next step and compile (it is the same command as step 4 but without the clean at the end).  It has been a while since I have compiled the source and I am not for sure if 2.6.30.5 will compile without a patch.

---

### Post by n00bz on 2009-09-13
> **Ayuthia said:**
> I am guessing that this is the first time that you are trying to compile this source.  If that is the case, this message is normal.  This command is supposed to clean out all the directories if the source has been compiled before.  In this case, it has not been compiled before so the build directory has not been created.

You should be able to go ahead and go to the next step and compile (it is the same command as step 4 but without the clean at the end).  It has been a while since I have compiled the source and I am not for sure if 2.6.30.5 will compile without a patch.

hey thanks for the reply, anyways 

i typed

john@mobius:~$ john@mobius:~$ make -C /lib/modules/2.6.30.5-ep0/build M=`pwd`
bash: john@mobius:~$: command not found


no luck yet

---

### Post by Ayuthia on 2009-09-13
> **n00bz said:**
> hey thanks for the reply, anyways 

i typed

john@mobius:~$ make -C /lib/modules/2.6.30.5-ep0//build M=`pwd`
make: *** /lib/modules/2.6.30.5-ep0//build: No such file or directory.  Stop.

no luck yet

It looks like it is because you have 2 / after 2.6.30.5-ep0 when you should only need one.  You might try the following:
```
make -C /lib/modules/2.6.30.5-ep0/build M=`pwd`
```
If it still says that it cannot find the build directory, then it means that you are either missing the linux header files or else the build link was not created.

---

### Post by n00bz on 2009-09-13
> **Ayuthia said:**
> It looks like it is because you have 2 / after 2.6.30.5-ep0 when you should only need one.  You might try the following:
```
make -C /lib/modules/2.6.30.5-ep0/build M=`pwd`
```If it still says that it cannot find the build directory, then it means that you are either missing the linux header files or else the build link was not created.

john@mobius:~$ make -C /lib/modules/2.6.30.5-ep0/build M=`pwd`
make: *** /lib/modules/2.6.30.5-ep0/build: No such file or directory.  Stop.

i must be missing something, how do i get that stuff?

---

### Post by Ayuthia on 2009-09-13
I just saw your edited post.  It looks like the build symbolic link is not there.  If you compiled a custom kernel, then you need to check and see if /lib/modules/2.6.30-ep0/build does exist.  If it does not, you will need to check and see if /usr/src/linux-2.6.30-ep0 exists.  If it does, you will need to do the following:
```
cd /lib/modules/2.6.30-ep0
sudo ln -s /usr/src/linux-2.6.30-ep0 build
```
That will create the symbolic link to point build over to the linux header files.

---

### Post by n00bz on 2009-09-13
> **Ayuthia said:**
> I just saw your edited post.  It looks like the build symbolic link is not there.  If you compiled a custom kernel, then you need to check and see if /lib/modules/2.6.30-ep0/build does exist.  If it does not, you will need to check and see if /usr/src/linux-2.6.30-ep0 exists.  If it does, you will need to do the following:
```
cd /lib/modules/2.6.30-ep0

```That will create the symbolic link to point build over to the linux header files.

ok....ummm i know that /lib/modules/2.6.30-ep0/build does not 
i also did check /usr/src/linux-2.6.30-ep0  by simply typing it onto  my terminal and it said

root@mobius:/home/john# cd /lib/modules/2.6.30-ep0
bash: cd: /lib/modules/2.6.30-ep0: No such file or directory

=S  but out of curiousity i typed in sudo ln -s /usr/src/linux-2.6.30-ep0 build

root@mobius:/home/john# sudo ln -s /usr/src/linux-2.6.30-ep0 build
ln: creating symbolic link `build': File exists

i'm going to level with you, i have no no clue about whats going on right now. i'm the noobest you'll ever come acros      thanks for your help

---

### Post by Ayuthia on 2009-09-13
> **n00bz said:**
> ok....ummm i know that /lib/modules/2.6.30-ep0/build does not 
i also did check /usr/src/linux-2.6.30-ep0  by simply typing it onto  my terminal and it said

root@mobius:/home/john# cd /lib/modules/2.6.30-ep0
bash: cd: /lib/modules/2.6.30-ep0: No such file or directory

=S  but out of curiousity i typed in sudo ln -s /usr/src/linux-2.6.30-ep0 build

root@mobius:/home/john# sudo ln -s /usr/src/linux-2.6.30-ep0 build
ln: creating symbolic link `build': File exists

i'm going to level with you, i have no no clue about whats going on right now. i'm the noobest you'll ever come acros      thanks for your help
I forgot that you are using the 2.6.30.5 kernel.  You need to change 2.6.30-ep0 to 2.6.30.5-ep0.  Sorry about that.

So we just need to make sure that the build link is pointing over to /usr/src/linux-2.6.30.5-ep0.  You can verify that by typing:
```
ls -l /lib/modules/2.6.30.5-ep0/build
```

If you are already running in this kernel you can also do the following:
```
ls -l /lib/modules/`uname -r`/build
```The uname -r command provides the current kernel version so that you don't have to type or remember your kernel version.

---

### Post by n00bz on 2009-09-13
> **Ayuthia said:**
> I forgot that you are using the 2.6.30.5 kernel.  You need to change 2.6.30-ep0 to 2.6.30.5-ep0.  Sorry about that.

So we just need to make sure that the build link is pointing over to /usr/src/linux-2.6.30.5-ep0.  You can verify that by typing:
```
ls -l /lib/modules/2.6.30.5-ep0/build
```If you are already running in this kernel you can also do the following:
```
ls -l /lib/modules/`uname -r`/build
```The uname -r command provides the current kernel version so that you don't have to type or remember your kernel version.

its alright, thanks for your help 
um i typed it in and

john@mobius:~$ ls -l /lib/modules/2.6.30.5-ep0/build
ls: cannot access /lib/modules/2.6.30.5-ep0/build: No such file or directory

---

### Post by Ayuthia on 2009-09-13
> **n00bz said:**
> its alright, thanks for your help 
um i typed it in and

john@mobius:~$ ls -l /lib/modules/2.6.30.5-ep0/build
ls: cannot access /lib/modules/2.6.30.5-ep0/build: No such file or directory

Ok.  Just to be sure that it is the correct directory, check and see if /lib/modules/2.6.30.5-ep0 exists:
```
ls /lib/modules/2.6.30.5-ep0
```
If it does exist, check:
```
ls /usr/src/linux-2.6.30.5-ep0
```
If they both exist:
```
cd /lib/modules/2.6.30.5-ep0
sudo ln -s /usr/src/linux-2.6.30.5-ep0 build
```
And then you can go back and try to compile again.

---

### Post by n00bz on 2009-09-13
> **Ayuthia said:**
> Ok.  Just to be sure that it is the correct directory, check and see if /lib/modules/2.6.30.5-ep0 exists:
```
ls /lib/modules/2.6.30.5-ep0
```If it does exist, check:
```
ls /usr/src/linux-2.6.30.5-ep0
```If they both exist:
```
cd /lib/modules/2.6.30.5-ep0
sudo ln -s /usr/src/linux-2.6.30.5-ep0 build
```And then you can go back and try to compile again.

```
john@mobius:~$ ls /lib/modules/2.6.30.5-ep0
kernel             modules.ccwmap   modules.ieee1394map  modules.ofmap   modules.seriomap     modules.usbmap
modules.alias      modules.dep      modules.inputmap     modules.order   modules.symbols
modules.alias.bin  modules.dep.bin  modules.isapnpmap    modules.pcimap  modules.symbols.bin
```

```
john@mobius:~$ ls /usr/src/linux-2.6.30.5-ep0
ls: cannot access /usr/src/linux-2.6.30.5-ep0: No such file or directory
```

```
john@mobius:~$ cd /lib/modules/2.6.30.5-ep0
john@mobius:/lib/modules/2.6.30.5-ep0$ sudo ln -s /usr/src/linux-2.6.30.5-ep0 build
[sudo] password for john: 
john@mobius:/lib/modules/2.6.30.5-ep0$ make -C /lib/modules/2.6.30.5-ep0/build M=`pwd`
make: *** /lib/modules/2.6.30.5-ep0/build: No such file or directory.  Stop.
```

man this is frustrating, sooo lib/modules, does not exists, how do i make it so that it is so?

---

### Post by Ayuthia on 2009-09-13
> **n00bz said:**
> 

```
john@mobius:~$ ls /usr/src/linux-2.6.30.5-ep0
ls: cannot access /usr/src/linux-2.6.30.5-ep0: No such file or directory
```

```
john@mobius:~$ cd /lib/modules/2.6.30.5-ep0
john@mobius:/lib/modules/2.6.30.5-ep0$ sudo ln -s /usr/src/linux-2.6.30.5-ep0 build
[sudo] password for john: 
john@mobius:/lib/modules/2.6.30.5-ep0$ make -C /lib/modules/2.6.30.5-ep0/build M=`pwd`
make: *** /lib/modules/2.6.30.5-ep0/build: No such file or directory.  Stop.
```

man this is frustrating, sooo lib/modules, does not exists, how do i make it so that it is so?
The problem is that /usr/src/linux-2.6.30.5-ep0 does not exist.  Since it is not there, then the build link is not going to work.

How did you get the linux-2.6.30.5-ep0 kernel?  If you compiled it on your own, where did you compile it?  If you just downloaded the kernel and installed it, do you know if they supply header files (something like linux-2.6.30.5-ep0-headers?

Can you supply the result of:
```
ls /usr/src
```It might be possible that the linux-2.6.30.5-ep0 directory might be labeled differently.

---

### Post by kevdog on 2009-09-13
Sorry for butting in on the current conversation, but the build symbolic link located within:

/lib/modules/`uname -r` 

should be symbolically linked to:
/usr/src/linux-headers-`uname -r`

So what I would do would be within /lib/modules/`uname -r`

ln -s /usr/src/linux-headers-`uname -r` build

Then can you do a ls -la
and tell me where the build directory points to?

---

### Post by n00bz on 2009-09-14
> **Ayuthia said:**
> The problem is that /usr/src/linux-2.6.30.5-ep0 does not exist.  Since it is not there, then the build link is not going to work.

How did you get the linux-2.6.30.5-ep0 kernel?  If you compiled it on your own, where did you compile it?  If you just downloaded the kernel and installed it, do you know if they supply header files (something like linux-2.6.30.5-ep0-headers?

Can you supply the result of:
```
ls /usr/src
```It might be possible that the linux-2.6.30.5-ep0 directory might be labeled differently.

yea sure umm its  

```
john@mobius:/lib/modules/2.6.30.5-ep0$ ls /usr/src
linux-headers-2.6.30.5-ep0

```

---

### Post by n00bz on 2009-09-14
> **kevdog said:**
> Sorry for butting in on the current conversation, but the build symbolic link located within:

/lib/modules/`uname -r` 

should be symbolically linked to:
/usr/src/linux-headers-`uname -r`

So what I would do would be within /lib/modules/`uname -r`

ln -s /usr/src/linux-headers-`uname -r` build

Then can you do a ls -la
and tell me where the build directory points to?

ahh ok errr i typed it in 

```
john@mobius:/lib/modules/2.6.30.5-ep0$ ln -s /usr/src/linux-headers-`uname -r` build
ln: creating symbolic link `build': File exists

```

i got that and then i typed this and got
```

john@mobius:/lib/modules/2.6.30.5-ep0$  ls -la
total 2360
drwxr-xr-x  3 root root   4096 2009-09-13 23:16 .
drwxr-xr-x  3 root root   4096 2009-08-29 12:43 ..
lrwxrwxrwx  1 root root     27 2009-09-13 23:16 build -> /usr/src/linux-2.6.30.5-ep0
drwxr-xr-x 10 root root   4096 2009-08-29 12:08 kernel
-rw-r--r--  1 root root 374128 2009-08-29 12:08 modules.alias
-rw-r--r--  1 root root 371071 2009-08-29 12:08 modules.alias.bin
-rw-r--r--  1 root root     69 2009-08-29 12:08 modules.ccwmap
-rw-r--r--  1 root root 143202 2009-08-29 12:08 modules.dep
-rw-r--r--  1 root root 218348 2009-08-29 12:08 modules.dep.bin
-rw-r--r--  1 root root   1331 2009-08-29 12:08 modules.ieee1394map
-rw-r--r--  1 root root    218 2009-08-29 12:08 modules.inputmap
-rw-r--r--  1 root root   1236 2009-08-29 12:08 modules.isapnpmap
-rw-r--r--  1 root root     74 2009-08-29 12:08 modules.ofmap
-rw-r--r--  1 root root  62150 2009-08-27 13:48 modules.order
-rw-r--r--  1 root root 169905 2009-08-29 12:08 modules.pcimap
-rw-r--r--  1 root root   1387 2009-08-29 12:08 modules.seriomap
-rw-r--r--  1 root root 152949 2009-08-29 12:08 modules.symbols
-rw-r--r--  1 root root 197274 2009-08-29 12:08 modules.symbols.bin
-rw-r--r--  1 root root 668803 2009-08-29 12:08 modules.usbmap
john@mobius:/lib/modules/2.6.30.5-ep0$ 
```

thanks any help is greatly appreciated

---

### Post by Ayuthia on 2009-09-14
> **n00bz said:**
> ahh ok errr i typed it in 

```
john@mobius:/lib/modules/2.6.30.5-ep0$ ln -s /usr/src/linux-headers-`uname -r` build
ln: creating symbolic link `build': File exists

```

i got that and then i typed this and got
```

john@mobius:/lib/modules/2.6.30.5-ep0$  ls -la
total 2360
drwxr-xr-x  3 root root   4096 2009-09-13 23:16 .
drwxr-xr-x  3 root root   4096 2009-08-29 12:43 ..
lrwxrwxrwx  1 root root     27 2009-09-13 23:16 build -> /usr/src/linux-2.6.30.5-ep0
drwxr-xr-x 10 root root   4096 2009-08-29 12:08 kernel
-rw-r--r--  1 root root 374128 2009-08-29 12:08 modules.alias
-rw-r--r--  1 root root 371071 2009-08-29 12:08 modules.alias.bin
-rw-r--r--  1 root root     69 2009-08-29 12:08 modules.ccwmap
-rw-r--r--  1 root root 143202 2009-08-29 12:08 modules.dep
-rw-r--r--  1 root root 218348 2009-08-29 12:08 modules.dep.bin
-rw-r--r--  1 root root   1331 2009-08-29 12:08 modules.ieee1394map
-rw-r--r--  1 root root    218 2009-08-29 12:08 modules.inputmap
-rw-r--r--  1 root root   1236 2009-08-29 12:08 modules.isapnpmap
-rw-r--r--  1 root root     74 2009-08-29 12:08 modules.ofmap
-rw-r--r--  1 root root  62150 2009-08-27 13:48 modules.order
-rw-r--r--  1 root root 169905 2009-08-29 12:08 modules.pcimap
-rw-r--r--  1 root root   1387 2009-08-29 12:08 modules.seriomap
-rw-r--r--  1 root root 152949 2009-08-29 12:08 modules.symbols
-rw-r--r--  1 root root 197274 2009-08-29 12:08 modules.symbols.bin
-rw-r--r--  1 root root 668803 2009-08-29 12:08 modules.usbmap
john@mobius:/lib/modules/2.6.30.5-ep0$ 
```

thanks any help is greatly appreciated

We will need to remove the build file and relink it:
```
cd /lib/modules/`uname -r`
sudo rm build
sudo ln -s /usr/src/linux-headers-`uname -r` build
```
That should solve your problem.

I am a Gentoo user and tend to build my kernels. They don't have the linux-headers prefix.  I keep forgetting to switch my mind back the the Ubuntu standards.

---

### Post by kevdog on 2009-09-14
Ayuthia

Had no idea you used Gentoo -- learn something everyday!!

---

### Post by n00bz on 2009-09-14
> **Ayuthia said:**
> We will need to remove the build file and relink it:
```
cd /lib/modules/`uname -r`
sudo rm build
sudo ln -s /usr/src/linux-headers-`uname -r` build
```That should solve your problem.

I am a Gentoo user and tend to build my kernels. They don't have the linux-headers prefix.  I keep forgetting to switch my mind back the the Ubuntu standards.

really? thats it lol =D i'm sooo happy my face actually looks like that, 
but umm one question err do i start all over again from the first page? from the first step ( redownload that file)  all the way down?

---

### Post by Ayuthia on 2009-09-14
> **kevdog said:**
> Ayuthia

Had no idea you used Gentoo -- learn something everyday!!

It's funny.  I was using Arch for a while and life was good.  I then started developing again and missed Gentoo so I started using it again and have been very happy with it.  I might try using slackware sometime, but I am not for sure if I am going to like it or not since it likes the keep it simple method.  It does not sound like things break too often...

n00bz, my hope is that the link will now get you to be able to start compiling the kernel module again.  However, if you have not patched the Broadcom STA source, it will most likely crash during compile.  Here is a link that might help you through that problem:
[http://www.void.gr/kargig/blog/2009/07/18/trying-to-achieve-a-more-stable-hybrid-broadcom-wl-kernel-module-for-broadcom-4328/](http://www.void.gr/kargig/blog/2009/07/18/trying-to-achieve-a-more-stable-hybrid-broadcom-wl-kernel-module-for-broadcom-4328/)

The person who wrote it is using four different patches.  The 2.6.30 patch 2 file is something that you will need. The hidden-essid one is handy if you are using a hidden essid.  The other two I am not sure about.  You might be able to get a clean compile with just those two files.  I would not use the last one if you are using a 64 bit version though since it is listed as a 32-bit patch.  I am guessing that it is labeled like that because the author is using a 32-bit version, but I am not sure if it was tested on a 64-bit kernel.

---

### Post by Ayuthia on 2009-09-14
> **n00bz said:**
> really? thats it lol =D i'm sooo happy my face actually looks like that, 
but umm one question err do i start all over again from the first page? from the first step ( redownload that file)  all the way down?

You just need to continue at this point:
```
make -C /lib/modules/2.6.30.5-ep0/build M=`pwd`
```

---

### Post by n00bz on 2009-09-14
> **Ayuthia said:**
> It's funny.  I was using Arch for a while and life was good.  I then started developing again and missed Gentoo so I started using it again and have been very happy with it.  I might try using slackware sometime, but I am not for sure if I am going to like it or not since it likes the keep it simple method.  It does not sound like things break too often...

n00bz, my hope is that the link will now get you to be able to start compiling the kernel module again.  However, if you have not patched the Broadcom STA source, it will most likely crash during compile.  Here is a link that might help you through that problem:
[http://www.void.gr/kargig/blog/2009/07/18/trying-to-achieve-a-more-stable-hybrid-broadcom-wl-kernel-module-for-broadcom-4328/](http://www.void.gr/kargig/blog/2009/07/18/trying-to-achieve-a-more-stable-hybrid-broadcom-wl-kernel-module-for-broadcom-4328/)

The person who wrote it is using four different patches.  The 2.6.30 patch 2 file is something that you will need. The hidden-essid one is handy if you are using a hidden essid.  The other two I am not sure about.  You might be able to get a clean compile with just those two files.  I would not use the last one if you are using a 64 bit version though since it is listed as a 32-bit patch.  I am guessing that it is labeled like that because the author is using a 32-bit version, but I am not sure if it was tested on a 64-bit kernel.

hey i think everything went ok i finnaly got to do the make -C /lib/modules/2.6.30.5-ep0/build M=`pwd`

and this came out
 ```
john@mobius:~/wdriver$  make -C /lib/modules/2.6.30.5-ep0/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.30.5-ep0'
  LD      /home/john/wdriver/built-in.o
  CC [M]  /home/john/wdriver/src/wl/sys/wl_linux.o
/home/john/wdriver/src/wl/sys/wl_linux.c:57:27: error: net/ieee80211.h: No such file or directory
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_attach’:
/home/john/wdriver/src/wl/sys/wl_linux.c:362: error: implicit declaration of function ‘ieee80211_get_crypto_ops’
/home/john/wdriver/src/wl/sys/wl_linux.c:362: warning: assignment makes pointer from integer without a cast
/home/john/wdriver/src/wl/sys/wl_linux.c:365: warning: assignment makes pointer from integer without a cast
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_free’:
/home/john/wdriver/src/wl/sys/wl_linux.c:634: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c:669: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c:685: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:689: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_open’:
/home/john/wdriver/src/wl/sys/wl_linux.c:714: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_close’:
/home/john/wdriver/src/wl/sys/wl_linux.c:742: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_start’:
/home/john/wdriver/src/wl/sys/wl_linux.c:765: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_alloc_if’:
/home/john/wdriver/src/wl/sys/wl_linux.c:850: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_get_driver_info’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1030: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_ioctl’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1118: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c:1119: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_get_stats’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1204: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_get_wireless_stats’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1236: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c:1237: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_set_mac_address’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1304: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c:1312: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘_wl_set_multicast_list’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1335: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_tkip_miccheck’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1726: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1729: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_tkip_micadd’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1748: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_tkip_encrypt’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1768: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_tkip_decrypt’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1790: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1792: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_tkip_keyset’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1834: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1844: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1851: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1861: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1871: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1878: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_tkip_printstats’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1897: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1899: error: dereferencing pointer to incomplete type
make[1]: *** [/home/john/wdriver/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/home/john/wdriver] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.30.5-ep0'
```

after that i did this 
sudo modprobe ieee80211_crypt_tkipand this came out 
```
john@mobius:~/wdriver$ sudo modprobe ieee80211_crypt_tkip
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module ieee80211_crypt_tkip not found.
```

any ideas?

---

### Post by Ayuthia on 2009-09-14
> **n00bz said:**
> hey i think everything went ok i finnaly got to do the make -C /lib/modules/2.6.30.5-ep0/build M=`pwd`

and this came out
 ```
john@mobius:~/wdriver$  make -C /lib/modules/2.6.30.5-ep0/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.30.5-ep0'
  LD      /home/john/wdriver/built-in.o
  CC [M]  /home/john/wdriver/src/wl/sys/wl_linux.o
/home/john/wdriver/src/wl/sys/wl_linux.c:57:27: error: net/ieee80211.h: No such file or directory
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_attach’:
/home/john/wdriver/src/wl/sys/wl_linux.c:362: error: implicit declaration of function ‘ieee80211_get_crypto_ops’
/home/john/wdriver/src/wl/sys/wl_linux.c:362: warning: assignment makes pointer from integer without a cast
/home/john/wdriver/src/wl/sys/wl_linux.c:365: warning: assignment makes pointer from integer without a cast
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_free’:
/home/john/wdriver/src/wl/sys/wl_linux.c:634: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c:669: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c:685: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:689: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_open’:
/home/john/wdriver/src/wl/sys/wl_linux.c:714: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_close’:
/home/john/wdriver/src/wl/sys/wl_linux.c:742: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_start’:
/home/john/wdriver/src/wl/sys/wl_linux.c:765: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_alloc_if’:
/home/john/wdriver/src/wl/sys/wl_linux.c:850: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_get_driver_info’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1030: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_ioctl’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1118: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c:1119: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_get_stats’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1204: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_get_wireless_stats’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1236: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c:1237: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_set_mac_address’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1304: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c:1312: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘_wl_set_multicast_list’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1335: error: ‘struct net_device’ has no member named ‘priv’
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_tkip_miccheck’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1726: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1729: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_tkip_micadd’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1748: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_tkip_encrypt’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1768: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_tkip_decrypt’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1790: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1792: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_tkip_keyset’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1834: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1844: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1851: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1861: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1871: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1878: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c: In function ‘wl_tkip_printstats’:
/home/john/wdriver/src/wl/sys/wl_linux.c:1897: error: dereferencing pointer to incomplete type
/home/john/wdriver/src/wl/sys/wl_linux.c:1899: error: dereferencing pointer to incomplete type
make[1]: *** [/home/john/wdriver/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/home/john/wdriver] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.30.5-ep0'
```


If you look at my previous [post]("http://ubuntuforums.org/showpost.php?p=7945591&postcount=177"), I provided a link that has some patches that will help.  The error message should be able to be fixed by using the 2.6.30 patch 2 patch that the author mentions.  For some reason the ieee80211.h file keeps changing names.

---

### Post by n00bz on 2009-09-14
> **Ayuthia said:**
> If you look at my previous [post]("http://ubuntuforums.org/showpost.php?p=7945591&postcount=177"), I provided a link that has some patches that will help.  The error message should be able to be fixed by using the 2.6.30 patch 2 patch that the author mentions.  For some reason the ieee80211.h file keeps changing names.

ohh yea sorry about that,  
ummm so i followed thier instructions and got up to the part where you start patching. 

```
root@mobius:/home/john/hybrid_wl# patch -p0 < hidden-essid.patch
The program 'patch' is currently not installed.  You can install it by typing:
apt-get install patch
bash: patch: command not found
```i tried to install but got me nowhere

i'm soo sorry for asking for so much help, i really would pay you if i could meet you. thanks again

---

### Post by Ayuthia on 2009-09-14
The hidden-essid patch will help if you have your router hidden.  The patch that you need is this [one]("http://aur.archlinux.org/packages/broadcom-wl/broadcom-wl/broadcom-sta-5.10.91.9-linux-2.6.30-2.patch").  You can patch it by doing the following:
```
patch -p1 < broadcom-sta-5.10.91.9-linux-2.6.30-2.patch
```
If it does not produce any error messages, you can then try to compile again.  If you still have error messages, please post the messages and we can see if we can fix those.

---

### Post by n00bz on 2009-09-14
> **Ayuthia said:**
> If you look at my previous [post]("http://ubuntuforums.org/showpost.php?p=7945591&postcount=177"), I provided a link that has some patches that will help.  The error message should be able to be fixed by using the 2.6.30 patch 2 patch that the author mentions.  For some reason the ieee80211.h file keeps changing names.

ha  ohhh ic, sorry about that, i was in a rush last night fully dident see that, ok well i folled the link did mostly everything, still there seems to be trouble wil un-taring  check it out. 
```
john@mobius:/lib/modules/2.6.30.5-ep0/hybrid_wl$ tar -xzf /hybrid-portsrc-x86_32-v5_10_91_9.tar.gz

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors

```
followed everything up to that point, i dident think it was such a big problem, becuase i think untaring is like extracting right? well i went to the next step and got no where -.-"  i started the next step check it out 
```
 john@mobius:/lib/modules/2.6.30.5-ep0/hybrid_wl$ patch -p0 < hidden-essid.patch
The program 'patch' is currently not installed.  You can install it by typing:
sudo apt-get install patch
bash: patch: command not found
john@mobius:/lib/modules/2.6.30.5-ep0/hybrid_wl$ patching file src/wl/sys/wl_iw.c

```

what gives?

---

### Post by n00bz on 2009-09-14
> **Ayuthia said:**
> The hidden-essid patch will help if you have your router hidden.  The patch that you need is this [one]("http://aur.archlinux.org/packages/broadcom-wl/broadcom-wl/broadcom-sta-5.10.91.9-linux-2.6.30-2.patch").  You can patch it by doing the following:
```
patch -p1 < broadcom-sta-5.10.91.9-linux-2.6.30-2.patch
```If it does not produce any error messages, you can then try to compile again.  If you still have error messages, please post the messages and we can see if we can fix those.

ohh ha dident see this one either, so ```
john@mobius:/lib/modules/2.6.30.5-ep0/hybrid_wl$ patch -p1 < broadcom-sta-5.10.91.9-linux-2.6.30-2.patch
The program 'patch' is currently not installed.  You can install it by typing:
sudo apt-get install patch
bash: patch: command not found


``` this means that i cant go forward or can i?  i tried to install  'patch'
```
 john@mobius:/lib/modules/2.6.30.5-ep0/hybrid_wl$ sudo ap-get install patch
sudo: ap-get: command not found
john@mobius:/lib/modules/2.6.30.5-ep0/hybrid_wl$ sudo apt-get install patch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  diff-doc
The following NEW packages will be installed:
  patch
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 100kB of archives.
After this operation, 213kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com jaunty/main patch 2.5.9-5 [100kB]
Fetched 100kB in 0s (116kB/s)
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Selecting previously deselected package patch.
(Reading database ... 102689 files and directories currently installed.)
Unpacking patch (from .../patch_2.5.9-5_i386.deb) ...
Processing triggers for man-db ...
Setting up patch (2.5.9-5) ...
E: Directory '/var/log/apt/' missing

```   turns out i dont have that directory =( how should i go about making it so that it does exists

again any help is greatly appreciated

---

### Post by Ayuthia on 2009-09-14
> **n00bz said:**
> ohh ha dident see this one either, so ```
john@mobius:/lib/modules/2.6.30.5-ep0/hybrid_wl$ patch -p1 < broadcom-sta-5.10.91.9-linux-2.6.30-2.patch
The program 'patch' is currently not installed.  You can install it by typing:
sudo apt-get install patch
bash: patch: command not found


``` this means that i cant go forward or can i?  i tried to install  'patch'
```
 john@mobius:/lib/modules/2.6.30.5-ep0/hybrid_wl$ sudo ap-get install patch
sudo: ap-get: command not found
john@mobius:/lib/modules/2.6.30.5-ep0/hybrid_wl$ sudo apt-get install patch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  diff-doc
The following NEW packages will be installed:
  patch
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 100kB of archives.
After this operation, 213kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com jaunty/main patch 2.5.9-5 [100kB]
Fetched 100kB in 0s (116kB/s)
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Selecting previously deselected package patch.
(Reading database ... 102689 files and directories currently installed.)
Unpacking patch (from .../patch_2.5.9-5_i386.deb) ...
Processing triggers for man-db ...
Setting up patch (2.5.9-5) ...
E: Directory '/var/log/apt/' missing

```   turns out i dont have that directory =( how should i go about making it so that it does exists

again any help is greatly appreciated

I am not for sure about this one.  It would be better to create another thread to get this issue resolved and then come back to this one.  That will get you some better results for that problem.

---

### Post by n00bz on 2009-09-14
> **Ayuthia said:**
> I am not for sure about this one.  It would be better to create another thread to get this issue resolved and then come back to this one.  That will get you some better results for that problem.

=p its ok 
alright

---

### Post by n00bz on 2009-09-14
> **Ayuthia said:**
> The problem is that /usr/src/linux-2.6.30.5-ep0 does not exist.  Since it is not there, then the build link is not going to work.

How did you get the linux-2.6.30.5-ep0 kernel?  If you compiled it on your own, where did you compile it?  If you just downloaded the kernel and installed it, do you know if they supply header files (something like linux-2.6.30.5-ep0-headers?

Can you supply the result of:
```
ls /usr/src
```It might be possible that the linux-2.6.30.5-ep0 directory might be labeled differently.

i think i migh thave overlooked something. can you tell me the code to see my network bit? i want to check to see if i am indeed a 32 bit- or a 64 bit user

---

### Post by Ayuthia on 2009-09-14
> **n00bz said:**
> i think i migh thave overlooked something. can you tell me the code to see my network bit? i want to check to see if i am indeed a 32 bit- or a 64 bit user
uname -m should give you that information.  It will be x86_64 if it is 64-bit.

---

### Post by n00bz on 2009-09-14
> **Ayuthia said:**
> uname -m should give you that information.  It will be x86_64 if it is 64-bit.

wait the hell i got 

john@mobius:~/wdrives$ uname -m
i686 

whats that mean?

---

### Post by Ayuthia on 2009-09-14
> **n00bz said:**
> wait the hell i got 

john@mobius:~/wdrives$ uname -m
i686 

whats that mean?
It means that you have a 32 bit machine.  The 64-bit versions are x86_64 and ia64 and the 32-bit versions are i386, i486, i586, i686.

---

### Post by n00bz on 2009-09-15
> **Ayuthia said:**
> It means that you have a 32 bit machine.  The 64-bit versions are x86_64 and ia64 and the 32-bit versions are i386, i486, i586, i686.

-.-" i'm an idiot....gahh back to the first step

---

### Post by A_Fiachra on 2009-09-21
> **mike_l said:**
> After searching for ways to get wireless working on my HP dv9000, I came across [this thread.]("http://ubuntuforums.org/showthread.php?t=850913") Apparently, Broadcom offers linux drivers for it's 802.11a/b/g/n cards (chipsets BCM4311, BCM4312, BCM4321, and BCM4322, in both 32 and 64 bit).

Figuring that there are other people out there with the same problem: here's the steps I took to install the native drivers:

[LIST=1]
[*]**Download the appropriate driver**
I downloaded the 64 bit version of the driver from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
It's important that you get the correct version, as the 32 and 64 bit versions are not compatible.
[*]**Make the .ko file**
First, make a temporary directory 
```
mkdir wdriver 

```... and place the downloaded package into it (hybrid-portsrc-_64_5_10_27_6.tar.gz, or hybrid-portsrc-x86_32_5_10_27_6.tar.gz for the 32 bit version)
Then 'cd' into the temporary directory and un-tar the file. 
```
cd wdriver
tar -xzf hybrid-portsrc-x86_64_5_10_27_6.tar.gz 

```Now, we want to make the wl.ko file, so we enter: 
(<2.6.xx.xx> is your kernel version: mine was "2.6.24-19-generic". Use tab-completion to find yours.)
```
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`

```You should now have a file "wl.ko" located in the temporary directory you created (wdriver).
[*]**Make sure that no other wireless drivers are installed**
Enter: (Don't worry if there are any errors returned)
```
sudo rmmod bcm43xx
sudo rmmod b43
sudo rmmod b43legacy

```I also uninstalled ndiswrapper, just to be sure:
```
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-common 

```
[*]**Test the new wireless driver**
Now, lets test out our new wireless driver. Enter:
```
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko 

```If it worked, and you can see/connect to wireless networks, you'll want to:
[*]**Make your changes permanent.**
First, you may want to blacklist the old b43/b43legacy/bcm43xx drivers. Enter:
```
sudo gedit /etc/modprobe.d/blacklist
```and add the following to the end of the file:
```
blacklist b43
blacklist b43legacy
blacklist bcm43xx
```Now, let's move the wireless driver somewhere more permenant:
```
sudo mkdir /lib/modules/<2.6.xx.xx>/wlan
sudo mv wl.ko /lib/modules/<2.6.xx.xx>/wlan
```Now, lets make it so that the driver and wireless encryption module are loaded on startup. Enter:
```

sudo gedit /etc/modules

```and add
```
ieee80211_crypt_tkip
```to the bottom.

Now run:
```
sudo gedit /etc/rc.local
```and add
```
sudo insmod /lib/modules/<2.6.xx.xx>/wlan/wl.ko

```at the end of the file, but before the line "exit 0"

That's it. If I've made any errors, please let me know. Thanks.
[/LIST]



I've been following this thread with interest, since I have a wireless problem with the same card.

when I run make, I get:
```

 make -C /lib/modules/`uname -r`/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  LD      /home/alee/download/hybrid_wl/built-in.o
  CC [M]  /home/alee/download/hybrid_wl/src/wl/sys/wl_linux.o
  CC [M]  /home/alee/download/hybrid_wl/src/wl/sys/wl_iw.o
  CC [M]  /home/alee/download/hybrid_wl/src/shared/linux_osl.o
  LD [M]  /home/alee/download/hybrid_wl/wl.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/alee/download/hybrid_wl/wl.o
see include/linux/module.h for more information
  CC      /home/alee/download/hybrid_wl/wl.mod.o
  LD [M]  /home/alee/download/hybrid_wl/wl.ko
make: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'


```Well, it's a warning ... I ignore it and move on ...

```

cat /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wl


```Ok, then, looking at my history I see
```

  481  sudo rmmod bcm43xx
  482  sudo rmmod b43
  483  sudo rmmod b43legacy
  484  rmmod ndiswrapper
  485  sudo apt-get remove ndiswrapper-common
  486  sudo modprobe ieee80211_crypt_tkip
  487  sudo insmod wl.ko 
  488  sudo depmod -a
  489  echo wl | sudo tee -a /etc/modules 
  490  sudo modprobe wl
  491  sudo insmod /lib/modules/`uname -r`/wlan/wl.ko
  492  sudo mkdir /lib/modules/`uname -r`/wlan/
  493  sudo mv wl.ko /lib/modules/`uname -r`/wlan/
  494  sudo insmod /lib/modules/`uname -r`/wlan/wl.ko
  495  iwlist channel
  496  iwlist
  497  iwlist scan


```and iwlist scan reveals :

```

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.




```?????!!!!


So I try:

```

alee@dell-desktop:~/download/hybrid_wl$ sudo ifconfig eth1 down
alee@dell-desktop:~/download/hybrid_wl$ sudo dhclient -r eth1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:22:5f:f9:80:9c
Sending on   LPF/eth1/00:22:5f:f9:80:9c
Sending on   Socket/fallback
alee@dell-desktop:~/download/hybrid_wl$ sudo ifconfig eth1 up
alee@dell-desktop:~/download/hybrid_wl$ sudo iwconfig eth1 essid "gone_viral"
alee@dell-desktop:~/download/hybrid_wl$ sudo iwconfig eth1 mode Managed
alee@dell-desktop:~/download/hybrid_wl$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:22:5f:f9:80:9c
Sending on   LPF/eth1/00:22:5f:f9:80:9c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
resolvconf: Error: /etc/resolv.conf must be a symlink
 * Reloading /etc/samba/smb.conf smbd only
   ...done.



```

And ... nothing

```

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

pan0      Interface doesn't support scanning.

alee@dell-desktop:~/download/hybrid_wl$ 


```


The Network Manager still says "Wireless Networks -> device not managed" and if I edit connections and create a wireless account for eth1, the Network Manager doesn't store it.  That is, I open Network Manager again and the eth1 interface entry is gone!!!


I'm out in the weeds here.

Any help is greatly appreciated!

-- AF

---

### Post by Ayuthia on 2009-09-21
> **A_Fiachra said:**
> 
```

alee@dell-desktop:~/download/hybrid_wl$ sudo ifconfig eth1 down
alee@dell-desktop:~/download/hybrid_wl$ sudo dhclient -r eth1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:22:5f:f9:80:9c
Sending on   LPF/eth1/00:22:5f:f9:80:9c
Sending on   Socket/fallback
alee@dell-desktop:~/download/hybrid_wl$ sudo ifconfig eth1 up
alee@dell-desktop:~/download/hybrid_wl$ sudo iwconfig eth1 essid "gone_viral"
alee@dell-desktop:~/download/hybrid_wl$ sudo iwconfig eth1 mode Managed
alee@dell-desktop:~/download/hybrid_wl$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:22:5f:f9:80:9c
Sending on   LPF/eth1/00:22:5f:f9:80:9c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
resolvconf: Error: /etc/resolv.conf must be a symlink
 * Reloading /etc/samba/smb.conf smbd only
   ...done.



```



It looks like you might have a problem with /etc/resolv.conf.  Have you modified it?

---

### Post by A_Fiachra on 2009-09-21
> **Ayuthia said:**
> It looks like you might have a problem with /etc/resolv.conf.  Have you modified it?


Not intentionally.

NetworkManager added a few nameservers -- how rude!  (I have been running ethernet on eth0)

But NM still says that the wireless card is not managed.

---

### Post by Ayuthia on 2009-09-21
> **A_Fiachra said:**
> Not intentionally.

NetworkManager added a few nameservers -- how rude!  (I have been running ethernet on eth0)

But NM still says that the wireless card is not managed.

Can you post the results of the following:
```
lshw -C network
lsmod|grep -e b43 -e ssb -e wl -e ssb
dmesg|grep -e b43 -e wl

```
This will help us see what your wireless card is trying to use, what modules the system is trying to use, and if any error messages are showing up.

---

### Post by A_Fiachra on 2009-09-21
Happy to!

THanks for the assistance 

```

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:f9:80:9c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:56:59:35
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.101 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 46:12:a0:c7:a2:80
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

```

sudo lsmod|grep -e b43 -e ssb -e wl -e ssb
wl                   1283488  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl

```


```


dmesg|grep -e b43 -e wl
[   12.067863] wl: module license 'unspecified' taints kernel.
[   12.070074] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.070327] wl 0000:0c:00.0: setting latency timer to 64
[  272.248462] wl 0000:0c:00.0: PCI INT A disabled
[  273.000329] wl 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[  273.000390] wl 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf69fc004)
[  273.000402] wl 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  273.000419] wl 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[  273.000486] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  273.000497] wl 0000:0c:00.0: setting latency timer to 64
[ 3986.108450] wl 0000:0c:00.0: PCI INT A disabled
[ 3986.888321] wl 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 3986.888381] wl 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf69fc004)
[ 3986.888393] wl 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 3986.888410] wl 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[ 3986.888477] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3986.888489] wl 0000:0c:00.0: setting latency timer to 64


```

Interesting about that license warning ... the Broadcom driver builds with a warning that I can't clear up that shows up in dmesg.

Thanks again .. as you can see, I only have the wl driver installed -- I am starting to suspect the driver or the card is hosed.

--AF

---

### Post by Ayuthia on 2009-09-21
> **A_Fiachra said:**
> Happy to!

THanks for the assistance 

```

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:f9:80:9c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:56:59:35
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.101 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 46:12:a0:c7:a2:80
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

```

sudo lsmod|grep -e b43 -e ssb -e wl -e ssb
wl                   1283488  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl

```


```


dmesg|grep -e b43 -e wl
[   12.067863] wl: module license 'unspecified' taints kernel.
[   12.070074] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.070327] wl 0000:0c:00.0: setting latency timer to 64
[  272.248462] wl 0000:0c:00.0: PCI INT A disabled
[  273.000329] wl 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[  273.000390] wl 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf69fc004)
[  273.000402] wl 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  273.000419] wl 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[  273.000486] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  273.000497] wl 0000:0c:00.0: setting latency timer to 64
[ 3986.108450] wl 0000:0c:00.0: PCI INT A disabled
[ 3986.888321] wl 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 3986.888381] wl 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf69fc004)
[ 3986.888393] wl 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 3986.888410] wl 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[ 3986.888477] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3986.888489] wl 0000:0c:00.0: setting latency timer to 64


```

Interesting about that license warning ... the Broadcom driver builds with a warning that I can't clear up that shows up in dmesg.

Thanks again .. as you can see, I only have the wl driver installed -- I am starting to suspect the driver or the card is hosed.

--AF

The only thing that I can think of is that you might have multiple wl modules for the kernel installed.  Can you check this:
```
ls -l /lib/modules/`uname -r`/wlan/wl.ko
ls -l /lib/modules/`uname -r`/volatile
```
I am guessing that it is using your compiled version since you did the insmod, but I am not for sure if the Ubuntu supplied one was currently loaded before you tried to load yours.

---

### Post by A_Fiachra on 2009-09-22
> **Ayuthia said:**
> The only thing that I can think of is that you might have multiple wl modules for the kernel installed.  Can you check this:
```
ls -l /lib/modules/`uname -r`/wlan/wl.ko
ls -l /lib/modules/`uname -r`/volatile
```I am guessing that it is using your compiled version since you did the insmod, but I am not for sure if the Ubuntu supplied one was currently loaded before you tried to load yours.


Oh!


Yes, look :

```

$ ls -l /lib/modules/`uname -r`/wlan/wl.ko
-rw-r--r-- 1 alee alee 1382071 2009-09-21 05:47 /lib/modules/2.6.28-15-generic/wlan/wl.ko

$ ls -l /lib/modules/`uname -r`/volatile
total 2192
-rw-r--r-- 1 root root  216975 2009-09-21 18:44 ath_hal.ko
-rw-r--r-- 1 root root  124940 2009-09-21 18:44 ath_pci.ko
-rw-r--r-- 1 root root   18405 2009-09-21 18:44 ath_rate_amrr.ko
-rw-r--r-- 1 root root   25692 2009-09-21 18:44 ath_rate_minstrel.ko
-rw-r--r-- 1 root root   17528 2009-09-21 18:44 ath_rate_onoe.ko
-rw-r--r-- 1 root root   24120 2009-09-21 18:44 ath_rate_sample.ko
-rw-r--r-- 1 root root   15221 2009-09-21 18:44 wlan_acl.ko
-rw-r--r-- 1 root root   18459 2009-09-21 18:44 wlan_ccmp.ko
-rw-r--r-- 1 root root  247465 2009-09-21 18:44 wlan.ko
-rw-r--r-- 1 root root   16267 2009-09-21 18:44 wlan_scan_ap.ko
-rw-r--r-- 1 root root   26193 2009-09-21 18:44 wlan_scan_sta.ko
-rw-r--r-- 1 root root   22923 2009-09-21 18:44 wlan_tkip.ko
-rw-r--r-- 1 root root   17099 2009-09-21 18:44 wlan_wep.ko
-rw-r--r-- 1 root root   11249 2009-09-21 18:44 wlan_xauth.ko
-rw-r--r-- 1 root root 1381735 2009-09-21 18:44 wl.ko



```

So, what I should do is unload the module via modprobe, and install again.

But what about that strange license warning when I make Broadcom's wl and try to load it ..

```

 dmesg | grep wl
[   12.067863] wl: module license 'unspecified' taints kernel.


```

?


Thanks again.

-- AF

---

### Post by A_Fiachra on 2009-09-22
Still not working ...

This is odd:

```

$ sudo find /lib -name wl.ko -exec ls -l {} \;
-rwxr-xr-x 1 root root 1382071 2009-09-22 04:59 /lib/modules/2.6.28-15-generic/kernel/drivers/net/wireless/wl.ko
-rw-r--r-- 1 root root 1382071 2009-09-20 17:47 /lib/modules/2.6.28-15-generic/kernel/net/wireless/wl.ko
-rw-r--r-- 1 root root 1381735 2009-09-22 05:14 /lib/modules/2.6.28-15-generic/volatile/wl.ko

$ lsmod | grep wl
wl                   1283488  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl


```

I'm not even loading the module I built!

Reading modprobe manpage ...

---

### Post by Ayuthia on 2009-09-22
The Broadcom tainting the kernel is ok.  It is a proprietary kernel module so it will get that message.

The only think that I can think of is to try and hide the wl.ko file that is currently found in /lib/modules/`uname -r`/volatile.  Before doing it, remove the wl.ko module:
```
sudo modprobe -r wl
```

Then move the /lib/modules/`uname -r`/volatile/wl.ko file to a place that is not located in the /lib/modules folder and then run:
```
sudo depmod -a
```It will rebuild the module dependencies in /lib/modules so that it will not see the Ubuntu supplied one.

Afterwards, try loading yours again and hopefully it will work.

---

### Post by A_Fiachra on 2009-09-22
Thanks fir the help.

I decided to roll back to the factory presets (I didn't have that much data on my new laptop anyway).

I'm just going to leave it alone, since it is working now.

```

sudo lsmod|grep -e b43 -e ssb -e wl 
wl                   1283488  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl

```

```

sudo find /lib/modules/ -name :wl.*" -exec ls -l {} \;
-rw-r--r-- 1 root root 1588918 2009-09-22 07:45 /lib/modules/2.6.28-11-generic/volatile/wl.ko


```

So, the ISO has exactly one driver for the Broadcom card and no legacy drivers.  It's clear now that somewhere along the line I built a new driver, installed it, didn't remove the old driver and things got sketchy.

Note to self -- don't upgrade without a good reason!!!!

:)

---

### Post by jrounds on 2009-09-27
As of 9/17/2009 I don't think this works anymore:

make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`

The issue is the folders are missing from the tar and in their place is I think an object file?  I am unclear.  Its a shame I used this advice a year ago to get my wifi network card going in my dell laptop and now I am having issues on a new install =/

---

### Post by jrounds on 2009-09-27
So there appears to be changes to the driver files so that the initial instructions are different.  Just a simple make of the contents of the tar worked for me netting a wl.ko.   Then the instructions here of how to clean out old installs and edit all the files to make this permanent worked better then the manufacturers own instructions.  And then I didn't see the wlan work until I restarted, but after that this all worked great.

edit: oh these forums are threaded.  Sorry this is in wrong thread.

---

### Post by n00bz on 2009-10-05
hey ummm my wl stoped working again. there was something wrong with our power here in toronto and my laptop just stoped working for a day, i turned it on this morning and its working, only, nothing is on it. so pretty much my laptop's been formated somehow. anyways, i 'm trying to re-install it again but the links you provided me before with the patchs dont work. well there not there anymore, umm there seems to be something new or something,    the site was   [http://aur.archlinux.org/packages/broadcom-wl/broadcom-wl/](http://aur.archlinux.org/packages/broadcom-wl/broadcom-wl/)

and it has these files 

NameLast ModifiedSizeType  [Parent Directory]("http://aur.archlinux.org/packages/broadcom-wl/")/ -  Directory [PKGBUILD]("http://aur.archlinux.org/packages/broadcom-wl/broadcom-wl/PKGBUILD")2009-Sep-21 13:07:450.9Ktext/plain [broadcom-wl.install]("http://aur.archlinux.org/packages/broadcom-wl/broadcom-wl/broadcom-wl.install")2009-Sep-21 13:16:190.4Ktext/plain
ummm what do i do , i cant ```
 make
``` and it seems i needed to patch the last time it worked 

help?

---

### Post by n00bz on 2009-10-05
i'm following the steps again from pg17 

```
 alexis@nebakunezer:~/wdriver$ ls -l /lib/modules/`uname -r`/build
total 0
lrwxrwxrwx 1 root root 27 2009-10-04 23:44 linux-2.6.30.5-ep0 -> /usr/src/linux-2.6.30.5-ep0
lrwxrwxrwx 1 root root 25 2009-10-04 23:51 linux-2.6.30-ep0 -> /usr/src/linux-2.6.30-ep0
lrwxrwxrwx 1 root root 35 2009-10-04 23:47 linux-headers-2.6.30.5-ep0 -> /usr/src/linux-headers-2.6.30.5-ep0

```

i think there might be something wrong.

---

### Post by gnickm on 2009-10-19
Just thought I'd contribute a little note of my experiences of getting the native drivers working on a HP TouchSmart tx2 tablet... Got the module built and installed, blacklisted *b43* and *ssb*, but could not get the damn thing to work. I was running into the issue mentioned around p9 of this thread:

```

[root@314-000351 ~]# iwlist wifi0 txpower
wifi0     2 available transmit-powers :
	  0 dBm  	(1 mW)
	  25 dBm  	(255 mW)
          Current Tx-Power:off

```

Ahem. Apparently when the WiFi light on the tablet glows **orange**, that means it's OFF. Press the slider to the right and it should glow **blue**. Afterwards:

```

[root@314-000351 ~]#  iwlist wifi0 txpower
wifi0     2 available transmit-powers :
	  0 dBm  	(1 mW)
	  25 dBm  	(255 mW)
          Current Tx-Power:32 dBm  	(1496 mW)

```

And it worked like a champ. So, make sure your WiFi is ON before proceeding. ](*,) :mrgreen:

---

### Post by hajj_3 on 2009-11-24
does the BCM4321 work by default with ubuntu 9.10 64bit? I'm deciding whether to buy this mini pci-e card for my laptop or the intel wifi 5100, i'll be using it on win7 x64, xp sp3 and ubuntu 9.10 x64. I believe this driver for the intel will work: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&ProdId=3062&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&ProdId=3062&lang=eng)

many thanks.

---

### Post by Ayuthia on 2009-11-25
> **hajj_3 said:**
> does the BCM4321 work by default with ubuntu 9.10 64bit? I'm deciding whether to buy this mini pci-e card for my laptop or the intel wifi 5100, i'll be using it on win7 x64, xp sp3 and ubuntu 9.10 x64. I believe this driver for the intel will work: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&ProdId=3062&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&ProdId=3062&lang=eng)

many thanks.

It used to work after you went into System->Administration->Hardware Drivers and activated the Broadcom STA module.  However in 9.10, it does need to download some items (I am not for sure if it is on the liveCD or not though) from the repositories.  

So to answer your question, right now it does not work by default.

---

### Post by NTHQ on 2009-12-02
I did a clean install of Ubuntu 9.10 64-bit and when I go to Hardware Drivers, it says "No proprietary drivers are in use on this system." and this list is empty.
I followed the steps in the first post but I get this error.

```

sudo insmod wl.ko
insmod: error inserting 'wl.ko': -1 Unknown symbol in module

```I have an HP Pavillion dv9000.
Here is some info:

```

lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
05:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

``````

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

``````

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:5e:60:26  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe5e:6026/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7324373 (7.3 MB)  TX bytes:933308 (933.3 KB)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

EDIT: Problem solved. Kernel update found the drivers.

---

### Post by northd_tech on 2009-12-19
[SIZE=2]If it helps hajj and NTHQ, I've got a working Broadcom 4321AG (according to Win Vista) that I'm currently using with the Broadcom STA wireless driver under 64-bit ubuntu 9.04 Jaunty Jackalope (with AMD DuoCore CPU's) on a HP DV9800 series laptop.  I have seen "ndiswrapper" work quite well with these cards and the correct Windows drivers too.

My WiFi connection stays rock-solid at 100% and hasn't dropped all night (but I'm in the same room as the 802.11g router/"radio").

If it helps anyone, here are the results of a working Broadcom STA wireless setup (but Ubuntu 9.04 reports this as a Broadcom 4328, not a 4321AG like Vista calls it).

**uname -a**
> 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 21:27:25 UTC 2009 x86_64 GNU/Linux
[/SIZE]
[SIZE=2]
**lspci**
> ...
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)**lsmod**
> 
Module                  Size  Used by
...
ieee80211_crypt_tkip    17920  0 
...
wl                   1286352  0 
ieee80211_crypt        14596  2 ieee80211_crypt_tkip,wl
...**ifconfig**
> eth0      Link encap:Ethernet  HWaddr 00:3c:86:5b:52:0c 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:13:24:12  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd70::221:ff:fc16:2412/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102740 errors:0 dropped:0 overruns:0 frame:388511
          TX packets:62440 errors:14 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:146750806 (146.7 MB)  TX bytes:5959295 (5.9 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86620 (86.6 KB)  TX bytes:86620 (86.6 KB)

virbr0    Link encap:Ethernet  HWaddr 0a:d5:48:c1:37:af  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::8d5:48ff:fec1:37af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:326299 (326.2 KB)
**iwconfig**
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:207  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

virbr0    no wireless extensions.

pan0      no wireless extensions.


**sudo lshw -C network**
[/SIZE]>  [SIZE=2] *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:6c:5b:59:0d
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 03:17:00:11:2d:19
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.110 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: virbr0
       serial: 0a:de:4b:c1:37:af
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 link=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 32:a9:c9:c6:87:d6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/SIZE]

---

### Post by rahul12 on 2010-09-20
> **NTHQ said:**
> I did a clean install of Ubuntu 9.10 64-bit and when I go to Hardware Drivers, it says "No proprietary drivers are in use on this system." and this list is empty.
I followed the steps in the first post but I get this error.
 
```

sudo insmod wl.ko
insmod: error inserting 'wl.ko': -1 Unknown symbol in module

```I have an HP Pavillion dv9000.
Here is some info:
 
```

lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
05:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

``````

iwconfig
lo        no wireless extensions.
 
eth0      no wireless extensions.

``````

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:5e:60:26  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe5e:6026/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7324373 (7.3 MB)  TX bytes:933308 (933.3 KB)
          Interrupt:20 Base address:0xe000 
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```
 
EDIT: Problem solved. Kernel update found the drivers.
 
Hi could you update me how to update the kernel.
I installed ubuntu 10.04 LTS -the lucid lynx.
when i try to make the wl.ko file, it reverted back specifying no such file or directory
 
uname -r shws a file 2.6.32-24-generic 
 
Could you assist?

---

### Post by rahul12 on 2010-09-20
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`
 
I am not able to use this command
it responds saying no file or directory 2.6.32-24-generic
 
Any assistance appreciated

---

### Post by Habitual on 2010-12-12
use this instead: 
```

make -C /lib/modules/`uname -r`/build M=`pwd` clean
make -C /lib/modules/`uname -r`/build M=`pwd`

```

---

### Post by nick92 on 2011-02-15
Thanks a lot for this post mate. I have been trying to get the Wireless on my laptop working for ages, and have tried loads of different solutions but this is the only one that worked.

Thanks again
Nick

---

### Post by IncendiumDCLXVI on 2011-03-18
Hello all,
I'm not too new to Linux (having run Fedora for a while a couple of years ago), but new to Ubuntu and definately new to building things with the terminal. I am tech savvy, though...
Anyway, I have Ubuntu 10.10 on an iMac (late '08. My Airport card is BCM4321, kernel 2.6.35-22-generic (if you need more info just ask)
I'm having troubles at the "make" stage. When I enter: 
> [FONT=Courier New]make -C /lib/modules/2.6.35-22-generic/build M=`pwd`[/FONT]I get this:
> [FONT=Courier New]make: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  LD      /home/josh/wdriver/built-in.o
  CC [M]  /home/josh/wdriver/src/shared/linux_osl.o
  CC [M]  /home/josh/wdriver/src/wl/sys/wl_linux.o
  CC [M]  /home/josh/wdriver/src/wl/sys/wl_iw.o
  LD [M]  /home/josh/wdriver/wl.o
ld: Relocatable linking with relocations from format elf64-x86-64 (/home/josh/wdriver/lib/wlc_hybrid.o_shipped) to format elf32-i386 (/home/josh/wdriver/wl.o) is not supported
make[1]: *** [/home/josh/wdriver/wl.o] Error 1
make: *** [_module_/home/josh/wdriver] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'[/FONT]
I have been up all night! Please help.

---

### Post by Ayuthia on 2011-03-18
> **IncendiumDCLXVI said:**
> Hello all,
I'm not too new to Linux (having run Fedora for a while a couple of years ago), but new to Ubuntu and definately new to building things with the terminal. I am tech savvy, though...
Anyway, I have Ubuntu 10.10 on an iMac (late '08. My Airport card is BCM4321, kernel 2.6.35-22-generic (if you need more info just ask)
I'm having troubles at the "make" stage. When I enter: 
I get this:
I have been up all night! Please help.

It sounds like you might have downloaded the incorrect version of the Broadcom source..  You are either running a 32-bit Ubuntu system and compiling a 64-bit Broadcom driver or else you have the 64-bit and trying to compile the 32-bit.

You might want to double check the version that you downloaded (the package name should show if it is 32 or 64 bit) and then see if your system matches it by typing this in the Terminal:
```

uname -m

```
If it shows x86_64, it is 64-bit and something like i586 if it is 32-bit.

---

### Post by IncendiumDCLXVI on 2011-03-18
Thank you so much Ayuthia, 
I wouldn't have thought of that. I swear I thought I was running 64 bit, but regardless it works now!

---

### Post by Ayuthia on 2011-03-18
> **IncendiumDCLXVI said:**
> Thank you so much Ayuthia, 
I wouldn't have thought of that. I swear I thought I was running 64 bit, but regardless it works now!

You are welcome.  I am glad that you are able to get it up and running.  Congratulations!

---

### Post by IncendiumDCLXVI on 2011-03-18
Unfortunately I spoke too soon. While I was working on this issue I moved my computer next to the router so I can be hardwired, then when I got the wireless to work I unplugged the ethernet cable and it worked perfectly. After I moved the computer back to my desk, however, I can not get the wireless to connect. I can still see the settings in Net Config, but it's not connecting. Any ideas? I didn't change any settings, nor anything else. I simply shut her down and moved her....

---

### Post by Ayuthia on 2011-03-18
> **IncendiumDCLXVI said:**
> Unfortunately I spoke too soon. While I was working on this issue I moved my computer next to the router so I can be hardwired, then when I got the wireless to work I unplugged the ethernet cable and it worked perfectly. After I moved the computer back to my desk, however, I can not get the wireless to connect. I can still see the settings in Net Config, but it's not connecting. Any ideas? I didn't change any settings, nor anything else. I simply shut her down and moved her....

Are there other routers nearby that are using the same channel (You can see some of the information by going into the Terminal and typing 'sudo iwlist scan' without the quotes)?  I am thinking that there might be some interference in the air that is preventing the connection.  If you see some, you might try changing the channel on your router if it is possible.

---

### Post by IncendiumDCLXVI on 2011-03-18
Ayuthia,
Thank you for responding to me so quickly again. I was able to get it working by just uninstalling and reinstalling the driver. Hopefully that isn't just a temporary fix. If I run into this issue again I will be sure to try your suggestion.

Incendium

---

### Post by DarkTide on 2011-03-25
I get the following error:
ahid@RockerGeek:~/hybrid_wl$ sudo make -C /lib/modules/`uname -r`/build M='pwd'
make: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
make[1]: *** No rule to make target `pwd/src/wl/sys/wl_linux.o', needed by `pwd/wl.o'.  Stop.
make: *** [_module_pwd] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
 what do you think?
 Intrepid 
 HP2070ee tablet pc.
BCM4312

---

### Post by Ayuthia on 2011-03-25
> **DarkTide said:**
> I get the following error:
ahid@RockerGeek:~/hybrid_wl$ sudo make -C /lib/modules/`uname -r`/build M='pwd'
make: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
make[1]: *** No rule to make target `pwd/src/wl/sys/wl_linux.o', needed by `pwd/wl.o'.  Stop.
make: *** [_module_pwd] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
 what do you think?
 Intrepid 
 HP2070ee tablet pc.
BCM4312

You used a single quote for m='pwd' instead of the back quote "`" so it should have read:
```

sudo make -C /lib/modules/`uname -r`/build M=`pwd`

```
If I remember correctly you can also do:
```

sudo make -C /lib/modules/$(uname -r)/buld M= $(pwd)

```
and it will do the same thing but not use the quotes.

Hope that helps.

---

### Post by stekre on 2011-04-04
I'm having PROBLEMS with a BCM4311 card. Tried everything I can find for the last 2 days. I'm running jolicloud 1.2, but since it's based on ubuntu i hope you can help me.

It seems like everything is installed, but the driver isn't activated.

Here is the listing from: lshw -c network

  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:40400000-40403fff


I find the card under administration->hardware drivers, Broadcom STA wireless driver. But when I try to activate it I get this error:

SystemError:InstallArchives() failed

When I install the driver from synaptic I get this error:

Error! Bad return status for module build on kernel: 2.6.35.10-1-jolicloud (i686)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.6.48.36+bdcom/build/ for more information.


Would be great if someone could help me to fix this.

---

### Post by MasterNetra on 2011-05-12
Have a BCM4312 myself and found a workaround!

Pretty simple actually, just install maverick's bcmwl-kernel-source!

Link to the driver: [http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

---

### Post by garypeg on 2011-05-13
Sorry, should have marked this Resolved long ago.

---

### Post by saa1959b on 2011-05-29
> **mike_l said:**
> **Download the appropriate driver**

[LIST=1]
[*][COLOR=Lime] I downloaded the 64 bit version of the driver from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
It's important that you get the correct version, as the 32 and 64 bit versions are not compatible. [/COLOR]
[*][COLOR=Red]**Make the .ko file**[/COLOR]
[COLOR=Lime] First, make a temporary directory 
```
mkdir wdriver 

```... and place the downloaded package into it (hybrid-portsrc-_64_5_10_27_6.tar.gz, or hybrid-portsrc-x86_32_5_10_27_6.tar.gz for the 32 bit version)
Then 'cd' into the temporary directory and un-tar the file. 
```
cd wdriver
tar -xzf hybrid-portsrc-x86_64_5_10_27_6.tar.gz 

```Now, we want to make the wl.ko file, so we enter: 
(<2.6.xx.xx> is your kernel version: mine was "2.6.24-19-generic". Use tab-completion to find yours.)
[/COLOR]```
[COLOR=Lime]make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean[/COLOR]
[COLOR=Red] make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`[/COLOR]

```
[/LIST]
```
# make -C /lib/modules/2.6.38-8-generic/build M=`pwd` clean
make: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CLEAN   /home/saa1959/Downloads/wdriver/.tmp_versions
make: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'

# make -C /lib/modules/2.6.38-8-generic/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  LD      /home/saa1959/Downloads/wdriver/built-in.o
  CC [M]  /home/saa1959/Downloads/wdriver/src/shared/linux_osl.o
  CC [M]  /home/saa1959/Downloads/wdriver/src/wl/sys/wl_linux.o
/home/saa1959/Downloads/wdriver/src/wl/sys/wl_linux.c: In function &#8216;wl_attach&#8217;:
/home/saa1959/Downloads/wdriver/src/wl/sys/wl_linux.c:485:3: error: implicit declaration of function &#8216;init_MUTEX&#8217;
make[1]: *** [/home/saa1959/Downloads/wdriver/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/home/saa1959/Downloads/wdriver] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
```

Also see [http://pastebin.com/5gV1YvaY](http://pastebin.com/5gV1YvaY)

How do I successfully make the .ko file?

---

### Post by davequig on 2011-06-01
I'm at step 4 but when I input: sudo modprobe ieee80211_crypt_tkip
I get: FATAL: Module ieee80211_crypt_tkip not found

Then when I input: sudo insmod wl.ko
I get: insmod: error inserting 'wl.ko' : -1 Unknown symbol in module



Please help. Thanks.

---

### Post by stefounet on 2013-04-20
Hello. I realize this is an old thread and all relevant answers may already be around. Anyway, here is a [link]("http://wireless.kernel.org/en/users/Drivers/b43") that worked like a charm for me, no compilation needed. Summarized:
1. Identify the PCI-ID of your device by typing lspci -vnn -d 14e4:
2. Look it up in the "Supported devices" table provided in the link
3. If your PCI-ID is supported, you're in luck, because there is a package that will do all the work for you (see "Device firmware installation"). If not, well, I am not sure...

Good luck!

---

### Post by wildmanne39 on 2013-04-21
Thread closed. Please do not post in old threads.

---

