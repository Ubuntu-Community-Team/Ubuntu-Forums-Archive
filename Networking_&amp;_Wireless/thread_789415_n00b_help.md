---
title: "n00b help"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by Snappo on 2008-05-10
Could someone like re-write the start of this to say the files are on my desktop as i have no net on it yet but i can move the files via cd.

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

I have a Atheros ar5005g so i'm hoping it works :D

---

### Post by Snappo on 2008-05-10
please help/bump

---

### Post by Snappo on 2008-05-11
bump

---

### Post by ugm6hr on 2008-05-11
Your post doesn't make sense.

And that thread is for AR5007, not 5005.

---

### Post by Snappo on 2008-05-11
> **ugm6hr said:**
> Your post doesn't make sense.

And that thread is for AR5007, not 5005.

There is nothing for the for the ar5005 so i am going with the closest.

I need the script rewritten as if the files were already on my desktop as i am not able to download them with the command because i am still trying to setup my net but i have moved the files there via cd.

---

### Post by mbarak on 2008-05-11
since the files are already on your desktop you just have the skip all the "wget" parts and run everything else from the directory where you downloaded those file
i.e. cd into your desktop folder

cd ~/Desktop

---

### Post by Snappo on 2008-05-11
> **mbarak said:**
> since the files are already on your desktop you just have the skip all the "wget" parts and run everything else from the directory where you downloaded those file
i.e. cd into your desktop folder

cd ~/Desktop

Thats what i was doing up till here then i got lost

6. Install the Windows drivers (using ndiswrapper):
Code:

pushd */ar5007eg/
sudo ndiswrapper -i net5211.inf
popd

7. Make sure ndiswrapper loads up every time we start Linux:
Code:

sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules

---

### Post by ugm6hr on 2008-05-11
I would say that starting with a How-to for the wrong wifi card is probably not a good idea.

I only briefly looked through that post, and it seems to use ndiswrapper, which may work for your 5005 card, except that the Windows drivers would have to be the correct ones (i.e. not the ones suggested in that How-to).

I'm at a different computer, but I think the AR5005G works with madwifi.

I would suggest starting again, and giving the output from the following commands:
```
lspci
lshw -C network
```

---

### Post by mbarak on 2008-05-11
you should just need to enter those commands in the terminal
what does it say when you enter those commands?

---

### Post by Snappo on 2008-05-11
> **mbarak said:**
> you should just need to enter those commands in the terminal
what does it say when you enter those commands?

It can't locate ndiswrapper or something along them lines.

As for mad wifi i have already tried that.

---

### Post by mbarak on 2008-05-12
did you run this command?

sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential
you need the kernel headers and the building programs to build ndiswrapper from source
since you have no internet right now, first type in "uname -r" in the terminal and go to packages.ubuntu.com and download the packages "linux-headers-(the result of uname -r) and build-essentials and all their dependencies. install them on your system, reinstall ndiswrapper (make && sudo make install)  and try again. (you might want to look into apt-zip to do all that)

also, why are you trying to build ndiswrapper from source? ubuntu has binary packages in their repositories and can save you all this trouble.
search for "ndiswrapper" at packages.ubuntu.com and download it and all dependencies.
this way you skip the whole part about compiling ndiswrapper

also i'd like to revisit the comment made by: ugm6hr

> 
I would say that starting with a How-to for the wrong wifi card is probably not a good idea.

I only briefly looked through that post, and it seems to use ndiswrapper, which may work for your 5005 card, except that the Windows drivers would have to be the correct ones (i.e. not the ones suggested in that How-to).

I'm at a different computer, but I think the AR5005G works with madwifi.

I would suggest starting again, and giving the output from the following commands:
 	Code:
 	lspci
lshw -C network 


You really should follow his advice

---

### Post by Snappo on 2008-05-12
> **mbarak said:**
> did you run this command?

sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential
you need the kernel headers and the building programs to build ndiswrapper from source
since you have no internet right now, first type in "uname -r" in the terminal and go to packages.ubuntu.com and download the packages "linux-headers-(the result of uname -r) and build-essentials and all their dependencies. install them on your system, reinstall ndiswrapper (make && sudo make install)  and try again. (you might want to look into apt-zip to do all that)

also, why are you trying to build ndiswrapper from source? ubuntu has binary packages in their repositories and can save you all this trouble.
search for "ndiswrapper" at packages.ubuntu.com and download it and all dependencies.
this way you skip the whole part about compiling ndiswrapper

also i'd like to revisit the comment made by: ugm6hr



