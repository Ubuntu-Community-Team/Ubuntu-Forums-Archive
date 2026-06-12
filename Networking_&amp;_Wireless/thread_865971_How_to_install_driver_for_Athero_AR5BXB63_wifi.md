---
title: "How to install driver for Athero AR5BXB63 wifi?"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by Olnex on 2008-07-21
I have an Acer Aspire 5315, it has Athero AR5BXB63 wireless card (written on the label at the bottom of laptop), after installing Hardy Heron, the restricted hardware information has:

Atheros Hardware Access Layer (HAL)
Support for Athero 802.11 wireless LAN cards

However, network manager applet on the top right corner does not show any wireless connection, could anyone tell me or point me to the right direction to make wireless work?

Thanks a lot!

Here is the output of lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by acreech on 2008-08-06
I am having this exact same problem. 

> 
*-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:c8:1c:d2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.64 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0


---

### Post by mathieu.ward on 2008-08-09
i guess that makes 3. would love to get this functional otherwise i will have no other otion but VISTA ( i dont want to but i feel ther is no other way)

acer aspire 5315, intel celeron 550 2gz, 1gb ddr2, 
atheros AR5BXB63 and a fresh intall of hardy. i believe this is 32 bit system


tried to fallow a walk through on another thread but got lost

i love ubuntu and would like to have this feature at my disposal

all help greafully recieved

---

### Post by chili555 on 2008-08-09
> AR242xHere are instructions; they require an active internet connection, so walk your computer over to the router and hook up the ethernet. Open a terminal and do these commands, each in order and in turn. ```
sudo apt-get install build-essential linux-headers-generic
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz
tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801/
```The file name will change as the current build changes. Just watch what the file is that is extracted.```
make
sudo make install
sudo modprobe ath_pci
sudo reboot
```Your wireless should now be alive. Post back if you need help.

---

### Post by mathieu.ward on 2008-08-10
what can i say,  outstanding!  thank you very much

followed your instructions late last night, lost patience and went to bed zzzzzz

woke up, booted and to my amazement fully functioning WiFi


thank you soooo much, you are a credit to the community
:grin::grin::grin::grin:

---

