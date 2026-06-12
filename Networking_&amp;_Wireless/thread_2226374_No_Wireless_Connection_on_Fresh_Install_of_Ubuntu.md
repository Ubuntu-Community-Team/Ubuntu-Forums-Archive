---
title: "No Wireless Connection on Fresh Install of Ubuntu"
date: 2014-05-26
forum: Networking &amp; Wireless
---

### Post by marton3 on 2014-05-26
Hi. 
I freshly installed Ubuntu, current version, on my new Acer Aspire M5-583p-6423. However, I have found that there is no wireless connections available, and I can't even enable wifi. I seem to be missing a driver? Can anyone help?

Here is my sudo lshw -C network terminal: 
```
*-network UNCLAIMED     
       description: Network controller
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b0600000-b0607fff memory:b0400000-b05fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:05:00.1
       logical name: eth0
       version: 14
       serial: 08:9e:01:f2:52:63
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-2_0.0.1 07/08/13 ip=192.168.1.14 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:62 ioport:3000(size=256) memory:b0704000-b0704fff memory:b0700000-b0703fff
```

---

### Post by Hadaka on 2014-05-26
hi, please post the output of..
```
lspci -nnk | grep -iA2 net
rfkill list all
lsmod
grep -v lp /etc/motd
```
thsnks.

---

### Post by marton3 on 2014-05-27
```
marton@marton-Aspire-M5-583P:~$ lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Lite-On Communications Inc Device [11ad:6606]
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5287] (rev 01)
--
05:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 14)
    Subsystem: Acer Incorporated [ALI] Device [1025:079b]
    Kernel driver in use: r8169
marton@marton-Aspire-M5-583P:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
marton@marton-Aspire-M5-583P:~$ lsmod
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_realtek    61438  1 
hid_multitouch         17407  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
joydev                 17381  0 
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
snd_rawmidi            30144  1 snd_seq_midi
acer_wmi               32522  0 
intel_powerclamp       14705  0 
sparse_keymap          13948  1 acer_wmi
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
gf128mul               14951  1 lrw
snd_timer              29482  2 snd_pcm,snd_seq
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               102222  0 
serio_raw              13462  0 
lpc_ich                21080  0 
i915                  783485  5 
rtsx_pci_ms            18151  0 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
memstick               16966  1 rtsx_pci_ms
parport_pc             32701  0 
mei_me                 18627  0 
mei                    82274  1 mei_me
soundcore              12680  1 snd
ppdev                  17671  0 
drm_kms_helper         52758  1 i915
drm                   302817  4 i915,drm_kms_helper
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
i2c_algo_bit           13413  1 i915
video                  19476  2 i915,acer_wmi
wmi                    19177  1 acer_wmi
mac_hid                13205  0 
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  3 hid_multitouch,hid_generic,usbhid
rtsx_pci_sdmmc         23274  0 
ahci                   25819  3 
r8169                  67581  0 
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
libahci                32168  1 ahci
mii                    13934  1 r8169
marton@marton-Aspire-M5-583P:~$ grep -v lp /etc/motd
grep: /etc/motd: No such file or directory
marton@marton-Aspire-M5-583P:~$ 


```

---

### Post by Hadaka on 2014-05-27
hi,please open a terminal..ctrl/alt/t and do
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
thanks.

---

