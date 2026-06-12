---
title: "unable to get wireless working"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by underdog512 on 2008-04-02
I just install gutsy on an hp ze4900 which has a broadcom 4306 embeded wifi card  and I am having trouble with the wirless card.

I installed the drivers with the restricted drivers manager.  First the light is not lighting up.  the network manager shows no wirless networks and the Wlan0 is showing as enabled  but is not picking up any wireless networks.

I tested to make sure the wifi network is online byh using a different laptop.  I found and connected to the wifi network just fine.

I tried following some ndis walkthrough that I found in these forums to no avail.

Here is the output of ndiswrapper -l if it is any help

bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)


Here are some output from some other commands

 lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


adam@adam-laptop:~$ lspci -n
00:00.0 0600: 8086:3580 (rev 02)
00:00.1 0880: 8086:3584 (rev 02)
00:00.3 0880: 8086:3585 (rev 02)
00:02.0 0300: 8086:3582 (rev 02)
00:02.1 0380: 8086:3582 (rev 02)
00:1d.0 0c03: 8086:24c2 (rev 03)
00:1d.1 0c03: 8086:24c4 (rev 03)
00:1d.2 0c03: 8086:24c7 (rev 03)
00:1d.7 0c03: 8086:24cd (rev 03)
00:1e.0 0604: 8086:2448 (rev 83)
00:1f.0 0601: 8086:24cc (rev 03)
00:1f.1 0101: 8086:24ca (rev 03)
00:1f.3 0c05: 8086:24c3 (rev 03)
00:1f.5 0401: 8086:24c5 (rev 03)
00:1f.6 0703: 8086:24c6 (rev 03)
02:00.0 0200: 10ec:8139 (rev 10)
02:05.0 0607: 104c:ac50 (rev 02)
02:06.0 0280: 14e4:4320 (rev 03)


 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Any ideas as to what is going on?

---

### Post by underdog512 on 2008-04-03
Anybody out there?

---

### Post by mrm48 on 2008-04-03
What output do you get when you run the ifconfig command? Also, what kind of authentication/security is the network using?

I have a similar HP with a Broadcom in it and the restricted drivers worked out of the box for me.

---

### Post by prshah on 2008-04-03
> **underdog512 said:**
> I just install gutsy on an hp ze4900 which has a broadcom 4306 embeded wifi card  and I am having trouble with the wirless card.

Here is the output of ndiswrapper -l if it is any help
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)


since ndiswrapper suggests that an alternate driver is present, why not try to use that? ```
sudo rmmod ndiswrapper
sudo modprobe bcm43xx
sudo /etc/init.d/networking restart
sudo iwconfig wlan0

```

If it works, you can either delete the ndiswrapper driver or blacklist it. If it doesn't: any dmesg output would be helpful.```
dmesg | tail -25
```

---

### Post by dstew on 2008-04-03
The native driver is listed as an alternate to the ndiswrapper driver. You should blacklist the native driver. To do that, edit (or create) the file /etc/modprobe.d/blacklist and add the line
**blacklist bcm43xx**. Then reboot. Check ndiswrapper -l again to make sure the native driver is not loaded along with ndiswrapper.

---

### Post by underdog512 on 2008-04-03
> **prshah said:**
> since ndiswrapper suggests that an alternate driver is present, why not try to use that? ```
sudo rmmod ndiswrapper
sudo modprobe bcm43xx
sudo /etc/init.d/networking restart
sudo iwconfig wlan0