### Post by chili555 on 2008-08-10
Thank you for your kind comments. Glad it's working! Please note that when an update brings a new kernel, you will need to build this module for the new one. You will need to do:```
cd madwifi-hal-0.10.5.6-r3835-20080801/
**make clean**
make
sudo make install
sudo modprobe ath_pci
```

---

### Post by mathieu.ward on 2008-08-11
ok im goint to dumb now, but...

i added the code from the post above, but what has it done? i wont know if my wifi is working till i get home and am at work atm.

sound dumb i know, but i would like to gain a resonable understanding of ubuntu

many thanks in advance

matty:):)

---

### Post by chili555 on 2008-08-11
Well, there was no need to run that code now, although it did no harm. My post said:> when an update brings a new kernel, you will need to build this module for the new one.Your running kernel can be determined with the command:```
uname -r
```My machine returns *2.6.24-19-generic*. If we turn on our computers tomorrow and the little Update Manager is glowing away in the panel and we run it and find that one of the packages being updated is *linux-image*, we will know we have gotten a newer, updated kernel. Another indicator will be that we are asked to reboot in order to complete the update. 

When you do reboot, you will find that your wireless no longer works. That's because you built the *ath_pci* for the kernel we have today and no *ath_pci* module for your spanking new kernel has yet been built. It will be built when you run the code I suggested. 

Here is another way to look at it. Here is a list of the kernels in my own system:
kernel 2.6.24-19-generic   <--has an *ath_pci* module built.
kernel 2.6.24-18-generic
kernel 2.6.24-17-generic
kernel 2.6.24-16-generic
and a few others...

As you can see, if, for an example, a new kernel 2.6.24-20 gets installed, it will not have an *ath_pci* module built for it. I will then have to run the above code to build it.

If this is not clear now, post back and I do my best to answer any questions.

---

### Post by Machina987 on 2008-08-11
Thanks, i got it online Appreciate your help.

---

### Post by AdNZL on 2008-08-11
Hi Chili555. Out of all the instructions I've followed on this forum, your's has had the most success. It's still not working but I actually got a whole bunch of error messages flash up on my screen on reboot instead of it just sitting there doing nothing. At least the error messages showed something was happening.

my wireless details are

** Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)**

I am not sure how to get those error messages writen down as they flash up so fast and it happened when the laptop was shutting down. The general impression I got from what little I could read was that it wasn't happy about something (duh) and it said something about disabling the wireless card. (not much help I know :( )

Any help would be really appreciated.

(oh yeah the lap top is a compaq Presario C793VU)

**EDIT**:

[I]OMG It works! it works! IT WORKS!!!

With all the mucking about I'd done previously,(trying to get the damn thing working and following this thread [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)) I'd switched off the restricted drivers. Once I switched them back on the wireless sprung into life, although very quietly as the indicator light did not change to blue to show it was on, but I can detect 3 wireless networks around me, which funnily enough vista can't see.

So if anyone else finds this doesn't work, make sure your restricted drivers are switched on and it might, like it did for me, YAY!

*Happy happy dance :) *[/I]

---

### Post by carlolovearianne on 2008-08-11
I just reinstalled Hardy on my laptop and in the past I was able to make the wireless work by following the instructions found in [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html#](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html#) but this time it didn't seem to work.

I figured out that maybe the link wasn't updated but luckily I quickly found this thread and it's working again as it used to be (which was, uhm, 2 hours ago :))

Thank you so much chili555.

---

### Post by chili555 on 2008-08-11
Thank you all for your kind comments. We aim to please.

---

### Post by windozehater on 2008-08-12
Chilli555 I can't thank you enough, I have an acer 5570z with that darn atheros card. and after trying every piece of advice i could find and scapping & reinstalling my system probably dozens of times you have made my laptop fully functional without any bugs. Until now the only way i could get wireless was through the external card slot or to swap out the internal with the broadcomm from my wifes compaq, this has been going on for a year. God Bless You, I thought i was gonna go nuts and have to though this machine into oncomming traffic.

---

### Post by deanet on 2008-08-12
I have the exact same problem, but here is what I did to fix it.
Went to the Acer site and downloaded the windows driver for the Acer 5310 (Atheros V5.3.0.45 for XP) and extracted it in my home folder and then used the Windows Wireless Driver Tool in Ubuntu 8.04 to install the driver.  Be sure and remove amy previous windows wireless drivers first.

---

### Post by LightsOutArtwork on 2008-08-16
Forgive the newbieness of my questions, however, I was wondering if there is a difference between this and 64 bit.  What would the difference be if you ran this as 32 on a 64-bit?  Let me know if I should just start a new thread or if this has been answered already as I couldn't find the answer for myself.  

I've been trying to get my wireless working for a week now and this is the first one that has worked for me.

Its connected at 54% which seems low to me for some reason. I'm working on a HP with a atheros ar242x, but the important thing is that it actually works! So many many thanks for that!

---

### Post by uhappo on 2008-08-21
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

sudo apt-get install build-essential linux-headers-generic
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz
tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801/

make
sudo make install
sudo modprobe ath_pci
sudo reboot

```

WLAN working very beatifully, same as desktop effects!!!
WUHUU!!!

---

### Post by SalsaShark on 2008-08-21
Sweeeeeeet.  Thanks a lot, Chili.  Now this may seem kind of dumb but whatever... is there any way to get madwifi-hal etc... out of my home folder, or at least hidden, without messing everything else up?  Now it just seems cluttered in there and I'm a very organized and uncluttered person.

---

### Post by mikebdoss on 2008-08-26
Chili555, many, many thanks. Everything was working on my new Vaio NR260E except the wireless, and I was having the same issues as most other folks. Your very straight-forward approach worked perfectly. Thanks again!

---

### Post by sudoMakeMeASandwhich on 2008-09-02
I followed your tutorial to the letter, however, I am still having some issues.

I have an HP Pavilion dv6911us, with the Atheros AR242x 802.11abg

I have two proprietary drivers (not enabled):
Atheros Hardware Access Layer (HAL)
Support for Atheros 802.11 wireless LAN cards

I followed you tutorial to the letter, and got no errors, but when I rebooted the wifi still would not work

