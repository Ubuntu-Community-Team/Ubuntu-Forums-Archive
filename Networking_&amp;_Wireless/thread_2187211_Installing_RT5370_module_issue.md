---
title: "Installing RT5370 module issue"
date: 2013-11-11
forum: Networking &amp; Wireless
---

### Post by tom14 on 2013-11-11
I received my RT5370 usb wifi dongle,but I can't get it work.I'm note sure if I did the installation properly.I've got cd with the dongle,plus I downloaded the driver-module from Ralink site.They don't seem identical though,and now I'm note sure which one I have installed if I did any at all :-)
Here are some infos:
```
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ lsb_release -d
Description:    Ubuntu 12.04.3 LTS
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
usb_storage            39646  0 
rt2800usb              22373  0 
rt2800lib              53298  1 rt2800usb
rt2x00usb              20099  1 rt2800usb
rt2x00lib              48923  3 rt2800usb,rt2800lib,rt2x00usb
arc4                   12473  2 
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ath5k                 145127  0 
radeon                733899  2 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
ath                    19387  1 ath5k
rtl8187                56323  0 
snd_timer              28931  2 snd_pcm,snd_seq
mac80211              436493  5 rt2800lib,rt2x00usb,rt2x00lib,ath5k,rtl8187
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39826  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd                    62218  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                96744  0 
cfg80211              178877  5 rt2x00lib,ath5k,ath,rtl8187,mac80211
drm                   197641  4 radeon,ttm,drm_kms_helper
soundcore              14635  1 snd
smsc_ircc2             28358  0 
serio_raw              13027  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
eeprom_93cx6           12687  1 rtl8187
yenta_socket           27428  0 
irda                  185517  1 smsc_ircc2
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
rfcomm                 38139  4 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
parport_pc             32114  1 
ppdev                  12849  0 
video                  19115  0 
crc_ccitt              12627  2 rt2800lib,irda
binfmt_misc            17292  1 
i2c_algo_bit           13199  1 radeon
wmi                    18744  0 
mac_hid                13077  0 
shpchp                 32265  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40180  0 
tg3                   141465  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
floppy                 60184  0 
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 

```
I would like to remove or uninstall previous installation,and do a fresh one,and do it properly.Thanks in advance for your help...

---

