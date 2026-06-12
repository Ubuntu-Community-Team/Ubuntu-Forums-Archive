---
title: "Problem with wireless connection Ubuntu 14.04"
date: 2015-01-28
forum: Networking &amp; Wireless
---

### Post by Shawn_Foster on 2015-01-28
Hello,

I am having trouble seeing any wireless connection at all.  I have a Lenovo laptop that had Windows 8 on it and the Wireless worked fine.  I installed Ubuntu 14.04 and now I have to wireless at all.  

The output from the wireless_script is:

```



########## wireless info START ##########


Report from: 28 Jan 2015 15:48 EST -0500


Booted last: 28 Jan 2015 10:00 EST -0500


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 04)
    Subsystem: Lenovo Device [17aa:2210]
    Kernel driver in use: e1000e


04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter [10ec:818b]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:001b]


##### lsusb #############################


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 17ef:1010 Lenovo 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 008: ID 17ef:100f Lenovo 
Bus 003 Device 005: ID 17ef:1010 Lenovo 
Bus 003 Device 004: ID 138a:0017 Validity Sensors, Inc. 
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 007: ID 04ca:7035 Lite-On Technology Corp. 
Bus 003 Device 006: ID 0bda:8761 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


wmi                    19177  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:172.16.0.159  Bcast:172.16.3.255  Mask:255.255.252.0
          inet6 addr: fe80::56ee:75ff:fe3b:ab02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2003231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1081791 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2766745260 (2.7 GB)  TX bytes:127250929 (127.2 MB)
          Interrupt:20 Memory:f1600000-f1620000 


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.0.1      0.0.0.0         UG    0      0        0 eth0
172.16.0.0      0.0.0.0         255.255.252.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search BASVR


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         172.16.0.159
    Prefix:          22 (255.255.252.0)
    Gateway:         172.16.0.1


    DNS:             172.16.0.5


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
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


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
# PCI device 0x8086:0x153a (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[    5.974397] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3


########## wireless info END ############



```

Any thoughts on why I wouldn't see a wireless connection at all.  Even if I go to the system settings and click on Network.  I don't see a wireless connection at all.  

Thanks in advance.  :)

~Shawn

---

### Post by jeremy31 on 2015-01-28
There isn't a driver loaded, so
```
sudo apt-get install linux-headers-generic build-essential git
```
```
git clone https://github.com/lwfinger/rtlwifi_new.git
```
```
cd rtlwifi_new
```
```
make
```
```
sudo make install
```
reboot

---

### Post by Shawn_Foster on 2015-01-28
Perfect!!! That did the trick!  Thanks a lot for your help!

---

### Post by jeremy31 on 2015-01-28
> **Shawn_Foster said:**
> Perfect!!! That did the trick!  Thanks a lot for your help!

Great, try it for a few days and use the forum tools at the top of the thread to mark it solved.

And until your wifi card is supported in tree by the linux kernel used by Ubuntu, you will lose wifi every time the kernel updates until you
```
[COLOR=#000000][FONT=Ubuntu Mono]cd rtlwifi_new
```
```
make clean
```
```
make
```
```
sudo make install
```[/FONT][/COLOR]

---

