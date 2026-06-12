---
title: "Install of TEW-664UB V 2.0 on 14.04.01 32-bit"
date: 2014-12-04
forum: Networking &amp; Wireless
---

### Post by MacDee on 2014-12-04
Looking to Install TEW-664UB V 2.0 on 14.04.01 32-bit on a Dell OptiPlex GX620. I read this uses rtl8192du so I have tried CHili555 suggestion of

```
sudo rm -rf  rtl8192du
wget https://github.com/lwfinger/rtl8192du/archive/kernel-version.zip
unzip kernel-version.zip
cd rtl8192du-kernel-version
make
sudo make install
sudo modprobe 8192du
```

but I end up with this
```
allan@allan-OptiPlex-GX620:~/rtl8192du-kernel-version$ sudo make install
install -d /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/
install -m644 8192du.ko  /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/
install: cannot stat ‘8192du.ko’: No such file or directory
make: *** [install] Error 1
```

Just did a new install of 14.04 on a new hard drive and got Zoneminder working again. Now trying to get my usb wireless working again.

Any help would be appreciated.

---

### Post by MacDee on 2014-12-05
Since my post was moved from New to Ubuntu to Networking and Wireless I followed the instructions on the sticky for this thread and here is the txt file from my machine after update.

```

########## wireless info START ##########

Report from: 05 Dec 2014 08:24 EST -0500

Booted last: 05 Dec 2014 08:21 EST -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:56:26 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
    Subsystem: Dell OptiPlex GX620 [1028:01ad]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 001 Device 005: ID 20f4:664b TRENDnet 
Bus 001 Device 004: ID 0bc2:5071 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 413c:2107 Dell Computer Corp. 
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.16  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:feb9:c3d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46774 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69417369 (69.4 MB)  TX bytes:1777105 (1.7 MB)
          Interrupt:16 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.16
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             71.243.0.12

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

Region: America/New_York (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp

##### modprobe options ##################

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
# PCI device 0x14e4:0x1677 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   14.856207] intel_rng: don't want to disable this in firmware setup, and if

########## wireless info END ############
```

Any help with getting the wireless up and running would be appreciated.

---

### Post by MacDee on 2014-12-06
So I have also tried this zip file thing ([https://github.com/lwfinger/rtl8192d...ive/master.zip]("https://github.com/lwfinger/rtl8192du/archive/master.zip")) that seemed to make and install without error but still nothing. Still no wireless extentions shown with iwconfig. I've looked at previous posts and I think I've tried them all. Seemy  previous posts.

Am I missing something obvious? Although I enjoy playing around with Linux I have to admit I'm usually way over my head.

As alway any help would be appreciated.

---

### Post by chili555 on 2014-12-06
Let's have a peek at:```
sudo modprobe 8192du
modinfo 8192du | grep 664B
dmesg | grep 8192
```Thanks.

---

### Post by MacDee on 2014-12-06
Here's what i get
```
allan@allan-OptiPlex-GX620:~$ sudo modprobe 8192du
[sudo] password for allan: 
modprobe: FATAL: Module 8192du not found.
allan@allan-OptiPlex-GX620:~$ modinfo 8192du | grep 664B
modinfo: ERROR: Module 8192du not found.
allan@allan-OptiPlex-GX620:~$ dmesg | grep 8192
[    0.004167] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004172] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.169218] PM: Registering ACPI NVS region [mem 0x3f686c00-0x3f688bff] (8192 bytes)
[    0.553812] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.553836] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.553873] TCP: Hash tables configured (established 8192 bind 8192)
[    1.350038] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
allan@allan-OptiPlex-GX620:~$ 


```

---

### Post by chili555 on 2014-12-06
> modprobe: FATAL: Module 8192du not found.That strongly suggests that the make, sudo make install, sudo modprobe 8192du steps did not go properly. Please try again and let me know if you see an error, warning or other signs of distress.

---

### Post by MacDee on 2014-12-06
do I need to clean out my directory first? Then do then get the kernel-version zip again or the master.zip? my directory right now looks like this.

```
allan@allan-OptiPlex-GX620:~$ cd /home/allan
allan@allan-OptiPlex-GX620:~$ ls
Desktop             Music                     Templates
Documents           Pictures                  usb
Downloads           Public                    Videos
examples.desktop    rtl8192du-kernel-version  wireless-info.txt
kernel-version.zip  rtl8192du-master          wireless_script
allan@allan-OptiPlex-GX620:~$ 

