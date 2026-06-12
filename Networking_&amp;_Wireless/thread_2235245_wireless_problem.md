---
title: "wireless problem"
date: 2014-07-19
forum: Networking &amp; Wireless
---

### Post by sridhar4 on 2014-07-19
Hi,

I updated to ubuntu 12.04 LTS and now my wireless does not work.  Below are the details:

OS - Ubuntu 12.04
Hardware - HP 1000 

lshw output:
 ```
*-network UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:63500000-6350ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 05
       serial: d8:9d:67:7c:3e:10
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:63404000-63404fff memory:63400000-63403fff
```

lspci output:
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM75 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series]
07:00.0 Network controller: Ralink corp. Device 539b
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
```

rfkill output:
```
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
My older ubuntu version works, so currently I am using that one.  In the latest version that I installed I am not able to get on line, so I will need a method where I can download the files/driver to my computer and then do the fix.

Thanks and please let me know what other info you may need.
Regards,
Sridhar

---

### Post by varunendra on 2014-07-20
Welcome to the forums Sridhar!

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by sridhar4 on 2014-07-21
Below is the output.  Thanks in advance.

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

sridhar-HP-1000-Notebook-PC 3.2.0-61-generic x86_64,  Ubuntu 12.04.4 LTS, precise

CPU    : Intel(R) Core(TM) i3-2328M CPU @ 2.20GHz
Memory : 1833 MB
Uptime : 22:09:22 up 3 min,  2 users,  load average: 0.51, 0.30, 0.12


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

07:00.0 Network controller [0280]: Ralink corp. Device [1814:539b]
    Subsystem: Hewlett-Packard Company Device [103c:18ed]
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)
--
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:1855]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 15d9:0a41 Trust International B.V. MI-2540D [Optical mouse]
Bus 002 Device 004: ID 064e:e263 Suyin Corp. 


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface           Soft blocked  Hard blocked
0: hp-wifi: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
wmi                    19105  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=======o========o==============o=========o===========o==============o===========
 Interface & ID | Type  | Driver | State        | Default | Speed     | Support      | HW Addr   
================o=======o========o==============o=========o===========o==============o===========
 eth0           | Wired | r8169  | unavailable  | no      |           |              | <MAC eth0>
----------------+-------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

AmyxRouter           : ssid=AmyxRouter | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
AmyxRouter-guest     : ssid=AmyxRouter-guest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
EconomyInn           : ssid=EconomyInn | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Economy Inn          : ssid=Economy Inn | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Emirates1            : ssid=Emirates1 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Eric                 : ssid=Eric | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
FAST_31B948          : ssid=FAST_31B948 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
FAST_31C9B4          : ssid=FAST_31C9B4 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
FREE_WIFI-8          : ssid=FREE_WIFI-8 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
ghar                 : ssid=ghar | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
HENRY_Network_1      : ssid=HENRY_Network_1 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
HOMETJ               : ssid=HOMETJ | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
office-vla           : ssid=office-vla | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Office-wlan          : ssid=Office-wlan | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
qixinghu-2           : ssid=qixinghu-2 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
rd001                : ssid=rd001 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
svr                  : ssid=svr | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
svr 1                : ssid=svr | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Tenda_2C5650         : ssid=Tenda_2C5650 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
TP-LINK_625298       : ssid=TP-LINK_625298 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
TP-LINK_E7863A       : ssid=TP-LINK_E7863A | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
TP-LINK_E7863A 1     : ssid=TP-LINK_E7863A | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-opensource-graphics.conf]
blacklist nouveau
blacklist radeon 
blacklist lbm-nouveau
blacklist lbm-radeon 


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:0e:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
rmhwk-workaround
rmhwk-workaround
rmhwk-workaround
rmhwk-workaround
rmhwk-workaround
rmhwk-workaround
rmhwk-workaround
rmhwk-workaround
rmhwk-workaround
rmhwk-workaround

[/etc/rc.local]
/usr/sbin/workaround_r8169
echo 0 > /sys/module/video/parameters/brightness_switch_enabled
exit 0

[/etc/modprobe.d]
snd-hda-intel.conf: options snd-hda-intel power_save_controller=N


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.2.0-61-generic root=UUID=015fd5d7-ea8c-426b-afe3-cea0fd168f34 ro i915.modeset=1 quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.273337] audit: initializing netlink socket (disabled)
[    2.028485] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   20.743433] wmi: Mapper loaded
[   21.570847] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

    ======== Done ========
```

---

### Post by varunendra on 2014-07-21
The native driver in your current kernel does not support the wireless card. Your best option is to upgrade you Hardware Enablement Stack to the latest as mentioned here : [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Once upgraded to the latest kernel, the driver that comes with it will natively support the wireless card.

Alternatively, you can either compile a backported driver, or the proprietary driver downloaded from Ralink's official site (most probably what you did to make it work last time). Both these options will require you to redo the same process every time a kernel upgrade happens.

Compiling and installing a backported driver is slightly easier than compiling the proprietary one, since the proprietary one *may* require an additional patch to make it compatible with the kernel you are using. The steps to install the backported driver, in general, are -

[indent]download > extract > run "make defconfig-wifi" > run "make" > run "sudo make install".

Steps to install the proprietary driver, in general are -

download > extract > download patch & apply it (may or may not required) > edit a config file > "make" > "make install" > blacklist native driver[/indent]

Let me know which option you wish to go with.

Upgrading the Enablement Stack has the advantage that you'll need to do that only once, but keep a Live DVD handy since it has the potential to break some functions. If a fresh install is not a problem for you, perhaps it is the best and safest option to try 12.04.4 or even 14.04 Live DVD in live mode, and see if it works nicely with your hardware. If satisfied, do a fresh install of it.

---

### Post by sridhar4 on 2014-07-24
Hi Varun,

Thank you.  That solved the problem.

---

### Post by sridhar4 on 2014-07-24
By the way, I ended up doing an upgrade to the Enablement Stack, which I guess is a different way of saying I installed a patch.

---

### Post by varunendra on 2014-07-24
> **sridhar4 said:**
> By the way, I ended up doing an upgrade to the Enablement Stack, which I guess is a different way of saying I installed a patch.

Nope, it's not a patch. A patch is when you add/remove/modify _part of something_ in what you get by default. While what you have got by upgrading the Enablement stack is the 'Standard' that you would get by default if you do a fresh install of 12.04.4 directly from a 12.04.4 DVD.

It is not upgraded by default and is kept 'Optional' due to certain reasons, especially of this kind -
> Anyone running a Raring or Saucy enablement stack in Precise might have an unexpected result if they upgrade their entire system to Quantal. The packages offered in the Raring/Saucy enablement stack would supersede the Quantal packages.

Which means if you now tried to upgrade the 'Release' to a slightly newer version (Precise to Raring, Trusty etc.) while your Hardware Enablement Stack is already upgraded to a superior version *(for example, Raring by default comes with kernel 3.8, while now your kernel may have already been upgraded to 3.11 or 3.13, along with compatible Xorg packages)*, things would be very likely to break. Since it is something beyond the control of the standard upgrade/update mechanism of Ubuntu, it is one of the reasons why it is kept optional.

---

