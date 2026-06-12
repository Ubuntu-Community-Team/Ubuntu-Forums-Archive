---
title: "linux and wireless"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by Gothy on 2007-09-06
ok thats it!

i've had enough ive used 2 versions of ubuntu now, and each time.
I cant get the wireless to work!

even asking you guy's for help,  so many people flood the forum, about there own problems or ignoor my posts!

IS THERE A LINUX THATS FREE, AND MAKES WIRELESS WORK EASLIY?

---

### Post by codesplice on 2007-09-06
What wireless card are you having so much trouble with?

---

### Post by kevdog on 2007-09-06
Please post the following

lspci -nn
lshw -C network

---

### Post by Gothy on 2007-09-07
thank you,

I have ubuntu version 7.04
and a belkin F5D7051 usb high speed wireless G network adapter

AS normal it wont work out the box on ubuntu!

if possible please give me a fool proof guide as to how to get my wireless set-up,
remembering that i dont know much technical about linux!

Please help! plz plz plz.

last time i got so far,
then i couldnt download the particular drivers from this site i needed!

---

### Post by codesplice on 2007-09-07
I hate to be the bearer of bad news, but the Linux-USB Device Overview website shows no support for your device.

[http://www.qbik.ch/usb/devices/showdev.php?id=3513](http://www.qbik.ch/usb/devices/showdev.php?id=3513)

Evidently at least one person has had some luck:

> Yes, tricked my mandriva. first installed the ndiswrapper-rpm (1.2) without success, then (without uninstalling) compiled ndiswrapper 1.13 and loaded the driver (who is hidden on the CD) as root in my terminal, following the installation instructions on ndiswrapper-wiki. Then used the mandriva controlcenter to configure a new wifi-connection. Works right now. F5D7051 uses the BCM4320 chipset.

Don't know if that will help you or not.

Good luck.

---

### Post by kevdog on 2007-09-07
OK, some conflicting stuff out on google, but it seems that your device has a broadcom 4320 chipset.  This means you will need to install ndiswrapper along with WinXP drivers for the device.

ndiswrapper is not a problem

Do you have WinXp drivers for your device? (not vista!!)

---

### Post by Gothy on 2007-09-07
yes i have the windows drivers for it as im using them at the moment!

thanks soooooooooooooooo much for your help!:KS

right Ndiswrapper,
where can i get this and is it easy to set-up?:confused:

---

### Post by Gothy on 2007-09-08
ok i have downloaded ndiswrapper 1.47

I'm going to plug in my linux hard drive and see how i get on, any suggestions would really help! :)

---

### Post by Gothy on 2007-09-08
ok i have no idea even when following the instrutions on how to set-up ndiswrapper.

is it possible for anyone to help me with this?
a step by step linux noob guide!

eg. click on the terminal, go to the desktop, double clcik ndiswrapper e.t.c.

---

### Post by kevdog on 2007-09-08
Give me a second to find the instructions....

---

### Post by kevdog on 2007-09-08
Here are my ndiswrapper instructions.  
To complete without a working internet connection you will need:
1. The ubuntu installation cd
2. USB flash drive
3. Another computer with an internet connection to transfer just a few files
4. WinXP drivers for your wireless card


This guide is now getting rather long.  It is organized into the following sections
1. Installation of ndiswrapper and windows drivers from source files (what most people want)
2. Ensuring that your wireless interface is on wlan0 and not some other interace (eth1,ath1,etc)
3. Modification of /etc/network/interfaces file (for those wanting to use NetworkManager)
4. Common Tips Problems, Suggestions (This section is continually growing, check here first if you have a problem)

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

***The following section will work if you have an internet connection
*** If you do not have an internet connection, on a different computer you will need to download the ndiswrapper source file from: 
[http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz)
Please place this file on a flash drive (USB Flash drive), transfer it to the Ubuntu machine, and then place it in the ~/ndiswrapper directory.  Continue with the next following set of instructions
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

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files (see below).
In addition, please turn off any (WEP/WPA/MAC filtering) that may be present in the router.  This is to confirm that the basic ndiswrapper setup can connect to an unencrypted network.  Instructions how to configure for WEP/WPA encryption are included in another separate guide. 

Ndiswrapper by default assumes your card to be assigned to the interface wlan0 -- this may or may not be the case.
If after rebooting, and you issue the following command:
```
ifconfig
```
And you do not see an interface named wlan0, then continue.
Below are some strategies that I have used to ensure that your wireless device is assigned to the wlan0 interface.

**Verification/Modification of /etc/iftab file**

The /etc/iftab file acts to permanently asssociate a given MAC Address with an interface name.  Additions in this file are only necessary if you need to lock down the interface name with a MAC Address.  First discover what interface name is currently associated to your network card MAC Address:
```
lshw -C network
```

Example output:
```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       **logical name: wlan0**
       version: 03
       **serial: 00:12:17:35:17:10 **
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

```

In the example above my card's MAC Address - 00:12:17:35:17:10 - is currently assigned to wlan0 (logical name line).  If your card is assigned to a different logical name (such as eth1, ath0, ra0), then modifications will be needed to your /etc/iftab file.  

To modify your /etc/iftab file:
```
gksu gedit /etc/iftab
```

You will need to ensure your interface name is associated with wlan0 rather than a different interface name. There are two ways to accomplish this: 
#1) Let the computer do it automatically at boot, 
#2) Manually make the association  

In case #1 manually comment all the associations listed in your /etc/iftab file -- allow the computer to assign them internally at boot.  **This solution is probably the most viable for most users.**  An example of how to accomplish this:  

```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

#eth1 mac 00:12:17:35:17:10 arp 1

```

Because the association of eth1 with the MAC Address was commented, the computer will internally and automatically make the assocation of an interface name with the MAC address.  This process of associating wlan0 with the networking device's MAC Address should work about 99% of the time.  If for some reasom it does not, proceed to step #2.

In case #2 - Manually make the association you need to ensure there is only one MAC address associated with one interface name.

```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

#eth1 mac 00:12:17:35:17:10 arp 1
wlan0 mac 00:12:17:35:17:10 arp 1

```

In this example the old interface associated of eth1 was commented, and the new association of wlan0 to the card MAC address was made manually.

If modification of the /etc/iftab file was performed, a reboot is recommended at this time.
```
sudo shutdown -r now
```

**Modification of /etc/network/interfaces file**

First step is to comment out all the unnecessary interface names with the file.  In order to discover what interface names are currently needed:

```
lshw -C network
```
With all the devices listed, note their logical names.  An example:

```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       **logical name: wlan0**
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

```

Only the names mentioned with this command need to be listed in the /etc/network/interfaces file (along with the loopback address).

First backup your current interface file configuration in case something goes wrong:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak

To modify your /etc/network/interfaces file:
[CODE]gksu gedit /etc/network/interfaces
```


A basic interface file, might include the following (assuming a wired ethernet device is present - eth0, and the wireless device installed with ndiswrapper - wlan0) -- Note in this example I commented out the old eth1 interface -- I could have also removed these lines to have the same effect.

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

```

Further modications may be needed to this file, depending if you need to run your card in roaming mode (convenient with laptops that often connect to different routers of networks), configure your card with static IP address, desire to set WEP/WPA authentication parameters manually, etc.  Again there are many possibilites at this point, far too many to list the different permutations, however this gives you a basic starting point.


**[SIZE="4"]Common Tips Problems, Suggestions[/SIZE]**

Suggestions:
1. The command **[SIZE="3"]lshw -C network[/SIZE]** always tells you what driver you are using. Here is an example:
```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **[SIZE="3"]driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1[/SIZE]** ip=192.168.1.102 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11


```

If you are having a problem after the installation, ensure that you have the correct version of ndiswrapper installed, and that you are not using another driver.

2. Discovering your chipset -- You can always find the chipset of your pci wireless device with the following command (***Note this will not work for wireless USB dongles):

```
lspci -nn | grep Network
```

3. **Broadcom chipset users** -- Be sure to blacklist the bcm43xx driver in the /etc/modprobe.d/blacklist file

For broadcom chipset users, in most cases you will need to blacklist the native bcm43xx drivers since they take precedence over ndiswrapper.  If after installing ndiswrapper, and things are not working, and you check lshw -C network and you find the following:
```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **[SIZE="3"]bcm43xx[/SIZE]** ip=192.168.1.102 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11


```

You need to do ONE of the following to solve this problem:
a. At command line type:
```
echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist
```

b. Manually edit the /etc/modprobe.d/blacklist file: (```
gksu gedit /etc/modprobe.d/blacklist
```), and add the following:
```
blacklist bcm43xx
```

4. INVALID DRIVER - Ive installed ndiswrapper but when I try to install the Windows driver Im getting a line that states:

```

root@dhcppc1 ndiswrapper-1.47]# /usr/sbin/ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
root@dhcppc1 ndiswrapper-1.47]# /usr/sbin/ndiswrapper -l
bcmwl5 : invalid driver!
driver : invalid driver!

```

This error usually means that there are duplicate or more than one driver installed with ndiswrapper.  The easiest way to resolve this message is to do the following:

```
sudo rm -R /etc/ndiswrapper *
```

You will then have to reinstall your windows driver via.
```
sudo ndiswrapper **********.inf  <-----Substitue the appropriate name of your inf file here.
```

5. I tried install ndiswrapper from repository before I found this guide.  How do I uninstall it??

B][SIZE="4"]Ndiswrapper Uninstall Instructions[/SIZE][/B]

