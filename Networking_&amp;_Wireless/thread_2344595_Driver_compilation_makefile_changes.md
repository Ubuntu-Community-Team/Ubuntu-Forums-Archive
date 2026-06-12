---
title: "Driver compilation makefile changes"
date: 2016-11-26
forum: Networking &amp; Wireless
---

### Post by pietervanderstar on 2016-11-26
Hello,

I have used a couple of linux versions in the past, and for each of them the hardware I needed just worked. But today I got a problem using a new Wifi dongle (If I should have posted this thread in the wireless section please let me know.) And I never had to deal with anything like this. Most of the stuff I did was some programming and setting up databases and servers. Now I need to work on the driver. Seraching both the web and this forum I only found people with the same problem, but no solutions. The instructions tell me to set some parameters in the makefile. 
EXTRA_CFLAGS += -DCONFIG_LITTLE_ENDIAN
SUBARCH := $(shell uname -m | sed -e s/i.86/i386/)
[I][B]ARCH ?= $(SUBARCH)
CROSS_COMPILE ?=
KVER := $(shell uname -r)[/B][/I]
KSRC := /lib/modules/$(KVER)/build
Where the bold is supposed to be the stuff I need to change/add to (I think). But without an example I have no idea what to do here.
I realize this is probably asking a pilot to go round with the foodcart, but I am stuck.
output of uname -a:
```
Linux STC2016021 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```
I hope you can help me out.

---

### Post by howefield on 2016-11-26
Moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by jeremy31 on 2016-11-26
What wifi dongle?  Please post results for ```
lsusb
```

---

