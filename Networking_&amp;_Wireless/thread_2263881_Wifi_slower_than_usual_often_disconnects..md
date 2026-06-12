---
title: "Wifi slower than usual often disconnects."
date: 2015-02-04
forum: Networking &amp; Wireless
---

### Post by josh114 on 2015-02-04
So because of me being a pretty stupid college kid I messed up my computer and accidently deleted my old operating system (windows 8.1), so for the next week or so I'm pretty much stuck with using Ubuntu 14.04 until I get my recovery disk from Toshiba. Ever since I got Ubuntu on my laptop ( Satellite P75 A7100) the wifi has been going really slow and just disconnects for no sound reason. I looked around the forums for a bit and couldn't really find much, or at least understand anything, that could help. I did however run the script...thing...that does a thing. said thing can be seen below:


```
########## wireless info START ##########

Report from: 04 Feb 2015 00:08 CST -0600

Booted last: 03 Feb 2015 23:41 CST -0600

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################


01:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
    Kernel driver in use: iwlwifi

07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:fa72]
    Kernel driver in use: alx

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0bc2:2340 Seagate RSS LLC 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04f2:b41a Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 8087:07dc Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################


##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                189813  0 
mac80211              630669  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  1 toshiba_acpi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr c4:54:44:37:df:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

wlan0     Link encap:Ethernet  HWaddr ac:7b:a1:49:c0:50  
          inet addr:172.24.20.124  Bcast:172.24.23.255  Mask:255.255.252.0
          inet6 addr: fe80::ae7b:a1ff:fe49:c050/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33875650 (33.8 MB)  TX bytes:3099695 (3.0 MB)


##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"ResNet"  
          Mode:Managed  Frequency:5.805 GHz  Access Point: 00:19:92:38:C9:89   
          Bit Rate=43.3 Mb/s   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:52   Missed beacon:0


##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.24.20.1     0.0.0.0         UG    0      0        0 wlan0
172.24.20.0     0.0.0.0         255.255.252.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################


NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        C4:54:44:37:DF:82

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [ResNet] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        AC:7B:A1:49:C0:50

  Capabilities:
    Speed:           28 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    ResNet:          Infra, 00:19:92:38:E4:09, Freq 5240 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    ResNet 5:        Infra, 00:19:92:38:E4:0A, Freq 5240 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    ResNet:          Infra, 00:19:92:38:E4:01, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    ResNet:          Infra, 00:19:92:38:87:61, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    ResNet:          Infra, 00:19:92:38:72:C1, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Cisco_WPS_37039: Infra, C8:D7:19:AB:18:AE, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    ResNet:          Infra, 00:19:92:38:BE:81, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    HP-Print-B1-ENVY 4500 series: Infra, 28:80:23:EF:29:B1, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    ResNet:          Infra, 00:19:92:38:C9:81, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    *ResNet:         Infra, 00:19:92:38:C9:89, Freq 5805 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    ResNet 5:        Infra, 00:19:92:38:72:CA, Freq 5240 MHz, Rate 54 Mb/s, Strength 2 WPA WPA2
    ResNet:          Infra, 00:19:92:38:72:C9, Freq 5240 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    ResNet:          Infra, 00:19:92:38:E7:01, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2

  IPv4 Settings:
    Address:         172.24.20.124
    Prefix:          22 (255.255.252.0)
    Gateway:         172.24.20.1

    DNS:             172.24.0.1
    DNS:             208.67.222.222
    DNS:             208.67.220.220



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
```

---

### Post by Bucky Ball on 2015-02-04
Welcome. Just a thought, not sure if it will help: click on the network icon> edit the wireless you are using>IPv6 tab>set to ignore. IPv4 tab and untick 'Require IPv4 addressing ...' if it is ticked. General tab> make sure 'Automatically connect to this network' and 'All users may connect ...' are enabled. Disable 'Automatically connect to VPN' (unless you are trying to use one).

* Try [THIS]("http://ubuntuforums.org/showthread.php?t=2242147&page=2&p=13112184&viewfull=1#post13112184"). chili555 is one of the resident wireless gurus here, the fix did work and solved this one with your card: Intel Corporation Wireless 7260

* Also, from the same thread, it appears that the bug with your card has been fixed in upstream kernels (3.18). See [HERE]("http://ubuntuforums.org/showthread.php?t=2242147&page=2&p=13158808&viewfull=1#post13158808").

PS: Please use [code] tags instead of [quote] tags for terminal output. Neater, space-saving and easier to read. I have fixed your first post. See the last link in my signature for how to use them. ;)

Good luck.

---

### Post by josh114 on 2015-02-04
Alright thanks, but what does he mean by:

Now we compile the driver.>  	 	sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop/backports-3.16-1
make defconfig-iwlwifi
make
sudo make install 


is there a program I open to do that or?

---

### Post by josh114 on 2015-02-04
Ok well I figured out how to update my kernels, but I'm not sure how I go about the first link thing.

---

### Post by Bucky Ball on 2015-02-04
> **josh114 said:**
> Alright thanks, but what does he mean by:

Now we compile the driver.

is there a program I open to do that or?

If you're still in the dark, you open a terminal and enter the commands one at a time, pressing enter after each. No other program required.

---

