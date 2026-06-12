---
title: "D-link N150 DWA-123 USB Adapter/Ubuntu 13.10/PC"
date: 2014-02-08
forum: Networking &amp; Wireless
---

### Post by john_smith8 on 2014-02-08
My wifi adapter is D-Link N150 DWA-123 (H/W ver. D1 | F/W ver. 4.00), and only DWA-122/125 model is listed here [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB)

this is the result after I run the wireless code

I'm still new to linux can someone point me the right direction ?

Thanks a lot

```


*************** info trace ***************

***** uname -a *****

Linux john-OEM 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Foxconn International, Inc. Device [105b:0df2]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 003: ID 2001:3310 D-Link Corp. 
Bus 001 Device 006: ID 8564:1000  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 10c4:8103 Cygnal Integrated Products, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

No way to aquire root rights found.

***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

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

***** modinfo *****


***** udev rules *****

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****


****************** done ******************


```

---

### Post by praseodym on 2014-02-08
Hi,

this is (so far) an unknown chipset. Please check
```

usb-devices
```for more info. We may need to add the device ID to a common driver. Does LAN work?

---

### Post by john_smith8 on 2014-02-08
> **praseodym said:**
> Hi,

this is (so far) an unknown chipset. Please check
```

usb-devices
```for more info. We may need to add the device ID to a common driver. Does LAN work?

I havn't try, I don't have an Ethernet line available, only wifi

is there anyway to enable rt2800usb thing ? I look around and it seem like that's a packet include the RALINK N150 DWA-123 rev.A1. Mine is rev.D1 though

---

### Post by praseodym on 2014-02-08
Please show the output, then we'll see...

---

### Post by john_smith8 on 2014-02-08
Err... what code to put in the terminal, sr I'm don't really know what to do

---

### Post by praseodym on 2014-02-08
```
usb-devices
```
This should show more info about your device

---

### Post by john_smith8 on 2014-02-08
> **praseodym said:**
> ```
usb-devices
``` This should show more info about your device     ```
 
T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=01 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=2001 ProdID=3310 Rev=00.00
S:  Manufacturer=Realtek
S:  Product=DWA-123 11n Adapter
S:  SerialNumber=78542E2244BE
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

 
```

---

### Post by praseodym on 2014-02-08
Ok, lets try this driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.8
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
echo 'install 8192cu modprobe --ignore-install 8192cu ; /bin/echo "2001 3310" > /sys/bus/usb/drivers/rtl8192cu/new_id' | sudo tee /etc/modprobe.d/8192cu.conf
```
Reboot and check
```

iwconfig
lsmod
dmesg | grep 8192
ifconfig -a
cat /etc/resolv.conf
iwlist chan
```

---

### Post by john_smith8 on 2014-02-08
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
```

give me 

```

E: Unable to locate package build-essential
E: Unable to locate package dkms
E: Unable to locate package git

```

I somehow using my android phone to tethe to internet, any packet I can get ?

---

### Post by praseodym on 2014-02-08
Open the update-manager-> Settings and activate the repositories main, restricted, universe, multiverse, close it and
```

sudo apt-get update
```Then try it again.

---

### Post by john_smith8 on 2014-02-08
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.


```

lsmod
```
Module                  Size  Used by
rndis_wlan             44355  0 
rndis_host             14087  1 rndis_wlan
cdc_ether              13967  1 rndis_host
usbnet                 37607  3 rndis_host,rndis_wlan,cdc_ether
cfg80211              401762  1 rndis_wlan
cdc_acm                27922  0 
usb_storage            48294  0 
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18959  2 
rfcomm                 53664  0 
bluetooth             323656  10 bnep,rfcomm
coretemp               13195  0 
snd_hda_codec_realtek    45592  1 
kvm                   368949  0 
snd_hda_intel          42658  3 
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
ext2                   67224  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
lpc_ich                16864  0 
microcode              18830  0 
serio_raw              13189  0 
lp                     13299  0 
mac_hid                13037  0 
parport                40795  3 lp,ppdev,parport_pc
xts                    12749  1 
gf128mul               14503  1 xts
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
dm_crypt               22316  2 
i915                  594380  3 
video                  18777  1 i915
r8169                  61562  0 
floppy                 55378  0 
i2c_algo_bit           13197  1 i915
drm_kms_helper         46867  1 i915
drm                   242400  4 i915,drm_kms_helper
mii                    13654  2 r8169,usbnet
```



dmesg | grep 8192```
[    0.165622] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.165659] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.165692] TCP: Hash tables configured (established 8192 bind 8192)
[    0.690217] agpgart-intel 0000:00:00.0: detected 8192K stolen memory


