---
title: "ASUS X551MA-SX035D - no wifi"
date: 2014-04-04
forum: Networking &amp; Wireless
---

### Post by Dan_kesson on 2014-04-04
I recently baught an ASUS X551MA-SX035D withous OS.
I installed Ubuntu 13.10 with a USB. Everything seems to work except the wifi. There is a special buttom (Fn-F2) on this laptop for wifi but it doesn't work under Linux.

rfkill list returned:

Wireless LAN
   Soft blocked: no
   Hard blocked: no

I am new to the Linux world and at loss of what to do.

EDIT: Correct name is:ASUS X551MA-SX035D. Title is incorrect. Sorry!

---

### Post by varunendra on 2014-04-05
Welcome to the forums Dan_kesson!

Did rfkill list also returned any interface "phy0"? Was it 'Hard blocked'? If yes, try the solution in this thread : [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

Else, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by bapoumba on 2014-04-05
Edited thread title.

---

### Post by Dan_kesson on 2014-04-05
Thank you for your reply. I ran you script and the wireless-info.txt is as follows:

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

##### kernel #####

Linux dan-X551MA 3.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8821]
    Subsystem: AzureWave Device [1a3b:2161]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5286] (rev 01)

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b404 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 13d3:3414 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 80), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN, NO-IBSS
    (57240 - 63720 @ 2160), (N/A, 0)

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.18
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             193.150.193.150
    DNS:             83.255.245.11

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

##### iwlist channel #####

##### lsmod #####

##### modinfo #####

##### modules #####

lp
rtc

##### blacklist #####

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

##### udev rules #####

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #####

########## wireless info END ############


```

---

### Post by varunendra on 2014-04-05
Your wireless card is very new in the market and so far there is probably no working Linux driver for it as mentioned here : [https://wikidevi.com/wiki/Realtek_RTL8821AE_Combo_Module](https://wikidevi.com/wiki/Realtek_RTL8821AE_Combo_Module)

For a few possible solutions, please see answers here : [http://askubuntu.com/questions/384246/how-do-i-get-a-realtek-8821-wireless-card-working](http://askubuntu.com/questions/384246/how-do-i-get-a-realtek-8821-wireless-card-working)

---

### Post by Dan_kesson on 2014-04-06
The solutions discussed in the link are probably too complicated for me. I guess I have to wait or install Windows.

---

### Post by Ulf_Hegelund on 2014-04-08
Bought the same computer as Dan_kesson yesterday. Since then I have installed Ubuntu 13.10 and have tried, vainly, to get the wifi working. I have tried a number of suggestions found in this forum without success. I understand from varunendras post that it seems i just have to wait until a proper driver comes around. But just in  case, i will post my output from the script wit the humble question: Is there hope for me?

code:
 ########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

##### kernel #####

Linux Saga-Ubuntu-laptop 3.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8821]
    Subsystem: AzureWave Device [1a3b:2161]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5286] (rev 01)

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b404 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 13d3:3414 IMC Networks 
Bus 001 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 80), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN, NO-IBSS
    (57240 - 63720 @ 2160), (N/A, 0)

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Trådbunden anslutning 1] -------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

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

---

### Post by varunendra on 2014-04-08
> **Ulf_Hegelund said:**
> i will post my output from the script wit the humble question: Is there hope for me?

As per the report, you clearly have the same card, so there is only as much hope as discussed in the thread I linked to.

If windows drivers with ndiswrapper don't help, then getting a cheap, supported USB wifi adapter is probably the only solution for now. In fact it is probably the quickest and easiest solution.

---

### Post by praseodym on 2014-04-08
Hi there,

both of you need to install the Mainline-kernel 3.14:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/linux-headers-3.14.0-031400-generic_3.14.0-031400.201403310035_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/linux-headers-3.14.0-031400-generic_3.14.0-031400.201403310035_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/linux-headers-3.14.0-031400_3.14.0-031400.201403310035_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/linux-headers-3.14.0-031400_3.14.0-031400.201403310035_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/linux-image-3.14.0-031400-generic_3.14.0-031400.201403310035_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/linux-image-3.14.0-031400-generic_3.14.0-031400.201403310035_amd64.deb)

Save these files in "Downloads" and install them via:
```

sudo dpkg -i ~/Downloads/*.deb
sudo apt-get install build-essential dkms
```

Reboot.

---

### Post by Ulf_Hegelund on 2014-04-14
Praseodym 

I tried your suggestions. After reboot the screen whent black. Nevermind, reinstall is in progress. Any idea what might have happened?

---

### Post by praseodym on 2014-04-14
Maybe any proprietary VGA driver in use?

---

### Post by Stergios_Galanis on 2014-04-24
> **praseodym said:**
> Maybe any proprietary VGA driver in use?


It simply has an Intel ValleyView Gen7 (rev 0c) graphics card installed. [output using the command "sudo lshw -c video"]
Any ideas as to why upgrading to any kernel from 3.13 and above (3.14 generic to be specific, in order to fix the wireless issue) the screen goes blank (like powered off) right when it is about to show the login screen?
Isn't it supposed to function properly when upgrading the kernel since it's functional in a previous version already?

It only shows the login screen when adding "nomodeset" in grub2 settings upon boot ... and it gets to a very low resolution (4:3)

Any ideas to troubleshoot please?

Thanks!

---

### Post by Stergios_Galanis on 2014-04-24
> **Stergios_Galanis said:**
> It simply has an Intel ValleyView Gen7 (rev 0c) graphics card installed. [output using the command "sudo lshw -c video"]
Any ideas as to why upgrading to any kernel from 3.13 and above (3.14 generic to be specific, in order to fix the wireless issue) the screen goes blank (like powered off) right when it is about to show the login screen?
Isn't it supposed to function properly when upgrading the kernel since it's functional in a previous version already?

It only shows the login screen when adding "nomodeset" in grub2 settings upon boot ... and it gets to a very low resolution (4:3)

Any ideas to troubleshoot please?

Thanks!


Correction ...

under Ubuntu 13.10 with version 3.11.0-19-generic kernel the system says it is Intel Bay Trail graphics.

Thanks!

---

### Post by praseodym on 2014-04-25
Lets check:
```

lspci -nnk | grep -iA2 VGA
lsmod
```

---

