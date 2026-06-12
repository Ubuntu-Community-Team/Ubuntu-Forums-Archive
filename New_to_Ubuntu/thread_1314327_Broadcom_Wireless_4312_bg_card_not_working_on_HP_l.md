---
title: "Broadcom Wireless 4312 b/g card not working on HP laptop - Karmic Koala"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by ubunt22rock on 2009-11-04
Hi I just downloaded Karmic. Everything's perfect except that I cant use wifi. My broadcaom STA driver's active but "not in use".

I tried some things mentioned in other threads. but no improvements. 

I am a bit frustrated cos I havent been using linux for past 6 months cos my jaunty was kinda stupid and most drivers dint work. And now this.

Would be grateful if any of you could help

(note: I posted this in hardware/laptops. no use. so posting again. you can close either. I just want to get noticed)

---

### Post by yeats on 2009-11-04
> 
I tried some things mentioned in other threads. but no improvements. 

Can you share what you've done?  I have a Broadcom card on my Dell mini and had to install bcmwl-kernel-source.  When I rebooted, wireless worked with no further problems.

---

### Post by ubunt22rock on 2009-11-04
yes, I tried that. and it dint work. 

apart from that : there is one described here [http://ubuntuforums.org/showthread.php?t=1307197](http://ubuntuforums.org/showthread.php?t=1307197)

Another trick I tried was to install windows style drivers. I dont remember the package's name. But that dint work either

---

### Post by lkraemer on 2009-11-04
The info here should help you.
[http://ubuntuforums.org/showthread.php?t=1314852](http://ubuntuforums.org/showthread.php?t=1314852)
But you are going to have to reverse the things you have done to purge
what you don't need.  You can't mix and match, because things get in
the way, and prevent the drivers from working.

So gather your guide you used so you know what to remove/purge/uninstall
and pick one method.

lk

---

### Post by ubunt22rock on 2009-11-04
I uninstalled ndiswrapper. I followed your instructions and unzipped the new b43 b43 legacy folders into /lib/firmware. rebooted blah bla. There is still no wireless. I mean in the task bar tray if i right click on the network part. there is not even an option for "enable wireless"

in the system->admisnistration->hardware drivers : Broadcom sta is installed and active but "not in use"

and iwconfig gives:

@jaguar:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

God help me

---

### Post by Jesus_Valdez on 2009-11-04
What I did with Karmic Koala is first unintall the package "bcmwl-kernel-source" from synpatic, then delete the "residual configuration" (the "State" tab in synaptic). Plug the ethernet cable and install again "bcmwl-kernel-source".

After a reboot my Broadcom wifi was back.

---

### Post by ubunt22rock on 2009-11-05
I cant find the state tab in synaptic nor "residual configuration"

---

### Post by lkraemer on 2009-11-05
UPDATED 11-06-2009 after booting from LiveCD and testing to VERIFY for 9.10

OK, let's verify that everything is placed as it should be.  In a Terminal Window do:
```

cd /
cd /lib/firmware/b43
ls -alt

```
You should see a listing of the *.fw files.  Then do:
```

cd ..
cd /b43legacy
ls -alt

```
You should see more *.fw files. You should have used some command similar to this to copy the files:
```

sudo cp -r /home/loginname/Desktop/b43* /lib/firmware

```
If the folders are present and filled with *.fw files do the following
ndiswrapper command in lowercase (last letter is a lowercase "L"):
```

ndiswrapper -l
lsmod
cat /etc/modprobe.d/blacklist.conf

```
Post the output of these commands.  The first command should show as an error
if you correctly removed ndiswrapper.  Look for modules that need
to be removed.  Module b43xx, and ndiswrapper shouldn't be found.  
If lsmod shows module b43xx, ndiswrapper, and others installed you
will need to blacklist them, since you are going to be using b43.
IF b43 SHOWS AS BEING BLACKLISTED, INSERT A # IN FRONT OF EACH
TO ENABLE THE USE OF b43.  You may have to remove some (one) of
the following depending on what lsmod shows as being loaded:
```

modprobe -r b43xx
modprobe -r b43legacy
ifconfig
iwconfig

```
Post the output of the last two commands.  iwconfig should display 
something like the following:
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
In my case it would look like this:
```

sudo ifconfig ath0 down
sudo dhclient -r ath0
sudo iwconfig ath0 essid "Airlink"
sudo iwconfig ath0 mode Managed
sudo ifconfig ath0 up
sudo dhclient ath0

```
You may want to do
```

sudo /etc/init.d/networking restart

```
And wait a few minutes......

You should be up and running.

lk

---

### Post by ubunt22rock on 2009-11-05
```
root@jaguar:~# ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
apt-get install ndiswrapper-common
ndiswrapper: command not found

```

```
root@jaguar:~# lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
ppdev                   6688  0 
snd_hda_codec_nvhdmi     4828  1 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
iptable_filter          3100  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
ip_tables              11692  1 iptable_filter
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               9586440  39 
uvcvideo               59080  0 
psmouse                56180  0 
x_tables               16544  1 ip_tables
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               36736  1 uvcvideo
lirc_ene0100            8096  0 
v4l1_compat            14496  2 uvcvideo,videodev
sdhci_pci               7100  0 
soundcore               7264  1 snd
sdhci                  17472  1 sdhci_pci
jmb38x_ms               9600  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
serio_raw               5280  0 
joydev                 10272  0 
btusb                  11856  2 
lib80211                6528  0 
memstick               10072  1 jmb38x_ms
hp_accel               11228  0 
lirc_dev               10804  1 lirc_ene0100
lp                      8964  0 
lis3lv02d               7452  1 hp_accel
input_polldev           3716  1 lis3lv02d
parport                35340  2 ppdev,lp
led_class               4096  2 sdhci,hp_accel
r8169                  32064  0 
mii                     5212  1 r8169
intel_agp              27484  0 
agpgart                34988  2 nvidia,intel_agp
video                  19380  0 
output                  2780  1 video

```

```
root@jaguar:~# cat /etc/modprobe.d/blacklist.conf 
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
#blacklist bcm43xx

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
blacklist ssb

```

```
root@jaguar:~# ifconfig 
eth0      Link encap:Ethernet  HWaddr ------------------------  
          inet addr:-----------------  Bcast:---------------Mask:255.255.255.0
          inet6 addr: -------------------------- Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:526846 (526.8 KB)  TX bytes:78637 (78.6 KB)
          Interrupt:31 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

I have removed the addresses for privacy's sake :)

```
root@jaguar:~# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

I did everything you instructed. no use. While copying the b43 and b43 legacy. I merged/replaced all files.

Besides I "modprobe -r"-d b44 b43 b43legacy and ssb.

Still the same.

---

### Post by lkraemer on 2009-11-05
OK, I just tested the procedure, and I told you incorrectly since Ubuntu 9.10
has changed the module they use.  They use b43 and ssb so you need to go back
and blacklist b43xx, remove the blacklist for b43 and ssb.  Then enable the
hardware drivers, and you should be in business.

You might try a power down and power back up.  Then try the command:
```

lsmod

```
to see if b43 is installed.  If not and your Restricted Hardware drivers icon is
being displayed in the top right toolbar try clicking on it and having it enable
the restricted drivers.

lk

---

### Post by ubunt22rock on 2009-11-05
```
adhithya@jaguar:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
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
01:00.0 VGA compatible controller: nVidia Corporation G98M [GeForce G 105M] (rev a1)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
05:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
05:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
05:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

```

```
adhithya@jaguar:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 090c:137b Feiya Technology Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
adhithya@jaguar:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:db000000-db003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: --------------------
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=130.113.31.149 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:31 ioport:3000(size=256) memory:d5010000-d5010fff(prefetchable) memory:d5000000-d500ffff(prefetchable) memory:d5020000-d502ffff(prefetchable)

```

and I have uploaded my hardware drivers page. notice it says installed but not in use

---

### Post by lkraemer on 2009-11-05
OK, I know what is going on.  I just booted into 9.10 via LiveCD, with my
PCMCIA Wifi card that uses Broadcom Chips.  I captured the lsmod output
before and after and have two screen shots.  I copied the firmware and
then enabled the drivers.  Everything works......

There has been a change in 9.10 and they are using the b43 module, so you need
to go back and blacklist b43xx, and remove the blacklist for ssb, and b43 so that
everything works.  REF: the lsmod modules loaded and used.

 lsmod - before restricted drivers load
Module                  Size  Used by
nls_iso8859_1           3740  0 
vfat                   10716  0 
fat                    51452  1 vfat
binfmt_misc             8356  1 
lp                      8964  0 
arc4                    1660  2 
ecb                     2524  2 
snd_ali5451            18888  2 
b43                   122136  0 
snd_ac97_codec        101216  1 snd_ali5451
ac97_bus                1532  1 snd_ac97_codec
mac80211              181236  1 b43
snd_pcm_oss            37920  0 
cfg80211               93052  2 b43,mac80211
snd_mixer_oss          16028  1 snd_pcm_oss
led_class               4096  1 b43
snd_pcm                75296  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
ssb                    35300  1 b43
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
pcmcia                 36808  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
joydev                 10272  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
yenta_socket           24200  2 
snd_timer              22276  2 snd_pcm,snd_seq
ppdev                   6688  0 
rsrc_nonstatic         11644  1 yenta_socket
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_ali15x3             6336  0 
parport_pc             31940  1 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 32272  0 
parport                35340  3 lp,ppdev,parport_pc
psmouse                56180  0 
i2c_ali1535             5792  0 
snd                    59204  14 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dm_crypt               12928  0 
iptable_filter          3100  0 
serio_raw               5280  0 
soundcore               7264  1 snd
snd_page_alloc          9156  1 snd_pcm
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
squashfs               22912  1 
aufs                  149420  1 
nls_cp437               5372  1 
isofs                  31620  1 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52544  0 
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
natsemi                26944  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video
ati_agp                 6760  1 
agpgart                34988  3 ttm,drm,ati_agp

lsmod after restricted drivers load
Module                  Size  Used by
nls_iso8859_1           3740  0 
vfat                   10716  0 
fat                    51452  1 vfat
binfmt_misc             8356  1 
lp                      8964  0 
arc4                    1660  2 
ecb                     2524  2 
snd_ali5451            18888  2 
b43                   122136  0 
snd_ac97_codec        101216  1 snd_ali5451
ac97_bus                1532  1 snd_ac97_codec
mac80211              181236  1 b43
snd_pcm_oss            37920  0 
cfg80211               93052  2 b43,mac80211
snd_mixer_oss          16028  1 snd_pcm_oss
led_class               4096  1 b43
snd_pcm                75296  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
ssb                    35300  1 b43
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
pcmcia                 36808  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
joydev                 10272  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
yenta_socket           24200  2 
snd_timer              22276  2 snd_pcm,snd_seq
ppdev                   6688  0 
rsrc_nonstatic         11644  1 yenta_socket
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_ali15x3             6336  0 
parport_pc             31940  1 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 32272  0 
parport                35340  3 lp,ppdev,parport_pc
psmouse                56180  0 
i2c_ali1535             5792  0 
snd                    59204  14 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dm_crypt               12928  0 
iptable_filter          3100  0 
serio_raw               5280  0 
soundcore               7264  1 snd
snd_page_alloc          9156  1 snd_pcm
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
squashfs               22912  1 
aufs                  149420  1 
nls_cp437               5372  1 
isofs                  31620  1 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52544  0 
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
natsemi                26944  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video
ati_agp                 6760  1 
agpgart                34988  3 ttm,drm,ati_agp

As you can see I can see two Wifi Routers, and I am sending this after connecting.
Sorry, for the confusion.  I did not verify that b43 was being used versus b43xx.

lk

---

### Post by ubunt22rock on 2009-11-06
Hi

I got it working. Thanks a lot :)

---

### Post by stevenw66 on 2009-11-06
How do you blacklist these modules. What is the file path?

> **lkraemer said:**
> OK, I know what is going on.  I just booted into 9.10 via LiveCD, with my
PCMCIA Wifi card that uses Broadcom Chips.  I captured the lsmod output
before and after and have two screen shots.  I copied the firmware and
then enabled the drivers.  Everything works......

There has been a change in 9.10 and they are using the b43 module, so you need
to go back and blacklist b43xx, and remove the blacklist for ssb, and b43 so that
everything works.  REF: the lsmod modules loaded and used.

 lsmod - before restricted drivers load
Module                  Size  Used by
nls_iso8859_1           3740  0 
vfat                   10716  0 
fat                    51452  1 vfat
binfmt_misc             8356  1 
lp                      8964  0 
arc4                    1660  2 
ecb                     2524  2 
snd_ali5451            18888  2 
b43                   122136  0 
snd_ac97_codec        101216  1 snd_ali5451
ac97_bus                1532  1 snd_ac97_codec
mac80211              181236  1 b43
snd_pcm_oss            37920  0 
cfg80211               93052  2 b43,mac80211
snd_mixer_oss          16028  1 snd_pcm_oss
led_class               4096  1 b43
snd_pcm                75296  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
ssb                    35300  1 b43
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
pcmcia                 36808  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
joydev                 10272  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
yenta_socket           24200  2 
snd_timer              22276  2 snd_pcm,snd_seq
ppdev                   6688  0 
rsrc_nonstatic         11644  1 yenta_socket
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_ali15x3             6336  0 
parport_pc             31940  1 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 32272  0 
parport                35340  3 lp,ppdev,parport_pc
psmouse                56180  0 
i2c_ali1535             5792  0 
snd                    59204  14 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dm_crypt               12928  0 
iptable_filter          3100  0 
serio_raw               5280  0 
soundcore               7264  1 snd
snd_page_alloc          9156  1 snd_pcm
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
squashfs               22912  1 
aufs                  149420  1 
nls_cp437               5372  1 
isofs                  31620  1 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52544  0 
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
natsemi                26944  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video
ati_agp                 6760  1 
agpgart                34988  3 ttm,drm,ati_agp

lsmod after restricted drivers load
Module                  Size  Used by
nls_iso8859_1           3740  0 
vfat                   10716  0 
fat                    51452  1 vfat
binfmt_misc             8356  1 
lp                      8964  0 
arc4                    1660  2 
ecb                     2524  2 
snd_ali5451            18888  2 
b43                   122136  0 
snd_ac97_codec        101216  1 snd_ali5451
ac97_bus                1532  1 snd_ac97_codec
mac80211              181236  1 b43
snd_pcm_oss            37920  0 
cfg80211               93052  2 b43,mac80211
snd_mixer_oss          16028  1 snd_pcm_oss
led_class               4096  1 b43
snd_pcm                75296  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
ssb                    35300  1 b43
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
pcmcia                 36808  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
joydev                 10272  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
yenta_socket           24200  2 
snd_timer              22276  2 snd_pcm,snd_seq
ppdev                   6688  0 
rsrc_nonstatic         11644  1 yenta_socket
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_ali15x3             6336  0 
parport_pc             31940  1 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 32272  0 
parport                35340  3 lp,ppdev,parport_pc
psmouse                56180  0 
i2c_ali1535             5792  0 
snd                    59204  14 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dm_crypt               12928  0 
iptable_filter          3100  0 
serio_raw               5280  0 
soundcore               7264  1 snd
snd_page_alloc          9156  1 snd_pcm
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
squashfs               22912  1 
aufs                  149420  1 
nls_cp437               5372  1 
isofs                  31620  1 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52544  0 
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
natsemi                26944  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video
ati_agp                 6760  1 
agpgart                34988  3 ttm,drm,ati_agp

As you can see I can see two Wifi Routers, and I am sending this after connecting.
Sorry, for the confusion.  I did not verify that b43 was being used versus b43xx.

lk

---

### Post by ubunt22rock on 2009-11-06
go to /etc/modprobe.d/blacklist.conf(or blacklist) and add a "#" in front of any module you want to be out of the blacklist. u need super user previleges for that

---

### Post by lkraemer on 2009-11-07
To Blacklist a module (assume b43 for now) you would do the following:

For versions earlier than 9.04:
```

sudo gedit /etc/modprobe.d/blacklist

```
and add a module like b43 if you want it to not be loaded/used.  Likewise,
if a module is already blacklisted you can add a # as the first character
to disable the blacklisting by making it a comment, making it usable by
the system.

For version 9.04 and above:
```

sudo gedit /etc/modprobe.d/blacklist.conf

```

lk

---

