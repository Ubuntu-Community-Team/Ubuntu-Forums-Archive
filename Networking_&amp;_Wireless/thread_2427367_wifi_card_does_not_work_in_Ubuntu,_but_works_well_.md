---
title: "wifi card does not work in Ubuntu, but works well under W10."
date: 2019-09-21
forum: Networking &amp; Wireless
---

### Post by ortollj on 2019-09-21
Hi
 
 
 PC :TOSHIBA SATELLITE-C70-B, 
OS:UBUNTU 18.04
  
 UBUNTU is installed in dual boot on my Toshiba PC. I made the installation of UBUNTU with a wired connection, wanting to use my PC in the garden, I realized that my wifi card was not detected, my wifi card does not work in Ubuntu, but works well under W10.

 
 
 
 
 ```
ortollj@ortollj-SATELLITE-C70-B:~$  wget -N -t 5 -T 10 https://framagit.org/cracolinux/wificheck/raw/master/wificheck && chmod +x wificheck && ./wificheck

 --2019-09-21 09:52:20--  https://framagit.org/cracolinux/wificheck/raw/master/wificheck
 Resolving framagit.org (framagit.org)... 2a01:4f8:200:1302::42, 144.76.206.42
 Connecting to framagit.org (framagit.org)|2a01:4f8:200:1302::42|:443... connected.
 HTTP request sent, awaiting response... 200 OK
 Length: 2026 (2,0K) [text/plain]
 Saving to: ‘wificheck’
 
 
 wificheck           100%[===================>]   1,98K  --.-KB/s    in 0s       
 
 
 Last-modified header missing -- time-stamps turned off.
 2019-09-21 09:52:20 (104 MB/s) - ‘wificheck’ saved [2026/2026]
 
 
 [sudo] password for ortollj:  
 enp1s0    no wireless extensions.
 
 
 lo        no wireless extensions.
 
 
 ./wificheck: line 58: ifconfig: command not found
 enp1s0    Interface doesn't support scanning.
 
 
 lo        Interface doesn't support scanning.
 
 
 ./wificheck: line 74: nm-tool: command not found
 Error: argument 'status' not understood. Try passing --help instead.
 Le fichier wificheck.log a été crée dans /home/ortollj
 Vous n'avez plus qu'à copier/coller son contenu sur le forum
  accès &#8594;&#8594; file://home/ortollj/wificheck.log
 ortollj@ortollj-SATELLITE-C70-B:~$ lspci -nn | grep -i network
 07:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
 ortollj@ortollj-SATELLITE-C70-B:~$ lspci -nnk | grep -i network -A 3
 07:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
     Subsystem: Lite-On Communications Inc BCM43142 802.11b/g/n [11ad:6655]
 08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)
     Subsystem: Toshiba America Info Systems RTS5229 PCI Express Card Reader [1179:ff1e]
 ortollj@ortollj-SATELLITE-C70-B:~$ ip a
 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
     inet 127.0.0.1/8 scope host lo
        valid_lft forever preferred_lft forever
     inet6 ::1/128 scope host  
        valid_lft forever preferred_lft forever
 2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
     link/ether 00:8c:fa:8b:81:21 brd ff:ff:ff:ff:ff:ff
     inet 192.168.0.28/24 brd 192.168.0.255 scope global dynamic noprefixroute enp1s0
        valid_lft 42765sec preferred_lft 42765sec
     inet6 2a01:e0a:99:2420:71f1:ff4b:df07:b652/64 scope global temporary dynamic  
        valid_lft 85964sec preferred_lft 85712sec
     inet6 2a01:e0a:99:2420:cef4:9398:de42:fea8/64 scope global dynamic mngtmpaddr noprefixroute  
        valid_lft 85964sec preferred_lft 85964sec
     inet6 fe80::78bb:62a5:c1a9:f988/64 scope link noprefixroute  
        valid_lft forever preferred_lft forever
 ortollj@ortollj-SATELLITE-C70-B:~$ dmesg | grep firmware
 [    0.162332] Spectre V2 : Enabling Restricted Speculation for firmware calls
 [  252.681690] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-0930-0225.hcd failed with error -2
 [ 1184.410592] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-0930-0225.hcd failed with error -2
 [ 1216.712631] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-0930-0225.hcd failed with error -2
 [ 1247.306241] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-0930-0225.hcd failed with error -2
 ortollj@ortollj-SATELLITE-C70-B:~$ apt-cache search BCM43142A0-0930-0225.hcd
 ortollj@ortollj-SATELLITE-C70-B:~$  

```

