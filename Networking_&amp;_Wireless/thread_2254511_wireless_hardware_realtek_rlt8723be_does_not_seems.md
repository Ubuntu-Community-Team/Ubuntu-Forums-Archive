---
title: "wireless hardware realtek rlt8723be does not seems to be there"
date: 2014-11-27
forum: Networking &amp; Wireless
---

### Post by bejo3 on 2014-11-27
hello ubuntu forum.  

on my new lenovo thinkpad e555 i installed elementary os. Being a linux newby I am not sure, but as far as i have understood, the e-os distribution is build on ubuntu. A lot of threads concerning my issue which I found by googling it, lead to posts in this forum, so i decided to post my issue here, too. hopefully i am at the right place and somebody can help me with this: 

my machine is supposed to have wifi. to be more exact it should be the hardware: realtek rlt8723be. i do not find any hint on how to use it. it is as if it is not there... 
I ran the wireless_script eith my ethernet internet connection and got this: 

```



########## wireless info START ##########


Report from: 27 Nov 2014 21:12 CET +0100


Booted last: 27 Nov 2014 20:26 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	elementary OS
Description:	elementary OS Luna
Release:	0.2.1
Codename:	luna


##### kernel ############################


Linux 3.2.0-72-generic #107-Ubuntu SMP Thu Nov 6 14:24:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Pantheon


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:5110]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b723]
	Subsystem: Lenovo Device [17aa:b736]


##### lsusb #############################


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 04f2:b444 Chicony Electronics Co., Ltd 
Bus 004 Device 002: ID 0bda:b728 Realtek Semiconductor Corp. 


##### PCMCIA card info ##################


##### rfkill ############################


0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


wmi                    19256  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.2.105  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2ad2:44ff:fedf:d1e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7647995 (7.6 MB)  TX bytes:687019 (687.0 KB)
          Interrupt:86 


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.0.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0  [Kabelnetzwerkverbindung 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.2.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1


    DNS:             192.168.2.1


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


##### iw reg get ########################


nl80211 not found.


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
rtc


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


[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b44
blacklist b43legacy
blacklist b43
blacklist brcm80211
blacklist brcmsmac
blacklist brcmfmac
blacklist ssb
blacklist bcma
blacklist bcm43xx


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:03.1/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[   12.642913] IBM TrackPoint firmware: 0x0e, buttons: 3/3


########## wireless info END ############



```

did lenovo forget to implement the hardware or is my machine missing a driver? There are a lot of reported problems concerning the realtek rlt8723be, but i did not manage to find a solution for my topic. 
i would be very happy to receive a good hint on what i should do? 
thanks in advance. 

best regards, Johannes.

---

### Post by chili555 on 2014-11-27
> Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b723]
	Subsystem: Lenovo Device [17aa:b736]
There it is and it lacks a driver. We know nothing about Elementary, but if you were running Ubuntu 12.04, roughly where 3.2.0-xx would be, we'd first suggest you upgrade to 14.04 where it would work from the start. 

If you won't upgrade, then consider this: [http://askubuntu.com/questions/389268/no-wifi-connection-on-ubuntu-13-10](http://askubuntu.com/questions/389268/no-wifi-connection-on-ubuntu-13-10)

---

### Post by bejo3 on 2014-11-27
Hi chili555. 
Thank you for the answer. 
I tryed to follow the steps of your given link. After I had received the files via git, make unfortunately did not work. The Makefile is missing. Either not all files were downloaded or this is due to my distribution. 

the created folder rtl8723be tells me to have the following content: 
```

drwxr-xr-x  3 bejo bejo 4096 Nov 28 00:46 ./
drwxr-xr-x 21 bejo bejo 4096 Nov 28 00:46 ../
drwxrwxr-x  8 bejo bejo 4096 Nov 28 00:46 .git/
-rw-rw-r--  1 bejo bejo 1092 Nov 28 00:46 .gitignore

```

Makefile missing? I do not even know, how a Makefile looks like... but according to my internet researches, I would assume, the file is missing. 
Do you see a way how this still could work out on my machine? 

Thanks again. Johannes.

---

