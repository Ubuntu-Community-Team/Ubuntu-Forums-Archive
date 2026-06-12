---
title: "Got wireless working, but won't work after a reboot"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by murphykieran on 2008-09-25
I installed Ubuntu on a laptop today and had a bit of trouble getting wireless to work.  I eventually found a solution via installing Windows drivers using something called ndiswrapper and a handy graphical tool call ndisgtk.  I did that and also edited something called a blacklist to prevent the computer from using other drivers for the wireless (I think).  After that, I rebooted, I went into the network setting program, it detected both my wireless router and also a wireless booster I installed for a PC in an area with a very weak signal.  I entered my WEP key and hey presto! it worked.  I loaded Firefox and had Internet access, yay!

However, after shutting down the laptop and restarting it, it's lost all internet and network access.  When I go into the network setting program, it's not detecting either the wireless network or the booster, and re-entering in the WEP key makes no difference.   I also tried reinstalling the Windows drivers via the ndisgtk tool, but it made no difference and tried a couple of reboots.

Any obvious reasons why my wireless was working and is now no longer functioning?  I can't even ping the wireless router.

---

### Post by pytheas22 on 2008-09-25
It sounds perhaps like the ndiswrapper module is not getting auto-loaded by the system.  You can easily fix that by typing once:
```

echo ndiswrapper | sudo tee -a /etc/modules
```

Does that resolve the issue?

If not, please reboot, and before doing anything else, run these commands and post the output here:
```

lsmod | grep ndis
sudo iwlist scan
lshw -C Network
dmesg | grep -e ndis -e wlan
```

---

### Post by willca on 2008-09-26
what card do you have?

lspci | grep Ethernet

---

### Post by murphykieran on 2008-09-26
> **pytheas22 said:**
> It sounds perhaps like the ndiswrapper module is not getting auto-loaded by the system.  You can easily fix that by typing once:
```

echo ndiswrapper | sudo tee -a /etc/modules
```

Does that resolve the issue?No, I tried that and rebooted and it's still not working.

Yesterday at one stage it was telling me that I had both a wlan0 and wlan0:avahi when I did an ifconfig command, now it's only listing the wlan0

The ndisgtk program for Windows wireless drivers is telling me I have net5211 installed and hardware is present.

> If not, please reboot, and before doing anything else, run these commands and post the output here:
```

lsmod | grep ndis
sudo iwlist scan
lshw -C Network
dmesg | grep -e ndis -e wlan
```

```
kieran@kieran-laptop:~$ lsmod | grep ndis
ndiswrapper           192920  0 
usbcore               146028  5 uvcvideo,ndiswrapper,ehci_hcd,uhci_hcd
kieran@kieran-laptop:~$ sudo iwlist scan
[sudo] password for kieran: 
lo        Interface doesn't support scanning.

wlan0     No scan results

kieran@kieran-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: b0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:15:af:e5:37:52
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,05/02/2007,5.3.0.45 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
kieran@kieran-laptop:~$ dmesg | grep -e ndis -e wlan
[   27.324040] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   27.782338] ndiswrapper: driver net5211 (,05/02/2007,5.3.0.45) loaded
[   27.782784] ndiswrapper (ZwClose:2227): closing handle 0xdf87d928 not implemented
[   29.306245] ndiswrapper: using IRQ 18
[   29.565087] wlan0: ethernet device 00:15:af:e5:37:52 using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   29.570799] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   29.652614] usbcore: registered new interface driver ndiswrapper
[   45.612579] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   92.536750] ndiswrapper (mp_reset:62): wlan0 is being reset
kieran@kieran-laptop:~$ 

```
As you can see, it also denies the existence of the ethernet connection, but that's a different problem, wireless is really what I want to get working.

---

### Post by pytheas22 on 2008-09-26
hmmm, very strange.  From the output you posted, it looks like ndiswrapper should be working and the interface up after a reboot.  But when you left-click on the Network Manager applet (top-right corner), you don't see an option for wireless networking at all?

What happens if you type:
```

sudo iwlist scan
```

(it should give you a list of wireless networks in range)?

---

### Post by murphykieran on 2008-09-26
> **pytheas22 said:**
> hmmm, very strange.  From the output you posted, it looks like ndiswrapper should be working and the interface up after a reboot.  But when you left-click on the Network Manager applet (top-right corner), you don't see an option for wireless networking at all?Do you mean the little icon of 2 computers in the system tray in the top right? On this PC here which is connected to the router via ethernet, I get a little box pops up with details about the connection.  On the laptop however, all I get is a "manual configuration" option and when I click it it brings up the "Network settings" program which allows me to setup the wireless, wep keys etc.  In the wireless settings for the wlan0 it's remembering the details from when I got it correctly setup yesterday - network name, password type, the actual wep password, etc. but if I click in the drop down menu for "network name", there's nothing listed as if it can't detect any networks, even though it was working fine for a while yesterday.

