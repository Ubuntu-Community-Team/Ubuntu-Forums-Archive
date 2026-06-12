---
title: "edimax ew7811un - rtl8188cus, 12.04LTS 32bit kernel 3.2.0-54-generic-pae"
date: 2013-10-13
forum: Networking &amp; Wireless
---

### Post by sh2515 on 2013-10-13
Hi all

This is my 3rd edimax ew7811un - son keeps standing on it - and this one is causing me a headache.
The speed is a 1/10th of what it should be, it's not faulty as I have tested it on another OS.
I use the realtek drivers from their site and have never had a problem with this model before.

I initially thought it was the power saving mode as dmesg kept bring it up but even after turning it off it is still performing the same. 
* see below on howto turn powersaving off. 

iwconfig wlan0
```
wlan0     IEEE 802.11bgn  ESSID:"not for nosey people"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.462 GHz  Access Point: A4:B1:E9:00:7F:3B   
          Bit Rate:65 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=57/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

ifconfig
```
wlan0     Link encap:Ethernet  HWaddr no:t-:fo:r-:no:se:y  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::821f:2ff:feaf:1791/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11734 errors:0 dropped:12891 overruns:0 frame:0
          TX packets:10336 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12291251 (12.2 MB)  TX bytes:1733846 (1.7 MB)
```
lsusb
```
Bus 002 Device 003: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
```

dmesg
```
[ 2770.852758] rtl8192c_dm_RF_Saving(): RF_Save
[ 2800.911870] rtl8192c_dm_RF_Saving(): RF_Normal
[ 2806.924889] rtl8192c_dm_RF_Saving(): RF_Save
[ 2830.971876] rtl8192c_dm_RF_Saving(): RF_Normal
```


*
If you want to turn power saving off from the official Realtek drivers follow this using GUI desktop unless stated.
- download driver from realtek
- uncompress to any location - I have a Drivers folder in my home for this, but doesn't matter if you put it on desktop.
- go into "RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105" or what ever your version is
- go into "Driver"
- double click the tar file but don't extract
- find the "Makefile" in the extraction program window and open in a text editor
find and change this
```
CONFIG_POWER_SAVING            =    y
```
to 
```
CONFIG_POWER_SAVING            =    n
```
save and close and it will auto save the changes back into the tar file.
- go into the terminal and type
```
~/Drivers/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ sudo -i
~/Drivers/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ sh install.sh
```
done

Anyway hope someone can help shed light on why my link speed is being retarded.

Cheers

---

### Post by wildmanne39 on 2013-10-13
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by sh2515 on 2013-10-13
Thank you for taking the time to help me.  I have run the script and here is the file.[ATTACH]246930[/ATTACH]

---

### Post by wildmanne39 on 2013-10-13
Please try:
```
sudo modprobe -rv rtl8192cu
sudo modprobe -v 8192cu
```
watch for errors.
Thanks

---

### Post by sh2515 on 2013-10-14
Thanks for the help. I used both commands and they returned no errors.  The speed is still same slow speed.

---

### Post by wildmanne39 on 2013-10-14
Please post the output of:
```
lsmod
```
so we can see  if it is now using the driver you compiled.
Thanks

---

### Post by sh2515 on 2013-10-14
lsmod
```
Module                  Size  Used by
ip6table_filter        12711  0 
ip6_tables             18432  1 ip6table_filter
ebtable_nat            12695  0 
ebtables               21508  1 ebtable_nat
xt_state               12514  1 
ipt_REJECT             12512  2 
xt_CHECKSUM            12493  1 
iptable_mangle         12646  1 
xt_tcpudp              12531  5 
iptable_filter         12706  1 
ipt_MASQUERADE         12663  4 
iptable_nat            13016  1 
nf_nat                 24959  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19084  4 iptable_nat,nf_nat
nf_conntrack           73847  5 xt_state,ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18106  3 iptable_mangle,iptable_filter,iptable_nat
x_tables               22011  12 ip6table_filter,ip6_tables,ebtables,xt_state,ipt_REJECT,xt_CHECKSUM,iptable_mangle,xt_tcpudp,iptable_filter,ipt_MASQUERADE,iptable_nat,ip_tables
bridge                 79601  0 
stp                    12848  1 bridge
rfcomm                 38139  0 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
binfmt_misc            17292  1 
joydev                 17393  0 
btusb                  17948  1 
nfsd                  229909  2 
nfs                   372273  1 
lockd                  78865  2 nfsd,nfs
fscache                50642  1 nfs
auth_rpcgss            39597  2 nfsd,nfs
nfs_acl                12771  2 nfsd,nfs
sunrpc                215112  12 nfsd,nfs,lockd,auth_rpcgss,nfs_acl
snd_hda_codec_conexant    52521  1 
snd_hda_intel          32719  2 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
8192cu                502561  0 
ath3k                  12825  0 
bluetooth             158447  14 rfcomm,bnep,btusb,ath3k
uvcvideo               67203  0 
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
videodev               86588  1 uvcvideo
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
psmouse                86546  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
i915                  428056  3 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13027  0 
snd                    62218  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
ideapad_laptop         17890  0 
sparse_keymap          13658  1 ideapad_laptop
video                  19115  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56396  0 


