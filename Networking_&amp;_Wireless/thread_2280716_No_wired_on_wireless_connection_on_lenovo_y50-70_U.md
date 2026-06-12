---
title: "No wired on wireless connection on lenovo y50-70 UDH with fresh ubuntu 14.04"
date: 2015-06-01
forum: Networking &amp; Wireless
---

### Post by Emil_Dafinov on 2015-06-01
Hello, 
I just got a new Lenovo y50-70 UHD and I've been trying to connect it to the internet with no success. Both wired and wireless don't seem to work.
Here is my wireless-info:
```



########## wireless info START ##########


Report from: 31 May 2015 06:53 EDT -0400


Booted last: 31 May 2015 06:26 EDT -0400


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Lenovo Device [17aa:0623]


09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380d]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0489:e07a Foxconn / Hon Hai 
Bus 003 Device 003: ID 5986:055e Acer, Inc 
Bus 003 Device 002: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


mxm_wmi                13021  1 nouveau
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop
wmi                    19193  2 mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


    NetworkManager


Running:


root       807     1  0 06:26 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


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


Region: America/New_York (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN


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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[   19.448279] nouveau 0000:01:00.0: Direct firmware load failed with error -2 (repeated 2 times)


########## wireless info END ############ 



```

I tried installing the [COLOR=#000000][FONT=Ubuntu Mono]bcmwl-kernel-source[/FONT][/COLOR] , but it didn't make any difference  :( Would anyone have an idea about what I can do to fix this?

Thanks in advance

---

### Post by wildmanne39 on 2015-06-02
Hi, the driver did not install because you do not have an internet connection, you can install it without an internet connection by doing the following:

The driver and its dependency dkms are on the installation DVD or USB. Insert the install media and navigate to pool > restricted > b > bcmwl and drag and drop the bcmwl deb package to your desktop. Do the same with pool > main > d > dkms. Now install the deb files. Open a terminal and:
```
cd ~/Desktop
sudo dpkg -i *.deb
sudo modprobe wl
```
Thanks

---

### Post by Emil_Dafinov on 2015-06-02
I did install the driver as you suggested. I tried ```
 sudo modprobe wl
``` but I got an error saying ```


modprobe: FATAL: Module wl not found
```

---

### Post by jeremy31 on 2015-06-02
You will likely need to download the newer version of bcmwl-kernel-source from a mirror at [http://packages.ubuntu.com/utopic/amd64/bcmwl-kernel-source/download](http://packages.ubuntu.com/utopic/amd64/bcmwl-kernel-source/download)

The one on the disk is likely to be 6.30.223.141 and 6.30.223.248 is needed with the 3.16 kernel

---

### Post by wildmanne39 on 2015-06-02
I am not sure what version is on the disk but did you run the cd and access it as described in my post or did you run the live version and boot to the cd? Did you get any errors while installing the driver besides the one you posted or did you not watch for errors?
Thanks

---

