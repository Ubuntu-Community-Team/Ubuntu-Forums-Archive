---
title: "Wireless Setup Probs BCM4306 Dell 500m Inspiron"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by linuxitis on 2007-06-17
I downloaded Feisty yesterday and have been trying to configure wireless ever since.  I tried the ndiswrapper method from another post, but something appears to have gone amiss.  With the default install I had the problem of my network controller being disabled. Now it is worse--unclaimed. On the windows partition of the laptop, the wireless link was able to repair itself. That did not bring back this one.  Could anyone please help?  Many thanks.

 *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@01:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32
       resources: iomemory:fcffe000-fcffffff irq:11
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth1
       version: 81
       serial: 00:0b:db:9e:d4:eb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=192.168.1.5 latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:fcffd000-fcffdfff ioport:ecc0-ecff irq:11

---

### Post by kevdog on 2007-06-17
Ok, lets start with the basics, you are going to have to install wireless drivers for your card with ndiswrapper.  If you already have a previous version installed you will need to totally uninstall it.  Then download the tar.gz ndiswrapper source file from [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/)
Go to downloads and get the stable release.  This of course will need to be done on any other computer with a working internet connection.  I would place the tar.gz file on a USB stick and then move it over to ubuntu computer and place the tarball in ~/temp/ndiswrapper.

If you just installed ubuntu, you will need another package to compile source files (the ndiswrapper source files).  Since you do not have an internet connection, the build-essential package is found on the CD.  To install please on Ubuntu computer, place CD in drive.

Then at command line:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential.

Ill give you more later, I just dont want to overwhelm you with instructions at this point.  Its quite easy, but does involve a lot of commands.

---

### Post by linuxitis on 2007-06-17
Thank you. I do have a wired internet connection. I downloaded ndiswrapper-1.47.tar.gz per instruction; however it downloaded to desktop. is there a faster/better way to download compiler?

---

### Post by kevdog on 2007-06-17
Yes -- I saw you had a wired connection but assumed you didnt have an internet connection.

sudo aptitude install build-essential

Optional step:
Even though you put the ndiswrapper.tar.gz file on the desktop, when you unzip this file its going to make like 50 files or something.  I would move it from ~/Desktop to ~/temp/ndiswrapper.  We are going to do everything from command line anyway, so having it on the desktop isnt going to help us much anyway.

Can you post:
lsusb

---

### Post by linuxitis on 2007-06-17
Sorry to be such the noob that I am, but how do I move the archive from ~/Desktop to ~/temp/ndiswrapper?

Here is the output of lsusb:

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:00e1 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Thank you for your patience.

---

### Post by kevdog on 2007-06-17
Sorry Im a little lost too --

To answer your question:
mkdir ~/temp/ndiswrapper
cd ~/Desktop
mv ndiswraper*****.tar.gz ~/temp/ndiswrapper   (replace name of file -- HINT use the TAB button it autocompletes -- try it you will see what I mean -- type like ndis and then hit the TAB button).

What kind of linksys device are you using again??  Model number, name of device.

---

### Post by kevdog on 2007-06-17
Sorry my fault, please post:

lspci

Im getting multiple posts confused.

---

### Post by linuxitis on 2007-06-17
1. mkdir command returns: 