### Post by chili555 on 2014-11-27
*Smacks forehead!*> This repo is obsolete. Use lwfinger/rtlwifi_new instead.Therefore, let's change the method to:```
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install
sudo modprobe rtl8723be
```I haven't easy access to a 3.2.0-xx install, so I have no idea if it 'makes' without error.

By the way, a Makefile appears like this:```
chili@T410:~/rtlwifi_new$ ls
base.c     debug.c         pci.h      regd.o     rtl_pci.ko     rtlwifi.o
base.h     debug.h         pci.o      rtl8188ee  rtl_pci.mod.c  stats.c
base.o     debug.o         ps.c       rtl8192c   rtl_pci.mod.o  stats.h
btcoexist  efuse.c         ps.h       rtl8192ce  rtl_pci.o      stats.o
cam.c      efuse.h         ps.o       rtl8192cu  rtl_usb.ko     usb.c
cam.h      efuse.o         rc.c       rtl8192de  rtl_usb.mod.c  usb.h
cam.o      firmware        rc.h       rtl8192ee  rtl_usb.mod.o  usb.o
compat.h   [COLOR="#FF0000"]Makefile [/COLOR]       rc.o       rtl8192se  rtl_usb.o      wifi.h
core.c     modules.order   README.md  rtl8723ae  rtlwifi.ko
core.h     Module.symvers  regd.c     rtl8723be  rtlwifi.mod.c
core.o     pci.c           regd.h     rtl8821ae  rtlwifi.mod.o

```As always, post back if you get stuck.

---

### Post by bejo3 on 2014-11-28
Hi Chili555. 

Thank you for the new files. 
As you mentioned, it didn't "make" without errors. 

```

bejo@bejo-ThinkPad-E555:~/rtlwifi_new$ make
make -C /lib/modules/3.2.0-72-generic/build M=/home/bejo/rtlwifi_new modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-3.2.0-72-generic'
  CC [M]  /home/bejo/rtlwifi_new/pci.o
/home/bejo/rtlwifi_new/pci.c: In Funktion »rtl_pci_parse_configuration«:
/home/bejo/rtlwifi_new/pci.c:432:2: Fehler: Implizite Deklaration der Funktion »pcie_capability_read_word« [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/bejo/rtlwifi_new/pci.o] Fehler 1
make[1]: *** [_module_/home/bejo/rtlwifi_new] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-3.2.0-72-generic'
make: *** [all] Fehler 2

```

My computer speaks german - but fortunately the translation is given too;-) 
Apparently there is a problem with the implicit-function-declaration for pcie_capability_read_word in pci.c. I did not find the function declaration in that file at all. Actually I could not find it in any of the given files. I have no clue, how to approach a solution here. 

The readme file says: "This code will build on any kernel 3.0 and newer." So there is little remainig hope, that it could work. 

I do not know, whether it makes sence to try to solve this, since I seem to have to go into these thousands of lines of code in detail. I am not really familiar with programming at that level and don't know how the wifi hardware works exactly. Isn't this too big for me? What is your opinion? Do you have an idea, what I could try to change?

Thanks again for your time and help. 

Regards, Johannes.

---

### Post by jeremy31 on 2014-11-28
I can't get it to build on my 3.2 laptop either, I do know of workaround that compiled for me, however I don't have that card
```
cd Desktop
```
```
wget -N -t 5 -T 10 https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.16/backports-3.16-1.tar.xz
```
```
tar -xvpf backports-3.16-1.tar.xz
```
```
sudo apt-get update
```
```
sudo apt-get install linux-headers-generic build-essential
```
```
cd backports-3.16-1
```
```
make defconfig-rtlwifi
```
```
make
```
```
sudo make install
```

It might take some time for some commands to finish but after the last one it should inform you to reboot

Good Luck bejo3

---

### Post by bejo3 on 2014-11-28
Hi jeremy31. 

Thank you for your answer. I typed in your lines step by step and ended up with this message: 

```

  DEPMOD  3.2.0-72-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("elementary OS") tag for your distribution to avoid this warning.

Your backported driver modules should be installed now.
Reboot.

```

I locked in a root, updated my intramfs and rebooted the system. I still do not see the wifi. 
This time I got no errors or warnings. 

A lot of things were downloaded and installed meanwhile. I ran the wireless script again. 

```


