---
title: "Trouble configuring USB WL Adaptor w Ndiswrapper"
date: 2015-04-24
forum: Networking &amp; Wireless
---

### Post by John_Mackenzie on 2015-04-24
I need help configuring my wireless USB adapter to connect to a FIOS router.  

I have a dual boot WinXP/Linux computer with Ubunto UGI.  I can install a driver for my USB device, but my Ubunto Network Connections seems to bring up a Gnome network manager which does not allow me to edit the right combination of wpak-2 and web key inputs to properly connect.  The interface asks only for a web name.  

I have tried to alter the authentication type in other edit tabs, but the edit screen turns "grey", and won't let me save.

I know the usb adapter works, because it connects nicely from a WinXP boot.  I have downloaded about 150 pages worth of Ndiswrapper fixes dealing with this subject - and have had no luck installing other utilities to resolve the problem.

I have multiversons of Ndiswrapper on my system now, and am unsure which version is being loaded at start-up.  

My /usr/network/interfaces file contains: 

auto lo
iface lo inet loopback

and Ndiswrapper is in my modprobe.d directory.

Why is this so difficult?  Please help!

---

### Post by coffeecat on 2015-04-24
> **John_Mackenzie said:**
> Why is this so difficult?

Because you are trying to configure ndiswrapper which should be the absolute last option you should ever consider. Most people prefer to purchase a wireless USB device that works out of the box in Ubuntu (most do) rather than inflict ndiswrapper upon themselves.

I've moved this to the ***Networking & Wireless*** section so that those who take a particular interest in wireless devices will be able to help you. Please read the sticky here:

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Download and run the wireless script and then post the wireless-info.txt file it generates, so that those who help can see if there is a better way of fixing your problem.

---

### Post by John_Mackenzie on 2015-04-25
Thx, Coffeecat, for your reply.  Something which runs well straight "out of the box" sounds good to me!  Therefore I'm gonna go with a hot-wired ethernet connection - and be done with this problem.  

I have 75 updates waiting to install, and my system is becoming unstable - prompting me every 30 sec or so for new connection information, and then freezing up after a couple of reconnection attempts.  

I am sure your networking experts could've eventually gotton to the bottom of my usb wireless device hook-up problems.  

But in view of your comments and in the interest of expediency, I think a wired connection is a good work around - given all of the effort expended to date.

---

### Post by coffeecat on 2015-04-25
Well - your wireless device may be easy to configure or it may not, but by installing ndiswrapper things have become clouded. If you wish to run the wireless script and post the results I'm sure someone will be able to see whether it is worth expending effort on your wireless device or not.

---

### Post by John_Mackenzie on 2015-04-25
OK, here's the wireless info file received from my system:

```

########## wireless info START ##########

Report from: 25 Apr 2015 09:07 EDT -0400

Booted last: 25 Apr 2015 09:03 EDT -0400

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid

##### kernel ############################

Linux 2.6.32-122-rtai #rtai SMP Tue Jul 27 12:44:07 CDT 2010 i686 unknown unknown GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

GNOME

##### lspci #############################

00:13.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

##### lsusb #############################

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0586:3419 ZyXEL Communications Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

ndiswrapper           187876  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xc400 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1130 (1.1 KB)  TX bytes:1350 (1.3 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:-2147483648 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

domain GraceComputers.local
search Type address
nameserver 192.168.0.6
nameserver 4.2.2.2

##### NetworkManager info ###############

NetworkManager Tool

State: asleep

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unmanaged
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             unmanaged
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=false
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory

nm-system-settings.conf (used up to Ubuntu 10.04):

[main]
plugins=ifupdown,keyfile

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'C363J' [AC1]>
                    ESSID:"C363J"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'IFRG1' [AC2]>
                    ESSID:"IFRG1"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: <MAC 'TY9DP' [AC3]>
                    ESSID:"TY9DP"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-96 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ndiswrapper]
filename:       /lib/modules/2.6.32-122-rtai/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.57
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     F6DADA61B4D1144125AE04B
depends:        
vermagic:       2.6.32-122-rtai SMP mod_unload 586TSC 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #################

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

##### /etc/modules ######################

lp

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v0586p340Fd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0586p3410d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0586p3419d*dc*dsc*dp*ic*isc*ip* ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/action_wpa] (777 root)
PATH=/sbin:/usr/sbin:/bin:/usr/bin
if [ ! -x /sbin/wpa_action ]; then
    exit 0
fi
SELF=action_wpa
COMMAND=
IFPLUGD_IFACE=
case "${1}" in
        suspend|hibernate)
                COMMAND=disconnect
                ;;
        resume|thaw)
                COMMAND=reconnect
                ;;
esac
if [ -z "$COMMAND" ]; then
    # ifplugd(8) - <iface> <action>
    #
    # If an ifplugd managed interface is brought up, disconnect any
    # wpa-roam managed interfaces so that only one "roaming" interface
    # remains active on the system.
    IFPLUGD_IFACE="${1}"
    case "${2}" in
        up)
            COMMAND=disconnect
            ;;
        down)
            COMMAND=reconnect
            ;;
        *)
            echo "${SELF}: unknown $0 arguments: ${@}" >&2
            exit 1
            ;;
        esac
fi
if [ -z "$COMMAND" ]; then
    echo "${SELF}: unknown arguments: ${@}" >&2
    exit 1
fi
for CTRL in /var/run/wpa_supplicant/*; do
    [ -S "${CTRL}" ] || continue
    IFACE="${CTRL#/var/run/wpa_supplicant/}"
    wpa_action "${IFACE}" check || continue
    if [ "${IFPLUGD_IFACE}" ] && [ "${IFPLUGD_IFACE}" = "${IFACE}" ]; then
        # if ifplugd is managing this interface (not likely but..)
        # do nothing
        continue
    fi
    wpa_cli -i "${IFACE}" "${COMMAND}"
done

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x0586:0x3419 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    9.637959] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[    9.801415] type=1505 audit(1429966987.990:3):  operation="profile_load" pid=673 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.215081] ndiswrapper: driver wlangzg (ZyXEL Communications Corp.,09/22/2008,1.7.3.38) loaded
[   10.216429] type=1505 audit(1429966988.406:7):  operation="profile_replace" pid=818 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.801084] wlan0: ethernet device <MAC 'wlan0' [IF]> using NDIS driver: wlangzg, version: 0x1070326, NDIS version: 0x501, vendor: 'ZyXEL G-220v3 Wireless USB Adapter', 0586:3419.F.conf
[   10.807555] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   10.846548] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.384964] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   50.840018] wlan0: no IPv6 routers present

########## wireless info END ############


```

