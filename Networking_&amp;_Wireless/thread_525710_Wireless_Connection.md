---
title: "Wireless Connection"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by Sonic12 on 2007-08-14
Hello all,

I'm extremely new to Ubuntu and cannot connect to the internet via wireless.

I know my wireless card works because on my XP partition it connects, picks up wireless networks and works well.  Unfortunately I have not had the same fortune with Ubuntu.

I entered the following line into the terminal and followed by the output:
----
lspci -v | grep -A 4 Eth

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
        Subsystem: Dell Latitude D610
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dfcf0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
----


I also entered and got:
----
lspci -v | less

03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.
11g Wireless LAN Controller (rev 02)
        Subsystem: Dell Unknown device 0005
        Flags: bus master, fast devsel, latency 64, IRQ 18
        Memory at dfbfe000 (32-bit, non-prefetchable) [size=8K]
----


Under    System -> Preferences -> Sessions   my "Network Manager" box is checked so that's not the problem.

Does anyone know what's going on?


Thank you!!

---

### Post by kevdog on 2007-08-14
Can you post 

lshw -C network

Your output shows a wired and wireless ethernet controller.  For the wireless controller you are going to have to install drivers -- either bcm43xx fw cutter or use ndiswrapper.  Either one will work for you

---

### Post by Sonic12 on 2007-08-14
Initially I tried got:
----
lshw -C network

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:43:4e:75:6b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.72 firmware=5751-v3.29a latency=0 multicast=yes
       resources: iomemory:dfcf0000-dfcfffff irq:16
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@03:03.0
       logical name: eth1
       version: 02
       serial: 00:14:a4:2a:60:c6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:dfbfe000-dfbfffff irq:18
----


I tried and got:
----
sudo apt-get install ndiswrapper

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper
----


then:
----
sudo apt-get install bcm43xx fw cutter

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcm43xx
----


hmm....?  (thank you)

---

### Post by Phurious on 2007-08-14
I was in the same boat.  I am using a similar system, a Dell M70 with a Broadcom 4311.  I had been trying, unsuccessfully, for some time to get my wirless up until I found this thread - [http://ubuntuforums.org/showthread.php?t=405990&highlight=4311]("http://ubuntuforums.org/showthread.php?t=405990&highlight=4311") .  I downloaded the GTK installer mentioned, and ran the "installer.py" script.  When it launches, it seems to want to install the broadcom firmware; I used the second option and installed the ndiswrapper and driver.  It is important to note that I tried to use this tool before and it did not work.  I decided I would do a clean install of Feisty and start over - no telling what I changed hacking on it.  The process I used:

1.  Clean install of Feisty

2.  Then in a terminal window:
     ```
sudo apt-get update
sudo apt-get upgrade
```

3.  Next I used the installed from the above mentioned post before doing anything else to the system. 

Surprisingly, this also allowed me to connect to my router running WPA2 and TKIP with no other modifications required.

---

### Post by kevdog on 2007-08-14
Here is how to install ndiswrapper:

**[SIZE="4"]Download, Compiling, Installing and Configuring Ndiswrapper from Source Files[/SIZE]**



If you already have an internet connection (ie a working wired ethernet connection),

please skip to step #4. Without any internet connection, please begin at step #1.



All commands typed at command prompt:



```


   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"

   2. sudo apt-cdrom add

   3. sudo aptitude update

   4. sudo aptitude install build-essential linux-headers-`uname -r`
```





OK next we want to download the ndiswrapper source files (Reference URL = _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_)



We are grabbing ndiswrapper-1.48-rc1



```
cd ~

mkdir ndiswrapper

wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz -O ~/ndiswrapper/ndiswrapper-1.48rc1.tar.gz 

cd ndiswrapper


```



Extract, compile, and install ndiswrapper

```
tar -zxvf ndiswrapper-1.48rc1.tar.gz

cd ndiswrapper-1.48rc1

make distclean

make

sudo make install
```



Verify installation with

```
ndiswrapper -v
```



The output should be something like the following:

```


utils version: '1.9', utils version needed by module: '1.9'

module details:

filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko

version:        1.48rc1

vermagic:       2.6.20-16-generic SMP mod_unload 586


```



Next create and place your Window's wireless driver into ~/driver:

```
cd ~

mkdir driver

cd driver
```



Ensuring the ***.sys and ***.inf file for the Window's driver are in the~/driver directory:

```
sudo ndiswrapper -i *****.inf
```



Verify installation with:

```
ndiswrapper -l
```

Make sure no errors are reported and you get something like:

> 

bcmwl5: driver installed

device (14E4:4320) present





Ok, to insert the ndiswrapper module into the linux kernel:

```
sudo depmod -a
```



Ensure you dont get any errors when running this command.  Then:

```
sudo modprobe ndiswrapper
```



To verify there wasnt any errors:

```
dmesg
```

and look for something like:

> ndiswrapper version *version* loaded



Next lets make an alias for wlan0 associated with ndiswrapper

```
sudo ndiswrapper -m
```



And ensure that the ndiswrapper module is loaded at boot:

```
echo "ndiswrapper" | sudo tee -a /etc/modules
```



I recommend rebooting at this time.

```
sudo shutdown -r now
```



Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running

---

### Post by Sonic12 on 2007-08-15
Thanks to everyone for the help!!

It's up and running now.


w00t!
^.^

---