in the past i tried ndiswrapper (that didn't work) but I disabled ndiswrapper and i took ath_pci off blacklist.

when i do iwconfig i get:
```
$ iwconfig
lo        no wierless extensions

eth0      no wierless extensions
```
I don't get ath0

I tried enableing the proprietary drivers, that lets me get the ath0 when I do iwconfig. However, I still can't get wifi to work and the drivers disable when I restart the comp.

---

### Post by d_singo69 on 2008-09-06
Thanks Chili555. You have just ended weeks of frustration. just superb.

---

### Post by Lindy08 on 2008-09-24
To All,

Thanks and I hope I can get this solution to work.  I just bought an Acer 5026Z and have the same problem.  Am completely new to Ubuntu and Linux.  Been searching and trying various posted solutions.  Question:  I am booting Ubuntu up off a Live Zip Drive I made.  Not ready to try a full dual boot install yet.  Will Chili555's solution work under these conditions.  I don't want to mess up my Vista OS.  I noted that after trying other fixes in Ubuntu that didn't work, a Vista boot automatically reinstalled the drivers for the wifi card so I was ok.

Thanks,
Lindy08

---

### Post by Lindy08 on 2008-09-25
Dear Chili555 I got to thru the fourth line of code:

cd madwifi-hal-0.10.5.6-r3835-20080801/

then I got an error message that no such file name or directory existed. ????  Couldn't go farther.  I am running off a bootable Live Flash drive not a full install.  I am all of about a week into being a Linux Newbee.

Thanks for any more instruction.  Up to that point things looked good.

---

### Post by Hilko on 2008-09-25
chili555 Thank you so very much !!! It is working perfectly, i can see lot's of networks now. Very nice clear easy to follow instructions.
People like you can really make a difference and can keep me from using windows. Thanks again !


> **Lindy08 said:**
> Dear Chili555 I got to thru the fourth line of code:

cd madwifi-hal-0.10.5.6-r3835-20080801/

then I got an error message that no such file name or directory existed. ????  Couldn't go farther.  I am running off a bootable Live Flash drive not a full install.  I am all of about a week into being a Linux Newbee.

Thanks for any more instruction.  Up to that point things looked good.


Lindy08, you need to change the directory name to the name you see on the first line after the command "tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
"

For example:
 ```
cd madwifi-hal-0.10.5.6-r3861-20080903/
```

instead of
cd madwifi-hal-0.10.5.6-r3835-20080801/

---

### Post by 10gallons on 2008-09-25
Here's a very useful post:

[http://ubuntuforums.org/showthread.php?t=785040&highlight=ar5418]("http://ubuntuforums.org/showthread.php?t=785040&highlight=ar5418")

It may help?

---

### Post by Lindy08 on 2008-09-30
I finally got the driver directory and all related files generated but the final modprobe still didn't work.  I did finally note the change in directory name. I think the directory is in the wrong location on by bootable Unbuntu zip drive.  I saved a copy of the directory and can copy it into the correct location if I know where that is.  When it is a subdirectory in the "Unbuntu" directory, the whole subdirectory and files are deleted on reboot.  It won't let me copy into the System directory.  Seems like the driver files are not being located.  I tried un-enabling the Windows drivers and doing the final modprobe to no avail.  This command line stuff is like the old DOS days from 25 years ago.  I hope this makes sense to someone out there who can help because I feel like I am close to solving it.  THANKS

---

### Post by dsmcginn on 2008-11-19
it didnt work...
=(

doug@doug:~$ sudo apt-get install build-essential linux-headers-generic
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
doug@doug:~$ wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
--09:17:13--  [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
           => `madwifi-hal-0.10.5.6-current.tar.gz'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://snapshots.madwifi-project.orgmadwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.orgmadwifi-hal-0.10.5.6-current.tar.gz) [following]
--09:17:13--  [http://snapshots.madwifi-project.orgmadwifi-hal-0.10.5.6-current.tar.gz/](http://snapshots.madwifi-project.orgmadwifi-hal-0.10.5.6-current.tar.gz/)
           => `index.html'
Resolving snapshots.madwifi-project.orgmadwifi-hal-0.10.5.6-current.tar.gz... failed: Name or service not known.

---

### Post by Olnex on 2008-11-19
Go to [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/") and download the latest one.

---

### Post by dsmcginn on 2008-11-21
so i finally got everything going smoothly...but the final modprobe gave me this:

doug@doug:~/Desktop/madwifi-hal-0.10.5.6-r3875-20081105$ sudo modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-21-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

anyone else get that?

---

### Post by Olnex on 2008-11-21
Which version of Ubuntu are you using? When I used 8.04, I disabled in the restricted hardware the option which contains "HAL", leave the other item enabled, installed the driver, did NOT modprobe it, restart and it works.
I am using 8.10 now, I just installed the drive and restart, it works.

---

### Post by aircooledbusnut on 2008-12-01
Thank you very much for this help.  I have been running ndiswrapper on my 64bit for a while, it was working however I became increasingly frustrated rmmod and modprobe ing ndiswrapper up to six times before my wireless would work.  Your solution has it starting right off the bat.  Oh, I added 1 thing to your fix.
echo "ath_pci" | sudo tee -a /etc/modules

so it starts with out me having to modprobe.
Thanks again

---

### Post by gregm164 on 2008-12-06
I'm currently just having a demo of Ubuntu on my laptop before installing, love dual-booting on my desktop. So i wanted to make sure wifi worked so i went through this whole thing. However when you reboot, you lose any data, so would that mean this will only work when I have it properly installed?


And also _**totally**_ dumb question but what should happen when this is working? Must i click on the little network thingy on the panel and see something about wireless network? Will it scan wifi or do i third-party program for that?

---

### Post by hacker0wnz on 2008-12-06
i have the same problem on my dv5z1000 laptop. i tried to follow the instruction but
i relized that i cant connect to internet at all.
(except with the other computer running vista)


Drivers Is Activated and also Says In Use

Atheros 802.11 LAN card

AR5009 WLAN 



HELP PLEASE! :(

---

### Post by lovelyvik293 on 2008-12-06
@gregm164 you can access the internet and do certain things at the Live session mode but you can't save things.

Yes The tiny Network thing scan the wifi.

---

### Post by kice0623 on 2008-12-28
Atheros AR5BXB63
help this how to does not work for my c769 compaq newbie

---

### Post by cptrohn on 2009-01-16
> **chili555 said:**
> Here are instructions; they require an active internet connection, so walk your computer over to the router and hook up the ethernet. Open a terminal and do these commands, each in order and in turn. ```
sudo apt-get install build-essential linux-headers-generic
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz
tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801/
```The file name will change as the current build changes. Just watch what the file is that is extracted.```
make
sudo make install
sudo modprobe ath_pci
sudo reboot
```Your wireless should now be alive. Post back if you need help.

Ok I just tried to do this and when I get to the end of the first of the codes that is listed ```
cd madwifi-hal-0.10.5.6-r3835-20080801/
``` It comes back in my terminal as :No such file or directory.

Help?

---

### Post by cptrohn on 2009-01-16
Ok.. please disregard my post, I didn't read far enough into the thread and saw what I did wrong!!  Wireless working smoothly now!!


Thanks for the great workaround guys!!

---

### Post by loomerds on 2009-02-19
This is a great discussion that provides an Athelos wifi solution under most circumstances.  However, depending upon one's kernel files, the make command breaks on some systems when trying to compile the madwifi file.  For those who have the problem (which throws a "No rule to make target" error), or for those who don't want to have to recompile after kernel updates, you may want to try the MadWifi HAL DKMS Mini-How-To at [http://myrtg.blogspot.com/2008/11/madwifi-hal-dkms-mini-how-to.html](http://myrtg.blogspot.com/2008/11/madwifi-hal-dkms-mini-how-to.html).  It worked like a charm for me.

---

### Post by mikebdoss on 2009-11-11
I've successfully used Chili555's instructions, and they've worked perfectly for me. Every time there's a new kernel build, I follow his instructions [here]("http://ubuntuforums.org/showpost.php?p=5559725&postcount=6"), and they re-repair my wifi. 

All was fine until 9.10 - the instructions no longer work. When I try to 'make', I get the following errors:

```

michael@white:~/madwifi-hal-0.10.5.6-r3835-20080801$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/michael/madwifi-hal-0.10.5.6-r3835-20080801 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.o
In file included from /home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/../net80211/ieee80211_monitor.h:34,
                 from /home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:75:
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/../ath/if_athvar.h:107: error: conflicting types for 'irqreturn_t'
include/linux/irqreturn.h:16: note: previous declaration of 'irqreturn_t' was here
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_attach':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:478: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:819: error: 'struct net_device' has no member named 'open'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:820: error: 'struct net_device' has no member named 'stop'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:821: error: 'struct net_device' has no member named 'hard_start_xmit'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:822: error: 'struct net_device' has no member named 'tx_timeout'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:824: error: 'struct net_device' has no member named 'set_multicast_list'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:825: error: 'struct net_device' has no member named 'do_ioctl'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:826: error: 'struct net_device' has no member named 'get_stats'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:827: error: 'struct net_device' has no member named 'set_mac_address'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:828: error: 'struct net_device' has no member named 'change_mtu'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_detach':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1130: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1185: error: 'struct net_device' has no member named 'stop'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_vap_create':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1194: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1269: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_vap_delete':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1453: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_suspend':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1553: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1553: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1553: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1553: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1553: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1553: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_resume':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1560: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1560: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1560: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1560: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1560: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:1560: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_intr':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:2315: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_fatal_tasklet':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:2511: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_rxorn_tasklet':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:2521: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_bmiss_tasklet':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:2531: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_init':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:2573: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_stop_locked':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:2676: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_stop':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:2757: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_reset':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:2797: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_tx_startraw':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:3002: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_hardstart':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:3315: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_mgtstart':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:3662: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_key_alloc':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:3994: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_key_delete':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:4059: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_key_set':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:4135: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_key_update_begin':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:4150: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_key_update_end':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:4171: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_mode_init':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:4261: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_updateslot':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:4396: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_beacon_dturbo_config':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:4423: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_beacon_dturbo_update':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:4472: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_turbo_switch_mode':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:4615: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_bstuck_tasklet':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:5329: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_node_alloc':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:5737: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_node_cleanup':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:5765: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_recv_mgmt':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:6286: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_rx_tasklet':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:6409: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_grppoll_start':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:6847: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_grppoll_stop':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:7053: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_wme_update':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:7259: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_uapsd_flush':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:7278: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_tx_start':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:7451: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_tx_tasklet_q0':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:8300: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_tx_tasklet_q0123':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:8321: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_tx_tasklet':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:8365: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_tx_timeout':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:8398: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_calibrate':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:8783: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_scan_start':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:8863: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_scan_end':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:8883: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_set_channel':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:8901: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_set_coverageclass':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:8917: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_mhz2ieee':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:8927: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_newstate':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:8942: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_setup_stationkey':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:9437: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_newassoc':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:9598: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_getchannels':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:9629: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_xr_rate_setup':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:9927: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_setup_subrates':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:9956: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_rate_setup':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:9999: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_printtxbuf':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:10223: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_getstats':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:10250: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_set_mac_address':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:10273: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_change_mtu':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:10302: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_ioctl':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:10391: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_announce':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11144: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'txcont_configure_radio':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11340: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'txcont_queue_packet':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11611: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'txcont_on':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11745: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'txcont_off':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11766: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_get_dfs_testmode':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11780: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_set_dfs_testmode':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11807: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_get_txcont':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11817: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_set_txcont_power':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11835: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_get_txcont_power':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11853: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_set_txcont_rate':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11863: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_get_txcont_rate':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11880: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_set_dfs_cac_time':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11890: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_get_dfs_cac_time':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11900: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_set_dfs_excl_period':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11920: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_get_dfs_excl_period':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11929: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_test_radar':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11941: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_dump_hal_map':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:11956: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_rcv_dev_event':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:12065: error: 'struct net_device' has no member named 'priv'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:12067: error: 'struct net_device' has no member named 'open'
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c: In function 'ath_debug_iwpriv':
/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.c:12436: error: 'struct net_device' has no member named 'priv'
make[3]: *** [/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.o] Error 1
make[2]: *** [/home/michael/madwifi-hal-0.10.5.6-r3835-20080801/ath] Error 2
make[1]: *** [_module_/home/michael/madwifi-hal-0.10.5.6-r3835-20080801] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [modules] Error 2

```

Any suggestions? I'm new enough that I really don't know where to go from here.

---

### Post by mikebdoss on 2009-11-11
Update - I used the instructions at [https://answers.launchpad.net/ubuntu/+question/74211](https://answers.launchpad.net/ubuntu/+question/74211), and they worked great for me, and I'm back with my wifi. I'm just hoping I won't have to find a new fix every time a new update comes...

---

### Post by olgasmi on 2011-10-30
Checking requirements... ok.
Checking kernel configuration... FAILED
Only kernel versions 2.4.x and above are supported.
You have 3.0.0-13-generic.
make: *** [configcheck] Virhe 1
olga@Olga-Laptop:~/Työpöytä/madwifi-hal-0.10.5.6-r4103-20100110$ 
olga@Olga-Laptop:~/Työpöytä/madwifi-hal-0.10.5.6-r4103-20100110$ sudo modprobe ath_pci
FATAL: Module ath_pci not found.
Checking requirements... ok.
Checking kernel configuration... FAILED
Only kernel versions 2.4.x and above are supported.
You have 3.0.0-13-generic.
make: *** [configcheck] Virhe 1
olga@Olga-Laptop:~/Työpöytä/madwifi-hal-0.10.5.6-r4103-20100110$ 
olga@Olga-Laptop:~/Työpöytä/madwifi-hal-0.10.5.6-r4103-20100110$ sudo modprobe ath_pci
FATAL: Module ath_pci not found.

Someone remember witch file includes that code ath_pci  in Ubuntu 11.10? O_O

---

### Post by nothingspecial on 2011-10-30
Please don't dig up old threads.

It's also not a good idea to follow 4 year old instructions as things progress.

If you have a problem, create a new thread with as much detail as you can.

Closed.

---

