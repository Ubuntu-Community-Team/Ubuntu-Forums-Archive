---
title: "Intermittent wireless problems: Toshiba Satellite L655-S5150 - RTL8188CE 802.11b/g/n"
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by PopsTheSailor on 2013-09-06
My wireless at home has intermittent wireless connectivity issues. Here as my specs the last time it worked without issue was on 11.10. I'm on 13.04 now. I dual boot to Windows 7 and NEVER have issues with connectivity so I'm confident that it is a problem with Ubuntu. If you search for my wireless card in the forums, you will see I am not alone. I've tried much of the stuff listed in other posts but nothing has fixed my problem.

I've tired:
1. Setting my router security to use only WAP2 - no change
2. Issued a modprobe command when I was having problems - no change

It was suggested that I post the output from 
1. sudo lshw -C network
2. iwconfig

Here is the output from **sudo lshw -C network**
******************************************************************
*-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: e0:ca:94:a2:66:52
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.8.0-29-generic firmware=N/A ip=192.168.2.11 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:d4400000-d4403fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c1
       serial: e8:9a:8f:2b:1e:5d
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:d3400000-d343ffff ioport:2000(size=128)
******************************************************************

Output from **iwconfig**
******************************************************************
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"**removed by OP for security reasons**"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: **removed by OP for security reasons**   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr: off
Power Management: off
Link Quality=54/70  Signal level=-56 dBm  
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:106   Missed beacon:0

******************************************************************

All suggestions that have very specific in what I should do / try would be greatly appreciated. I'm not that experienced with linux so please don't give me cryptic suggestions as I won't have a clue how to do them. :)

---

### Post by praseodym on 2013-09-07
Try a driver update according to this:

[http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-treiber-installieren/2/#post-5443987](http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-treiber-installieren/2/#post-5443987)

---

### Post by PopsTheSailor on 2013-09-07
Unfortunately, I can't read German. :(

---

### Post by praseodym on 2013-09-07
There's no need to read ;)
```

sudo apt-get install --reinstall build-essential linux-headers-$(uname -r) linux-headers-generic
wget media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
tar xvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
sudo cp -r firmware/* /lib/firmware  
```
Reboot

---

