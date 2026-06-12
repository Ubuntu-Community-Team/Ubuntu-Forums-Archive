---
title: "Wireless not working BCM4318"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by adfriedman on 2010-09-25
I am new to Ubuntu (I have version 10.04) and for a linux user I am very un-tech savy.  I have scoured the forums and still can't get my wireless to work.  I have a Dell Inspiron 2200 and I think I have a Broadcom BCM4318 wireless card because of the output of sudo lshw -C network (which I pasted at the bottom of this post.)

When I right click on the internet connection icon on the top toolbar there is a check next to "enable wireless".  When I left click on it, it says, "Wireless Networks Disconnected"

I think I installed several things with the Synaptic package manager because in the manager it says:
b43-fwcutter it says installed version is:  1:012-1build1
bcmwl-modaliases it says installed version is:  5.60.48.36+bdcom-0ubuntu3
broadcom-sta-common it says installed version is:  5.10.91.9.3-3
broadcom-sta-source it says installed version is:  5.10.91.9.3-3
bcmwl-kernel-soutce it says installed version is: 5.60.48.36+bdcom-0ubuntu5

When I click on System>Administration>Hardware drivers, a box pops up that says: "no proprietary drivers are in use on this system"

[one other thing, I have tried downloading several drivers.  I don't think it worked because I get a zip file with a lot of other files inside the zip and I don't know what to do after I extract the files]

I would greatly appreciate any help you can provide.  
Thanks,
Adam



output of [sudo lshw -C network] is:
*-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:36:79:4d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,11/02/2005, 4.10.4 latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:19 memory:dfdfe000-dfdfffff
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:14:22:b5:95:b6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.15.101 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:dfdfd000-dfdfdfff ioport:df40(size=64)

---

### Post by Kr4zyl3gz on 2010-09-25
Ok i spent about 6 hours fighting with A laptop that had to have the B43 patch and pretty much my advice is to search B43 on here and somewhere (not sure the link off hand) there is a step by step guide to get it working i got a Aspire (acer) That has the same issue i wanted to yank my hair out my head 

_________________
Sincerely 

Kr4zyl3gz

---

### Post by Chris1274 on 2010-09-25
The easiest solution is to find a wired internet connection and download the Broadcom driver through System > Administration > Hardware Drivers.

---

### Post by beew on 2010-09-25
It seems that the BCM4318 card is a bit special. Check this if you have tried other methods,  the OP in the thread claimed that methods worked for other BCM43XX cards didn't work on this one. This is a long thread starting 2006 but the later entries seem reasonably recent. Good luck.

