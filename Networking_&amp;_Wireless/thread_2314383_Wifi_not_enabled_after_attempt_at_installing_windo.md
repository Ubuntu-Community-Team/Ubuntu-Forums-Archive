---
title: "Wifi not enabled after attempt at installing windows wireless driver"
date: 2016-02-20
forum: Networking &amp; Wireless
---

### Post by Nomad Dome on 2016-02-20
14.04 lts

I was using a TP-Link TL-WN721N wireless network adapter.  It worked, but not consistently.  Sometimes I would have to unplug and replug the dongle to make it work.  I read in the forums that it did not work out of the box and required restarting.  To solve this, I decided to try downloading the Windows driver and using "Windows Wireless Drivers" to install.  

*What could possibly go wrong (tm)?*

Current state, options for wireless networking seem to be non-existent.  I am currently using my phone as a tethered USB connection.  

I have run all updates
I have uninstalled all windows wireless network drivers
rebooted several times
Checked for additional network drivers none are available (only the nvidia proprietary driver)

I was using Gnome, and the network icon did not even appear.  I've now switched to the default... I have the networking icon, but no wifi options.

I've tried using multiple USB ports. 
I have a different adapter which used to work on this system (USB wireless N Linux adapter from ThinkPenguin).  That also does not work.

NETWORK shows only:
Wired (the one connected via USB to my phone)
Wired (cable unplugged)
Network proxy

I ran lshw:

lor@Ubuntuoffice-NFORCE6M-A:~$ sudo lshw -c network
[sudo] password for lor: 
  *-network               
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 10
       serial: 74:d4:35:31:b7:cc
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:fdcc0000-fdcfffff ioport:df00(size=128)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 02:52:00:03:66:63
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.119 link=yes multicast=yes
lor@Ubuntuoffice-NFORCE6M-A:~$ 


Listing USB devices:
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0461:0010 Primax Electronics, Ltd HP Keyboard
Bus 002 Device 003: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 002 Device 007: ID 04e8:6863 Samsung Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I have a USB Wireless N Linux adapter from ThinkPenguin.com which used to work.  I tried this and ran lsusb and got identical results.  


I'm obviously a Noob, but tried everything I could think of before hitting the forum.  Any help is greatly appreciated!

---

### Post by Nomad Dome on 2016-02-20
lor@Ubuntuoffice-NFORCE6M-A:~$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
lor@Ubuntuoffice-NFORCE6M-A:~$ ls /etc/modprobe.d
alsa-base.conf               blacklist-watchdog.conf  nvidia-current_hybrid.conf
blacklist-ath_pci.conf       dkms.conf                nvidia-current-updates_hybrid.conf
blacklist.conf               fbdev-blacklist.conf     nvidia-graphics-drivers.conf
blacklist-firewire.conf      iwlwifi.conf             oss-compat.conf
blacklist-framebuffer.conf   mlx4.conf                radeon-kms.conf
blacklist-modem.conf         ndiswrapper.conf         vmwgfx-fbdev.conf
blacklist-oss.conf           nvidia-331_hybrid.conf
blacklist-rare-network.conf  nvidia-340_hybrid.conf
lor@Ubuntuoffice-NFORCE6M-A:~$ dmesg | grep iwl

---

### Post by Nomad Dome on 2016-02-21
Any ideas?  anyone?

---

### Post by Bucky Ball on 2016-02-21
*Thread moved to **Networking & Wireless**.*

Yes. Please use code tags for terminal output. Thanks. See link in my signature. :)

You've installed all Windows drivers? Unsure why. Please run the wireless info script in my signature and post the output here (between code tags, thanks) and let's try to unravel what you've got there now and get back to square one and a working connection.

It's not a great idea to start piling in drivers when you're not sure what you're up to (no offence intended). This can lead to a worse mess than you started with and makes a fix more lengthy, complicated and, occasionally, confusing to get to. ;)

---

### Post by Nomad Dome on 2016-02-27
```

########## wireless info START ##########


Report from: 27 Feb 2016 09:17 CST -0600


Booted last: 27 Feb 2016 09:12 CST -0600


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-77-generic #121-Ubuntu SMP Wed Jan 20 10:50:59 UTC 2016 i686 athlon i686 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


GNOME


##### lspci #############################


02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
	Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
	Kernel driver in use: alx


##### lsusb #############################


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0461:0010 Primax Electronics, Ltd HP Keyboard
Bus 002 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04e8:6863 Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


wmi                    18673  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth2      Link encap:Ethernet  HWaddr <MAC 'eth2' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 


usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet addr:192.168.42.119  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'usb0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3385 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2448062 (2.4 MB)  TX bytes:690260 (690.2 KB)


virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


virbr0    no wireless extensions.


usb0      no wireless extensions.


eth2      no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root      1204     1  0 09:12 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


** (process:3916): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation


NetworkManager Tool


State: connected (global)


- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.42.119
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129


    DNS:             192.168.42.129


- Device: eth2 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth2' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


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


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Auto DoaneDao-f8a90ece-3ef2-4aa3-a8f7-fcd33057a777]] (600 root)
[connection] id=Auto DoaneDao | type=802-11-wireless | permissions=user:notk:;
[802-11-wireless] ssid=DoaneDao


[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=Doanedao_2GEXT
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: America/Chicago (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


lo        no frequency information.


virbr0    no frequency information.


usb0      no frequency information.


eth2      no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


virbr0    Interface doesn't support scanning.


usb0      Interface doesn't support scanning.


eth2      Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


lp


coretemp


coretemp


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v000014E4d00004318sv00000042sd00001737bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00000042sd00001737bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000015sd00001737bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000015sd00001737bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
alias usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip* ndiswrapper


[/etc/modprobe.d/oss-compat.conf]
softdep snd-pcm post: snd-pcm-oss
softdep snd-mixer post: snd-mixer-oss
softdep snd-seq post: snd-seq-midi snd-seq-oss


[/etc/modprobe.d/radeon-kms.conf]
options radeon modeset=1


##### rc.local ##########################


/sbin/modprobe raw1394


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x0846:0x6a00 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:07:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth2' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"
# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan3"


##### dmesg #############################


[   23.284154] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready (repeated 2 times)
[   29.288872] IPv6: ADDRCONF(NETDEV_UP): virbr0: link is not ready
[   32.506886] usb 1-1: device firmware changed
[   33.472837] rndis_host 1-1:1.0 usb0: register 'rndis_host' at usb-0000:00:12.2-1, RNDIS device, <MAC 'usb0' [IF]>


########## wireless info END ############

```

---

### Post by Nomad Dome on 2016-03-03
anyone?

---

### Post by txcrittr on 2016-03-03
I could be wrong, but it looks like ndiswrapper is still operational.  Have you tried uninstalling that?

---

