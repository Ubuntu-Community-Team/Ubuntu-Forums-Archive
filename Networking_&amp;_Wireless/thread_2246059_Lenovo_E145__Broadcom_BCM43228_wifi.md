---
title: "Lenovo E145 / Broadcom BCM43228 wifi"
date: 2014-09-28
forum: Networking &amp; Wireless
---

### Post by patrick56 on 2014-09-28
Hi,

I got a Lenovo E145 laptop with a broadcom chip BCM43228.

The wifi works with windows without a problem, however ifconfig and iwconfig don't return a "wlan0". Also, "sudo modprobe bc43" and "sudo modprobe wl" don't work. Especially, modprobe wl does not return an exisiting module.

I tried to upgrade the Kernel to 3.16.3 but no changes.

I tried to install many different deb packages via USB stick, but no results:

/Users/pmu/Downloads/autoconf_2.69-6_all.deb
/Users/pmu/Downloads/b43-fwcutter_018-2_amd64.deb
/Users/pmu/Downloads/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_i386.deb
/Users/pmu/Downloads/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64 (1).deb
/Users/pmu/Downloads/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb
/Users/pmu/Downloads/bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_amd64.deb
/Users/pmu/Downloads/binutils_2.20.1-3ubuntu7.1_amd64.deb
/Users/pmu/Downloads/broadcom-sta-dkms_5.100.82.112-8_all.deb
/Users/pmu/Downloads/default-jre_1.7-51_amd64.deb
/Users/pmu/Downloads/dkms_2.2.0.3-0_all.deb
/Users/pmu/Downloads/firmware-b43-installer_017-2_all.deb
/Users/pmu/Downloads/firmware-b43-installer_018-2_all.deb
/Users/pmu/Downloads/libjna-java_3.2.7-4_amd64.deb
/Users/pmu/Downloads/libsigsegv2_2.10-2_amd64.deb
/Users/pmu/Downloads/linux-firmware-nonfree_1.14ubuntu3_all.deb
/Users/pmu/Downloads/linux-headers-generic_3.13.0.36.43_amd64.deb
/Users/pmu/Downloads/linux-image-3.16.3-031603-generic_3.16.3-031603.201409171435_amd64.deb
/Users/pmu/Downloads/linux-libc-dev_3.13.0-36.63_amd64.deb
/Users/pmu/Downloads/m4_1.4.17-2ubuntu1_amd64.deb
/Users/pmu/Downloads/wireless-tools_30~pre9-3ubuntu4_amd64.deb

How can this be debugged?

---

### Post by varunendra on 2014-09-29
Welcome to the forums Patrick!

Did you install those packages all at once? :shock:

That would make your system a perfect arena of driver-gladiators, in which every single one of them would try to kill the other, and in the end, probably none would be alive. :p

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by patrick56 on 2014-10-31
Sorry for the long time since your reply. Here is the output of the script:


```

patrick@patrick-ThinkPad-Edge-E145:~$ cat wireless-info.txt 

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

patrick-ThinkPad-Edge-E145 3.16.3-031603-generic x86_64,  Ubuntu Utopic Unicorn (development branch), utopic

CPU    : AMD E1-2500 APU with Radeon(TM) HD Graphics
Memory : 3156 MB
Uptime : 08:51:51 up 7 min,  2 users,  load average: 0,54, 0,77, 0,49


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Broadcom Corporation Device [14e4:0607]
    Kernel driver in use: bcma-pci-bridge
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:510c]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 5986:0299 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:21f3 Broadcom Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                    Soft blocked  Hard blocked
0: tpacpi_bluetooth_sw: Bluetooth      no            no
1: hci0: Bluetooth                     no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

wmi                    19379  0 
b43                   410494  0 
bcma                   52702  1 b43
mac80211              687021  1 b43
cfg80211              521225  2 b43,mac80211
ssb                    63214  1 b43


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=======o========o===========o=========o===========o==============o===========
 Interface & ID             | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
============================o=======o========o===========o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired | r8169  | connected | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.2.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
----------------------------+-------+--------+-----------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
WWanEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search Speedport_W723_V_Typ_A_1_01_009


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.435/0.510/0.586/0.078 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.065/0.071/0.077/0.006 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : fr_FR.UTF-8)
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb

[/etc/modprobe.d/blacklist.conf]
blacklist ssb
blacklist bcma
blacklist b43
blacklist brcmsmac

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b44
blacklist b43legacy
blacklist b43
blacklist brcm80211
blacklist brcmsmac
blacklist ssb


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[wmi]
filename:       /lib/modules/3.16.3-031603-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[b43]
filename:       /lib/modules/3.16.3-031603-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     3CEE8C37D02010CA66D9311
depends:        bcma,ssb,mac80211,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.16.3-031603-generic/kernel/drivers/bcma/bcma.ko
srcversion:     D52E980A55E0AC3C372382C
depends:        

[mac80211]
filename:       /lib/modules/3.16.3-031603-generic/kernel/net/mac80211/mac80211.ko
srcversion:     E4D3FCB715C0CB33E42D11E
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.3-031603-generic/kernel/net/wireless/cfg80211.ko
srcversion:     D86AFD97E7F71C59777C05F
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.16.3-031603-generic/kernel/drivers/ssb/ssb.ko
srcversion:     2055C3093DA2EE9DEB5572C
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
b43

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.16.3-031603-generic root=UUID=f8bf3775-2996-4c4e-ba2d-faf1e725ce62 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.261433] Initializing cgroup subsys net_cls
[    0.261465] Initializing cgroup subsys net_prio
[    1.439793] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.440764] audit: initializing netlink subsys (disabled)
[    1.871677] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    7.480433] psmouse serio5: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   12.269739] bcma: bus0: Found chip with id 0xA8DC, rev 0x00 and package 0x08
[   12.269770] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[   12.269792] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1E, class 0x0)
[   12.269833] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x12, class 0x0)
[   12.269854] bcma: bus0: Core 3 found: SDIO Device (manuf 0x4BF, id 0x829, rev 0x07, class 0x0)
[   12.283417] bcma: bus0: Bus registered
[   14.496574] wmi: Mapper loaded
[   15.426037] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   15.429062] thinkpad_acpi: Unsupported brightness interface, please contact [EMAIL="ibm-acpi-devel@lists.sourceforge.net"]ibm-acpi-devel@lists.sourceforge.net[/EMAIL]
[   15.720305] [drm] Found VCE firmware/feedback version 40.2.2 / 15!
[   16.976686] bluetooth hci0: Direct firmware load failed with error -2
[   16.978786] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0a5c-21f3.hcd not found
[   17.633994] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

    ======== Done ========

```

---

### Post by mörgæs on 2014-10-31
Please follow the instructions regarding CODE tags.

---

### Post by patrick56 on 2014-11-01
Sorry about the code tags, updated these. Anything unusual in the wireless setup?

---

### Post by Bucky Ball on 2014-11-01
Did you follow the[ instructions HERE?]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29")

Your output gives us:

Kernel driver in use: bcma-pci-bridge

Read [THIS]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Broadcom_STA_Wireless_driver_.28Proprietary.29"). You need the STA driver for that card.

---

### Post by chili555 on 2014-11-01
> **Bucky Ball said:**
>  You need the STA driver for that card.Indeed! Hook up that ethernet for a few moments, open a terminal and do:```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```Detach the ethernet, reboot and enjoy.

---

### Post by patrick56 on 2014-11-09
Hmm.. ok, how would I remove the current driver, since simply installing the STA driver seems not to work:


```

lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


01:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Broadcom Corporation Device [14e4:0607]
    Kernel driver in use: bcma-pci-bridge
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:510c]
    Kernel driver in use: r8169

```

---

### Post by chili555 on 2014-11-10
> **patrick56 said:**
> Hmm.. ok, how would I remove the current driver, since simply installing the STA driver seems not to work:


```

lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


01:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Broadcom Corporation Device [14e4:0607]
    Kernel driver in use: bcma-pci-bridge
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:510c]
    Kernel driver in use: r8169

```Please show us the result of:```
sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source
```Reboot and then show us your *lspci* as above.

---

### Post by patrick56 on 2014-11-10
Ok, now the driver seems to be found, but the blacklisting might still affect the WLAN discovery negatively. At least, I dont see any wlan networks.

here is the output of the wireless script

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

patrick-ThinkPad-Edge-E145 3.16.3-031603-generic x86_64,  Ubuntu 14.10, utopic

CPU    : AMD E1-2500 APU with Radeon(TM) HD Graphics
Memory : 3156 MB
Uptime : 19:35:44 up 4 min,  2 users,  load average: 1,28, 0,67, 0,30


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Broadcom Corporation Device [14e4:0607]
    Kernel driver in use: bcma-pci-bridge
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:510c]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 5986:0299 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:21f3 Broadcom Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                    Soft blocked  Hard blocked
0: hci0: Bluetooth                     no            no
1: tpacpi_bluetooth_sw: Bluetooth      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

wl                   6367694  0 
wmi                    19379  0 
b43                   410494  0 
bcma                   52702  1 b43
mac80211              687021  1 b43
cfg80211              521225  3 wl,b43,mac80211
ssb                    63214  1 b43


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=======o========o=============o=========o===========o==============o===========
 Interface & ID | Type  | Driver | State       | Default | Speed     | Support      | HW Addr   