### Post by chili555 on 2013-11-11
> mac80211              436493  5 [COLOR="#FF0000"]rt2800lib,rt2x00usb,rt2x00lib,ath5k,rtl8187[/COLOR]Wow, Tom! You have a variety of wireless drivers loaded, most of which not only have nothing to do with your device, but probably conflict. Let's clean them up and see if the USB springs to life. First, open a terminal and do:```
gksudo gedit /etc/modules
```If any of the highlighted drivers except the rt2800xx gang are listed to be loaded automatically, remove them. Proofread carefully, save and close gedit. If you are in any doubt, post the contents of the file here and we'll work together.

The driver suite rt2800usb ought to drive your USB without any need to compile a downloaded driver once we get rid of the conflicts. Reboot and show us:```
lsusb
iwconfig
```

Do you have an internal device that's not working as expected? We probably need to blacklist its driver, as well. Please run and post:```
lspci -nn | grep 0280
```

---

### Post by tom14 on 2013-11-11
> **chili555 said:**
> Wow, Tom! You have a variety of wireless drivers loaded, most of which not only have nothing to do with your device, but probably conflict. Let's clean them up and see if the USB springs to life. First, open a terminal and do:```
gksudo gedit /etc/modules
```If any of the highlighted drivers except the rt2800xx gang are listed to be loaded automatically, remove them. Proofread carefully, save and close gedit. If you are in any doubt, post the contents of the file here and we'll work together.

The driver suite rt2800usb ought to drive your USB without any need to compile a downloaded driver once we get rid of the conflicts. Reboot and show us:```
lsusb
iwconfig
```

Do you have an internal device that's not working as expected? We probably need to blacklist its driver, as well. Please run and post:```
lspci -nn | grep 0280
```
There's only one thing listed at /etc/modules,it's lp,that's all.And also,there's nothing under lspci but info how to use it.Nothing listed.Internal module is ath5k,which I disconnect with modprobe -r ath5k

---

### Post by chili555 on 2013-11-11
Did you carefully enter the whole command? You can certainly copy and paste:```
lspci -nn | grep 0280
```If it still produces no result, then try:```
lspci -nn
```Please let me see:```
cat /etc/modules
ls /etc/modprobe.d
```We must be missing something else why would rtl8187 load??

---

### Post by tom14 on 2013-11-11
> **chili555 said:**
> Did you carefully enter the whole command? You can certainly copy and paste:```
lspci -nn | grep 0280
```If it still produces no result, then try:```
lspci -nn
```Please let me see:```
cat /etc/modules
ls /etc/modprobe.d
```We must be missing something else why would rtl8187 load??
  Here are the informations you've asked for::
```
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo su
[sudo] password for tom: 
root@tom-HP-Compaq-nc8000-DU449EA-ABD:/home/tom# lspci -nn | grep 0280
root@tom-HP-Compaq-nc8000-DU449EA-ABD:/home/tom# exit
exit
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ lspci -nn | grep 0280
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV350/M10 [Mobility Radeon 9600 PRO Turbo] [1002:4e50]
02:04.0 Ethernet controller [0200]: Qualcomm Atheros AR5212/AR5213 Wireless Network Adapter [168c:0013] (rev 01)
02:06.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller [1217:7223]
02:06.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller [1217:7223]
02:06.2 System peripheral [0880]: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator [1217:7110]
02:06.3 CardBus bridge [0607]: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller [1217:7223]
02:0d.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] [104c:8023]
02:0e.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet [14e4:165e] (rev 03)
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ ls /etc/modprobe.d
alsa-base.conf           blacklist-framebuffer.conf   blacklist-watchdog.conf
blacklist-ath_pci.conf   blacklist-modem.conf         vmwgfx-fbdev.conf
blacklist.conf           blacklist-oss.conf
blacklist-firewire.conf  blacklist-rare-network.conf
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 

```

---

### Post by chili555 on 2013-11-11
Is your internal Atheros not working as expected? Why did you need to get the USB? Do have any idea why rtl8187 loaded? Did you load it explicitly from the terminal? There are a few mysteries here!

---

### Post by tom14 on 2013-11-11
> **chili555 said:**
> Is your internal Atheros not working as expected? Why did you need to get the USB? Do have any idea why rtl8187 loaded? Did you load it explicitly from the terminal? There are a few mysteries here!
The router I use now is 70 yards away,only windows in between.The reason I ordered rt5370 was,I wanted to try some other chipset.My rtl8187 adapter didn't work good at all with 200 yards away router,and there was no way to use internal module for such a distance.Since I started to connect to closer router,throughout all of October,my rtl8187 was working fine,and even internal Atheros was working fine.Now,the situation is,I have a good connection for 5 to mostly 30 minutes,than it drops (both RTL8187 and Atheros are acting similarly),but most of the time I shut off Atheros because RTL has better reception with it's dish-like antenna.If everything's ok with RTL8187 connection,I wouldn't care for this new dongle.Both of them,RTL8187 and RT5370 have full signal and best link quality when I use them on MS-Windows,plus RT5370 is n type,it's so fast.I would like to have at least one reliable adapter that works with my ubuntu,which,by the way,more I use it,more I love it.Only this connection issue...

---

### Post by chili555 on 2013-11-11
Let's blacklist the ath5k.```
sudo -i
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
modprobe -r rtl8187
modprobe -r ath5k
exit
```Now let us see:```
nm-tool
```Does the USB see networks and try to connect?

---

### Post by tom14 on 2013-11-11
> **chili555 said:**
> Let's blacklist the ath5k.```
sudo -i
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
modprobe -r rtl8187
modprobe -r ath5k
exit
```Now let us see:```
nm-tool
```Does the USB see networks and try to connect?
I did all that,nm-tool shows only wired tg3 driver,and no wireless.I'm pretty sure that I've messed up something while playing with RT5370 driver installation,and now it won't load the driver...

---

### Post by chili555 on 2013-11-11
Does it start if you do:```
sudo modprobe rt2800usb
```

---

### Post by tom14 on 2013-11-11
> **chili555 said:**
> Does it start if you do:```
sudo modprobe rt2800usb
```
No,iwconfig output is: no wireless extension

---

### Post by chili555 on 2013-11-11
Curious! Let's see:```
uname -r
modinfo rt2800usb | grep 3070
```

---

### Post by tom14 on 2013-11-12
> **chili555 said:**
> Curious! Let's see:```
uname -r
modinfo rt2800usb | grep 3070
```
```
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ uname -r
3.2.0-55-generic
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ modinfo rt2800usb | grep 3070
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 

