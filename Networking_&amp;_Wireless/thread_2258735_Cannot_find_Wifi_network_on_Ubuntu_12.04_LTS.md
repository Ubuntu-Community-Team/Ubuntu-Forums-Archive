---
title: "Cannot find Wifi network on Ubuntu 12.04 LTS"
date: 2014-12-30
forum: Networking &amp; Wireless
---

### Post by Rohit_Jain on 2014-12-30
Hi,

I've got a Dell Latitude 3440 laptop, with Ubuntu 12.04 LTS installed on it. I am unable to connect to WiFi. The network itself doesn't show any WiFi connections to connect to, however, in Edit Connection, I've a WiFi connection configured. Seems like some driver issue? I don't know for sure. I've recently upgraded my Linux Firmware after the update manager popped up with that suggestion.

Any help with this stuff.

---

### Post by praseodym on 2014-12-30
Please run the wireless script from the sticky thread and show the outputs.

---

### Post by Rohit_Jain on 2014-12-30
Hi,

This is output I got after running the script:

```


########## wireless info START ##########


Report from: 30 Dec 2014 17:57 IST +0530


Booted last: 30 Dec 2014 16:20 IST +0530


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.5 LTS
Release:	12.04
Codename:	precise


##### kernel ############################


Linux 3.5.0-57-generic #84~precise1-Ubuntu SMP Thu Nov 6 06:09:35 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


06:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Dell Device [1028:020c]


07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Dell Device [1028:0606]
	Kernel driver in use: r8168


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0c45:64af Microdia 
Bus 001 Device 005: ID 0cf3:0036 Atheros Communications, Inc. 


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
wmi                    19257  1 dell_wmi
ath3k                  12918  0 
bluetooth             212001  25 bnep,rfcomm,btusb,ath3k


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:10.71.2.51  Bcast:10.71.3.255  Mask:255.255.252.0
          inet6 addr: fe80::76e6:e2ff:fe0b:fe89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:87638044 (87.6 MB)  TX bytes:6470336 (6.4 MB)
          Interrupt:57 Base address:0x2000 


tun0      Link encap:UNSPEC  HWaddr <MAC 'tun0' [IF]>  
          inet addr:192.168.15.110  P-t-P:192.168.15.109  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2061 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2624 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:547345 (547.3 KB)  TX bytes:229609 (229.6 KB)


##### iwconfig ##########################


tun0      no wireless extensions.


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.71.0.1       0.0.0.0         UG    0      0        0 eth0
10.71.0.0       0.0.0.0         255.255.252.0   U     1      0        0 eth0
10.120.15.0     192.168.15.109  255.255.255.0   UG    0      0        0 tun0
46.51.216.0     192.168.15.109  255.255.248.0   UG    0      0        0 tun0
46.137.192.0    192.168.15.109  255.255.192.0   UG    0      0        0 tun0
54.169.0.0      192.168.15.109  255.255.0.0     UG    0      0        0 tun0
54.179.0.0      192.168.15.109  255.255.0.0     UG    0      0        0 tun0
54.251.0.0      192.168.15.109  255.255.0.0     UG    0      0        0 tun0
54.254.0.0      192.168.15.109  255.255.0.0     UG    0      0        0 tun0
54.255.0.0      192.168.15.109  255.255.0.0     UG    0      0        0 tun0
122.248.192.0   192.168.15.109  255.255.192.0   UG    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
175.41.128.0    192.168.15.109  255.255.192.0   UG    0      0        0 tun0
192.168.15.0    192.168.15.109  255.255.255.0   UG    0      0        0 tun0
192.168.15.1    192.168.15.109  255.255.255.255 UGH   0      0        0 tun0
192.168.15.109  0.0.0.0         255.255.255.255 UH    0      0        0 tun0


##### resolv.conf #######################


nameserver 127.0.0.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         10.71.2.51
    Prefix:          22 (255.255.252.0)
    Gateway:         10.71.0.1


    DNS:             103.6.156.199
    DNS:             8.8.8.8


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


[[/etc/NetworkManager/system-connections/PSL-HO]] (600 root)
[connection] id=PSL-HO | type=802-11-wireless
[802-11-wireless] ssid=PSL-HO | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


nl80211 not found.


##### iwlist channels ###################


tun0      no frequency information.


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


sudo: unable to resolve host PSLBLRLA-136-06
tun0      Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath3k]
filename:       /lib/modules/3.5.0-57-generic/updates/dkms/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0.1
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     FBB03F235485371B207CD8D
depends:        bluetooth
vermagic:       3.5.0-57-generic SMP mod_unload modversions 


##### module parameters #################


##### /etc/modules ######################


lp
rtc
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


[/etc/modprobe.d/dkms.conf]
blacklist r8169


[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/sleep.d/11-bluetooth-restart] (755 root)
case "$1" in
    hibernate|suspend)
        ;;
    resume|thaw)
        sleep 2
        sudo service bluetooth restart
        ;;
    *) exit 0
        ;;
    esac


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0 (r8168)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


########## wireless info END ############



```

