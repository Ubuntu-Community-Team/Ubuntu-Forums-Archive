---
title: "No wired lan available--wireless usb lan not working"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by Glenn_Sullivan on 2014-04-18
Output of lsusb:
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
Bus 001 Device 004: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU] *************
 
Bus 001 Device 003: ID 07ca:4826 AVerMedia Technologies, Inc. ************
 
Bus 001 Device 002: ID 0781:5530 SanDisk Corp. Cruzer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Devices not working is marked with stars

---

### Post by wildmanne39 on 2014-04-18
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

---

### Post by Glenn_Sullivan on 2014-04-19
I have no network connection on the Ubuntu PC and therefore no internet connection. There is no Ethernet cables in my apartment building, the only means of internet is wlan. I have windows 8.1 on the same computer and everything works fine with windows.

---

### Post by Glenn_Sullivan on 2014-04-19
```
########## wireless info START ##########
##### release #####
Distributor ID: Ubuntu
Description: Ubuntu 14.04 LTS
Release: 14.04
Codename: trusty
##### kernel #####
Linux glenn-MS-7641 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
##### lspci #####
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
 Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7641]
 Kernel driver in use: r8169
##### lsusb #####
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]
Bus 001 Device 003: ID 07ca:4826 AVerMedia Technologies, Inc. 
Bus 001 Device 002: ID 0781:5530 SanDisk Corp. Cruzer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
##### PCMCIA Card Info #####

##### rfkill #####

##### iw reg get #####
country 00:
 (2402 - 2472 @ 40), (3, 20)
 (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
 (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
 (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
 (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
##### interfaces #####
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
##### iwconfig #####
wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #####
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
##### resolv.conf #####

##### nm-tool #####
NetworkManager Tool
State: disconnected
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             disconnected
  Default:           no
  HW Address:        94:44:52:5C:C5:A4
  Capabilities:
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
  Wireless Access Points 

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        8C:89:A5:6C:52:B4
  Capabilities:
    Carrier Detect:  yes
  Wired Properties
    Carrier:         off
 
##### NetworkManager.state #####
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
##### NetworkManager.conf #####
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false
##### iwlist #####
wlan0     No scan results

##### iwlist channel #####
wlan0     14 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
##### lsmod #####
r8712u                184158  0 
##### modinfo #####
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     607999565FE22A6079602D8
alias:          usb:v0409p02B6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7622d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0051d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp845Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8174d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3325d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3310d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3341d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3340d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3339d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3301d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0064d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0049d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0058d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p4901d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED18d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3306d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0015d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9605d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7612d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3303d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp815Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3309d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3336d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3335d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3334d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3333d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3342d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3311d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3323d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9061d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8192d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8172d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v25D4p4CABd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v25D4p4CA1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApC512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p646Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0752d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp5077d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0154d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0063d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0059d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0045d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED16d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB28d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0167d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE032d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE034d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0016d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9603d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7611d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3306d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3306d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0047d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp11F1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp945Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1791d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1786d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDApC512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8713d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8173d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8171d*dc*dsc*dp*ic*isc*ip*in*
depends:        
staging:        Y
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        00:A5:A6:57:59:DE:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)

##### modules #####

lp
rtc
##### blacklist #####


```> **Glenn_Sullivan said:**
> I have no network connection on the Ubuntu PC and therefore no internet connection. There is no Ethernet cables in my apartment building, the only means of internet is wlan. I have windows 8.1 on the same computer and everything works fine with windows.

---

### Post by wildmanne39 on 2014-04-19
The file you posted is missing information from blacklist down.

---

### Post by praseodym on 2014-04-19
Hi,

you need nameservers in your /etc/resolv.conf:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by Glenn_Sullivan on 2014-04-19
Wildman: there is no blacklisted modules being used on my computer. My computer has had no internet connection under Ubuntu since the installer CD/DVD was inserted up until it was running on its on and still does not and I looked at the script and the last thing listed is the blacklisted modules. My computer is running in a fallback mode, because the proper drivers were not loaded during installation.