```

---

### Post by chili555 on 2013-11-12
As you can see, rt2800usb covers your device and ought to drive it:> tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ modinfo rt2800usb | grep 3070
alias:          usb:v[COLOR="#FF0000"]148F[/COLOR]p[COLOR="#FF0000"]3070[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*> ID [COLOR="#FF0000"]148f:3070[/COLOR] Ralink Technology, Corp. RT2870/RT3070 Wireless AdapterLet's try to see what's happening or, more correctly, not happening, when you load the module:```
sudo modprobe rt2800usb
dmesg | grep rt2
```Some laptops turn off all wireless, including USB, if the switch is set to 'Off;' let's check:```
rfkill list all
```Let's see if all the competing drivers are now out of the way:```
lsmod
```

---

### Post by tom14 on 2013-11-12
> **chili555 said:**
> As you can see, rt2800usb covers your device and ought to drive it:Let's try to see what's happening or, more correctly, not happening, when you load the module:```
sudo modprobe rt2800usb
dmesg | grep rt2
```Some laptops turn off all wireless, including USB, if the switch is set to 'Off;' let's check:```
rfkill list all
```Let's see if all the competing drivers are now out of the way:```
lsmod
```
```
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo modprobe rt2800usb
[sudo] password for tom: 
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ dmesg | grep rt2
[   33.908367] phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x3070 detected.
[   33.908374] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   33.908901] usbcore: registered new interface driver rt2800usb
[ 1355.755169] phy2 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x3070 detected.
[ 1355.755184] phy2 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[ 2488.573525] phy5 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x3070 detected.
[ 2488.573541] phy5 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[ 3985.089997] phy6 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x3070 detected.
[ 3985.090012] phy6 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[ 7177.022030] phy8 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x3070 detected.
[ 7177.022039] phy8 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ rfkill list all
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ lsmod
Module                  Size  Used by
btusb                  17948  0 
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
usb_storage            39646  0 
arc4                   12473  0 
rtl8187                56323  0 
eeprom_93cx6           12687  1 rtl8187
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
rt2800usb              22373  0 
rt2800lib              53298  1 rt2800usb
snd_seq_midi           13132  0 
rt2x00usb              20099  1 rt2800usb
snd_rawmidi            25424  1 snd_seq_midi
rt2x00lib              48923  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436493  4 rtl8187,rt2800lib,rt2x00usb,rt2x00lib
snd_seq_midi_event     14475  1 snd_seq_midi
radeon                733899  2 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178877  3 rtl8187,rt2x00lib,mac80211
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39826  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197641  4 radeon,ttm,drm_kms_helper
snd                    62218  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
smsc_ircc2             28358  0 
psmouse                96744  0 
irda                  185517  1 smsc_ircc2
soundcore              14635  1 snd
serio_raw              13027  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
i2c_algo_bit           13199  1 radeon
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
rfcomm                 38139  4 
crc_ccitt              12627  2 rt2800lib,irda
bnep                   17830  2 
parport_pc             32114  1 
ppdev                  12849  0 
bluetooth             158447  11 btusb,rfcomm,bnep
video                  19115  0 
binfmt_misc            17292  1 
wmi                    18744  0 
mac_hid                13077  0 
shpchp                 32265  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40180  0 
tg3                   141465  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
floppy                 60184  0 
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 

