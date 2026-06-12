---
title: "Ubuntu 9.10 can't Detect My Wirless Network"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by mogui_666 on 2009-11-20
Hi,

after upgrading to ubuntu 9.10, ubuntu suddenly can't detect my wireless network. it has detect all my neighborhood network except mine.

please help. Thanks in advance=)

---

### Post by wrgb2 on 2009-11-20
Do you have a network manager icon in the notification area?  If so, what do you see when you click on it?

---

### Post by ukripper on 2009-11-20
> **mogui_666 said:**
> Hi,

after upgrading to ubuntu 9.10, ubuntu suddenly can't detect my wireless network. it has detect all my neighborhood network except mine.

please help. Thanks in advance=)

can you post output of the following:
```
lsmod
```

```
iwconfig
```

---

### Post by Don1500 on 2009-11-20
bump

---

### Post by mogui_666 on 2009-11-20
when i key in "Ismod", this is what it show.

```
Module                  Size  Used by
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_ice1712            57668  0 
snd_ice17xx_ak4xxx      3420  1 snd_ice1712
snd_ak4xxx_adda         8028  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              7708  1 snd_ice1712
snd_ac97_codec        101216  1 snd_ice1712
ac97_bus                1532  1 snd_ac97_codec
snd_i2c                 5148  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         6940  1 snd_ice1712
binfmt_misc             8356  1 
rt2870sta             488820  0 
arc4                    1660  2 
ecb                     2524  2 
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
snd_hwdep               7200  1 snd_hda_codec
mac80211              181236  2 rt2x00usb,rt2x00lib
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  5 snd_hda_intel,snd_hda_codec,snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211               93052  2 rt2x00lib,mac80211
snd                    59204  22 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_i2c,snd_mpu401_uart,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
i2c_nforce2             6784  0 
serio_raw               5280  0 
crc_ccitt               1852  1 rt2800usb
ppdev                   6688  0 
parport_pc             31940  1 
soundcore               7264  1 snd
nvidia               9586440  36 
agpgart                34988  1 nvidia
joydev                 10272  0 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
lp                      8964  0 
x_tables               16544  1 ip_tables
parport                35340  3 ppdev,parport_pc,lp
hid_sunplus             1852  0 
usbhid                 38208  0 
usb_storage            52544  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
forcedeth              54152  0 


```

and when i key in "iwconfig", this is wat the screen show:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=2 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

thank for the help=)

---

### Post by Miroslav011 on 2009-11-20
Hi,

I've just installed ubuntu 9.10 and I'm having a smilar problem.  Except I can't see any wireless networks when I click on the network thing at the top right.

BTW I'm a complete Linux noob.  Any help is appreciated.

---

### Post by Saghaulor on 2009-11-20
Read this thread, it will help you a lot.