---

### Post by pcfan1234 on 2019-09-21
Install Broadcom-STA: ```
sudo apt-get install bcmwl-kernel-source 


```

---

### Post by coffeecat on 2019-09-21
*Thread moved to **Networking & Wireless**.*

@ortollj, I've edited your post to restore the default font size. Please use default font properties, except for highlighting purposes. The font size you chose for your post was so tiny that it was difficult to read.

---

### Post by ortollj on 2019-09-21
@coffeecat, ok

@pcfan1234:

```
ortollj@ortollj-SATELLITE-C70-B:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for ortollj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-wine libwine libwine:i386 wine32:i386 wine64
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  dkms
Suggested packages:
  menu
The following NEW packages will be installed:
  bcmwl-kernel-source dkms
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
Need to get 1&#8239;618 kB of archives.
After this operation, 8&#8239;357 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 dkms all 2.3-3ubuntu9.5 [68,1 kB]
Get:2 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/restricted amd64 bcmwl-kernel-source amd64 6.30.223.271+bdcom-0ubuntu4 [1&#8239;550 kB]
Fetched 1&#8239;618 kB in 2s (886 kB/s)                    
Selecting previously unselected package dkms.
(Reading database ... 179052 files and directories currently installed.)
Preparing to unpack .../dkms_2.3-3ubuntu9.5_all.deb ...
Unpacking dkms (2.3-3ubuntu9.5) ...
Selecting previously unselected package bcmwl-kernel-source.
Preparing to unpack .../bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Setting up dkms (2.3-3ubuntu9.5) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.0.0-29-generic
Building for architecture x86_64
Building initial module for 5.0.0-29-generic
Can't load /var/lib/shim-signed/mok/.rnd into RNG
140202166841792:error:2406F079:random number generator:RAND_load_file:Cannot open file:../crypto/rand/randfile.c:88:Filename=/var/lib/shim-signed/mok/.rnd
Generating a RSA private key
........................+++++
...................................................................................................................................................+++++
writing new private key to '/var/lib/shim-signed/mok/MOK.priv'
-----
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-29-generic/updates/dkms/

depmod.........................

DKMS: install completed.
modprobe: ERROR: could not insert 'wl': Operation not permitted
update-initramfs: deferring update (trigger activated)
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for initramfs-tools (0.130ubuntu3.8) ...
update-initramfs: Generating /boot/initrd.img-5.0.0-29-generic
ortollj@ortollj-SATELLITE-C70-B:~$
```

---

### Post by ortollj on 2019-09-21
I need help for this message:

modprobe: ERROR: could not insert 'wl': Operation not permitted
.
I copy the wifilog below maybe there is information usefull ?