### Post by pietervanderstar on 2016-11-28
It is a TL-WN822N V4. The driver is downloaded from  [http://www.tp-link.com/us/download/TL-WN822N_V4.html#Driver](http://www.tp-link.com/us/download/TL-WN822N_V4.html#Driver). This is for older Ubuntu versions. I can return the device, but I'd like to have tried to get it working first. Some info:```
uname:   Linux STC2016021 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux/ lsusb (the line of the device):   Bus 001 Device 007: ID 2357:0108
``` I got a driver from somewere on the internet: ```
git clone https://github.com/jeremyb31/rtl8192eu-linux-driver cd rtl8192eu-linux-driver/ sudo make sudo make install
``` So it kind of works now. I frequently lose connection for a moment, I need to reconnect the device after boot etc.

p.s. lshw -c network returned:
```
  *-network               
       description: Ethernet interface
       product: I211 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: enp6s0
       version: 03
       serial: d0:50:99:ae:17:d5
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.3.0-k firmware=0. 4-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:19 memory:df900000-df91ffff ioport:b000(size=32) memory:df920000-df923fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (2) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 31
       serial: d0:50:99:ae:17:d7
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.8-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:149 memory:dfd00000-dfd1ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:7
       logical name: enx18a6f7132d7a
       serial: 18:a6:f7:13:2d:7a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192eu ip=192.168.2.2 multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by jeremy31 on 2016-11-28
Please post results for ```
iwconfig; modinfo -p rtl8192eu
```

---

### Post by pietervanderstar on 2016-11-28
here you go
```
lo        no wireless extensions.

enp0s31f6  no wireless extensions.

enx18a6f7132d7a  IEEE 802.11bgn  ESSID:"<my network name>"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 2C:95:7F:4C:6C:1F   
          Bit Rate:130 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/100  Signal level=86/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

enp6s0    no wireless extensions.

modinfo: ERROR: Module rtl8192eu not found.

```

---

### Post by jeremy31 on 2016-11-28
See if```
echo "options 8192eu rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/8192eu.conf
```
Helps after a reboot

---

### Post by pietervanderstar on 2016-11-28
That didn't work. I still had to pull out the usb connector and than put it back in.
It may be the device is on a hub, I'll try another port and report back.

---

### Post by pietervanderstar on 2016-11-28
nope, still does not work

---

### Post by jeremy31 on 2016-11-28
Let's try Mange's driver
```
mkdir mange
cd mange
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
cd ~/rtl8192eu-linux-driver
sudo make uninstall
cd mange/rtl8192eu-linux-driver
make
sudo make install
```

Reboot

Mange has made some newer commits that may help

---

### Post by pietervanderstar on 2016-11-28
Thanks, that worked. 
I still have a question. What did this command do?
```
echo "options 8192eu rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/8192eu.conf
```

---

### Post by jeremy31 on 2016-11-28
That command disables the modules power management and the usb power management that is in the module.  I knew it was used in Pvaret's rtl8192cu module to fix some disconnect issues so I figured it would also help with this chipset

[https://github.com/pvaret/rtl8192cu-fixes/blob/master/8192cu-disable-power-management.conf](https://github.com/pvaret/rtl8192cu-fixes/blob/master/8192cu-disable-power-management.conf)

---

### Post by pietervanderstar on 2016-11-29
Well, it seems yesterday was an exception. Last night I shut down my computer. When I just booted the wireless did not respond, even with that echo command mentioned in my previous post I could not get it working. 
I think I will go back to the store and see if they have another.

---

### Post by jeremy31 on 2016-11-29
Check your kernel to see if it was updated
If you have 4.4.0-48 you will need to recompile
```

cd ~/mange/rtl8192eu-linux-driver
make clean
make
sudo make install
```
Then reboot

---

### Post by pietervanderstar on 2016-11-29
nope, I am still running 4.4.0-47
I did a recompile and reinstall and it worked over one reboot, after the second reboot it stopped working.

---

### Post by pietervanderstar on 2016-11-29
I just tried
```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8192eu-dkms
```
with the same results.

---

### Post by jeremy31 on 2016-11-30
Does ```
lsmod | grep 8192
```
Have any results when it fails to work, also check
```
dmesg | grep 8192
```

---

### Post by pietervanderstar on 2016-11-30
The results (with hanipouspilot/rtlwifi)
```
lsmod|grep 8192
8192eu               1708032  0
snd                    81920  31 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device

```
the dmsg command was not found because I aparently have three.
```
dmsg|grep 8192
No command 'dmsg' found, did you mean:
 Command 'qmsg' from package 'torque-client-x11' (universe)
 Command 'qmsg' from package 'torque-client' (universe)
 Command 'dmesg' from package 'util-linux' (main)
dmsg: command not found

```

---

### Post by jeremy31 on 2016-11-30
You had a typo on the second command, it is
```
dmesg | grep 8192
```

Not
```
dmsg | grep 8192
```

---

### Post by pietervanderstar on 2016-12-01
yup, sorry.
```
dmesg | grep 8192
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff880476400000 s98008 r8192 d28968 u262144
[    0.000000] pcpu-alloc: s98008 r8192 d28968 u262144 alloc=1*2097152
[    0.314587] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.314614] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    3.839455] RTL871X: rtl8192eu v4.3.15_14701.20150715_BTCOEX20150615-41
[    3.839457] RTL871X: rtl8192eu BT-Coex version = BTCOEX20150615-41
[    3.839514] RTL871X: CHIP TYPE: RTL8192E
[    3.840395] RTL871X: Chip Version Info: CHIP_8192E_Normal_Chip_SMIC_B_CUT_2T2R_RomVer(0)
[    3.840398] RTL871X: _ConfigChipOutEP_8192E OutEpQueueSel(0x07), OutEpNumber(3) 
[    3.840399] RTL871X: ====> ReadAdapterInfo8192EU
[    3.898571] RTL871X: hal_ReadMACAddress_8192EU MAC Address from EFUSE = 18:a6:f7:13:2d:7a
[    3.898573] RTL871X: Hal_ReadPowerSavingMode8192E...bHWPwrPindetect(0)-bHWPowerdown(0) ,bSupportRemoteWakeup(1)
[    3.898576] RTL871X: Hal_EfuseParseBTCoexistInfo8192E: Disable BT-coex, wifi ant_num=2
[    3.898580] RTL871X: ReadAdapterInfo8192EU <====
[    3.898946] usbcore: registered new interface driver rtl8192eu
[    3.899793] rtl8192eu 1-12:1.0 enx18a6f7132d7a: renamed from wlan0

```

---

### Post by jeremy31 on 2016-12-02
Was that done after a disconnect or just after booting?  It doesn't show anything wrong.  Next time see if ```
dmesg | egrep '8192|enx18'
```
Shows anything

---

### Post by pietervanderstar on 2016-12-05
I have returned the adapter and it has been replaced by a Eminent device. That worked out of the box.
Thanks for your help.

---

