---
title: "installing wireless driver using ndiswrapper"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by arc_tangent on 2010-03-10
Hey guys,
I'm installing drivers to get my wireless to function, but I'm having trouble with the installation.  My big question is, do I need to find a new driver?  Or should I be using something other than ndiswrapper?


the chip I'm using is BCM 4311 (rev02)
PCI-ID 14e4:4319
Broadcom corporation

I was following this set of instructions:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The driver I am installing is sp32156, from:
[http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&lc=en&softwareitem=ob-38773-1](http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&lc=en&softwareitem=ob-38773-1)

I unpacked the .bin, .inf and .sys files that were required using cabextract.

not sure where to go from here.  I installed the driver properly.  Then I attempted to get it to recognize my wireless card, and it didn't.  So I can only assume that it's:

1. a problem with the driver
2. I shouldn't have used ndiswrapper
3. I used the wrong .sys file
4. some other difficulty that I'm unaware of


Here's some of the last few steps I took, including looking to see if i could get a network connection.  Which obviously didn't happen.

```
sarah@sarah-computer:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
sarah@sarah-computer:~$ tail /var/log/messages
Mar 10 20:38:22 sarah-computer kernel: [ 5645.756953] generic-usb 0003:046D:C03D.0003: input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.2-1/input0
Mar 10 21:56:38 sarah-computer kernel: [10342.215541] Disabling lock debugging due to kernel taint
Mar 10 21:56:38 sarah-computer kernel: [10342.223316] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Mar 10 21:56:38 sarah-computer kernel: [10342.273227] usbcore: registered new interface driver ndiswrapper
Mar 10 21:58:47 sarah-computer kernel: [10471.473614] eth0: link down
Mar 10 22:00:34 sarah-computer kernel: [10578.590479] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 10 22:01:24 sarah-computer pulseaudio[1446]: ratelimit.c: 99 events suppressed
Mar 10 22:01:42 sarah-computer pulseaudio[1446]: ratelimit.c: 73 events suppressed
Mar 10 22:01:54 sarah-computer pulseaudio[1446]: ratelimit.c: 72 events suppressed
Mar 10 22:02:56 sarah-computer pulseaudio[1446]: ratelimit.c: 75 events suppressed
sarah@sarah-computer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:cb:18:f6  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fecb:18f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:373366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:331279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:430887239 (430.8 MB)  TX bytes:150196830 (150.1 MB)
          Interrupt:21 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sarah@sarah-computer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```Any ideas?  Not sure where to go from here.

Thanks for your help, guys! :)

---

### Post by anewguy on 2010-03-10
Please post back the output of the following:

lspci

sudo ndiswrapper -l (that's a lower case "L" for "List")

Also - did you do the blacklist entries as mentioned in the 1 thread?  Without doing so, the wireless still will not work.  However, right now I don't even see your wireless at all.

We'll go from there.

Dave ;)

---

### Post by arc_tangent on 2010-03-10
Hey, thanks!  I totally didn't expect a reply so soon.  Here you go:

```
sarah@sarah-computer:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
01:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
01:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
01:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
01:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

``````
sarah@sarah-computer:~$ sudo ndiswrapper -l
[sudo] password for sarah: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4319) present (alternate driver: ssb)
sarah@sarah-computer:~$ 

```Yeah I did blacklist whatever was already present.  But I did that in a previous session.  Would I have had to do that again in this session?

---

### Post by anewguy on 2010-03-11
I noticed the output from the ndiswrapper list command shows the correct driver, but it also shows an alternate of ssb - ssb should have been blacklisted.

Try:

cat /etc/modprobe.d/blacklist and check the end of that to be sure bcm43xx, b43, b43legacy and ssb are all listed on separate lines beginning with "blacklist".  If need be:

sudo gedit /etc/modprobe.d/blacklist

and add as needed.  Save the file, then be sure to reboot, as the changes won't take effect until you reboot.


Also, I'm assuming you are running 9.10 - if not, the blacklist file has a different name.

Post back what you find out.

Dave ;)

EDIT:  Also, please post back the output of:

iwconfig

Thanks

---

### Post by arc_tangent on 2010-03-11
This is what I found!

```
sarah@sarah-computer:~$ cat /etc/modprobe.d/blacklist
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb

```before the reboot


Oh and here's the iwconfig entry
> sarah@sarah-computer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


---

### Post by lkraemer on 2010-03-11
Please specify what version of Ubuntu you are using.  Because, as of
Version 9.04, and later versions, the file name has been changed to
/etc/modprobe.d/blacklist.conf

And your listing of blacklist.conf looks suspicious since it has no
remarks etc.  So, I'd start by inserting these module names to be
blacklisted in the correct file, then delete /etc/modprobe.d/blacklist
file but keep /etc/modprobe.d/blacklist.conf.

