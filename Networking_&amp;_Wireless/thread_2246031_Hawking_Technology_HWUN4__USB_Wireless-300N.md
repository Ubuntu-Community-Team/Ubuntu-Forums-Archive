---
title: "Hawking Technology HWUN4 / USB Wireless-300N"
date: 2014-09-27
forum: Networking &amp; Wireless
---

### Post by aeboltho on 2014-09-27
I just decided to build myself a desktop two days ago and that I didn't want to pay for Windows, so I'm very new at this linux game.  Things seem to be going fairly well...I have **ubuntu 14.04 LTS** installed and seemingly running fine.  I had a wireless adapter but my graphics card physically blocks the PCI-express slot for it, so I returned that and the guy at the store gave me a **Hawking Technology USB Wireless-300N Network Adapter**, the box also says** HWUN4**.  He said it would work fine with linux, although none of the included materials agree with that.  But I have it so I'd like to give it an honest shot at working.

I tried putting the included disk in but I can't run the autorun.exe file (I assume that's meant for Windows...don't make fun of me too much...)

I tried the lsusb command in the terminal and it gave me a line saying:
Bus 005 Device 002:  ID 0e66:0020 Hawking Technologies

I assume that means it recognizes the device but it just doesn't know what to do with the signal from it...

Anyone know of a place that I could find a linux supported driver for this, and maybe how to actually install said driver?  Since I returned the old network adapter I don't have a connection to the internet on my desktop (I'm also upstairs and lacking a long enough cable), but I do have an 8gb flashdrive that I could use to transfer files from my work laptop, which I'm using to post this.

Any help would be appreciated, including suggestions to return it and buy something else if this is just a wall to bash my head against

---

### Post by varunendra on 2014-09-29
Welcome to the forums aeboltho!

While the adapter is plugged in, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by motoperpetuo on 2014-10-25
> **varunendra said:**
> Welcome to the forums aeboltho!

While the adapter is plugged in, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

looks like the original poster never got back to you, but i have the same wifi adapter and the same question. here is my wireless-info.txt. would very much appreciate any advice:

```


	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

biella 3.2.0-4-486 i686,  Debian GNU/Linux 7.6 (wheezy), wheezy

CPU    : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
Memory : 3040 MB
Uptime : 10:39:00 up 4 min,  1 user,  load average: 0.40, 0.39, 0.18


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

00:19.0 Ethernet controller [0200]: Intel Corporation 82566DC Gigabit Network Connection [8086:104b] (rev 02)
	Subsystem: Dell Device [1028:01db]
	Kernel driver in use: e1000e


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 1e4e:0f01  
Bus 007 Device 003: ID 0e66:0020 Hawking Technologies 
Bus 005 Device 002: ID 046d:c52e Logitech, Inc. 


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

mxm_wmi                12467  1 nouveau
wmi                    13051  2 mxm_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=======o========o===========o=========o===========o==============o===========
 Interface & ID             | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
============================o=======o========o===========o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired | e1000e | connected | yes     | 1000 Mb/s |              | <MAC eth0>

    Address:         10.0.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1
    DNS:             75.75.75.75
    DNS:             75.75.76.76

    Address:         2601:1:8480:10d8:216:76ff:febf:4ee6
    Prefix:          64
    Gateway:         fe80::921a:caff:fe1b:50b1

    Address:         fe80::216:76ff:febf:4ee6
    Prefix:          64
    Gateway:         fe80::921a:caff:fe1b:50b1
    DNS:             2001:558:feed::1
    DNS:             2001:558:feed::2
----------------------------+-------+--------+-----------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

HOME-50B2            : ssid=HOME-50B2 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
HOME-50B2 1          : ssid=HOME-50B2 | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
Wireless connection 1 : ssid=HOME-50B2 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

domain hsd1.co.comcast.net.
search hsd1.co.comcast.net.
nameserver 75.75.75.75
nameserver 75.75.76.76
nameserver 2001:558:feed::1
nameserver 2001:558:feed::2


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0

--- 10.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.837/1.287/1.737/0.450 ms

--- 75.75.75.75 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1008ms


--- 75.75.76.76 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 23.324/23.477/23.631/0.216 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[mxm_wmi]
filename:       /lib/modules/3.2.0-4-486/kernel/drivers/platform/x86/mxm-wmi.ko
depends:        wmi

[wmi]
filename:       /lib/modules/3.2.0-4-486/kernel/drivers/platform/x86/wmi.ko
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
loop

[/etc/modprobe.d]
radeon-kms.conf   : options radeon modeset=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.2.0-4-486 root=UUID=7080a23d-49f6-4ae9-8668-ea853d65dd0f ro quiet


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.004170] Initializing cgroup subsys net_cls
[    1.660827] audit: initializing netlink socket (disabled)
[    2.040620] Initializing network drop monitor service
[    3.802142] platform microcode: firmware: agent loaded intel-ucode/06-0f-06 into memory
[    3.802690] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    6.878322] wmi: Mapper loaded
[   17.522291] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

	======== Done ========

```

---

