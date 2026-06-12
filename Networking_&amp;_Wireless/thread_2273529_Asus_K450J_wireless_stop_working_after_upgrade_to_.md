---
title: "Asus K450J wireless stop working after upgrade to kernel 4.0"
date: 2015-04-13
forum: Networking &amp; Wireless
---

### Post by pr16 on 2015-04-13
Hi everyone,

Today I decided to upgrade to linux kernel 4.0, because I was facing some problems with hardware (touchpad, bluetooth and more a less wifi).
Before the upgrade, my wifi was working after following [this steps]("http://ubuntuforums.org/showthread.php?t=2201597"). After the kernel upgrade I was so happy because my touchpad and bluetooth were finally working properly when I realised my wifi card stoped working. 
I've already reinstalled ubuntu to see if it needed the previous configurations but the problem presists. I've redone the steps of that link and still the same. Does anyone knows how can I fix it please?

Thanks in advance ;)

---

### Post by wildmanne39 on 2015-04-13
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by pr16 on 2015-04-14
Sorry, I'm new in the forum and I haven't seen that. 
I ran the script and found out that I've a Brodcom network controller. I've already followed the steps from [here]("http://ubuntuforums.org/showthread.php?t=2214110") and the problem persists. In other words, I uninstalled the bcmwl-kernel-source package and installed thefirmware-b43-installer package. Rebooted and I still have the problem. 

The  wireless Script output is here:
```
 

########## wireless info START ##########

Report from: 14 Apr 2015 18:31 WEST +0100

Booted last: 14 Apr 2015 18:28 WEST +0100

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.0.0-040000-generic #201504121935 SMP Sun Apr 12 23:36:33 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME

##### lspci #############################

03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6605]

04:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: alx

##### lsusb #############################

Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 13d3:5188 IMC Networks 
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 006: ID 04ca:2006 Lite-On Technology Corp. 
Bus 001 Device 004: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

asus_nb_wmi            24576  0 
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  1 nouveau
wmi                    20480  3 mxm_wmi,nouveau,asus_wmi
video                  28672  3 i915,nouveau,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::12c3:7bff:fe55:b62d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:934458 (934.4 KB)  TX bytes:210874 (210.8 KB)
          Interrupt:19 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

Region: Europe/Lisbon (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

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
blacklist acer_wmi

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x10a1 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   11.898017] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-04ca-2006.hcd failed with error -2
[   11.898022] Bluetooth: hci0: BCM: patch brcm/BCM43142A0-04ca-2006.hcd not found

########## wireless info END ############


```
Thanks

---

### Post by wildmanne39 on 2015-04-14
Please do:
```
sudo apt-get install bcmwl-kernel-source
```
Reboot

---

### Post by pr16 on 2015-04-14
I did that, but I found out that kernel 4.0 isn't supported yet :s I got this on the terminal:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1512 kB of archives.
After this operation, 8038 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 236935 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.1_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.1) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.1) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 4.0.0-040000-generic
Building for architecture x86_64
Building initial module for 4.0.0-040000-generic
ERROR (dkms apport): kernel package linux-headers-4.0.0-040000-generic is not supported
Error! Bad return status for module build on kernel: 4.0.0-040000-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log for more information.
modprobe: FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-4.0.0-040000-generic

```

Is there any chance that kernel 4 will be supported?
Thanks

P.S. (Edit)
And here is the log file:
```