### Post by marton3 on 2014-05-27
Doesn't look like it did anything... 
```
marton@marton-Aspire-M5-583P:~$ sudo apt-get update
[sudo] password for marton: 
mSorry, try again.
[sudo] password for marton: 
Sorry, try again.
[sudo] password for marton: 
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://security.ubuntu.com trusty-security InRelease                  
Ign http://us.archive.ubuntu.com trusty-updates InRelease                  
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]       
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Get:2 http://security.ubuntu.com trusty-security Release [58.5 kB]
Ign http://extras.ubuntu.com trusty InRelease                                 
Get:3 http://us.archive.ubuntu.com trusty Release.gpg [933 B]                 
Get:4 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Get:5 http://us.archive.ubuntu.com trusty-backports Release.gpg [933 B]        
Get:6 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Get:7 http://us.archive.ubuntu.com trusty Release [58.5 kB]                    
Get:8 http://extras.ubuntu.com trusty Release [11.9 kB]                        
Get:9 http://security.ubuntu.com trusty-security/main Sources [16.0 kB]        
Get:10 http://security.ubuntu.com trusty-security/restricted Sources [14 B]    
Get:11 http://extras.ubuntu.com trusty/main Sources [14 B]                     
Get:12 http://us.archive.ubuntu.com trusty-updates Release [58.5 kB]           
Get:13 http://security.ubuntu.com trusty-security/universe Sources [4,212 B]   
Get:14 http://security.ubuntu.com trusty-security/multiverse Sources [687 B]   
Get:15 http://security.ubuntu.com trusty-security/main amd64 Packages [51.8 kB]
Get:16 http://extras.ubuntu.com trusty/main amd64 Packages [14 B]              
Get:17 http://us.archive.ubuntu.com trusty-backports Release [58.6 kB]         
Get:18 http://extras.ubuntu.com trusty/main i386 Packages [14 B]               
Get:19 http://security.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Get:20 http://us.archive.ubuntu.com trusty/main Sources [1,064 kB]             
Get:21 http://security.ubuntu.com trusty-security/universe amd64 Packages [17.9 kB]
Get:22 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [1,154 B]
Get:23 http://security.ubuntu.com trusty-security/main i386 Packages [49.4 kB] 
Ign https://private-ppa.launchpad.net trusty InRelease                         
Get:24 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:25 http://security.ubuntu.com trusty-security/universe i386 Packages [17.9 kB]
Get:26 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,404 B]
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Get:27 http://security.ubuntu.com trusty-security/main Translation-en [24.4 kB]
Get:28 http://security.ubuntu.com trusty-security/multiverse Translation-en [587 B]
Get:29 http://security.ubuntu.com trusty-security/restricted Translation-en [14 B]
Hit https://private-ppa.launchpad.net trusty Release                           
Get:30 http://us.archive.ubuntu.com trusty/restricted Sources [5,433 B]        
Get:31 http://security.ubuntu.com trusty-security/universe Translation-en [9,065 B]
Get:32 http://us.archive.ubuntu.com trusty/universe Sources [6,399 kB]         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Ign http://security.ubuntu.com trusty-security/main Translation-en_US
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US
Get:33 http://us.archive.ubuntu.com trusty/multiverse Sources [174 kB]
Get:34 http://us.archive.ubuntu.com trusty/main amd64 Packages [1,350 kB]
Get:35 http://us.archive.ubuntu.com trusty/restricted amd64 Packages [13.0 kB]
Get:36 http://us.archive.ubuntu.com trusty/universe amd64 Packages [5,859 kB]
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US
Ign https://private-ppa.launchpad.net trusty/main Translation-en
Get:37 http://us.archive.ubuntu.com trusty/multiverse amd64 Packages [132 kB]
Get:38 http://us.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]       
Get:39 http://us.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]  
Get:40 http://us.archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]   
Get:41 http://us.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]   
Get:42 http://us.archive.ubuntu.com trusty/main Translation-en [762 kB]        
Get:43 http://us.archive.ubuntu.com trusty/multiverse Translation-en [102 kB]  
Get:44 http://us.archive.ubuntu.com trusty/restricted Translation-en [3,457 B] 
Get:45 http://us.archive.ubuntu.com trusty/universe Translation-en [4,089 kB]  
Get:46 http://us.archive.ubuntu.com trusty-updates/main Sources [45.7 kB]      
Get:47 http://us.archive.ubuntu.com trusty-updates/restricted Sources [14 B]   
Get:48 http://us.archive.ubuntu.com trusty-updates/universe Sources [28.2 kB]  
Get:49 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [2,234 B]
Get:50 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [109 kB]
Get:51 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [14 B]
Get:52 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [74.9 kB]
Get:53 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [7,089 B]
Get:54 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [107 kB] 
Get:55 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [14 B]
Get:56 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [75.3 kB]
Get:57 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [7,273 B]
Get:58 http://us.archive.ubuntu.com trusty-updates/main Translation-en [51.2 kB]
Get:59 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [3,811 B]
Get:60 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [14 B]
Get:61 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [33.8 kB]
Get:62 http://us.archive.ubuntu.com trusty-backports/main Sources [14 B]       
Get:63 http://us.archive.ubuntu.com trusty-backports/restricted Sources [14 B] 
Get:64 http://us.archive.ubuntu.com trusty-backports/universe Sources [4,123 B]
Get:65 http://us.archive.ubuntu.com trusty-backports/multiverse Sources [768 B]
Get:66 http://us.archive.ubuntu.com trusty-backports/main amd64 Packages [14 B]
Get:67 http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages [14 B]
Get:68 http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages [4,099 B]
Get:69 http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [619 B]
Get:70 http://us.archive.ubuntu.com trusty-backports/main i386 Packages [14 B] 
Get:71 http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages [14 B]
Get:72 http://us.archive.ubuntu.com trusty-backports/universe i386 Packages [4,114 B]
Get:73 http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages [619 B]
Get:74 http://us.archive.ubuntu.com trusty-backports/main Translation-en [14 B]
Get:75 http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en [307 B]
Get:76 http://us.archive.ubuntu.com trusty-backports/restricted Translation-en [14 B]
Get:77 http://us.archive.ubuntu.com trusty-backports/universe Translation-en [2,506 B]
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com trusty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com trusty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com trusty-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com trusty-backports/main Translation-en_US       
Ign http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com trusty-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com trusty-backports/universe Translation-en_US   
Fetched 28.3 MB in 14s (1,941 kB/s)                                            
Reading package lists... Done


```