```
Wow,bunch of errors here!

---

### Post by chili555 on 2013-11-12
> mac80211              436493  4 [COLOR="#FF0000"]rtl8187[/COLOR],rt2800lib,rt2x00usb,rt2x00libIf it is not called in /etc/modules, why is rtl8187 loading? Have you tried the device while we are troubleshooting? I am not sure we are going to get anywhere with competing drivers loaded.> rt2800_init_eeprom: Error - Invalid RF chipset 0x3070 detected.Googling...

EDIT: See here: [https://github.com/raspberrypi/linux/issues/303](https://github.com/raspberrypi/linux/issues/303) and here: [http://www.geekamole.com/2013/rt2800usb-fix-for-ralinkmediatek-3070-gentoo-linux/](http://www.geekamole.com/2013/rt2800usb-fix-for-ralinkmediatek-3070-gentoo-linux/)  I'm working out a fix.

---

### Post by tom14 on 2013-11-12
> **chili555 said:**
> If it is not called in /etc/modules, why is rtl8187 loading? Have you tried the device while we are troubleshooting? I am not sure we are going to get anywhere with competing drivers loaded.Googling...

EDIT: See here: [https://github.com/raspberrypi/linux/issues/303](https://github.com/raspberrypi/linux/issues/303) and here: [http://www.geekamole.com/2013/rt2800usb-fix-for-ralinkmediatek-3070-gentoo-linux/](http://www.geekamole.com/2013/rt2800usb-fix-for-ralinkmediatek-3070-gentoo-linux/)  I'm working out a fix.
Yes,I probably have the same situation.I will also make changes once I figure out how to do it.

---

### Post by chili555 on 2013-11-12
> **tom14 said:**
> Yes,I probably have the same situation.I will also make changes once I figure out how to do it.I have already figured it out for you; it's what I do! Please get a temporary wired ethernet connection and do:```
sudo apt-get install build-essential linux-headers-generic
```Download this file to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/2013/11/07/backports-20131107.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/2013/11/07/backports-20131107.tar.bz2)  Right-click it and select 'Extract Here.' Now back to the terminal:```
cd Desktop/backports-20131107
make defconfig-wifi
make
sudo make install
```The process is a bit lengthy; please be patient. Detach the ethernet, reboot and let us have your report.

---

### Post by tom14 on 2013-11-13
> **chili555 said:**
> I have already figured it out for you; it's what I do! Please get a temporary wired ethernet connection and do:```
sudo apt-get install build-essential linux-headers-generic
```Download this file to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/2013/11/07/backports-20131107.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/2013/11/07/backports-20131107.tar.bz2)  Right-click it and select 'Extract Here.' Now back to the terminal:```
cd Desktop/backports-20131107
make defconfig-wifi
make
sudo make install
```The process is a bit lengthy; please be patient. Detach the ethernet, reboot and let us have your report.
This is what I get by make install,I think just too many errors,and my RT5370 not working yet
```
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ cd Desktop/backports-20131107
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~/Desktop/backports-20131107$ sudo make defconfig-wifi
[sudo] password for tom: 
make[2]: `conf' is up to date.
warning: (USB_NET_RNDIS_WLAN && USB_NET_RNDIS_HOST && USB_NET_ZAURUS) selects USB_NET_CDCETHER which has unmet direct dependencies (USB && NET && n && m && <choice> && USB_USBNET)
warning: (USB_NET_RNDIS_WLAN && USB_NET_RNDIS_HOST && USB_NET_ZAURUS) selects USB_NET_CDCETHER which has unmet direct dependencies (USB && NET && n && m && <choice> && USB_USBNET)
#
# configuration written to .config
#
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~/Desktop/backports-20131107$ sudo make
make[5]: `conf' is up to date.
warning: (USB_NET_RNDIS_WLAN && USB_NET_RNDIS_HOST && USB_NET_ZAURUS) selects USB_NET_CDCETHER which has unmet direct dependencies (USB && NET && n && m && <choice> && USB_USBNET)
warning: (USB_NET_RNDIS_WLAN && USB_NET_RNDIS_HOST && USB_NET_ZAURUS) selects USB_NET_CDCETHER which has unmet direct dependencies (USB && NET && n && m && <choice> && USB_USBNET)
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/tom/Desktop/backports-20131107/compat/main.o
  CC [M]  /home/tom/Desktop/backports-20131107/compat/compat-3.3.o
  CC [M]  /home/tom/Desktop/backports-20131107/compat/compat-3.4.o
  CC [M]  /home/tom/Desktop/backports-20131107/compat/compat-3.5.o
  CC [M]  /home/tom/Desktop/backports-20131107/compat/user_namespace.o
  CC [M]  /home/tom/Desktop/backports-20131107/compat/compat-3.6.o
  CC [M]  /home/tom/Desktop/backports-20131107/compat/compat-3.7.o
