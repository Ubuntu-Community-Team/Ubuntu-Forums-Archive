---
title: "HP EliteBook 725 G2 wireless not working"
date: 2014-11-29
forum: Networking &amp; Wireless
---

### Post by aridus on 2014-11-29
I have purchased a new HP EliteBook 725 G2 and installed Ubuntu 14.10 (dual boot with Windows). Wireless was not working so I added the proprietary driver for the Broadcom BCM43228 802.11a/b/g/n (there was no other option).  It installed fine. Bluetooth is working. The wireless button is switched on. I can connect to the router with an ethernet cable. However, my wireless is not detected. I can connect to my wireless on this machine with Windows. 

Output of 'lspci -nn -d 14e4:' is
...Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]

Having looked at

[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

I followed the instructions to install bcmwl-kernel-source (as this is apparently appropriate for  14e4:4359) but still no joy.

Does anybody more knowledgeable/sensible have any suggestsion (I am banging my head on the wall...)?

With grateful thanks

---

### Post by westie457 on 2014-11-29
These suggestions might sound stupid.

Unplug the ethernet cable,does the wireless try to connect?

If it does not then leave the cable unplugged and reboot.

If not working now follow the info at this link for the 'Wireless Script'. We will need to see the generated report. 

[http://ubuntuforums.org/showthread.php?p=13024222#post13024222](http://ubuntuforums.org/showthread.php?p=13024222#post13024222)


Thank you.

---

### Post by aridus on 2014-11-29
westie457 - thank you - it is very kind of you to reply. When I unplug the ethernet cable wireless does not try to connect. Followed your instruction and rebooted without ethernet cabe, still not working. I have therefore run the script (as connection via ethernet cable is not working either now, I did this following the instructions for Method 2, and was able to run the script on the new computer). With grateful thanks.

Herewith:

```


	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

martin 3.16.0-23-generic x86_64,  Ubuntu 14.10, utopic

CPU    : AMD A10 PRO-7350B R6, 10 Compute Cores 4C+6G
Memory : 6858 MB
Uptime : 06:18:00 up 21 min,  1 user,  load average: 0.15, 0.30, 0.25


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0e)
	Subsystem: Hewlett-Packard Company Device [103c:221d]
	Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
	Subsystem: Broadcom Corporation Device [14e4:05e2]
	Kernel driver in use: bcma-pci-bridge


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b466 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0a5c:21f1 Broadcom Corp. HP Portable Bumble Bee
Bus 003 Device 002: ID 138a:003f Validity Sensors, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 002: ID 0718:0a02 Imation Corp. 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface     Soft blocked  Hard blocked
0: hci0: Bluetooth      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
wmi                    19193  1 hp_wmi
bcma                   52443  0 


module parameters ~~~~~~~~~~~~~~~~~~

wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=======o========o===========o=========o===========o==============o===========
 Interface & ID             | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
============================o=======o========o===========o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired | r8169  | connected | yes     | 1000 Mb/s |              | <MAC eth0>

    Address:         192.168.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
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
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.878/4.444/8.010/3.566 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.033/0.038/0.043/0.005 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

No way to aquire root rights found.


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[hp_wmi]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     2BEC5DCE5B3A6695D374C6A
depends:        wmi,sparse-keymap

[wmi]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[bcma]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/bcma/bcma.ko
srcversion:     D52E980A55E0AC3C372382C
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
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
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.16.0-23-generic root=UUID=1197a3dc-1e3d-49ef-8a8a-c018d2e026c3 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[  837.785541] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  837.786238] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  837.786854] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  837.787514] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  837.788412] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  870.359350] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  870.360510] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  870.362669] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  870.363396] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  870.364238] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  870.365056] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  870.365908] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  875.842529] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  875.843271] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  875.844890] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  875.845620] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  875.846117] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  875.846614] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[  875.847209] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1019.040876] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1019.041879] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1019.044183] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1019.044920] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1019.045585] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1019.046347] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1019.047358] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1025.140997] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1025.142002] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1025.144462] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1025.145249] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1025.145884] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1025.146563] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1025.147433] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1184.715556] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1184.716501] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1184.718789] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1184.719500] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1184.720107] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1184.720751] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1184.721657] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1228.368307] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1228.369313] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1228.371669] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1228.372479] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1228.373149] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1228.373860] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform
[ 1228.374745] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform

	======== Done ========

```

---

### Post by aridus on 2014-12-01
started a new thread ([http://ubuntuforums.org/showthread.php?t=2254816](http://ubuntuforums.org/showthread.php?t=2254816)) to try and resolve the issue with the ethernet card not working on this computer, and in so doing we slipped into discussion of this problem (the Broadcom wireless adapter). Both issues remain unresolved, however.

Should this present thread therefore be closed?

With thanks.

---

### Post by westie457 on 2014-12-02
You are getting a lot more help from jeremy31 in your other thread.

As for this thread click on 'Report Post' and ask for it to be closed.

---

### Post by aridus on 2014-12-02
Thank you, and I have done so.

---

### Post by howefield on 2014-12-02
Thread closed, duplicate here : [http://ubuntuforums.org/showthread.php?t=2254816](http://ubuntuforums.org/showthread.php?t=2254816)

---