```

---

### Post by wildmanne39 on 2013-10-14
Please post the output of:
```
modinfo 8192cu
```
Thanks

---

### Post by sh2515 on 2013-10-14
modinfo
```
filename:       /lib/modules/3.2.0-54-generic-pae/kernel/drivers/net/wireless/8192cu.ko
version:        v3.4.4_4749.20121105
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     657E53E8FE213B566819C54
alias:          usb:v0BDAp8186d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0061d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p624Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp2103d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp2102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v4855p0091d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p1201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFFCd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFFBd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFF8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFFAd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFF9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFF7d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3358d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3359d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp317Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p4902d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v4856p0091d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp5088d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3357d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v4855p0090d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp018Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp818Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       3.2.0-54-generic-pae SMP mod_unload modversions 686 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:charp
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_force_iol:Force to enable IOL (bool)
parm:           rtw_intel_class_mode:The intel class mode [0: off, 1: on] (uint)
parm:           rtw_mc2u_disable:int
```

---

### Post by wildmanne39 on 2013-10-14
Please change the encryption in your router to just wpa2 AES if you have that option then set your wireless settings to match the screenshots.
If it is still slow post a new wireless file so we can see if the changes stuck and what difference they made.
You need to unplug your usb ethernet to test the wireless connection otherwise your wireless will be overridden by the usb ethernet.
Thanks

---

### Post by sh2515 on 2013-10-15
I am really grateful for your patience.

I tried the above, except the usb network is the inbuilt NIC.  I tried the usbwifi on another OS again as I can't see anything wrong, but it is working fine.  I also tried ```
wavemon
``` to see if anything was in the background taking up resources but nothing was running in excess of my actions.

Anyway here is the new wifi file.

[ATTACH]246976[/ATTACH]

---

### Post by wildmanne39 on 2013-10-15
Please post the output of:
```
grep 8192 /etc/modprobe.d/*
```
Thanks

---

### Post by wildmanne39 on 2013-10-15
Please also provide the link to where you got this driver from.
Thanks

---

### Post by chili555 on 2013-10-15
> the usb network is the inbuilt NICPlease explain. Do you have a built-in wireless device as well as the Edimax USB? Please post:```
sudo lshw -C network
lsusb
```

---

### Post by sh2515 on 2013-10-16
grep 8192 /etc/modprobe.d/*
```
:~$ grep 8192 /etc/modprobe.d/*
/etc/modprobe.d/8192cu.conf:options 8192cu rtw_power_mgnt=0 rtw_enusbss=0
/etc/modprobe.d/blacklist.conf:blacklist rtl8192cu
/etc/modprobe.d/blacklist.conf:blacklist rtl8192c_common
```

Link to driver from realtek [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true") 
or the url on it's own is [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

sudo lshw -C network
```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 88:ae:1d:d7:a4:7d
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:3000(size=256) memory:f4910000-f4910fff memory:f4900000-f490ffff memory:f4920000-f493ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:2
       logical name: wlan0
       serial: 80:1f:02:af:17:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu ip=192.168.1.67 multicast=yes wireless=IEEE 802.11bgn
```
lsusb
```
:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 002 Device 004: ID 090c:37b1 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
Bus 006 Device 002: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
```

lspci
```
:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

There is a built in BCM4312 lphy wireless card, but I disabled it in the bios when I got the usb wifi. The BCM4312 is a g network rating and it had intermittent problems, which is why I changed to a usb wifi.
The usb NIC is an error on my behalf, which is why I added the lspci. This is also where the BCM4312 chip comes under.

I tried a live stick - elementery OS - and enabled the BCM4312 for inbuilt wifi and it worked fine. So I will try the live Ubuntu 12.04 to see if an error occurred during a
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by sh2515 on 2013-10-16
just looking at the 
```
sudo lshw -C network
```
it says it is using the _**rtl**_8192cu driver, I am sure it should be using the 8192cu driver
```
configuration: broadcast=yes **[COLOR=#ff0000]driver=rtl8192cu[/COLOR]** ip=192.168.1.67 multicast=yes wireless=IEEE 802.11bgn
```

---

### Post by sh2515 on 2013-10-16
I tried the live usb of Ubuntu 12.04 64bit.  Took some work to get both wireless up and running, however it returned some interesting results.
The inbuilt BCM4312 wireless ran at good speed for g.
However.
Following the guidance on the web for installing the realtek 8192cu drivers for kernel 3.8< the speed was the slow same for the rtl8188cus.

---

### Post by wildmanne39 on 2013-10-17
That driver is to old for 12.04LTS 3 please completely remove it and try this one:
[https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb](https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb)
Download it to your downloads folder which is default then install:
```
cd Downloads
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
```
Reboot

---

### Post by sh2515 on 2013-10-22
Hi

So sorry I haven't replied sooner, I didn't see an e-mail alert to say someone had replied.

I tried the package and got this```
Selecting previously unselected package rtl8192cu-tjp-dkms.
(Reading database ... 889922 files and directories currently installed.)
Unpacking rtl8192cu-tjp-dkms (from rtl8192cu-tjp-dkms_1.6_all.deb) ...
Setting up rtl8192cu-tjp-dkms (1.6) ...
Loading new rtl8192cu-tjp-1.6 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-55-generic-pae
Building for architecture i686
Building initial module for 3.2.0-55-generic-pae
Done.

8192cu:
Running module version sanity check.
Error! Module version v3.4.4_4749.20121105 for 8192cu.ko
is not newer than what is already found in kernel 3.2.0-55-generic-pae (v3.4.4_4749.20121105).
You may override by specifying --force.

depmod....

Backing up initrd.img-3.2.0-55-generic-pae to /boot/initrd.img-3.2.0-55-generic-pae.old-dkms
Making new initrd.img-3.2.0-55-generic-pae
(If next boot fails, revert to initrd.img-3.2.0-55-generic-pae.old-dkms image)
update-initramfs....

DKMS: install completed.
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-55-generic-pae
```

---