########## wireless info START ##########

Report from: 28 Nov 2014 22:55 CET +0100

Booted last: 28 Nov 2014 22:46 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    elementary OS
Description:    elementary OS Luna
Release:    0.2.1
Codename:    luna

##### kernel ############################

Linux 3.2.0-72-generic #107-Ubuntu SMP Thu Nov 6 14:24:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Pantheon

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:5110]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 04f2:b444 Chicony Electronics Co., Ltd 
Bus 004 Device 002: ID 0bda:b728 Realtek Semiconductor Corp. 

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be             120801  0 
rtl8723_common         23712  1 rtl8723be
rtl_pci                35613  1 rtl8723be
rtlwifi                91070  2 rtl8723be,rtl_pci
mac80211              614800  3 rtl8723be,rtl_pci,rtlwifi
cfg80211              599648  2 rtlwifi,mac80211
btcoexist              50313  1 rtl8723be
compat                 37460  6 rtl8723be,rtl_pci,rtlwifi,mac80211,cfg80211,btcoexist
wmi                    19256  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.2.105  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2ad2:44ff:fedf:d1e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1921 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:886642 (886.6 KB)  TX bytes:298162 (298.1 KB)
          Interrupt:86 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.0.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Kabelnetzwerkverbindung 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.2.0-72-generic/updates/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
version:        backported from Linux (v3.16-0-g19583ca) using backports v3.16-1-0-g87df966
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,compat,btcoexist,mac80211
vermagic:       3.2.0-72-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.2.0-72-generic/updates/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
vermagic:       3.2.0-72-generic SMP mod_unload modversions 

[rtl_pci]
filename:       /lib/modules/3.2.0-72-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2A841709EF6A38E777CCD34
depends:        mac80211,rtlwifi,compat
vermagic:       3.2.0-72-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.2.0-72-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.16-0-g19583ca) using backports v3.16-1-0-g87df966
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     AEDBFD2C2F64D9D545BF951
depends:        mac80211,compat,cfg80211
vermagic:       3.2.0-72-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.2.0-72-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.16-0-g19583ca) using backports v3.16-1-0-g87df966
srcversion:     15791DA6391E3692639BAB5
depends:        cfg80211,compat
vermagic:       3.2.0-72-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.2.0-72-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.16-0-g19583ca) using backports v3.16-1-0-g87df966
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     67813FD63FE30A8DC22E6B7
depends:        compat
vermagic:       3.2.0-72-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b44
blacklist b43legacy
blacklist b43
blacklist brcm80211
blacklist brcmsmac
blacklist brcmfmac
blacklist ssb
blacklist bcma
blacklist bcm43xx

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:03.1/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[    5.070059] rtl8723be 0000:03:00.0: PCI INT A -> GSI 40 (level, low) -> IRQ 40
[    5.070079] rtl8723be 0000:03:00.0: setting latency timer to 64
[    5.134887] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[    5.191157] rtlwifi: Firmware rtlwifi/rtl8723befw.bin not available
[   12.341779] IBM TrackPoint firmware: 0x0e, buttons: 3/3

########## wireless info END ############

```

Unfortunately all given hints did not work out for me here. If you have another idea, please let me know. 

Thanks alot - Johannes.

---

### Post by jeremy31 on 2014-11-28
> **bejo3 said:**
> Hi jeremy31. 

Thank you for your answer. I typed in your lines step by step and ended up with this message: 

```

  DEPMOD  3.2.0-72-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("elementary OS") tag for your distribution to avoid this warning.

Your backported driver modules should be installed now.
Reboot.

```

I locked in a root, updated my intramfs and rebooted the system. I still do not see the wifi. 
This time I got no errors or warnings. 

A lot of things were downloaded and installed meanwhile. I ran the wireless script again. 

```


########## wireless info START ##########

Report from: 28 Nov 2014 22:55 CET +0100

Booted last: 28 Nov 2014 22:46 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    elementary OS
Description:    elementary OS Luna
Release:    0.2.1
Codename:    luna

##### kernel ############################