These are instructions for manual un-installation of ndiswrapper.  I would suggest if you installed ndiswrapper from repository with use of Synaptic, apt-get(aptitude), or some other means (Aptitude), you use the same means to uninstall the ndiswrapper program.  Sometimes however un-installation via these means are unsuccessful and the following steps are necessary.  These steps are also necessary if you have ever installed ndiswrapper from source sometime in the past.

Dont worry if some of these commands don't do anything or seem not to work -- some may be repetitive.

```

sudo aptitude purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo sh -c "sed '/^ndiswrapper$/d' /etc/modules > /etc/modules.temp.rm; mv /etc/modules.temp.rm /etc/modules"
sudo rmmod ndiswrapper
sudo /lib/modules/`uname -r`/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
sudo rm -rf /etc/ndiswrapper
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

```

---

### Post by Gothy on 2007-09-09
thanks for trying ur a star:KS

however it hasnt worked!

can i have your email address, I would like to send you a file which is an open office 2.2 file
no programs i have outside of ubuntu can read it!
The file contains everything that the terminal said,
from start to finish!

sorry for being a pain, but im such a linux noob:confused::confused::confused:

---

### Post by kevdog on 2007-09-09
Just post the contents of the files here,

or pipe the output of th commands to a file, like

iwlist scan > iwlist.txt