```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 90:fb:a6:36:7b:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27444 (27.4 KB)  TX bytes:27444 (27.4 KB)

usb0      Link encap:Ethernet  HWaddr f2:0d:a9:a5:2a:74  
          inet addr:192.168.42.99  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::f00d:a9ff:fea5:2a74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:130150 (130.1 KB)  TX bytes:121257 (121.2 KB)
```

cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


```


iwlist chan
```
lo        no frequency information.

eth0      no frequency information.

usb0      no frequency information.


```

---

### Post by praseodym on 2014-02-08
Lets check
```

sudo modprobe -v 8192cu
dmesg | grep 8192
iwconfig
```
Is there a driver CD? If yes, what is the name of the Windows driver? Or is there even a Linux driver on it?

---

### Post by john_smith8 on 2014-02-08
sudo modprobe -v 8192cu
```
install modprobe --ignore-install 8192cu ; /bin/echo "2001 3310" > /sys/bus/usb/drivers/rtl8192cu/new_id 
libkmod: ERROR ../libkmod/libkmod-module.c:791 kmod_module_insert_module: could not find module by name='8192cu'
ERROR: could not insert '8192cu': Function not implemented
sh: 1: cannot create /sys/bus/usb/drivers/rtl8192cu/new_id: Directory nonexistent
libkmod: ERROR ../libkmod/libkmod-module.c:925 command_do: Error running install command for 8192cu
ERROR: could not insert '8192cu': Unknown symbol in module, or unknown parameter (see dmesg)


```


dmesg | grep 8192
```
[    0.165622] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.165659] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.165692] TCP: Hash tables configured (established 8192 bind 8192)
[    0.690217] agpgart-intel 0000:00:00.0: detected 8192K stolen memory


```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.


```

I have a windows driver CD, no Linux thoug

---

### Post by john_smith8 on 2014-02-08
sudo modprobe -v 8192cu
```
install modprobe --ignore-install 8192cu ; /bin/echo "2001 3310" > /sys/bus/usb/drivers/rtl8192cu/new_id 
libkmod: ERROR ../libkmod/libkmod-module.c:791 kmod_module_insert_module: could not find module by name='8192cu'
ERROR: could not insert '8192cu': Function not implemented
sh: 1: cannot create /sys/bus/usb/drivers/rtl8192cu/new_id: Directory nonexistent
libkmod: ERROR ../libkmod/libkmod-module.c:925 command_do: Error running install command for 8192cu
ERROR: could not insert '8192cu': Unknown symbol in module, or unknown parameter (see dmesg)


```


dmesg | grep 8192
```
[    0.165622] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.165659] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.165692] TCP: Hash tables configured (established 8192 bind 8192)
[    0.690217] agpgart-intel 0000:00:00.0: detected 8192K stolen memory


```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.


```

I have a windows driver CD, no Linux thoug

[http://ubuntuone.com/6jBAQwylCIMOdFwbYfhpE0](http://ubuntuone.com/6jBAQwylCIMOdFwbYfhpE0)

---

### Post by praseodym on 2014-02-08
Ok, obviously, the driver wasnt installed. Try the native one instead:
```