Linux 3.2.0-72-generic #107-Ubuntu SMP Thu Nov 6 14:24:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Pantheon

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:5110]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 04f2:b444 Chicony Electronics Co., Ltd 
Bus 004 Device 002: ID 0bda:b728 Realtek Semiconductor Corp. 

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be             120801  0 
rtl8723_common         23712  1 rtl8723be
rtl_pci                35613  1 rtl8723be
rtlwifi                91070  2 rtl8723be,rtl_pci
mac80211              614800  3 rtl8723be,rtl_pci,rtlwifi
cfg80211              599648  2 rtlwifi,mac80211
btcoexist              50313  1 rtl8723be
compat                 37460  6 rtl8723be,rtl_pci,rtlwifi,mac80211,cfg80211,btcoexist
wmi                    19256  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.2.105  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2ad2:44ff:fedf:d1e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1921 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:886642 (886.6 KB)  TX bytes:298162 (298.1 KB)
          Interrupt:86 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.0.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Kabelnetzwerkverbindung 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.2.0-72-generic/updates/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
version:        backported from Linux (v3.16-0-g19583ca) using backports v3.16-1-0-g87df966
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,compat,btcoexist,mac80211
vermagic:       3.2.0-72-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.2.0-72-generic/updates/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
vermagic:       3.2.0-72-generic SMP mod_unload modversions 

[rtl_pci]
filename:       /lib/modules/3.2.0-72-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2A841709EF6A38E777CCD34
depends:        mac80211,rtlwifi,compat
vermagic:       3.2.0-72-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.2.0-72-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.16-0-g19583ca) using backports v3.16-1-0-g87df966
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     AEDBFD2C2F64D9D545BF951
depends:        mac80211,compat,cfg80211
vermagic:       3.2.0-72-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.2.0-72-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.16-0-g19583ca) using backports v3.16-1-0-g87df966
srcversion:     15791DA6391E3692639BAB5
depends:        cfg80211,compat
vermagic:       3.2.0-72-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.2.0-72-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.16-0-g19583ca) using backports v3.16-1-0-g87df966
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     67813FD63FE30A8DC22E6B7
depends:        compat
vermagic:       3.2.0-72-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b44
blacklist b43legacy
blacklist b43
blacklist brcm80211
blacklist brcmsmac
blacklist brcmfmac
blacklist ssb
blacklist bcma
blacklist bcm43xx

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:03.1/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[    5.070059] rtl8723be 0000:03:00.0: PCI INT A -> GSI 40 (level, low) -> IRQ 40
[    5.070079] rtl8723be 0000:03:00.0: setting latency timer to 64
[    5.134887] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[    5.191157] rtlwifi: Firmware rtlwifi/rtl8723befw.bin not available
[   12.341779] IBM TrackPoint firmware: 0x0e, buttons: 3/3

########## wireless info END ############

```

Unfortunately all given hints did not work out for me here. If you have another idea, please let me know. 

Thanks alot - Johannes.

Wireless info indicates you need firmware, I think that is in linux-firmware package ```
sudo apt-get install linux-firmware
``` reboot

---

### Post by bejo3 on 2014-11-28
Hi again. 

the firmware package is up to date. When I type in your command, my computer tells me, that it is the newest version...

another idea? 

Thanks, Johannes.

---

### Post by jeremy31 on 2014-11-28
[https://www.dropbox.com/s/2060sbivgdr73cd/rtl8723befw.bin?dl=0](https://www.dropbox.com/s/2060sbivgdr73cd/rtl8723befw.bin?dl=0)
Download it into your home folder then ```
sudo cp rtl8723befw.bin /lib/firmware/rtlwifi/
```
Reboot again, I don't know why that wasn't in linux-firmware for 12.04

---

### Post by bejo3 on 2014-11-29
THANK YOU! It is working now. 

Excellent support over here. 

Have a great time! And thanks again. Best regards, Johannes.

---

### Post by Moulik on 2015-02-26
jeremy31,

I tried the same step on my laptop. But it gave an error. 
I have Lenovo Z50 70 laptop with Realtek RLT8723BE for wifi. The kernel is the newest one. 

moulik@Lenovo:~/Documents/backports-3.16-1$ make
make[5]: `conf' is up to date.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/moulik/Documents/backports-3.16-1/compat/main.o
  LD [M]  /home/moulik/Documents/backports-3.16-1/compat/compat.o
  CC [M]  /home/moulik/Documents/backports-3.16-1/drivers/net/wireless/rtlwifi/base.o
