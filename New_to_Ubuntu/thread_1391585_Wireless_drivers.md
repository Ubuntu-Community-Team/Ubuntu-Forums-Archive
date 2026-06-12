---
title: "Wireless drivers"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by Lunami on 2010-01-27
Greetings to all, it's been quite a while since I been in here. A computer I was using, simply couldn't handle the 8.10 I was using, but I've returned with a new computer, and this is fairing much better with the last one. Now, for the most part, I've got everything that I wanted done, the only problem I'm having currently, is with the wireless drivers, and from there, I should be able to continue.

Now, using what I remember from before, I downloaded ndisgtk, and ndiswrapper, and attempted to install them, however, after running through every possible way I could think of, they all failed, and quite horribly. I'm currently, dual booting with Ubuntu 9.10, and Windows XP Home Edition on this machine (hoping to soon wipe Windows off, and making this an Ubuntu machine, but, this will be quite a while).

Is there something I'm missing?

I'm running a 1.7 processor, with 768 ram, and a dual hard drives with a total of 120 gigs of space. Far better than my last model. I've used Ubuntu before, but it's been at least a year since it's been used, so please dun mind me if I seem rusty, and ask a few questions, or for a bit of explaining on some things.

---

### Post by drzoo2 on 2010-01-27
> **Lunami said:**
> Greetings to all, it's been quite a while since I been in here. A computer I was using, simply couldn't handle the 8.10 I was using, but I've returned with a new computer, and this is fairing much better with the last one. Now, for the most part, I've got everything that I wanted done, the only problem I'm having currently, is with the wireless drivers, and from there, I should be able to continue.

Now, using what I remember from before, I downloaded ndisgtk, and ndiswrapper, and attempted to install them, however, after running through every possible way I could think of, they all failed, and quite horribly. I'm currently, dual booting with Ubuntu 9.10, and Windows XP Home Edition on this machine (hoping to soon wipe Windows off, and making this an Ubuntu machine, but, this will be quite a while).

Is there something I'm missing?

I'm running a 1.7 processor, with 768 ram, and a dual hard drives with a total of 120 gigs of space. Far better than my last model. I've used Ubuntu before, but it's been at least a year since it's been used, so please dun mind me if I seem rusty, and ask a few questions, or for a bit of explaining on some things.

What is the wireless chipset?

---

### Post by 3rdalbum on 2010-01-27
You should only use ndiswrapper if there's no native Linux driver for your wireless.

If the reason why your card didn't work out-of-the-box was because the wrong driver took control of it, then Ndiswrapper won't help.

Try searching for the name of your card (or the chipset - try `lspci` and `lsusb` commands to find this out) and the word "ubuntu" on Google for more help.

For instance: RTL8187 Ubuntu.

---

### Post by Lunami on 2010-01-27
The model is from Belkin, other than that, I can't give specifics, such as model. We lost the box ages ago. It's a PCI card however, with an antenna.

I've ran the lspci already, but nothing specific came up, that I saw. I'll be back in a moment or so as I copy / paste the console, only able to get online through windows.

---

### Post by 3rdalbum on 2010-01-27
Well, Belkin often seem to use Broadcom chipsets. Have you tried connecting your computer via Ethernet cable, refreshed the package list (System > Administration > Synaptic Package Manager, click the Reload button, close Synaptic) and then gone to the Hardware Drivers program and seen if it suggests a driver for you to download?

---

### Post by Lunami on 2010-01-27
Results of my lsusb
> lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

As for ethernet, I'm not able to do that without unhooking the computer, and setting it up in a different room. I'd like to exhaust other ideas first before doing such a thing.

---

### Post by Lunami on 2010-01-27
Quick little update here, I did something, not sure what, but when I open up the hardware something or other (just woke up, bare with me) under system, and administrative, something like that, and there popped up something for Broadcom b43, or something similar. I click activate, but it does nothing, either continues to scan for forever, or doesn't move at all.

Also, I continue to find this error here when deal with .deb packages.

> Broken dependencies

Your system has broken dependencies. This application cannot continue until this is fixed. To fix it run 'gksudo synaptic' or 'sudo apt get install -f' in a terminal window.


Any help would be greatly appreciated.

---

### Post by lkraemer on 2010-01-27
These commands will give you more information and you can post the results:
```

lspci
lsusb
lshw -C network
lsmod
cat /etc/modprobe.d/blacklist
             OR for => 9.04 use cat /etc/modprobe.d/blacklist.conf
ndiswrapper -l
iwconfig

```

lk

---

### Post by skymera on 2010-01-27
```
 02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 
```
 
A Broadcom chip inside your wireless card. as far as i know, there is a tool for sorting out the firmware.
There was a thread yesterday about it. The tool is

```
 b43-fwcutter (1:012-1) Utility for extracting Broadcom 43xx firmware

```
i think

---

