---
title: "Wifi will not connect"
date: 2016-09-14
forum: Networking &amp; Wireless
---

### Post by Joe_Misseri on 2016-09-14
> **Wild Man said:**
> Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

I'm having my own issue that sounds similar. 

Everything was honky dory until I did out-of-normal security update for Ubuntu that I'm presuming effected my kernal/wireless driver compatibility,etc.

I've been running Ubuntu 14.04 for some time with no major errors but have had some wireless issues in the past. Long-story-short, I'm going to follow your wireless script directions and past the findings below, lastly -- since my wireless has went down, I do not have connection to the internet via ethernet/cable, etc:

```
jm@jm-Aspire-5750G:~$ sudo apt-get update
[sudo] password for jm: 
Err http://security.ubuntu.com trusty-security InRelease
  
Err http://extras.ubuntu.com trusty InRelease
  
Err http://archive.getdeb.net trusty-getdeb InRelease
  
Err http://security.ubuntu.com trusty-security Release.gpg                  
  Could not resolve 'security.ubuntu.com'
Err http://archive.getdeb.net trusty-getdeb Release.gpg                     
  Could not resolve 'archive.getdeb.net'
Err http://extras.ubuntu.com trusty Release.gpg                                
  Could not resolve 'extras.ubuntu.com'
Err http://toolbelt.heroku.com ./ InRelease                                    
  
Err http://toolbelt.heroku.com ./ Release.gpg                                  
  Could not resolve 'toolbelt.heroku.com'
Err http://us.archive.ubuntu.com trusty InRelease                             
  
Err http://us.archive.ubuntu.com trusty-updates InRelease                     
  
Err http://us.archive.ubuntu.com trusty-backports InRelease                   
  
Err http://archive.canonical.com trusty InRelease                             
  
Err http://repo.sinew.in stable InRelease                                     
  
Err http://dl.google.com stable InRelease                                     
  
Err http://dl.google.com stable InRelease                                     
  
Err http://us.archive.ubuntu.com trusty Release.gpg                           
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com trusty-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://archive.canonical.com trusty Release.gpg
  Could not resolve 'archive.canonical.com'
Err http://dl.google.com stable Release.gpg
  Could not resolve 'dl.google.com'
Err http://ppa.launchpad.net trusty InRelease
  
Err http://ppa.launchpad.net trusty InRelease
  
Err http://ppa.launchpad.net trusty InRelease
  
Err http://repo.sinew.in stable Release.gpg
  Could not resolve 'repo.sinew.in'
Err http://us.archive.ubuntu.com trusty-backports Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://ppa.launchpad.net trusty InRelease
  
Err http://ppa.launchpad.net trusty InRelease
  
Err http://ppa.launchpad.net trusty InRelease
  
Err http://dl.google.com stable Release.gpg
  Could not resolve 'dl.google.com'
Err http://ppa.launchpad.net trusty Release.gpg
  Could not resolve 'ppa.launchpad.net'
Err http://ppa.launchpad.net trusty Release.gpg
  Could not resolve 'ppa.launchpad.net'
Err http://ppa.launchpad.net trusty Release.gpg
  Could not resolve 'ppa.launchpad.net'
Err http://ppa.launchpad.net trusty Release.gpg
  Could not resolve 'ppa.launchpad.net'
Err http://ppa.launchpad.net trusty Release.gpg
  Could not resolve 'ppa.launchpad.net'
Err http://ppa.launchpad.net trusty Release.gpg
  Could not resolve 'ppa.launchpad.net'
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/brightbox/ruby-ng/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/chris-lea/node.js/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://repo.sinew.in/dists/stable/InRelease  

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/trusty-getdeb/InRelease  

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/InRelease  

W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/InRelease  

W: Failed to fetch http://toolbelt.heroku.com/ubuntu/./InRelease  

W: Failed to fetch http://ppa.launchpad.net/kilian/f.lux/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/nginx/stable/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/noobslab/icons/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/videolan/stable-daily/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/trusty-getdeb/Release.gpg  Could not resolve 'archive.getdeb.net'

W: Failed to fetch http://toolbelt.heroku.com/ubuntu/./Release.gpg  Could not resolve 'toolbelt.heroku.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://repo.sinew.in/dists/stable/Release.gpg  Could not resolve 'repo.sinew.in'

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Could not resolve 'dl.google.com'

W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg  Could not resolve 'dl.google.com'

W: Failed to fetch http://ppa.launchpad.net/brightbox/ruby-ng/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/chris-lea/node.js/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/kilian/f.lux/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/nginx/stable/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/noobslab/icons/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/videolan/stable-daily/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net'

W: Some index files failed to download. They have been ignored, or old ones used instead.
jm@jm-Aspire-5750G:~$ 
jm@jm-Aspire-5750G:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apache2-bin apache2-doc apache2-utils bcmwl-kernel-source dkms libcgmanager0
  libcgmanager0:i386 libmm-glib0 libnautilus-extension1a libunity-core-6.0-9
  nautilus nautilus-data unity unity-services yelp-xsl
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,172 kB of archives.
After this operation, 381 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y       
WARNING: The following packages cannot be authenticated!
  libmm-glib0 libcgmanager0:i386 libcgmanager0 apache2-bin apache2-doc
  apache2-utils dkms bcmwl-kernel-source libnautilus-extension1a unity
  libunity-core-6.0-9 unity-services nautilus-data nautilus yelp-xsl
Install these packages without verification? [y/N] y
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libmm-glib0 amd64 1.0.0-2ubuntu1.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-backports/main libcgmanager0 i386 0.39-2ubuntu2~ubuntu14.04.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-backports/main libcgmanager0 amd64 0.39-2ubuntu2~ubuntu14.04.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-backports/main apache2-bin amd64 2.4.10-1ubuntu1.1~ubuntu14.04.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-backports/main apache2-doc all 2.4.10-1ubuntu1.1~ubuntu14.04.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-backports/main apache2-utils amd64 2.4.10-1ubuntu1.1~ubuntu14.04.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main dkms all 2.2.0.3-1.1ubuntu5.14.04.7
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/restricted bcmwl-kernel-source amd64 6.30.223.248+bdcom-0ubuntu0.2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libnautilus-extension1a amd64 1:3.10.1-0ubuntu9.11
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main unity amd64 7.2.6+14.04.20160408-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libunity-core-6.0-9 amd64 7.2.6+14.04.20160408-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main unity-services amd64 7.2.6+14.04.20160408-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus-data all 1:3.10.1-0ubuntu9.11
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus amd64 1:3.10.1-0ubuntu9.11
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-backports/main yelp-xsl all 3.12.0-1~ubuntu14.04.1
  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/modemmanager/libmm-glib0_1.0.0-2ubuntu1.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cgmanager/libcgmanager0_0.39-2ubuntu2~ubuntu14.04.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cgmanager/libcgmanager0_0.39-2ubuntu2~ubuntu14.04.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-bin_2.4.10-1ubuntu1.1~ubuntu14.04.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-doc_2.4.10-1ubuntu1.1~ubuntu14.04.1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.4.10-1ubuntu1.1~ubuntu14.04.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5.14.04.7_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.2_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1a_3.10.1-0ubuntu9.11_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity/unity_7.2.6+14.04.20160408-0ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity/libunity-core-6.0-9_7.2.6+14.04.20160408-0ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity/unity-services_7.2.6+14.04.20160408-0ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_3.10.1-0ubuntu9.11_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_3.10.1-0ubuntu9.11_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/y/yelp-xsl/yelp-xsl_3.12.0-1~ubuntu14.04.1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
jm@jm-Aspire-5750G:~$ 
```

