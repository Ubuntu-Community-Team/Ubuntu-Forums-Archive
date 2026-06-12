---
title: "My eth1 interface disappeared after I did updates and rebooted!"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by mekmiotek on 2007-02-21
Hi everyone.

I installed Ubuntu 6.10 on an IBM thinkpad T23. After installation eth0 was up and on my lan(wired). I wanted to get the wireless going, so I did
sudo ifconfig eth0 down
sudo dhclient
and eth1 came up with an ip from dhcp. I unplugged from the lan and everything was great. An icon appeared on the top bar saying It had to install like 130 updates. (I think 130, may be off). I did the downloads and installed them all, all wirelessly via eth1. It then said it needed a reboot.
After reboot, my eth1 is gone! Its not even listed when I do iwconfig. Somehow the updates killed the drivers for the wireless card I guess. Can anyone help me to get it back up? Ive tried all kinds of things with no success.

mekmiotek@mekmiotek-laptop:/etc/network$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:00.0 CardBus bridge: Texas Instruments PCI1420
02:00.1 CardBus bridge: Texas Instruments PCI1420
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)

mekmiotek@mekmiotek-laptop:/etc/network$ lsmod
Module                  Size  Used by
orinoco_cs             17540  0 
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
nvram                  10376  1 
uinput                 10368  1 
savage                 35200  2 
drm                    74644  3 savage
speedstep_ich           6544  0 
speedstep_lib           5764  1 speedstep_ich
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_ich,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
ibm_acpi               28672  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dock                    8716  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
af_packet              24584  8 
lp                     12964  0 
hostap_pci             59152  0 
hostap                123012  1 hostap_pci
ieee80211_crypt         7552  1 hostap
orinoco_pci             8320  0 
orinoco                45076  2 orinoco_cs,orinoco_pci
hermes                  9472  3 orinoco_cs,orinoco_pci,orinoco
pcmcia                 40380  1 orinoco_cs
e100                   38020  0 
mii                     6912  1 e100
prism2_pci             74752  0 
yenta_socket           28812  2 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
tsdev                   9152  0 
irtty_sir              10112  0 
sir_dev                18308  1 irtty_sir
nsc_ircc               25100  0 
irda                  214332  3 irtty_sir,sir_dev,nsc_ircc
psmouse                41352  0 
evdev                  11392  2 
crc_ccitt               3200  1 irda
floppy                 63044  0 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
hw_random               7320  0 
serio_raw               8452  0 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
intel_agp              26012  1 
agpgart                34888  2 drm,intel_agp
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
pcspkr                  4352  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
ext3                  142856  1 
jbd                    62228  1 ext3
uhci_hcd               24968  0 
usbcore               134912  2 uhci_hcd
ide_generic             2432  0 
ide_disk               18560  3 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
piix                   11780  1 
generic                 6276  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability


Anyone have any ideas? Thanks.

-mk

---

### Post by gradedcheese on 2007-02-21
> 
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)


