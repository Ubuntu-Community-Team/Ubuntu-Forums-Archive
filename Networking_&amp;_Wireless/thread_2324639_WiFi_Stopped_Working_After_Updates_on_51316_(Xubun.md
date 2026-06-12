---
title: "WiFi Stopped Working After Updates on 5/13/16 (Xubuntu 14.04.4 LTS)"
date: 2016-05-15
forum: Networking &amp; Wireless
---

### Post by roostishaw2 on 2016-05-15
Hello,

I used my desktop normally on Friday, but when I booted it up on Saturday (yesterday), there was no WiFi icon in the icon tray and there is now no network connection. I believe I installed some updates on Friday before shutting down.

I've been searching around for a solution for a few hours now. I have tried downgrading the libnl packages (with no luck; lots of errors), verifying that /etc/network/interfaces looks like it "should", using "sudo ifconfig eth0 up" and "sudo ifconfig wlan0 up", killing and restarting network-manager, and several other things.

Here are the outputs to a few commands I've been seeing to diagnose network issues:

```
me@desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Ethernet Connection (2) I218-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 00
       serial: 08:62:66:26:dd:43
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.1-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:df800000-df81ffff memory:df838000-df838fff ioport:f040(size=32)
  *-network DISABLED
       description: Wireless interface
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 03
       serial: 40:e2:30:98:75:73
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:16 memory:df400000-df407fff memory:df200000-df3fffff
```

At one point I had it so that neither of the above read "DISABLED", but it looks like it's back to showing that now.

```
me@desktop:~$ lspci -knn | grep Net -A2
05:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:855c]
    Kernel driver in use: wl
```

```
me@desktop:~$ sudo nm-applet 

** (nm-applet:2690): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-ctmYfT0Ijd: Connection refused

(nm-applet:2690): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2769:41: Expected a valid selector

** (nm-applet:2690): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files

(nm-applet:2690): nm-applet-WARNING **: Error connecting to ModemManager: Error calling StartServiceByName for org.freedesktop.ModemManager1: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ExecFailed: Cannot launch daemon, file not found or permissions invalid

(nm-applet:2690): nm-applet-WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files
nm-applet-Message: using fallback from indicator to GtkStatusIcon

**^C**

nm-applet-Message: PID 0 (we are 2690) sent signal 2, shutting down...
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
nm-applet-Message: PID 2690 (we are 2690) sent signal 15, shutting down...

** (nm-applet:2690): CRITICAL **: nm_secret_agent_unregister: assertion 'priv->registered == TRUE' failed
```

After running "sudo nm-applet", the network icon appears in the icon tray, but clicking it only shows "NetworkManager is not running..." Another random snippet of info: I do not have "trusty-proposed" enabled for updates, and I don't think I ever have.

Can someone please point me in the right direction, or let me know what other info I can provide to help solve my problem?

Thank you!

---

### Post by roostishaw2 on 2016-05-15
Here's the output of that wireless-info script:

```

########## wireless info START ##########

Report from: 15 May 2016 07:55 EDT -0400

Booted last: 15 May 2016 07:07 EDT -0400

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-59-generic #65~14.04.1-Ubuntu SMP Tue Apr 19 18:57:09 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Xubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
    Subsystem: ASUSTeK Computer Inc. Device [1043:85c4]
    Kernel driver in use: e1000e

05:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:855c]
    Kernel driver in use: wl

##### lsusb #############################

Bus 006 Device 002: ID 8087:8001 Intel Corp. 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 8087:8009 Intel Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 13fe:3d00 Kingston Technology Company Inc. 
Bus 001 Device 002: ID 1038:1384 SteelSeries ApS 
Bus 001 Device 005: ID 0b05:17cf ASUSTek Computer, Inc. 
Bus 001 Device 006: ID 0665:6000 Cypress Semiconductor 
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6369280  0 
eeepc_wmi              16384  0 
asus_wmi               24576  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0 
cfg80211              532480  1 wl
wmi                    20480  2 mxm_wmi,asus_wmi
video                  20480  1 asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:df800000-df820000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

    None found.

##### NetworkManager info ###############

** (process:2982): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files

** (process:2982): WARNING **: error: could not connect to NetworkManager

NetworkManager Tool

State: unknown

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

[[/etc/NetworkManager/system-connections/NSA5]] (600 root)
[connection] id=NSA5 | type=802-11-wireless
[802-11-wireless] ssid=NSA5 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     26 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/3.19.0-59-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       3.19.0-59-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.19.0-59-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46EBD6732E992614FD7F01B
depends:        
intree:         Y
vermagic:       3.19.0-59-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3B:80:88:D8:E6:B9:3E:AD:6E:77:B0:3C:9C:4E:5C:BA:FB:1A:0B:20
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x15a1 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x43b1 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    3.764190] init: network-manager main process (1080) killed by SEGV signal
[    3.764194] init: network-manager main process ended, respawning
[    3.768649] init: network-manager main process (1084) killed by SEGV signal
[    3.768653] init: network-manager main process ended, respawning
[    3.773436] init: network-manager main process (1088) killed by SEGV signal
[    3.773442] init: network-manager main process ended, respawning
[    3.777916] init: network-manager main process (1092) killed by SEGV signal
[    3.777921] init: network-manager main process ended, respawning
[    3.782390] init: network-manager main process (1096) killed by SEGV signal
[    3.782395] init: network-manager main process ended, respawning
[    3.786736] init: network-manager main process (1100) killed by SEGV signal
[    3.786741] init: network-manager main process ended, respawning
[    3.791089] init: network-manager main process (1104) killed by SEGV signal
[    3.791093] init: network-manager main process ended, respawning
[    3.795645] init: network-manager main process (1108) killed by SEGV signal
[    3.795649] init: network-manager main process ended, respawning
[    3.799944] init: network-manager main process (1112) killed by SEGV signal
[    3.799948] init: network-manager respawning too fast, stopped
[  370.075724] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1256.755005] traps: NetworkManager[2628] general protection ip:469fee sp:7fffd0059330 error:0 in NetworkManager[400000+10d000]
[ 1256.824208] init: network-manager main process (2628) killed by SEGV signal
[ 1256.824214] init: network-manager main process ended, respawning
[ 1256.828225] traps: NetworkManager[2633] general protection ip:469fee sp:7ffdfc898530 error:0 in NetworkManager[400000+10d000]
[ 1256.888321] init: network-manager main process (2633) killed by SEGV signal
[ 1256.888327] init: network-manager main process ended, respawning
[ 1256.892194] traps: NetworkManager[2638] general protection ip:469fee sp:7fff8c17c470 error:0 in NetworkManager[400000+10d000]
[ 1256.952027] init: network-manager main process (2638) killed by SEGV signal
[ 1256.952033] init: network-manager main process ended, respawning
[ 1256.956001] traps: NetworkManager[2643] general protection ip:469fee sp:7ffde2787bc0 error:0 in NetworkManager[400000+10d000]
[ 1257.015273] init: network-manager main process (2643) killed by SEGV signal
[ 1257.015280] init: network-manager main process ended, respawning
[ 1257.019507] traps: NetworkManager[2648] general protection ip:469fee sp:7ffdbe70be10 error:0 in NetworkManager[400000+10d000]
[ 1257.080366] init: network-manager main process (2648) killed by SEGV signal
[ 1257.080373] init: network-manager main process ended, respawning
[ 1257.084445] traps: NetworkManager[2653] general protection ip:469fee sp:7ffd66f2c6a0 error:0 in NetworkManager[400000+10d000]
[ 1257.145109] init: network-manager main process (2653) killed by SEGV signal
[ 1257.145115] init: network-manager main process ended, respawning
[ 1257.148948] traps: NetworkManager[2658] general protection ip:469fee sp:7ffd26b6da30 error:0 in NetworkManager[400000+10d000]
[ 1257.209643] init: network-manager main process (2658) killed by SEGV signal
[ 1257.209650] init: network-manager main process ended, respawning
[ 1257.213707] traps: NetworkManager[2663] general protection ip:469fee sp:7ffce1201280 error:0 in NetworkManager[400000+10d000]
[ 1257.273139] init: network-manager main process (2663) killed by SEGV signal
[ 1257.273146] init: network-manager main process ended, respawning
[ 1257.277199] traps: NetworkManager[2668] general protection ip:469fee sp:7ffdd51fe290 error:0 in NetworkManager[400000+10d000]
[ 1257.337713] init: network-manager main process (2668) killed by SEGV signal
[ 1257.337720] init: network-manager main process ended, respawning
[ 1257.341554] traps: NetworkManager[2673] general protection ip:469fee sp:7fff9af2b6e0 error:0 in NetworkManager[400000+10d000]
[ 1257.400840] init: network-manager main process (2673) killed by SEGV signal
[ 1257.400846] init: network-manager main process ended, respawning
[ 1257.463779] init: network-manager main process (2678) killed by SEGV signal
[ 1257.463786] init: network-manager respawning too fast, stopped
[ 2940.611218] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############


```

---

### Post by Bashing-om on 2016-05-15
roostishaw2; Well;

Maybe a victim of the update bug ?

see: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634)
One method of fixing, that many find easier to implement:
[http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841](http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by marty777 on 2016-05-15
A real nasty update bug.
Luckily it can be solved with a live system dvd and a usb-stick.

This helped me to solve it quickly (one solution of the link above).

------------
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: answercell"]      You can do it this way to fix the problem:
   Download file:

  
[LIST]
[*]libnl-3-200_3.2.21-1_XXX.deb 
[*]libnl-route-3-200_3.2.21-1_XXX.deb 
[*]libnl-genl-3-200_3.2.21-1_XXX.deb

  OS 32bit: XXX = i386 || OS 64bit: XXX = amd64 
[/LIST]
  Link: [http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl3/](http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl3/)

copy them onto a usb-stick, reboot your system with your HD-system.
got to folder and install them with the command:
[INDENT]   sudo dpkg -i lib*.deb
 [/INDENT]
Then Reboot. Done 

     [/TD]
[/TR]
[/TABLE]
-------

---

### Post by roostishaw2 on 2016-05-15
Thanks so much guys!

I followed the instructions of marty777 and it worked. I think I actually tried those instructions earlier but was using the wrong versions of the debs (32 vs. 64 bit).

Is there any way to know when it's safe to update?

I don't have trusty-proposed enabled.

---

### Post by marty777 on 2016-05-16
In that particular case, there was no (safe) way to avoid it.
Because updates should be installed quickly, but they should have been better verified.

---

### Post by konstantinos4 on 2016-05-16
I had the same problem! I confirm this [http://askubuntu.com/a/771685](http://askubuntu.com/a/771685) solves the problem at least until an update fix is published.

---