```

If it works, you can either delete the ndiswrapper driver or blacklist it. If it doesn't: any dmesg output would be helpful.```
dmesg | tail -25
```

here is dmesg output

dmesg | tail -25
[ 1803.336000] sr: Add. Sense: Unable to recover table-of-contents
[ 1805.336000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 1805.336000] sr: Sense Key : Medium Error [current] 
[ 1805.336000] sr: Add. Sense: Unable to recover table-of-contents
[ 1807.336000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 1807.336000] sr: Sense Key : Medium Error [current] 
[ 1807.336000] sr: Add. Sense: Unable to recover table-of-contents
[ 1809.336000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 1809.336000] sr: Sense Key : Medium Error [current] 
[ 1809.336000] sr: Add. Sense: Unable to recover table-of-contents
[ 1811.336000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 1811.336000] sr: Sense Key : Medium Error [current] 
[ 1811.336000] sr: Add. Sense: Unable to recover table-of-contents
[ 1813.336000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 1813.336000] sr: Sense Key : Medium Error [current] 
[ 1813.336000] sr: Add. Sense: Unable to recover table-of-contents
[ 1815.336000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 1815.336000] sr: Sense Key : Medium Error [current] 
[ 1815.336000] sr: Add. Sense: Unable to recover table-of-contents
[ 1817.336000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 1817.336000] sr: Sense Key : Medium Error [current] 
[ 1817.336000] sr: Add. Sense: Unable to recover table-of-contents
[ 1819.336000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 1819.336000] sr: Sense Key : Medium Error [current] 
[ 1819.336000] sr: Add. Sense: Unable to recover table-of-contents

---

### Post by underdog512 on 2008-04-03
> **dstew said:**
> The native driver is listed as an alternate to the ndiswrapper driver. You should blacklist the native driver. To do that, edit (or create) the file /etc/modprobe.d/blacklist and add the line
**blacklist bcm43xx**. Then reboot. Check ndiswrapper -l again to make sure the native driver is not loaded along with ndiswrapper.

bcm43xx is already listed

---

### Post by dstew on 2008-04-03
You mean it is already blacklisted?

---

### Post by underdog512 on 2008-04-03
yes it is already blacklisted

---

### Post by kevdog on 2008-04-04
Reboot for one.

Do you want to use ndiswrapper or bcm43xx?  They are mutually exclusive.  I would recommend ndiswrapper.


Reboot and then please post 

lsmod

Also you dont happen to have a wired ethernet connection running on the machine do you?

If you could also post the following:
lshw -C network

---

### Post by underdog512 on 2008-04-04
I went ahead and took the bcm43xx off the blacklist and uninstalled the bcml5 driver that was installed with ndiswrapper.  Then just install the bcm43xx with the restricted driver management tool.  

Now the light seems to come on and off intermittently and still no networks listed to connect to.

any ideas?

---

### Post by underdog512 on 2008-04-04
> **mrm48 said:**
> What output do you get when you run the ifconfig command? Also, what kind of authentication/security is the network using?

I have a similar HP with a Broadcom in it and the restricted drivers worked out of the box for me.

I went ahead and took the bcm43xx off the blacklist and uninstalled the bcml5 driver that was installed with ndiswrapper. Then just install the bcm43xx with the restricted driver management tool.

Now the light seems to come on and off intermittently and still no networks listed to connect to.

any ideas?

oops sorry about the double post!!

---

### Post by kevdog on 2008-04-04
Ok can you list the following:

iwlist scan
lshw -C network

Thanks.

---

### Post by underdog512 on 2008-04-04
> **kevdog said:**
> Reboot for one.

Do you want to use ndiswrapper or bcm43xx?  They are mutually exclusive.  I would recommend ndiswrapper.


Reboot and then please post 

lsmod

Also you dont happen to have a wired ethernet connection running on the machine do you?

If you could also post the following:
lshw -C network


I would like to use bcm43xx

I do have a wired connection but I dissconnect it, rebooted, and still joy


adam@adam-laptop:~$ lsmod
Module                  Size  Used by
af_packet              24840  2 
ipv6                  273892  12 
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
sbs                    19592  0 
ac                      6148  0 
video                  18060  0 
container               5504  0 
battery                11012  0 
button                  8976  0 
dock                   10656  0 
ndiswrapper           193436  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
pcmcia                 41388  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
bcm43xx               127336  0 
joydev                 11328  0 
ieee80211softmac       31360  1 bcm43xx
ieee80211              35656  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  1 ieee80211
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
serio_raw               8068  0 
psmouse                39952  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ata_piix               17540  2 
8139cp                 25088  0 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
8139too                27776  0 
mii                     6528  2 8139cp,8139too
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor


adam@adam-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:4f:19:af
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.1.1.102 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:94:25:c3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

adam@adam-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results



Do you think this could be a hardware issue with the wireless card?

---

### Post by kevdog on 2008-04-04
Ok, things look good right now, the bcm43xx driver is loaded and the driver is recognized on eth1.

So what does 

iwlist scan

show?

If it shows nothing, do the following

sudo ifconfig eth0 down
sudo ifconfig eth1 up
sudo iwlist scan

Anything change --- looks like you are close to getting this working!

---

### Post by underdog512 on 2008-04-04
> **kevdog said:**
> Ok, things look good right now, the bcm43xx driver is loaded and the driver is recognized on eth1.

So what does 

iwlist scan

show?

If it shows nothing, do the following

sudo ifconfig eth0 down
sudo ifconfig eth1 up
sudo iwlist scan

Anything change --- looks like you are close to getting this working!

no change when I run those commands,  and the light keeps turning off and on.

---

### Post by kevdog on 2008-04-04
Hmm,  not a big fan of the restricted bcm43xx driver, but lets keep going.

Can you check dmesg, and post only the lines relevant to the bcm43xx process.  I want to make sure there is not any errors.  Also you are certain you are in range of wireless networks?  Like you are sitting right by the router?  The restricted driver only gives you 11 Mb/sec whereas ndiswrapper will give you 54 Mb/sec.  Make sure your router is broadcasting in either b only or mixed b/g mode rather than in g only mode.

---

### Post by underdog512 on 2008-04-04
I can certainly try the ndiswrapper again.  The only reason I decided to go with bcm43xx is because I at least go the wireless light to light up.  

I don't know if I did somthing wrong installing the bcml5 driver ndiswrapper.  Do you know of a better walkthrough for installing that driver than what is in the forums here?

at any case, I did find this in the dmesg output.  

[   16.104000] bcm43xx driver
[   15.960000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   33.488000] ADDRCONF(NETDEV_UP): eth1: link is not ready

---

### Post by underdog512 on 2008-04-07
any ideas anyone?

---

### Post by kevdog on 2008-04-07
Hmm, Id go back to ndiswrapper.  I wrote a tutorial but Im not certain if its any better than possibly what you have read:?

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by underdog512 on 2008-04-07
thanks i will try that tuesday when I have some time.  (got a 12 hour shift 2morrow).  I will check back in once I have tried it.

---

### Post by underdog512 on 2008-04-07
> **kevdog said:**
> Hmm, Id go back to ndiswrapper.  I wrote a tutorial but Im not certain if its any better than possibly what you have read:?

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)


I tried your tutorial and I didn't get any errors, but still no joy.  

here is a line from demsg

[   18.648000] ndiswrapper version 1.48 loaded (smp=yes, preempt=no)

I don't see any lines regading the bcmwl5

---

### Post by Bubbasheeko on 2008-04-07
I am having similar issues, except I have an Acer Aspire 5100.  I couldn't have purchased one with an Atheros card...nooo...it had to be Broadcom lol.  I am interested to see if a solution if found here.  I can't use wired or wireless.  Neither work for me.  I love Realtek and Broadcom lol.

You are one up on me.  I did see a patch for the bcm43xx that you could get.  If you have a wired connection you could try:

> sudo apt-get install bcm43xx-fwcutter

I have not been able to try it as I have no internet connection in Ubuntu at all.  May do the trick.

---

### Post by kevdog on 2008-04-07
underdog

Please post

ndiswrapper -l
modinfo ndiswrapper

---

### Post by wertyuiop408 on 2008-04-07
[this should work for you]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc"), and bubbasheko just download the files and stick them onto a usb, cd etc and then install them in ubuntu

---

### Post by underdog512 on 2008-05-04
the wi-fi card works just fine on 8.04!!

---