/home/tom/Desktop/backports-20131107/compat/compat-3.7.c: In function ‘of_get_child_by_name’:
/home/tom/Desktop/backports-20131107/compat/compat-3.7.c:275:2: error: implicit declaration of function ‘for_each_child_of_node’ [-Werror=implicit-function-declaration]
/home/tom/Desktop/backports-20131107/compat/compat-3.7.c:276:3: error: expected ‘;’ before ‘if’
cc1: some warnings being treated as errors
make[6]: *** [/home/tom/Desktop/backports-20131107/compat/compat-3.7.o] Error 1
make[5]: *** [/home/tom/Desktop/backports-20131107/compat] Error 2
make[4]: *** [_module_/home/tom/Desktop/backports-20131107] Error 2
make[3]: *** [modules] Error 2
make[2]: *** [modules] Error 2
make[1]: *** [modules] Error 2
make: *** [default] Error 2
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~/Desktop/backports-20131107$ sudo make install
  CC [M]  /home/tom/Desktop/backports-20131107/compat/compat-3.7.o
/home/tom/Desktop/backports-20131107/compat/compat-3.7.c: In function ‘of_get_child_by_name’:
/home/tom/Desktop/backports-20131107/compat/compat-3.7.c:275:2: error: implicit declaration of function ‘for_each_child_of_node’ [-Werror=implicit-function-declaration]
/home/tom/Desktop/backports-20131107/compat/compat-3.7.c:276:3: error: expected ‘;’ before ‘if’
cc1: some warnings being treated as errors
make[5]: *** [/home/tom/Desktop/backports-20131107/compat/compat-3.7.o] Error 1
make[4]: *** [/home/tom/Desktop/backports-20131107/compat] Error 2
make[3]: *** [_module_/home/tom/Desktop/backports-20131107] Error 2
make[2]: *** [modules] Error 2
make[1]: *** [modules] Error 2
make: *** [install] Error 2
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~/Desktop/backports-20131107$ 

```

---

### Post by tom14 on 2013-11-13
Here is lsmod too,it should be working,but it's dead,no led or anything,and no other drivers loaded...
```
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
rt2800usb              22373  0 
rt2800lib              53298  1 rt2800usb
rt2x00usb              20099  1 rt2800usb
snd_rawmidi            25424  1 snd_seq_midi
rt2x00lib              48923  3 rt2800usb,rt2800lib,rt2x00usb
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
mac80211              436493  3 rt2800lib,rt2x00usb,rt2x00lib
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon                733899  2 
psmouse                96744  0 
smsc_ircc2             28358  0 
cfg80211              178877  2 rt2x00lib,mac80211
snd                    62218  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
irda                  185517  1 smsc_ircc2
serio_raw              13027  0 
soundcore              14635  1 snd
pcmcia                 39826  0 
ttm                    65344  1 radeon
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
drm_kms_helper         45466  1 radeon
video                  19115  0 
rfcomm                 38139  4 
bnep                   17830  2 
parport_pc             32114  1 
crc_ccitt              12627  2 rt2800lib,irda
ppdev                  12849  0 
bluetooth             158447  10 rfcomm,bnep
drm                   197641  4 radeon,ttm,drm_kms_helper
binfmt_misc            17292  1 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
wmi                    18744  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
mac_hid                13077  0 
i2c_algo_bit           13199  1 radeon
shpchp                 32265  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
tg3                   141465  0 
crc_itu_t              12627  1 firewire_core
floppy                 60184  0 
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 