================o=======o========o=============o=========o===========o==============o===========
 eth0           | Wired | r8169  | unavailable | no      | 100 Mb/s  |              | <MAC eth0>
----------------+-------+--------+-------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
WWanEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Wi-Fi connection 1   : ssid=WLAN-5FF089 | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : fr_FR.UTF-8)
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist ssb
blacklist bcma
blacklist b43
blacklist brcmsmac

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[wl]
filename:       /lib/modules/3.16.3-031603-generic/updates/dkms/wl.ko
srcversion:     DF2576C38AD45205B3556DD
depends:        cfg80211
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[wmi]
filename:       /lib/modules/3.16.3-031603-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[b43]
filename:       /lib/modules/3.16.3-031603-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     3CEE8C37D02010CA66D9311
depends:        bcma,ssb,mac80211,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.16.3-031603-generic/kernel/drivers/bcma/bcma.ko
srcversion:     D52E980A55E0AC3C372382C
depends:        

[mac80211]
filename:       /lib/modules/3.16.3-031603-generic/kernel/net/mac80211/mac80211.ko
srcversion:     E4D3FCB715C0CB33E42D11E
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.3-031603-generic/kernel/net/wireless/cfg80211.ko
srcversion:     D86AFD97E7F71C59777C05F
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.16.3-031603-generic/kernel/drivers/ssb/ssb.ko
srcversion:     2055C3093DA2EE9DEB5572C
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4359 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
b43

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.16.3-031603-generic root=UUID=f8bf3775-2996-4c4e-ba2d-faf1e725ce62 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.262328] Initializing cgroup subsys net_cls
[    0.262360] Initializing cgroup subsys net_prio
[    1.443237] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.444178] audit: initializing netlink subsys (disabled)
[    1.952184] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    7.445180] psmouse serio5: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   11.084763] bcma: bus0: Found chip with id 0xA8DC, rev 0x00 and package 0x08
[   11.084793] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[   11.084815] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1E, class 0x0)
[   11.084855] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x12, class 0x0)
[   11.084876] bcma: bus0: Core 3 found: SDIO Device (manuf 0x4BF, id 0x829, rev 0x07, class 0x0)
[   11.097654] bcma: bus0: Bus registered
[   12.418016] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.379886] wmi: Mapper loaded
[   14.601020] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.609667] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   14.637045] bluetooth hci0: Direct firmware load failed with error -2
[   14.743817] thinkpad_acpi: http://ibm-acpi.sf.net/
[   14.746837] thinkpad_acpi: Unsupported brightness interface, please contact ibm-acpi-devel@lists.sourceforge.net
[   15.162276] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0a5c-21f3.hcd not found
[   16.588391] [drm] Found VCE firmware/feedback version 40.2.2 / 15!

    ======== Done ========

```

---

### Post by patrick56 on 2014-11-10
now trying to remove the old driver first:

```

$ sudo apt-get remove  bcmwl-kernel-source 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-image-generic
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  bcmwl-kernel-source
0 upgraded, 0 newly installed, 1 to remove and 148 not upgraded.
After this operation, 8 036 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 210217 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu1) ...
Removing all DKMS Modules

```

---

### Post by patrick56 on 2014-11-10
now after removing, I did

```

patrick@patrick-ThinkPad-Edge-E145:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-image-generic
Use 'apt-get autoremove' to remove it.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 148 not upgraded.
Need to get 1 511 kB of archives.
After this operation, 8 036 kB of additional disk space will be used.
Get:1 http://fr.archive.ubuntu.com/ubuntu/ utopic/restricted bcmwl-kernel-source amd64 6.30.223.248+bdcom-0ubuntu1 [1 511 kB]
Fetched 1 511 kB in 0s (1 823 kB/s)       
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 210583 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu1) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu1) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
Building only for 3.16.3-031603-generic
Building for architecture x86_64
Building initial module for 3.16.3-031603-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.16.3-031603-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-3.16.3-031603-generic

```

---

### Post by chili555 on 2014-11-10
Excellent. Please reboot and show us an new version of the wireless script.

Thanks.

---

### Post by patrick56 on 2014-11-16
unfortunately, the driver is still not loaded.

see the dump of the wireless script

```

patrick@patrick-ThinkPad-Edge-E145:~$ cat wireless-info.txt 

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

patrick-ThinkPad-Edge-E145 3.16.3-031603-generic x86_64,  Ubuntu 14.10, utopic

CPU    : AMD E1-2500 APU with Radeon(TM) HD Graphics
Memory : 3156 MB
Uptime : 13:32:20 up 1 min,  2 users,  load average: 3,30, 1,20, 0,43


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Broadcom Corporation Device [14e4:0607]
    Kernel driver in use: bcma-pci-bridge
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:510c]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 5986:0299 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:21f3 Broadcom Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                    Soft blocked  Hard blocked
0: tpacpi_bluetooth_sw: Bluetooth      no            no
1: hci0: Bluetooth                     no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

