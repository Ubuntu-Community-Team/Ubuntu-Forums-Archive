---
title: "Broadcom wireless help"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by Itchmecho on 2007-09-05
ok i have ready some things about broadcom wirless cards so i know what is sorta going on, but i am still very new to the linux, and this is my first distro. so a lot of guides say i need a wired connection, but i don't have one, i have always had a wireless, and mine is a desktop. the wires are all downstairs, and stuff, and i am not movin this thing downstairs, i mean that is just way too many stairs! so is there any way to do it without a connection, or downloading all the files on here and then putting them on the HD so Ubuntu can like detect? or something?  i am not THAT computer literate, i am sorta from a beginers level, but i am not into networking or any of that stuff:(:( i would love the help

---

### Post by kevdog on 2007-09-05
Here are my ndiswrapper instructions.  
To complete without a working internet connection you will need:
1. The ubuntu installation cd
2. USB flash drive
3. Another computer with an internet connection to transfer just a few files
4. WinXP drivers for your Broadcom wireless card

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

---

### Post by Itchmecho on 2007-09-05
is it ok to use vista drivers?

---

### Post by kevdog on 2007-09-05
No, do not use the Vista drivers.  You need the WinXP drivers.  Are you using a 64bit or 32 bit version of ubuntu??  If using 64bit, you need the 64 bit WinXP driver.  You might need to download these drivers from the manufactures website.

---

### Post by Itchmecho on 2007-09-05
no i got 32 bit because my vista is 32 bit, and ok i got the winXP drivers and everything on there, now i just need help installing it, i already posted. and thank you for all your help, your very fast in replying, and give lots of help! thanks a lot! :D

would you like the link to my other thread so you can help me or no? lol thanks for the help again!

---

### Post by kevdog on 2007-09-05
Ill help you but I gave you the instructions on how to do everything...unless you've already tried ndiswrapper and kinda of "screwed things up"

---

### Post by Itchmecho on 2007-09-05
meh nvm about it, i just needed to get my wireless card to work once i installed it, but i havn't yet, i know kinda dumb, but i know that my card has a problem because when i tried to load it up from the live CD it still wouldn't show up but nvm about the other thing

---

### Post by kevdog on 2007-09-05
NO idea what you meant in the last post, but post back if you need any further help

---

### Post by Itchmecho on 2007-09-06
ok i am having trouble installing the ndiswrapper... when you said this:  If you do not have an internet connection, on a different computer you will need to download the ndiswrapper source file from: 
[http://superb-east.dl.sourceforge.ne...1.48rc1.tar.gz](http://superb-east.dl.sourceforge.ne...1.48rc1.tar.gz)
Please place this file on a flash drive (USB Flash drive), transfer it to the Ubuntu machine, and then place it in the ~/ndiswrapper directory. Continue with the next following set of instructions


but i can't install the ndiswrapper directory, and when i try the steps listed after... i keep getting errors... now how the heck do i install ndiswrapper program, i am really confued!!! can someone tell me what i should see and do?

---

### Post by kevdog on 2007-09-06
Make the directory ndiswrapper

cd ~
mkdir ndiswrapper

Copy the ndiswrapper.tar.gz file to ~/ndiswrapper

cd ~/ndiswrapper

Extract the source files:
tar -zxvf ndiswrapper.14XXXXX.tar.gz <---Again use your version here
cd ndiswrapper-1.4XXXXXX  <----Again substitute your correct directory here

Compile and install ndiswrapper
sudo make distclean
make
sudo make install

This makes the ndiswrapper module.  Insert the driver inside the module
sudo ndiswrapper -i ***********.inf <-----Whatever driver you have
sudo modprobe ndiswrapper

---

### Post by Itchmecho on 2007-09-06
ok thank you i didn't see a step in the other one...

now i am having to go through the whole 9 yards, i have to do EVERYTHING it just won't take, aghhh anyways if i have anymore questions i will post here

---

### Post by Itchmecho on 2007-09-06
alright i think i have a big problem, whenever i boot ubuntu the lights on my receiver card don't light up... what is up with that? i did everything, but my network settings say i only have the loopback, and not the WLAN... i am gonna see because i didn't reboot my computer after i made those changes, so maybe i had to reboot

---

### Post by kevdog on 2007-09-06
If your are still having problems just post the following so we can verify/debug your current situation

lshw -C network
ndiswrapper -l
modinfo ndiswrapper
iwlist scan
/etc/iftab

---

### Post by Itchmecho on 2007-09-07
ok here it is in an attachment

---

### Post by Itchmecho on 2007-09-07
i will be reading any response tomorrow, i am in Eastern time and it is 1:00 AM, i am supposed to get up at 5:00 so i should be back around 3:00 PM tomorrow

---

### Post by kevdog on 2007-09-07
Do the following and then reboot:

echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist
echo ndiswrapper | sudo tee -a /etc/modules

---

### Post by Itchmecho on 2007-09-07
ok well that works, only, another problem popped up, it says i can connect to the network, i have that wlan0 option, and the light shows up, but i can not connect, i don't know why, any ideas?

---

### Post by kevdog on 2007-09-07
You are close

Please post the following 
lshw -C network
iwlist scan
modinfo ndiswrapper 
ndiswrapper -l

---

### Post by Itchmecho on 2007-09-07
OK I THINK MY COMPUTER IS LIKE HAUNTED OR SOMETHING! i got it to work, but only under the manual configuration, i don't wanna do it like that, i want it to connect automatically...
 i will post what you want faster because i don't have to swich

---

### Post by Itchmecho on 2007-09-07
ok here is a screenshot of my network settings, i will send you more in a PM if you want me to, or i could put it on here [http://i83.photobucket.com/albums/j306/shadow_gds/scrnofnetworksettings.png](http://i83.photobucket.com/albums/j306/shadow_gds/scrnofnetworksettings.png)

---

### Post by Itchmecho on 2007-09-07
do you know how to get it without the manual?

---

### Post by kevdog on 2007-09-07
Two things to make it connect automatically -- again right now for unencrypted network.

#1. Comment or delete all the lines in the /etc/network/interfaces file except the two lines containing lo
Id recommend the comment and also copying the file to back it up. (This along with xorg.conf -- but thats a different story)

2. Based on the screenshot you showed me, click properties and select enable roaming.  (Will not work on Dapper).  If you dont have that option reboot, and then look for it again.

---

### Post by Itchmecho on 2007-09-07
ok well need to do that later, but i have a problem not really related to networking, but i will ask it anyway, i have an external drive, how come ubuntu won't read it? it used to, but now it doesn't

---

### Post by kevdog on 2007-09-08
is the device mounted?  you can type mount to see if its assigned a path.  iyou might have to mount it manually.  i find that sometimes i need to do this with my usb stick    who the heck knows why?

---