When you have that done post the output of:
```

lsmod

```

If lsmod shows modules b43 bcm43xx b44 ssb and others installed you will
need to blacklist them, since you are using ndiswrapper.  You may have
to remove the following depending on what lsmod shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

```

To load the windows driver you should have used these commands:
```

sudo ndiswrapper -i bcmwl5.inf (Yours may be different as needed)
sudo ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
cd /etc
sudo gedit modules

```
( and add a new line to the end of the file. Type the following:
ndiswrapper <press enter>)

Now save the file and exit the editor.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

ifconfig
iwconfig
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```

Dave, I didn't mean to take over your answers.  Just trying to help.
Thanks!

lk

---

### Post by walt.smith1960 on 2010-03-11
trying to get a recalcitrant WiFi adapter to work. There is an app in the repositories which may or may not be helpful:NDISGTK. I haven't found the .inf and/or .sys files for my adapter yet so haven't tried it. Warning OT:  [rant]a pox on those who use an exe file to install device drivers[/rant]

---

### Post by anewguy on 2010-03-11
lkraemer - thank you for the clarification on the file name.  For some reason I was thinking backwards.  I had a feeling it was the file name at first, but then thought backwards to how the file naming actually changed so I thought it was okay.  This should fix their problem.

Thanks again!
Dave ;)

---

### Post by arc_tangent on 2010-03-11
Ikraemer:

> Please specify what version of Ubuntu you are using.I'm using 9.10. 

So do I input what I had done last time. but instead with the .conf?

Ahh thank you guys for helping me, this is so awesome! 

walt.smith: haha I was just following directions, honest!  
I have installed that app, but I'm attempting to get used to using the terminal right now.

---

### Post by arc_tangent on 2010-03-11
Here's the output

CODE]sarah@sarah-computer:/$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_intel8x0           30168  3 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
pcmcia                 36808  0 
snd_seq_midi            6464  0 
joydev                 10240  0 
snd_rawmidi            22176  1 snd_seq_midi
iptable_filter          3100  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ip_tables              11692  1 iptable_filter
yenta_socket           24296  1 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rsrc_nonstatic         11644  1 yenta_socket
x_tables               16544  1 ip_tables
snd                    59204  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
led_class               4096  1 sdhci
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                56500  0 
serio_raw               5280  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
8139too                22620  0 
usbhid                 38208  0 
usb_storage            52768  1 
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
ssb                    35524  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
[/CODE]

---

### Post by k3lt01 on 2010-03-11
As far as installing the correct driver goes you need to do a little more than what you have indicated to keep it where it should be. n.b. I wouldn't use ndisgtk for installing the driver as it has a problem remembering things when you reboot.

Anyway this is the process I use, I don't have to blacklist anything so I'm not up to date with that process anymore.

```
# Notes. Make sure drivers are visible on the Desktop then copy and paste each command into a terminal to install the wireless network drivers for your wireless card.

cd Desktop

sudo ndiswrapper -i yourcardsdriver.inf

ndiswrapper -l

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

echo "ndiswrapper"|sudo tee -a /etc/modules

sudo shutdown -r now
```

---

### Post by lkraemer on 2010-03-11
Yes, go ahead and make the edits, inserting the module names to be
blacklisted in the correct file.

Then delete /etc/modprobe.d/blacklist making sure you 
keep /etc/modprobe.d/blacklist.conf.

Open a Terminal Window:
```

cd /
cd /etc/modprobe.d
sudo rm blacklist
ls -alt
cd /

```

Then proceed with the remainder of my previous writeup, that pretty
well matches what k3lt01 is telling you.

Continue from:
If lsmod shows modules b43 bcm43xx b44 ssb and others installed you will
need to blacklist them, since you are using ndiswrapper. You may have
to remove the following depending on what lsmod shows:

and lsmod does show ssb as being loaded......

lk

---

### Post by arc_tangent on 2010-03-11
okay, thanks!

Just before I restart, here's the outputs (so if something goes wrong we can pinpoint down what happened o_o;;;;):