echo 'install rtl8192cu modprobe --ignore-install rtl8192cu ; /bin/echo "2001 3310" > /sys/bus/usb/drivers/rtl8192cu/new_id' | sudo tee /etc/modprobe.d/8192cu.conf
sudo modprobe -v rtl8192cu
dmesg | grep 8192
iwconfig
```
One of the config files reads rtl8192cu, but also sth. with rtl8188etr or so

---

### Post by john_smith8 on 2014-02-08
```
[    0.165622] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.165659] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.165692] TCP: Hash tables configured (established 8192 bind 8192)
[    0.690217] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[ 5887.956977] usbcore: registered new interface driver rtl8192cu
[ 5888.003389] rtl8192cu: Chip version 0x10
[ 5888.006882] rtl8192cu: MAC address: ff:ff:ff:ff:ff:ff
[ 5888.006888] rtl8192cu: Board Type 7


```

I'll restart and check again

---

### Post by john_smith8 on 2014-02-08
still no wifi

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.


```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 90:fb:a6:36:7b:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54205 (54.2 KB)  TX bytes:54205 (54.2 KB)

usb0      Link encap:Ethernet  HWaddr 3e:92:f3:dc:b6:e8  
          inet addr:192.168.42.192  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::3c92:f3ff:fedc:b6e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5631 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6769914 (6.7 MB)  TX bytes:847833 (847.8 KB)


```

---

### Post by praseodym on 2014-02-08
Nope, obviously, its not working. What interface is "usb0"? Are you connected via phone?

Ok, Google is your friend:

[http://askubuntu.com/questions/371300/how-do-i-get-a-usb-wi-fi-d-link-dwa-125-rev-d1-rtl8188etv-working](http://askubuntu.com/questions/371300/how-do-i-get-a-usb-wi-fi-d-link-dwa-125-rev-d1-rtl8188etv-working)

Its the "8188eu" driver:

Download this file and unpack it in "Downloads":

[https://dl.dropboxusercontent.com/u/2902662/rtl8188eu.tar.gz](https://dl.dropboxusercontent.com/u/2902662/rtl8188eu.tar.gz)

Installation:
```

cd ~/Downloads/rtl8188eu/
make
sudo make install
sudo cp rtl8188eufw.bin /lib/firmware
```
Reboot.

For those having an internet connection:
```

sudo apt-get install git
git clone https://github.com/lwfinger/rtl8188eu
cd rtl8188eu
make
sudo make install
sudo cp rtl8188eufw.bin /lib/firmware
```

---

### Post by john_smith8 on 2014-02-08
nm-tool (usb0 is my HTC phone)
```
- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        0E:BD:D9:1B:B1:77

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.47
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        90:FB:A6:36:7B:C9

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

---

### Post by praseodym on 2014-02-08
Tried that driver?

---

### Post by john_smith8 on 2014-02-08
tried and still no change

---

### Post by praseodym on 2014-02-08
Check
```

dmesg | grep rtl8
iwconfig
lsmod
cat /etc/resolv.conf
```

---

### Post by john_smith8 on 2014-02-08
```
[  664.368890] usbcore: registered new interface driver rtl8192cu
[  664.387902] rtl8192cu: Chip version 0x10
[  664.391513] rtl8192cu: MAC address: ff:ff:ff:ff:ff:ff
[  664.391518] rtl8192cu: Board Type 7


```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.


```

lsmod
```
Module                  Size  Used by
btrfs                 813281  0 
raid6_pq               97455  1 btrfs
zlib_deflate           26445  1 btrfs
xor                    26221  1 btrfs
ufs                    73658  0 
qnx4                   13101  0 
hfsplus                92933  0 
hfs                    49390  0 
minix                  31317  0 
ntfs                   95723  0 
msdos                  17093  0 
jfs                   169886  0 
xfs                   788606  0 
libcrc32c              12543  2 xfs,btrfs
reiserfs              225146  0 
parport_pc             31981  0 
ppdev                  17391  0 
rfcomm                 53664  0 
bnep                   18959  2 
bluetooth             323656  10 bnep,rfcomm
binfmt_misc            13140  1 
ext2                   67224  1 
coretemp               13195  0 
kvm_intel             128218  0 
rndis_wlan             44355  0 
kvm                   368949  1 kvm_intel
rndis_host             14087  1 rndis_wlan
cdc_ether              13967  1 rndis_host
usbnet                 37607  3 rndis_host,rndis_wlan,cdc_ether
cfg80211              401762  1 rndis_wlan
cdc_acm                27922  0 
snd_hda_codec_realtek    45592  1 
snd_hda_intel          42658  3 
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
microcode              18830  0 
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
serio_raw              13189  0 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
lpc_ich                16864  0 
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
xts                    12749  1 
gf128mul               14503  1 xts
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
dm_crypt               22316  2 
usb_storage            48294  0 
i915                  594380  3 
floppy                 55378  0 
r8169                  61562  0 
video                  18777  1 i915
i2c_algo_bit           13197  1 i915
drm_kms_helper         46867  1 i915
mii                    13654  2 r8169,usbnet
drm                   242400  4 i915,drm_kms_helper
```

cat /etc/resolv.conf
```