```

---

### Post by chili555 on 2014-12-06
Above you said master compiled successfully. Therefor,  I suggest:```
cd ~/rtl8192du-master
make clean
make
sudo make install
sudo modprobe 8192du
```Watch for errors, etc. Warnings are probably OK.

---

### Post by MacDee on 2014-12-06
Seems I got an error finding a directory.
```
allan@allan-OptiPlex-GX620:~$ cd ~/rtl8192du-master
allan@allan-OptiPlex-GX620:~/rtl8192du-master$ make clean
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
allan@allan-OptiPlex-GX620:~/rtl8192du-master$ sudo make install
[sudo] password for allan: 
install -d /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/
install -m644 8192du.ko  /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/
install: cannot stat ‘8192du.ko’: No such file or directory
make: *** [install] Error 1
allan@allan-OptiPlex-GX620:~/rtl8192du-master$ sudo modprobe 8192du
modprobe: FATAL: Module 8192du not found.
allan@allan-OptiPlex-GX620:~/rtl8192du-master$ 


```

---

### Post by chili555 on 2014-12-06
Yes, because you missed a step. Please try again:```
cd ~/rtl8192du-master
make clean
[COLOR="#FF0000"]make[/COLOR]
sudo make install
sudo modprobe 8192du
```

---

### Post by MacDee on 2014-12-06
I guess that's what happens when you are a hunt and peek typer like me. So this time it seemed to compile clean with a couple of warnings. But still Module 8192du not found.

```
allan@allan-OptiPlex-GX620:~/rtl8192du-master$ cd ~/rtl8192du-master
allan@allan-OptiPlex-GX620:~/rtl8192du-master$ make clean
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
allan@allan-OptiPlex-GX620:~/rtl8192du-master$ make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.13.0-40-generic/build M=/home/allan/rtl8192du-master  modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-40-generic'
  CC [M]  /home/allan/rtl8192du-master/core/rtw_cmd.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_security.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_debug.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_io.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_ioctl_set.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_ieee80211.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_mlme.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_mlme_ext.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_wlan_util.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_pwrctrl.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_rf.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_recv.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_sta_mgt.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_ap.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_xmit.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_p2p.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_sreset.o
  CC [M]  /home/allan/rtl8192du-master/core/rtw_efuse.o
  CC [M]  /home/allan/rtl8192du-master/hal/hal_intf.o
  CC [M]  /home/allan/rtl8192du-master/hal/hal_com.o
  CC [M]  /home/allan/rtl8192du-master/hal/rtl8192d_hal_init.o
  CC [M]  /home/allan/rtl8192du-master/hal/rtl8192d_phycfg.o
  CC [M]  /home/allan/rtl8192du-master/hal/rtl8192d_rf6052.o
  CC [M]  /home/allan/rtl8192du-master/hal/rtl8192d_dm.o
  CC [M]  /home/allan/rtl8192du-master/hal/rtl8192d_rxdesc.o
  CC [M]  /home/allan/rtl8192du-master/hal/rtl8192d_cmd.o
  CC [M]  /home/allan/rtl8192du-master/hal/usb_halinit.o
  CC [M]  /home/allan/rtl8192du-master/hal/rtl8192du_led.o
  CC [M]  /home/allan/rtl8192du-master/hal/rtl8192du_xmit.o
  CC [M]  /home/allan/rtl8192du-master/hal/rtl8192du_recv.o
  CC [M]  /home/allan/rtl8192du-master/hal/hal8192duhwimg.o
  CC [M]  /home/allan/rtl8192du-master/hal/usb_ops_linux.o
  CC [M]  /home/allan/rtl8192du-master/hal/rtl8192d_xmit.o
  CC [M]  /home/allan/rtl8192du-master/os_dep/osdep_service.o
  CC [M]  /home/allan/rtl8192du-master/os_dep/os_intfs.o
/home/allan/rtl8192du-master/os_dep/os_intfs.c:874:2: warning: initialization from incompatible pointer type [enabled by default]
  .ndo_select_queue = rtw_select_queue,
  ^
