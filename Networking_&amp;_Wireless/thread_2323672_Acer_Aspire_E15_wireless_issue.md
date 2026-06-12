---
title: "Acer Aspire E15 wireless issue"
date: 2016-05-07
forum: Networking &amp; Wireless
---

### Post by binari2 on 2016-05-07
Hello, I am new to Ubuntu (14.04), I googled what is about WLAN issues, I upgraded and downgraded the kernel, and so on. But I didn't find a way to solve this problem. My output is:

```

########## wireless info START ##########

Report from: 07 May 2016 10:55 EEST +0300

Booted last: 07 May 2016 10:27 EEST +0300

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-35-generic #40~14.04.1-Ubuntu SMP Fri Mar 18 16:37:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:098a]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lite-On Communications Inc Device [11ad:0806]

04:00.0 3D controller [0302]: NVIDIA Corporation GK208M [GeForce 920M] [10de:1299] (rev a1)

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0bda:57cc Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 04ca:3015 Lite-On Technology Corp. 
Bus 001 Device 002: ID 248a:8564  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
mxm_wmi                16384  1 nouveau
video                  40960  3 i915,acer_wmi,nouveau
wmi                    20480  3 acer_wmi,mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13050443 (13.0 MB)  TX bytes:1853644 (1.8 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search zte.com.cn

##### network managers ##################

Installed:

    NetworkManager

Running:

root       839     1  0 10:27 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Europe/Istanbul (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   16.224608] r8169 0000:02:00.0 eth0: link down
[   16.224650] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.108156] r8169 0000:02:00.0 eth0: link up
[   35.108165] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

Many thanks in advance...

---

### Post by spandey on 2016-05-07
How about downloading 16.04 and trying it without installing?

---

### Post by jeremy31 on 2016-05-07
> **spandey said:**
> How about downloading 16.04 and trying it without installing?

That doesn't work as the needed firmware is missing but I think 16.04 is the better choice but it would need to be installed

The firmware is on a github site from Kalle Valo [https://github.com/kvalo/ath10k-firmware](https://github.com/kvalo/ath10k-firmware)

The downside to using Kalle's is that the firmware file name is appended with the firmware version, for example QCA9377/hw1.0/firmware-5.bin_WLAN.TF.1.0-00267-1 and the module wants to see QCA9377/hw1.0/firmware-5.bin

I did a github clone of Kalle's and did the renaming

If you want it to work in 14.04, you will need to install the backported kernel modules and firmware
```
sudo apt-get install build-essential linux-headers-generic git
git clone https://github.com/jeremyb31/ath10k-firmware.git
sudo cp ath10k-firmware/ /lib/firmware/ath10k/
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gz
tar -zxvf backports-4.4.2-1.tar.gz
cd backports-4.4.2-1
make defconfig-wifi
make
sudo make install
```

Reboot

The downside of using 14.04 without a 4.4 kernel like 16.04 uses is that after every kernel update you will lose wifi and have to
```
cd backports-4.4.2-1
make clean
make defconfig-wifi
make
sudo make install
```

The 4.4 kernel in 16.04 already supports your wifi it just lacks firmware and the firmware can be installed
```
sudo apt-get install git
git clone https://github.com/jeremyb31/ath10k-firmware.git
sudo cp ath10k-firmware/ /lib/firmware/ath10k/
```

Reboot and wireless will work and no worries about kernel updates

---

### Post by binari2 on 2016-05-09
It works!! It seems that I will stay in my same kernel for long time. Thanks =d>

---

