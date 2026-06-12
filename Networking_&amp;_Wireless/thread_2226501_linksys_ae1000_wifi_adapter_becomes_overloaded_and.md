---
title: "linksys ae1000 wifi adapter becomes overloaded and unresponsive"
date: 2014-05-27
forum: Networking &amp; Wireless
---

### Post by LUCASBSTANLEY on 2014-05-27
Hello I have tried everything I could to get this to work I am now lost and looking to you for help here are my specs and here is whats going on
memory 2.0gib
processor AMD Sempron(tm) Processor 3400+ 
graphics Gallium 0.4 on AMD RV635
os type 32-bit
disk 76.5GB help i also have a 5450 hd silent graphics card 				

first wheni try and install everything like this i get this error
god@slave:~$ cd 2010_0915_RT3572_Linux_STA_v2.4.0.2/
god@slave:~/2010_0915_RT3572_Linux_STA_v2.4.0.2$ make
make -C tools
make[1]: Entering directory `/home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
/home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools/bin2h
cp -f os/linux/Makefile.6 /home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/Makefile
make -C /lib/modules/3.13.0-27-generic/build SUBDIRS=/home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-27-generic'
  CC [M]  /home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.o
/home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSFSInfoChange’:
/home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:1228:20: error: incompatible types when assigning to type ‘int’ from type ‘kuid_t’
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:1229:20: error: incompatible types when assigning to type ‘int’ from type ‘kgid_t’
   pOSFSInfo->fsgid = current_fsgid();  
                    ^
/home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:1694:38: warning: initialization discards ‘const’ qualifier from pointer target type [enabled by default]
  struct net_device_ops *pNetDevOps = pNetDev->netdev_ops;
                                      ^
/home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:1731:38: warning: initialization discards ‘const’ qualifier from pointer target type [enabled by default]
  struct net_device_ops *pNetDevOps = pNetDev->netdev_ops;
                                      ^
make[2]: *** [/home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-27-generic'
make: *** [LINUX] Error 2
god@slave:~/2010_0915_RT3572_Linux_STA_v2.4.0.2$ 







so I tried this 

god@slave:~$  patch -p1 < rt5390sta_3.12.patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- ../rt_linux.h    2013-05-22 03:28:50.000000000 +0000
|+++ ./include/os/rt_linux.h    2014-02-04 21:54:39.982679908 +0000
--------------------------
File to patch: 
now i am unable to figure out where to go from here

---

### Post by cariboo on 2014-05-28
You should get better and quicker help here than in ABT.

---

### Post by LUCASBSTANLEY on 2014-05-28
did you move the location of this thread?

---

### Post by LUCASBSTANLEY on 2014-05-30
so much for getting help

---

### Post by praseodym on 2014-05-31
Stop crying ;)

That driver is from 2010, i.e. old. Try this one:

[http://forum.ubuntuusers.de/topic/fritz-wlan-usb-stick-n-v2-usb-id-057c-8501-chi/2/#post-5364732](http://forum.ubuntuusers.de/topic/fritz-wlan-usb-stick-n-v2-usb-id-057c-8501-chi/2/#post-5364732)

---

### Post by LUCASBSTANLEY on 2014-05-31
thanks but what does this mean

god@slave:~$ cd DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared
god@slave:~/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared$ make
make -C tools
make[1]: Entering directory `/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/tools'
/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/tools/bin2h
cp -f os/linux/Makefile.6 /home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux/Makefile
make -C /lib/modules/3.13.0-27-generic/build SUBDIRS=/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-27-generic'
  CC [M]  /home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux/../../os/linux/rt_linux.o
/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux/../../os/linux/rt_linux.c: In function &#8216;__RtmpOSFSInfoChange&#8217;:
/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux/../../os/linux/rt_linux.c:1141:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kuid_t&#8217;
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux/../../os/linux/rt_linux.c:1142:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kgid_t&#8217;
   pOSFSInfo->fsgid = current_fsgid();
                    ^