I'm unsure if it installed after downloading the package. Did the terminal not run the rest of the commands?

---

### Post by Hadaka on 2014-05-27
Hi, yes it ran the updates, ,there were 3 lines of code to run
they should be entered one line at a time in the terminal, you have
2 more lines to run. open a terminal ctrl/alt/t and do
one line at a time
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl

```

---

### Post by marton3 on 2014-05-27
```
marton@marton-Aspire-M5-583P:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for marton: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot libfakeroot
Suggested packages:
  dpkg-dev debhelper
The following NEW packages will be installed:
  bcmwl-kernel-source dkms fakeroot libfakeroot
0 upgraded, 4 newly installed, 0 to remove and 185 not upgraded.
Need to get 1,271 kB of archives.
After this operation, 6,564 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main dkms all 2.2.0.3-1.1ubuntu5 [64.4 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/restricted bcmwl-kernel-source amd64 6.30.223.141+bdcom-0ubuntu2 [1,126 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty/main libfakeroot amd64 1.20-3ubuntu2 [25.4 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty/main fakeroot amd64 1.20-3ubuntu2 [55.0 kB]
Fetched 1,271 kB in 1s (887 kB/s)  
Selecting previously unselected package dkms.
(Reading database ... 163222 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5) ...
Selecting previously unselected package bcmwl-kernel-source.
Preparing to unpack .../bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../libfakeroot_1.20-3ubuntu2_amd64.deb ...
Unpacking libfakeroot:amd64 (1.20-3ubuntu2) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../fakeroot_1.20-3ubuntu2_amd64.deb ...
Unpacking fakeroot (1.20-3ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up dkms (2.2.0.3-1.1ubuntu5) ...
Setting up bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Loading new bcmwl-6.30.223.141+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-24-generic
Building for architecture x86_64
Building initial module for 3.13.0-24-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-24-generic/updates/dkms/

depmod......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up libfakeroot:amd64 (1.20-3ubuntu2) ...
Setting up fakeroot (1.20-3ubuntu2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Processing triggers for initramfs-tools (0.103ubuntu4) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
marton@marton-Aspire-M5-583P:~$ sudo modprobe wl
marton@marton-Aspire-M5-583P:~$ 


```

And it worked! Thank-you so much! You are the kind of person that restores my faith in humanity, spending countless hours on a forum helping people you don't even know. Thank you so much, again!

---

### Post by Hadaka on 2014-05-27
you are welcome, thank you for the kind words
i am pleased that worked for you.
please take the time to mark this thread SOLVED
How to->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