[B]*P.S:*  Just FYI, I did a backup from my previous laptop to this one. My previous laptop was Ubuntu 14.04. And this one is 12.04. While doing backup, I mistakenly also copied ~/.config directory, and merged all it's content in my new laptop. Can that be problem (which I think is the prime candidate).

[/B]

---

### Post by jeremy31 on 2014-12-30
The big issue is that your wifi card is not supported with the newest 12.04 kernel, the 168c:0037 is but not your 168c:0036, here is why I say this
```
filename:       /lib/modules/3.2.0-74-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DAE1627B8BFAFE91C008E84
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,cfg80211,ath
intree:         Y
vermagic:       3.2.0-74-generic SMP mod_unload modversions 


```

I would guide you through installing it using backports, but I have to get to work now

---

### Post by praseodym on 2014-12-30
Install the LTS enablement stack:
```

sudo apt-get -s install --install-recommends linux-generic-lts-trusty linux-image-generic-lts-trusty linux-headers-generic-lts-trusty xserver-xorg-lts-trusty libgl1-mesa-glx-lts-trusty
``` 
If it works without errors, repeat it without "-s"

---

### Post by Rohit_Jain on 2014-12-30
I got following unmet dependencies error:

The following packages have unmet dependencies:
 libgl1-mesa-glx-lts-trusty : Depends: libglapi-mesa-lts-trusty (= 10.1.3-0ubuntu0.2~precise2) but it is not going to be installed
 xserver-xorg-lts-trusty : Recommends: xserver-xorg-input-all-lts-trusty but it is not going to be installed
                           Recommends: xserver-xorg-video-all-lts-trusty but it is not going to be installed
                           Recommends: x11-xserver-utils-lts-trusty but it is not going to be installed
                           Conflicts: libglapi-mesa:i386 (>= 0~)
E: Unable to correct problems, you have held broken packages.

---

### Post by praseodym on 2014-12-30
Please run
```

sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
If it asks you to reboot, do so, and try it again.

---

### Post by Rohit_Jain on 2014-12-30
> **praseodym said:**
> Please run
```

sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
If it asks you to reboot, do so, and try it again.

