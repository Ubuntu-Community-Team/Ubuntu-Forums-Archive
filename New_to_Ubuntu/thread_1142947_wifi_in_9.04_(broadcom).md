---
title: "wifi in 9.04 (broadcom)"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by chilimac02 on 2009-04-29
My wireless adapter isn't working, although system-admin-hardware tells me that Broadcom STA wireless driver is installed, but not being used...

What the heck do I have to do to use it? When I installed the beta, wifi worked, but I recently did a re-install with the official 9.04 release and now wifi won't work...

---

### Post by brunogirin on 2009-04-29
This wiki page may help: [https://wiki.ubuntu.com/DebuggingNetworkManager](https://wiki.ubuntu.com/DebuggingNetworkManager)

---

### Post by chilimac02 on 2009-04-29
yeah, i don't get any of that. I tried the first step, and my driver wouldn't unload...

---

### Post by lkraemer on 2009-04-29
Open a Terminal Window and DO:
```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig

```
Then post the output of all the commands.

lkraemer

---

### Post by chilimac02 on 2009-04-29
Output:

justin@justin-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:eb:d1:22:fa:d4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
justin@justin-laptop:~$ sudo lshw -C network
[sudo] password for justin: 
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:eb:d1:22:fa:d4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
justin@justin-laptop:~$ sudo lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               63240  0 
psmouse                61972  0 
soundcore              15200  1 snd
compat_ioctl32          9344  1 uvcvideo
k8temp                 12416  0 
pcspkr                 10496  0 
i2c_nforce2            14980  0 
serio_raw              13316  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
joydev                 18368  0 
nvidia               7234012  39 
btusb                  19608  2 
agpgart                42696  1 nvidia
video                  25360  5 
output                 11008  1 video
usbhid                 42336  0 
forcedeth              61712  0 
ssb                    41220  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
justin@justin-laptop:~$ sudo ndiswrapper -l
sudo: ndiswrapper: command not found
justin@justin-laptop:~$ cat /etc/modprobe.d/blacklist
cat: /etc/modprobe.d/blacklist: No such file or directory
justin@justin-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

justin@justin-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by dkruidhof on 2009-04-29
go [here]("http://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). that's what fixed it for me, although I do have a different broadcom card.

---

### Post by chilimac02 on 2009-04-30
followed those instructions... I made it to step 3, but then got a bunch of warning messages. Anyone help?

[PHP]ustin@justin-laptop:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
justin@justin-laptop:~/bcm43xx$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ndiswrapper line 3: ignoring bad line starting with 'install'
WARNING: /etc/modprobe.d/ndiswrapper line 4: ignoring bad line starting with 'modprobe'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'modprobe'
bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: ssb)
justin@justin-laptop:~/bcm43xx$ sudo depmod -a
justin@justin-laptop:~/bcm43xx$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ndiswrapper line 3: ignoring bad line starting with 'install'
WARNING: /etc/modprobe.d/ndiswrapper line 4: ignoring bad line starting with 'modprobe'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'modprobe'
justin@justin-laptop:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
justin@justin-laptop:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

justin@justin-laptop:~/bcm43xx$ sudo ndiswrapper -m
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ndiswrapper line 3: ignoring bad line starting with 'install'
WARNING: /etc/modprobe.d/ndiswrapper line 4: ignoring bad line starting with 'modprobe'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'modprobe'
module configuration already contains alias directive

module configuration contains directive install ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper-1.9 line 868, <MODPROBE> line 248.
justin@justin-laptop:~/bcm43xx$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
justin@justin-laptop:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
justin@justin-laptop:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0
[/PHP]

---

### Post by dkruidhof on 2009-04-30
it looks like you already did the permanent hardy bug fix below all those commands. either way, i don't think those errors should be a big concern. did you run 'lshw -C network' afterwards? what module is your wireless card using? if it's smb keep on reading and following the directions on that link i posted earlier.

---

### Post by lkraemer on 2009-04-30
Now, go back and run the commands in Post #4,
separate them such that each group is easy to
locate.

Then, don't jump the gun and do anything else until
we know what you have already done.

lkraemer

---

### Post by dkruidhof on 2009-04-30
and since you are using Juanty, post the output of this too:

```
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by chilimac02 on 2009-04-30
here you go, from #4

[PHP]justin@justin-laptop:~$ sudo lshw -C network
[sudo] password for justin: 
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:f1:36:03:3c:b4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
justin@justin-laptop:~$ 
justin@justin-laptop:~$ 
justin@justin-laptop:~$ 
justin@justin-laptop:~$ 
justin@justin-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
ndiswrapper           193436  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 18368  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               63240  0 
psmouse                61972  0 
soundcore              15200  1 snd
usbhid                 42336  0 
compat_ioctl32          9344  1 uvcvideo
btusb                  19608  2 
pcspkr                 10496  0 
k8temp                 12416  0 
serio_raw              13316  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usbtouchscreen         17412  0 
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
nvidia               7234012  39 
agpgart                42696  1 nvidia
i2c_nforce2            14980  0 
video                  25360  5 
output                 11008  1 video
forcedeth              61712  0 
ssb                    41220  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
justin@justin-laptop:~$ 
justin@justin-laptop:~$ 
justin@justin-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ndiswrapper line 3: ignoring bad line starting with 'install'
WARNING: /etc/modprobe.d/ndiswrapper line 4: ignoring bad line starting with 'modprobe'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'modprobe'
bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: ssb)
justin@justin-laptop:~$ 
justin@justin-laptop:~$ 
justin@justin-laptop:~$ cat /etc/modprobe.d/blacklist
blacklist bcm43xx
blacklist wl
blacklist bcm43xx
blacklist wl
justin@justin-laptop:~$ 
justin@justin-laptop:~$ 
justin@justin-laptop:~$ 
justin@justin-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

justin@justin-laptop:~$ 
[/PHP]

and from the previous post:

[PHP]justin@justin-laptop:~$ cat /etc/modprobe.d/blacklist.conf
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

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
justin@justin-laptop:~$ [/PHP]

---

### Post by dkruidhof on 2009-04-30
> **chilimac02 said:**
> here you go, from #4

[PHP]justin@justin-laptop:~$ sudo lshw -C network
[sudo] password for justin: 
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:f1:36:03:3c:b4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/PHP]

it appears that your wireless device isn't getting a logical name. I looked around online about that and one person said they fixed that problem by turning on their wireless device with a physical switch on the laptop. Another person fixed it by reinstalling Ubuntu. Maybe someone else can offer a better way to fix it. Sorry.

Another problem is that your wireless device is being loading with module ssb, when it should be loaded with ndiswrapper. That is addressed under the Hardy Bug Fix in the link I posted previously. However, we'll probably have to fix logical name problem first.

---

### Post by chilimac02 on 2009-04-30
I tried flipping my wifi switch, but that did nothing (except toggle bluetooth). Could I manually edit a file in order to give the card a logical address? 

I've reinstalled 9.04 2x trying to get wifi to work before getting on the forum. I did that because wifi worked fine in the beta 2 version of 9.04.

---

### Post by dkruidhof on 2009-04-30
can you check if the output of ```
lshw -C network
``` changes when you hit your wifi's toggle switch?

---

### Post by chilimac02 on 2009-04-30
When I've got the switch off:
[PHP]sudo lshw -C network
[sudo] password for justin: 
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:83:86:5e:52:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/PHP]

When the switch is on:
[PHP]sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:83:86:5e:52:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/PHP]

That's what i've got...

My system is:
hp tx1320us
AMD Turion TL-60
2GB Ram

---

### Post by lkraemer on 2009-04-30
You might give this a try.
[http://ubuntuforums.org/showthread.php?p=7186022](http://ubuntuforums.org/showthread.php?p=7186022)

lkraemer

---

### Post by chilimac02 on 2009-04-30
After reading the above post, I followed the instructions in the link. I had little faith in them... but... Ahem they worked.

I just turned the switch to "off" rebooted, and the card works fine now. I'm totally at a loss as to why, but I really don't care because it works!!

---

### Post by lkraemer on 2009-05-01
That's exactly why I prefer folks trying one thing at a time, and not
jumping the gun and doing three things all at once when others jump in
with their suggestions, even when they haven't tried them out themselves.
You can and will mess up more than you can ever fix, if you're led in
three directions at once.

So, this was a valuable lesson:
1.  SEARCH & GOOGLE are your friends.  It fixed your problem!
2.  Go slow, think about what you are doing, and do one thing at a time! 
3.  Others will help if you give them a chance, even when you don't search!

lkraemer

---

