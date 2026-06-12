---
title: "Unclaimed wireless network controller after update on 12.04"
date: 2014-02-19
forum: Networking &amp; Wireless
---

### Post by tyrel3 on 2014-02-19
Hi, I'm haivng the same problem as this post:

[http://ubuntuforums.org/showthread.php?t=2206487](http://ubuntuforums.org/showthread.php?t=2206487)

After I installed the new kernel update and restarted, i couldnt use my wireless anymore. 
Because I am new to linux and ubuntu, I am not totally sure what to do, if I need to install a driver or what driver to install. 

This came up when i did the lshw -c command:

>  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 0c
       serial: ac:22:0b:b7:7e:70
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=10.0.0.20 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:62 ioport:e000(size=256) memory:f7900000-f7900fff memory:f2100000-f2103fff
  *-network UNCLAIMED
       description: Network controller
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 73
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:f7800000-f7801fff



I'll greatly appreciate any help.

---

### Post by chili555 on 2014-02-19
And did you have this part as well? > I had to install some kind of special patch for the kernel when I first installed this version of Ubuntu on my laptop a couple of months ago because it had the same problem What does this tell us?```
modinfo iwlwifi | grep 7260
ls -al  /lib/firmware | grep 7260
```Thanks.

---

### Post by tyrel3 on 2014-02-20
I installed the kernel patch right before this problem. When I first installed Ubuntu there didnt seem to be a kernel patch. 

Here is what I got from the code:

firmware:       iwlwifi-[COLOR=#ff0000]7260[/COLOR]-7.ucode


7260 there is in red...

---

### Post by chili555 on 2014-02-20
However, if the *modinfo* step doesn't produce any result, then the driver doesn't claim your device.  I suggest you download this to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.xz](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.xz) Right-click it and select 'Extract Here.' Now open a terminal and do:

```
cd ~/Desktop/backports-3.13.2-1/
make defconfig-iwlwifi
make
sudo make install

```Reboot and tell us if it's working as expected.

---

### Post by tyrel3 on 2014-02-20
Ok entered sudo make install and rebooted but still not able to use my wireless.

---

### Post by chili555 on 2014-02-20
Let's see:```
modinfo iwlwifi | grep -e version -e 7260
sudo modprobe iwlwifi
dmesg | grep iwl
```Were there errors, warnings, etc., as you compiled the package?

---

### Post by tyrel3 on 2014-02-20
I didnt see any warnings or errors before no.

Here is the result of that:

version:        backported from Linux (v3.13.2-0-gfd82174) using backports v3.13.2-1-0-gaef13bc
version:        in-tree:d
firmware:       iwlwifi-7260-7.ucode
srcversion:     C0571F3796F945AB0945BB5
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
tyrel@HODOR:~$ sudo modprobe iwlwifi
tyrel@HODOR:~$ dmesg | grep iwl
[    8.191860] iwlwifi 0000:03:00.0: irq 63 for MSI/MSI-X
[    8.363143] iwlwifi 0000:03:00.0: request for firmware file 'iwlwifi-7260-7.ucode' failed.
[    8.363190] iwlwifi 0000:03:00.0: no suitable firmware found!

---

### Post by chili555 on 2014-02-20
It looks like there is a problem with the firmware. May I now see:```
ls [COLOR="#FF0000"]-al[/COLOR]  /lib/firmware | grep 7260
```

---

### Post by tyrel3 on 2014-02-20
hmm I'm trying that command but nothing is happening.

---

### Post by tyrel3 on 2014-02-20
i did 

ls -al /lib/firmware 

and got this:

total 20296
drwxr-xr-x 65 root root    4096 Feb 18 21:52 .
drwxr-xr-x 23 root root    4096 Feb 20 19:45 ..
drwxr-xr-x 27 root root    4096 Feb  4 06:59 3.11.0-15-generic
drwxr-xr-x 27 root root    4096 Feb 18 21:52 3.11.0-17-generic
drwxr-xr-x  2 root root    4096 Feb  4 07:00 3com
drwxr-xr-x  2 root root    4096 Feb  4 07:00 acenic
drwxr-xr-x  2 root root    4096 Feb  4 07:00 adaptec
drwxr-xr-x  2 root root    4096 Feb  4 07:00 advansys
-rw-r--r--  1 root root   50698 Nov  8  2012 agere_ap_fw.bin
-rw-r--r--  1 root root   65046 Nov  8  2012 agere_sta_fw.bin
-rw-r--r--  1 root root   22622 Jul 12  2013 aic94xx-seq.fw
drwxr-xr-x  2 root root    4096 Feb  4 07:00 amd-ucode
drwxr-xr-x  6 root root    4096 Feb  4 07:00 ar3k
-rw-r--r--  1 root root   70624 Nov  8  2012 ar7010_1_1.fw
-rw-r--r--  1 root root   70624 Nov  8  2012 ar7010.fw
-rw-r--r--  1 root root   83968 Nov  8  2012 ar9170-1.fw
-rw-r--r--  1 root root    3508 Nov  8  2012 ar9170-2.fw
-rw-r--r--  1 root root   15960 Jul 12  2013 ar9170.fw
-rw-r--r--  1 root root   51312 Nov  8  2012 ar9271.fw
drwxr-xr-x  2 root root    4096 Feb  4 07:00 asihpi
-rw-r--r--  1 root root  246804 Jul 12  2013 ath3k-1.fw
drwxr-xr-x  5 root root    4096 Feb  4 07:00 ath6k
-rw-r--r--  1 root root   30348 Jul 12  2013 atmel_at76c502_3com.bin
-rw-r--r--  1 root root   31764 Jul 12  2013 atmel_at76c502.bin
-rw-r--r--  1 root root   31764 Jul 12  2013 atmel_at76c502d.bin
-rw-r--r--  1 root root   31776 Jul 12  2013 atmel_at76c502e.bin
-rw-r--r--  1 root root   35180 Jul 12  2013 atmel_at76c504_2958.bin
-rw-r--r--  1 root root   39928 Jul 12  2013 atmel_at76c504a_2958.bin
-rw-r--r--  1 root root   31748 Jul 12  2013 atmel_at76c504.bin
-rw-r--r--  1 root root   31824 Jul 12  2013 atmel_at76c506.bin
-rw-r--r--  1 root root    9726 Nov  8  2012 atmsar11.fw
drwxr-xr-x  2 root root    4096 Feb  4 07:00 av7110
drwxr-xr-x  2 root root    4096 Feb  4 07:00 bnx2
drwxr-xr-x  2 root root    4096 Feb  4 07:00 bnx2x
drwxr-xr-x  2 root root    4096 Feb  4 07:00 brcm
-rw-r--r--  1 root root   13424 Jul 12  2013 carl9170-1.fw
drwxr-xr-x  3 root root    4096 Feb  4 07:00 cis
drwxr-xr-x  2 root root    4096 Feb  4 07:00 cpia2
drwxr-xr-x  2 root root    4096 Feb  4 07:00 cxgb3
drwxr-xr-x  2 root root    4096 Feb  4 07:00 cxgb4
drwxr-xr-x  2 root root    4096 Feb  4 07:00 dabusb
drwxr-xr-x  2 root root    4096 Feb  4 07:00 dsp56k
-rw-r--r--  1 root root   12401 Nov  8  2012 dvb-fe-xc5000-1.6.114.fw
-rw-r--r--  1 root root   33768 Nov  8  2012 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root   50222 Nov  8  2012 dvb-usb-terratec-h5-drxk.fw
drwxr-xr-x  2 root root    4096 Feb  4 07:00 e100
drwxr-xr-x  2 root root    4096 Feb  4 07:00 ea
drwxr-xr-x  2 root root    4096 Feb  4 07:00 edgeport
drwxr-xr-x  2 root root    4096 Feb  4 07:00 emi26
drwxr-xr-x  2 root root    4096 Feb  4 07:00 emi62
drwxr-xr-x  2 root root    4096 Feb  4 07:00 ene-ub6250
drwxr-xr-x  2 root root    4096 Feb  4 07:00 ess
-rw-r--r--  1 root root  180776 Nov  8  2012 f2255usb.bin
-rw-r--r--  1 root root   35068 Nov  8  2012 GPL-3
drwxr-xr-x  2 root root    4096 Feb 14  2012 hp
-rw-r--r--  1 root root   72992 Nov  8  2012 htc_7010.fw
-rw-r--r--  1 root root   51272 Nov  8  2012 htc_9271.fw
-rw-r--r--  1 root root 1251036 Nov  8  2012 i2400m-fw-usb-1.4.sbcf
-rw-r--r--  1 root root 1334532 Nov  8  2012 i2400m-fw-usb-1.5.sbcf
-rw-r--r--  1 root root 1531932 Nov  8  2012 i6050-fw-usb-1.5.sbcf
drwxr-xr-x  2 root root    4096 Feb  4 07:00 intel
-rw-r--r--  1 root root   34304 Nov  8  2012 intelliport2.bin
-rw-r--r--  1 root root  209190 Jul 12  2013 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 Jul 12  2013 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 Jul 12  2013 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 Jul 12  2013 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 Jul 12  2013 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 Jul 12  2013 ipw2200-sniffer.fw
drwxr-xr-x  2 root root    4096 Feb  4 07:00 isci
-rw-r--r--  1 root root  337520 Nov  8  2012 iwlwifi-1000-5.ucode
-rw-r--r--  1 root root  337572 Nov  8  2012 iwlwifi-100-5.ucode
-rw-r--r--  1 root root  689680 Nov  8  2012 iwlwifi-105-6.ucode
-rw-r--r--  1 root root  701228 Nov  8  2012 iwlwifi-135-6.ucode
-rw-r--r--  1 root root  695876 Nov  8  2012 iwlwifi-2000-6.ucode
-rw-r--r--  1 root root  707392 Nov  8  2012 iwlwifi-2030-6.ucode
-rw-r--r--  1 root root  150100 Nov  8  2012 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187972 Nov  8  2012 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  340696 Nov  8  2012 iwlwifi-5000-5.ucode
-rw-r--r--  1 root root  337400 Nov  8  2012 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  454608 Nov  8  2012 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  444128 Nov  8  2012 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root  677296 Nov  8  2012 iwlwifi-6000g2a-6.ucode
-rw-r--r--  1 root root  679436 Nov  8  2012 iwlwifi-6000g2b-6.ucode
-rw-r--r--  1 root root  469780 Nov  8  2012 iwlwifi-6050-5.ucode
drwxr-xr-x  2 root root    4096 Feb  4 07:00 kaweth
drwxr-xr-x  2 root root    4096 Feb  4 07:00 keyspan
drwxr-xr-x  2 root root    4096 Feb  4 07:00 keyspan_pda
drwxr-xr-x  2 root root    4096 Feb  4 07:00 korg
-rw-r--r--  1 root root  118888 Nov  8  2012 lbtf_usb.bin
-rw-r--r--  1 root root     262 Nov  8  2012 lgs8g75.fw
drwxr-xr-x  2 root root    4096 Feb  4 07:00 libertas
drwxr-xr-x  2 root root    4096 Feb  4 07:00 matrox
drwxr-xr-x  2 root root    4096 Feb  4 07:00 mrvl
-rw-r--r--  1 root root   13847 Nov  8  2012 mts_cdma.fw
-rw-r--r--  1 root root   14067 Nov  8  2012 mts_edge.fw
-rw-r--r--  1 root root   13847 Nov  8  2012 mts_gsm.fw
-rw-r--r--  1 root root   13769 Nov  8  2012 mts_mt9234mu.fw
-rw-r--r--  1 root root   13769 Nov  8  2012 mts_mt9234zba.fw
-rw-r--r--  1 root root   51596 Jul 12  2013 mwl8335_duplex.fw
drwxr-xr-x  2 root root    4096 Feb  4 07:00 mwl8k
-rw-r--r--  1 root root  377784 Nov  8  2012 myri10ge_ethp_z8e.dat
-rw-r--r--  1 root root  367464 Nov  8  2012 myri10ge_eth_z8e.dat
-rw-r--r--  1 root root  563592 Nov  8  2012 myri10ge_rss_ethp_z8e.dat
-rw-r--r--  1 root root  553192 Nov  8  2012 myri10ge_rss_eth_z8e.dat
drwxr-xr-x  2 root root    4096 Feb  4 07:00 myricom
-rw-r--r--  1 root root   15664 Jul 12  2013 NPE-B
-rw-r--r--  1 root root   15664 Jul 12  2013 NPE-C
drwxr-xr-x  2 root root    4096 Feb  4 07:00 ositech
-rw-r--r--  1 root root 1825359 Jul 12  2013 phanfw.bin
-rw-r--r--  1 root root   76802 Nov  8  2012 ql2100_fw.bin
-rw-r--r--  1 root root   84566 Nov  8  2012 ql2200_fw.bin
-rw-r--r--  1 root root  123170 Jul 12  2013 ql2300_fw.bin
-rw-r--r--  1 root root  132978 Jul 12  2013 ql2322_fw.bin
-rw-r--r--  1 root root  228056 Jul 12  2013 ql2400_fw.bin
-rw-r--r--  1 root root  199776 Jul 12  2013 ql2500_fw.bin
drwxr-xr-x  2 root root    4096 Feb  4 07:00 qlogic
drwxr-xr-x  2 root root    4096 Feb  4 07:00 r128
drwxr-xr-x  2 root root    4096 Feb  4 07:00 radeon
-rw-r--r--  1 root root    8192 Nov  8  2012 rt2561.bin
-rw-r--r--  1 root root    8192 Nov  8  2012 rt2561s.bin
-rw-r--r--  1 root root    8192 Nov  8  2012 rt2661.bin
-rw-r--r--  1 root root    8192 Nov  8  2012 rt2860.bin
-rw-r--r--  1 root root    8192 Nov  8  2012 rt2870.bin
lrwxrwxrwx  1 root root      10 Feb 16 17:27 rt3070.bin -> rt2870.bin
-rw-r--r--  1 root root    4096 Nov  8  2012 rt3071.bin
lrwxrwxrwx  1 root root      10 Feb 16 17:27 rt3090.bin -> rt2860.bin
-rw-r--r--  1 root root    4096 Nov  8  2012 rt3290.bin
-rw-r--r--  1 root root    2048 Nov  8  2012 rt73.bin
drwxr-xr-x  2 root root    4096 Feb  4 07:00 RTL8192E
drwxr-xr-x  2 root root    4096 Feb  4 07:00 RTL8192SE
drwxr-xr-x  2 root root    4096 Feb  4 07:00 rtl_nic
drwxr-xr-x  2 root root    4096 Feb  4 07:00 rtlwifi
-rw-r--r--  1 root root    9508 Jul 12  2013 s2250.fw
-rw-r--r--  1 root root    1092 Jul 12  2013 s2250_loader.fw
drwxr-xr-x  2 root root    4096 Feb  4 07:00 sb16
drwxr-xr-x  2 root root    4096 Feb  4 07:00 scripts
drwxr-xr-x  2 root root    4096 Feb  4 07:00 slicoss
drwxr-xr-x  2 root root    4096 Feb  4 07:00 sun
drwxr-xr-x  2 root root    4096 Feb  4 07:00 sxg
-rw-r--r--  1 root root   37028 Nov  8  2012 TDA7706_OM_v2.5.1_boot.txt
-rw-r--r--  1 root root   10509 Nov  8  2012 TDA7706_OM_v3.0.2_boot.txt
drwxr-xr-x  2 root root    4096 Feb  4 07:00 tehuti
-rw-r--r--  1 root root   13765 Nov  8  2012 ti_3410.fw
-rw-r--r--  1 root root   13764 Nov  8  2012 ti_5052.fw
drwxr-xr-x  2 root root    4096 Feb  4 07:00 ti-connectivity
drwxr-xr-x  2 root root    4096 Feb  4 07:00 tigon
-rw-r--r--  1 root root   51972 Nov  8  2012 tlg2300_firmware.bin
-rw-r--r--  1 root root    7614 Nov  8  2012 tr_smctr.bin
drwxr-xr-x  2 root root    4096 Feb  4 07:00 ttusb-budget
drwxr-xr-x  2 root root    4096 Feb  4 07:00 ueagle-atm
drwxr-xr-x  2 root root    4096 Feb  4 07:00 usbdux
-rw-r--r--  1 root root     999 Nov  8  2012 usbduxfast_firmware.bin
-rw-r--r--  1 root root    1770 Nov  8  2012 usbdux_firmware.bin
-rw-r--r--  1 root root    8192 Nov  8  2012 usbduxsigma_firmware.bin
-rw-r--r--  1 root root   16382 Nov  8  2012 v4l-cx231xx-avcore-01.fw
-rw-r--r--  1 root root  141200 Nov  8  2012 v4l-cx23418-apu.fw
-rw-r--r--  1 root root  158332 Nov  8  2012 v4l-cx23418-cpu.fw
-rw-r--r--  1 root root   16382 Nov  8  2012 v4l-cx23418-dig.fw
-rw-r--r--  1 root root  262144 Jul 12  2013 v4l-cx2341x-dec.fw
-rw-r--r--  1 root root  376836 Jul 12  2013 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root  155648 Jul 12  2013 v4l-cx2341x-init.mpg
-rw-r--r--  1 root root   16382 Dec 11  2012 v4l-cx23885-avcore-01.fw
-rw-r--r--  1 root root   16382 Jul 12  2013 v4l-cx23885-enc.fw
-rw-r--r--  1 root root   16382 Nov  8  2012 v4l-cx25840.fw
-rw-r--r--  1 root root    8192 Jul 12  2013 v4l-pvrusb2-24xxx-01.fw
-rw-r--r--  1 root root    8192 Jul 12  2013 v4l-pvrusb2-29xxx-01.fw
drwxr-xr-x  2 root root    4096 Feb  4 07:00 vicam
-rw-r--r--  1 root root   11341 Nov  8  2012 vntwusb.fw
drwxr-xr-x  2 root root    4096 Feb  4 07:00 vxge
-rw-r--r--  1 root root    5208 Jul 12  2013 WHENCE.ubuntu
-rw-r--r--  1 root root   23554 Nov  8  2012 whiteheat.fw
-rw-r--r--  1 root root    5626 Nov  8  2012 whiteheat_loader.fw
drwxr-xr-x  2 root root    4096 Feb  4 07:00 yam
drwxr-xr-x  2 root root    4096 Feb  4 07:00 yamaha
-rw-r--r--  1 root root   62484 Jul 12  2013 zd1201-ap.fw
-rw-r--r--  1 root root   70612 Jul 12  2013 zd1201.fw
drwxr-xr-x  2 root root    4096 Feb  4 07:00 zd1211

---

### Post by chili555 on 2014-02-20
Funny. In post #3 it was there, yes? Let's try to fix it. With a temporary wired ethernet connection:```
cd /lib/firmware
sudo wget https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode
```Reboot.

---

### Post by tyrel3 on 2014-02-22
Yes! It's back! 
[IMG]http://2.bp.blogspot.com/-S7zLndndNKQ/T9-WM0mF2HI/AAAAAAAAA58/1b1CTK30DhQ/s1600/youre-the-best.gif[/IMG]

---

### Post by chili555 on 2014-02-22
You made my day! Thanks for your kind appreciation.

Whenever a later kernel version is installed by Update manager, recompile:```
cd ~/Desktop/backports-3.13.2-1/
[COLOR="#FF0000"]make clean[/COLOR]
make defconfig-iwlwifi
make
sudo make install
```Please retain the files and these instructions for that time. 

Please use thread tools at the top to mark Solved.

---