nameserver 127.0.1.1


```

---

### Post by praseodym on 2014-02-08
Sorry, I forgot something. Redownload the driver and try it again.

See answer #1 there. Driver file adjusted.

---

### Post by john_smith8 on 2014-02-08
followed instruction at #8 of this thread

but when I run 
git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
```
fatal: destination path 'rtl8192cu-fixes' already exists and is not an empty directory.


```

iwconfig
```
blacklist rtl8192cu

```

lsmod
```
Module                  Size  Used by
rndis_wlan             44355  0 
rndis_host             14087  1 rndis_wlan
cdc_ether              13967  1 rndis_host
usbnet                 37607  3 rndis_host,rndis_wlan,cdc_ether
cfg80211              401762  1 rndis_wlan
cdc_acm                27922  0 
usb_storage            48294  0 
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18959  2 
rfcomm                 53664  0 
bluetooth             323656  10 bnep,rfcomm
binfmt_misc            13140  1 
coretemp               13195  0 
kvm                   368949  0 
ext2                   67224  1 
snd_hda_codec_realtek    45592  1 
snd_hda_intel          42658  3 
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
microcode              18830  0 
serio_raw              13189  0 
lpc_ich                16864  0 
soundcore              12600  1 snd
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
xts                    12749  1 
gf128mul               14503  1 xts
dm_crypt               22316  2 
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
i915                  594380  3 
video                  18777  1 i915
r8169                  61562  0 
i2c_algo_bit           13197  1 i915
drm_kms_helper         46867  1 i915
floppy                 55378  0 
drm                   242400  4 i915,drm_kms_helper
mii                    13654  2 r8169,usbnet


```

dmesg | grep 8192
```
[    0.165617] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.165654] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.165686] TCP: Hash tables configured (established 8192 bind 8192)
[    0.690246] agpgart-intel 0000:00:00.0: detected 8192K stolen memory


```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 90:fb:a6:36:7b:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30773 (30.7 KB)  TX bytes:30773 (30.7 KB)

usb0      Link encap:Ethernet  HWaddr e2:ba:db:a2:66:1a  
          inet addr:192.168.42.84  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::e0ba:dbff:fea2:661a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62796 (62.7 KB)  TX bytes:95379 (95.3 KB)


```
cat /etc/resolv.conf
```
nameserver 127.0.1.1


```

iwlist chan
```
lo        no frequency information.

eth0      no frequency information.

usb0      no frequency information.


```

---

### Post by john_smith8 on 2014-02-09
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 90:fb:a6:36:7b:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8063 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:706164 (706.1 KB)  TX bytes:706164 (706.1 KB)

usb0      Link encap:Ethernet  HWaddr 22:ae:e2:36:23:01  
          inet addr:192.168.42.236  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::20ae:e2ff:fe36:2301/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53854 errors:6 dropped:0 overruns:0 frame:6
          TX packets:33134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66702122 (66.7 MB)  TX bytes:5292138 (5.2 MB)


```

iwconfif
```
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.