> What happens if you type:
```

sudo iwlist scan
```

(it should give you a list of wireless networks in range)?No, nothing.
```
wlan0 No scan results
```
It's very frustrating because I know it works with wireless because I successfully got it working for a while.  If I thought that wireless wouldn't work at all on it, I'd just reinstall Windows XP, but I'd love get it up and running with Ubuntu.

---

### Post by issih on 2008-09-26
I suspect you have that your problem is arising because ubuntu thinks it already has a driver that will work for your wireless card. This driver is being loaded, and is then stopping ndiswrapper from taking control of the hardware.

I suspect it will be a module called ath...something as that is how most of the atheros drivers are labelled.

do:

```
sudo lsmod | grep ath
```

If there are drivers in there that look suspect try unloading those modules and reloading ndiswrapper. If that works you need to blacklist those drivers so they don't get loaded at boot.

Hope that helps

---

### Post by shanix on 2008-09-26
Were you happen to be using roaming mode?
Tried to reload the ndiswrapper module? and tail -f /var/log/syslog and see if you can spot anything...

---

### Post by murphykieran on 2008-09-26
No, there's no ath modules loaded.  I already went through the process of blacklisting the Atheros drivers.  Roaming mode isn't activated either.

---

### Post by pytheas22 on 2008-09-26
> I suspect you have that your problem is arising because ubuntu thinks it already has a driver that will work for your wireless card.

Good point, but in this case conflicting drivers/modules aren't the problem, as the 'lshw -C' output (post #4) indicates that ndiswrapper is being used to drive the card.

I think that I have found the source of the problem, however.  In your dmesg output you have this line:
```

[   92.536750] ndiswrapper (mp_reset:62): wlan0 is being reset
```

