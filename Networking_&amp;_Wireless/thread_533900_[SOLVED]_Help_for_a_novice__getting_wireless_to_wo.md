---
title: "[SOLVED] Help for a novice : getting wireless to work"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by MSDeath on 2007-08-24
I have just converted to Feisty after a life time of MS. I installed it on a physically sepearte hard rive in my Dell 8400 which now dual boots into Ubuntu and XP Pro.

The install was a  breeze and everyhting seems to work brillantly except internet connection.

I have followed numerous threads  but none of the proposed solutions seem to work. The dell is 4 years old now and has all the bells and whistles.

When I type in lspci - v i get the following output
02:00.0 Network Controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
Subsystem: Melco Inc Buffalo WLI2-PCI-G54S High Speed Mode Wireless Desktop Adapter
Memory @ fcfe000

I don't know anyhting about Linux and am really struggling to get this going.

All help appreciated

---

### Post by kevdog on 2007-08-24
You are in good shape, so dont worry about a thing.  Do you have an ethernet connection that you can use in Ubuntu to download files, or do you think you might need a USB flash stick to transfer files from a different computer with an internet connection?  

Ill send you the instructions for your setup once I get them.  And do you have any Windows XP drivers for your networking card?

---

### Post by MSDeath on 2007-08-25
No Ethernet connection. Transfering via USB Stick.
The machine dual doots into XP and I have all the disks / drivers available.
I copied fwcutter onto desk top .tar.bz2 file type and extracted it.
However when I run sudo apt-get install bcm43xx-fwcutter in the terminal window it comes back with package not found!
Appreciate any help you can provide
Cheers

---

### Post by kevdog on 2007-08-25
We can do either bcm43xx-fwcutter or ndiswrapper.  bcm43xx is a lot easier initially just to get up and running.  jamie-jackson is doing to testing right now, and he is at least finding the svn ndiswrapper version to be roughly twice as fast as the bcm43xx approach, however results are not done yet and no conclusions up to this point.  We could always switch later.

