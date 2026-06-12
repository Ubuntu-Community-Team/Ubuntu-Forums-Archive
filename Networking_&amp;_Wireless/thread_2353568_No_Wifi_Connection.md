---
title: "No Wifi Connection"
date: 2017-02-23
forum: Networking &amp; Wireless
---

### Post by aidanikuz on 2017-02-23
Before continuing, disclaimer: I know this question has been asked  and answered a million times and I have tried a the few solutions in  those questions and I still can't connect to the internet. 
 I have a Lenovo ThingPad Edge E145. I bought it just to install a  Linux system and learn Linux from it. I have installed Ubuntu 14.04 but  previously installed Ubuntu 16. I reverted to Ubuntu 14 because I  thought it was a problem with Ubuntu 16. I reinstalled Ubuntu 14 twice  now, first with no wireless connection and now i tried connecting using  the Ethernet cable but still no connection to the internet.
  NOTE: I'm staying on campus at university so currently im at my  computer lab as its the only place I can use the Ethernet freely.  although i keep having to go under the desk to connect the lenovo coz  the cable is short. Also I'm still searching through the net for  solutions. i will post up any updates. 

  Most suggestions I found seemed to suggest

```
sudo apt-gt update
```

  and other sudo apt-get which did not work for example, the line above would result in:

```
0% [Connecting to my.archive.ubuntu.com] [ Connecting to security.ubunu.com
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Could not resolve 'security.ubuntu.com'
```

  and so forth.
  Also tried 

```
sudo apt-get purge bcmwl-kernel-source
```   

and the result was: unable to locate package bcmwl-kernel-source
  There was another "forum"(lost the link) which had steps like  checking ifconfig, netstat -r, ping the default gateway, cat  /etc/resolv.conf and host [www.google.pl]("http://www.google.pl"). respectively those steps seem  to have positive results until host [www.google.pl]("http://www.google.pl") resulted in

```
connection timed out; no servers could be reached
```

  so now i feel like this problems seems to be situation-specific and I  really need help. here are some things you might ask me to share:

**ifconfig**
```



    eth0 Link encap:Ethernet HWaddr 08:9e:01:f6:a4:76
            inet addr:10.3.72.134 Bcast:10.3.72.255 Mask:255.255.255.0
            inet6 addr: fe80::a9e:1ff:fef6:a476/64 Scope:Link
            UP BROADCAST MULTICAST MTU:1500 Metric:1
            RX packets:3748 errors:0 dropped:0 overruns:0 frame:0
            TX packets:1666 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:318467 (318.4 KB) TX bytes:160140 (160.1KB)

    lo      Link encap:Local Loopback
            inet addr:127.0.0.1 Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING MTU:65536 Metric:1
            RX packets:1078 errors:0 dropped:0 overruns:0 frame:0
            TX packets:1078 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
           RX bytes:74422 (74.4 KB) TX bytes:74422 (74.4 KB)   

```

  [B]iwconfig
[/B]```


      lo      no wireless extension
    eth0    no wireless extension

```

[B]sudo lshw -c network
[/B]```

   *-network
        description: Network controller
        product: BCM43142 802.11b/g/n
        vendor: Broadcom Corporation
        physical id: 0
        bus info: pci@0000:01:00.0
        version: 01
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress bus_master cap_list
        configuration: driver=bcm-pci-bridge latency=0
        resources: irq:37 memory:f1300000-f1307fff
    *-network
        description: Ethernet interface
        product: RTL8111/8168/8411 PCI Gigabit Ethernet Controller
        vendor: Realtek Semiconductor Co., Ltd
        physical id: 0
        bus info: pci@0000:03:00.0
        logical info: eth0
        version: 07
        serial: 08:9e:01:f6:a4:76
        size: 100Mbit/s
        capacity: 1Gbit/s
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi msix vpd bus_master cap_list ethernet physical tp mil 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
        configuration: autonegotiation=no broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168-3_0.0.4 03/27/12 ip=10.3.72.134 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
        resources: irq:35 ioport:2000(size=256) memory:f0904000-f0904fff memory:f0900000-f0903fff

```

[B]cat /etc/network/interfaces
[/B]
```

#interfaces(5) file used by ifup(8) and ifdown(8)     
auto lo     
iface lo inet loopback 

```
  [B]UPDATE: I tried to change the above file to:
[/B]
```
      
    #interfaces(5) file used by ifup(8) and ifdown(8)     
    auto lo eth0 
    iface lo inet loopback 

    iface eth0 inet dhcp 

```  but i got : ```
Warning Calling Inhibit failed:  GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name  org.gnome.SessionManager was not provided by any .service files
```

  And then I rebooted and literally no wired connection connected. and  also said device not managed so I reverted the file to its original. So  now I have wired connection but still no internet. 


[B]nm-tool
[/B]
```

     NetworkManager Tool     State: connected (global) 
    - Device: eth0 [Wired connection 1] --------------------------------       
      Type:        Wired       
      Driver:      r8169       
      State:       connected       
      Default:     yes       
      HW Address:  08:9E:01:F6:A4:76 
      Capabilities:         
      Carrier Detect: yes         
      Speed:          100Mb/s 
      Wired Properties               
      Carrier :       on        
      IPv4 Settings: 
      Address:        10.3.72.134         
      Prefix:         24 (255.255.255.0)         
      Gateway:        10.3.72.1 
      DNS:            202.185.483.7 

```

Anything else you might need to see? Thanks in advance!

---

### Post by QIII on 2017-02-23
Hello and welcome to the Forums!

Please use formatting tags sparingly, if at all.

There was really no need for the table formatting in your post.

---

### Post by wildmanne39 on 2017-02-23
Your ethernet connection is using the wrong driver but it will still connect and usually download very very slow.

Please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
Thanks

---

### Post by aidanikuz on 2017-02-24
result from cat /etc/lsb-release; uname -a :

```

DISTRI_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"
Linux usrnm 4.4.0-31-generic #50-14.04.1-Ubuntu SMP Wed Jul 13 01:07:32 UTC 201 
6 x86_64 x86_64 GNU/Linux

```

