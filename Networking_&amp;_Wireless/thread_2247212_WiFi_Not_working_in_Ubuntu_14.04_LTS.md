---
title: "WiFi Not working in Ubuntu 14.04 LTS"
date: 2014-10-06
forum: Networking &amp; Wireless
---

### Post by Unleashed_Animal on 2014-10-06
Hi,

I have installed Ubuntu 14.04 LTS, but facing issue that WI-FI is not working, I went to system settings and then "Additional Drivers" tab I din't see anything there so I installed drivers by these following commands :- 
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
[COLOR=#222222]sudo apt-get install b43-fwcutter firmware-b43-installer[/COLOR][COLOR=#222222][FONT=Verdana] 

Then it showed me message that installed successfully, but still I am struggling with WI-FI settings.  when I type "iwconfig" command then it shows me :- 
[/FONT][/COLOR]

eth0 no wireless extensions.


lo no wireless extensions.

[COLOR=#222222][FONT=Verdana] Please help me. Thanks in advance.[/FONT][/COLOR]

---

### Post by Hadaka on 2014-10-06
Hi,please copy and paste the following into a terminal

```
lspci -n | grep 0280
lsmod | egrep 'b43|wl'
rfkill list all
```
post the output.
thanks

---

### Post by Unleashed_Animal on 2014-10-07
$ lspci -n | grep 0280
02:00.0 0280: 10ec:818b
$ lsmod | egrep 'b43|wl'
$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by Hadaka on 2014-10-07
Hi,
"I have installed Ubuntu 14.04 LTS, but facing issue that WI-FI is not  working, I went to system settings and then "Additional Drivers" tab I  din't see anything there so I installed drivers by these following  commands :- 
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
[COLOR=#222222]sudo apt-get install b43-fwcutter firmware-b43-installer[/COLOR][COLOR=#222222][FONT=Verdana]"

HiNT: you dont have a broadcom card this is why its not working.

you have a Realtek card.
please follow this wireless script guide and post the output.

[http://ubuntuforums.org/showthread.php?p=13024222#post13024222](http://ubuntuforums.org/showthread.php?p=13024222#post13024222)
[/FONT][/COLOR]

---

### Post by Unleashed_Animal on 2014-10-08
Hi,
I also went to "system setting" and found that no additional driver are there so I installed that, after that  now if I run these commands 
[COLOR=#000000]sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source [/COLOR]
[COLOR=#222222]sudo apt-get install b43-fwcutter firmware-b43-installer[/COLOR][COLOR=#222222][FONT=Verdana]"

[/FONT][/COLOR]It says me that you already have the newest version, so am I missing anything else, Please guide me.

---

### Post by Unleashed_Animal on 2014-10-08
Hi,
Output of script :- [http://ubuntuforums.org/showthread.p...2#post13024222]("http://ubuntuforums.org/showthread.php?p=13024222#post13024222") is :- 

 

    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


<system_name> 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i3-4000M CPU @ 2.40GHz
Memory : 3593 MB
Uptime : 11:14:13 up  1:03,  2 users,  load average: 0.30, 0.31, 0.21




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
    Subsystem: Lenovo Device [17aa:501e]
    Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter [10ec:818b]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:001b]
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader [10ec:5227] (rev 01)




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 003 Device 005: ID 04f2:b398 Chicony Electronics Co., Ltd 
Bus 003 Device 004: ID 0bda:8761 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 04ca:0061 Lite-On Technology Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                    Soft blocked  Hard blocked
0: tpacpi_bluetooth_sw: Bluetooth      no            no
1: hci0: Bluetooth                     no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


wmi                    19177  0 




module parameters ~~~~~~~~~~~~~~~~~~


wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
============================o=======o========o===========o=========o===========o==============o===========
 Interface & ID             | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
============================o=======o========o===========o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired | e1000e | connected | yes     | 100 Mb/s  |              | <MAC eth0>


    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------+--------+-----------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




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




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.330/0.436/0.542/0.106 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.021/0.030/0.039/0.009 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_IN")
country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


           - 




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~






blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist b43
blacklist b43




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x8086:0x153b (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=8ad9ccea-95d6-427d-916f-23ce4d037058 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.892085] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.892337] audit: initializing netlink socket (disabled)
[    5.688085] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   10.040377] wmi: Mapper loaded
[   10.071629] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   10.099661] Modules linked in: snd_seq_midi snd_seq_midi_event snd_rawmidi snd_hda_intel(+) snd_hda_codec thinkpad_acpi(+) snd_hwdep nvram snd_pcm i915(+) snd_seq snd_page_alloc snd_seq_device snd_timer video drm_kms_helper snd drm wmi mac_hid i2c_algo_bit mei_me soundcore mei parport_pc ppdev lp parport hid_generic usbhid hid rtsx_pci_sdmmc e1000e ahci psmouse libahci ptp rtsx_pci pps_core
[   12.168495] Bluetooth: BNEP (Ethernet Emulation) ver 1.3


    ======== Done ========


Please let me know if you need more info from my side.

---

### Post by varunendra on 2014-10-08
> **Unleashed_Animal said:**
> 02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter **[COLOR="#FF0000"][10ec:818b][/COLOR]**


Unfortunately, this device is not supported by default in any of the default kernels available in default Ubuntu installations. However, there are some proposed fixes for the time being that seem to work for most people if not everyone.

Please see this bug report, and read the comments (especially #184 and #204) to see and try the fixes : [https://bugs.launchpad.net/bugs/1239578](https://bugs.launchpad.net/bugs/1239578)

I recommend adding yourself to the "Affects Me" list of the bug report, along with a comment on how the proposed fixes work for you. Thanks.

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

--

---

### Post by Unleashed_Animal on 2014-10-08
Hi,

Along with WIFI, I tried to use data-card also for internet, so I configured new mobile-broadband connection, but when I click on connect button, it asks for password, when I enter root password, it says "Authentication failed", when I use same data card in another system, it does not ask anything, Am I missing something, Please guide me.

---

### Post by varunendra on 2014-10-08
Please start a different thread with a suitable title for the Mobile Broadband connection. WiFi and Mobile Broadband are completely different beasts.

Feel free to post a link to your new thread here so we can follow and possibly post suggestions if we can think of something.

---