```
 
>>    cat /etc/lsb-release 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.3 LTS"

>>    lsusb 

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0930:0225 Toshiba Corp. 
Bus 002 Device 003: ID 04f2:b448 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

>>    lspci -k -nn | grep -A 3 -i net 

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Toshiba America Info Systems RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1179:ff1e]
    Kernel driver in use: r8169
    Kernel modules: r8169
07:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lite-On Communications Inc BCM43142 802.11b/g/n [11ad:6655]
    Kernel modules: wl
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)

>>    sudo lshw -C network 

  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 0c
       serial: 00:8c:fa:8b:81:21
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.0.28 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:4000(size=256) memory:c3000000-c3000fff memory:c3100000-c3103fff
  *-network UNCLAIMED
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:c3400000-c3407fff

>>    lsmod | sort 

acpi_pad              184320  0
aesni_intel           372736  2
aes_x86_64             20480  1 aesni_intel
ahci                   40960  2
amdgpu               3497984  1
amd_iommu_v2           20480  1 amdgpu
autofs4                45056  2
bluetooth             557056  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm
bnep                   24576  2
btbcm                  16384  1 btusb
btintel                24576  1 btusb
btrtl                  20480  1 btusb
btusb                  49152  0
cfg80211              675840  0
chash                  16384  1 amdgpu
cmac                   16384  1
coretemp               20480  0
crc32_pclmul           16384  0
crct10dif_pclmul       16384  1
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
crypto_simd            16384  1 aesni_intel
drm                   479232  19 gpu_sched,drm_kms_helper,amdgpu,i915,ttm
drm_kms_helper        180224  2 amdgpu,i915
ecdh_generic           28672  2 bluetooth
fb_sys_fops            16384  1 drm_kms_helper
ghash_clmulni_intel    16384  0
glue_helper            16384  1 aesni_intel
gpu_sched              32768  1 amdgpu
hid                   126976  2 usbhid,hid_generic
hid_generic            16384  0
i2c_algo_bit           16384  2 amdgpu,i915
i915                 1818624  22
industrialio           73728  1 toshiba_acpi
input_leds             16384  0
intel_cstate           20480  0
intel_powerclamp       20480  0
intel_rapl             24576  0
intel_rapl_perf        16384  0
ip_tables              32768  0
irqbypass              16384  1 kvm
joydev                 28672  0
kvm                   626688  2 kvmgt,kvm_intel
kvmgt                  28672  0
kvm_intel             237568  0
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
libahci                32768  1 ahci
lp                     20480  0
lpc_ich                24576  0
mac_hid                16384  0
mdev                   24576  2 kvmgt,vfio_mdev
media                  53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
mei                   102400  1 mei_me
mei_me                 40960  0
memstick               20480  1 rtsx_pci_ms
Module                  Size  Used by
nls_iso8859_1          16384  1
parport                53248  3 parport_pc,lp,ppdev
parport_pc             36864  0
ppdev                  24576  0
psmouse               151552  0
r8169                  81920  0
realtek                20480  0
rfcomm                 77824  4
rtsx_pci               61440  2 rtsx_pci_sdmmc,rtsx_pci_ms
rtsx_pci_ms            24576  0
rtsx_pci_sdmmc         28672  0
sch_fq_codel           20480  2
serio_raw              20480  0
snd                    86016  31 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek   114688  1
snd_hda_core           86016  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hda_intel          40960  10
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_timer              36864  2 snd_seq,snd_pcm
soundcore              16384  1 snd
sparse_keymap          16384  1 toshiba_acpi
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
toshiba_acpi           49152  0
toshiba_bluetooth      20480  0
ttm                   102400  1 amdgpu
usbhid                 53248  0
uvcvideo               94208  0
vfio                   32768  3 kvmgt,vfio_mdev,vfio_iommu_type1
vfio_iommu_type1       28672  0
vfio_mdev              16384  0
video                  49152  2 toshiba_acpi,i915
videobuf2_common       45056  2 videobuf2_v4l2,uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_vmalloc      20480  1 uvcvideo
videodev              200704  3 videobuf2_v4l2,uvcvideo,videobuf2_common
wmi                    28672  1 toshiba_acpi
x86_pkg_temp_thermal    20480  0
x_tables               40960  1 ip_tables

```
```


>>    iwconfig 


>>    ifconfig -a 


>>    sudo iwlist scan 


>>    uname -r -m 

5.0.0-29-generic x86_64

>>    cat /etc/network/interfaces 

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

>>    nm-tool 


>>    nmcli dev wifi 


>>    nmcli connection list (< 15.04) ou nmcli connection show (>= 15.04) 

NAME                UUID                                  TYPE      DEVICE 
Wired connection 1  7ac0980e-8e92-3c7b-84a2-855364b7e754  ethernet  enp1s0 

>>    nmcli connection status 


>>    sudo rfkill list 

0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
 
```

---

### Post by jeremy31 on 2019-09-22
I think you will need to disable Secure Boot in BIOS settings, check ```
mokutil --sb-state
```

---

### Post by ortollj on 2019-09-23
Ok jeremy , you are right (however, I was sure to have it disabled !)

```
ortollj@ortollj-SATELLITE-C70-B:~$ mokutil --sb-state
SecureBoot enabled
```

Thanks, I'm gonna disabled it, and I tell you the result.

---

### Post by ortollj on 2019-09-23
seems much better now !


```
wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-29-generic/updates/dkms/

depmod........

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for initramfs-tools (0.130ubuntu3.8) ...
update-initramfs: Generating /boot/initrd.img-5.0.0-29-generic
ortollj@ortollj-SATELLITE-C70-B:~$
```

---

### Post by ortollj on 2019-09-23
The wifi is ok now, Thanks a lot to every one !!!!!!. Special thank to jeremy31.

sorry to have been a little heavy about  this f.. secure boot UEFI.

---