result from [COLOR=#000000][FONT=&quot]lspci -nnk | grep -iA2 net :
[/FONT][/COLOR]
```

01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
           Subsystem: Lenovo Device [17aa:0611]
           Kernel driver in use: bcm-pci-bridge
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL811/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
           Subsystem: Lenovo Device [17aa:510c]
           Kernel driver in use: r8169

```

results for [COLOR=#000000][FONT=&quot]lsusb:

[/FONT][/COLOR]```

Bus 002 Device 002: ID 04ca:700b Lite-On Technology Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

```

result of [COLOR=#000000][FONT=&quot]iwconfig:
[/FONT][/COLOR]
```

lo      no wireless configuration
eth0  no wireless configuration

```

result of [COLOR=#000000][FONT=&quot]rfkill list all:
[/FONT][/COLOR]
```

0: tpacpi_bluetooth_sw: Bluetooth
Soft blocked: no
Hard blocked: no

1:hci0: Bluetooth
Soft blocked: no
Hard blocked: no

```

[COLOR=#000000][FONT=&quot]result of [/FONT][/COLOR][COLOR=#000000][FONT=&quot]lsmod:

[/FONT][/COLOR]```

Module                  Size  Used by
cmac                   16384  2
bnep                   20480  2
rfcomm                 69632  8
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
btusb                  45056  0
videodev              180224  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             516096  25 bnep,btbcm,btrtl,btusb,rfcomm,btintel
media                  24576  2 uvcvideo,videodev
snd_hda_codec_realtek    86016  1
amd_freq_sensitivity    16384  0
kvm                   532480  0
amdkfd                131072  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
amd_iommu_v2           20480  1 amdkfd
snd_hda_codec_hdmi     53248  1
radeon               1503232  3
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
aesni_intel           167936  2
snd_hwdep              16384  1 snd_hda_codec
ttm                    94208  1 radeon
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
joydev                 20480  0
input_leds             16384  0
serio_raw              16384  0
rtsx_pci_ms            20480  0
bcma                   53248  0
drm_kms_helper        143360  1 radeon
memstick               20480  1 rtsx_pci_ms
edac_mce_amd           24576  0
edac_core              53248  0
k10temp                16384  0
snd_seq_midi           16384  0
drm                   360448  42 ttm,drm_kms_helper,radeon
fam15h_power           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
thinkpad_acpi          90112  1
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
wmi                    20480  0
nvram                  16384  1 thinkpad_acpi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
i2c_piix4              24576  0
shpchp                 36864  0
i2c_algo_bit           16384  1 radeon
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
soundcore              16384  1 snd
sysimgblt              16384  1 drm_kms_helper
video                  40960  1 thinkpad_acpi
parport_pc             36864  0
mac_hid                16384  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         24576  0
psmouse               122880  0
ahci                   36864  2
r8169                  81920  0
libahci                32768  1 ahci
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    16384  1 r8169
fjes                   28672  0

 

```[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]

---

### Post by wildmanne39 on 2017-02-24
Your Broadcom 14e4:4355 uses bcmwl-kernel-source. It and its dependency dkms are on the installation DVD or USB. Insert the install media and navigate to pool > restricted > b > bcmwl and drag and drop the bcmwl deb package to your desktop. Do the same with pool > main > d > dkms. Now we install the deb files. Open a terminal then do:
```
cd ~/Desktop
sudo dpkg -i *.deb
sudo modprobe wl
```
For the ethernet connection download the driver:
[https://media-cdn.ubuntu-de.org/forum/attachments/49/47/3005217-r8168-dkms-8.043.02.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/49/47/3005217-r8168-dkms-8.043.02.tar.gz)

This is assuming you have an internet connection after installing the wifi driver if not you can tether you cell phone to install the correct driver, then do:
```
sudo tar xvf ~/Downloads/3005217-r8168-dkms-8.043.02.tar.gz -C /usr/src
sudo dkms add -m r8168 -v 8.043.02
sudo dkms build -m r8168 -v 8.043.02
sudo dkms install -m r8168 -v 8.043.02
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot now both should be working.

Ethernet directions came from here:
[https://ubuntuforums.org/showthread.php?t=2346935](https://ubuntuforums.org/showthread.php?t=2346935)

---

### Post by aidanikuz on 2017-02-24
Thank you. I did the first step, result:

```

Selecting previously unselected package dkms.
(Reading database ... 166759 files and directories currently installed.)
Preparing to unpack dkms_2.2.0.3-1.1ubuntu5.14.04.7_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04.7) ...
Setting up dkms (2.2.0.3-1.1ubuntu5.14.04.7) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...

```

Then i tried sudo modprobe wl result:

```

modeprobe: FATAL: modue wl not found

```

**i guess the wifi part failed.**

so I just continued with the next step for ethernet and downloaded the file on a different laptop and used the USB to place it on my Desktop, result:

```

r8168.8.043.02/src/Makefile
r8168.8.043.02/src/rtl_eeprom.h
r8168.8.043.02/
r8168.8.043.02/src/r8168_fibre.h
r8168.8.043.02/src/rtl_eeprom.c
r8168.8.043.02/autorun.sh
r8168.8.043.02/src/r8168_n.c
r8168.8.043.02/src/rtltool.h
r8168.8.043.02/dkms.conf
r8168.8.043.02/Makefile
r8168.8.043.02/src/Makefile_linux24x
r8168.8.043.02/src/r8168.h
r8168.8.043.02/src/r8168_realwow.h
r8168.8.043.02/src/rtltool.c
r8168.8.043.02/src/r8168_dash.h
r8168.8.043.02/src/r8168_asf.h
r8168.8.043.02/src/
r8168.8.043.02/REAME
r8168.8.043.02/src/r8168_asf.c

```

sudo dkms add -m r8168 -v 8.043.02, result: [B]DKMS: add completed

[/B]sudo dkms build -m r8168 -v 8.043.02, result: [B]DKMS: build completed

[/B]sudo dkms install -m r8168 -v 8.043.02, result: [B]DKMS: install completed

[/B]sudo depmod -a , no error displayed so it ran well i guess then, sudo update-initramfs -u : [B]update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic

[/B]echo "blacklist "r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf : **blacklist r8169**


unfortunately, i don't have access to en ethernet cable at the moment to test it out. I will update on the ethernet connection once I get access to it.

---

### Post by wildmanne39 on 2017-02-25
For your wifi it looks like you missed the first step:
> insert the install media and navigate to pool > restricted > b > bcmwl and drag and drop the bcmwl deb package to your desktop.
I am not sure but you may have to run dkms procedure again, that is the package that rebuilds the driver each time there is a kernel update so with it being installed first it is likely it will not be part of the driver and you will lose wifi as soon as the kernel is updated.

From what I see it looks like the ehternet driver was installed correctly.

---

### Post by aidanikuz on 2017-02-26
Hi! yes i did miss that step. I'm sorry. 

Anyway, thank you so much now i can connect to the internet by wifi though really slow connection but I think that's because of the wifi im connected to. The ethernet though keeps searching, the internet signal thing keeps blinking and keeps disconnecting. Can i delete the files on the desktop or move it into a different location?

---

### Post by wildmanne39 on 2017-02-26
Yes you can delete them. Please mark this thread solved and start a new one for the ethernet connection.
Glad the wireless is working.

Make sure your ethernet connection is unplugged.

---

### Post by aidanikuz on 2017-02-27
Okay. thanks again!

---

