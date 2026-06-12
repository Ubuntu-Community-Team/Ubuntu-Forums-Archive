---
title: "Uninstall to install driver coz its already exist"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by candyoff on 2006-08-16
Dear all

I was trying to install a patched version of my drivers for Orinoco. 
Following : [https://wiki.ubuntu.com/OrinocoMonitorMode](https://wiki.ubuntu.com/OrinocoMonitorMode)

there was a problem after i execute "make" of driver version 0.15
So i went to download another version 0.13, and try to execute "make" again. 
But it said 

user@eddy-laptop:~/Desktop/orinoco-0.15$ make
make -C /usr/src/linux-headers-2.6.15-26-386 M=/home/user/Desktop/orinoco-0.15 KERNELRELEASE=2.6.15-26-386 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
/home/eddy/Desktop/orinoco-0.15/Kbuild:38: *** This driver is already enabled in the kernel.  Stop.
make[1]: *** [_module_/home/eddy/Desktop/orinoco-0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make: *** [modules] Error 2

Can I know how can I disable/remove/uninstall the previous installed driver so that I can re install a fresh one?
Thank you

Warmest Regards

---

### Post by arkham on 2006-08-16
You can try a 'modprobe -r <module name>' (use lsmod to  list the module names) to remove the module from the current kernel (then run lsmod again to make sure it is gone).  Then try running make again.

Adam

---

### Post by candyoff on 2006-08-17
Hi Adam
Thanks for the help
I have tried lsmod, but not sure which one I should remove 
Afraid that I will remove the wrong one and dont know how to install it back.

The lists are at the bottom. 

Anyway, I tried " modprobe -l | grep orinoco "
I have manually deleted the files. 
But after I restart, its still listed after i exeucute "" modprobe -l | grep orinoco " although the files are deleted...


/lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/orinoco_tmd.ko
/lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/orinoco_plx.ko
/lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/orinoco_pci.ko
/lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/orinoco_nortel.ko
/lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/orinoco.ko
/lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/orinoco_cs.ko

with lsmod

Module                  Size  Used by
acpi_sbs               19980  0
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
button                  6672  0
e100                   40580  0
mii                     5888  1 e100
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
radeon                116000  1
drm                    73236  2 radeon
speedstep_ich           5260  0
speedstep_lib           4484  1 speedstep_ich
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_ich,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
ipv6                  265728  6
nls_utf8                2176  1
ntfs                  103536  1
dm_mod                 58936  1
af_packet              22920  4
md_mod                 72532  0
lp                     11844  0
pcmcia                 40508  0
pcspkr                  2180  0
joydev                 10048  0
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
irtty_sir               8576  0
snd_intel8x0           33692  1
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
sir_dev                19628  1 irtty_sir
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
rtc                    13492  0
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
irda                  187068  2 irtty_sir,sir_dev
crc_ccitt               2304  1 irda
floppy                 62148  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
psmouse                36100  0
serio_raw               7300  0
intel_agp              22940  1
agpgart                34888  2 drm,intel_agp
evdev                   9856  2
tsdev                   8000  0
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
usbhid                 39904  0
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130692  4 usbhid,ehci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  4
piix                   11012  1
generic                 5124  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  73
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit


Regards

---

### Post by Peter L. Leadford on 2008-01-29
*bump*

I'm running into the same problems, same setup, although i do have a slightly newer kernel (2.6.20-15-powerpc). The card works but i would like to use the monitor mode.

I've tried both methods described [here]("https://wiki.ubuntu.com/OrinocoMonitorMode") and [here]("https://help.ubuntu.com/community/WifiDocs/OrinocoKismet") without any results. 

Initially i get this:
> make -C /usr/src/linux-headers-2.6.20-16-powerpc M=/orinoco/orinoco-0.15 KERNELRELEASE=2.6.20-16-powerpc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-powerpc'
/orinoco/orinoco-0.15/Kbuild:38: *** This driver is already enabled in the kernel.  Stop.
make[1]: *** [_module_/orinoco/orinoco-0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-powerpc'
make: *** [modules] Error 2

I removed the airport, hermes and orinoco modules from the kernel via rmmod and modprobe, i also deleted the related *ko files (after backing them up) but after *make* i still get the same error. When i for instance *modprobe -l | grep orinoco* i still see the drivers listed (although thru lsmod i don't see anything related). I tried blacklisting airport, orinoco and hermes but without any result (both in /etc/modprobe.d/blacklist, /etc/modprobe.d/blacklist-wlan and /etc/default/linux-restricted-modules-common). Could this be the problem? If so, how can i disable those drivers?

I reversed the above and tried chili555's suggestion by commenting out those lines mentioned and this is what i get:
> make -C /usr/src/linux-headers-2.6.20-16-powerpc M=/orinoco/orinoco-0.15 KERNELRELEASE=2.6.20-16-powerpc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-powerpc'
  CC [M]  /orinoco/orinoco-0.15/orinoco.o
/orinoco/orinoco-0.15/orinoco.c:2466:67: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/orinoco/orinoco-0.15/orinoco.c: In function &#8216;alloc_orinocodev&#8217;:
/orinoco/orinoco-0.15/orinoco.c:2466: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/orinoco/orinoco-0.15/orinoco.c:2466: error: (Each undeclared identifier is reported only once
/orinoco/orinoco-0.15/orinoco.c:2466: error: for each function it appears in.)
/orinoco/orinoco-0.15/orinoco.c:2467:68: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/orinoco/orinoco-0.15/orinoco.c:2468:75: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
make[2]: *** [/orinoco/orinoco-0.15/orinoco.o] Error 1
make[1]: *** [_module_/orinoco/orinoco-0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-powerpc'
make: *** [modules] Error 2

I have no idea what to make of this.

Another thing, i read that 0.15x drivers can be unstable with certain firmware versions. I am using 0.15 (see info below), i tried googling but i couldn't find anything that says more about wich firmware versions could be unstable. Is downgrading to a lower firmware version an option? If so, how do i downgrade the firmware from the wireless card?

Any help is appreciated a lot, have been running into walls for days now.

Cheers,
Paul

This is the info on my wireless card:
> description: Wireless interface
physical id: 1
logical name: eth1
serial: 00:30:65:cf:10:d1
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.70 link=no multicast=yes wireless=IEEE 802.11b

Edit: I'm on Feisty, upgrading to 7.10 is no option (i successfully turned my pismo into a brick this way).

---

### Post by Peter L. Leadford on 2008-02-06
*bump*

I tried it this [way]("http://www.wains.be/index.php/2005/11/05/ubuntu-breezy-510-kismet-orinoco-patched-drivers-for-monitoring-and-scan-modes/") with the latest source (2.6.20-16-powerpc) and latest orinoco driver (orinoco-0.15).

When i *make modules* i get this error in the end:
```
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  CC [M]  drivers/net/wireless/orinoco.o
drivers/net/wireless/orinoco.c:2466:67: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
drivers/net/wireless/orinoco.c: In function ‘alloc_orinocodev’:
drivers/net/wireless/orinoco.c:2466: error: ‘INIT_WORK’ undeclared (first use in this function)
drivers/net/wireless/orinoco.c:2466: error: (Each undeclared identifier is reported only once
drivers/net/wireless/orinoco.c:2466: error: for each function it appears in.)
drivers/net/wireless/orinoco.c:2467:68: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
drivers/net/wireless/orinoco.c:2468:75: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
make[3]: *** [drivers/net/wireless/orinoco.o] Error 1
make[2]: *** [drivers/net/wireless] Error 2
make[1]: *** [drivers/net] Error 2
make: *** [drivers] Error 2

```

Does anyone got a clue?

---