You really should follow his advice

I have searched forums and that is the closest to the model i have. I don't have a clue how to build drivers so it wouldn't matter anyway all i can do is try.

---

### Post by Snappo on 2008-05-12
i got you guys soome results

> snappo@snappo-linux:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)
snappo@snappo-linux:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:00:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:d0:89:90:b0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=128 maxlatency=8 mingnt=3 module=via_rhine multicast=yes



---

### Post by mbarak on 2008-05-12
After doing a quick search on these forums for your chipset it seems that your card should work out of the box. Perhaps you didn't enable restricted drivers for it (System > Administration > Hardware)
Or perhaps your network settings have been messed up somewhere?

If you still insist on using ndiswrapper:
I'm assuming you're running hardy...
To install ndiswrapper:
Download these packages and put them on your computer:
[http://packages.ubuntu.com/hardy/ndiswrapper-common](http://packages.ubuntu.com/hardy/ndiswrapper-common)
[http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9)
install them by just double-clicking or running this in the download directory:
```
dpkg -i ndiswrapper*
```

then find a windows driver for this chipset: AR5212/AR5213 and install it with ndiswrapper

---

### Post by Snappo on 2008-05-13
> **mbarak said:**
> After doing a quick search on these forums for your chipset it seems that your card should work out of the box. Perhaps you didn't enable restricted drivers for it (System > Administration > Hardware)
Or perhaps your network settings have been messed up somewhere?

If you still insist on using ndiswrapper:
I'm assuming you're running hardy...
To install ndiswrapper:
Download these packages and put them on your computer:
[http://packages.ubuntu.com/hardy/ndiswrapper-common](http://packages.ubuntu.com/hardy/ndiswrapper-common)
[http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9)
install them by just double-clicking or running this in the download directory:
```
dpkg -i ndiswrapper*
```

then find a windows driver for this chipset: AR5212/AR5213 and install it with ndiswrapper


I see two restricted drivers enabled but i don't have a clue how to use it?

---

### Post by ugm6hr on 2008-05-13
I think you may in trouble with that chipset...

This suggests that NM is the problem: [http://ubuntuforums.org/showthread.php?t=728910](http://ubuntuforums.org/showthread.php?t=728910)

This guy hadn't turned the device on: [http://ubuntuforums.org/showthread.php?t=722798](http://ubuntuforums.org/showthread.php?t=722798)

This suggets almost no one can get it to work: [http://ubuntuforums.org/showthread.php?t=691094](http://ubuntuforums.org/showthread.php?t=691094)

Not sure what else to suggest.  Sorry.

---

### Post by mbarak on 2008-05-13
maybe if you disable the driver for your wireless card in the restricted drivers manager (something about atheros perhaps?) restart, and re-enable it and restart?

---

### Post by Snappo on 2008-05-13
> **mbarak said:**
> maybe if you disable the driver for your wireless card in the restricted drivers manager (something about atheros perhaps?) restart, and re-enable it and restart?

tried that no results

---

### Post by mbarak on 2008-05-13
i'm sorry i can't help you. maybe if you install the windows driver with ndiswrapper, or maybe if you re-install ubuntu hardy? i honestly don't know what's wrong

---

### Post by Snappo on 2008-05-14
I'm at work atm with my laptop on a wired network using ubuntu (i love it) so is there anything i can download to help me get my wifi network working for home?

---

### Post by mbarak on 2008-05-14
i would say to disable and re-enable your restricted drivers just to make sure it got downloaded properly
if the drivers that come with ubuntu don't work, install ndiswrapper
```
sudo apt-get install ndisgtk
```
this is a graphical front-end to ndiswrapper - might make things a little easier for you
download the drivers for xp from your wireless card's company's website and install them with ndisgtk (i think you go to system>administration>windows wireless drivers - or something along those lines, or run gksudo ndisgtk)

---

### Post by Snappo on 2008-05-14
There is no direct switch to turn it on but while i'm in windows i use a key combination to start the wifi. I'm going to try out what you done so i will get back to you then.

---

### Post by mbarak on 2008-05-14
to turn it on or off you just check or uncheck the box
and, what do you man by "key combination" ? you mean the password to authenticate yourself with your wireless router (wep key)?

if that is the case then perhaps your wireless was working all along, but you never entered this key into the NetworkManager
before install the ndiswrapper driver, click on the network manager applet (the two screens on the top right) if it asks you for a password make sure its WEP 128bit. if it asks again change that to WEP 64/128 hex and enter that long string of letters and numbers (the key combination) and, that should work

---

### Post by Snappo on 2008-05-14
> **mbarak said:**
> to turn it on or off you just check or uncheck the box
and, what do you man by "key combination" ? you mean the password to authenticate yourself with your wireless router (wep key)?

if that is the case then perhaps your wireless was working all along, but you never entered this key into the NetworkManager
before install the ndiswrapper driver, click on the network manager applet (the two screens on the top right) if it asks you for a password make sure its WEP 128bit. if it asks again change that to WEP 64/128 hex and enter that long string of letters and numbers (the key combination) and, that should work

No i mean the key comination to enabled my wifi like a hardware button would turn on the wifi. The network i use is not encrypted and i tried what you said and no results i am really starting to loose hope. :(

---

### Post by mbarak on 2008-05-14
ooooooooooo i understand what you mean now
your wifi card is built into your laptop you have to hit a special combination on your laptop to turn on the radar - right?

did you try using that same combination?
try this: run 
```
sudo udevmonitor
```
type the key combo and see if anything happens
if you get a message, that means the system recognizes you are trying to turn on the radar
if nothing happens you have to turn on the radar some other way
*i think there is a program out there to do exactly that
what is your laptop model?

---

### Post by Snappo on 2008-05-14
> **mbarak said:**
> ooooooooooo i understand what you mean now
your wifi card is built into your laptop you have to hit a special combination on your laptop to turn on the radar - right?

did you try using that same combination?
try this: run 
```
sudo udevmonitor
```
type the key combo and see if anything happens
if you get a message, that means the system recognizes you are trying to turn on the radar
if nothing happens you have to turn on the radar some other way
*i think there is a program out there to do exactly that
what is your laptop model?

Packard bell easynote r1

---

### Post by mbarak on 2008-05-14
when you pressed the key combination to turn on your wifi radar - did anything happen?
(i think the key combo is fn + f1)

---

### Post by Snappo on 2008-05-14
> **mbarak said:**
> when you pressed the key combination to turn on your wifi radar - did anything happen?
(i think the key combo is fn + f1)

Nothing happens

---

### Post by mbarak on 2008-05-14
even while running sudo udevmonitor  ??
then perhaps the problem is that your laptop has a software switch i.e. - it uses software to turn on your wireless card

---

### Post by mbarak on 2008-05-14
Alright, i think i know how to fix your little problem.

follow these steps:

install kernel headers
```
sudo apt-get install linux-headers-$(uname -r)
```

Download and install rfswitch 
```

wget http://internap.dl.sourceforge.net/sourceforge/rfswitch/rfswitch-1.3.tar.gz
tar -xzf rfswitch-1.3.tar.gz
cd rfswitch-1.3
sudo make install

```###run dmesg

Load the driver
```
sudo modprobe pbe5
```turn on the wifi radar:
press your key combo (fn+f1 i think)
run dmesg
if it sais something about turning on wifi, skip the following
if it sais something about unknown key combo, do the following
```
sudo bash -c "echo 1 > /proc/pbe5/radio"
```###run dmesg

if it's different, and it sais something about turning on your radio (i have no idea what it will say, i don't have your laptop :P)
uumm...come to think of it, even if it doesn't say anything, in network manager turn off wireless, turn off network - then turn them both back on. if your wireless if working PERFECT :p we'll find a way to make it automatic
if not then, i'm really sorry i don't know what else to do
uninstall rfswitch with these commands in the rfswitch source directory:
```
sudo rmmod pbe5
sudo make uninstall
```

---

### Post by Snappo on 2008-05-14
> **mbarak said:**
> Alright, i think i know how to fix your little problem.

follow these steps:

Download and install rfswitch 
```

wget http://internap.dl.sourceforge.net/sourceforge/rfswitch/rfswitch-1.3.tar.gz
tar -xzf rfswitch-1.3.tar.gz
cd rfswitch-1.3
sudo make install

```###run dmesg

Load the driver
```
sudo modprobe pbe5
```
turn on the wifi radar:
press your key combo (fn+f1 i think)
run dmesg
if it sais something about turning on wifi, skip the following
if it sais something about unknown key combo, do the following
```
sudo bash -c "echo 1 > /proc/pbe5/radio"
```###run dmesg

if it's different, and it sais something about turning on your radio (i have no idea what it will say, i don't have your laptop :P)
uumm...come to think of it, even if it doesn't say anything, in network manager turn off wireless, turn off network - then turn them both back on. if your wireless if working PERFECT :p we'll find a way to make it automatic
if not then, i'm really sorry i don't know what else to do
uninstall rfswitch with these commands in the rfswitch source directory:
```
sudo rmmod pbe5
sudo make uninstall
```

Thank you very much! are you sure this will work for my laptop model/wifi I will check it once i get a reply :P

---

### Post by mbarak on 2008-05-14
i have no idea, but it really won't hurt to try
if it makes you feel better see this page:
[https://wiki.ubuntu.com/LaptopTestingTeam/PackardBellR1100](https://wiki.ubuntu.com/LaptopTestingTeam/PackardBellR1100)

Oops, sorry i forgot something
Install your kernel headers (to compile the rfswitch module) before doing anything
```
sudo apt-get install linux-headers-$(uname -r)
```
i'll edit the post above also

---

### Post by Snappo on 2008-05-14
> **mbarak said:**
> i have no idea, but it really won't hurt to try
if it makes you feel better see this page:
[https://wiki.ubuntu.com/LaptopTestingTeam/PackardBellR1100](https://wiki.ubuntu.com/LaptopTestingTeam/PackardBellR1100)

Oops, sorry i forgot something
Install your kernel headers (to compile the rfswitch module) before doing anything
```
**sudo apt-get install linux-headers-$(uname -r)**
```
i'll edit the post above also

When i run linux i can't use the internet because i take apt-get means it connects to the internet?

---

### Post by mbarak on 2008-05-14
o, in that case
run uname -r in the terminal, copy the result
search for on the website package.ubuntu.com:
linux-headers-resultof-(uname -r)
download it and all dependencies
then download rfswitch using the link above

to install the .deb files from the website, just double click on them

Edit: that is...do all this from where/when you are able to use the internet

---

### Post by Snappo on 2008-05-14
It didn't work :( i think we are back at square one with the drivers

---

### Post by Snappo on 2008-05-15
bump

---

### Post by Snappo on 2008-05-15
bump

---

### Post by mbarak on 2008-05-15
sorry, do you remember what dmesg said after loading the module and trying to turn the radio on?
the messages from syslog might help also
tail /var/log/syslog

---

### Post by Snappo on 2008-05-15
> **mbarak said:**
> sorry, do you remember what dmesg said after loading the module and trying to turn the radio on?
the messages from syslog might help also
tail /var/log/syslog

It said the drivers weren't installed or missing hardware.

---

### Post by mbarak on 2008-05-15
are you sure you loaded the pbe5 driver?
```
sudo modprobe pbe5
```

Try running
```
sudo depmod -a
```
and then loading the pbe5 driver
```
sudo modprobe pbe5
```
???

---

### Post by Snappo on 2008-05-16
> **mbarak said:**
> are you sure you loaded the pbe5 driver?
```
sudo modprobe pbe5
```

Try running
```
sudo depmod -a
```
and then loading the pbe5 driver
```
sudo modprobe pbe5
```
???

nonono doesn't work i don't think the drivers are setup for wifi or something...

---

### Post by mbarak on 2008-05-16
Did you install a windows driver through ndiswrapper? if so you should uninstall it first
i think it's:
```

sudo rm -r /etc/ndiswrapper
sudo rmmod ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper

```
here's another idea after you remove the ndiswrapper drivers
try these commands
```

sudo modprobe -r ath_rate_sample ath_hal ath_pci pbe5
sudo modprove pbe5
sudo bash -c "echo 1> /proc/pbe5/radio"
sudo modprobe ath_pci

```what it's doing is removing the atheros madwifi driver, adding the pbe5 driver, then adding the madwifi driver
perhaps...hopefully...that'll work

---

### Post by Snappo on 2008-05-16
> **mbarak said:**
> Did you install a windows driver through ndiswrapper? if so you should uninstall it first
i think it's:
```

sudo rm -r /etc/ndiswrapper
sudo rmmod ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper

```

then try these commands
```

sudo modprobe -r ath_rate_sample ath_hal ath_pci pbe5
sudo modprove pbe5
sudo bash -c "echo 1> /proc/pbe5/radio"
sudo modprobe ath_pci

```
what it's doing is removing the atheros madwifi driver, adding the pbe5 driver, then adding the madwifi driver
perhaps...hopefully...that'll work

I had to reinstall ubuntu ndiswrapper messed it up.

---

### Post by mbarak on 2008-05-16
ndiswrapper messed it up? that sounds very weird :S
does your wireless work now?

**if not try the above commands anyways (without the ndiswrapper part)

---

### Post by Snappo on 2008-05-16
> **mbarak said:**
> ndiswrapper messed it up? that sounds very weird :S
does your wireless work now?

**if not try the above commands anyways (without the ndiswrapper part)

seems my wifi driver shows different in linux

> 

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

snappo@Snappo-Linux:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)
snappo@Snappo-Linux:~$ 

---

### Post by mbarak on 2008-05-17
> 00:06.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
Nope, still the same one.
If your wireless still doesn't work - try installing rfswitch driver again

---

### Post by Snappo on 2008-05-17
> **mbarak said:**
> Nope, still the same one.
If your wireless still doesn't work - try installing rfswitch driver again

But look lol.... there are restricted drivers enabled but no wifi manager and i was reading i need to download it via the package monitor but i don't have internet to do that.

The rfswtich went fine and i tested the fn keey to disable sound etc and it all works so that couldn't be the problem. I also run a command to search wireless networks and i got an error that no wireless hardware is there.

---

### Post by mbarak on 2008-05-17
The purpose of rfswitch is that to turn on the wireless you need a software driver because your laptop doesn't have a physical switch.  The problem is that the driver is for windows only. The rfswitch driver is trying to replace that part of the driver i.e. - just to turn it on, not to actually use it (that's for madwifi)
you can get the madwifi driver from this package:
[http://packages.ubuntu.com/hardy/linux-restricted-modules-2.6.24-16-generic](http://packages.ubuntu.com/hardy/linux-restricted-modules-2.6.24-16-generic)
download that package and every package it depends on. then install them on your ubuntu system
an easy way to do this is to put them all in a folder, then go to system>administration> synaptic
and click file>add downloaded packages
once the packages are installed enable the restricted driver for your wireless card (you might have to restart)
if it STILL doesn't work - install the rfswitch driver, turn it on (like i showed you before) and...well hopefully that works
really hope it works - computers aren't nearly as nice (and, ubuntu especially) without the internet :p

---

### Post by Snappo on 2008-05-17
> **mbarak said:**
> The purpose of rfswitch is that to turn on the wireless you need a software driver because your laptop doesn't have a physical switch.  The problem is that the driver is for windows only. The rfswitch driver is trying to replace that part of the driver i.e. - just to turn it on, not to actually use it (that's for madwifi)
you can get the madwifi driver from this package:
[http://packages.ubuntu.com/hardy/linux-restricted-modules-2.6.24-16-generic](http://packages.ubuntu.com/hardy/linux-restricted-modules-2.6.24-16-generic)
download that package and every package it depends on. then install them on your ubuntu system
an easy way to do this is to put them all in a folder, then go to system>administration> synaptic
and click file>add downloaded packages
once the packages are installed enable the restricted driver for your wireless card (you might have to restart)
if it STILL doesn't work - install the rfswitch driver, turn it on (like i showed you before) and...well hopefully that works
really hope it works - computers aren't nearly as nice (and, ubuntu especially) without the internet :p


haha thanks i will give it another shot :) oh and while we are on this subject my gfx is not supported and i am running on a very bad/ugly resolution and no one can help me with it :(

---

### Post by mbarak on 2008-05-18
for your graphics try running
gksu displayconfig-gtk
under the graphics card tab - make sure you are using the 'via' driver
other than that, I don't know enough to help you with this
did you try changing the resolution in system>preferences>screen resolution

---

### Post by Snappo on 2008-05-18
> **mbarak said:**
> for your graphics try running
gksu displayconfig-gtk
under the graphics card tab - make sure you are using the 'via' driver
other than that, I don't know enough to help you with this
did you try changing the resolution in system>preferences>screen resolution

Yes but it won't go high it is about 800x200 or something

---

### Post by mbarak on 2008-05-21
for your wireless try this:

check in your bios for disable wireless, or disable mini-pci and make sure they're disablred

if that doesn't work try this:
```

sudo rmmod ath_rate_sample ath_hal ath_pci
sudo modprobe ath_pci rfkill = 0

```if that doesn't work - try booting your computer with acpi=force
apparently, this will fix your wireless, but break your usb :S not the best of solutions but...a solution none-the-less

to boot in acpi=force mode 

edit the file /boot/grub/menu.lst
```
gksudo gedit /boot/grub/menu.lst
```look for this line
```
# kopt=root=UUID=077f10a6-a284-416e-a6f3-b474de14fe0e ro

```and add acpi=force to the end
```
# kopt=root=UUID=077f10a6-a284-416e-a6f3-b474de14fe0e ro acpi=force

```

then run this command:
```
sudo update-grub
```

---