```

---

### Post by praseodym on 2014-02-09
Remove the old driver:

```
sudo rm -r /usr/src/8192cu-fixes
```
and remove the directory "rtl8192cu-fixes"

I meant this one:

[https://dl.dropboxusercontent.com/u/2902662/rtl8188eu.tar.gz](https://dl.dropboxusercontent.com/u/2902662/rtl8188eu.tar.gz)

---

### Post by john_smith8 on 2014-02-10
sudo dkms add ./rtl8192cu-fixes
```
Error! DKMS tree already contains: 8192cu-1.8
You cannot add the same module/version combo more than once.

```
lsmod

```
Module                  Size  Used by
rndis_wlan             44355  0 
rndis_host             14087  1 rndis_wlan
cdc_ether              13967  1 rndis_host
usbnet                 37607  3 rndis_host,rndis_wlan,cdc_ether
cfg80211              401762  1 rndis_wlan
usb_storage            48294  0 
cdc_acm                27922  2 
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18959  2 
rfcomm                 53664  0 
bluetooth             323656  10 bnep,rfcomm
binfmt_misc            13140  1 
ip6t_REJECT            12826  1 
coretemp               13195  0 
xt_hl                  12465  6 
ip6t_rt                13259  3 
kvm                   368949  0 
nf_conntrack_ipv6      18450  7 
nf_defrag_ipv6         26064  1 nf_conntrack_ipv6
ext2                   67224  1 
ipt_REJECT             12485  1 
xt_LOG                 17446  10 
xt_limit               12541  13 
xt_tcpudp              12756  18 
xt_addrtype            12563  4 
nf_conntrack_ipv4      14492  7 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_conntrack           12664  14 
ip6table_filter        12711  1 
ip6_tables             17819  1 ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12645  0 
nf_nat                 25588  1 nf_nat_ftp
nf_conntrack_ftp       14056  1 nf_nat_ftp
nf_conntrack           82913  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12706  1 
ip_tables              17987  1 iptable_filter
x_tables               22067  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
snd_hda_codec_realtek    45592  1 
snd_hda_intel          42658  3 
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
microcode              18830  0 
snd                    60790  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                16864  0 
serio_raw              13189  0 
mac_hid                13037  0 
soundcore              12600  1 snd
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
xts                    12749  1 
gf128mul               14503  1 xts
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
dm_crypt               22316  2 
i915                  594380  3 
floppy                 55378  0 
video                  18777  1 i915
r8169                  61562  0 
i2c_algo_bit           13197  1 i915
drm_kms_helper         46867  1 i915
drm                   242400  4 i915,drm_kms_helper
mii                    13654  2 r8169,usbnet


```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 90:fb:a6:36:7b:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48622 (48.6 KB)  TX bytes:48622 (48.6 KB)

usb0      Link encap:Ethernet  HWaddr 7e:97:e5:48:6d:8c  
          inet addr:192.168.42.127  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::7c97:e5ff:fe48:6d8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:195081 (195.0 KB)  TX bytes:104646 (104.6 KB)


```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.


```

---

### Post by praseodym on 2014-02-10
Uninstallation:
```

sudo dkms remove -m 8192cu -v 1.8
```

---

### Post by john_smith8 on 2014-02-10
reinstall Ubuntu

follow #8 of this thread step by step

result: no wifi

lsmod```
Module                  Size  Used by
nls_iso8859_1          12617  1 
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18959  2 
rfcomm                 53664  0 
bluetooth             323656  10 bnep,rfcomm
ext2                   67224  1 
coretemp               13195  0 
kvm_intel             128218  0 
kvm                   368949  1 kvm_intel
rndis_wlan             44355  0 
snd_hda_codec_realtek    45592  1 
rndis_host             14087  1 rndis_wlan
snd_hda_intel          42658  3 
cdc_ether              13967  1 rndis_host
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
usbnet                 37607  3 rndis_host,rndis_wlan,cdc_ether
cfg80211              401762  1 rndis_wlan
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
cdc_acm                27922  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
lpc_ich                16864  0 
microcode              18830  0 
serio_raw              13189  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
mac_hid                13037  0 
xts                    12749  1 
gf128mul               14503  1 xts
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
dm_crypt               22316  2 
usb_storage            48294  1 
i915                  594380  3 
r8169                  61562  0 
floppy                 55378  0 
video                  18777  1 i915
i2c_algo_bit           13197  1 i915
drm_kms_helper         46867  1 i915
drm                   242400  4 i915,drm_kms_helper
mii                    13654  2 r8169,usbnet


