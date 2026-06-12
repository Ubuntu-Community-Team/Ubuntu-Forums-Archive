---
title: "Asus X510UQ WiFi adaptor not showing up"
date: 2018-04-21
forum: Networking &amp; Wireless
---

### Post by davedub on 2018-04-21
Hi All,

I've installed Ubuntu 16.04 LTS on my Asus X510UQ. The wireless card doesn't show up - when I click the network symbol, it reports 'No network devices available' (there is no ethernet connection port on the machine, which means I've not managed to run sudo apt-get update yet)

 ~ I have tried fn + f2. No change.
 ~ I have run the wireless-info script as found at [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) and pasted the output below.

Any help much appreciated!

 - davedub

```



########## wireless info START ##########


Report from: 21 Apr 2018 12:31 EDT -0400


Booted last: 21 Apr 2018 00:00 EDT -0400


Script from: 10 Jan 2018 20:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 78)
    Subsystem: Intel Corporation Device [8086:0010]


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0a2b Intel Corp. 
Bus 001 Device 002: ID 13d3:5a07 IMC Networks 
Bus 001 Device 004: ID 0781:5590 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  1 nouveau
wmi                    20480  3 mxm_wmi,nouveau,asus_wmi
video                  40960  3 i915_bpo,nouveau,asus_wmi


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:155264 (155.2 KB)  TX bytes:155264 (155.2 KB)


##### iwconfig ##########################


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2596     1  0 12:24 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


##### Netplan config ####################


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


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


##### dmesg #############################


########## wireless info END ############



```

---

### Post by praseodym on 2018-04-21
Please check
```

sudo modprobe -v iwlwifi
dmesg | grep iwl
```

---

### Post by davedub on 2018-04-22
Thank you for the reply. I ran those commands. Not much output:

```

focus@focus-X510UQ:~$ sudo modprobe -v iwlwifi
[sudo] password for focus: 
insmod /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 
focus@focus-X510UQ:~$ dmesg | grep iwl
focus@focus-X510UQ:~$ 

```

---

### Post by praseodym on 2018-04-22
Ok, seems that this device is too new for kernel 4.4. Try 4.13

---

### Post by davedub on 2018-04-22
I've checked through for instructions on how to do a kernel downgrade, but they all seem to require an established internet connection.
I then checked for an older version of the Ubuntu installer, as I thought I'd be able to downgrade by re-installing an older version. However, I have not been able to identify which iso would contain kernel 4.13.

 ~ Could you advise on how I can downgrade to kernel 4.13 without an internet connection?

---

### Post by user_of_gnomes on 2018-04-23
Use a cabled connection.

---

### Post by davedub on 2018-04-24
Ah - I did mention in the OP: "[COLOR=#000000]there is no ethernet connection port on the machine"

So would that make [/COLOR][COLOR=#000000]downgrading to kernel 4.13 (i.e. without an internet connection) impossible?[/COLOR]

---

### Post by davedub on 2018-04-28
OK, so I've bought a USB Ethernet adaptor and have a connection. 

I'm now trying to downgrade kernel from 4.4 to 4.13. However, I am having no luck in doing so. I finally found a way to get the grub menu up on boot (i.e. edited the /etc/default/grub file), but cannot find clear instructions on how I can get different kernel options to show on the grub menu.

Any advice on how I can downgrade kernel from 4.4 to 4.13 gratefully received!

---

### Post by praseodym on 2018-04-28
It is not a downgrade, but an upgrade!

---