Still the same dependency issue :(

---

### Post by Rohit_Jain on 2014-12-30
After running those commands, I restarted my machine. Then again ran the previous command, but it came up with following error:

Unable to lock administrator directory (/var/lib/dpkg/) is another process using it?

Then I ran the command: 

    sudo lsof /var/lib/dpkg/lock

I got following warning:

      lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/rohitj-temporary/.gvfs
      Output information may be incomplete.

---

### Post by praseodym on 2014-12-30
Is another package manager opened? Close all of them and try it again. Or shutdown and restart

---

### Post by Rohit_Jain on 2014-12-30
No other things are open. That lock issue is not coming now. But the result is again the same unmet dependencies.. The same one.

---

### Post by praseodym on 2014-12-30
Check this one

[http://askubuntu.com/questions/336138/dependency-issues-while-trying-to-upgrade-12-04-2-to-the-12-04-3-hwe-stack](http://askubuntu.com/questions/336138/dependency-issues-while-trying-to-upgrade-12-04-2-to-the-12-04-3-hwe-stack)

---

### Post by Rohit_Jain on 2014-12-30
Following the solutions in that link, I added few more packages, and came up with this:

```

sudo apt-get -s install --install-recommends libgl1-mesa-dri-lts-trusty libglapi-mesa-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty xserver-xorg-input-all-lts-trusty xserver-xorg-video-all-lts-trusty x11-xserver-utils-lts-trusty linux-generic-lts-trusty linux-image-generic-lts-trusty linux-headers-generic-lts-trusty

```

Now I get two conflicts:

```

The following packages have unmet dependencies:
 libglapi-mesa-lts-trusty : Conflicts: libglapi-mesa:i386
 xserver-xorg-lts-trusty : Conflicts: libglapi-mesa:i386 (>= 0~)
E: Unable to correct problems, you have held broken packages.

```

Then I tried removing *libglapi-mesa-lts-trusty, *as I thought that was conflicting, but that didn't help. I'm all lost now...

---

### Post by Rohit_Jain on 2014-12-30
Has this all to do something with the fact that I replaced the .config folder from 14.04 onto 12.04, and thus it could have messed up my configuration or something?

---

### Post by Rohit_Jain on 2014-12-30
Aha, got it working with this one:

```

sudo apt-get -s install --install-recommends libgl1-mesa-dri-lts-trusty libglapi-mesa-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty xserver-xorg-input-all-lts-trusty xserver-xorg-video-all-lts-trusty x11-xserver-utils-lts-trusty linux-generic-lts-trusty linux-image-generic-lts-trusty linux-headers-generic-lts-trusty libglapi-mesa-lts-trusty:i386 libgl1-mesa-dri-lts-trusty:i386 libgl1-mesa-glx-lts-trusty:i386

```

Had to add these 3:

- libglapi-mesa-lts-trusty:i386 
- libgl1-mesa-dri-lts-trusty:i386
- libgl1-mesa-glx-lts-trusty:i386

at the end.

Now should I run this with `-s` removed?

---

### Post by praseodym on 2014-12-30
Yes

---

### Post by Rohit_Jain on 2015-01-01
It failed with following errors:

```

run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
Error! Bad return status for module build on kernel: 3.13.0-43-generic (x86_64)
Consult /var/lib/dkms/oem-bt-dw1705/0.1/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.13.0-43-generic (x86_64)
Consult /var/lib/dkms/r8168/8.032.04/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.5.0-57-generic
Found initrd image: /boot/initrd.img-3.5.0-57-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-74-generic
Found initrd image: /boot/initrd.img-3.2.0-74-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic-lts-trusty (3.13.0.43.37) ...
Setting up linux-headers-3.13.0-43 (3.13.0-43.72~precise1) ...
Setting up linux-headers-3.13.0-43-generic (3.13.0-43.72~precise1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
Error! Bad return status for module build on kernel: 3.13.0-43-generic (x86_64)
Consult /var/lib/dkms/oem-bt-dw1705/0.1/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.13.0-43-generic (x86_64)
Consult /var/lib/dkms/r8168/8.032.04/build/make.log for more information.
Setting up linux-headers-generic-lts-trusty (3.13.0.43.37) ...
Setting up linux-generic-lts-trusty (3.13.0.43.37) ...
Setting up x11-xserver-utils-lts-trusty (7.7+2ubuntu1~precise1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place



```

---

### Post by praseodym on 2015-01-01
8.0.32 is too old.

```
sudo dkms remove -m r8168-dkms -v 8.033.00 --all
sudo rm -r /usr/src/r8168-dkms-8.032.00 
```
Take the new one

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.039.00
sudo dkms build -m r8168-dkms -v 8.039.00
sudo dkms install -m r8168-dkms -v 8.039.00
sudo depmod -a
sudo update-initramfs -u 
```

---

### Post by Rohit_Jain on 2015-01-03
Well it turned out that with the previous command, which failed with error,the WiFi started working after restarting the machine. But since it's office laptop, I prefered to do a fresh installation. Installed 14.04 LTS rather. Thanks for your help.

Since that solved the WiFi issue, should I mark it as Solved, ignoring the error I got?

---

