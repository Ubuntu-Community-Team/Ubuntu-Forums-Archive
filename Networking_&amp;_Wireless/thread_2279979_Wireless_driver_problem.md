---
title: "Wireless driver problem"
date: 2015-05-27
forum: Networking &amp; Wireless
---

### Post by evy2 on 2015-05-27
Hi everyone, 

I just installed Ubuntu 14.04 on my new hard drive. Since there is no Wireless Driver present I tried to nstall the following packages but it doesn't work:

linux-headers-3.16.0-38-generic_3.16.0-38.52_i386.deb
linux-headers-3.16.0-38-_3.16.0-38.52_all.deb

bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu3_i386.deb
dkms_2.2.3-2ubuntu3_all.deb

Probably I'm not using the right packages. 

Here some laptop info: Linux Boltop 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Thank you so much in advance! 


Evy

---

### Post by Bucky Ball on 2015-05-27
Can you plug in an ethernet cable and get online? Do an update, reboot. Any wireless messages? Not a good idea to start throwing in linux .debs when you're not quite sure what they are doing. Could just confuse the issue. 

After an update have a look in Additional Drivers. Anything there for wireless? B43 or STA?

Do you actually know what card you have? You don't mention it which gives us little chance of helping. Please give us the output of:

```
sudo lshw -C network
```

Please put terminal output in [code] tags. See the last link in my signature for how.

---

### Post by evy2 on 2015-05-27
Thank you so much for your answer. I used those .deb files because I had this problem once before and then it worked, but you are right, I shouldn't just juggle with these .deb files. I have an ethernet cable so I am connected to the internet right now. I did an update en rebooted my system. Below you can find the output from the terminal. 

```

  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: d4:be:d9:68:6d:24
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.13-3 ip=134.184.69.139 latency=0 link=yes multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:44 memory:f7e00000-f7e1ffff memory:f7e39000-f7e39fff ioport:f080(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: BCM43228 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d03fff

```

---

### Post by wildmanne39 on 2015-05-27
Please click on the wireless script in my signature and post the file it creates here using code tags.
Thanks

---

### Post by beastlife42 on 2015-05-27
Hello,
I could have my wireless connection on Acer Aspire V3-471G with the card BCM43228 all in good order after upgrading from Trusty Thar to kernel Wily 4.0.4 by installing the package bcmwl - 6.30.223.248+bdcom-0ubuntu3.

To achieve this, I downloaded [http://launchpadlibrarian.net/206246268/bcmwl-kernel-source_6.30.223.248%2Bbdcom-0ubuntu3_amd64.deb](http://launchpadlibrarian.net/206246268/bcmwl-kernel-source_6.30.223.248%2Bbdcom-0ubuntu3_amd64.deb) and used the command dpkg in the Terminal to build the module on my machine. Hope this can help you as I see you have the same BCM43228 on your machine.

---

### Post by evy2 on 2015-05-29
Thank you for your answer. Below you can find the output of the .txt file. 

```


########## wireless info START ##########

Report from: 29 May 2015 11:43 CEST +0200

Booted last: 27 May 2015 12:41 CEST +0200

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Dell Device [1028:0535]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Dell Device [1028:0014]

0b:00.0 SD Host controller [0805]: O2 Micro, Inc. Device [1217:8221] (rev 05)

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 413c:8197 Dell Computer Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
6: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
wmi                    19193  1 dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:134.184.69.139  Bcast:134.184.69.255  Mask:255.255.255.0
          inet6 addr: fe80::d6be:d9ff:fe68:6d24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1649064 errors:0 dropped:11346 overruns:0 frame:0
          TX packets:302222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:711627823 (711.6 MB)  TX bytes:47074368 (47.0 MB)
          Interrupt:20 Memory:f7e00000-f7e20000 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         134.184.69.100  0.0.0.0         UG    0      0        0 eth0
134.184.69.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       750     1  0 May27 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

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
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         134.184.69.139
    Prefix:          24 (255.255.255.0)
    Gateway:         134.184.69.100

    DNS:             134.184.250.7
    DNS:             134.184.15.13

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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Europe/Brussels (based on set time zone)

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

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############


```

---

### Post by evy2 on 2015-05-29
Thank you Beastlife42 for your answer but unfortunately it didn't work for me...

---

### Post by wildmanne39 on 2015-05-29
Please do:
```
sudo apt-get install bcmwl-kernel-source
```
watch for errors I suspect that the installation of the driver will fail, if it does post the complete output here.
Thanks

---

### Post by evy2 on 2015-06-01
It worked! Thank you so much!

---

### Post by wildmanne39 on 2015-06-01
Glad to help.
Enjoy!

---