Ah yes.  The -11 kernel introduces an ABI change, this means that you need a Prism driver compiled for the -11 ABI.  You have two options:
1) reboot into the previous (-10) kernel and things should be ok.
2) download the prism driver source and build the module for -11.  This actually isn't that hard to do, but you need a couple things first:
```

sudo apt-get install build-essential linux-headers-2.6.17-11-generic

```
(if you haven't used apt-get yet, do "sudo apt-get update" first).  Now you can just "make" and "make install" the driver when you download it.

---

### Post by mekmiotek on 2007-02-21
Thanks for the help Gradedcheese.

im attempting to do your option 2.

Ive downloaded what I believe are the Prism source drivers, but I seem to be having a problem compiling them....I think.

I downloaded and uncompressed it all, and I do this:

mekmiotek@mekmiotek-laptop:~/Desktop/hostap-driver-0.4.9$ sudo make
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/mekmiotek/Desktop/hostap-driver-0.4.9/driver/modules \
                MODVERDIR=/home/mekmiotek/Desktop/hostap-driver-0.4.9/driver/modules modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
scripts/Makefile.build:17: /home/mekmiotek/Desktop/hostap-driver-0.4.9/driver/modules/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/mekmiotek/Desktop/hostap-driver-0.4.9/driver/modules/Makefile'.  Stop.
make[1]: *** [_module_/home/mekmiotek/Desktop/hostap-driver-0.4.9/driver/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [2.6] Error 2
mekmiotek@mekmiotek-laptop:~/Desktop/hostap-driver-0.4.9$ 

Is it because of where I have the drivers? Do they need to be in any special directory?


-mk

---

### Post by mekmiotek on 2007-02-21
Also, maybe you can tell me if this is expected behavior, but before I run the make command in the hostap directory, there are alot of files in /hostap/driver/modules/

After I run the make, all the files are gone, these files:

mekmiotek@mekmiotek-laptop:~/Desktop/hostap-driver-0.4.9/driver/modules$ ls -all
total 704
drwxr-xr-x 2 mekmiotek users   4096 2006-05-07 00:05 .
drwxr-xr-x 4 mekmiotek users   4096 2006-05-07 00:05 ..
-rw-r--r-- 1 mekmiotek users     41 2003-10-11 23:08 .cvsignore
-rw-r--r-- 1 mekmiotek users   2719 2003-11-11 00:47 hostap_80211.h
-rw-r--r-- 1 mekmiotek users  31315 2005-09-18 21:51 hostap_80211_rx.c
-rw-r--r-- 1 mekmiotek users  15183 2005-08-06 13:55 hostap_80211_tx.c
-rw-r--r-- 1 mekmiotek users  88393 2006-04-16 21:09 hostap_ap.c
-rw-r--r-- 1 mekmiotek users   8286 2005-08-06 13:55 hostap_ap.h
-rw-r--r-- 1 mekmiotek users  32152 2006-04-16 21:16 hostap.c
-rw-r--r-- 1 mekmiotek users  19587 2005-03-26 23:07 hostap_common.h
-rw-r--r-- 1 mekmiotek users   3776 2005-09-17 23:51 hostap_compat.h
-rw-r--r-- 1 mekmiotek users   4315 2006-05-07 00:05 hostap_config.h
-rw-r--r-- 1 mekmiotek users   4298 2005-02-19 19:24 hostap_crypt.c
-rw-r--r-- 1 mekmiotek users  39759 2005-02-19 19:24 hostap_crypt_ccmp.c
-rw-r--r-- 1 mekmiotek users   1928 2003-11-23 22:06 hostap_crypt.h
-rw-r--r-- 1 mekmiotek users  27666 2005-02-19 19:24 hostap_crypt_tkip.c
-rw-r--r-- 1 mekmiotek users  13040 2005-02-19 19:24 hostap_crypt_wep.c
-rw-r--r-- 1 mekmiotek users  28654 2006-05-07 00:04 hostap_cs.c
-rw-r--r-- 1 mekmiotek users  18628 2004-12-17 23:27 hostap_download.c
-rw-r--r-- 1 mekmiotek users   2173 2003-11-29 21:14 hostap.h
-rw-r--r-- 1 mekmiotek users 101474 2006-04-16 21:10 hostap_hw.c
-rw-r--r-- 1 mekmiotek users  14719 2005-03-26 23:53 hostap_info.c
-rw-r--r-- 1 mekmiotek users 115047 2006-04-16 21:07 hostap_ioctl.c
-rw-r--r-- 1 mekmiotek users  11056 2006-05-07 00:04 hostap_pci.c
-rw-r--r-- 1 mekmiotek users  16870 2006-05-07 00:04 hostap_plx.c
-rw-r--r-- 1 mekmiotek users  11861 2005-03-26 23:50 hostap_proc.c
-rw-r--r-- 1 mekmiotek users   1787 2005-09-18 21:51 hostap_wext.h
-rw-r--r-- 1 mekmiotek users  31827 2005-08-06 13:55 hostap_wlan.h
-rw-r--r-- 1 mekmiotek users   1391 2003-11-23 22:03 Makefile

---

### Post by H-Radical on 2007-02-21
Hi,
I'm having the exact same problem, but I can't find the drivers from anywhere. Where did you get them from, mekmiotek?

---

### Post by mekmiotek on 2007-02-21
[http://hostap.epitest.fi/](http://hostap.epitest.fi/)

On my way out the door, I believe from there though

---

### Post by H-Radical on 2007-02-25
If I'm not mistaken, those drivers are only for 2.6.14 . I haven't found anything for 2.6.17-11. How can I boot into the -10 kernel? Any help would be appreciated cause I really need my wireless back asap.

Thanks in advance.

---

### Post by gradedcheese on 2007-02-25
Ah.  Reboot and press ESC after the BIOS stuff to get the grub boot menu, choose the -10 kernel.  If that works, edit (with sudo) /boot/grub/meny.lst and change the default kernel there.

---

### Post by stani on 2007-03-15
Help this bug out on Feisty, contribute by passing your details to launchpad:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

> Can everyone affected please attach (do not paste into comment) the output of "lspci -vv" and "lspci -vvn", make sure to name the file something like lspci-vv-<yourname>.txt

There is not much time left, please participate!

Stani

---