praseodym: your suggestion of putting nameservers in resolv.conf made no difference in operation of my computer.

---

### Post by wildmanne39 on 2014-04-19
There should still be information below that point like error messages and blacklist modules, there are always blacklisted modules. Did you run the script by entering your password when you were ask to enter it? Anyway run the script again and see if you get more information.
Thanks

---

### Post by praseodym on 2014-04-20
Please download these files and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)
[http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz)

Installation via:
```

cd ~/Downloads/
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.038.00
sudo dkms build -m r8168-dkms -v 8.038.00
sudo dkms install -m r8168-dkms -v 8.038.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and check the LAN connection

---

### Post by Glenn_Sullivan on 2014-04-20
```
cd ~/Downloads/
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.038.00
sudo dkms build -m r8168-dkms -v 8.038.00
sudo dkms install -m r8168-dkms -v 8.038.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Failed to work and the reason is that I have no other Ubuntu computers that could run the code. and the ailing computer will not run even the first line of code without generating errors. I will have to download the deb files from Ubuntu on a windows computer and transport them to the bad Ubuntu computer by means of flash drive. So until someone can tell me the exact location and name of needed deb files, the computer is as useful as a boat anchor. By the way the unit is a wireless r8712 usb. My wlan unit is not listed as being compatible with that module.

---

### Post by praseodym on 2014-04-20
Klick on the orange links above to download them and use a flash drive for transport to the Ubuntu computer. Run the commands there.

---

### Post by Glenn_Sullivan on 2014-04-20
finally got the script to work and guess what the problem was not solved. Exactly my computer never connects to the wifi router, but it does seem to do something it properly identifies all SSID's near by, but will not connect to them. It may ask for the password up to twice before it dies and says disconnected from network.

---

### Post by wildmanne39 on 2014-04-20
You need to post the complete file created by the script here is we can look at it and see what is going on, it was not suppose to fix your issue, it is informational only.

---

### Post by praseodym on 2014-04-21
This was for the LAN device. Lets check for wireless:
```

iwconfig
lsmod
sudo iwlist scan
rfkill list
```

---

### Post by Glenn_Sullivan on 2014-04-21
praseodym,

Your last script produced the following output without fixing the problem:
```
eth0      no wireless extensions.
lo        no wireless extensions.
wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Module                  Size  Used by
nls_iso8859_1          12713  1 
cfg80211              484040  0 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
joydev                 17381  0 
ir_lirc_codec          13021  0 
lirc_dev               19980  1 ir_lirc_codec
ir_mce_kbd_decoder     13214  0 
hid_generic            12548  0 
ir_sanyo_decoder       12839  0 
ir_sony_decoder        12713  0 
ir_jvc_decoder         12751  0 
ir_rc6_decoder         12874  0 
ir_rc5_decoder         12710  0 
ir_nec_decoder         12915  0 
rc_rc6_mce             12502  0 
snd_hda_codec_realtek    61438  1 
usbhid                 52616  0 
mceusb                 21980  0 
hid                   106148  3 hid_generic,usbhid
rc_core                28124  12 lirc_dev,ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,mceusb,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder,rc_rc6_mce
r8712u                184158  0 
snd_hda_intel          52355  3 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
kvm_amd                59987  0 
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
kvm                   451511  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
aesni_intel            55624  0 
snd_timer              29482  2 snd_pcm,snd_seq
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
serio_raw              13462  0 
fam15h_power           13119  0 
edac_core              62291  0 
k10temp                13126  0 
snd                    69238  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
edac_mce_amd           22617  0 
radeon               1514165  3 
soundcore              12680  1 snd
sp5100_tco             13979  0 
i2c_piix4              22155  0 
ttm                    85115  1 radeon
drm_kms_helper         52758  1 radeon
drm                   302817  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
shpchp                 37032  0 
mac_hid                13205  0 
wmi                    19177  0 
parport_pc             32701  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
usb_storage            62209  1 
r8168                 400910  0 
ahci                   25819  2 
r8169                  67581  0 
pata_atiixp            13271  0 
libahci                32168  1 ahci
mii                    13934  1 r8169
[sudo] password for glenn: 
eth0      Interface doesn't support scanning.
lo        Interface doesn't support scanning.
wlan0     No scan results
 

```