/home/allan/rtl8192du-master/os_dep/os_intfs.c:874:2: warning: (near initialization for ‘rtw_netdev_ops.ndo_select_queue’) [enabled by default]
  CC [M]  /home/allan/rtl8192du-master/os_dep/usb_intf.o
  CC [M]  /home/allan/rtl8192du-master/os_dep/usb_ops_linux.o
  CC [M]  /home/allan/rtl8192du-master/os_dep/ioctl_linux.o
  CC [M]  /home/allan/rtl8192du-master/os_dep/xmit_linux.o
  CC [M]  /home/allan/rtl8192du-master/os_dep/mlme_linux.o
  CC [M]  /home/allan/rtl8192du-master/os_dep/recv_linux.o
  CC [M]  /home/allan/rtl8192du-master/os_dep/ioctl_cfg80211.o
  CC [M]  /home/allan/rtl8192du-master/os_dep/rtw_android.o
  LD [M]  /home/allan/rtl8192du-master/8192du.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/allan/rtl8192du-master/8192du.mod.o
  LD [M]  /home/allan/rtl8192du-master/8192du.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-40-generic'
allan@allan-OptiPlex-GX620:~/rtl8192du-master$ sudo make install
install -d /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/
install -m644 8192du.ko  /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/
install -d /lib/firmware/rtlwifi
install -m644 rtl8192dufw.bin /lib/firmware/rtlwifi
install -m644 rtl8192dufw_wol.bin /lib/firmware/rtlwifi
allan@allan-OptiPlex-GX620:~/rtl8192du-master$ sudo modprobe 8192du
modprobe: FATAL: Module 8192du not found.
allan@allan-OptiPlex-GX620:~/rtl8192du-master$ 

```

---

### Post by chili555 on 2014-12-06
Please try:```
sudo depmod -a
sudo modprobe 8192du
```If it is still not found, see if it's installed as expected:```
ls /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/ | grep 8192du
```And try to load it explicitly:```
sudo modprobe /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/8192du.ko
```

By the way, you can simply copy and paste these commands.

---

### Post by MacDee on 2014-12-06
Ok the depmod seems to have found it. so I ran the dmesg and iwconfig and I'm getting something now . Now I need to digest where I am and see if it can talk to my wireless router. 

Thanks for all your help.


```
allan@allan-OptiPlex-GX620:~/rtl8192du-master$ sudo depmod -a
allan@allan-OptiPlex-GX620:~/rtl8192du-master$ sudo modprobe 8192du
allan@allan-OptiPlex-GX620:~/rtl8192du-master$ dmesg | grep -e wlan -e 8192[    0.004168] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004173] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.165219] PM: Registering ACPI NVS region [mem 0x3f686c00-0x3f688bff] (8192 bytes)
[    0.553789] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.553814] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.553850] TCP: Hash tables configured (established 8192 bind 8192)
[    1.349701] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[ 2232.512474] 8192du: module verification failed: signature and/or  required key missing - tainting kernel
[ 2232.515439] r8192du: EEPROM type is E-FUSE, E-CUT chip
[ 2232.747936] r8192du: MacPhyMode: SINGLEMAC_SINGLEPHY
[ 2232.749329] usbcore: registered new interface driver rtl8192du
[ 2233.954940] r8192du: MacPhyMode: SINGLEMAC_SINGLEPHY
[ 2235.488467] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2235.489255] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2259.005310] r8192du: MacPhyMode: SINGLEMAC_SINGLEPHY
allan@allan-OptiPlex-GX620:~/rtl8192du-master$ iwconfig
wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

allan@allan-OptiPlex-GX620:~/rtl8192du-master$ 


```

---

### Post by chili555 on 2014-12-06
Looks like a success. Please detach the ethernet and run:```
sudo iwlist wlan0 scan
```Does it scan and see networks? You don't have to post them all, just tell us if you see yours and, if not, what is the error or message.

If it scans, click the Network Manager icon and connect.

---

### Post by MacDee on 2014-12-06
Yes it scanned my network and I was able to connect wirelessly.

Thank you again for all of the help.

---

### Post by chili555 on 2014-12-06
Glad it's working!

You have compiled the driver for the kernel version that was running when you compiled. When a later kernel version is installed, typically by Update Manager, you must re-compile after rebooting into the later kernel.

```
cd ~/rtl8192du-master
make clean
make
sudo make install
sudo depmod -a
sudo modprobe 8192du
```Have fun!

---

### Post by MacDee on 2014-12-06
The wireless on my ubuntu machine will be used for talking with an intranet in the woods of Vermont without internet. So there shouldn't be updates up there unless absolutely necessary and the Zoneminder I run on it also doesn't like updates. But I will keep the recompile with depmod in mind if I do updates.

Thanks

---