[http://ubuntuforums.org/showthread.php?t=190177&page=10](http://ubuntuforums.org/showthread.php?t=190177&page=10)

**Edited:** Sorry, I forgot to clarify what 'other methods' you should try first.. 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[URL="http://linuxwireless.org/en/users/Drivers/b43"]
http://linuxwireless.org/en/users/Drivers/b43[/URL]

---

### Post by statistic on 2010-09-25
Hey, I recently helped a bunch of people install 10.04 on their laptops, and for the broadcom cards the STA driver is usually available in the restricted drivers list. As crazy as it sounds, try looking again, one of the guy's laptops didn't have it in the list one minute, then I reopened it a moment later and it was there. Try making sure you're connected to the Internet via ethernet as well, that may help, or it may not.

---

### Post by adfriedman on 2010-09-25
Thanks for the help but I still can't get it working.  I have a wired connection.  I have checked system>administration>hardware drivers many times and it always says, "no proprietary drivers are in use on this system."  Is this what you mean by the "restricted drivers list" or is this list somewhere else?

---

### Post by Chris1274 on 2010-09-25
Maybe try updating your system first:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
Then reboot and re-check Hardware Drivers again.

---

### Post by reidi on 2010-09-25
> **Chris1274 said:**
> Maybe try updating your system first:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
Then reboot and re-check Hardware Drivers again.

I would be VERY careful before updating to 10.10.  I cannot get my Broadcom 4318 working properly with the new kernel.  It connects, but randomly and frequently drops the connection.

Stick with 10.04 for now - wireless worked flawlessly for me with the Broadcom 4318.

---

### Post by adfriedman on 2010-09-25
I tried the code you suggested (sudo apt-get update && sudo apt-get dist-upgrade) before reidi cautioned me against it.  I went to system>admin>hardware drivers and I finally saw a driver there for b43.  I clicked install (or something like that, I can't remember.) then I rebooted.  The wireless still doesn't work and when I go back to the hardware drivers and now the driver isn't listed.

---

### Post by Chris1274 on 2010-09-25
> **reidi said:**
> I would be VERY careful before updating to 10.10.  I cannot get my Broadcom 4318 working properly with the new kernel.  It connects, but randomly and frequently drops the connection.

Stick with 10.04 for now - wireless worked flawlessly for me with the Broadcom 4318.

'dist-upgrade' doesn't yet upgrade 10.04 to 10.10. I presume it won't until the RC is ready.

---

### Post by Chris1274 on 2010-09-25
> **adfriedman said:**
> I tried the code you suggested (sudo apt-get update && sudo apt-get dist-upgrade) before reidi cautioned me against it.  I went to system>admin>hardware drivers and I finally saw a driver there for b43.  I clicked install (or something like that, I can't remember.) then I rebooted.  The wireless still doesn't work and when I go back to the hardware drivers and now the driver isn't listed.

Broadcom STA wasn't on the list? That's the one that works for me.

If not, maybe try going to the Broadcom website and downloading it from there.

---

### Post by reidi on 2010-09-25
Sorry to ask, but you do have any mechanical wireless switch on the laptop turned to "On" right?

What do you get when you run this command?

lspci -vnn | grep 14e4

The command should result in a string similiar to this example:

0001:01:01.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

If you run:

sudo lsmod | grep b43

does the output show any entries for the b43 module?

If not enter the commands
sudo modprobe b43 
sudo lsmod | grep b43 

You should see b43 in the output.

Do you have a folder /lib/firmware/b43 on your system?  Does it have files in it?

Try:
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
ifconfig

The wlan0 section of the ifconfig output should come back with
something like this:

wlan0     Link encap:Ethernet  HWaddr 00:1c:df:4f:fe:15  
          inet addr:192.168.0.66  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:dfff:fe4f:fe15/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53402769 (53.4 MB)  TX bytes:10847771 (10.8 MB)

I have found linuxwireless.org very helpful in the past, but I don't think it should be necessary to go that route if you truly have a Broadcom 4318 and the module/firmware/driver is being installed properly.

---

### Post by Chris1274 on 2010-09-26
> **Chris1274 said:**
> 'dist-upgrade' doesn't yet upgrade 10.04 to 10.10. I presume it won't until the RC is ready.

In fact, it won't do so at all unless you modify /etc/apt/sources.list. 

>  apt-get dist-upgrade differs from apt-get upgrade in that it will remove obsolete packages and add new dependencies, while apt-get upgrade  will not. this is necessary when upgrading from one distro release to  another, but it is not the *only* time it is necessary. thus, in aptitude, dist-upgrade has been renamed to full-upgrade
<maco> apt-get dist-upgrade will only change you from  one release to another if you've modified /etc/apt/sources.list to  point to a newer release, but this method of upgrading is not  recommended

The above is from [http://ubuntulinuxtipstricks.blogspot.com/2010/02/dist-upgrade-misnomer-confusion.html](http://ubuntulinuxtipstricks.blogspot.com/2010/02/dist-upgrade-misnomer-confusion.html)

---

### Post by lkraemer on 2010-09-26
adfriedman,
This HOWTO: should help:
[http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+Broadcom)

Start by posting the output from Step #1, we'll go from there.


When I've seen your posting, if everything looks good......
go to:
**#2 Use DEFAULT B43 Driver in 10.04**

lk

---

### Post by adfriedman on 2010-09-26
First I want to say that this is my first time posting to the ubuntu forum and I am amazed at how many people are going out of their way to try to help some shmoe who can't work his wireless.  I am baffled (in a good way) at these multiple acts of kindness.  I rarely see this type of generosity offline.  Thank you so much to the ubuntu community.  

As per your questions reidi and lkraemer:

The output from :lspci -vnn | grep 14e4   
is the following:
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)


The output from: sudo lsmod | grep b43
is the following:
b43                   163523  0 
ssb                    38671  1 b43
mac80211              205146  1 b43
cfg80211              126517  2 b43,mac80211
led_class               2864  1 b43


I do have a folder
/lib/firmware/b43 :  It has 32 files, all with .fw extensions



eth0      Link encap:Ethernet  HWaddr 00:14:22:b5:95:b6  
          inet addr:192.168.15.101  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:feb5:95b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:819406 (819.4 KB)  TX bytes:299388 (299.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:36:79:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:dfdfe000-dfe00000 

AND LASTLY, THE OUTPUT FROM: 
lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

WAS

lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
adam@adam-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
adam@adam-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:36:79:4d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,11/02/2005, 4.10.4 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: irq:19 memory:dfdfe000-dfdfffff
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:14:22:b5:95:b6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.15.101 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:dfdfd000-dfdfdfff ioport:df40(size=64)
adam@adam-laptop:~$ lsmod
Module                  Size  Used by
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
pcmcia                 33024  0 
b43                   163523  0 
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_oss            26726  0 
vga16fb                11385  0 
binfmt_misc             6587  1 
snd_seq_midi            4557  0 
vgastate                8961  1 vga16fb
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ppdev                   5259  0 
ssb                    38671  1 b43
snd_timer              19098  2 snd_pcm,snd_seq
joydev                  8708  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205146  1 b43
i915                  285586  3 
yenta_socket           20408  1 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29297  1 i915
cfg80211              126517  2 b43,mac80211
rsrc_nonstatic         10015  1 yenta_socket
soundcore               6620  1 snd
dell_wmi                1793  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
ndiswrapper           184677  0 
psmouse                63245  0 
led_class               2864  1 b43
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
drm                   162409  4 i915,drm_kms_helper
dell_laptop             6856  0 
serio_raw               3978  0 
lp                      7028  0 
intel_agp              24119  2 i915
agpgart                31724  2 drm,intel_agp
dcdbas                  5422  1 dell_laptop
i2c_algo_bit            5028  1 i915
parport                32635  2 ppdev,lp
video                  17375  1 i915
output                  1871  1 video
e100                   28211  0 
mii                     4381  1 e100
adam@adam-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)
adam@adam-laptop:~$ cat /etc/modprobe.d/blacklist.conf
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

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

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

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
adam@adam-laptop:~$ iwconfig

---

### Post by beew on 2010-09-26
Did you check the link I posted? It is exactly about your card.

[http://ubuntuforums.org/showthread.php?t=190177&page=10]("http://ubuntuforums.org/showthread.php?t=190177&page=10")

---

### Post by lkraemer on 2010-09-26
adfriedman,
OK, first things first....A lot of folks try to help, but most don't spend
the time to get the necessary detail.  Enough said!

(I assume you are still trying to get the Broadcom B43 Drivers working in Ubuntu 10.04
versus using Ndiswrapper and the Windows XP Drivers.)

Now. you have two problems already.  Ndiswrapper has two drivers installed, which must be removed, along with Ndiswrapper.  So, let's try this.



**REMOVE WINDOWS DRIVERS:**
If you want to REMOVE the Windows Drivers:...............
If the output of ndiswrapper -l shows any drivers loaded,
remove ALL of them. If memory serves me correctly the command is:
```

sudo ndiswrapper -e bcmwl5

```
This should clean up nidswrapper & drivers and:
```

ndiswrapper -l

```
should return nothing as being loaded.

Then remove ndiswrapper:
```

sudo modprobe -r ndiswrapper

```
Remove from startup file by editing:
```

sudo nano /etc/modules

```
to remove ndiswrapper.

Now, That should fix the two conflicting drivers.

Now that you already have the firmware installed it should be simple.
Double check that you have the two folders b43 & b43legacy located at
/lib/firmware/b43 and /lib/firmware/b43legacy and that these folders have
*.fw files in them.

Now you just have to Enable the B43 Driver:
SYSTEM -> ADMINISTRATION ->HARDWARE DRIVERS
should have a B43 Driver listed a driver listed for your wireless,
if so enable it. (If by chance you have already ENABLED it, go ahead
and let it try to uninstall, then install it again by clicking again.)
It should find the drivers and load them, because the Firmware is where
it needs to be.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```

Check Network Manager (right click on the icon) to be sure the "Enable Wireless"
box is checked (It should be ENABLED already by default.)

It shouldn't take more than 15 minutes......to get it working.

Check to see if you have wireless now. If not, you might need to
check the Loaded Modules, making sure there are no conflicts with other
Wifi drivers that might have been loaded, or others that cause conflicts.
```

lsmod

```
If it isn't working, post the output of lsmod.


lk

---

### Post by adfriedman on 2010-09-26
Beew, I tried the link that you posted.  Much of it I didn't understand (I'm really untech savy for a linux user.) But I tried the three step process mentioned in [https://help.ubuntu.com/community/Wi...eisty_No-Fluff](https://help.ubuntu.com/community/Wi...eisty_No-Fluff).   it didn't seem to work.

---

### Post by adfriedman on 2010-09-26
I entered the codes in order, but when I entered: sudo nano /etc/modules

I got the following: (and if I tried to close the terminal, I got a message saying "there is still a process running in the terminal.  Closing the terminal will kill it.)

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
b43
b43
ndiswrapper


                                [ Read 9 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell


However, then the B43 driver was in the hardware driver section.  I activated it and now it says, "The B43 driver is activated and currently in use." Which is great news.   I rebooted, but when I right click on the network manager, the enable wireless has no checkmark and I can't check it so I can't seem to enable the wireless.

BTW, I double checked and I don't have a switch on the computer to turn off the wireless.


And the results of lsmod are:

Module                  Size  Used by
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
binfmt_misc             6587  1 
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
fbcon                  35102  71 
arc4                    1153  2 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_dummy           1338  0 
vga16fb                11385  0 
b43                   163523  0 
vgastate                8961  1 vga16fb
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
ssb                    38671  1 b43
ppdev                   5259  0 
pcmcia                 33024  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
mac80211              205146  1 b43
i915                  285586  3 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211              126517  2 b43,mac80211
drm_kms_helper         29297  1 i915
snd_timer              19098  2 snd_pcm,snd_seq
dell_wmi                1793  0 
joydev                  8708  0 
yenta_socket           20408  1 
led_class               2864  1 b43
drm                   162409  4 i915,drm_kms_helper
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           184677  0 
intel_agp              24119  2 i915
rsrc_nonstatic         10015  1 yenta_socket
dell_laptop             6856  0 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                63245  0 
serio_raw               3978  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
agpgart                31724  2 drm,intel_agp
dcdbas                  5422  1 dell_laptop
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
video                  17375  1 i915
output                  1871  1 video
e100                   28211  0 
mii                     4381  1 e100

---

### Post by lkraemer on 2010-09-26
OK,
Did you remove:

bcmwl5, and ssb, and the module ndiswrapper?

If so, ndiswrapper is still shown in your lsmod
output and in in the startup file.

You have to get those drivers removed before B43 will function correctly.

Your error message is because you opened nano in a Terminal session (window).
You need to exit nano with CNTL X, or use CNTL O to write the changes,
then use CNTL X to exit nano.  Then you may close the Terminal window.
If you have an open Terminal window with a file open in nano and close the window
it's telling you nano will be closed.


lk

---

### Post by adfriedman on 2010-09-27
lkraemer,
I think you may have overestimated my competence.  I'm not sure how to remove bcmwl5, and ssb, and the module ndiswrapper.  I went to the synaptic package manager and there is no bcmwl5 or ssb.  There are two ndiswrappers installed (ndiswrapper-utils-1.9 and ndiswrapper-common) and one bcmwl installed (bcmwl-modaliases.  However bcmwl-kernel-source has nothing listed under the installed version column.)  I removed the two ndiswrappers using the synaptic package manager.

Also, I assume the error message that you are referring to is "there is still a process running in the terminal.  Closing the terminal will kill it." I ran the command sudo nano /etc/modules and got the same screen.  I  hit CNTL O and then CNTL X in the terminal, but it didn't change anything.

I'm guessing I butchered your instructions.  What did I do wrong?
Thanks

---

### Post by lkraemer on 2010-09-28
OK, Follow these instructions one at a time:

1. Open a Terminal Console (Window) by:
Clicking on APPLICATIONS -> ACCESSORIES -> TERMINAL

(This in a "TERMINAL" or "CONSOLE" or "COMMAND WINDOW" versus the Graphics
User Interface - GUI and it gives you all kinds of access/possibilities
to use to maintain your system.  You will become more familiar as we go
along.)

(To exit the Terminal properly, you close any application you have open,
such as nano by using CNTL X, to get back to the prompt in the Terminal.
Now tap the ENTER Key a few times, and see what happens. Now type exit
and tap enter.  Now open a Terminal and proceed.)

UPPER CASE and lower case makes a difference on most commands.  The file or
directory (folder) named "Music" is different than "MUSIC" or music or MuSiC".

To see a dir listing type in:
```

ls -alt

```
Now scroll up and look for the Directory Music.
Now depress the UP ARROW Key, notice what was typed for you from a seaed history.
Depress the ENTER key.
Now type in (and press ENTER when done typing):
```

history

```
NICE! to run a previous command type !x where x is the number to the left of the
list of commands, to repeat a previous command.

A PROMPT like this "larry@larry-laptop:~$" means the logged in USER, because it ends with  a $, while a PROMPT
like # means you are a SUPERUSER (SU) or have "ADMINISTRATOR PRIVLEDGES".  You exit that mode by typing
"exit" (without the quotes, then press the ENTER Key.)

As for editing with nano, you need to remove the line that has:
```

ndiswrapper

```
then save the file with CNTL O, then CNTL X, which will dump you back out in the
Terminal.   
```

cat /etc/modules

```
will list the file, and you should see the line with ndiswrapper gone.
```

exit

```
will close the Terminal, without the error message.


OK, you are ready to proceed......
 
2.  Cut and Paste the following Commands, one at a time, then press the "ENTER" Key.
(Highlight the command string, use CNTL C to copy then CNTL V to paste.)

(Now it should be noted that since you removed lots of software from
the GUI with Synaptics, some commands like ndiswrapper -l, might not
work or there may be an error message if it isn't installed.  You may have to
go back and re-install the previous software you have removed, to be able
to repair your drivers.  But, go ahead and see what happens.)

If you need to re-install that software run Synaptics:
SYSTEM -> ADMINISTRATION -> SYNAPTICS PACKAGE MANAGER

Then go to the following Tab:
FILE -> HISTORY -> DAY_YOU_REMOVED_THE_SOFTWARE
to see a listing of REMOVED/INSTALLED SOFTWARE, and make a note of
the software that needs to be re-installed.  That will put you
back to where you need to be for the remainder of the process.
WHEW!!!

**REMOVE WINDOWS DRIVERS:**
If the output of ndiswrapper -l shows any drivers loaded,
remove ALL of them. If memory serves me correctly the command is:
```

sudo ndiswrapper -e bcmwl5

```
This should clean up nidswrapper & drivers and:
```

ndiswrapper -l

```
should return nothing as being loaded.

Then remove ndiswrapper:
```

sudo modprobe -r ndiswrapper

```
Remove from startup file by editing:
```

sudo nano /etc/modules

```
to remove ndiswrapper.

Now, That should fix the two conflicting drivers.

Now that you already have the firmware installed it should be simple.
Double check that you have the two folders b43 & b43legacy located at
/lib/firmware/b43 and /lib/firmware/b43legacy and that these folders have
*.fw files in them.

Now you just have to Enable the B43 Driver:
SYSTEM -> ADMINISTRATION ->HARDWARE DRIVERS
should have a B43 Driver listed a driver listed for your wireless,
if so enable it. (If by chance you have already ENABLED it, go ahead
and let it try to uninstall, then install it again by clicking again.)
It should find the drivers and load them, because the Firmware is where
it needs to be.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```
Check Network Manager (right click on the icon) to be sure the "Enable Wireless" box is checked (It should be ENABLED already by default.)

It shouldn't take more than 15 minutes......to get it working.

Check to see if you have wireless now. If not, you might need to
check the Loaded Modules, making sure there are no conflicts with other
Wifi drivers that might have been loaded, or others that cause conflicts.
```

lsmod

```
If it still isn't working, post the output of lsmod.

lk

---

### Post by adfriedman on 2010-10-03
lkraemer,
Thanks for trying, but I can't figure out what to do at all.  I opened the terminal and typed: dis ls -alt and history.  Under history, there were two lines that had only "ndiswrapper -l" in them.  Other lines had ndiswrapper with other things in the line like "sudo ndiswrapper -m" or "sudo modprobe ndiswrapper"    Even if I knew which ndiswrapper lines to remove with nano, I have absolutely no idea how to remove lines with nano (or even what that means.)  I can go into nano by typing nano, but then I have no clue what to do.  When I do type cat /etc/modules, in the regular terminal, it lists lp, b43,b43 and ndiswrapper, for what that's worth.
Adam

---

### Post by lkraemer on 2010-10-03
Adam,
You're making this way too hard.  Haven't you ever used Wordpad or
Notepad in Windows?  Nano is just another editor, that is available 
in Linux.  If you can use Notepad, Wordpad or Word, then you should
be able to use Nano.  Can you type and edit a Letter or Email?  

The second thing you need to be able to do is CUT & PASTE!  Can you do that
in Notepad, Wordpad, or Word?  Nano works the same.

What is the problem?

You're only other option is to locate a friend that has edit capabilities, and can
follow the previous instructions.  Have him read and then execute the instructions
one at a time.


**Let's try this.**
Open a Terminal Console (Window) by:
Clicking on APPLICATIONS -> ACCESSORIES -> TERMINAL

Copy & Paste these lines ONE AT A TIME into the Terminal Console, then press the
ENTER KEY.
```

sudo ndiswrapper -e bcmwl5

```

Then post the output of:
```

ndiswrapper -l

```

lk

---

### Post by adfriedman on 2010-10-03
The output from typing "ndiswrapper -l" was:
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common


Also, I can edit in nano, but what I don't understand is what I'm supposed to edit.  Am I supposed to copy the output of the history command into nano and then remove any lines with ndiswrapper in them and then copy and paste the revised history back into the terminal?

---

### Post by lkraemer on 2010-10-03
Adam,
To get the modules removed you will need to install ndiswrapper
so we can use it to remove the drivers.  I'd suggest using Synaptics
Package manager to install ndiswrapper-common.

You need to edit the file named modules located at /etc thus the command:
```

sudo nano /etc/modules

```

My file contains:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
#floppy

```

Yours contains:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
b43
b43
ndiswrapper

```

You need to make yours look like this:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
b43

```
(which removes the last two lines.......)
then save the file with CNTL O then CNTL X
to exit nano.

When you are done with that post the output of:
```

ndiswrapper -l
lsmod

```

lk

---

### Post by adfriedman on 2010-10-03
I was able to fix the output of sudo nano /etc/modules so it is now: just lp and b43

The output of "ndiswrapper -l" is still:
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common

---

### Post by lkraemer on 2010-10-03
OK, Good!  Now go to SYSTEM -> ADMINISTRATION -> SYNAPTICS PACKAGE MANAGER
and install ndiswrapper-common.

Then, post the output of the previous request.
```

ndiswrapper -l
lsmod

```

lk

---

### Post by adfriedman on 2010-10-03
Sorry, I forgot to install ndiswrapper-common last time like you instructed.  I just did it.  The output for ndiswrapper -l    lsmod is:


adam@adam-laptop:~$ ndiswrapper -l
Error: ndiswrapper-utils-1.9 not installed!
adam@adam-laptop:~$ lsmod
Module                  Size  Used by
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
binfmt_misc             6587  1 
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
arc4                    1153  2 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_seq_dummy           1338  0 
bitblit                 4707  1 fbcon
snd_seq_oss            26726  0 
softcursor              1189  1 bitblit
snd_seq_midi            4557  0 
vga16fb                11385  0 
snd_rawmidi            19056  1 snd_seq_midi
vgastate                8961  1 vga16fb
ppdev                   5259  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
b43                   163523  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 33024  0 
snd_timer              19098  2 snd_pcm,snd_seq
ssb                    38671  1 b43
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205146  1 b43
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           20408  1 
i915                  285586  3 
cfg80211              126517  2 b43,mac80211
soundcore               6620  1 snd
rsrc_nonstatic         10015  1 yenta_socket
drm_kms_helper         29297  1 i915
dell_wmi                1793  0 
led_class               2864  1 b43
joydev                  8708  0 
ndiswrapper           184677  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
intel_agp              24119  2 i915
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
drm                   162409  4 i915,drm_kms_helper
dell_laptop             6856  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
agpgart                31724  2 intel_agp,drm
dcdbas                  5422  1 dell_laptop
psmouse                63245  0 
serio_raw               3978  0 
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
e100                   28211  0 
mii                     4381  1 e100

---

### Post by lkraemer on 2010-10-03
Adam,
It appears we need the ndiswrapper utils 1.9 also installed.
Quickly install that via Synaptics Package manager, and then post
the output of:
```

ndiswrapper -l

```

I'm looking over the output of lsmod now.

Keep refreshing your page so we can get this wrapped up.

lk

---

### Post by adfriedman on 2010-10-03
I installed ndiswrapper utils 1.9.  Then I entered ndiswrapper -l and the terminal went nuts with a hugely long output.  I thought there might be a mistake so I closed the terminal, reopened it and I tried again.  The output was nothing, it just gave me the prompt again.  Here is the copy/paste from the terminal:
adam@adam-laptop:~$ ndiswrapper -l
adam@adam-laptop:~$ ndiswrapper -l
adam@adam-laptop:~$

---

### Post by lkraemer on 2010-10-03
Adam,

You have a typo......
```

ndiswrapper -l

```
isn't the same as you are trying.  USE COPY & PASTE from this post, then post the output
of ndiswrapper -l (It is a lower case "L".)


At this point you should be three commands from being done.  They are:
```

sudo ndiswrapper -e bcmwl5
sudo modprobe -r ndiswrapper
sudo /etc/init.d/networking restart

```

Keep refreshing/reloading your page so we can get this wrapped up tonight.

lk

---

### Post by adfriedman on 2010-10-03
I just copied and pasted from your post and got the same thing, nothing.  

adam@adam-laptop:~$ ndiswrapper -l
adam@adam-laptop:~$ 
 
and the l is a lower case l.  Also I tried the three commands.  It didn't restart, but I then restarted the computer manually.  The output from the three commands was:adam@adam-laptop:~$ sudo ndiswrapper -e bcmwl5
[sudo] password for adam: 
couldn't delete /etc/ndiswrapper/bcmwl5: No such file or directory
adam@adam-laptop:~$ sudo modprobe -r ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

adam@adam-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
adam@adam-laptop:~$

---

### Post by lkraemer on 2010-10-03
OK, post the output of lsmod again.  Let's see what it contains now.

I think what has happened is that when you un-installed ndiswrapper and the utils,
the drivers that were installed were removed.........which is what we were trying to do.

Next you need to go to the top right tool bar and hover your mouse over the network or Wifi icon and then
right click and make sure both Wifi and Networking are enabled.  Then left click over the Wifi Icon and
see what networks are available.

Then go to SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS
and if b43 is Avtivated, Remove b43, then Install b43 again.

Then see if you have any Wifi networks available to connect to.
You should see some Wifi networks available.

If not, then try a restart of Ubuntu.


lk

---

### Post by adfriedman on 2010-10-03
When I right click on the networking icon, I can't check the "Enable Wireless choice."  The text is actually slightly more gray than "enable networking" which is checked.  Also, when you say disable b43 in hardware drivers, do you mean to click "remove"?  Also, the output from lsmod is:
adam@adam-laptop:~$ lsmod
Module                  Size  Used by
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
arc4                    1153  2 
bitblit                 4707  1 fbcon
snd_seq_dummy           1338  0 
binfmt_misc             6587  1 
snd_seq_oss            26726  0 
softcursor              1189  1 bitblit
vga16fb                11385  0 
snd_seq_midi            4557  0 
b43                   163523  0 
vgastate                8961  1 vga16fb
snd_rawmidi            19056  1 snd_seq_midi
ssb                    38671  1 b43
ppdev                   5259  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
mac80211              205146  1 b43
pcmcia                 33024  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211              126517  2 b43,mac80211
i915                  285586  3 
snd_timer              19098  2 snd_pcm,snd_seq
led_class               2864  1 b43
drm_kms_helper         29297  1 i915
joydev                  8708  0 
drm                   162409  4 i915,drm_kms_helper
yenta_socket           20408  1 
lp                      7028  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           184677  0 
dell_wmi                1793  0 
rsrc_nonstatic         10015  1 yenta_socket
i2c_algo_bit            5028  1 i915
intel_agp              24119  2 i915
dell_laptop             6856  0 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
psmouse                63245  0 
serio_raw               3978  0 
parport                32635  2 ppdev,lp
agpgart                31724  2 drm,intel_agp
dcdbas                  5422  1 dell_laptop
video                  17375  1 i915
output                  1871  1 video
e100                   28211  0 
mii                     4381  1 e100
adam@adam-laptop:~$

---

### Post by lkraemer on 2010-10-03
Adam,
Yes, I guess it is Remove.  I'd have to dig out my old Compaq to make sure.
Just Remove the B43 Hardware Drivers.  Then go back and select the B43
to install in Hardware Drivers.

Then check the Wifi Enable and Wifi networks available.

Keep Reloading your pages so we can get this done faster.

lk

---

### Post by adfriedman on 2010-10-03
I just removed and then reinstalled the b43 but I still can't click on enable wireless.  I'm going to restart and try again.

---

### Post by adfriedman on 2010-10-03
I just removed and then reinstalled the b43 but I still can't click on enable wireless.  I'm going to restart and try again.

---

### Post by adfriedman on 2010-10-03
I just removed and then reinstalled the b43 but I still can't click on enable wireless.  I'm going to restart and try again.

---

### Post by adfriedman on 2010-10-03
I removed and downloaded and reinstalled but I still can't click on enable wireless

---

### Post by adfriedman on 2010-10-03
still didn't work

---

### Post by lkraemer on 2010-10-03
Adam,
Your *.fw files are still in the two folders b43 & b43legacy located at
/lib/firmware/b43 and /lib/firmware/b43legacy and that these folders have
*.fw files in them......aren't they?

I must have missed something.  This always works.

Can you connect via an Ethernet cable and get all the latest Updates?
Then try the Wifi.

lk

---

### Post by adfriedman on 2010-10-03
I checked, the files are still there.  Could my wireless card be broken?  Thanks for trying.  I appreciate the help.  I'm calling it a night, but if you think of anything else, I'm certainly willing to give it a try tomorrow.

Thanks again for your time and patience.
Adam

---

### Post by lkraemer on 2010-10-03
OK, I'll try my old Compaq with LiveCD.

I got it working from LiveCD by mounting my hard drive, and by using the following commands.
```

cd /
cd /lib
cd /firmware
mkdir b43
mkdir b43legacy
cd b43
sudo cp /media/26b1c6d7-36da-41c3-a16d-b21c0df8fe4b/lib/firmware/b43/* .
cd ..
cd b43legacy
sudo cp /media/26b1c6d7-36da-41c3-a16d-b21c0df8fe4b/lib/firmware/b43legacy/* .
exit

```
Then I activated the B43 Hardware Driver.

Wifi came up working in less than 15 minutes.

There still has to be a conflict somewhere, because I'm posting this from my old
Compaq with Broadcom 4318 hardware.


Also post the file created by:
```

history > adam.txt

```

Post the output of:
```

cat /etc/modprobe.d/blacklist.conf
lshw -C network

```

The problem is you have been through several mix-n-match methods in the beginning,
and there is a conflict with drivers, or software that you have already installed.
If you had followed just one method instead of three or four folks' methods it
would be working, but they were just trying to help.  I doubt there is anything
wrong with your hardware.

You can prove that by booting from the Ubuntu 10.04 LiveCD, then follow my directions
from:
**I got it working from LiveCD by....................**

You will just have to mount your hard drive, then go to /media and see what string
of numbers your drive has to replace mine.  ie..../media/26b1c6d7-36da-41c3-a16d-b21c0df8fe4b
is my UUID of my drive, your will be different....so just substitute your UUID numbers.
All this shouldn't take you more than 20 minutes of copy & pasting.

Then Activate the B43 Hardware Drivers.  Wifi should come up working.

I forgot to ask.....You don't have a Wifi Switch or special keystrokes to
"ENABLE" the Wifi on that Computer do you?  I assumed it was "ENABLED".
Some have a ON/OFF Switch, or CNTL F2 or other keystrokes to ENABLE Wifi.
DOUBLE CHECK........

lk

---

### Post by adfriedman on 2010-10-04
I had checked and there is no wireless switch, but I didn't realize that a keystroke could turn off the wireless on a Dell.  After all that FN+F2 was the solution (although some of your advice definitely helped me install the b43 driver.)  

I just did a ceremonial unplugging of the ethernet cable.  Thanks a million for the help.

---

### Post by lkraemer on 2010-10-04
Well, it was worth the effort, and you learned a bunch.

Glad you got it working.  I guess I assumed too much when I assumed you
were aware of how it could be toggled ON/OFF.

WHEW!

lk

---