```

iwconfig```
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.


```

ifconfig```
eth0      Link encap:Ethernet  HWaddr 90:fb:a6:36:7b:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7407 (7.4 KB)  TX bytes:7407 (7.4 KB)

usb0      Link encap:Ethernet  HWaddr 36:68:95:60:f4:66  
          inet addr:192.168.42.125  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::3468:95ff:fe60:f466/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10781 (10.7 KB)  TX bytes:19609 (19.6 KB)


```

dmesg | grep 8192```
[    0.165628] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.165663] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.165695] TCP: Hash tables configured (established 8192 bind 8192)
[    0.686262] agpgart-intel 0000:00:00.0: detected 8192K stolen memory


```

lsusb```
Bus 001 Device 005: ID 2001:3310 D-Link Corp. 
Bus 001 Device 004: ID 8564:1000  
Bus 001 Device 002: ID 0bb4:0f60 HTC (High Tech Computer Corp.) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 10c4:8103 Cygnal Integrated Products, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
john@john-OEM:~$ 


```

---

### Post by praseodym on 2014-02-11
Nope, not #8, uninstall it again. I meant the 8188ee driver from #18

---

### Post by john_smith8 on 2014-02-12
> **praseodym said:**
> Nope, not #8, uninstall it again. I meant the 8188ee driver from #18

does not seem to work

```
john@john-OEM:~$ lsmod | grep 8188
8188eu                714014  0 
john@john-OEM:~$ lsmod | grep 2800
john@john-OEM:~$ lsmod | grep 8188
8188eu                714014  0 
john@john-OEM:~$ lsusb
Bus 001 Device 004: ID 2001:3310 D-Link Corp. 
Bus 001 Device 003: ID 8564:1000  
Bus 001 Device 008: ID 0bb4:0f60 HTC (High Tech Computer Corp.) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 10c4:8103 Cygnal Integrated Products, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
john@john-OEM:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 90:fb:a6:36:7b:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24058 (24.0 KB)  TX bytes:24058 (24.0 KB)

usb0      Link encap:Ethernet  HWaddr 72:69:60:b5:c2:44  
          inet addr:192.168.42.242  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::7069:60ff:feb5:c244/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1708 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2031621 (2.0 MB)  TX bytes:172921 (172.9 KB)

john@john-OEM:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.

john@john-OEM:~$ 


```

---

### Post by praseodym on 2014-02-13
Lets check
```

modprobe -c | grep -i "2001.*3310"
```

---

### Post by hemanth2 on 2014-02-21
Thanks .

---

### Post by hemanth2 on 2014-02-21
> **praseodym said:**
> Ok, lets try this driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.8
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
echo 'install 8192cu modprobe --ignore-install 8192cu ; /bin/echo "2001 3310" > /sys/bus/usb/drivers/rtl8192cu/new_id' | sudo tee /etc/modprobe.d/8192cu.conf
```
Reboot and check
```

iwconfig
lsmod
dmesg | grep 8192
ifconfig -a
cat /etc/resolv.conf
iwlist chan
```


[COLOR=#000000]Thanks .. This fixed my D--link DWA-123 adapter.[/COLOR][SIZE=4][COLOR=#000000] :grin::KS[/COLOR][/SIZE]

---

### Post by manishbhoola on 2014-03-31
An update after I upgraded to the latest 14.04 beta and inserted the D-Link N 150. Works straight out of the box, no configuration necessary. FYI please.

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 10 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=2001 ProdID=3310 Rev=00.00
S:  Manufacturer=Realtek
S:  Product=DWA-123 11n Adapter
S:  SerialNumber=D8FEE3568780
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=r8188eu

---