---

### Post by praseodym on 2014-04-21
The wrong LAN driver is still loaded:
```

sudo modprobe -rfv r8169
sudo modprobe -rfv r8168
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u
```

Please try:
```

echo "options r8712u power_mgnt=0 low_power=0" | sudo tee /etc/modprobe.d/r8712u.conf
sudo service network-manager stop
sudo modprobe -rfv r8712u
sudo modprobe -v r8712u
sudo service network-manager start
```

---

### Post by Glenn_Sullivan on 2014-04-21
praseodym,

Still did not work and still doing the same thing. The entry for r8169 was gone and was replaced by r8712u and the entry for r8168 was still there. This unit is a Belkin n150 that is less than two years old. According to the realtek webpage my unit is an r8192su, but to work both the r8192su and r8712u modules must both be running for the unit to work. Which explains what is going on it has been misidentified by the Ubuntu OS. Further complicating the situation is the fact that the lan is pci-express instead of pci.

---

### Post by Glenn_Sullivan on 2014-04-22
the latest output of lsusb is:```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]
Bus 001 Device 003: ID 07ca:4826 AVerMedia Technologies, Inc. 
Bus 001 Device 002: ID 0781:5530 SanDisk Corp. Cruzer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
and the latest output of lspci is:
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780L [Radeon 3000]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

```
and the output of lsmod is:
```
Module                  Size  Used by
nls_iso8859_1          12713  1 
cfg80211              484040  0 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
ir_lirc_codec          13021  0 
lirc_dev               19980  1 ir_lirc_codec
ir_mce_kbd_decoder     13214  0 
ir_sanyo_decoder       12839  0 
ir_jvc_decoder         12751  0 
ir_sony_decoder        12713  0 
ir_nec_decoder         12915  0 
ir_rc5_decoder         12710  0 
ir_rc6_decoder         12874  0 
joydev                 17381  0 
hid_generic            12548  0 
rc_rc6_mce             12502  0 
mceusb                 21980  0 
rc_core                28124  12 lirc_dev,ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,mceusb,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder,rc_rc6_mce
r8712u                184158  0 
usbhid                 52616  0 
hid                   106148  3 hid_generic,usbhid
snd_hda_codec_realtek    61438  1 
kvm_amd                59987  0 
kvm                   451511  1 kvm_amd
crct10dif_pclmul       14289  0 
snd_hda_intel          52355  3 
crc32_pclmul           13113  0 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
ghash_clmulni_intel    13259  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
radeon               1514165  3 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13462  0 
k10temp                13126  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
edac_core              62291  0 
snd_timer              29482  2 snd_pcm,snd_seq
edac_mce_amd           22617  0 
fam15h_power           13119  0 
snd                    69238  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
sp5100_tco             13979  0 
ttm                    85115  1 radeon
i2c_piix4              22155  0 
drm_kms_helper         52758  1 radeon
soundcore              12680  1 snd
drm                   302817  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
shpchp                 37032  0 
mac_hid                13205  0 
wmi                    19177  0 
parport_pc             32701  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
usb_storage            62209  1 
pata_atiixp            13271  0 
ahci                   25819  2 
libahci                32168  1 ahci
r8168                 400910  0 

```

---

### Post by Glenn_Sullivan on 2014-04-22
I kept googling my problem until I ran into someone else that had the same unsolvable problem with this usb wifi adapter and they never solved the problem either. Their answer was to by a different wifi adapter. The real problem is that I am trying to connect this adapter to a industrial grade wifi router. This router can broadcast up to 4 SSIDs at the same time on different channels and can use extreme encryption.

---

### Post by praseodym on 2014-04-22
Please check with the new adapter in your 4 ESSID environment:
```

sudo iwlist scan
```

---