Here the reference I used: [http://boredklink.googlepages.com/ubuntuguide](http://boredklink.googlepages.com/ubuntuguide)

Since you dont have an internet connection, you can use the above as reference and follow these steps:

References: 
	[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)
	[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

By default Im using a Linksys WPC54GS wireless card.  It contains the Broadcom Corporaton rev03 chipset.
These instructions are only likely to work if your wireless Card has a Broadcom Corporation chipset rev03 or higher
To check the chipset of your card (At a terminal prompt):
lspci | grep Broadcom\ Corporation

My Results returned:
06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Assuming you have a:
1. Wireless Card with Broadcom Chipset rev03 or higher
2. The computer in which you are installing that has no access to the internet
3. A USB stick
4. A second computer that does have access to the internet

You can do the following to obtain a wirless connection on an unencrypted network (encryption will be dealt with later).

1. On the computer with the internet connection and with USB drive installed
	Download the following 2 files to the USB stick:
	Debian Prepackaged Source for bcm43xx-firmware package:
		hhttp://packages.debian.org/testing/utils/bcm43xx-fwcutter

	Broadcom 43xx v3 windows driver:
		[http://drinus.net/airport/wl_apsta.o](http://drinus.net/airport/wl_apsta.o)

2. Insert the USB stick into the wireless computer in which you are installing Ubuntu
3. The USB stick should be recognized automatically, and a window should come up asking you what to do.  Select open folder
4. Navigate to where you placed the 2 files above.
5. Right Click on the Debian File and select Install with Debian Package Manager
	During the installation a dialoge box will appear, click on Terminal.  After sometime a Blue screen will appear in the 
	terminal asking whether you want to download updates.  Select NO (since there is no internet connection). And the installation
	will continue and complete
6. Drag the wl_apsta.o to the Desktop
7. Type the following lines within a terminal window:
	sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o
	sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/wl_apsta.o 

Driver installation should be successful at this point.
To test and see if there is a network connection
1. On the Gnome taskbar, goto System->Administration->Networking
2. Select Wireless Connection. A Second Window will pop-open (or select Properties) and select Enable Connection.
	Type the name of your wireless network (This can be found within your router settings - with Linksys routers
	[http://192.168.1.1](http://192.168.1.1). Wireless - Wireless Network Name SSID.  Also make sure on the router Security Mode is disabled (for now).)
	Close the window
3. A dialog box should appear with progress bar stating it is activating Network Interface.
4. To see if connection was successful, at terminal prompt type: ifconfig.
	Look for section heading under eth0 or eth1 (ethX) to see inet addr.  It should read something like:
	inet addr:192.168.1.101.

---

### Post by MSDeath on 2007-08-25
Thanks for the install guide. However I can't seem to find the file at the provided link;
[http://drinus.net/airport/wl_apsta.o](http://drinus.net/airport/wl_apsta.o)
Is there something else I should be looking for?
Cheers

---

### Post by MSDeath on 2007-08-25
I can also access the XP partition and drag the bcmwl5.sys and .inf files from there. However I don't understand the wl_apsta.o thing. Is this a file of some sort? 
Cheers

---

### Post by kevdog on 2007-08-25
Let me look around and see if I have a copy of the wl_apsta.o file -- sorry about the dang link -- it is definitely broken.  Iv got to have that file around here somewhere.  Give me a few hours.

---

### Post by kevdog on 2007-08-25
Here -- try this link -- it took me a while to find it
[http://www.revis.co.uk/site/files/](http://www.revis.co.uk/site/files/)

---

### Post by MSDeath on 2007-08-25
That doesn't do it. The website provides a link with the right name but takes you to a page full of characters. No downloads.
Can I copy and compile this or is there an alternative?
Cheers

---

### Post by kevdog on 2007-08-25
Can you right click on the file, and select save link(file) as?

---

### Post by MSDeath on 2007-08-25
i can do save link as. thats all

---

### Post by kevdog on 2007-08-25
Here is the file I used

To extract

tar -zxvf wlaspta.o.tar.gz

---

### Post by MSDeath on 2007-08-25
On the second command "sudo bcm43xx-fwcutter -w /lib/firmware..." etc I get "Cannot open input file ~Desktop/wl_apsta.o"
The extraction went fine as did the first command line
Any further advice?

---

### Post by MSDeath on 2007-08-25
Missing a "/" in 2nd command line. That seems to have worked. But no wireless showing in Networks.
Rebooting to check

---

### Post by MSDeath on 2007-08-25
Still nothing. No wireless showing.

---

### Post by kevdog on 2007-08-25
Can you post lshw -C network

Im about ready to bail on the bcm43 approach and just go with ndiswrapper -- are you?

---

### Post by kevdog on 2007-08-25
Just one last question before bailing.  Did you put the wl_apsta.o file on the Desktop before running:

```
sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o
sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/wl_apsta.o 
```

---

### Post by MSDeath on 2007-08-25
The bcm43xx is getting to me. How difficult to to ndiswrapper?

---

### Post by MSDeath on 2007-08-25
Could we do this tomorrow? If you post the requirements I will follow them through tomorrow evening and provide updates.
Cheers

---

### Post by kevdog on 2007-08-25
Ok, you already have your WinXP (not Vista) .sys and .inf files available. -- Thats half the battle.

Here is the rest of the setup (Dont get intimidated, although its a lot of steps.)  In addition to what is listed, first blacklist the bcm43xx module so it doesnt conflict (This attempts to get rid of what we just did)

```
echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist
```

Now the meat and potatoes

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
Please place this file on a flash drive (USB Flash drive), transfer it to the Ubuntu machine, and then place it in the ~/ndiswrapper directory.  Skip the following instructions in the box down below, and begin with ***Extract, compile and install ndiswrapper
```
cd ~
mkdir ndiswrapper
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz -O ~/ndiswrapper/ndiswrapper-1.48rc1.tar.gz 
cd ndiswrapper

```

****Extract, compile, and install ndiswrapper
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

### Post by MSDeath on 2007-08-25
How do I move ndiswrapper into the ndiswrapper directory?

---

### Post by kevdog on 2007-08-26
Can use nautilus -- GUI -- drag and drop or if on USB stick something like

mv /media/xxxxx/ndiswrapperxxxx.tar.gz ~/ndiswrapper

---

### Post by MSDeath on 2007-08-26
This works like clockwork. I didn't have to change the interfaces as it works perferctly well on eth0 and I have no wired network.
kevdog you're a dogs b****cks
Many thanks

---