### Post by Lunami on 2010-01-27
> lunami@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
lunami@ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam 100
Bus 001 Device 003: ID 154b:0005 PNY 
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
lunami@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:ef000000-ef001fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:40:ca:b5:a3:ee
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:11 ioport:c000(size=256) memory:ef002000-ef0020ff memory:30000000-3000ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:50:f5:0e:f0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
lunami@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
gspca_spca561           9372  0 
gspca_main             22812  1 gspca_spca561
videodev               36736  1 gspca_main
v4l1_compat            14496  1 videodev
snd_wavefront          37332  0 
arc4                    1660  2 
snd_cs4236             29620  0 
snd_wss_lib            26012  2 snd_wavefront,snd_cs4236
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ecb                     2524  2 
b43                   122136  0 
snd_opl3_lib           10396  2 snd_wavefront,snd_cs4236
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_hwdep               7200  2 snd_wavefront,snd_opl3_lib
snd_mpu401              7016  0 
snd_mpu401_uart         6940  3 snd_wavefront,snd_cs4236,snd_mpu401
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_pcm                75296  5 snd_cs4236,snd_wss_lib,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
x_tables               16544  1 ip_tables
snd_timer              22276  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device          6920  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              181236  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  1 b43
snd                    59204  21 snd_wavefront,snd_cs4236,snd_wss_lib,snd_intel8x0,snd_ac97_codec,snd_opl3_lib,snd_pcm_oss,snd_mixer_oss,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   6688  0 
psmouse                56180  0 
serio_raw               5280  0 
snd_page_alloc          9156  3 snd_wss_lib,snd_intel8x0,snd_pcm
lp                      8964  0 
shpchp                 32272  0 
soundcore               7264  1 snd
parport_pc             31940  1 
parport                35340  3 ppdev,lp,parport_pc
ns558                   5404  0 
gameport               11368  2 ns558
usb_storage            52544  1 
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
ssb                    35300  1 b43
floppy                 54916  0 
intel_agp              27484  1 
agpgart                34988  1 intel_agp
lunami@ubuntu:~$ cat /etc/modprobe.d/blacklist
cat: /etc/modprobe.d/blacklist: No such file or directory
lunami@ubuntu:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
ndiswrapper: command not found
lunami@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Again Ikraemer, I don't have ndiswrapper, the installation process failed, due to the error I listed in my last post, with the dependency.

@Skymera
I downloaded this program, I'll try it now, and report my findings soon. However, I'm expecting the dependency issue to arrise again.

---

### Post by Lunami on 2010-01-27
> lunami@ubuntu:~$ sudo dpkg -i '/home/lunami/Desktop/Link to My Documents/Downloads/b43-fwcutter_012-1_i386.deb' 
[sudo] password for lunami: 
Selecting previously deselected package b43-fwcutter.
(Reading database ... 114112 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_012-1_i386.deb) ...
Setting up b43-fwcutter (1:012-1) ...
--2010-01-26 23:27:54--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--install):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for man-db ...
Errors were encountered while processing:
 b43-fwcutter



What I get after trying to install the program listed by Skymera.

---

### Post by Lunami on 2010-01-27
Anyone at all?
I'm going to be here a while, and yes, I'm still looking this up, but nothing more than things I've already seen. From what I can tell, the biggest issue is the dependency, and the driver from Hardware Drivers not doing anything. I have to do some things in a few, but after this, if nothing else pops up on here, I will attempt to hook this computer up via ethernet, and hope that it does something.

---

### Post by bkratz on 2010-01-27
You do have to have an ethernet connection to download. anyway try this thread ---the second half if you don't have a connection

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Lunami on 2010-01-27
I've tried that before, but did so again. Same thing, nothing. The .iso was burned to a DVD, and isn't being read in my dvd drive (that isn't a burner). Perhaps it seems the only way to resolve this issue is through moving the pc... I really didn't want to have to do that, but seems there's no other choice.

---

### Post by lkraemer on 2010-01-27
lunami,
It's OK that you didn't have ndiswrapper installed.
My instructions were generic so I knew what was and was not
installed, so I could try and get as much info as possible with
out making multiple postings......

Ubuntu 9.10 works with the extracted firmware, because I
posted here:
[http://ubuntuforums.org/showthread.php?t=1314852](http://ubuntuforums.org/showthread.php?t=1314852)
with specific results from other testing.  Posting #3

Looks like you need an Ethernet connection OR
you can try to insert the firmware downloaded from here to
/lib/firmware for the Broadcom card. (It will do the same
thing as using b43fwcutter to extract the firmware)
[http://www.omattos.com/node/6](http://www.omattos.com/node/6)
With the downloaded file, extracted on your desktop....
```

cd /
sudo mkdir -p /lib/firmware/b43
sudo mkdir -p /lib/firmware/b43legacy
sudo cp -r /home/loginname/Desktop/b43* /lib/firmware

```
Now go try and activate your hardware drivers:
SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS

Then do:
```

sudo /etc/init.d/networking restart

```
Wait a few minutes......

Post the output of:
```

ifconfig
iwconfig

```
iwconfig should display something like the following:
```

ath0      IEEE 802.11g  ESSID:"Airlink"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:A3:91:B0:B2   
          Bit Rate:24 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-38 dBm  Noise level=-95 dBm
          Rx invalid nwid:57687  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Yours may be wlan0, instead of ath0.....

At this point you know your Router's ESSID, that ath0 (in my case) is the
router, and you should be able to bring it up manually.
Replace the <interface> below with your actual interface.
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```

In my case it would be:
```

sudo ifconfig ath0 down
sudo dhclient -r ath0
sudo iwconfig ath0 essid "Airlink"
sudo iwconfig ath0 mode Managed
sudo ifconfig ath0 up
sudo dhclient ath0

```

lk

---

### Post by Lunami on 2010-01-27
Got this to work, thank you. Just had to set the computer up with wireless, and that fixed the dependency error, everything started to run fine. Tested the wireless for a bit (when I was using 8.10, the connection was VERY choppy, I see slight improvements now). Seems the computer can handle ubuntu much better now. Thanks for the help everyone.

---