[http://ubuntuforums.org/showthread.php?t=571188&highlight=ack+driver+failed]("http://ubuntuforums.org/showthread.php?t=571188&highlight=ack+driver+failed")

It has just about everything you would need to get you rolling.

First I would make sure your wifi card is even there. ```
sudo ifconfig
```

Then, if it is, I would make sure that it is working properly. ```
sudo iwlist "your_network_card_name_ie_wlan0" scan
```

Then verify that it can see your network by making sure it showed up in the list.

After you get this far, then it gets a bit more in depth. Let's first make sure your network card is working and can see your network.

---

### Post by Miroslav011 on 2009-11-20
Thanks for the tip Saghaulor.  I will try that ASAP.

---

### Post by mogui_666 on 2009-11-20
oh my router is D-Link DIR-615 and my wireless adapter is D-Link DWA-140

---

### Post by Saghaulor on 2009-11-20
> **mogui_666 said:**
> oh my router is D-Link DIR-615 and my wireless adapter is D-Link DWA-140

If you ran the commands that I specified, and included the readout in a post, that would help.

Mogui_666, we've determined that your wifi card is recognized, now we need to figure out if its working. Please run the ```
sudo iwlist wlan0 scan
``` command.

---

### Post by Miroslav011 on 2009-11-20
[SIZE=2][COLOR=Black]It appears that it's not detecting my wireless card.  I have a Dell Vostro 1720 if that helps and the wireless card is the [/COLOR][/SIZE][FONT=Arial][SIZE=2][COLOR=Black]**Dell Wireless 1510 802.11a/g/n Draft Mini Card**[/COLOR][/SIZE][/FONT]

---

### Post by Saghaulor on 2009-11-20
> **Miroslav011 said:**
> [SIZE=2][COLOR=Black]It appears that it's not detecting my wireless card.  I have a Dell Vostro 1720 if that helps and the wireless card is the [/COLOR][/SIZE][FONT=Arial][SIZE=2][COLOR=Black]**Dell Wireless 1510 802.11a/g/n Draft Mini Card**[/COLOR][/SIZE][/FONT]

Post the output of ```
sudo ifconfig
``` and ```
sudo lspci
``` ```
sudo lsusb
``` ```
sudo lsmod
```

---

### Post by Miroslav011 on 2009-11-20
> **Saghaulor said:**
> Post the output of ```
sudo ifconfig
``` and ```
sudo lspci
``` ```
sudo lsusb
``` ```
sudo lsmod
```

> eth0      Link encap:Ethernet  HWaddr 00:21:70:f5:cd:16  
          inet addr:192.168.1.55  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fef5:cd16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22093 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1273 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3033545 (3.0 MB)  TX bytes:214300 (214.3 KB)
          Interrupt:32 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GS] (rev a1)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0e:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)
> Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c525 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
> Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
b43                   122136  0 
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
mac80211              181236  1 b43
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
dell_wmi                2564  0 
snd_timer              22276  2 snd_pcm,snd_seq
sdhci_pci               7100  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3100  0 
sdhci                  17472  1 sdhci_pci
ip_tables              11692  1 iptable_filter
cfg80211               93052  2 b43,mac80211
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56180  0 
soundcore               7264  1 snd
lp                      8964  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
serio_raw               5280  0 
led_class               4096  2 b43,sdhci
x_tables               16544  1 ip_tables
dcdbas                  7292  0 
parport                35340  2 ppdev,lp
joydev                 10272  0 
usbhid                 38208  0 
ohci1394               29900  0 
r8169                  32064  0 
mii                     5212  1 r8169
ssb                    35300  1 b43
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video
intel_agp              27484  0 
agpgart                34988  1 intel_agp
 That's all.

---

### Post by Saghaulor on 2009-11-20
Great, we're almost done. (I think.)

You've got a Broadcom chipset for your wifi. The drivers are not installed by default. I had the same issue with my netbook.

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GS] (rev a1)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
**0e:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)**
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01) 

You just need to install the drivers.

```
sudo aptitude install bcmwl-kernel-source
```

That should install the drivers to your wifi card.

Then see if your wifi card is showing up.

---

### Post by Miroslav011 on 2009-11-20
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "bcmwl-kernel-source"
Couldn't find any package whose name or description matched "bcmwl-kernel-source"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

---

### Post by Saghaulor on 2009-11-20
Maybe I typed it wrong.

```
apt-cache search broadcom
```

That should list anything related to broadcom that is listed in your repository cache.

Basically, you're looking for the package that I described. Once you get the name of it, install it the same way I previously instructed.

---

### Post by Miroslav011 on 2009-11-20
This is what I've done.

> apt-cache search broadcom
bcmwl-modaliases - Modaliases for the Broadcom 802.11 Linux STA driver

then

> sudo aptitude install bcmwl-modaliases
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Still nothing :S

---

### Post by Saghaulor on 2009-11-20
> **Miroslav011 said:**
> This is what I've done.



then



Still nothing :S

Do you have Proprietary Drivers and Software Restricted by copyright or legal issues enabled in your Software Sources? Make sure to ```
sudo aptitude update
``` before searching again.

---

### Post by Miroslav011 on 2009-11-20
I had literally just finished installing Ubuntu 5minutes prior.  And I have no knowledge of Linux whatsoever.  I'm learning as I go along.  So I haven't done any 'updates' I guess.

---

### Post by Saghaulor on 2009-11-20
> **Miroslav011 said:**
> I had literally just finished installing Ubuntu 5minutes prior.  And I have no knowledge of Linux whatsoever.  I'm learning as I go along.  So I haven't done any 'updates' I guess.

Oh, okay, then do the following.

Go to System->Administraton->Software Sources, and verify what I indicated.

Then do this. 

```
sudo aptitude update
```

```
sudo aptitude upgrade
```

Then after that's done, then look for your broadcom drivers.

---

### Post by Yanno on 2009-11-20
Go and download a folder called "b43-fwcutter-011",unzip it.Enter the folder in Terminal and type "make" then everything goes well.

---

### Post by Miroslav011 on 2009-11-20
I've done 

sudo aptitude update

then

sudo aptitude install bcmwl-kernel-source

and that installed

Now I'm updating everything I've missed since the CD was in the mail.

Is this generally a good way to go about things?  Installing updates all at once I mean, and how do I know which ones I need?

---

### Post by matthewbpt on 2009-11-20
I had a similar problem with the Broadcom card, the package manager says the package is installed but the driver still doesn't work. Try this,

[code]sudo apt-get remove bcmwl-kernel-source bcmwl-modaliases && sudo apt-get install bcmwl-kernel-source bcmwl-modaliases
sudo rmmod b43
sudo rmmod ssb
sudo modprobe wl[code]

The wireless should work now. Hope that helps!

---

### Post by Saghaulor on 2009-11-20
> **Miroslav011 said:**
> I've done 

sudo aptitude update

then

sudo aptitude install bcmwl-kernel-source

and that installed

Now I'm updating everything I've missed since the CD was in the mail.

Is this generally a good way to go about things?  Installing updates all at once I mean, and how do I know which ones I need?

Is your wireless working now?

Also, yes, installing mass updates with aptitude is fine. It's intelligent and can sort out that stuff. Also, yes, you want to install all the updates, as it only installs updates to what is actually installed on your computer. Any security hole should be patched.

---

### Post by ukripper on 2009-11-20
Anyone needs more info can see this bug report - [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/443185](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/443185)

---

### Post by Miroslav011 on 2009-11-20
Still not working, tried matthew's solution, still not working

> sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules


The wireless card is active, but when I go to Wireless Connections nothing shows up.

---

### Post by RwandaTim on 2009-11-20
Not sure what type of computer you're using.  I have a Dell Studio and wasn't able to get my wireless card to work.  I found the solution quickly and easily in the following thread: [http://ubuntuforums.org/showthread.php?t=1326140](http://ubuntuforums.org/showthread.php?t=1326140).  

Best of luck!

---

### Post by Miroslav011 on 2009-11-20
> **Yanno said:**
> Go and download a folder called "b43-fwcutter-011",unzip it.Enter the folder in Terminal and type "make" then everything goes well.

Where do I download this from?

---

### Post by Saghaulor on 2009-11-20
Have you tried restarting since you installed the drivers?

---

### Post by Miroslav011 on 2009-11-20
> **Saghaulor said:**
> Have you tried restarting since you installed the drivers?

Twice.

---

### Post by Saghaulor on 2009-11-20
> **Miroslav011 said:**
> Twice.

I hope that removing that module isn't going to complicate these matters.

I'm assuming your wifi card is showing up as 'wlan0'

Try ```
sudo iwlist wlan0 scan
```

See if that shows anything.

---

### Post by Miroslav011 on 2009-11-20
> **Saghaulor said:**
> I hope that removing that module isn't going to complicate these matters.

I'm assuming your wifi card is showing up as 'wlan0'

Try ```
sudo iwlist wlan0 scan
```See if that shows anything.


> sudo ifconfig
[sudo] password for snicla: 
eth0      Link encap:Ethernet  HWaddr 00:21:70:f5:cd:16  
          inet addr:192.168.1.55  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fef5:cd16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3893 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7265842 (7.2 MB)  TX bytes:527403 (527.4 KB)
          Interrupt:32 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:24:2b:af:91:99  
          inet6 addr: fe80::224:2bff:feaf:9199/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:273
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

> sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

So I have no clue what's going on with it.

---

### Post by Miroslav011 on 2009-11-20
I ran **sudo iwconfig**

```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:44 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received

```

---

### Post by Miroslav011 on 2009-11-20
Anyways it's Friday and my mouse just died on the Linux laptop so I'll call it a day.  Thanks for trying to help.  And my apologies for hijacking this thread.

I'll be back hopefully Sunday to try and figure this out.  If anyone has any other ideas, please feel free to post them.  I really enjoy Ubuntu so far.

---

### Post by Saghaulor on 2009-11-20
> **Miroslav011 said:**
> Anyways it's Friday and my mouse just died on the Linux laptop so I'll call it a day.  Thanks for trying to help.  And my apologies for hijacking this thread.

I'll be back hopefully Sunday to try and figure this out.  If anyone has any other ideas, please feel free to post them.  I really enjoy Ubuntu so far.

Hey, hopefully I can help you get this resolved. I'm glad that you enjoy Ubuntu. I certainly do and I'm very happy with the community. Most members are very quick to help. I've gotten a lot of help so now I try to give back when I can.

I don't believe that the drivers are installed correctly as nothing indicates that you have a wireless card.

Perhaps we should start from the beginning.

Let's remove everything related to the broadcom.

```
sudo aptitude purge bcmwl-kernel-source bcmwl-modaliases b43-fwcutter bcm5700-source
```

Then reinstall.

```
sudo aptitude install bcmwl-kernel-source bcmwl-modaliases
```

Then reboot.

```
sudo shutdown -r now
```

Then see if it's showing up.

```
sudo ifconfig
```

---

### Post by mogui_666 on 2009-11-21
> **Saghaulor said:**
> If you ran the commands that I specified, and included the readout in a post, that would help.

Mogui_666, we've determined that your wifi card is recognized, now we need to figure out if its working. Please run the ```
sudo iwlist wlan0 scan
``` command.

Hi Saghaulor,

thanks for the help, here is what it display:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:1A:C4:5C:8D:69
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-190 dBm  
                    Encryption key:on
                    ESSID:"2WIRE212"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001f378051548
                    Extra: Last beacon: 1020ms ago
                    IE: Unknown: 00083257495245323132
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 02 - Address: 00:14:7F:35:6C:C1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-187 dBm  
                    Encryption key:on
                    ESSID:"SpeedTouch2483E6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001b54ae52c
                    Extra: Last beacon: 1072ms ago
                    IE: Unknown: 00105370656564546F756368323438334536
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020000

```

---

### Post by Miroslav011 on 2009-11-21
> **Saghaulor said:**
> Hey, hopefully I can help you get this resolved. I'm glad that you enjoy Ubuntu. I certainly do and I'm very happy with the community. Most members are very quick to help. I've gotten a lot of help so now I try to give back when I can.

I don't believe that the drivers are installed correctly as nothing indicates that you have a wireless card.

Perhaps we should start from the beginning.

Let's remove everything related to the broadcom.

```
sudo aptitude purge bcmwl-kernel-source bcmwl-modaliases b43-fwcutter bcm5700-source
```Then reinstall.

```
sudo aptitude install bcmwl-kernel-source bcmwl-modaliases
```Then reboot.

```
sudo shutdown -r now
```Then see if it's showing up.

```
sudo ifconfig
```

```
 
eth0      Link encap:Ethernet  HWaddr 00:21:70:f5:cd:16  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fef5:cd16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4042 (4.0 KB)  TX bytes:5491 (5.4 KB)
          Interrupt:32 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:24:2b:af:91:99  
          inet6 addr: fe80::224:2bff:feaf:9199/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:271
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

---

### Post by Miroslav011 on 2009-11-22
Problem is fixed.  Actually, I think it was fixed on Friday but I wasn't doing it properly.  Either way, thank you for your help :)  It's very much appreciated.

Now to experiment with Ubuntu. :D

---

### Post by chwdhw on 2009-11-22
Running into similar problems here.  Just installed Ubuntu a couple days ago and now getting going but see that it doesn't recognize the D-link DWL-G510 wireless adaptor I have and shows no network connection. Starting at the beginning of this thread's recommendation I see the following
 
white@white-desktop:~$ lsmod
Module Size Used by
isofs 31620 1 
udf 80900 0 
crc_itu_t 1852 1 udf
binfmt_misc 8356 1 
ppdev 6688 0 
snd_intel8x0 30168 5 
snd_ac97_codec 101216 1 snd_intel8x0
ac97_bus 1532 1 snd_ac97_codec
snd_pcm_oss 37920 0 
snd_mixer_oss 16028 1 snd_pcm_oss
snd_pcm 75296 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy 2656 0 
snd_seq_oss 28576 0 
snd_seq_midi 6432 0 
snd_rawmidi 22208 1 snd_seq_midi
snd_seq_midi_event 6940 2 snd_seq_oss,snd_seq_midi
iptable_filter 3100 0 
snd_seq 50224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 22276 5 snd_pcm,snd_seq
usblp 12636 0 
lp 8964 0 
parport 35340 2 ppdev,lp
ip_tables 11692 1 iptable_filter
snd_seq_device 6920 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usbhid 38208 0 
shpchp 32272 0 
snd 59204 17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse 56180 0 
soundcore 7264 1 snd
serio_raw 5280 0 
snd_page_alloc 9156 2 snd_intel8x0,snd_pcm
x_tables 16544 1 ip_tables
usb_storage 52544 1 
8139too 22620 0 
8139cp 19260 0 
mii 5212 2 8139too,8139cp
output 2780 0 
intel_agp 27484 1 
agpgart 34988 2 intel_agp
white@white-desktop:~$ ^C
white@white-desktop:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
&#12288;
&#12288;
What might the next step be?

---

### Post by ukripper on 2009-11-23
> **chwdhw said:**
> Running into similar problems here.  Just installed Ubuntu a couple days ago and now getting going but see that it doesn't recognize the D-link DWL-G510 wireless adaptor I have and shows no network connection. Starting at the beginning of this thread's recommendation I see the following
 
white@white-desktop:~$ lsmod
Module Size Used by
isofs 31620 1 
udf 80900 0 
crc_itu_t 1852 1 udf
binfmt_misc 8356 1 
ppdev 6688 0 
snd_intel8x0 30168 5 
snd_ac97_codec 101216 1 snd_intel8x0
ac97_bus 1532 1 snd_ac97_codec
snd_pcm_oss 37920 0 
snd_mixer_oss 16028 1 snd_pcm_oss
snd_pcm 75296 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy 2656 0 
snd_seq_oss 28576 0 
snd_seq_midi 6432 0 
snd_rawmidi 22208 1 snd_seq_midi
snd_seq_midi_event 6940 2 snd_seq_oss,snd_seq_midi
iptable_filter 3100 0 
snd_seq 50224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 22276 5 snd_pcm,snd_seq
usblp 12636 0 
lp 8964 0 
parport 35340 2 ppdev,lp
ip_tables 11692 1 iptable_filter
snd_seq_device 6920 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usbhid 38208 0 
shpchp 32272 0 
snd 59204 17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse 56180 0 
soundcore 7264 1 snd
serio_raw 5280 0 
snd_page_alloc 9156 2 snd_intel8x0,snd_pcm
x_tables 16544 1 ip_tables
usb_storage 52544 1 
8139too 22620 0 
8139cp 19260 0 
mii 5212 2 8139too,8139cp
output 2780 0 
intel_agp 27484 1 
agpgart 34988 2 intel_agp
white@white-desktop:~$ ^C
white@white-desktop:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
&#12288;
&#12288;
What might the next step be?

can you post output of this command too:
```
lspci
```

---

### Post by Saghaulor on 2009-11-23
> **ukripper said:**
> can you post output of this command too:
```
lspci
```
Also do ```
sudo lsusb
``` if your Dlink is a usb card.

---

### Post by mogui_666 on 2009-11-24
> **Saghaulor said:**
> Also do ```
sudo lsusb
``` if your Dlink is a usb card.

this is what i get when i type "lspci"

```
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
02:06.0 USB Controller: NEC Corporation USB (rev 43)
02:06.1 USB Controller: NEC Corporation USB (rev 43)
02:06.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
02:07.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
02:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

for "sudo lsusb", this is what i get:

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 07d1:3c09 D-Link System DWA-140 802.11n Adapter [ralink rt2870]
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by Saghaulor on 2009-11-24
> Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 004: ID 07d1:3c09 D-Link System DWA-140 802.11n Adapter [ralink rt2870]**
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

There's your wifi card.

You have the Ralink chipset.

This seems to be what you need.

[http://www.apfelkraut.org/2009/02/howto-wlan-ralink-rt2870-usb-stick-kubuntu-810/]("http://www.apfelkraut.org/2009/02/howto-wlan-ralink-rt2870-usb-stick-kubuntu-810/")

And here's this if that doesn't help. 

[http://ubuntuforums.org/showthread.php?t=960642]("http://ubuntuforums.org/showthread.php?t=960642")

Good luck.

---

### Post by mogui_666 on 2009-11-24
Hi Saghaulor,

thanks for your help. i think I am still not smart enough to use Ubuntu.

Thanks for the help again=)

---

### Post by Saghaulor on 2009-11-25
> **mogui_666 said:**
> Hi Saghaulor,

thanks for your help. i think I am still not smart enough to use Ubuntu.

Thanks for the help again=)

You're smart enough, and gosh darnit, you're good enough. You're not used to the way Ubuntu works, and that's fine. It's something different which takes a little getting used to. You're doing great.

I'll try to help you some more.

So where are you at now?

---

### Post by mogui_666 on 2009-11-25
Hi Saghaulor,

thanks you very much for your precious time and help. but i have uninstall ubuntu from my computer already.

thanks again.

---

### Post by 4everraj on 2009-12-04
> 
rajaneesh@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
rajaneesh@ubuntu:~$ sudo lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0408:03ba Quanta Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 138a:0001 DigitalPersona, Inc Fingeprint Reader
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 062a:6301 Creative Labs 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



This is what I got as output of those two commands. Now I don't know how to proceed from here.

---

### Post by ukripper on 2009-12-04
> **4everraj said:**
> This is what I got as output of those two commands. Now I don't know how to proceed from here.

if you are using ubuntu 9.10.
Follow this as you have BCM4312 wireless card. This will work fine for you.


Run this in a terminal:

```
sudo apt-get install bcmwl-kernel-source
```
Reboot Ubuntu

 Go to System-->Administration-->Hardware drivers and check the use Broadcom sta wireless driver is listed and if it is not green then make sure LED turns green.

---

### Post by eopi on 2009-12-26
**Saghaulor **you can feel free to help me out.  I've been working on this problem for **2 years now**, I waited **10 months** for the new release but it didn't quite fix it. 

I have a Vostro 1500 and I definitely have BroadCom - wireless card and I think it's working, see why below. 

I have 9.10 Karmic and when I plug in cable line, ethernet, it read Auto Eth0 - it's working perfectly. 

Then when I go to Network manager I read Wired Network and Wireless Networks.  I can't click into Wireless Networks, greyed out. 

But When I go to VPN Connections, Connnect to Hidden Wireless Network and Create New Wireless Network, I can actually see that it's read the name of my wireless network name, the name I assigned to my wireless signal.

Then when I go to connect to hidden wireless network and select "Connection:"  my wireless name, ...

Everything Greys out, Network Name:, Wireless Security (WPA &WPA2 Persona) and Password, it all Greys out and then "Connect" also greys out and only Cancel is avaiable as an option.

New Wireless Network also greys out.

Any thoughts?

Hopefully there is a quick and easy fix here, maybe I'm overlooking something very easy to connect to wireless signal.

After 2 years of trying to fix this maybe I should just buy the perfect Laptop- **Saghaulor what is the perfect laptop and wireless card? Just in case ...**

It's just that everytime I try to fix this problem I age exponentially. :P

---

### Post by Saghaulor on 2009-12-28
> **eopi said:**
> **Saghaulor **you can feel free to help me out.  I've been working on this problem for **2 years now**, I waited **10 months** for the new release but it didn't quite fix it. 

I have a Vostro 1500 and I definitely have BroadCom - wireless card and I think it's working, see why below. 

I have 9.10 Karmic and when I plug in cable line, ethernet, it read Auto Eth0 - it's working perfectly. 

Then when I go to Network manager I read Wired Network and Wireless Networks.  I can't click into Wireless Networks, greyed out. 

But When I go to VPN Connections, Connnect to Hidden Wireless Network and Create New Wireless Network, I can actually see that it's read the name of my wireless network name, the name I assigned to my wireless signal.

Then when I go to connect to hidden wireless network and select "Connection:"  my wireless name, ...

Everything Greys out, Network Name:, Wireless Security (WPA &WPA2 Persona) and Password, it all Greys out and then "Connect" also greys out and only Cancel is avaiable as an option.

New Wireless Network also greys out.

Any thoughts?

Hopefully there is a quick and easy fix here, maybe I'm overlooking something very easy to connect to wireless signal.

After 2 years of trying to fix this maybe I should just buy the perfect Laptop- **Saghaulor what is the perfect laptop and wireless card? Just in case ...**

It's just that everytime I try to fix this problem I age exponentially. :P

I'll be glad to help you to the best of my abilities. Mind you I'm no expert, but I've fiddled around with this stuff quite a bit.

Firstly, have you read my previous posts in this thread? That is a good place to start.

Before you do anything though, lets find out where you're at.

Open a terminal, and run the following code. Please copy and paste it her on the forum, so that I can see what we're working with.

```
sudo lspci
```

Also, run this and and paste it too.

```
sudo ifconfig
```

---

### Post by Guilden_NL on 2009-12-28
> **eopi said:**
> 
But When I go to VPN Connections, Connnect to Hidden Wireless Network and Create New Wireless Network, I can actually see that it's read the name of my wireless network name, the name I assigned to my wireless signal.

Then when I go to connect to hidden wireless network and select "Connection:"  my wireless name, ...

Everything Greys out, Network Name:, Wireless Security (WPA &WPA2 Persona) and Password, it all Greys out and then "Connect" also greys out and only Cancel is avaiable as an option.

New Wireless Network also greys out.

Any thoughts?

I had a wireless card that acted exactly like this; I went down a very long list of troubleshooting, I couldn't find anyone that could point out the issue.  On a lark, I tried Wicd at the suggestion of someone and it was an instant fix.  I can't tell you why, just that it worked and I never gave it another thought until I updated the system a couple of years later and went with an Edimax card which worked straight out of the box with the standard Ubuntu wireless interface.

It's available in the Ubuntu repositories - it's a two minute download and install. You've only wasted two minutes of your time if it doesn't help you out.  On the other hand, it's a great little utility that you will probably want to run even on your working wireless setups.

Good luck, I am right there with you. It's frustrating to work through wireless issues, no matter what the OS!

---

### Post by Saghaulor on 2009-12-28
> **Guilden_NL said:**
> I had a wireless card that acted exactly like this; I went down a very long list of troubleshooting, I couldn't find anyone that could point out the issue.  On a lark, I tried Wicd at the suggestion of someone and it was an instant fix.  I can't tell you why, just that it worked and I never gave it another thought until I updated the system a couple of years later and went with an Edimax card which worked straight out of the box with the standard Ubuntu wireless interface.

It's available in the Ubuntu repositories - it's a two minute download and install. You've only wasted two minutes of your time if it doesn't help you out.  On the other hand, it's a great little utility that you will probably want to run even on your working wireless setups.

Good luck, I am right there with you. It's frustrating to work through wireless issues, no matter what the OS!


That's an idea. But if the drivers aren't installed, Wicd won't help.

I had a card that would crash the entire OS every time it connected using Network Manager or Wicd. Turns out something with the driver and the gui programs fritzd it.

I setup a script to manually start and connect the wifi card every reboot, and viola no more problems.

My suggestion to eopi, is first, lets see if the card is properly installed, then we'll try connecting it.

---

### Post by Guilden_NL on 2009-12-28
's cool.

But the OP stated "But When I go to VPN Connections, Connnect to Hidden Wireless Network and Create New Wireless Network, I can actually see that it's read the name of my wireless network name, the name I assigned to my wireless signal."

Same issue I had. Drivers loaded or it wouldn't have seen and reported my network. Hence my two minute "check and see" suggestion.

---

### Post by margazhang on 2009-12-29
Yes, if the needed drivers are installed, then simply installing wicd to replace NM will solve the problem instantly. I am running Linux (one is Kubuntu and the other Linux Mint) on two notebook/laptop computers and I had the wireless connection problem on both. In both cases, installing wicd via Synaptic (it will automatically remove NM) solved the problem right away.

So try installing wicd first, if that does not work then it is most likely the driver problem.

---

### Post by Saghaulor on 2009-12-29
> **Guilden_NL said:**
> 's cool.

But the OP stated "But When I go to VPN Connections, Connnect to Hidden Wireless Network and Create New Wireless Network, I can actually see that it's read the name of my wireless network name, the name I assigned to my wireless signal."

Same issue I had. Drivers loaded or it wouldn't have seen and reported my network. Hence my two minute "check and see" suggestion.

Good point.

I guess I wanted to be sure. I've found that sometimes users report things inaccurately by accident.

---

### Post by eopi on 2009-12-29
Thanks guys, I'm working on responding.  I greatly appreciate it. 

Busy with real work and other IT issues, forums are so helpful.

---

### Post by Remlique on 2009-12-30
I too am experiencing similar problems, also fairly new to linux. My router is a DIR-615 and I'm using a GXT wireless usb adapter. My situation, I plug in the wireless usb adapter, linux does its' thing, and it looked like it was working. Checked to see the available wireless networks, and the only ones I could find are the ones that belonged to my neighbours. I've used the same usb adapter on another computer so it seemed to work fine with my router, played around with some settings on the router, tried wicd, still no luck. Any help would be greatly appreciated

---

### Post by Remlique on 2010-01-04
bump

---

### Post by Linux000 on 2010-01-04
If you can see other wifi-networks, try "connect to a hidden network" and type in you network name there.

---

### Post by Remlique on 2010-01-05
Yea I tried that too, still no luck. I'm thinking there's something non-linux-friendly about the router. Anyone else having the same problem with their DIR-615?

---

### Post by Linux000 on 2010-01-05
As long as the router is 802.11(wifi) it should care, much less know what os your running.

---

### Post by Remlique on 2010-01-06
Yea my router is running 802.11. I also tried n, g, b, and a combination of each, still isn't working.

---

### Post by Linux000 on 2010-01-06
> I've used the same usb adapter on another computer

Was the other computer in a different location?

---