You can even append other commands to the file like:
lshw -C network >> iwlist.txt

Then transfer the file to a USB stick and to a computer that has an internet connection and then cut and paste the contents of the files right into the forum

---

### Post by Gothy on 2007-09-09
eh what ?

sorry that was also too confuseing

ok lets pretend, ok forget that. I KNOW NOTHING ABOUT COMPUTERS

:( :confused:
sorry is itpossible to do it the old fassioned email way

ahha
[www.yousendit.com](www.yousendit.com)
use that yeah register plz

---

### Post by kevdog on 2007-09-09
What part didnt work??  I dont need the exact error message, but what part in the instructions didnt work?

If you are unsure please post

ndiswrapper -v
ndiswrapper -l

---

### Post by Gothy on 2007-09-10
ok this is the bit it got stuck on.

Extract, compile, and install ndiswrapper
Code:

tar -zxvf ndiswrapper-1.48rc1.tar.gz
cd ndiswrapper-1.48rc1
make distclean
make
sudo make install

Verify installation with
Code:

ndiswrapper -v

The output should be something like the following:
Code:

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.48rc1
vermagic:       2.6.20-16-generic SMP mod_unload 586

--------------------------------------------------------------------------------

i will put the error messages from the terminal in a different program give me a few minutes.

---

### Post by kevdog on 2007-09-10
If you are having problems with this portion, just make sure you have installed the build-essential package and linux-header-`uname -r` package.  These two steps are in the very first part of the instructions.  Notice the backticks on the uname -r statement, not quotes.

To save you some space you dont have to type all the errors.  If the header files are not installed properly then you will get a bunch of cant find ******.h file.  

If you are past the make step listed above and actually did the make install statement, you can uninstall if you go into the install directory, and type sudo make uninstall, then sudo make distclean 

Again just one or two lines of the error output is sufficient.  If you are getting an error stating cant find the module utility, then keep going.  Just make sure you dont have ndiswrapper 1.38 showing.  This will give you errors later.  You need the ndiswrapper -v statement to show version 1.47 or later.

---

### Post by Gothy on 2007-09-10
this message did not appear,

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename: /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version: 1.48rc1
vermagic: 2.6.20-16-generic SMP mod_unload 586

when you say the backticks for uname - r statement
do i have to type  my username?

also the term DIRECTORY  im usure what you mean about this!

---

### Post by kevdog on 2007-09-10
What message appeared??

Type 
uname -r 
at the command line.

Lets say for example the output is name 2.6.22

linux-headers-`uname -r`

This is a shortcut way of writing
linux-hearders-2.6.22

---

### Post by SactoBob on 2007-09-10
If you want to use Linux, and it is worth $60 to get high performance, hassle free, wireless going, see [http://ubuntuforums.org/showthread.php?t=387871](http://ubuntuforums.org/showthread.php?t=387871).

A a wireless bridge will convert your wireless signal into a wired standard ethernet connection, and give you better performance too.

---

