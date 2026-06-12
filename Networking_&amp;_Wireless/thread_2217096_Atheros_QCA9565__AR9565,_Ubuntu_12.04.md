---
title: "Atheros QCA9565 / AR9565, Ubuntu 12.04"
date: 2014-04-15
forum: Networking &amp; Wireless
---

### Post by Liis on 2014-04-15
Hello!


So I have similar problem like many others. I update my laptop and after that it won't connect do wifi anymore. I have search forums, try to do different stuff, but still it doesn't work. Ubuntu is new for me so it's kinda difficult  to operate by myself. Can somebody help me, please?

---

### Post by Warren Hill on 2014-04-15
Take a look here

[https://help.ubuntu.com/community/WirelessTroubleshootingProcedure.](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure.)

---

### Post by Liis on 2014-04-15
Yep, I already have been there, and done that..didn't help much... :(

---

### Post by chili555 on 2014-04-15
> **Warren Hill said:**
> Take a look here

[https://help.ubuntu.com/community/WirelessTroubleshootingProcedure.](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure.)Here is what it says, Warren.> **This page does not exist yet. You can create a new empty page, or use one of the page templates.**

---

### Post by chili555 on 2014-04-15
> **Liis said:**
> Hello!


So I have similar problem like many others. I update my laptop and after that it won't connect do wifi anymore. I have search forums, try to do different stuff, but still it doesn't work. Ubuntu is new for me so it's kinda difficult  to operate by myself. Can somebody help me, please?Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0280
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Warren Hill on 2014-04-16
Apologies for previous link it should have  been 


[https://help.ubuntu.com/community/WirelessTroubleshootingProcedure](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure)

---

### Post by Liis on 2014-04-16
```
liis@liis-Inspiron-3521:~$ lspci -nn | grep 0280
08:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
liis@liis-Inspiron-3521:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```


Here it is.

---

### Post by praseodym on 2014-04-16
Deactivate the hardware encryption of the driver:
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by Liis on 2014-04-16
```
liis@liis-Inspiron-3521:~$ echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
[sudo] password for liis: 
Sorry, try again.
[sudo] password for liis: 
options ath9k nohwcrypt=1
liis@liis-Inspiron-3521:~$ sudo modprobe -rfv ath9k
rmmod /lib/modules/3.2.0-60-generic/updates/cw-3.6/ath9k.ko
rmmod /lib/modules/3.2.0-60-generic/updates/cw-3.6/mac80211.ko
rmmod /lib/modules/3.2.0-60-generic/updates/cw-3.6/ath9k_common.ko
rmmod /lib/modules/3.2.0-60-generic/updates/cw-3.6/ath9k_hw.ko
rmmod /lib/modules/3.2.0-60-generic/updates/cw-3.6/ath.ko
rmmod /lib/modules/3.2.0-60-generic/updates/cw-3.6/cfg80211.ko
liis@liis-Inspiron-3521:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.2.0-60-generic/updates/cw-3.6/cfg80211.ko 
insmod /lib/modules/3.2.0-60-generic/updates/cw-3.6/ath.ko 
insmod /lib/modules/3.2.0-60-generic/updates/cw-3.6/ath9k_hw.ko 
insmod /lib/modules/3.2.0-60-generic/updates/cw-3.6/ath9k_common.ko 
insmod /lib/modules/3.2.0-60-generic/updates/cw-3.6/mac80211.ko 
insmod /lib/modules/3.2.0-60-generic/updates/cw-3.6/ath9k.ko nohwcrypt=1 nohwcrypt=1 nohwcrypt=1 nohwcrypt=1
```


Hope I did it right.

---

### Post by praseodym on 2014-04-16
So, lets check now:
```

dmesg | grep ath
iwconfig
ifconfig -a
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
```
I recommend changing the encryption to pure WPA2-AES (CCMP), check the router manual.

---

### Post by Liis on 2014-04-16
```
liis@liis-Inspiron-3521:~$ dmesg | grep ath
[   16.559221] device-mapper: multipath: version 1.3.2 loaded
[   16.704049] ath3k: Unknown symbol bt_printk (err 0)
[   16.732652] ath3k: Unknown symbol bt_printk (err 0)
[  587.594210] ath9k: ath9k: Driver unloaded
liis@liis-Inspiron-3521:~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


liis@liis-Inspiron-3521:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr ec:f4:bb:86:1c:c1  
          inet addr:192.168.1.118  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eef4:bbff:fe86:1cc1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15063 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16021412 (16.0 MB)  TX bytes:1245342 (1.2 MB)
          Interrupt:43 Base address:0x8000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:120917 (120.9 KB)  TX bytes:120917 (120.9 KB)


liis@liis-Inspiron-3521:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search lan
liis@liis-Inspiron-3521:~$ iwlist chan
lo        no frequency information.


eth0      no frequency information.


liis@liis-Inspiron-3521:~$ sudo iwlist scan
[sudo] password for liis: 
lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.
```

---

### Post by praseodym on 2014-04-16
**ath3k** is your Bluetooth driver. Obviously its unloading the wireless driver **ath9k**. Lets check
```

sudo modprobe -rfv ath3k
sudo modprobe -v ath9k nohwcrypt=1
```

---

### Post by Liis on 2014-04-16
Something wrong with that code because it doesn't do anything.

---

### Post by praseodym on 2014-04-16
Lets check
```

lsmod
iwconfig
cat /etc/resolv.conf
route -n
ifconfig -a
sudo iwlist scan
rfkill list
```

---

### Post by Liis on 2014-04-16
```
liis@liis-Inspiron-3521:~$ lsmod
Module                  Size  Used by
ath9k                 145061  0 
mac80211              557654  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              387055  2 ath9k,ath9k_common
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
cfg80211              219204  3 ath9k,mac80211,ath
snd_hda_codec_hdmi     32193  1 
snd_hda_codec_realtek    73693  1 
joydev                 17693  0 
rfcomm                 46747  0 
parport_pc             32866  0 
bnep                   18139  2 
ppdev                  17113  0 
rts5139               351188  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_intel          33327  3 
snd_hda_codec         134156  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
bluetooth             205289  10 rfcomm,bnep
compat                 20099  8 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211,rfcomm,bnep,bluetooth
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
fglrx                7535410  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
dm_multipath           23275  0 
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    41616  0 
psmouse                97519  0 
soundcore              15091  1 snd
serio_raw              13211  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  478556  2 
wmi                    19256  1 dell_wmi
drm_kms_helper         46978  1 i915
drm                   241971  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_raid45              78155  0 
r8169                  62190  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20961  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 653116  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
liis@liis-Inspiron-3521:~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


liis@liis-Inspiron-3521:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search lan
liis@liis-Inspiron-3521:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
liis@liis-Inspiron-3521:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr ec:f4:bb:86:1c:c1  
          inet addr:192.168.1.118  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eef4:bbff:fe86:1cc1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20914 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20267358 (20.2 MB)  TX bytes:2068936 (2.0 MB)
          Interrupt:43 Base address:0x8000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:219302 (219.3 KB)  TX bytes:219302 (219.3 KB)


liis@liis-Inspiron-3521:~$ sudo iwlist scan
[sudo] password for liis: 
lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


liis@liis-Inspiron-3521:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

---

### Post by praseodym on 2014-04-16
Obviously, there is no entry for an interface. Lets create one:
```

sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
sudo service udev reload
sudo service udev restart
sudo /etc/init.d/networking restart
sudo service network-manager restart
```
Check:
```

ifconfig -a
iwconfig
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by Liis on 2014-04-16
```
liis@liis-Inspiron-3521:~$ sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
mv: cannot stat `/etc/udev/rules.d/70-persistent-net.rules': No such file or directory

```

---

### Post by praseodym on 2014-04-16
Ok, thats the reason. Continue with the others.

---

### Post by Liis on 2014-04-16
```
liis@liis-Inspiron-3521:~$ sudo udevadm trigger
[sudo] password for liis: 
liis@liis-Inspiron-3521:~$ sudo udev reload
sudo: udev: command not found
liis@liis-Inspiron-3521:~$ sudo service udev restart
udev stop/waiting
udev start/running, process 13385
liis@liis-Inspiron-3521:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
liis@liis-Inspiron-3521:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 13440

```

---

### Post by Liis on 2014-04-16
```
liis@liis-Inspiron-3521:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr ec:f4:bb:86:1c:c1  
          inet addr:192.168.1.118  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eef4:bbff:fe86:1cc1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:171151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:211267801 (211.2 MB)  TX bytes:13541264 (13.5 MB)
          Interrupt:43 Base address:0x8000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:571940 (571.9 KB)  TX bytes:571940 (571.9 KB)


liis@liis-Inspiron-3521:~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


liis@liis-Inspiron-3521:~$ cat /etc/udev/rules.d/70-persistent.net.rules
cat: /etc/udev/rules.d/70-persistent.net.rules: No such file or directory

```

---

### Post by praseodym on 2014-04-16
```
sudo udev reload
```

needs to be
```

sudo [COLOR="#FF0000"]service[/COLOR] udev reload
sudo service udev restart
sudo /etc/init.d/networking restart
sudo service network-manager restart
```
(alternatively: reboot)

Then check the other outputs

---

### Post by Liis on 2014-04-16
```
liis@liis-Inspiron-3521:~$ sudo service udev reload
[sudo] password for liis: 
liis@liis-Inspiron-3521:~$ sudo service udev restart
udev stop/waiting
udev start/running, process 3820
liis@liis-Inspiron-3521:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
liis@liis-Inspiron-3521:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 3873
```

This was result..did reboot but still no wifi connection.

---

### Post by praseodym on 2014-04-16
Please upgrade the kernel to 3.11 via:
```

sudo apt-get install linux-image-generic-lts-saucy linux-headers-generic-lts-saucy build-essential dkms
sudo apt-get install xserver-xorg-lts-saucy libgl1-mesa-glx-lts-saucy
```
Reboot.

---

### Post by Liis on 2014-04-16
```
liis@liis-Inspiron-3521:~$ sudo apt-get install linux-image-generic-lts-saucy linux-headers-generic-lts-saucy build-essential dkms
[sudo] password for liis: 
Sorry, try again.
[sudo] password for liis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
dkms is already the newest version.
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2:i386 libkrb5-3:i386 libk5crypto3:i386 libstdc++6:i386
  libxfixes3:i386 gir1.2-timezonemap-1.0 libqt4-declarative:i386 realpath
  efibootmgr liblcms1:i386 diffstat libwrap0:i386 libsamplerate0:i386
  linux-headers-3.2.0-26-generic libjpeg-turbo8:i386 libdmraid1.0.0.rc16
  libdebconfclient0 libjpeg8:i386 linux-headers-3.2.0-26 kpartx-boot
  libqt4-script:i386 libopts25 libqt4-network:i386 gir1.2-json-1.0
  libqt4-dbus:i386 libxxf86vm1:i386 quilt libgl1-mesa-dri:i386
  libxcb-glx0:i386 libgl1-mesa-glx:i386 autogen libjack-jackd2-0:i386
  libx11-xcb1:i386 libgnutls26:i386 libglapi-mesa:i386 libtasn1-3:i386
  libfreetype6:i386 sni-qt:i386 user-setup libmysqlclient18:i386
  libexpat1:i386 kpartx libqt4-xmlpatterns:i386 libavahi-common-data:i386
  rdate libjson0:i386 libxcb1:i386 libp11-kit0:i386 libxau6:i386
  mingw32-runtime libcups2:i386 libqtcore4:i386 libkrb5support0:i386
  libdebian-installer4 libopts25-dev libice6:i386 libspeexdsp1:i386
  libxdmcp6:i386 libgcrypt11:i386 btrfs-tools libxml2:i386 mingw32
  libkeyutils1:i386 apt-clone localechooser-data libqt4-sql:i386
  libasound2:i386 language-pack-kde-en libflac8:i386 libxrender1:i386
  liborc-0.4-0:i386 libvorbisenc2:i386 kde-l10n-engb mingw32-binutils
  libqt4-xml:i386 libasyncns0:i386 libxss1:i386 libtiff4:i386 skype-bin:i386
  libgstreamer-plugins-base0.10-0:i386 libqtgui4:i386 libavahi-client3:i386
  libx11-6:i386 libfontconfig1:i386 libsm6:i386 libpulse0:i386 archdetect-deb
  libxdamage1:i386 dmraid python-pyicu libqt4-sql-mysql:i386
  libgssapi-krb5-2:i386 libxi6:i386 libvorbis0a:i386 libqtwebkit4:i386
  libgstreamer0.10-0:i386 libaudio2:i386 language-pack-kde-en-base libxt6:i386
  libxv1:i386 libxext6:i386 libavahi-common3:i386 gir1.2-xkl-1.0
  libsndfile1:i386 libsqlite3-0:i386 libmng1:i386 libasound2-plugins:i386
  libgpg-error0:i386 libllvm3.0:i386 libogg0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.11.0-19 linux-headers-3.11.0-19-generic
  linux-image-3.11.0-19-generic
Suggested packages:
  fdutils linux-lts-saucy-doc-3.11.0 linux-lts-saucy-source-3.11.0
  linux-lts-saucy-tools
The following NEW packages will be installed:
  linux-headers-3.11.0-19 linux-headers-3.11.0-19-generic
  linux-headers-generic-lts-saucy linux-image-3.11.0-19-generic
  linux-image-generic-lts-saucy
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 71.3 MB of archives.
After this operation, 278 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-3.11.0-19-generic amd64 3.11.0-19.33~precise1 [57.5 MB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.11.0-19 all 3.11.0-19.33~precise1 [12.6 MB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.11.0-19-generic amd64 3.11.0-19.33~precise1 [1,080 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-generic-lts-saucy amd64 3.11.0.19.18 [2,454 B]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-generic-lts-saucy amd64 3.11.0.19.18 [2,468 B]
Fetched 71.3 MB in 9s (7,819 kB/s)                                             
Selecting previously unselected package linux-image-3.11.0-19-generic.
(Reading database ... 225381 files and directories currently installed.)
Unpacking linux-image-3.11.0-19-generic (from .../linux-image-3.11.0-19-generic_3.11.0-19.33~precise1_amd64.deb) ...
Done.


Selecting previously unselected package linux-headers-3.11.0-19.
Unpacking linux-headers-3.11.0-19 (from .../linux-headers-3.11.0-19_3.11.0-19.33~precise1_all.deb) ...
Selecting previously unselected package linux-headers-3.11.0-19-generic.
Unpacking linux-headers-3.11.0-19-generic (from .../linux-headers-3.11.0-19-generic_3.11.0-19.33~precise1_amd64.deb) ...
Selecting previously unselected package linux-headers-generic-lts-saucy.
Unpacking linux-headers-generic-lts-saucy (from .../linux-headers-generic-lts-saucy_3.11.0.19.18_amd64.deb) ...
Selecting previously unselected package linux-image-generic-lts-saucy.
Unpacking linux-image-generic-lts-saucy (from .../linux-image-generic-lts-saucy_3.11.0.19.18_amd64.deb) ...
Setting up linux-image-3.11.0-19-generic (3.11.0-19.33~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-19-generic /boot/vmlinuz-3.11.0-19-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.11.0-19-generic /boot/vmlinuz-3.11.0-19-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
Error! Bad return status for module build on kernel: 3.11.0-19-generic (x86_64)
Consult /var/lib/dkms/alsa-hda/0.201207191422~precise1/build/make.log for more information.
```

---

### Post by praseodym on 2014-04-16
Ok, thats a sound module which is not build, but it should be an updated one there in the new kernel. Reboot

---

### Post by Liis on 2014-04-17
So today I turned my computer on and then its says i should reboot comp to finish updates..I did it, but then that picture shows up and I have no idea again what to do. :([IMG]http://ubuntuforums.org/attachment.php?attachmentid=252134&d=1397721620&thumb=1&stc=1[/IMG]

---

### Post by praseodym on 2014-04-17
Thats the Grub-2 bootloader. Mark the first entry and press RETURN

---

### Post by Liis on 2014-04-17
Okay, I did it but now its just loading and thats it.

---

### Post by praseodym on 2014-04-17
Reboot and choose "previous Ubuntu versions".

Have you tried 14.04 LTS which is released today from Live-CD or -USB?

---

### Post by Liis on 2014-04-17
It starded to work, there is no wifi icon so i went system settings -> network and then its says "the system network services are not compatible with this version" 
i did wrong choice at the beginning?

---

### Post by Liis on 2014-04-17
No I haven't try. It's already so complicated for me :(. But if that solve my problem I would like to try it.

---

### Post by praseodym on 2014-04-17
Please download these files:

For 32bit:

[http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.4.0-0ubuntu4.3_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.4.0-0ubuntu4.3_i386.deb)
[http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.9.4.1-0ubuntu2.3_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.9.4.1-0ubuntu2.3_i386.deb)

For 64bit:

[http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.4.0-0ubuntu4.3_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.4.0-0ubuntu4.3_amd64.deb)
[http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.9.4.1-0ubuntu2.3_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.9.4.1-0ubuntu2.3_amd64.deb)

Save them in "Downloads" (remove other DEB files there) and install via
```

sudo dpkg -i ~/Downloads/network*.deb
sudo service network-manager restart
```
If

```
uname -a
```

shows kernel 3.2 then remove 3.11 via
```

sudo apt-get remove --purge linux-image-3.11* linux-headers-3.11*
sudo apt-get autoremove
```
Reboot.

---

### Post by Liis on 2014-04-17
```
liis@liis-Inspiron-3521:~$ sudo dpkg -i ~/Downloads/network*.deb
[sudo] password for liis: 
(Reading database ... 254973 files and directories currently installed.)
Preparing to replace network-manager 0.9.4.0-0ubuntu4.3 (using .../network-manager_0.9.4.0-0ubuntu4.3_amd64.deb) ...
Unpacking replacement network-manager ...
Preparing to replace network-manager-gnome 0.9.4.1-0ubuntu2.3 (using .../network-manager-gnome_0.9.4.1-0ubuntu2.3_amd64.deb) ...
Unpacking replacement network-manager-gnome ...
Setting up network-manager (0.9.4.0-0ubuntu4.3) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up network-manager-gnome (0.9.4.1-0ubuntu2.3) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
liis@liis-Inspiron-3521:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 3996
liis@liis-Inspiron-3521:~$ uname -a
Linux liis-Inspiron-3521 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```


Umm not sure, that last line shows kernel?

---

### Post by praseodym on 2014-04-17
Yes, its 3.2, now remove 3.11 as described and try the 3.13 Mainline-kernel (which is part of 14.04):

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300-generic_3.13.0-031300.201401192235_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300-generic_3.13.0-031300.201401192235_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300_3.13.0-031300.201401192235_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300_3.13.0-031300.201401192235_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-image-3.13.0-031300-generic_3.13.0-031300.201401192235_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-image-3.13.0-031300-generic_3.13.0-031300.201401192235_amd64.deb)

Put them alone into "Downloads" and
```

sudo dpkg -i ~/Downloads/linux-*.deb
```
Reboot.

---

### Post by Liis on 2014-04-17
```
liis@liis-Inspiron-3521:~$ sudo dpkg -i ~/Downloads/linux-*.deb
[sudo] password for liis: 
(Reading database ... 258274 files and directories currently installed.)
Preparing to replace linux-headers-3.13.0-031300 3.13.0-031300.201401192235 (using .../linux-headers-3.13.0-031300_3.13.0-031300.201401192235_all.deb) ...
Unpacking replacement linux-headers-3.13.0-031300 ...
Preparing to replace linux-headers-3.13.0-031300-generic 3.13.0-031300.201401192235 (using .../linux-headers-3.13.0-031300-generic_3.13.0-031300.201401192235_amd64.deb) ...
Unpacking replacement linux-headers-3.13.0-031300-generic ...
Preparing to replace linux-image-3.13.0-031300-generic 3.13.0-031300.201401192235 (using .../linux-image-3.13.0-031300-generic_3.13.0-031300.201401192235_amd64.deb) ...
Done.
Unpacking replacement linux-image-3.13.0-031300-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-031300-generic /boot/vmlinuz-3.13.0-031300-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-031300-generic /boot/vmlinuz-3.13.0-031300-generic
Setting up linux-headers-3.13.0-031300 (3.13.0-031300.201401192235) ...
Setting up linux-headers-3.13.0-031300-generic (3.13.0-031300.201401192235) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-031300-generic /boot/vmlinuz-3.13.0-031300-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
ERROR (dkms apport): kernel package linux-headers-3.13.0-031300-generic is not supported
Error! Bad return status for module build on kernel: 3.13.0-031300-generic (x86_64)
Consult /var/lib/dkms/alsa-hda/0.201207191422~precise1/build/make.log for more information.
ERROR (dkms apport): kernel package linux-headers-3.13.0-031300-generic is not supported
Error! Bad return status for module build on kernel: 3.13.0-031300-generic (x86_64)
Consult /var/lib/dkms/oem-wireless-ath9k-3.9-rc4-2/0.1/build/make.log for more information.
Setting up linux-image-3.13.0-031300-generic (3.13.0-031300.201401192235) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.13.0-031300.201401192235 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.13.0-031300.201401192235 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-031300-generic /boot/vmlinuz-3.13.0-031300-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-031300-generic /boot/vmlinuz-3.13.0-031300-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
ERROR (dkms apport): kernel package linux-headers-3.13.0-031300-generic is not supported
Error! Bad return status for module build on kernel: 3.13.0-031300-generic (x86_64)
Consult /var/lib/dkms/alsa-hda/0.201207191422~precise1/build/make.log for more information.
ERROR (dkms apport): kernel package linux-headers-3.13.0-031300-generic is not supported
Error! Bad return status for module build on kernel: 3.13.0-031300-generic (x86_64)
Consult /var/lib/dkms/oem-wireless-ath9k-3.9-rc4-2/0.1/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-031300-generic /boot/vmlinuz-3.13.0-031300-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-031300-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-3.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-1.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8411-2.fw for module r8169
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-031300-generic /boot/vmlinuz-3.13.0-031300-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-031300-generic /boot/vmlinuz-3.13.0-031300-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-031300-generic /boot/vmlinuz-3.13.0-031300-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-031300-generic
Found initrd image: /boot/initrd.img-3.13.0-031300-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-39-generic
Found initrd image: /boot/initrd.img-3.2.0-39-generic
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

---

### Post by Liis on 2014-04-17
YAY, did reboot and I have wifi again. THANK YOU SO MUCH!! :)

---

### Post by praseodym on 2014-04-18
Thats good news.

Now you can clean-up the old kernels and header by running this command (copy/paste!):

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/(.*)-([^0-9]+)/1/")"'/d;s/^[^ ]* [^ ]* ([^ ]*).*/1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```
After that re-install 3.11 as backup:
```

sudo apt-get install linux-image-generic-lts-saucy linux-headers-generic-lts-saucy
```

---

### Post by Liis on 2014-04-25
Did that also, for now everything works perfectly :)

---

