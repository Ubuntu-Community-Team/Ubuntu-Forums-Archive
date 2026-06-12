---
title: "Wireless problem"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Leshinsky on 2009-05-15
Ok,  i looked at the other wireless problem but it did not seem to fit.  i can not conntect with my built in wireless card.  But i can connect with my netgear usb wireless card.  when i type in 
lshw -C network into terminal i get this.

matthew@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:3b:34:0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:1f:33:06:6c:4f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.106 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3e:00:55:6f:e0:28
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
matthew@ubuntu:~$ 

can anyone tell me what is going on.  i also checked under system admin and hardware profiles. and it says there is a alt driver to atleros wireless lan cards.

---

### Post by superprash2003 on 2009-05-15
which ubuntu version are you running?

---

### Post by Leshinsky on 2009-05-15
I am running the latest version.  I just installed ubuntu this weekend.  I am not sure how to find out the version number

---

### Post by lkraemer on 2009-05-15
I am trying to help 67 with the exact same Wifi card at:
[http://ubuntuforums.org/showthread.php?t=1158560](http://ubuntuforums.org/showthread.php?t=1158560)
starting at #3.  You might want to follow along.

It shouldn't be that hard.

lkraemer

---

### Post by Leshinsky on 2009-05-15
ok that other forum told me to do lshw -C network and post the results.  so here they are.  

matthew@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:3b:34:0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:1f:33:06:6c:4f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.106 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:2 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: b2:ee:7b:1e:dc:af
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
matthew@ubuntu:~$ su
Password: 
root@ubuntu:/home/matthew# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:3b:34:0c
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:1f:33:06:6c:4f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.106 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:2 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: b2:ee:7b:1e:dc:af
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@ubuntu:/home/matthew# 

lshw -C networklshw -C network

---

### Post by lkraemer on 2009-05-15
OK, slow but sure go ahead and follow the other post. 
```

```
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist     OR for 9.04 use cat /etc/modprobe.d/blacklist.conf
iwconfig 
cd /
cd /lib/firmware
ls -alt
cd /b43
ls -alt
[/CODE]
Post the output of the above commands.

Then keep reading ahead...

lkraemer

---

### Post by Leshinsky on 2009-05-16
ok,  here you guys go.  i got stuck at the second directory switch.  but everything before that is on here.

matthew@ubuntu:~$ lsmod
Module                  Size  Used by
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
vboxnetflt             93992  0 
vboxdrv               123048  1 vboxnetflt
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
snd_hda_intel         435636  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
rtl8187                53376  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
uvcvideo               63240  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
compat_ioctl32          9344  1 uvcvideo
mac80211              217208  1 rtl8187
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
eeprom_93cx6           10240  1 rtl8187
iTCO_wdt               19108  0 
acer_wmi               24260  0 
videodev               41600  1 uvcvideo
psmouse                61972  0 
iTCO_vendor_support    11652  1 iTCO_wdt
led_class              12036  1 acer_wmi
v4l1_compat            21764  2 uvcvideo,videodev
pcspkr                 10496  0 
serio_raw              13316  0 
cfg80211               38032  2 rtl8187,mac80211
video                  25360  0 
ath_pci                99224  0 
snd                    62628  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              34108  1 
wlan                  210288  1 ath_pci
ath_hal               198864  1 ath_pci
output                 11008  1 video
soundcore              15200  1 snd
agpgart                42696  3 drm,intel_agp
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
matthew@ubuntu:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
matthew@ubuntu:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
matthew@ubuntu:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:41:3B:E9   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=15/100  Signal level:65/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

matthew@ubuntu:~$ cd
matthew@ubuntu:~$ cd /lib/firmware
matthew@ubuntu:/lib/firmware$ ls -alt
total 6524
drwxr-xr-x 19 root root   4096 2009-05-15 09:24 ..
lrwxrwxrwx  1 root root     14 2009-05-12 18:22 NPE-B -> NPE-B.01020201
lrwxrwxrwx  1 root root     14 2009-05-12 18:22 NPE-C -> NPE-C.02020201
drwxr-xr-x  5 root root   4096 2009-04-20 08:03 .
drwxr-xr-x 13 root root   4096 2009-04-20 08:03 acx
drwxr-xr-x  2 root root   4096 2009-04-20 08:03 zd1211
drwxr-xr-x 15 root root   4096 2009-04-20 08:01 2.6.28-11-generic
-rw-r--r--  1 root root 132978 2009-04-02 15:46 ql2322_fw.bin
-rw-r--r--  1 root root 206500 2009-04-02 15:46 ql2400_fw.bin
-rw-r--r--  1 root root   8192 2009-04-02 15:46 rt2561.bin
-rw-r--r--  1 root root   8192 2009-04-02 15:46 rt2561s.bin
-rw-r--r--  1 root root   8192 2009-04-02 15:46 rt2661.bin
-rw-r--r--  1 root root   8192 2009-04-02 15:46 rt2860.bin
-rw-r--r--  1 root root   4096 2009-04-02 15:46 rt2870.bin
-rw-r--r--  1 root root   2048 2009-04-02 15:46 rt73.bin
-rw-r--r--  1 root root  62484 2009-04-02 15:46 zd1201-ap.fw
-rw-r--r--  1 root root  70612 2009-04-02 15:46 zd1201.fw
-rw-r--r--  1 root root  22622 2009-04-02 15:46 aic94xx-seq.fw
-rw-r--r--  1 root root  30348 2009-04-02 15:46 atmel_at76c502_3com.bin
-rw-r--r--  1 root root  35184 2009-04-02 15:46 atmel_at76c502_3com-wpa.bin
-rw-r--r--  1 root root  31764 2009-04-02 15:46 atmel_at76c502.bin
-rw-r--r--  1 root root  31764 2009-04-02 15:46 atmel_at76c502d.bin
-rw-r--r--  1 root root  35276 2009-04-02 15:46 atmel_at76c502d-wpa.bin
-rw-r--r--  1 root root  31776 2009-04-02 15:46 atmel_at76c502e.bin
-rw-r--r--  1 root root  35272 2009-04-02 15:46 atmel_at76c502e-wpa.bin
-rw-r--r--  1 root root  35276 2009-04-02 15:46 atmel_at76c502-wpa.bin
-rw-r--r--  1 root root  28156 2009-04-02 15:46 atmel_at76c503-i3861.bin
-rw-r--r--  1 root root  28032 2009-04-02 15:46 atmel_at76c503-i3863.bin
-rw-r--r--  1 root root  35372 2009-04-02 15:46 atmel_at76c503-rfmd-0.90.2-140.bin
-rw-r--r--  1 root root  37800 2009-04-02 15:46 atmel_at76c503-rfmd-acc.bin
-rw-r--r--  1 root root  37956 2009-04-02 15:46 atmel_at76c503-rfmd.bin
-rw-r--r--  1 root root  35180 2009-04-02 15:46 atmel_at76c504_2958-wpa.bin
-rw-r--r--  1 root root  39928 2009-04-02 15:46 atmel_at76c504a_2958-wpa.bin
-rw-r--r--  1 root root  31748 2009-04-02 15:46 atmel_at76c504.bin
-rw-r--r--  1 root root  35196 2009-04-02 15:46 atmel_at76c504c-wpa.bin
-rw-r--r--  1 root root  37005 2009-04-02 15:46 atmel_at76c505a-rfmd2958.bin
-rw-r--r--  1 root root  36992 2009-04-02 15:46 atmel_at76c505-rfmd2958.bin
-rw-r--r--  1 root root  35528 2009-04-02 15:46 atmel_at76c505-rfmd.bin
-rw-r--r--  1 root root  31824 2009-04-02 15:46 atmel_at76c506.bin
-rw-r--r--  1 root root  35228 2009-04-02 15:46 atmel_at76c506-wpa.bin
-rw-r--r--  1 root root 114688 2009-04-02 15:46 BCM2033-FW.BIN
-rw-r--r--  1 root root   3245 2009-04-02 15:46 BCM2033-MD.BIN
-rw-r--r--  1 root root  32522 2009-04-02 15:46 dvb-fe-cx24116.fw
-rw-r--r--  1 root root  12772 2009-04-02 15:46 dvb-fe-or51132-qam.fw
-rw-r--r--  1 root root  17532 2009-04-02 15:46 dvb-fe-or51132-vsb.fw
-rw-r--r--  1 root root   8518 2009-04-02 15:46 dvb-fe-or51211.fw
-rw-r--r--  1 root root  24478 2009-04-02 15:46 dvb-fe-tda10046.fw
-rw-r--r--  1 root root 239956 2009-04-02 15:46 dvb-ttpci-01.fw
-rw-r--r--  1 root root  12700 2009-04-02 15:46 dvb-usb-af9015.fw
-rw-r--r--  1 root root  10757 2009-04-02 15:46 dvb-usb-avertv-a800-02.fw
-rw-r--r--  1 root root   9025 2009-04-02 15:46 dvb-usb-bluebird-01.fw
-rw-r--r--  1 root root  34306 2009-04-02 15:46 dvb-usb-dib0700-1.10.fw
-rw-r--r--  1 root root  33768 2009-04-02 15:46 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root   9180 2009-04-02 15:46 dvb-usb-dibusb-5.0.0.11.fw
-rw-r--r--  1 root root   7558 2009-04-02 15:46 dvb-usb-dibusb-6.0.0.8.fw
-rw-r--r--  1 root root   7431 2009-04-02 15:46 dvb-usb-dtt200u-01.fw
-rw-r--r--  1 root root   3360 2009-04-02 15:46 dvb-usb-tvwalkert.fw
-rw-r--r--  1 root root   4286 2009-04-02 15:46 dvb-usb-umt-010-02.fw
-rw-r--r--  1 root root  10752 2009-04-02 15:46 dvb-usb-vp702x-01.fw
-rw-r--r--  1 root root  10752 2009-04-02 15:46 dvb-usb-vp7045-01.fw
-rw-r--r--  1 root root   8480 2009-04-02 15:46 dvb-usb-wt220u-02.fw
-rw-r--r--  1 root root  12902 2009-04-02 15:46 dvb-usb-wt220u-fc03.fw
-rw-r--r--  1 root root   8518 2009-04-02 15:46 dvb-usb-wt220u-zl0353-01.fw
-rw-r--r--  1 root root 209190 2009-04-02 15:46 ipw2100-1.3.fw
-rw-r--r--  1 root root 201138 2009-04-02 15:46 ipw2100-1.3-i.fw
-rw-r--r--  1 root root 196458 2009-04-02 15:46 ipw2100-1.3-p.fw
-rw-r--r--  1 root root 191142 2009-04-02 15:46 ipw2200-bss.fw
-rw-r--r--  1 root root 185660 2009-04-02 15:46 ipw2200-ibss.fw
-rw-r--r--  1 root root 187836 2009-04-02 15:46 ipw2200-sniffer.fw
-rw-r--r--  1 root root 112128 2009-04-02 15:46 isl3877
-rw-r--r--  1 root root  29024 2009-04-02 15:46 isl3886
-rw-r--r--  1 root root  30060 2009-04-02 15:46 isl3887usb_bare
-rw-r--r--  1 root root  93996 2009-04-02 15:46 isl3890
-rw-r--r--  1 root root  29468 2009-04-02 15:46 isl3890usb
-rw-r--r--  1 root root 149652 2009-04-02 15:46 iwlwifi-3945-1.ucode
-rw-r--r--  1 root root 149816 2009-04-02 15:46 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root 187608 2009-04-02 15:46 iwlwifi-4965-1.ucode
-rw-r--r--  1 root root 187764 2009-04-02 15:46 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root 345008 2009-04-02 15:46 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root 118884 2009-04-02 15:46 lbtf_usb.bin
-rw-r--r--  1 root root  76802 2009-04-02 15:46 ql2100_fw.bin
-rw-r--r--  1 root root  84566 2009-04-02 15:46 ql2200_fw.bin
-rw-r--r--  1 root root 123170 2009-04-02 15:46 ql2300_fw.bin
-rw-r--r--  1 root root 141200 2009-04-02 15:46 v4l-cx23418-apu.fw
-rw-r--r--  1 root root 158332 2009-04-02 15:46 v4l-cx23418-cpu.fw
-rw-r--r--  1 root root  16382 2009-04-02 15:46 v4l-cx23418-dig.fw
-rw-r--r--  1 root root 262144 2009-04-02 15:46 v4l-cx2341x-dec.fw
-rw-r--r--  1 root root 376836 2009-04-02 15:46 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 2009-04-02 15:46 v4l-cx2341x-init.mpg
-rw-r--r--  1 root root  16382 2009-04-02 15:46 v4l-cx23885-avcore-01.fw
-rw-r--r--  1 root root 376836 2009-04-02 15:46 v4l-cx23885-enc.fw
-rw-r--r--  1 root root  16382 2009-04-02 15:46 v4l-cx25840.fw
-rw-r--r--  1 root root   8192 2009-04-02 15:46 v4l-pvrusb2-24xxx-01.fw
-rw-r--r--  1 root root   8192 2009-04-02 15:46 v4l-pvrusb2-29xxx-01.fw
-rw-r--r--  1 root root  15664 2009-02-13 14:30 NPE-C.02020201
-rw-r--r--  1 root root  15664 2009-02-13 14:30 NPE-B.01020201
matthew@ubuntu:/lib/firmware$ cd /b43
bash: cd: /b43: No such file or directory
matthew@ubuntu:/lib/firmware$ cd
matthew@ubuntu:~$ cd /b43
bash: cd: /b43: No such file or directory
matthew@ubuntu:~$

---

### Post by lkraemer on 2009-05-17
Your command iwconfig shows:

wlan1 IEEE 802.11bg ESSID:"linksys"
Mode:Managed Frequency:2.437 GHz Access Point: 00:13:10:41:3B:E9 

which shows you are already connected to linksys on wlan1 with
AP 00:13:10:41:3B:E9.

Are you sure you aren't already connected?

lkraemer

---

### Post by Leshinsky on 2009-05-17
I am connected through a netgear usb wireless card.  netgear is the name of my router.  my built in wireless card will not work in linux.

---

### Post by lkraemer on 2009-05-17
OK, you're lsmod command doesn't show b43 or ssb as being used, and
ath_pci is installed.

There aren't any *.fw files in /lib/firmware/b43 or
/lib/firmware/b43legacy and if you had a Wired LAN connection and
went to SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS and enabled the Hardware Drivers with a LAN connection there should have been folders created and files inserted for the Restricted Drivers to work. 


Disable Hardware Restricted Drivers by going to:
SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS and DISABLE, then reboot.

Blacklist as required..... (b43 & ssb aren't in the modules listed, but blacklist them anyway)

Open a Terminal window and add the following to the blacklist.conf file right after bcm43xx.
blacklist b43
blacklist ssb


```

sudo gedit /etc/modprobe.d/blacklist.conf

```
Save the file.

Download Current MadWifi Drivers via wired LAN connection.

Go to:
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)
and download the current Version madwifi-hal-0.10.5.6-current.tar.gz and extract it to a folder under your home/login named madwifi_ar5007. That folder will be named something like madwifi-hal-0.10.5.6-r4016-20090429, assuming the version hasn't been updated.

Just realize that when you Update ubuntu, and get a New Kernel you will have to recompile to make it work again. No big deal after you have done it once. (NOTE: you can always select a previous Kernel from the Grub menu with a working Wifi until you get the time to rework for the new Kernel.)

Here is what I use when a New Kernel is downloaded.

When a new Kernel has been downloaded and
your Wifi doesn't work.......DO:
(I am adding the first command to remove the already loaded ath_pci
but it might not really be needed, won't hurt!)
```

sudo modprobe -r ath_pci
cd ~/madwifi_ar5007
cd madwifi-hal-0.10.5.6-r4003-20090416 
make clean
make
sudo make install
sudo modprobe ath_pci
sudo /etc/init.d/networking restart

```
Then, I'd reboot.

That should get you going, assuming no errors with the make, and your Wifi
is turned on by switch or by appropriate keystrokes to enable it.

```

iwconfig

```
should show your wifi as ath0, wlan0 or something like that.

REF:
[http://madwifi-project.org/](http://madwifi-project.org/)
[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)

[http://linux.die.net/man/8/modprobe](http://linux.die.net/man/8/modprobe)

lkraemer

---