---

### Post by coffeecat on 2015-04-25
There were a lot of incomplete or broken BBCode quote tags in your post. I've removed them and substituted code tags which preserve formatting. Anyway, to your problem. This is the fundamental issue you need to address before troubleshooting your wireless: 

> **John_Mackenzie said:**
> 
```

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid


```


Ubuntu 10.04 desktop passed end-of-life two years ago and the server edition is just about to go end-of-life. Those 75 updates were tested only against the server edition and may not be compatible with the desktop. Indeed, a few months ago an update for server 10.04 caused severe problems for those still running the desktop version. This may explain your instability problems. I suggest you don't try to upgrade, but backup your data and go for a fresh installation of a supported version, currently 14.04 for long-term-support, or the just released 15.04 if you don't mind only 9 months support. Don't go for 14.10 as it only has 3 months' life left.

Once you have a fresh installation of a supported version, you may find that your wireless device works without further fiddling about. But, if not, someone will be able to help you, hopefully without recourse to ndiswrapper. Your wireless device id is 0586:3419, which is a Zydas chipset, which ought to just work, but we'll see.

Another thing to be aware of. Ubuntu 10.04 came with the old gnome 2 desktop. That has now been replaced in Ubuntu with the Unity desktop. Some dislike it; others, including myself, like it. You may or may not. If you don't, there are alternatives available in the recognised Ubuntu flavours, such as Xubuntu or Ubuntu Mate which closely resembles what you have been using in 10.04.

The important point is that we won't be able to help you until you have a working installation of a currently supported release of Ubuntu or one of the Ubuntu flavours.  

Good luck!

---

### Post by John_Mackenzie on 2015-04-27
All those Ubuntu users who need help, take 1 step forward .............. not so fast John!  Tis truly a mine field out there!  Nevertheless, thx for your advice.

---

### Post by kurt18947 on 2015-04-27
Coffeecat has it right. A live DVD or USB will tell you how your wifi device will interact without having to do a full install. I find 14.04 quite boring, it just works which is a GOOD thing. Ubuntu-Mate is quite similar to gnome2 and is also quite lightweight so may work well on older/lower powered machines. I did have video problems trying to install Ubuntu-Mate on an HP Mini1000 where Xubuntu works perfectly. Built-in WiFi support has improved quite a lot in recent kernels so that may remove the need for NDIS-wrapper.

Edit: A quick google using the I.D. shown in the wireless script output shows this:

[https://wikidevi.com/wiki/ZyXEL_ZyAIR_G-220_v3](https://wikidevi.com/wiki/ZyXEL_ZyAIR_G-220_v3). Perhaps you'll need to enable backports.


[CENTER] **WI1 chip1:** **ZyDAS** ZD1211B
[/CENTER]
 [CENTER] **WI1 chip2:** **Airoha** AL2230
[/CENTER]
  **Probable Linux driver**
[**[COLOR=green]zd1211rw[/COLOR]**]("http://wireless.kernel.org/en/users/Drivers/zd1211rw") ([**[COLOR=magenta]in backports[/COLOR]**]("https://backports.wiki.kernel.org/index.php/Main_Page"))
**[USB ID not yet observed in any mainline kernel / this ]("https://wikidevi.com/wiki/List_of_Wi-Fi_Device_IDs_in_Linux")**

---

