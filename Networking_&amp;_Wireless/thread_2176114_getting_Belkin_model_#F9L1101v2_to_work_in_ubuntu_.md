---
title: "getting Belkin model #F9L1101v2 to work in ubuntu 13.04"
date: 2013-09-22
forum: Networking &amp; Wireless
---

### Post by dosodavis on 2013-09-22
I found this:

[COLOR=#ff0000]Fortunately, I believe there is a way. Please get a working ethernet  connection and copy and paste these commands, each one at a time.[/COLOR][COLOR=#ff0000] 	[/COLOR][COLOR=#ff0000]Code:
sudo apt-get install build-essential linux-headers-generic git
git clone [https://github.com/lwfinger/rtl8192du.git](https://github.com/lwfinger/rtl8192du.git) cd rtl8192du
make
sudo make install
sudo modprobe 8192du[/COLOR]



When I do this command: [COLOR=#0000cd]"git clone https://github.com/lwfinger/rtl8192du.git"[/COLOR] this is what I get:
Cloning into 'rtl8192du'...
error: Failed connect to github.com:8000; Connection timed out while accessing [https://github.com/lwfinger/rtl8192du.git/info/refs?service=git-upload-pack](https://github.com/lwfinger/rtl8192du.git/info/refs?service=git-upload-pack)
fatal: HTTP request failed

I also tried having the sight open while running the command and it did the same thing.

---

### Post by varunendra on 2013-09-23
Welcome to the forums dosodavis :)

The [post=12688576]post[/post] you copied the stated solution was dealing with a different adapter. Are you sure yours is the same? Does lsusb (when the adapter is plugged in) show -
```
ID 20f4:664b
``` in the output?

If not, you may need a different driver.

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It'll give us almost all the info required to find a solution to your problem. Run the script when the adapter is plugged in.

---

### Post by dosodavis on 2013-09-26
This is what I get:

~$ lsusb

Bus 001 Device 003: ID 050d:110a Belkin Components 
Bus 002 Device 002: ID 0402:7675 ALi Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hu
here is the wireless script result:

Linux 3.8.0-30-generic #44-UbuntuMP Thu Aug 22 20:52:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

06:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0598]
    Kernel driver in use: atl1c
07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel driver in use: wl

***** lsusb *****

Bus 001 Device 002: ID 
Bus 001 Device 003: ID 050d:110a Belkin Components 
Bus 002 Device 002: ID 0402:7675 ALi Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

eth1      IEEE 802.11abg  ESSID:"ASUS"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

wl                   3074449  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
cfg80211              510937  1 wl

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth1  [ASUS] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *ASUS:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA2
    Comtrendc560:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 9 WEP

  IPv4 Settings:
    Address:         192.168.1.67
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"ASUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 000441535553
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFD191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DDAC0050F204104A0001101044000102103B00010310470010CEFA0E6ADC53B98C6470B42F04EBBFBC102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000752542D4E3636551042001137343A64303A32623A35633A65353A33301054000800060050F20400011011000752542D4E363655100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180202F03C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Comtrendc560"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 000C436F6D7472656E6463353630
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000


***** resolv.conf *****

nameserver

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.8.0-30-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     6E2531203CF49EB24353067
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.8.0-30-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


***** udev rules *****

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:15.2/0000:06:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.3/0000:07:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.3/0000:07:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

***** dmesg *****

[   14.098574] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.335706] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   14.523388] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   15.640841] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x040213)
[ 2824.193657] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 2824.193676] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 2824.193699] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 2824.193707] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 2824.193725] ERROR @wl_dev_intvar_get : error (-1)
[ 2824.193733] ERROR @wl_cfg80211_get_tx_power : error (-1)

****************** done ******************

---

### Post by varunendra on 2013-09-26
Aha, happy smileys instead of codes :P

Please always use '**Code**' box to post commands & terminal outputs. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how. You should edit your above post afterwards to wrap the ouputs within code tags.

Onto the problem -
> **dosodavis said:**
> Bus 001 Device 003: ID 050d:110a Belkin Components

Even though you have a different card, your device is indeed supported by the same driver "rtl8192du" and the recommended procedure to install it was the same post that you were originally following.

So not sure if it was a connection fault or possibly a command error on your part. Can you open this site : [https://github.com/lwfinger/rtl8192du](https://github.com/lwfinger/rtl8192du) ?

If yes, there should be no issues in cloning it. Please make sure your internet connection is working and you can open the above page. Then do *(a shameless copy-paste from Dr. Chilli's [post=12688576]post[/post])* -
```
sudo apt-get install build-essential linux-headers-generic git
git clone https://github.com/lwfinger/rtl8192du.git
cd rtl8192du
make
sudo make install
sudo modprobe 8192du
```
If there are any errors again, try downloading the driver as a zip file ([https://github.com/lwfinger/rtl8192du/archive/master.zip](https://github.com/lwfinger/rtl8192du/archive/master.zip)) and post back for further steps.

---

### Post by dosodavis on 2013-09-26
Yes I can open that site.
I'm not sure what you mean by a "shameless" copy-paste

---

### Post by varunendra on 2013-09-26
> **dosodavis said:**
> I'm not sure what you mean by a "shameless" copy-paste
Nothing about you, it is what I did (I shamelessly copied all the commands from his posts :P).

You have to enter those commnads, one-by-one, in a terminal (ctrl-alt-T). If some error occurs, post back the error, and try downloading the zip file I linked to.

---

### Post by dosodavis on 2013-09-26
I had to use your zip file but I did get it going. I'm sending this message using my Belkin adapter. Thanks so much.

---

### Post by varunendra on 2013-09-26
Great! Credit goes to Mr. chili555, whose post I copied the commands from. :P

---

