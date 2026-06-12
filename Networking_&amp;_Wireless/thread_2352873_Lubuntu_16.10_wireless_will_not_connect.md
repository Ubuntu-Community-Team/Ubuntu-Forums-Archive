---
title: "Lubuntu 16.10 wireless will not connect"
date: 2017-02-16
forum: Networking &amp; Wireless
---

### Post by pelai on 2017-02-16
Hi!

I've just installed a the Lubuntu 16.10 with alternate iso on my Sony Vaio Notebook Model PCG-21313M and the network connection does not work at all, neither the wifi nor the ethernet connection. When clicking on the Networks button on the taskbar it shows those messages regarding Ethernet and Wi-fi Networks:

Ethernet Network
device not managed

Wi-Fi Network
device not ready

I'm quite new in Ubuntu and Linux so I'm not sure how to solve it and what information do I need to provide.

Thanks in advance!

---

### Post by wildmanne39 on 2017-02-16
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by wildmanne39 on 2017-02-16
*Thread moved to **Networking & Wireless**.*

---

### Post by pelai on 2017-02-16
Hi [COLOR=#000000]wildmanne39,

Thanks! These are the results of the commands:

[/COLOR]```
$ cat /etc/lsb-release;uname -aDISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.10
DISTRIB_CODENAME=yakkety
DISTRIB_DESCRIPTION="Ubuntu 16.10"
Linux Petit-Vaio 4.8.0-22-generic #24-Ubuntu SMP Sat Oct 8 09:14:42 UTC 2016 i686 i686 i686 GNU/Linux


$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Kernel driver in use: rt2800pci
--
02:00.5 Ethernet controller [0200]: JMicron Technology Corp. JMC260 PCI Express Fast Ethernet Controller [197b:0260] (rev 02)
    Subsystem: Sony Corporation JMC260 PCI Express Fast Ethernet Controller [104d:9075]
    Kernel driver in use: jme
    Kernel modules: jme


$ lsusb
Bus 001 Device 002: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 18a5:0303 Verbatim, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


$ iwconfig
lo        no wireless extensions.


enp2s0f5  no wireless extensions.


wlp1s0    IEEE 802.11  ESSID:"InTheGhetto"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: EC:08:6B:74:66:EE   
          Bit Rate=52 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-23 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:6060   Missed beacon:0


$ rfkill list all
0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


$lsmod
Module                  Size  Used by
nls_iso8859_1          16384  1
uas                    20480  0
usb_storage            57344  2 uas
ccm                    20480  1
arc4                   16384  2
rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
uvcvideo               77824  0
rt2800lib              90112  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              49152  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
videobuf2_vmalloc      16384  1 uvcvideo
mac80211              679936  3 rt2800lib,rt2x00pci,rt2x00lib
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              159744  3 uvcvideo,videobuf2_core,videobuf2_v4l2
snd_hda_codec_realtek    77824  1
cfg80211              512000  2 rt2x00lib,mac80211
media                  36864  2 uvcvideo,videodev
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_hda_intel          32768  3
gpio_ich               16384  0
snd_hda_codec         118784  3 snd_hda_intel,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           69632  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_generic,snd_hda_codec_realtek
eeprom_93cx6           16384  1 rt2800pci
snd_hwdep              16384  1 snd_hda_codec
snd_pcm                94208  3 snd_hda_intel,snd_hda_codec,snd_hda_core
jmb38x_ms              20480  0
coretemp               16384  0
snd_timer              32768  1 snd_pcm
snd                    69632  13 snd_hda_intel,snd_hwdep,snd_hda_codec,snd_timer,snd_hda_codec_generic,snd_hda_codec_realtek,snd_pcm
input_leds             16384  0
joydev                 20480  0
memstick               16384  1 jmb38x_ms
soundcore              16384  1 snd
serio_raw              16384  0
sony_laptop            53248  0
lpc_ich                20480  0
shpchp                 32768  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              20480  0
x_tables               24576  1 ip_tables
autofs4                40960  2
i915                 1245184  4
i2c_algo_bit           16384  1 i915
drm_kms_helper        147456  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
psmouse               122880  0
drm                   311296  6 i915,drm_kms_helper
jme                    36864  0
sdhci_pci              24576  0
sdhci                  45056  1 sdhci_pci
pata_acpi              16384  0
mii                    16384  1 jme
fjes                   28672  0
video                  36864  2 sony_laptop,i915



```[COLOR=#000000]
[/COLOR]

---

### Post by wildmanne39 on 2017-02-16
Please post the output of:
```
cat /etc/resolv.conf
cat /etc/network/interfaces
modinfo rt2800pci
```
Thanks

---

### Post by pelai on 2017-02-16
cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.0.254
```

cat /etc/network/interfaces
```
# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto wlp1s0
iface wlp1s0 inet dhcp
	wpa-ssid InTheGhetto
	wpa-psk  *************
```

modinfo rt2800pci
```
filename:       /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.kolicense:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     4D2CAAE95D28B3DF4F72A52
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Bsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005360sv*sd*bc*sc*i*
alias:          pci:v00001814d0000359Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.8.0-22-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
```

Thanks!

---

### Post by wildmanne39 on 2017-02-16
Please do:
```
echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
Then:
```
sudo dpkg-reconfigure resolvconf
```
then answer 'Yes' to the "Prepare /etc/resolv.conf for dynamic updates?" question and 'No' to the one about temporarily appending your existing config to the dynamic one, now reboot.

This file:
> source /etc/network/interfaces
should only have this in it unless you are not using network manager, which is easier to use:
```
auto lo
iface lo inet loopback 
```
You can see if network manager is running with the following command:
```
ps aux | egrep 'Network|wicd'
```

---

### Post by pelai on 2017-02-16
I'm afraid there is no files in /etc/network/interfaces.d/*, however there is a file with similar content, /etc/network/interfaces. This is the actual content:

```

# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto wlp1s0
iface wlp1s0 inet dhcp
	wpa-ssid InTheGhetto
	wpa-psk  ***********

```

The result of ps aux | egrep 'Network|wicd':

```

$ ps aux | egrep 'Network|wicd'root       596  0.2  1.7  87052 17240 ?        Ssl  23:05   0:00 /usr/sbin/NetworkManager --no-daemon

pelai     1637  0.0  0.0   6372   856 pts/0    S+   23:10   0:00 grep -E --color=auto Network|wicd

```

Also there is a message appering at the up-right corner saying:

```

Network service discovery disabled

Your current network has a .local domain, which is not recommended and incompatible with the Avahi network service discovery. The service has been disabled.

```

---

### Post by wildmanne39 on 2017-02-16
Did you remove this:
```
# The primary network interface
auto wlp1s0
iface wlp1s0 inet dhcp
	wpa-ssid InTheGhetto
	wpa-psk  ***********
```
from the file if not please do so and if you have networks showing in the network manager icon remove them then reboot and let network manager find your networks, make sure that networking and wifi are enabled also.

The message you received can be safely ignored.

---

### Post by pelai on 2017-02-17
It worked!! At least for the wifi connection...! 

The wifi seems to work fine now, but the ethernet connection is still not working. There is the same message:

```

Ethernet Network
device not managed

```

Thank you!

---

### Post by praseodym on 2017-02-17
Please run:
```

sudo apt-get install ethtool
sudo ethtool enp2s0f5
dmesg | grep jme
```

---

### Post by wildmanne39 on 2017-02-17
Glad the wifi is working now and I will turn you over to praseodym for your ethernet connection.

---

### Post by pelai on 2017-02-18
Hi praseodym,

I've tried what you said but this is the result of the first command:

```

$ sudo apt-get install ethtool
[sudo] password for pelai: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ethtool is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'ethtool' has no installation candidate

```

---

### Post by pelai on 2017-02-23
I still haven't found the solution, anyone have any clue?

---

### Post by wildmanne39 on 2017-02-23
You will have better luck marking this thread solved for the wireless issue, and starting a new one just for the ethernet connection, there is only supposed to be one issue per thread and this is one of the reasons you get better support having separate threads.

I will change the title to reflect the wireless issue so searches can find the solution easier.
Thanks

---

### Post by pelai on 2017-02-23
Ok, thanks! I will create a new thread then.

---

