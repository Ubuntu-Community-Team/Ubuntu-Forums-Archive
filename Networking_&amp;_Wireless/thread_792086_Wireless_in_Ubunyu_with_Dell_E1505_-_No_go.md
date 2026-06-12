---
title: "Wireless in Ubunyu with Dell E1505 - No go"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by Eman1955 on 2008-05-12
The help section in Ubuntu states how easy it is now to set up wireless and fly through the internet. As usual, not for me the first time around. I'm new to Ubuntu, just dropped Xandros and want to totally get rid of Windoze.

Can anyone give me explicit instructions to get me on the internet in Ubuntu?

whats the best book out there on Ubuntu?

E

---

### Post by Ayuthia on 2008-05-12
Welcome to the Community!

Can you post the results of your lspci -nn information.  This needs to be done from the Terminal.  It will help us figure out your wireless card and point you to a guide that can help.

---

### Post by Eman1955 on 2008-05-13
Can you post the results of your lspci -nn information. This needs to be done from the Terminal. It will help us figure out your wireless card and point you to a guide that can help.

bob@bob-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M52 [Mobility Radeon X1300] [1002:7149]
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
bob@bob-laptop:~$

---

### Post by Ayuthia on 2008-05-13
> **Eman1955 said:**
> 
0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
bob@bob-laptop:~$
This is your wireless card.  Here is a [link]("http://ubuntuforums.org/showthread.php?t=779754") on how you can get it installed. Or if you have a working internet connection, you can try and find the Hardware Drivers Manager.  I think it is under System->Administration.  I could be wrong though.  I am using KDE instead of Gnome.

Hope that helps.

---

### Post by Eman1955 on 2008-05-14
OK, I'll give this a try.  I normally don't give up but I'm ready to give this up and go back to Xandros, at least everything worked but they were slow in updates.

S

---

### Post by Eman1955 on 2008-05-14
"I could be wrong though.  I am using KDE instead of Gnome."

How does one choose KDE over Gnome?  I know there are xxx flavors out there, just curious which is better than the next.

Thanks,

S

---

### Post by Ayuthia on 2008-05-14
> **Eman1955 said:**
> "I could be wrong though.  I am using KDE instead of Gnome."

How does one choose KDE over Gnome?  I know there are xxx flavors out there, just curious which is better than the next.

Thanks,

SThere is no real answer to this question.  There are so many different reasons to pick one over another.  Lots of people like Gnome because of the ease of use.  People like KDE because it is similar to Windows in look and feel so it is easier to adjust.  Developers like KDE because of the development packages that are available.  Some people like things to be lightweight so they go with Xubuntu (Xfce).  

One easy way to test out which desktop manager is to check out Knoppix.  It is a LiveCD and it provides various desktop managers to try out.  Of course it is a Debian based product so you will run into the wireless thing there also.

---

### Post by Ayuthia on 2008-05-14
Out of curiosity, what have you done so far in your wireless journey with Ubuntu?

---

### Post by Eman1955 on 2008-05-14
ok here is the lastest try and I thought it was going to work because there were no errors.  Except in administration -> Networks the wireless setup option was totally gone!

5/14/08

Requirements

You need two things:

    *  A kernel >= 2.6.21 (limited support for 2.6.21)
    * Your kernel headers installed 

Please be very sure you have your kernel headers installed before reporting any sort of build issues with this package. This usually will mean having this symlink point to a valid directory with kernel headers in it:

/lib/modules/`uname -r`/build

The exception to this is if you are building the package targeting a kernel you are not running. Users doing this should read the Building for external kernels section.

Additionally, the kernel you're building for needs a valid ".config" file, if it isn't present compat will assume you have PCI, USB and PCMCIA built into your kernel and if not, fail building.

Where to download

You can download this package here:

[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

This package is updated daily. It reflects the latest on wireless-testing.git tree.

Directly downloading the tarball

We have enabled anti-hotlinking to the compat-wireless-2.6.tar.bz2 tarball. This ensures users directed to this tarball from random tutorials online will hopefully read this page. Anti-hotlinking prevents users from accessing the tarball directly before seeing this page. In summary, you cannot directly (for example using wget) this tarball before having viewed this introductory page. If you try to do so you will be redirected here. You can, however, directly download a dated version of the tarball, for example compat-wireless-2008-03-25.tar.bz2.

You can find the latest dated tarball in the compat-wireless-2.6 download directory.

Archive of compat-wireless-2.6 tarballs

linuxwireless.org only hosts the latest dated compat-wireless-2.6 tarball but if you would like an older release please check the compat-wireless-2.6 archive, which is hosted by Orbit.

Building and installing

Extract:

Extract the content of the package:  (Downloaded 5/14/08:  compat-wireless-2.6.tar.bz2)

tar jxvf compat-wireless-$(date -I).tar.bz2

Build:

Build the latest Linux wireless subsystem:

cd compat-wireless-$(date -I)
make

Install:

We use the updates/ directory so your distribution's drivers are left intact.

sudo make install

Uninstall:

This nukes our changes to updates/ so you can go back to using your distribution's supported drivers.

sudo make uninstall

Unload:

Since you might be replacing your old mac80211 drivers you should first try to unload all existing mac80211 and related drivers. Note also that broadcom, zydas, and atheros devices have old legacy drivers which you need to be sure are removed first. We provide a mechanism to unload all old and legacy drivers first so you should run to be sure:

sudo make unload

Load:

If you know what module you need you can simply load the module using modprobe. If you simply are not sure you can use:

sudo make load

Note that this will run make unload first, just in case you forgot. This unloads your old wireless subsystem drivers and loads the new shiny ones. For example if ipw3945 and its proprietary daemon are found it'll be stopped and the module unloaded and then iwl3945 will be loaded. If you are simply upgrading a mac80211 driver this will unload the old one and the old mac80211 drivers and load the new ones.

Drivers

Here is the list of all the drivers we support in this package.

Drivers

adm8211

at76_usb

ath5k

b43

b43legacy

iwl3945

iwl4965

ipw2100

ipw2200

ub8xxx

libertas_cs

p54_pci

p54_usb

rndis_wlan

rt2400pci

rt2400pci

rt2500pci

rt2500usb

rt61pci

rt73usb

rtl8180

rtl8187

zd1211rw

Known issues

    * Strange wireless device names: 

Lets clarify device names first. Regularly you should only see two new device names:

    * wmaster0
    * wlan0 

The wmaster0 device is what we call the master device. The master device is an internal master device used only by mac80211. It should be ignored by users. If possible we will try to hide it from users later.

On distribution releases with old udev rules you may end up with strange network device names, for example, wlan0_rename. You may also end up with master device names such as eth3, when this was actually intended to be named wmaster0. This happens because master interface has the same MAC address as the real interface, and it is created first. The old udev rule, which keys on the MAC addres, may rename it to device names like eth3, for example. Then the real interface is created, udev sees that it has already renamed an interface with that MAC and gives it the wlan0_rename name.

If you delete the generated rename rules, it should create the correct ones on the next boot. Alternately, you could add:

ATTRS{type}="1"

selector to your current rule. Debian puts these autogenerated udev rules in /etc/udev/rules.d/z25_persistent-net.rules. Other distributions may vary slightly.

    *

      nl80211: 

Kernels <= 2.6.22 now get nl80211 support, however, genl_multicast_group won't work. This compatibility cannot be extended to older kernels as the struct genl_family was extended on 2.6.23 to add the struct list_head mcast_groups. Right now nothing is using this though so you should be able to use the existing nl80211 userspace applications.

    * b43: 

b43 and b43legacy now load. Since there was an old softmac broadcom driver we provide a load script for this driver. To load the new generation drivers (b43 and b43legacy) you can run:

sudo b43load b43

To revert back to bcm43xx you can run:

sudo b43load bcm43xx

    *

      MadWifi: 

If MadWifi is present the build system will detect this and disable it. It does this by simply renaming ath_pci.ko to ath_pci.ko.ignore. This lets us disable the MadWifi driver without blacklisting it which could cause issues with users later. If you would like to enable MadWifi at a later time and disable ath5k you can run:

sudo athload madwifi

To revert back to ath5k you can run:

sudo athload ath5k

Why was this work done?

It was done for users or developers stuck on older kernels that want to help test or patch wireless work. Additionally if you're on a recent kernel this lets you get the latest and greatest wireless-2.6 git work without much effort. This may mean new drivers for some users. Last but not least we hope this will encourage vendors and developers to post patches upstream first rather than forking or maintaining their own mac80211 releases with their own patches for their own drivers.

    * prism54, p54pci, p54usb? 

We don't provide prism54 in this package because distributions already provide it. p54 is its replacement. prism54 works only with full MAC cards. p54 works with both full MAC and soft MAC cards. p54 just doesn't yet support ad-hoc, and AP mode. Should prism54 get any new updates we'll start packaging it here.

    * What about net/ieee80211/softmac/ and their drivers? 

Documentation/feature-removal-schedule.txt is being updated to mark this for removal. Here is the relevant text:

What:  iee80211 softmac wireless networking component
When:  2.6.26 (or after removal of bcm43xx and port of zd1211rw to mac80211)
Files: net/ieee80211/softmac
Why:   No in-kernel drivers will depend on it any longer.
Who:   John W. Linville <linville@tuxdriver.com>

    * Firmware: 

If your driver needs firmware please be sure to check the driver page for that driver here:

[http://linuxwireless.org/en/users/Driver](http://linuxwireless.org/en/users/Driver)

What's the difference between compat-wireless-2.6 and John Linville's tree?

This package is based on John's tree, we just add compatibility support for older kernels.

---

### Post by Ayuthia on 2008-05-14
Wow!  I have not ever tried that route with my wireless yet.  The 4311 rev 01 card should just work if you install b43-fwcutter.  All you have to do if you have a working internet connection is either go into Synaptic/Adept and install b43-fwcutter or else you can go to the Terminal and type:
```
sudo aptitude install b43-fwcutter
```You then let the computer find the firmware for you.

---

### Post by Eman1955 on 2008-05-15
nope, didn't work.
I'm out of options.
Thanks
S

---

### Post by Eman1955 on 2008-05-15
the system cannot find the file b43-fwcutter.  I made sure I was in the correct folder.
I did a complete search on the computer and it was not found.
Tel me now about my ignorance.

---

### Post by Eman1955 on 2008-05-15
Well I reloaded the system as I couldn't get a wireless connection to show any longer and configure.  I think I messed it up good.

How do these instructions look for wireless configuration?
[http://www.linuxwireless.org/en/users/Drivers/b43#b43andb43legacy](http://www.linuxwireless.org/en/users/Drivers/b43#b43andb43legacy)

---

### Post by Ayuthia on 2008-05-15
> **Eman1955 said:**
> Well I reloaded the system as I couldn't get a wireless connection to show any longer and configure.  I think I messed it up good.

How do these instructions look for wireless configuration?
[http://www.linuxwireless.org/en/users/Drivers/b43#b43andb43legacy](http://www.linuxwireless.org/en/users/Drivers/b43#b43andb43legacy)The instructions look fine.  The only thing that I will mention is that if you don't have build-essential installed, you will not be able to compile the b43-fwcutter.

b43-fwcutter should be in the installation CD.  To add it from the Terminal:
```
sudo apt-cdrom add
```It will ask you for the CD.  Insert it and it will be added.  Then:
```
sudo apt-get update
```will load the package lists into the system.
```
sudo apt-get install b43-fwcutter
```It will install the package and then will ask you if you want to have it find the firmware for you.  If you DO have an internet connection, say yes and it will install it for you.  

If you do NOT have a working internet connection, make sure that you say no or cancel.  You will need to download the firmware and place it in your home directory.  Here are the files that you need:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

Once they are in your home directory, go to the Terminal and do the following:
```
cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy

```

That should do it.  It is very similar to the link that you just provided.  The difference is that this one will also load the b43legacy drivers also.  This is the way that Ubuntu does it.  The information above is based on their install script that comes with b43-fwcutter.

---

### Post by jwm93k on 2008-05-15
Greetings. I had an Issue with DELL 530 laptop on Windows. It seems the DELL wireless card has a power option that if not set correctly will cause a lag, hang, or no connect at all. This new power option is set to default, and only works with new wireless routers. In Windows you go to the properties of the network card, click on configure, and de-select default. You also need to move the min-max slider to the min side and then back to the max side. Then I could connect to the internet. Is there a power setting in Ubuntu for wireless cards? Many Dell windows laptops have reported this problem. I expect there is a similar effect and setting in the Ubuntu world. If there is a power setting option somewhere in Ubuntu, it may help some of the Ubuntu Dell Laptop owners connect to the internet.

---

### Post by Eman1955 on 2008-05-16
Thanks for hanging in there with me Ayuthia.  It works!
Thank you, thank you, thank you!
What about a firewall and anitvirus?  I didn't see them (yet).

Thanks again!

[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)

---

### Post by Ayuthia on 2008-05-16
> **Eman1955 said:**
> Thanks for hanging in there with me Ayuthia.  It works!
Thank you, thank you, thank you!
What about a firewall and anitvirus?  I didn't see them (yet).

Thanks again!

[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)
I am not an expert on firewalls, but I have used Firestarter (you should be able to find this in Synaptic/Adept).

As for antivirus, I have used AVG (free version).  It is only for 32-bit though.  Here is the link to the download:
[http://www.grisoft.cz/filedir/inst/avg75fld-r51-a1243.i386.deb](http://www.grisoft.cz/filedir/inst/avg75fld-r51-a1243.i386.deb)

If you want to do this from the Terminal:
```
cd
wget -c http://www.grisoft.cz/filedir/inst/avg75fld-r51-a1243.i386.deb
sudo dpkg -i avg75fld-r51-a1243.i386.deb
```

It is rare to find a virus in Linux, but it is better to be safe than sorry!

---

### Post by Eman1955 on 2008-05-16
The more popular Linux gets the more attention it will get from the evil of the world.

---

### Post by Eman1955 on 2008-05-16
Off to the Cubs game.  Talk later.

S

---

### Post by Ayuthia on 2008-05-16
> **Eman1955 said:**
> Off to the Cubs game.  Talk later.

S
After all I have helped you with, no invite to the game???  I am only in Madison!!! :)

Have fun!

---

