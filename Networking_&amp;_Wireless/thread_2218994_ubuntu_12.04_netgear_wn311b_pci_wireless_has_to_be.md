---
title: "ubuntu 12.04 netgear wn311b pci wireless has to be reloaded every reboot"
date: 2014-04-22
forum: Networking &amp; Wireless
---

### Post by charles26 on 2014-04-22
I am running ubuntu 12.04 using a netgear WN311B PCI card. It works just fine with the "additional drivers" using the broadcom BTS driver however everytime I restart the system I have to disable and reactivate it for it to show up. I have tried a few options from the board already so I may have inadvertantly blacklisted something or messed something up that needs to be undone. below is the output of the wireless script:

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux Miner1 3.2.0-60-generic-pae #91-Ubuntu SMP Wed Feb 19 04:14:56 UTC 2014 i686 i686 i386 GNU/Linux

##### lspci #####

04:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
    Subsystem: Dell Device [1028:01a9]
    Kernel driver in use: tg3

05:05.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
    Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter [1385:7d00]
    Kernel modules: wl, ssb
05:0a.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] [104c:8023]

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 055d:3021 Samsung Electro-Mechanics Co. 
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard

##### PCMCIA Card Info #####

##### rfkill #####

##### iw reg get #####

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
10.0.3.0        0.0.0.0         255.255.255.0   U     0      0        0 lxcbr0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.17
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

##### iwlist channel #####

##### lsmod #####

ndiswrapper           196400  0 

##### modinfo #####

filename:       /lib/modules/3.2.0-60-generic-pae/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.57
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     B142941D46926C0169426B8
depends:        
vermagic:       3.2.0-60-generic-pae SMP mod_unload modversions 686 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### modules #####

lp

##### blacklist #####

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

##### udev rules #####

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:05:05.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:05:05.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #####

[   24.242226] intel_rng: don't want to disable this in firmware setup, and if
[   24.566296] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)

########## wireless info END ############

```

Where is a good place to start?

---

### Post by praseodym on 2014-04-22
A good place to start is uninstalling ndiswrapper:

```

sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper* ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf 
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo update-initramfs -u -k all
```
Reboot and check
```

lsmod
iwconfig
rfkill list
```

---

### Post by charles26 on 2014-04-22
Removed

lsmod

```

Module                  Size  Used by
ipt_MASQUERADE         12663  1 
iptable_nat            13016  1 
nf_nat                 24959  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19084  3 iptable_nat,nf_nat
nf_conntrack           73847  4 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18106  1 iptable_nat
x_tables               22011  3 ipt_MASQUERADE,iptable_nat,ip_tables
bridge                 79601  0 
stp                    12848  1 bridge
dm_crypt               22528  1 
snd_emu10k1_synth      13007  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
snd_seq_virmidi        13309  1 snd_emux_synth
snd_seq_midi_emul      13526  1 snd_emux_synth
snd_emu10k1           133257  3 snd_emu10k1_synth
snd_ac97_codec        110213  1 snd_emu10k1
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_emu10k1,snd_ac97_codec
snd_page_alloc         14108  2 snd_emu10k1,snd_pcm
snd_util_mem           13821  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13276  2 snd_emux_synth,snd_emu10k1
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25424  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
b43                   342801  0 
snd_seq                51592  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
dcdbas                 14098  0 
mac80211              436493  1 b43
psmouse                86546  0 
snd_timer              28931  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14172  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13027  0 
cfg80211              178877  2 b43,mac80211
bcma                   25651  1 b43
nvidia               4708655  22 
emu10k1_gp             12570  0 
gameport               15060  2 emu10k1_gp
snd                    62218  14 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17393  0 
soundcore              14635  1 snd
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
mac_hid                13077  0 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  1 
hid_logitech_dj        18290  0 
usbhid                 41937  1 hid_logitech_dj
hid                    81731  2 hid_logitech_dj,usbhid
usb_storage            39646  0 
firewire_ohci          40172  0 
ssb                    50691  1 b43
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   141465  0 


```

iwconfig

```

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

lxcbr0    no wireless extensions.

```

rfkill list

```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

### Post by praseodym on 2014-04-23
```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   [COLOR="#FF0000"]Tx-Power=0 dBm   [/COLOR]
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```
The card is "off". Any button or switch? Checked the BIOS settings?

---

### Post by charles26 on 2014-04-23
There isn't a power button. However I ran the additional drivers and started up the Broadcom STA drivers and all is well. It is consistently working and getting right at what it should be doing performance wise. Thank you for the help.

---