DKMS make.log for bcmwl-6.30.223.248+bdcom for kernel 4.0.0-040000-generic (x86_64)
Ter Abr 14 22:20:01 WEST 2015
make: Entering directory `/usr/src/linux-headers-4.0.0-040000-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/wl/sys/wl_linux.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.o
/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c: In function &#8216;wl_cfg80211_get_key&#8217;:
/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:1390:2: warning: passing argument 1 of &#8216;memcpy&#8217; discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
  memcpy(params.key, key.data, params.key_len);
  ^
In file included from ./arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from ./arch/x86/include/asm/cpumask.h:4,
                 from ./arch/x86/include/asm/msr.h:10,
                 from ./arch/x86/include/asm/processor.h:20,
                 from ./arch/x86/include/asm/thread_info.h:23,
                 from include/linux/thread_info.h:54,
                 from ./arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/include/linuxver.h:40,
                 from /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:26:
./arch/x86/include/asm/string_64.h:34:14: note: expected &#8216;void *&#8217; but argument is of type &#8216;const u8 *&#8217;
 extern void *memcpy(void *to, const void *from, size_t len);
              ^
/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c: In function &#8216;wl_cfg80211_get_station&#8217;:
/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:1444:20: error: &#8216;STATION_INFO_TX_BITRATE&#8217; undeclared (first use in this function)
   sinfo->filled |= STATION_INFO_TX_BITRATE;
                    ^
/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:1444:20: note: each undeclared identifier is reported only once for each function it appears in
/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:1457:20: error: &#8216;STATION_INFO_SIGNAL&#8217; undeclared (first use in this function)
   sinfo->filled |= STATION_INFO_SIGNAL;
                    ^
/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c: At top level:
/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:1778:2: warning: initialization from incompatible pointer type [enabled by default]
  .get_station = wl_cfg80211_get_station,
  ^
/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:1778:2: warning: (near initialization for &#8216;wl_cfg80211_ops.get_station&#8217;) [enabled by default]
cc1: warning: unrecognized command line option "-Wno-date-time" [enabled by default]
make[1]: *** [/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-4.0.0-040000-generic'

```

---

### Post by jeremy31 on 2015-04-15
The following should get bluetooth working.  Is your Asus one of them that the touchpad was detected as a PS2 mouse?  You can check [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1372609](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1372609) and see if one of Pilot6 patched kernels will work as I think he did a patched 3.16 and 3.19 kernel.  I know bcmwl-kernel-source will work in 3.16

```
wget https://www.dropbox.com/s/ojwv0u81as5ikhf/BCM43142A0-04ca-2006.hcd
```
```
sudo cp BCM43142A0-04ca-2006.hcd /lib/firmware/brcm/
```
```
sudo modprobe -r btusb
```
```
sudo modprobe btusb
```

---

### Post by pr16 on 2015-04-15
Thanks, that worked for mu bluetooth in kernel 3.16. And yes, my touchpad is the one that is detected as a PS2 mouse. I clicked the link but just can't find out how to install (I'm a noob, I know xD). But I have a wireless USB card and I got wifi working in kernel 4.0 with it. Do you think that broadcom will support kernel 4.0 or its better to downgrade to kernel 3.16 or 3.19?
Thanks

---

### Post by jeremy31 on 2015-04-15
There is a patched version of bcmwl-kernel-source available that appears to work with kernel 4.0
[https://github.com/longsleep/bcmwl-ubuntu](https://github.com/longsleep/bcmwl-ubuntu)

---

### Post by pr16 on 2015-04-15
Can you tell me how to compile and install, please?

---

### Post by jeremy31 on 2015-04-15
Still working on getting it to compile, had to wait to get into kernel.ubuntu.com to get the 4.0 kernel.

Eventually bcmwl-kernel-source will be released to work on kernel 4.0 and your touchpad will be working on Ubuntu kernel 3.13 or 3.16

Installing this might work [http://ppa.launchpad.net/hanipouspilot/focaltech-dkms/ubuntu/pool/main/f/focaltech-dkms/focaltech-dkms_1.1_all.deb](http://ppa.launchpad.net/hanipouspilot/focaltech-dkms/ubuntu/pool/main/f/focaltech-dkms/focaltech-dkms_1.1_all.deb) in 3.13 or 3.16

---

### Post by pr16 on 2015-04-16
ok, thanks. Nop, unfortunatly this touchpad drivers don't work on kernel 3.16.0-30-generic :(

---

### Post by pr16 on 2015-04-16
Thanks to you all. That touchpad drivers works in kernel 3.19 (I installed ubuntu 15.04). Then installing broadcom drivers (which also works in kernel 3.19) and after running ```
 echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf 
``` I could manage to get wi-fi working. Bluetooth was already working in this kernel :)

---