```

---

### Post by chili555 on 2013-11-13
First of all, when you, on this or any future compilation, see an error at 'make,' stop and fix it as all further steps will also be faulty. No module will be built and no device will work.

Second, I installed 12.04 LTS especially, among other projects, so I could test this fix. It works perfectly for me! My system differs in only one minor respect. You have:```
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ uname -r
[COLOR="#FF0000"]3.2.0-55-generic[/COLOR]
```And I have:```
chili@ThinkT60:~$ uname -r
3.2.0-[COLOR="#FF0000"]56[/COLOR]-generic-[COLOR="#FF0000"]pae[/COLOR]
```I really don't see how either makes any material difference. First, let's see if your CPU supports PAE:```
grep --color=always -i PAE /proc/cpuinfo
```If so, then I suggest you try:```
sudo apt-get install linux-image-3.2.0-[COLOR="#FF0000"]56[/COLOR]-generic-[COLOR="#FF0000"]pae[/COLOR]
```Watch carefully for any errors or warnings. If you get none, then do:```
sudo apt-get install linux-headers-3.2.0-56-generic-pae
```If all goes successfully, reboot and interrupt the boot process by immediately pressing the shift key to see the GRUB menu. Be sure you are booting into the -56 pae kernel and try the compile again.

If there are errors or alarming warnings, *STOP* and post them here before you proceed. Please see here for an example of the GRUB  menu. [http://www.subdude-site.com/WebPages_Local/RefInfo/Computer/Linux/UbuntuInstalls/images_diskPartition_Cyberpower/D029_ubuntuUpdateManagerDone_grubMenu_2010-10-12_18:22_946x693.jpg](http://www.subdude-site.com/WebPages_Local/RefInfo/Computer/Linux/UbuntuInstalls/images_diskPartition_Cyberpower/D029_ubuntuUpdateManagerDone_grubMenu_2010-10-12_18:22_946x693.jpg)

If your CPU doesn't support PAE, post back and I will wash down a few aspirins and we'll proceed.

---

### Post by tom14 on 2013-11-14
Thanks a lot Chili,my CPU doesn't support PAE,that was the only reason I installed xubuntu 12.04 non-pae,and not ubuntu 13.04 pae version

---

### Post by tom14 on 2013-11-19
OK Chili,this is what I did with my drivers.I put them all on the blacklist.And then I enabled RTL8187 only.And it works without interruption for 5 days now.For some reason RT5370 doesn't function with my linux machine,maybe because it's non-pae?.In case I accidentally or somehow find out what was wrong,I'll get back here and post my observations.Chili,thanks a lot for your time and patience

---

### Post by chili555 on 2013-11-19
> **tom14 said:**
> OK Chili,this is what I did with my drivers.I put them all on the blacklist.And then I enabled RTL8187 only.And it works without interruption for 5 days now.For some reason RT5370 doesn't function with my linux machine,maybe because it's non-pae?.In case I accidentally or somehow find out what was wrong,I'll get back here and post my observations.Chili,thanks a lot for your time and patienceI suspect that's the case. The driver was written assuming that 98% of all computers support PAE and sadly, yours doesn't. Linux is already no more than 4-5% of the market and to write a driver for 2% of the already slight 5% probably isn't seen as worth the effort to the manufacturers. Sorry.

---