wl                   6367694  0 
wmi                    19379  0 
b43                   410494  0 
bcma                   52702  1 b43
mac80211              687021  1 b43
cfg80211              521225  3 wl,b43,mac80211
ssb                    63214  1 b43


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=======o========o=============o=========o===========o==============o===========
 Interface & ID | Type  | Driver | State       | Default | Speed     | Support      | HW Addr   
================o=======o========o=============o=========o===========o==============o===========
 eth0           | Wired | r8169  | unavailable | no      |           |              | <MAC eth0>
----------------+-------+--------+-------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
WWanEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Wi-Fi connection 1   : ssid=WLAN-5FF089 | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : fr_FR.UTF-8)
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist ssb
blacklist bcma
blacklist b43
blacklist brcmsmac

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[wl]
filename:       /lib/modules/3.16.3-031603-generic/updates/dkms/wl.ko
srcversion:     DF2576C38AD45205B3556DD
depends:        cfg80211
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[wmi]
filename:       /lib/modules/3.16.3-031603-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[b43]
filename:       /lib/modules/3.16.3-031603-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     3CEE8C37D02010CA66D9311
depends:        bcma,ssb,mac80211,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.16.3-031603-generic/kernel/drivers/bcma/bcma.ko
srcversion:     D52E980A55E0AC3C372382C
depends:        

[mac80211]
filename:       /lib/modules/3.16.3-031603-generic/kernel/net/mac80211/mac80211.ko
srcversion:     E4D3FCB715C0CB33E42D11E
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.3-031603-generic/kernel/net/wireless/cfg80211.ko
srcversion:     D86AFD97E7F71C59777C05F
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.16.3-031603-generic/kernel/drivers/ssb/ssb.ko
srcversion:     2055C3093DA2EE9DEB5572C
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4359 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
b43

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.16.3-031603-generic root=UUID=f8bf3775-2996-4c4e-ba2d-faf1e725ce62 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.262087] Initializing cgroup subsys net_cls
[    0.262119] Initializing cgroup subsys net_prio
[    1.443420] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.444367] audit: initializing netlink subsys (disabled)
[    1.936061] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    7.517260] psmouse serio5: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   13.270768] bcma: bus0: Found chip with id 0xA8DC, rev 0x00 and package 0x08
[   13.270799] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[   13.270822] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1E, class 0x0)
[   13.270862] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x12, class 0x0)
[   13.270885] bcma: bus0: Core 3 found: SDIO Device (manuf 0x4BF, id 0x829, rev 0x07, class 0x0)
[   13.283738] bcma: bus0: Bus registered
[   14.637356] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.351811] wmi: Mapper loaded
[   16.879576] thinkpad_acpi: http://ibm-acpi.sf.net/
[   16.888160] thinkpad_acpi: Unsupported brightness interface, please contact ibm-acpi-devel@lists.sourceforge.net
[   17.374219] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.382980] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   18.727975] bluetooth hci0: Direct firmware load failed with error -2
[   18.729421] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0a5c-21f3.hcd not found
[   21.421400] [drm] Found VCE firmware/feedback version 40.2.2 / 15!

    ======== Done ========
[SUP]

```
[/SUP]

---

### Post by chili555 on 2014-11-16
The driver in question *wl* IS loaded; however, you have a conflict going. The driver b43 is also loaded and they are fighting each other for world supremacy! It is blacklisted six ways from Sunday:```
[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist ssb
blacklist bcma
blacklist b43
blacklist brcmsmac

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

```We would certainly think that having a module blacklisted three times (!!) would prevent it from loaded. However, the file /etc/modules calls for it to be loaded *anyway*! 

Please do:```
gksudo gedit /etc/modules
```Use nano or kate or leafpad if you don't have the text editor gedit. Remove b43 from the file. Proofread carefully, save and close the text editor.

Reboot and if it isn't working, show us:```
lsmod | grep -e wl -e b43
cat /etc/modules
```Thanks.

---

### Post by patrick56 on 2014-11-16
Solved!

The problem was indeed that the module got blacklisted. Oh my, it has been too long that I used Linux.
Thanks for your help and patience!

---

### Post by chili555 on 2014-11-16
> **patrick56 said:**
> Solved!

The problem was indeed that the module got blacklisted. Oh my, it has been too long that I used Linux.
Thanks for your help and patience!Not exactly. The b43 module is supposed to be blacklisted if you use the correct driver *wl* for your device. It shouldn't be added to /etc/modules to be loaded  anyway.

That's what you meant, I assume.

---