mkdir: cannot create directory `/home/dirk/temp/ndiswrapper': No such file or directory

2. Here is output of lspci:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
01:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

3. If by linksys device you mean wireless card, it is a Dell TrueMobile 1300 WLAN Mini-PCI Card.  Please let me know if meant something else.

---

### Post by kevdog on 2007-06-17
Ok try this then

mkdir ~/temp
mkdir ~/temp/ndiswrapper

Im trying to find the driver for you card.  As for you once you get the ndiswrapper.tar.gz file into the right directory;

cd ~/temp/ndiswrapper
tar -zxvf ndiswrapper****.tar.gz   <---Again substitute name of tar file

ls <---This will list a new directory called ndiswraper-1.4* (Again the output will tell you)

cd ndiswraper-1.4*

Then type
make distclean
make
sudo make install

Check if ndiswrapper was compiled and installed properly with
ndiswrapper -v

Please post the output from the above command!

---

### Post by kevdog on 2007-06-17
Two more things

Post output of:
lspci -n

This is going to help me find the driver of your card

Also

sudo aptitude install cabextract

---

### Post by linuxitis on 2007-06-17
1. Here is the output of ndiswrapper -v. it does not look particularly good. Note that I downloaded 1.47 as the latest stable version on the website. i will check again to make sure it is the latest.

module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

2. here is output of lspci -n:

00:00.0 0600: 8086:3580 (rev 02)
00:00.1 0880: 8086:3584 (rev 02)
00:00.3 0880: 8086:3585 (rev 02)
00:02.0 0300: 8086:3582 (rev 02)
00:02.1 0380: 8086:3582 (rev 02)
00:1d.0 0c03: 8086:24c2 (rev 01)
00:1d.1 0c03: 8086:24c4 (rev 01)
00:1d.2 0c03: 8086:24c7 (rev 01)
00:1d.7 0c03: 8086:24cd (rev 01)
00:1e.0 0604: 8086:2448 (rev 81)
00:1f.0 0601: 8086:24cc (rev 01)
00:1f.1 0101: 8086:24ca (rev 01)
00:1f.5 0401: 8086:24c5 (rev 01)
00:1f.6 0703: 8086:24c6 (rev 01)
01:01.0 0607: 1217:6972
01:03.0 0280: 14e4:4320 (rev 02)
01:08.0 0200: 8086:103d (rev 81)

3. cabextract installed.

---

### Post by kevdog on 2007-06-17
Did you have ndiswrapper installed before or tried to install ndiswrapper?  Usually this is the problem.  

Lets first uninstall what we did
cd ~/temp/ndiswrapper/ndiswrapper-1.4*
sudo make uninstall

Then we have to do the following:
sudo modprobe -r ndiswrapper

If you used synaptic to install ndiswrapper, use synaptice to uninstall ndiswrapper
Then type the following:
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

Ok now go back into directory
cd ~/temp/ndiswrapper/ndiswrapper-1.4*
make distclean
make
sudo make install

Check output and post: ndiswrapper -v

---

### Post by linuxitis on 2007-06-17
Here is the output of ndiswrapper -v now. (I did have to uninstall ndiswrapper-common and ndiswrapper-utils 1.9 before reinstalling.)

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586

---

### Post by linuxitis on 2007-06-17
Kevdog,

I don´t know if you are still there, but ndiswrapper site indicates the following two drivers might be good candidates. I am not sure how to figure out which one to use.

first one:

Card: Dell Truemobile 1300 minipci 54mbps

    *
      Chipset: Broadcom BCM4306
    *
      pciid: 14E4:4320
    *
      Driver: [http://ftp.us.dell.com/network/R94827.EXE](http://ftp.us.dell.com/network/R94827.EXE)
    *
      Other: Works with WEP and WPA with either CCMP/AES or TKIP ciphers. The INF file for this card specifies it should use 802.11b mode (upto 11Mbps) in Ad-Hoc mode. If you want to use 802.11g mode in Ad-Hoc mode, you need to change the setting IBSSGmode in the .conf files in the driver directory to 2.

Second one: 

#
Card: Dell Truemobile 1300 minipci

    *
      Chipset: Broadcom BCM4306
    *
      pciid: 0000:01:03.0
    *
      Driver: [ftp://ftp.us.dell.com/network/R83097.EXE](ftp://ftp.us.dell.com/network/R83097.EXE) (using bcmwl6a.inf)
    *
      Other: (Ubuntu) Problems listing the network configuration application at first, adding the interface manually to /etc/network/interfaces solved this and is now running perfectly.

Thanks again for your help.

---

### Post by kevdog on 2007-06-17
Im going to be away for about 4 hours, but the first link that you posted -- that the driver.  You will need the cabextract utility to extract the driver since the exe file is meant to run on windows.

---

### Post by linuxitis on 2007-06-17
Thanks. I will look for more info on cabextract.

---

### Post by linuxitis on 2007-06-17
I downloaded and extracted the first driver, not with cabextract, which did not work, but with unzip, which appeared to let me use ndiswrapper on the file bcml5.inf.  However, it appears that the network controller is still not working. It remains ¨unclaimed.¨

Here is what ndiswrapper -l returns:

bcmw15 : invalid driver!
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

Here is what lshw -C network returns: 

  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@01:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32
       resources: iomemory:fcffe000-fcffffff irq:11
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth1
       version: 81
       serial: 00:0b:db:9e:d4:eb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=192.168.1.5 latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:fcffd000-fcffdfff ioport:ecc0-ecff irq:11

Any thoughts?

---

### Post by kevdog on 2007-06-17
I think if you:

cd /etc/ndiswrapper
ls

you will see two directories or at least 2 things listed.

What I want you to do is to remove all the directories:

sudo rm -R *

If you do another:

ls

you should see nothing.

Then change to the directory where you extracted your drivers you told me about.
Do an 
ls

Make sure there are at least 2 files in the directory a .sys and .inf file.
If there are then

sudo ndiswrapper -i ****.inf   <---Substitute appropriate name

Then recheck with
ndiswrapper -l

Hopefully only one driver will then be listed.
Please post the results of the above.
We are making slow, but steady progress.

---

### Post by linuxitis on 2007-06-17
Sorry I missed your last post.  

I completed the last set of instructions and returned the following with sudo ndiswrapper -l:

bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

So it looks good. What should I do next?

---

### Post by kevdog on 2007-06-17
Great -- 

Just for your info we have compiled and installed ndiswrapper and then in the last step wrapped the windows driver inside of ndiswrapper.  We are now going to insert the ndiswrapper "driver" into the kernel

sudo depmod -a   <---Make sure no errors appear
sudo modprobe ndiswrapper

You can check if the module was loaded in the kernel by typing
dmesg
and looking for something stating driver was loaded.

To make module load at boot:
sudo ndiswrapper -m

Ill post another message in about 30 minutes, only one last step to do, I gotta run real quick!

---

### Post by linuxitis on 2007-06-17
Done. Thank you for hanging in there with me.

---

### Post by kevdog on 2007-06-17
Done ??

I can only hope that means you have completed the rest successfully.  Just for posterity I'll finish what I was going to say, even if it does no one any good.

Ndiswrapper creates an interface name wlan0 and assumes that your wireless card is connected to wlan0.
From what you posted earlier, Im not sure what your interface name was.  In feisty many are defaulting to eth0 or eth1.  From your earlier post, your wired connection was eth1, so I am assuming (possibly incorrectly) that your wireless connection is eth0.

We need to change this to make everything just work.

Backup your /etc/network/interfaces file:
sudo cp /etc/network/interfaces /etc/network/interfaces.original

Edit your /etc/network/interfaces file:
gksu gedit /etc/network/interfaces

I believe your file should be edited to the following:

auto lo
iface lo inet loopback

auto eth1
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


#2. We need to associate wlan0 physically with your card

Edit /etc/iftab

gksu gedit /etc/iftab

Depending on what your iftab file states, you need to change the old interface name to wlan0
In your case, do not change eth1.  This is your wired card.  If there is another interface such as eth0, change it to wlan0.  If there is nothing else, then dont worry about it, it will get autoconfigured later.

#3. If you are planning on using a graphical interface to connect (this is most applicable to notebooks that may connect to different networks --ie coffee shop, home LAN, friend's lan, school LAN), you may want to install network-manager-gnome (for Ubuntu) or knetworkmanager (for Kubuntu).  Here is an example of how to do this if you are using Ubuntu
sudo aptitude install network-manager-gnome

#4. This setup is only good for LANs that or either unencrypted (no WPA, or WEP) or using WEP (encryption). The WEP key can be set through the gnome network manager icon that appears by the clock if this is how your LAN is configured.  If your are using WPA encryption, yet one other package wpasupplicant needs to be installed and configured to use WPA.  Also, if a static IP address for your computer is desired, additional changes must be made to the /etc/network/interfaces file to set up your static IP address.  The above directions were assuming you were using dhcp in order to assign your local LAN address.

#5. Reboot your computer just to make sure everything will be set up properly.

---

### Post by linuxitis on 2007-06-17
You were right that I meant I had completed your prior instructions. When I read the interfaces file, the output was slightly different--no wlan:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback



auto eth1
iface eth1 inet dhcp


Should I continue with the additional steps?

---

### Post by linuxitis on 2007-06-17
I re-read your message. I believe what you meant was for me to edit the file to add the language on wlan0, so that is what I did. I also edited eth0 into wlan0 in the iftab file. I think I have the network manager app already.  Should I reboot?

---

### Post by kevdog on 2007-06-17
Yes you should add the wlan0 
FYI:  adding additional interfaces doesnt cause any harm, its just in the end my goal is always to have my computer run as lean as possible -- the computer will search for the interface, if it isnt found will move onto the next.  If the interface doesnt exist however, why have it listed in the interfaces file?  Anyway when trying to get things to run and for debugging purposes I often make several different interfaces file -- each name interfaces1, interfaces2, etc.  When I want to use one of the profiles I will simply copy for example interfaces2 to interfaces and then restart.

If you can please post your /etc/iftab file.  You can do this by doing:
more /etc/iftab
and then cutting and pasting into this forum.

What are your router requirements (WPA,WEP).  I believe this computer is a desktop??

---

### Post by linuxitis on 2007-06-17
Here is the output of more /etc/iftab:

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

wlan0 mac 00:90:4b:24:be:5e arp 1
eth1 mac 00:0b:db:9e:d4:eb arp 1

My router is a Verizon FIOS-issued router, WEP-enabled.  My computer is a laptop. A Dell Inspiron 500m.

Shall I reboot?

---

### Post by kevdog on 2007-06-17
Before rebooting just make sure you have network-manager-gnome installed
sudo aptitude install network-manager-gnome

If nothing is installed, then it is installed.

I dont have the most experience but WEP, but we will make it work. 

Reboot - but make sure you unplug your network cable.

---

### Post by linuxitis on 2007-06-17
OK. I rebooted, with cable unplugged (I am typing on desktop next to network-unplugged laptop).  

No networks were auto-detected. Do I need to do setup with Network Manager or other utility?

---

### Post by kevdog on 2007-06-17
Ok, here is where we unfortunately need to monkey around.  I hate this part

Post
ifconfig

also
iwlist wlan0 scanning

Hopefully that will give us something!

---

### Post by linuxitis on 2007-06-17
I think I managed to activate the antenna by hitting alt-F2, which is the activation key for the Dell 500m Inspiron.  I now see my wireless router when I use the manager utility.

Now the problem is remembering the WEP password. Verizon writes it on the modem itself, but sadly that WEP key is not working for me. 

I will try to sleep on it to remember the password.  At least I am seeing the network. 

I want to thank you again for your help. I really appreciate it.

---