I did some googling, and that message seems to pop up for other people who are having the exact same issue--ndiswrapper works when first installed, but after a reboot, nothing (see [this thread]("http://kubuntuforums.net/forums/index.php?topic=3097289.0") and [this thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=883586&page=1")).  Unfortunately, no one that I could find seems to have solved the problem, but I didn't google exhaustively, so if you search for "mp_reset:62" you might be able to find a fix that I missed.

Otherwise, what happens if you run:
```

sudo rmmod ndiswrapper
sudo ndiswrapper -r net5211
```

Then reinstall your Windows driver into ndiswrapper using ndisgtk, then run:
```

sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
sudo iwlist scan
```

Do you see networks then?  Can you connect?  If so, we can write a script that would just perform these steps automatically each time your reboot, which should effectively solve the problem...

---

### Post by murphykieran on 2008-09-26
> **pytheas22 said:**
> Then reinstall your Windows driver into ndiswrapper using ndisgtk, then run:
```

sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
sudo iwlist scan
```

Do you see networks then?  Can you connect?  If so, we can write a script that would just perform these steps automatically each time your reboot, which should effectively solve the problem...I tried that and got the same result "no scan results".  Bugger.

I'll google that "mp_reset:62" message and see if anyone else has found a solution.

Thanks for all the help so far.

---

### Post by murphykieran on 2008-09-26
Just thought I'd bump this thread to ask another question.  Obviously ndiswrapper might not be the solution to my problems, but a quick Google search of comes up with another possible solution - something called "madwifi" which is an (I think) attempt to build Linux drivers for Ahteros wifi chipsets.

Anyone know anything about it and how reliable or usable it is?

---

### Post by murphykieran on 2008-09-26
Okay, this experience has made me sad.  I just want wireless internet on this PC so I think it's time to just ditch Linux and reinstall Windows.  I'm not happy about it, but I want mobile wireless access on this PC.:(

I think I'll just go ahead tomorrow and put Windows XP on this thing tomorrow.

---

### Post by issih on 2008-09-27
madwifi is indeed a native driver that some people use with the ar242x chipset, 

This thread details a lot of peoples approaches to making the chipset you have work in hardy..

[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

I can't really help you any more than that other than to say I still think you have a module loading that shouldn't be. Have you gone into the hardware drivers bit and disabled the atheros drivers?

In the end though, if you can't get it to work for your hardware then the best solution is indeed to try something else, be that another linux distro (the hardware compatability varies quite a lot from distro to distro) or indeed to return to xp if that works for you.

If you have had enough for now, can I encourage you to give ubuntu another whirl when the next release (intrepid ibex 8.10) is released next month, as one of the main areas targetted for that release is support for wireless chipsets and general connectivity.

Sorry you had a trying time, unfortunately thats life sometimes :)

---

### Post by murphykieran on 2008-09-27
Yeah, I might download and try some other version of Linux if I can't get it working.  I'll check out that thread you linked to and see if it's useful to me.

Cheers.

edit: If I want to screw around and see if I can get the madwifi drivers to work, can someone given instructions to stop ndiswrapper from autoloading?

---

### Post by pytheas22 on 2008-09-27
Sorry that you're having such a frustrating time, and that reinstalling the Windows driver didn't help.

I didn't realize that you had an Atheros chipset--I wish we'd figured that out earlier (looking back, I see that that was mentioned in one of the outputs that you gave; sorry for not noticing).  Most Atheros cards have very good native Linux support (thanks to cooperation by Atheros with the open-source community), but ar242x I believe is a bit new and not supported by the version of madwifi that ships with Ubuntu 8.04.  However, the latest version of madwifi should support your chipset.  You can compile this latest version by using the script in [this thread]("http://ubuntuforums.org/showthread.php?t=798485")--it should be pretty easy.

Before running that script, you should get rid of ndiswrapper, which you can do by typing:
```

sudo apt-get remove --purge ndiswrapper*
```

Also remember to remove from your /etc/modprobe.d/blacklist file any lines containing "blacklist ath_pci" (ath_pci is the module used by madwifi).

You could also get a more up-to-date version of madwifi by installing Ubuntu 8.10 (only out in alpha now, so it won't be that stable, but your wireless would probably work in it out-of-the-box).

If you run that madwifi script successfully but your wireless still won't work and you want to keep troubleshooting, please post the output of:
```

lspci -nn
modinfo ath_pci
lshw -C Network
cat /etc/modprobe.d/blacklist
lsmod | grep ath
```

---

### Post by murphykieran on 2008-09-27
Thanks, I'm going to follow the instructions in that thread.  I don't have connectivity on the laptop so I'm downloading all the packages and other I need on this PC and I'll copy them over on a flash drive.  Hopefully it will do the trick.

> **pytheas22 said:**
> Before running that script, you should get rid of ndiswrapper, which you can do by typing:
```

sudo apt-get remove --purge ndiswrapper*
```I ran this command and it did it's thing without any errors. I was just checking after a reboot to make sure it was removed, so I ran the lsmod command and it's listing ndiswrapper as one of the loaded modules.

edit: I didn't notice the asterisk, so I ran it again with the asterisk and got the following output:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting ndiswrapper-common for regex 'ndiswrapper*'
Note, selecting ndiswrapper-utils for regex 'ndiswrapper*'
Note, selecting ndiswrapper-source for regex 'ndiswrapper*'
Note, selecting ndiswrapper-modules-1.9 for regex 'ndiswrapper*'
Note, selecting ndiswrapper-utils-1.9 for regex 'ndiswrapper*'
E: Couldn't find package ndiswrapper*
```
I rebooted and ran lsmod again, but it's still listing ndiswrapper as a loaded module.  I don't want to go through the madwifi setup if this will be a problem.

Thanks again for the help.

---

### Post by murphykieran on 2008-09-27
I went ahead and just reinstalled Ubuntu from scratch because it was only a new install anyway so I'm not losing anything and it was quicker than dealing with or removing any crap I'd already installed during my previous attempts at getting wireless working.  I went through the previous linked procedure for getting Madwifi working, but during the running of the installation script, I got the following error:
```
It seems that the driver did not detect compatible hardware
``` even though earlier in the output from the same installation process it said:
```
Found at least one Atheros device.
```
Maybe my wifi controller simply doesn't work in Linux. :(

Here's the outputs from the commands you asked for:

**lspci -nn**
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 04)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 04)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 04)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 04)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 04)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d4)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 04)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 04)
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
03:00.0 Ethernet controller [0200]: Attansic Technology Corp. Unknown device [1969:1026] (rev b0)

```

**modinfo ath_pci**
```
filename:       /lib/modules/2.6.24-19-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        0.9.4
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     D3FD3BD11169A96DBCFF8DE
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.24-19-generic SMP mod_unload 586 
parm:           countrycode:Override default country code (int)
parm:           maxvaps:Maximum VAPs (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)

```


[b]cat /etc/modprobe.d/blacklist
[/b]
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
```

**lsmod | grep ath**
```
ath_pci               100896  0 
wlan                  206960  1 ath_pci
ath_hal               192592  1 ath_pci
```

---

### Post by pytheas22 on 2008-09-28
Sorry that that still didn't help.  I don't know why the script didn't work, but according to [this post]("http://madwifi.org/ticket/1192") on the madwifi site, your card should be supported by the latest madwifi snapshot available from [here]("http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/").  If you download that file to your desktop, then run these commands, it would install it:
```

cd ~/Desktop
tar -xzvf madwifi*
cd madwifi*
make
sudo make install
```

Then after a reboot, is your card recognized?  Does 'lshw -C Network' still list it as unclaimed?

Your card should work in Linux.  Lots of other people have the exact same card, and it works.  So it's just a matter of figuring out why your system doesn't want to behave...

---

### Post by murphykieran on 2008-09-28
> Then after a reboot, is your card recognized?  Does 'lshw -C Network' still list it as unclaimed?I got the latest version of that file and ran through your instructions and after a reboot it's still listing the wireless as UNCLAIMED.

Doing some Googling suggested that maybe some cards are misidentified in Linux, it's being listed when I do 'lshw -C Network' as **AR242x 802.1abg Wireless PCI Express Adapter**.

But when I open the Windows driver .inf file from the drivers disc that came with the computer, part of the opening comments are:
```
;Abstract:
;    INF file for installing Atheros AR5001 Wireless Network Adapter
;
;    Installs ar5211.sys (NDIS 5/5.1 driver) on NT platforms (2000, XP and greater)
;    Installs ar52119x.sys (NDIS 5 driver) on 9x platforms

```Is it possible the card is being misidentified? 

According to the Madwifi Atheros compatibility list ([http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)), the Atheros AR5001X+ is supported, but there's no mentioned of a AR5001.  I don't know anything about wireless chips so I don't know if that's important.

---

### Post by pytheas22 on 2008-09-28
Good catch; it does seem like lspci was misidentifying your card.  However, madwifi does nonetheless seem to think that your card is supported:
> 
Atheros **AR5001X+**
Chipset:	AR5001X+ = (AR5211 + AR5111 + AR2111)
Chip:	AR5211 (802.11a +???)
URL:	[http://www.atheros.com/pt/AR5001Bulletins.htm](http://www.atheros.com/pt/AR5001Bulletins.htm)
Supports:	IEEE 802.11a, 802.11b, 802.11g(only ofdm)
Notes:	Also works with madwifi-old-openhal 

I'm pretty sure that this refers to your chipset.  So I'm not sure why madwifi doesn't want to claim it.  Perhaps the ath_pci module is not being loaded properly for some reason.  What is the output of:
```

dmesg | grep -e ath -e wlan
lsmod | grep ath
lshw -C Network
```

Sorry this is still not solved, but thanks for your patience.  I'm confident that we can solve it if we keep trying.

---

### Post by murphykieran on 2008-09-29
> **pytheas22 said:**
> ```

dmesg | grep -e ath -e wlan
lsmod | grep ath
```
Both these commands aren't giving any output at all.

```
lshw -C Network
```This is listing both the ethernet and wireless as UNCLAIMED.

> Sorry this is still not solved, but thanks for your patience.  I'm confident that we can solve it if we keep trying.Hey don't thank ME, I should be thanking YOU.  Which reminds me, if this works out, how do I go about thanking you?  I see some users here with "X thanks received" beside their avatar.

edit: Haha! I have it now.  I needed to enable the Atheros drivers because they were being marked by the system as restricted drivers and not in use, so I went to System>Administration>Hardware drivers, enabled them, rebooted, went into the network settings wizard, it detected the wireless network fine, so I put in my WEP key and it's accessing the web fine now.

edit2: And it's working fine after a reboot.  Looks like that's it folks. pytheas22, thanks for all the help, you've been extremely patient and helpful.

---

### Post by murphykieran on 2008-09-29
When I first installed Ubuntu, the first thing I did was enable the restricted Atheros drivers that 8.04 seemed to have come bundled with and rebooted, but it still wasn't picking up any networks which is why I tried using ndiswrapper, so I'm not sure why using those drivers now is working.  Maybe it was upgrading to the latest version of Madwifi that did the trick.

---

### Post by pytheas22 on 2008-09-29
Yes, the build of madwifi that ships by default with 8.04 probably didn't support your card, but the more recent version that you compiled from source did.

If you upgrade your kernel via Ubuntu updates, you will probably need to recompile madwifi again in order for the wireless to work on the new kernel (this only happens when you compile drivers from source yourself...normally this would not be necessary).  So just keep that in mind.

Otherwise, I'm glad it's finally solved, and have fun with Ubuntu now that you can finally get online :)

---

### Post by murphykieran on 2008-09-29
> **pytheas22 said:**
> If you upgrade your kernel via Ubuntu updates, you will probably need to recompile madwifi again in order for the wireless to work on the new kernel (this only happens when you compile drivers from source yourself...normally this would not be necessary).  So just keep that in mind.I'll probably just put on a fresh installation of 8.10 when it comes next month.

Again, thanks for everything.

---