make[2]: *** [/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-27-generic'
make: *** [LINUX] Error 2
god@slave:~/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared$

---

### Post by praseodym on 2014-06-01
Ok, try it with
```

sudo make
```

---

### Post by LUCASBSTANLEY on 2014-06-01
this is what happened when i tried sudo make
god@slave:~$ cd DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared
god@slave:~/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared$ sudo make
[sudo] password for god: 
make -C tools
make[1]: Entering directory `/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/tools'
/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/tools/bin2h
cp -f os/linux/Makefile.6 /home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux/Makefile
make -C /lib/modules/3.13.0-27-generic/build SUBDIRS=/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-27-generic'
  CC [M]  /home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux/../../os/linux/rt_linux.o
/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux/../../os/linux/rt_linux.c: In function &#8216;__RtmpOSFSInfoChange&#8217;:
/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux/../../os/linux/rt_linux.c:1141:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kuid_t&#8217;
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux/../../os/linux/rt_linux.c:1142:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kgid_t&#8217;
   pOSFSInfo->fsgid = current_fsgid();
                    ^
make[2]: *** [/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/god/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-27-generic'
make: *** [LINUX] Error 2
god@slave:~/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared$

---

### Post by praseodym on 2014-06-01
Ok,

doesnt work. Try to add the device ID to the native driver:

```
echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "13b1 002f" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf 
sudo modprobe -rfv rt2800usb
sudo modprobe -v rt2800usb
```
Replug the stick and check:
```

iwconfig
dmesg | grep rt2
sudo iwlist scan
```

---

### Post by LUCASBSTANLEY on 2014-06-01
so now this happens then when I try the second line of code my whole system freezes
god@slave:~$ echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "13b1 002f" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf 
[sudo] password for god: 
install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "13b1 002f" > /sys/bus/usb/drivers/rt2800usb/new_id

---

### Post by praseodym on 2014-06-01
Plus the others

---

### Post by LUCASBSTANLEY on 2014-06-01
when i attempt to try the second one my computer completley freezes and i have to hold the power button to shut it down

---

### Post by praseodym on 2014-06-02
Ok, after a reboot it works, too. Lets check now
```

iwconfig
lsmod
dmesg | grep rt2
sudo iwlist scan
iwlist chan
cat /etc/resolv.conf
```

---

### Post by LUCASBSTANLEY on 2014-06-03
ok so I havent seen it freeze as of late but it doesn't seem to be performing as well as it should here is what came up when i put in the last steps 
god@slave:~$ iwconfig
wlan0     IEEE 802.11abgn  ESSID:"airplane1"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:1D:D4:8A:16:30   
          Bit Rate=26 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1125  Invalid misc:727   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

god@slave:~$ lsmod
Module                  Size  Used by
usb_storage            48417  0 
cdc_acm                27963  0 
ctr                    12905  3 
ccm                    17496  3 
snd_hda_codec_hdmi     45303  1 
snd_hda_codec_realtek    51029  1 
arc4                   12536  2 
snd_hda_intel          42730  5 
snd_hda_codec         164067  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
rt2800usb              26581  0 
snd_pcm                85501  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
rt2x00usb              20041  1 rt2800usb
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
rt2800lib              83150  1 rt2800usb
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
rt2x00lib              48886  3 rt2x00usb,rt2800lib,rt2800usb
snd_rawmidi            25135  1 snd_seq_midi
radeon               1416373  4 
rfcomm                 53664  0 
bnep                   18895  2 
mac80211              546013  3 rt2x00lib,rt2x00usb,rt2800lib
bluetooth             342263  10 bnep,rfcomm
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
ttm                    72698  1 radeon
snd_timer              28584  2 snd_pcm,snd_seq
joydev                 17101  0 
cfg80211              409394  2 mac80211,rt2x00lib
serio_raw              13230  0 
crc_ccitt              12627  1 rt2800lib
drm_kms_helper         46907  1 radeon
snd                    60871  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
k8temp                 12842  0 
binfmt_misc            13140  1 
drm                   243792  6 ttm,drm_kms_helper,radeon
nv_tco                 13300  0 
i2c_nforce2            13037  0 
i2c_algo_bit           13197  1 radeon
soundcore              12600  1 snd
mac_hid                13037  0 
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_logitech_dj        18165  0 
usbhid                 46997  0 
hid                    87604  3 usbhid,hid_logitech_dj
pata_acpi              12886  0 
8139too                32571  0 
8139cp                 27171  0 
psmouse                91033  0 
mii                    13654  2 8139cp,8139too
sata_nv                23004  0 
pata_amd               13761  2 
floppy                 55416  0 
god@slave:~$ dmesg | grep rt2
[   20.401276] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3572, rev 0221 detected
[   20.645587] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0009 detected
[   20.702959] usbcore: registered new interface driver rt2800usb
[   21.184511] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   21.207042] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.33
[ 1833.033536] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 3572, rev 0221 detected
[ 1833.063651] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 0009 detected
[ 1833.179189] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[ 1833.179257] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.33
[ 4773.716910] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[ 4773.716948] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[ 4773.716952] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[ 4773.764158] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[ 4773.765279] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[ 4773.766409] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[ 4773.766473] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[ 4773.766477] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[ 4773.766494] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[10948.105823] ieee80211 phy2: rt2x00_set_rt: Info - RT chipset 3572, rev 0221 detected
[10948.134708] ieee80211 phy2: rt2x00_set_rf: Info - RF chipset 0009 detected
[10948.274242] ieee80211 phy2: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[10948.274304] ieee80211 phy2: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.33
[11629.293101] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[11629.293139] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[11629.293144] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[14397.360209] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[14397.360240] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[14397.360247] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[14397.372581] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[14397.372628] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[14397.372635] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[14397.377075] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[14397.377103] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[14397.377110] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[14397.380452] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[14397.380480] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[14397.380487] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[14397.380502] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[14397.384574] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[14397.385806] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[14397.385810] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[15357.460448] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[15357.460584] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[15357.460589] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[15837.609137] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[15837.609182] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[15837.609190] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[15837.636137] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[15837.636177] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[15837.636184] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[18157.681052] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[18157.681115] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[18157.681120] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[18957.312073] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[18957.369046] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[20517.376472] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[20517.376498] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[20517.376503] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[20517.644606] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[20517.645019] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[20517.645028] ieee80211 phy2: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[26477.769617] ieee80211 phy3: rt2x00_set_rt: Info - RT chipset 3572, rev 0221 detected
[26477.798498] ieee80211 phy3: rt2x00_set_rf: Info - RF chipset 0009 detected
[26477.981918] ieee80211 phy3: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[26478.017321] ieee80211 phy3: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.33
[66886.304486] ieee80211 phy3: rt2x00lib_rxdone_read_signal: Warning - Frame received with unrecognized signal, mode=0x0000, signal=0x0000, type=4
[70727.368588] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[70727.369711] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[70727.370834] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[70727.370919] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[70727.370924] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[70727.456459] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[70727.456709] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[70727.456714] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[70850.992855] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[70850.992889] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[70850.992893] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[70850.996224] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[70850.996385] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[70850.996389] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[70887.736732] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[70887.737009] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[70887.737015] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[70887.740106] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[70887.740349] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[70887.740353] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[70887.837106] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[70887.837144] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[70887.837148] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[70887.837165] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[70889.928732] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[70889.928753] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[70889.928757] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[70889.932103] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[70889.932328] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[70889.932333] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[71927.645122] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[71927.645299] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[71927.645304] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[71927.645325] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[100727.264638] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[100727.264975] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[100727.264980] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[100727.349137] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[100727.349154] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[100727.349158] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[100727.436897] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[100727.437303] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[100727.437312] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[105874.104179] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[105874.104208] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[105874.104215] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[105977.188066] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[105977.188102] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[105977.188110] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[105977.197063] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[105977.197089] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[105977.197096] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[105977.197180] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[105977.197202] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[105977.200435] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[105977.200462] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[105977.200469] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[105977.216199] ieee80211 phy3: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[105977.235446] ieee80211 phy3: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[106007.596696] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[106007.596732] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[106007.596740] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[106008.532695] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[106008.534687] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[106008.536433] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[106008.536517] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[106008.536527] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[106008.536536] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[106008.536544] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[106127.612204] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[106127.613301] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[106127.613315] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[106127.613330] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[106367.568236] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[106367.568343] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[106367.568347] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[106367.568375] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[110577.364892] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[110577.364929] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[110577.364933] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[110577.364956] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[110578.000887] ieee80211 phy3: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[110578.104513] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[110578.104552] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[110578.123512] ieee80211 phy3: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[110578.123652] ieee80211 phy3: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[110808.460043] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[110808.460322] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[110808.460327] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[116807.577053] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[116807.577076] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[116807.577081] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[116807.577093] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[116807.577097] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[121247.632121] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[121247.632170] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[121247.632175] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[121247.632202] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[149077.464791] ieee80211 phy3: rt2x00lib_rxdone_read_signal: Warning - Frame received with unrecognized signal, mode=0x0000, signal=0x0000, type=4
[150760.040004] ieee80211 phy3: rt2x00lib_rxdone_read_signal: Warning - Frame received with unrecognized signal, mode=0x0000, signal=0x0000, type=4
[158893.552391] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[158893.552419] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[158893.552424] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[158893.560261] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[158893.560283] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[158893.560287] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[158894.001017] ieee80211 phy3: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[158894.104645] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[158894.104671] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[158895.001017] ieee80211 phy3: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[158895.104648] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[158895.104670] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[158895.125146] ieee80211 phy3: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[158895.125262] ieee80211 phy3: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[160367.884584] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[160367.884612] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[160367.884617] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[160367.884634] ieee80211 phy3: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
god@slave:~$ sudo iwlist scan
[sudo] password for god: 
wlan0     Failed to read scan data : Resource temporarily unavailable

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

god@slave:~$ iwlist chan
wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 102 : 5.51 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 110 : 5.55 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 118 : 5.59 GHz
          Channel 132 : 5.66 GHz
          Current Frequency=2.447 GHz (Channel 8)

lo        no frequency information.

eth0      no frequency information.

god@slave:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search hsd1.wa.comcast.net
god@slave:~$

---

### Post by praseodym on 2014-06-03
Deactivate the power management
```

sudo iwconfig wlan0 power off
```

---

### Post by LUCASBSTANLEY on 2014-06-03
ok I've done that
god@slave:~$ sudo iwconfig wlan0 power off
god@slave:~$

---

### Post by praseodym on 2014-06-04
Please show
```

modinfo rt2800usb
```
You could try to decrease the current of the USB-slot (same here with a TP-Link, works great, no heating, etc):
```

echo 'KERNEL=="wlan*", ACTION=="add", RUN+="/sbin/iwconfig wlan0 txpower 18"' | sudo tee /etc/udev/rules.d/10-wlan-stick.rules
```
Replug the stick and check "iwconfig". "Tx-Power" should read **18 dBm** now

---

### Post by LUCASBSTANLEY on 2014-06-04
god@slave:~$ iwconfig
wlan0     IEEE 802.11abgn  ESSID:"airplane1"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:1D:D4:8A:16:30   
          Bit Rate=52 Mb/s   Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:31   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

---