```
sarah@sarah-computer:/$ sudo rmmod ssb
sarah@sarah-computer:/$ lsmod
Module                  Size  Used by
ndiswrapper           185532  0 
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
pcmcia                 36808  0 
snd_seq_midi            6464  0 
joydev                 10240  0 
snd_rawmidi            22176  1 snd_seq_midi
iptable_filter          3100  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ip_tables              11692  1 iptable_filter
yenta_socket           24296  1 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rsrc_nonstatic         11644  1 yenta_socket
x_tables               16544  1 ip_tables
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
led_class               4096  1 sdhci
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                56500  0 
serio_raw               5280  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
8139too                22620  0 
usbhid                 38208  0 
usb_storage            52768  1 
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
sarah@sarah-computer:/$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
sarah@sarah-computer:/$ sudo ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4319) present (alternate driver: ssb)
sarah@sarah-computer:/$ sudo depmod -a
sarah@sarah-computer:/$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
sarah@sarah-computer:/$ sudo ndiswrapper -m
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

sarah@sarah-computer:/$ cd /etc
sarah@sarah-computer:/etc$ sudo gedit modules
sarah@sarah-computer:/etc$ 

```sudo gedit modules...

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

**ndiswrapper**


```


EDIT:

okay so I restarted my computer,

> sarah@sarah-computer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:cb:18:f6  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fecb:18f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2218672 (2.2 MB)  TX bytes:333156 (333.1 KB)
          Interrupt:21 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sarah@sarah-computer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


it didn't detect the wireless?

---

### Post by anewguy on 2010-03-12
When going through the manual steps of ndiswrapper, I normally have the user remove everything the ndiswrapper currently knows, to start with a clean slate.

So:

sudo ndiswrapper -l (lower case "L")

for what is returned:

sudo ndiswrapper -e xxxxxxxxx   where xxxxxxxxx is the driver returned in the ndiswrapper -l command.

Repeat this until the ndiswrapper -l command returns nothing.

Since this entire process has been done more than once, I would also advice manually editing the modules file to remove any references to ndiswrapper.  This gives a completely slate there as well to start with.

Once everything has been cleaned up (nothing returned on ndiswrapper -l, no reference to ndiswrapper in the modules file), then I would proceed with the manual ndiswrapper instructions.

I have done the manual use of ndiswrapper *MANY* times, and if done correctly in the correct order you shouldn't have a problem.  Just be sure to start with a clean slate.

I also noticed back when you did the ndiswrapper -l that it said bcmwl5 was being used as the driver - I seem to remember there is also a bcmwl5a or some such thing (it's been a while) that was supposed to cover the 43xx series.  Perhaps that might be needed instead of bcmwl5.  If after following all the steps you still have nothing, I would clean everything up again and try using bcmwl5a (if you need a link to it just post back).

I'll let lkraemer keep helping you now, but wanted to post back what I usually have had to do to "start over" again with ndiswrapper, namely being sure to have a clean slate to work with.

Dave ;)

EDIT: You may have already answered this, but....are you running 32-bit or 64-bit Ubuntu?  Are the driver files you downloaded for 32-bit or 64-bit Windows?

---

### Post by lkraemer on 2010-03-12
I tend to agree with Dave,

So, if the output of ndiswrapper -l shows any drivers loaded,
remove ALL of them. If memory serves me correctly the command is:
```

sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -e ssb

```
Then remove ndiswrapper:
```

sudo modprobe -r ndiswrapper

```
This should clean up nidswrapper & drivers and:
```

ndiswrapper -l

```
should return nothing as being loaded.

Open a Terminal & Check for errors:
```

dmesg tail
lsmod

```

You may have to remove the following depending on what lsmod shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

```

Once this is all straightened up..........

Make sure that the bcmwl5.sys & inf files are both located in the same folder.....
I'll assume broadcom.......
Go back and start with:
```

cd ~/Desktop/broadcom
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
lsmod
ifconfig
iwconfig

```
Then post the output of the last eight commands.


lk

---

### Post by anewguy on 2010-03-12
lkraemer:  Thanks again for your input.  BTW - I would verify with the user which version of Linux (32 vs 64 bit) and which driver (32 vs 64 bit) they are using as well - a mismatch could result in nothing happening as well.

Dave ;)

---

### Post by lkraemer on 2010-03-13
Dave,
You are so right.  I assumed that the correct driver was being used
for the 32 bit or 64 bit Ubuntu installed.

Thanks.

lk

---

### Post by anewguy on 2010-03-13
BTW - as a side note - your avatar reminds me of something from the mid 1970's.  I was a twenty-something professional then and was involved in a local astronomy club.  The guy who somehow got elected president one year was a *real* jerk, and when I first brought my homemade scope to a public viewing session (ground the mirror and everything, but hadn't "finished" the outward appearance of the scope or mount) he came by and really insulted it.  What I found amusing was that more of the public visitors were around my scope and looking through it than his "fancy" store-bought.  At any rate, since the outward appearance doesn't matter on a scope, I painted the thing Allis Chalmers orange just to tick him off.  Everyone got a big kick out of it.

I had completely forgotten about that until I saw your avatar!

Thanks for bringing back an amusing memory!

Dave ;)

---

