---
title: "TP-Link TL-WN823N not detected on Ubuntu 16.04"
date: 2017-01-06
forum: Networking &amp; Wireless
---

### Post by thecrazydude778 on 2017-01-06
Hello,

So the problem is that this Wi-Fi adapter is not being detected at all. I have already tried to install the driver suppled by the TP-Link website but it didn't work because when I tried to compile and install the driver there were too many errors and the file couldn't be installed. I tried using the terminal to display all the USB devices and I could see was a device that didn't have a name at all (the space was totally blank). I've also tried reinstalling network manager and trying all the solutions and drivers I could find. I tried plugging it into different USB ports, Pressing the WPS button and installing more drivers.

I've looked at the following websites and tried out most of their solutions:

- [https://ubuntuforums.org/showthread.php?t=2266703](https://ubuntuforums.org/showthread.php?t=2266703) 
-  [https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md](https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md)

This is the output of sudo lshw -C network (My ethernet and my iPhone 5 hotspot)

```
*-network               
       description: Ethernet interface
       product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 02
       serial: 00:19:b9:44:37:01
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5754-v3.15 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:fe6f0000-fe6fffff
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@2:3
       logical name: enx9e04eb0a161a
       serial: 9e:04:eb:0a:16:1a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth ip=172.20.10.5 link=yes multicast=yes

and this is the list of USB drive and devices connected to the computer.

Bus 002 Device 002: ID 05ac:12a8 Apple, Inc. iPhone5/5C/5S/6
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 04b3:301b IBM Corp. SK-8815 Keyboard
Bus 007 Device 002: ID 04b3:301a IBM Corp. 2-port low-power hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 2357:0109  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

The device is an Optiplex 745 and it is running Ubuntu 16.04 LTS
The wireless adapter is a TP-Link TL-WN823N version 2.

Nothing is working right now. Please help me. 

Thanks.

---

### Post by wildmanne39 on 2017-01-06
Please do:
```
sudo apt-get update
sudo apt-get install git linux-headers-generic build-essential dkms

```
```
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.10
sudo depmod -a
sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
```
Edit: 
If you have secure boot on you will have to turn it off before installing the driver by going into the bios.
You may want to try another usb port.
Reboot

---

### Post by wildmanne39 on 2017-01-06
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by thecrazydude778 on 2017-01-06
I will use code tags next time (This was my first thread I made anyway). Anyway the wireless adapter still doesn't work and nothing has changed. I plugged it into another USB slot and restarted and it still hasn't worked yet. I also tried it on another Ubuntu system (a small acer laptop) with the same thing happening (showing no device name). I also tried it with my main laptop (running Windows 10) and it worked without any driver installation at all.

---

### Post by wildmanne39 on 2017-01-06
Please paste the output of all the commands so we can see what is going on.
```
dmesg | grep rtl
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
Thanks

---

### Post by thecrazydude778 on 2017-01-06
Nothing happened for the first one.

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04 LTS"
Linux server-OptiPlex-745 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

```
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express [14e4:167a] (rev 02)
    Subsystem: Dell OptiPlex 745 [1028:01da]
    Kernel driver in use: tg3
```

lsusb:
```
Bus 002 Device 002: ID 05ac:12a8 Apple, Inc. iPhone5/5C/5S/6
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 04b3:301b IBM Corp. SK-8815 Keyboard
Bus 006 Device 002: ID 04b3:301a IBM Corp. 2-port low-power hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 2357:0109  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

iwconfig:
```
lo        no wireless extensions.

enx9e04eb0a161a  no wireless extensions.

enp3s0    no wireless extensions.

```

rfkill list all (Nothing happened)


lsmod:
```
Module                  Size  Used by
nls_iso8859_1          16384  0
uas                    24576  0
usb_storage            69632  1 uas
appletalk              36864  0
ipx                    28672  0
p8023                  16384  1 ipx
p8022                  16384  1 ipx
psnap                  16384  2 ipx,appletalk
llc                    16384  2 p8022,psnap
ipheth                 16384  0
snd_hda_codec_analog    16384  1
snd_hda_codec_generic    77824  1 snd_hda_codec_analog
snd_hda_intel          40960  3
snd_hda_codec         135168  3 snd_hda_codec_generic,snd_hda_intel,snd_hda_codec_analog
snd_hda_core           73728  4 snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_hda_codec_analog
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
coretemp               16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
kvm_intel             172032  0
snd_timer              32768  2 snd_pcm,snd_seq
kvm                   540672  1 kvm_intel
snd                    81920  16 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog
soundcore              16384  1 snd
irqbypass              16384  1 kvm
input_leds             16384  0
dcdbas                 16384  0
joydev                 20480  0
serio_raw              16384  0
shpchp                 36864  0
lpc_ich                24576  0
8250_fintek            16384  0
mac_hid                16384  0
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 hid_generic,usbhid
psmouse               131072  0
pata_acpi              16384  0
i915                 1208320  8
tg3                   163840  0
ptp                    20480  1 tg3
pps_core               20480  1 ptp
floppy                 73728  0
video                  40960  1 i915
i2c_algo_bit           16384  1 i915
drm_kms_helper        155648  1 i915
fjes                   28672  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  10 i915,drm_kms_helper

```

Two of them didn't display anything.

---

### Post by wildmanne39 on 2017-01-06
Please install usb mode switch it is in the repositories and I think that will take care of the issue, what it does is make it not show as a storage device and show as a wifi adapter. It is after 3 AM here so I am getting of for tonight.
Thanks

---

### Post by jeremy31 on 2017-01-06
This WN823N uses a chipset other than the rtl8192cu so
```
sudo dkms remove 8192cu/1.10 --all
sudo depmod -a
sudo rm /etc/modprobe.d/blacklist-native-rtl8192.conf
```

Then we can use Pilot6's PPA to install the driver
```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8192eu-dkms
```

Reboot

---

### Post by thecrazydude778 on 2017-01-06
The USB wireless adapter now works but that was after install usb_modeswitch and after trying another driver it finally showed up after taking it out and plugging it back in again. I'm not sure if it was USB mode switch or the other driver I tried but it's fixed now.

Also I already tried jeremy31's solution but that didn't work. It's refused to download and it wouldn't add the repository.

Anyway it works now so thanks.

Handy Link: [http://askubuntu.com/questions/820886/problem-with-tp-link-tl-wn823n?noredirect=1&lq=1](http://askubuntu.com/questions/820886/problem-with-tp-link-tl-wn823n?noredirect=1&lq=1)

---

### Post by wildmanne39 on 2017-01-06
Glad it is working! would you please post the output of:
```
lsmod
```
that will help us learn so we can better help.
Enjoy!

---

### Post by jeremy31 on 2017-01-06
What other driver as I can think of only 2 others and they are both on github- mange and jeremyb31 but I think dkms support isn't available and the driver will need to be recompiled after kernel updates

---

### Post by thecrazydude778 on 2017-01-06
Here's what lsmod outputted:
```

Module                  Size  Used by
cfg80211              565248  0
8192eu                929792  0
snd_hda_codec_analog    16384  1
snd_hda_codec_generic    77824  1 snd_hda_codec_analog
snd_hda_intel          40960  3
snd_hda_codec         135168  3 snd_hda_codec_generic,snd_hda_intel,snd_hda_codec_analog
snd_usb_audio         176128  1
snd_hda_core           73728  4 snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_hda_codec_analog
snd_usbmidi_lib        36864  1 snd_usb_audio
snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
snd_pcm               106496  4 snd_usb_audio,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
coretemp               16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  2 snd_usbmidi_lib,snd_seq_midi
kvm_intel             172032  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
kvm                   540672  1 kvm_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  20 snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog
soundcore              16384  1 snd
irqbypass              16384  1 kvm
input_leds             16384  0
joydev                 20480  0
dcdbas                 16384  0
serio_raw              16384  0
shpchp                 36864  0
lpc_ich                24576  0
8250_fintek            16384  0
mac_hid                16384  0
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 hid_generic,usbhid
psmouse               131072  0
tg3                   163840  0
pata_acpi              16384  0
i915                 1208320  8
ptp                    20480  1 tg3
pps_core               20480  1 ptp
floppy                 73728  0
video                  40960  1 i915
i2c_algo_bit           16384  1 i915
fjes                   28672  0
drm_kms_helper        155648  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  10 i915,drm_kms_helper
```

---

### Post by wildmanne39 on 2017-01-06
Thanks for posting the lsmod output and if you installed the driver using this method
[https://github.com/Mange/rtl8192eu-linux-driver](https://github.com/Mange/rtl8192eu-linux-driver)
it looks like you do not have to worry about recompiling the driver when there is an update to the kernel unless there is an issue that I do not know about.

---

### Post by thecrazydude778 on 2017-01-06
Okay, thanks!

---

### Post by naja42 on 2017-02-19
I just made an homemade upgrade to the [official driver for Ubuntu 14]("http://www.tp-link.fr/download/TL-WN823N.html#Driver"), so it works with Ubuntu 16.04. I'm using it actually to post this message, it works properly, but no guarantee.

[Driver for TP-Link TL-WN823N for Ubuntu 16.04]("http://www.revaweb.com/data/TL-WN823NEU_V22_17_02_26_Linux.tar.gz")

Instructions :
-Extract files in a <directory>
Then, open a Terminal :
-"cd <directory>"
-"cd Driver"
-&#8220;sudo make&#8221; to compile the driver file.
-&#8220;sudo make install&#8221; to install the driver file.

All the working details :
Compiling the official driver for Ubuntu 14 shows that some functions need few more parameters to work with Ubuntu 16.04. *I have no idea what these new parameters are for*. I filled them with "0" and "NULL" and It's working : I'm actually using it to write this post. Hope for the best :wink:

---

### Post by tequila mambo on 2017-08-31
Thanks a lot for updating the drivers. Unfortunately this is not working for me. I downloaded your drivers and follow your instructions. When I run "sudo make", I get the output below.

My kernel is 4.10.0-28-generic

Thanks in advance!


```
"******************************************"
"NO SKRC,we will use default KSRC"
"******************************************"
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.10.0-28-generic/build M=/home/userName/Downloads/TL-WN823NEU_V22_17_02_26_Linux/Driver  modules
make[1]: Entering directory '/usr/src/linux-headers-4.10.0-28-generic'
"******************************************"
"NO SKRC,we will use default KSRC"
"******************************************"
  CC [M]  /home/userName/Downloads/TL-WN823NEU_V22_17_02_26_Linux/Driver/os_dep/linux/ioctl_linux.o
/home/userName/Downloads/TL-WN823NEU_V22_17_02_26_Linux/Driver/os_dep/linux/ioctl_linux.c: In function ‘rtw_ioctl_wext_private’:
/home/userName/Downloads/TL-WN823NEU_V22_17_02_26_Linux/Driver/os_dep/linux/ioctl_linux.c:15716:5: error: implicit declaration of function ‘is_compat_task’ [-Werror=implicit-function-declaration]
  if(is_compat_task())
     ^
cc1: some warnings being treated as errors
scripts/Makefile.build:294: recipe for target '/home/userName/Downloads/TL-WN823NEU_V22_17_02_26_Linux/Driver/os_dep/linux/ioctl_linux.o' failed
make[2]: *** [/home/userName/Downloads/TL-WN823NEU_V22_17_02_26_Linux/Driver/os_dep/linux/ioctl_linux.o] Error 1
Makefile:1524: recipe for target '_module_/home/userName/Downloads/TL-WN823NEU_V22_17_02_26_Linux/Driver' failed
make[1]: *** [_module_/home/userName/Downloads/TL-WN823NEU_V22_17_02_26_Linux/Driver] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-28-generic'
Makefile:1696: recipe for target 'modules' failed
make: *** [modules] Error 2
```

---

### Post by wildmanne39 on 2017-08-31
Hello, please do:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```
then go into the directory and do:
```
make clean
```
then try again.

Copy and paste all commands for accuracy.

---

### Post by wildmanne39 on 2017-08-31
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by tequila mambo on 2017-08-31
Thanks!

I ran 
[HTML]sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms[/HTML]

and it went well. Then I ran 
[HTML]make clean[/HTML]
in the directory of the drivers and got 
[HTML]"******************************************"
"NO SKRC,we will use default KSRC"
"******************************************"
cd hal/OUTSRC/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal/OUTSRC/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
[/HTML]

Then, I ran 
[HTML]make[/HTML]
and got the following error
[HTML]/home/userName/Downloads/TL-WN823NEU_V22_17_02_26_Linux/Driver/os_dep/linux/ioctl_linux.c: In function ‘rtw_ioctl_wext_private’:
/home/userName/Downloads/TL-WN823NEU_V22_17_02_26_Linux/Driver/os_dep/linux/ioctl_linux.c:15716:5: error: implicit declaration of function ‘is_compat_task’ [-Werror=implicit-function-declaration]
  if(is_compat_task())
     ^
cc1: some warnings being treated as errors
scripts/Makefile.build:294: recipe for target '/home/userName/Downloads/TL-WN823NEU_V22_17_02_26_Linux/Driver/os_dep/linux/ioctl_linux.o' failed
make[2]: *** [/home/userName/Downloads/TL-WN823NEU_V22_17_02_26_Linux/Driver/os_dep/linux/ioctl_linux.o] Error 1
Makefile:1524: recipe for target '_module_/home/userName/Downloads/TL-WN823NEU_V22_17_02_26_Linux/Driver' failed
make[1]: *** [_module_/home/userName/Downloads/TL-WN823NEU_V22_17_02_26_Linux/Driver] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-28-generic'
Makefile:1696: recipe for target 'modules' failed
make: *** [modules] Error 2
[/HTML]

Which I think is still the same.

Any ideas?

---

### Post by jeremy31 on 2017-08-31
Please post the results for ```
lsusb
```
There is a good chance that the source code provided by naja42 doesn't work with the 4.10 kernel

---

### Post by jibinkk on 2017-10-30
**TP Link TL-WN725N not working in ubuntu 14.04**

Hi,
Tried steps as given in [http://brilliantlyeasy.com/ubuntu-linux-tl-wn725n-tp-link-version-2-wifi-driver-install/](http://brilliantlyeasy.com/ubuntu-linux-tl-wn725n-tp-link-version-2-wifi-driver-install/)

[U]below is the wireless info
[/U]ifconfig lists the wifi adapter, but it does not detect any wifi signal[U]

Kindly help
[/U]
```
########## wireless info START ##########

Report from: 30 Oct 2017 23:58 IST +0530

Booted last: 30 Oct 2017 23:45 IST +0530

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.4.0-22-generic #40~14.04.1-Ubuntu SMP Fri May 13 17:27:18 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME Flashback (Metacity)

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 275d:0ba6  
Bus 001 Device 005: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 001 Device 006: ID 1a2c:2124 China Resource Semico Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              487424  0 
8188eu                671744  0 
mxm_wmi                16384  1 nouveau
wmi                    16384  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3954873 (3.9 MB)  TX bytes:547634 (547.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2073 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2073 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:173344 (173.3 KB)  TX bytes:173344 (173.3 KB)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       793     1  0 23:45 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8188eu
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan1' [IF2]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan1     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency=2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     No scan results

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[8188eu]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/8188eu.ko
version:        v4.1.4_6773.20130222
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     9DBEC54D57C1F4AE944C14E
depends:        
vermagic:       4.4.0-22-generic SMP mod_unload modversions 686 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_fw_iol:FW IOL (int)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

[8188eu]
debug: 1
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_busy_thresh: 40
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 66
rtw_chip_version: 0
rtw_enusbss: 0
rtw_fw_iol: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_power_mgnt: 1
rtw_rf_config: 5
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/50-8188eu.conf]
blacklist r8188eu

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[    7.494669] r8188eu 1-3:1.0 wlan1: renamed from wlan0
[    7.552521] systemd-udevd[347]: renamed network interface wlan0 to wlan1
[   10.717776] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[   10.814650] r8169 0000:02:00.0 eth0: link down
[   10.814696] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   69.563409] r8169 0000:02:00.0 eth0: link up
[   69.563428] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   93.837643] r8188eu 1-5:1.0 wlan1: renamed from wlan0
[   93.856545] systemd-udevd[2148]: renamed network interface wlan0 to wlan1
[   94.266449] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 3 times)

########## wireless info END ############
```

---

### Post by zhayat on 2018-02-25
> **wildmanne39 said:**
> Please install usb mode switch it is in the repositories and I think that will take care of the issue, what it does is make it not show as a storage device and show as a wifi adapter. It is after 3 AM here so I am getting of for tonight.
Thanks

Hi I'm having exactly the same issue install the tp-link driver on Ubuntu 16.04
I have followed all the steps in the previous posts on this thread,however can you please advise on how I install usb mode switch?

thanks in advance.

below is my system info:

> cat /etc/lsb-release; uname
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.4 LTS"

> lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Qualcomm Atheros Attansic L1 Gigabit Ethernet [1969:1048] (rev b0)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard [1043:8226]
    Kernel driver in use: atl1

> lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c70a Logitech, Inc. MX5000 Cordless Desktop
Bus 003 Device 003: ID 046d:c70e Logitech, Inc. MX1000 Bluetooth Laser Mouse
Bus 003 Device 005: ID 046d:c709 Logitech, Inc. BT Mini-Receiver (HCI mode)
Bus 003 Device 002: ID 046d:0b02 Logitech, Inc. C-UV35 [Bluetooth Mini-Receiver] (HID proxy mode)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by mmp153 on 2018-07-06
You can also try these steps
```

sudo apt-get update
sudo apt-get install git linux-headers-generic build-essential dkms
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
sudo dkms add ./rtl8192eu-linux-driver
sudo dkms install 8192eu/1.0
sudo depmod -a
sudo reboot

```
Hope it helps

---