In file included from /home/moulik/Documents/backports-3.16-1/backport-include/generated/utsrelease.h:1:0,
                 from /home/moulik/Documents/backports-3.16-1/backport-include/linux/skbuff.h:5,
                 from include/linux/if_ether.h:23,
                 from /home/moulik/Documents/backports-3.16-1/backport-include/linux/if_ether.h:3,
                 from include/linux/etherdevice.h:25,
                 from /home/moulik/Documents/backports-3.16-1/backport-include/linux/etherdevice.h:3,
                 from /home/moulik/Documents/backports-3.16-1/drivers/net/wireless/rtlwifi/wifi.h:37,
                 from /home/moulik/Documents/backports-3.16-1/drivers/net/wireless/rtlwifi/base.c:30:
include/generated/utsrelease.h:2:32: error: invalid digit "8" in octal constant
 #define UTS_UBUNTU_RELEASE_ABI 031800
                                ^
/home/moulik/Documents/backports-3.16-1/backport-include/linux/skbuff.h:333:56: note: in expansion of macro ‘UTS_UBUNTU_RELEASE_ABI’
     !(LINUX_VERSION_CODE == KERNEL_VERSION(3,13,11) && UTS_UBUNTU_RELEASE_ABI > 30)
                                                        ^
In file included from /home/moulik/Documents/backports-3.16-1/backport-include/generated/utsrelease.h:1:0,
                 from /home/moulik/Documents/backports-3.16-1/backport-include/linux/u64_stats_sync.h:5,
                 from include/net/snmp.h:52,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:14,
                 from /home/moulik/Documents/backports-3.16-1/backport-include/net/net_namespace.h:4,
                 from include/linux/netdevice.h:44,
                 from /home/moulik/Documents/backports-3.16-1/backport-include/linux/netdevice.h:3,
                 from include/linux/etherdevice.h:26,
                 from /home/moulik/Documents/backports-3.16-1/backport-include/linux/etherdevice.h:3,
                 from /home/moulik/Documents/backports-3.16-1/drivers/net/wireless/rtlwifi/wifi.h:37,
                 from /home/moulik/Documents/backports-3.16-1/drivers/net/wireless/rtlwifi/base.c:30:
include/generated/utsrelease.h:2:32: error: invalid digit "8" in octal constant
 #define UTS_UBUNTU_RELEASE_ABI 031800
                                ^
/home/moulik/Documents/backports-3.16-1/backport-include/linux/u64_stats_sync.h:118:56: note: in expansion of macro ‘UTS_UBUNTU_RELEASE_ABI’
     !(LINUX_VERSION_CODE == KERNEL_VERSION(3,13,11) && UTS_UBUNTU_RELEASE_ABI > 30)
                                                        ^
make[7]: *** [/home/moulik/Documents/backports-3.16-1/drivers/net/wireless/rtlwifi/base.o] Error 1
make[6]: *** [/home/moulik/Documents/backports-3.16-1/drivers/net/wireless/rtlwifi] Error 2
make[5]: *** [/home/moulik/Documents/backports-3.16-1/drivers/net/wireless] Error 2
make[4]: *** [_module_/home/moulik/Documents/backports-3.16-1] Error 2
make[3]: *** [modules] Error 2
make[2]: *** [modules] Error 2
make[1]: *** [modules] Error 2
make: *** [default] Error 2

---

### Post by jeremy31 on 2015-02-26
Considering you may have a newer kernel and newer backports are available now, try
```
wget -N -t 5 -T 10 https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz
tar -xf backports-3.18.1-1.tar.xz
cd ~/backports-3.18.1-1
make defconfig-rtlwifi
make
sudo make install
```

Since you have the Lenovo z50-70 check ```
rfkill list all
``` and post results

---

### Post by www.rzr.online.fr on 2015-05-03
Hi Do you have bluetooth working too ?

-- 
[http://rzr.online.fr/q/ideapad](http://rzr.online.fr/q/ideapad)

---