***NOTE:  I followed your your 'wireless-info.txt' instructions but hit bust  in terms of making the file Run and creating a new file. I checkboxed to execute and ran it via right-click but after a couple seconds idle.... nothing.

I did gather this for you though, if helpful?


```
$ 

jm@jm-Aspire-5750G:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 520M] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader (rev 10)
02:00.2 System peripheral: Broadcom Corporation BCM57765/57785 MS Card Reader (rev 10)
02:00.3 System peripheral: Broadcom Corporation BCM57765/57785 xD-Picture Card Reader (rev 10)
03:00.0 Network controller: Broadcom Corporation BCM43227 802.11b/g/n
jm@jm-Aspire-5750G:~$ sudo lshw -C network
[sudo] password for jm: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: b8:70:f4:df:3b:f2
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=sb latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:d1830000-d183ffff memory:d1840000-d184ffff memory:9fb00000-9fb007ff
  *-network UNCLAIMED
       description: Network controller
       product: BCM43227 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d1900000-d1903fff
```

---

### Post by wildmanne39 on 2016-09-15
Thread moved to your on thread, please do not hijack someone else's thread, it only creates confusion.

---

### Post by wildmanne39 on 2016-09-15
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by Joe_Misseri on 2016-09-15
```


jm@jm-Aspire-5750G:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"
Linux jm-Aspire-5750G 4.4.0-34-generic #53~14.04.1-Ubuntu SMP Wed Jul 27 16:56:40 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
jm@jm-Aspire-5750G:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
  Subsystem: Acer Incorporated [ALI] Device [1025:0504]
  Kernel driver in use: tg3
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
  Subsystem: Foxconn International, Inc. Device [105b:e040]
jm@jm-Aspire-5750G:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jm@jm-Aspire-5750G:~$ rfkill list all
0: acer-wireless: Wireless LAN
  Soft blocked: no
  Hard blocked: no
jm@jm-Aspire-5750G:~$ lsmod
Module                  Size  Used by
nls_utf8               16384  1 
isofs                  40960  1 
nls_iso8859_1          16384  2 
uas                    24576  0 
usb_storage            69632  3 uas
xt_multiport           16384  1 
iptable_filter         16384  1 
ip_tables              24576  1 iptable_filter
x_tables               36864  3 ip_tables,xt_multiport,iptable_filter
bnep                   20480  2 
rfcomm                 69632  0 
bluetooth             516096  10 bnep,rfcomm
binfmt_misc            20480  1 
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              180224  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
snd_hda_codec_hdmi     53248  1 
snd_hda_codec_realtek    86016  1 
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          36864  3 
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
i915                 1208320  3 
intel_rapl             20480  0 
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       16384  0 
coretemp               16384  0 
kvm_intel             167936  0 
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                      81920  17  snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
kvm                   536576  1 kvm_intel
drm_kms_helper        143360  1 i915
drm                   360448  5 i915,drm_kms_helper
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
mei_me                 36864  0 
mei                    98304  1 mei_me
aesni_intel           167936  0 
soundcore              16384  1 snd
i2c_algo_bit           16384  1 i915
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
shpchp                 36864  0 
lpc_ich                24576  0 
sysimgblt              16384  1 drm_kms_helper
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
input_leds             16384  0 
serio_raw              16384  0 
joydev                 20480  0 
parport_pc             36864  0 
ppdev                  20480  0 
mac_hid                16384  0 
mxm_wmi                16384  0 
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
video                  40960  2 i915,acer_wmi
wmi                    20480  2 acer_wmi,mxm_wmi
lp                     20480  0 
parport                49152  3 lp,ppdev,parport_pc
tg3                   163840  0 
psmouse               122880  0 
ptp                    20480  1 tg3
pps_core               20480  1 ptp
ahci                   36864  4 
sdhci_pci              28672  0 
libahci                32768  1 ahci
sdhci                  45056  1 sdhci_pci
fjes                   28672  0 
jm@jm-Aspire-5750G:~$ 


```

---

### Post by wildmanne39 on 2016-09-15
Please do:
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
Reboot

---

### Post by Joe_Misseri on 2016-09-15
Much kudos to you good sir.

Apologies for the newb forum jacking.

IDK  what code I entered this time around that was different other than not  installing the bcmwl-kernel-source properly in previous attempts, either  way.... thanks again!

---

### Post by wildmanne39 on 2016-09-15
Your welcome!
Enjoy!

---

