---
title: "[SOLVED] Atheros(not 5007) wireless problem"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by DXM31 on 2008-04-04
A friend gave me a laptop that he couldn't get to work with Vista so...Ubuntu I did go
I have the same issues discussed in this thread
[http://ubuntuforums.org/showthread.php?t=722798&highlight=atheros+wifi0](http://ubuntuforums.org/showthread.php?t=722798&highlight=atheros+wifi0)
except this one got resolved with a switch not being turn on.
I went and downloaded the owners manual and there is no switch.
I have the drivers
168.10.103 latency=24 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wifi0
       version: 01
       serial: 00:c0:a8:d1:bb:2d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
dale@dale-laptop:~$ Ismod | grep ath
bash: Ismod: command not found
dale@dale-laptop:~$ lsmod | grep ath
ath_rate_sample        14208  1 
ath_pci                98336  0 
wlan                  206660  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192720  3 ath_rate_sample,ath_pci

I brought down the wired connection and up ath0 and it is still sleeping
any suggestions?

oops had the wrong url first

---

### Post by DXM31 on 2008-04-05
Still sleeping
I been searching and found
rm /var/run/dhclient.pid
so I deleted pid file and still no go
It's funny when(with your help) I got wifi working on my other laptop there was no wifi in network manager, That one has the 5007 atheros.
This one seemed to have everything to work, it just doesn't work:confused:

---

### Post by kevdog on 2008-04-05
Everything looks OK with what you did, but what does iwlist scan show?

---

### Post by DXM31 on 2008-04-05
It shows me this
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

I have looked all over this laptop to see if there is a switch.
I did notice some missing screws so the guy I got this from had it open for some reason.

---

### Post by vs8 on 2008-04-05
I think I have that card too. Ubuntu has the restricted driver but it doen't work.

 *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:16:36:89:69:c3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=24.138.206.40 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1 UNCLAIMED
       description: Ethernet controller
       [COLOR="Red"]product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc[/COLOR].
       physical id: 4
       bus info: pci@0000:08:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10

Can someone tell me how to make this thing work? When I go to "Network Settings" the wireless card doesn't show up as it is supposed to.

---

### Post by DXM31 on 2008-04-05
It showed up in my network manager right from the start.
But I installed Wicd thinking that might help, but it didn't, and Wicd removes network manager

---

### Post by DXM31 on 2008-04-05
I'm thinking I should reinstall madwifi

---

### Post by kevdog on 2008-04-05
Check dmesg to see if any errors are showing up.  From what you posted everything looks like a go! Are any wireless networks actually in range?

---

### Post by DXM31 on 2008-04-05
Yes, I am using another laptop to type this.
One you helped setup by the way.
I will try dmesg and see what comes up

---

### Post by DXM31 on 2008-04-05
this is what looks suspicious 
[   30.252000] apm: BIOS not found.
[   30.468000] Failure registering capabilities with primary security module.

Is there an error I should be looking for?

---

### Post by kevdog on 2008-04-05
Ok here is what I pulled from madwifi:

 ¶
Chipset:	AR5005G = (AR2413)
Chip:	AR2413 (802.11b+g)
URL:	[http://www.atheros.com/pt/AR5005G.htm](http://www.atheros.com/pt/AR5005G.htm)
Supports:	IEEE 802.11b, 802.11g
Working: 	not working with version 0.9.2, dmesg reports: "unable to attach hardware: 'Hardware revision not supported' (HAL status 13)"
Notes: 	Several tickets indicate this; no response was ever given. However, some users have reported success, but could not confirm this.
Notes: 	Works perfectly on Slackware 11 (kernel 2.6.18.3) and madwifi 0.9.2. Just modprobe ath_pci after compiling/installing. (this on an Acer 3102 wlmi)
Notes: 	For Kernel 2.6.22.1 use trunk version (madwifi 0.9.3.1 release doesn't compile): svn checkout [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi . That works perfectly (I'm running Slackware 12 on Acer 3102wlmi).
Notes: 	I can confirm that this chipset works great with the madwifi-ng drivers on Debian Testing. Also monitor mode.
Notes: 	chipset is AR1423, as you can see through URL
Notes: 	This chipset works on the Acer Aspire 5040 if you install the acer_acpi driver [http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html](http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html)
Notes: 	Works on the Acer Aspire 3053 if you reload the modules (see [http://rik.rikva.nl/?q=node/10](http://rik.rikva.nl/?q=node/10)) and then run depmod -a (as root)
Notes: 	Works on the Acer Aspire 5051 using madwifi source pulled 2006-12-18 (OpenSuSE 10.2/x86_64)
Notes: 	Works on the Acer Aspire 5100 using madwifi source (Mandriva 2007.0/x86_64)
Notes: 	Cheap Ativa card works ok in gentoo. /etc/init.d/net.athx start does not ifconfig athx up the device, so preferred wireless won't work
Notes: 	Works out of the box with Ubuntu 7.10 and 6.06

The last claimed to work out of the box with 7.10, but who really knows.  All I know is that based on these reviews you should be able to solve your problem and get the card working.  Have you tried compiling from svn sources??

---

### Post by kevdog on 2008-04-05
dmesg should mention something about wifi0, ath0 or ath_pci.  Something like that.  apm is power management.  Dont think that should be a problem.

---

### Post by DXM31 on 2008-04-05
here is some wifi stuff
[   22.916000] ath_hal: module license 'Proprietary' taints kernel.
[   22.920000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   23.052000] wlan: 0.8.4.2 (0.9.3.2)
[   23.288000] ath_pci: 0.9.4.5 (0.9.3.2)
[   23.288000] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 18 (level, low) -> IRQ 22
[   23.888000] input: PC Speaker as /class/input/input2
[   23.908000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   23.908000] Uniform CD-ROM driver Revision: 3.20
[   23.984000] input: PS/2 Mouse as /class/input/input3
[   24.000000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   24.096000] ath_rate_sample: 1.2 (0.9.3.2)
[   24.096000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   24.096000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   24.096000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   24.096000] wifi0: mac 7.8 phy 4.5 radio 5.6
[   24.096000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   24.096000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   24.096000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   24.096000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   24.096000] wifi0: Use hw queue 8 for CAB traffic
[   24.096000] wifi0: Use hw queue 9 for beacons
[   24.372000] wifi0: Atheros 5212: mem=0xc9000000, irq=22

---

### Post by kevdog on 2008-04-05
Hmm I'm not getting what is wrong.  Everything looks right.

With the laptop you did

sudo dhclient -r ath0
sudo dhclient -r eth0
sudo ifconfig ath0 down
sudo ifconfig eth0 down
sudo ifconfig ath0 up

iwlist scan

If no networks show up, move closer to router.  If no networks then show up, lets go for svn.  I can't believe this isn't working.

---

### Post by DXM31 on 2008-04-05
> **kevdog said:**
> 

...  I can't believe this isn't working.

Me either here is what I got from the above
dale@dale-laptop:~$ sudo dhclient -r ath0
[sudo] password for dale:
There is already a pid file /var/run/dhclient.pid with pid 5323
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:c0:a8:d1:bb:2d
Sending on   LPF/ath0/00:c0:a8:d1:bb:2d
Sending on   Socket/fallback
dale@dale-laptop:~$ sudo dhclient -r eth0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:14:0b:09:c1:25
Sending on   LPF/eth0/00:14:0b:09:c1:25
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.10.1 port 67
dale@dale-laptop:~$ sudo ifconfig ath0 down
dale@dale-laptop:~$ sudo ifconfig eth0 down
dale@dale-laptop:~$ sudo ifconfig ath0 up
dale@dale-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

If the wifi card is broken or missing wouldn't I get some kind of error?
And I am about 8' from the router, I will get closer and see what happens.
I am running WEP if that makes a difference.

---

### Post by DXM31 on 2008-04-05
> **kevdog said:**
> ...  Have you tried compiling from svn sources??

How do I do that?

---

### Post by kevdog on 2008-04-05
Do you know how to compile from svn sources the madwifi drivers??

---

### Post by DXM31 on 2008-04-05
No, I don't, 
I have been doing some searches though.
I guess removing and reinstalling from SPM won't work.

---

### Post by kevdog on 2008-04-05
Its really easy

Using your wired connection on that computer

Ok just to make sure thing change, lets just detect the version you currently have:
modinfo ath_pci

sudo ath0 down
sudo eth0 up
sudo dhclient eth0
sudo aptitude install subversion linux-headers-`uname -r` build-essential
sudo modprobe -r ath_pci

cd ~
mkdir madwifi
cd madwifi
svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi_svn
cd madwifi_svn
make clean
make
sudo make install

Ok now lets make sure the version number changed with the installation of the latest ath_pci build:
modinfo ath_pci 

Make sure the driver has changed.

If it has changed proceed:
sudo depmod -a
sudo modprobe ath_pci

Confirm ath_pci currently associated with your card by checking with lshw -C network

Then

sudo dhclient -r eth0
sudo eth0 down
sudo ath0 up
iwlist scan


That should be it.  You can do these steps in less than a minute once you do it once.

Just a reminder that if you ever want to update your svn sources to the latest version in the future:
sudo ath0 down
sudo modprobe -r ath_pci
cd ~/madwifi
svn up
cd madwifi_svn
make clean
sudo make install
sudo modprobe ath_pci
sudo ath0 up
...

That's it...Easy!

---

### Post by DXM31 on 2008-04-05
The output from modinfo was different.
But then I got this
dale@dale-laptop:~/madwifi_svn$ sudo modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.22-14-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by kevdog on 2008-04-05
Did you check dmesg to see what the error was?

---

### Post by DXM31 on 2008-04-05
here is dmesg--
[ 7116.228000] UDF-fs: No VRS found
[ 7116.260000] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 7116.348000] ISO 9660 Extensions: RRIP_1991A
[ 7186.524000] ACPI: PCI interrupt for device 0000:05:01.0 disabled
[ 7186.524000] ath_pci: driver unloaded
[ 7797.220000] ath_pci: Unknown symbol ieee80211_check_mic
[ 7797.220000] ath_pci: disagrees about version of symbol ieee80211_encap
[ 7797.220000] ath_pci: Unknown symbol ieee80211_encap
[ 7797.220000] ath_pci: disagrees about version of symbol ieee80211_input
[ 7797.220000] ath_pci: Unknown symbol ieee80211_input
[ 7797.220000] ath_pci: disagrees about version of symbol ieee80211_ifattach
[ 7797.220000] ath_pci: Unknown symbol ieee80211_ifattach
[ 7797.220000] ath_pci: disagrees about version of symbol _ath_hal_attach
[ 7797.220000] ath_pci: Unknown symbol _ath_hal_attach
[ 7797.220000] ath_pci: Unknown symbol ieee80211_skb_untrack_debug
[ 7797.220000] ath_pci: disagrees about version of symbol ieee80211_beacon_update
[ 7797.220000] ath_pci: Unknown symbol ieee80211_beacon_update
[ 7797.220000] ath_pci: Unknown symbol ieee80211_dev_kfree_skb_list_debug
[ 7797.220000] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[ 7797.220000] ath_pci: Unknown symbol ath_hal_process_noisefloor
[ 7797.220000] ath_pci: disagrees about version of symbol ieee80211_vap_setup
[ 7797.220000] ath_pci: Unknown symbol ieee80211_vap_setup
[ 7797.220000] ath_pci: disagrees about version of symbol ieee80211_ifdetach
[ 7797.220000] ath_pci: Unknown symbol ieee80211_ifdetach
[ 7797.220000] ath_pci: Unknown symbol ieee80211_find_txnode_debug
[ 7797.224000] ath_pci: disagrees about version of symbol ieee80211_input_monitor
[ 7797.224000] ath_pci: Unknown symbol ieee80211_input_monitor
[ 7797.224000] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[ 7797.224000] ath_pci: Unknown symbol ath_hal_computetxtime
[ 7797.224000] ath_pci: disagrees about version of symbol ieee80211_crypto_newkey
[ 7797.224000] ath_pci: Unknown symbol ieee80211_crypto_newkey
[ 7797.224000] ath_pci: disagrees about version of symbol ieee80211_crypto_setkey
[ 7797.224000] ath_pci: Unknown symbol ieee80211_crypto_setkey
[ 7797.224000] ath_pci: disagrees about version of symbol ieee80211_dump_pkt
[ 7797.224000] ath_pci: Unknown symbol ieee80211_dump_pkt
[ 7797.224000] ath_pci: Unknown symbol ieee80211_dev_alloc_skb_debug
[ 7797.224000] ath_pci: disagrees about version of symbol ieee80211_ioctl_create_vap
[ 7797.224000] ath_pci: Unknown symbol ieee80211_ioctl_create_vap
[ 7797.224000] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[ 7797.224000] ath_pci: Unknown symbol ath_hal_mhz2ieee
[ 7797.224000] ath_pci: disagrees about version of symbol ieee80211_stop_running
[ 7797.224000] ath_pci: Unknown symbol ieee80211_stop_running
[ 7797.224000] ath_pci: Unknown symbol ieee80211_dev_kfree_skb_debug
[ 7797.224000] ath_pci: disagrees about version of symbol ieee80211_cipher_none
[ 7797.224000] ath_pci: Unknown symbol ieee80211_cipher_none
[ 7797.224000] ath_pci: Unknown symbol _ath_hal_detach
[ 7797.224000] ath_pci: disagrees about version of symbol ieee80211_crypto_delkey
[ 7797.224000] ath_pci: Unknown symbol ieee80211_crypto_delkey
[ 7797.224000] ath_pci: Unknown symbol ath_debug_global
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_beacon_miss
[ 7797.228000] ath_pci: Unknown symbol ieee80211_beacon_miss
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_beacon_alloc
[ 7797.228000] ath_pci: Unknown symbol ieee80211_beacon_alloc
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_getcfframe
[ 7797.228000] ath_pci: Unknown symbol ieee80211_getcfframe
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_iterate_nodes
[ 7797.228000] ath_pci: Unknown symbol ieee80211_iterate_nodes
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_vap_attach
[ 7797.228000] ath_pci: Unknown symbol ieee80211_vap_attach
[ 7797.228000] ath_pci: Unknown symbol ieee80211_wme_updateparams
[ 7797.228000] ath_pci: Unknown symbol alloc_skb_debug
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_ibss_merge
[ 7797.228000] ath_pci: Unknown symbol ieee80211_ibss_merge
[ 7797.228000] ath_pci: Unknown symbol skb_copy_debug
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_rate_attach
[ 7797.228000] ath_pci: Unknown symbol ieee80211_rate_attach
[ 7797.228000] ath_pci: Unknown symbol ieee80211_unref_node_debug
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_rate_detach
[ 7797.228000] ath_pci: Unknown symbol ieee80211_rate_detach
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_send_qosnulldata
[ 7797.228000] ath_pci: Unknown symbol ieee80211_send_qosnulldata
[ 7797.228000] ath_pci: Unknown symbol ieee80211_find_rxnode_debug
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_create_vap
[ 7797.228000] ath_pci: Unknown symbol ieee80211_create_vap
[ 7797.228000] ath_pci: Unknown symbol ieee80211_skb_track_debug
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_input_all
[ 7797.228000] ath_pci: Unknown symbol ieee80211_input_all
[ 7797.228000] ath_pci: Unknown symbol ieee80211_ref_node_debug
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_start_running
[ 7797.228000] ath_pci: Unknown symbol ieee80211_start_running
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_vap_detach
[ 7797.228000] ath_pci: Unknown symbol ieee80211_vap_detach
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_announce
[ 7797.228000] ath_pci: Unknown symbol ieee80211_announce
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_mark_dfs
[ 7797.228000] ath_pci: Unknown symbol ieee80211_mark_dfs
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_chan2ieee
[ 7797.228000] ath_pci: Unknown symbol ieee80211_chan2ieee
[ 7797.228000] ath_pci: disagrees about version of symbol ath_hal_init_channels
[ 7797.228000] ath_pci: Unknown symbol ath_hal_init_channels
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_dturbo_switch
[ 7797.228000] ath_pci: Unknown symbol ieee80211_dturbo_switch
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_crypto_encap
[ 7797.228000] ath_pci: Unknown symbol ieee80211_crypto_encap
[ 7797.228000] ath_pci: disagrees about version of symbol ieee80211_getrssi
[ 7797.228000] ath_pci: Unknown symbol ieee80211_getrssi
[ 7797.228000] ath_pci: Unknown symbol ieee80211_cancel_scan
[ 7797.228000] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[ 7797.228000] ath_pci: Unknown symbol ath_hal_getwirelessmodes

---

### Post by kevdog on 2008-04-05
Ok, lets back up a step then.

Download and install the most stable release then:
[http://sourceforge.net/project/showfiles.php?group_id=82936](http://sourceforge.net/project/showfiles.php?group_id=82936)

---

### Post by DXM31 on 2008-04-05
bz2 or gz or does it matter?

---

### Post by kevdog on 2008-04-05
Or if you want to try something, remove the linux-restricted-modules using synaptic (this is what originally installed your drivers), and then trying making the svn sources again

(Using synaptic -- uninstall linux-restricted-modules-<kernel-version>)
cd ~/madwifi/madwif_svn
make clean
make
sudo make install

---

### Post by DXM31 on 2008-04-05
I still get this error:

dale@dale-laptop:~/madwifi_svn$ sudo modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.22-14-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I didn't think you needed to see dmesg again

---

### Post by kevdog on 2008-04-05
Get the error when doing what -- attempting the svn install of the stable latest release

and no gz or bzip does not matter.

---

### Post by DXM31 on 2008-04-05
I got the error when doing the sudo modprobe ath_pci
I downloaded the tar.gz

---

### Post by kevdog on 2008-04-05
Which version the svn or stable?

Try this real quick

sudo aptitude install ieee80211-source

Then try building and installing the madwifi svn sources again
cd ~/madwifi/madwifi_svn
sudo make uninstall
make clean
make 
sudo make install
sudo modprobe ath_pci

Are you sure you installed the linux-header package correctly?

---

### Post by DXM31 on 2008-04-05
I see a problem
when trying to cd into the madwifi_svn it is not madwifi/madwifi_svn
I have two different directories under my home directory a madwifi and a madwifi_svn
I did something wrong somewhere

this caught my attention--
dale@dale-laptop:~$ cd ~/madwifi/madwifi_svn
bash: cd: /home/dale/madwifi/madwifi_svn: No such file or directory

---

### Post by kevdog on 2008-04-05
Its ok,  just b/c you have a different directory structure -- that isnt the problem.  I just used the directory structure so together we wouldnt be confused and I could refer to it by name and location specifically.

Try this
sudo aptitude purge linux-restricted-modules-`uname -r`

Then reboot, and lets start new.

---

### Post by DXM31 on 2008-04-05
OK this is **THE** most confusing thing of all.
It works:confused:
I pulled up Wicd to attach to the LAN and noticed the wireless was there.
So I connected to it(after putting in my WEP key)
Your a genius.
But I have not idea what we did.

---

### Post by kevdog on 2008-04-05
Worked after a reboot??

Just do me a favor and tell me what

modinfo ath_pci

tells you.  What version of the ath_pci driver are you using?

---

### Post by DXM31 on 2008-04-05
It stopped working but it does still show up in Wicd
Here is the modinfo
filename:       /lib/modules/2.6.22-14-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn r3434
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     2E14EC3361C30BBD05E5894
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           beacon_cal:int
parm:           countrycode:Override default country code (int)
parm:           maxvaps:Maximum VAPs (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           tpc:Enable/disable per-packet transmit power control (TPC) capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time driver debug output enable (int)
parm:           ieee80211_debug:Load-time 802.11 debug output enable (int)

---

### Post by kevdog on 2008-04-05
Ok, you are using the svn version.

What do you mean it stopped working?  You need to clarify your remarks.  Its like Im holding a one sided conversation or interogation.

---

### Post by DXM31 on 2008-04-05
Sorry about that
I was replying to you question and hit the submit reply button on the forum and my internet connection was down,
I tried to reconnect to the wireless and it wouldn't reconnect on the wireless so I plugged the LAN back in and that is where I am now.
But the wireless shows up in Wicd and it didn't before.
For some reason the wireless connection got dropped.

---

### Post by kevdog on 2008-04-06
Again you cant run your wired and wireless at the same time.

You know how to release your dhcp lease, take down the active interface, bring up the inactive interface.  The connection can be done by GUI or command line (which I think you've read my tutorial somewhere, sometime before).  WICD is great, however when you are struggling you need usually to try to connect via command line so some debugging output can be generated to help solve a problem.  Once its solved I encourage everyone to go back to the GUI (since really it is easier).

---

### Post by DXM31 on 2008-04-06
I didn't start up eth0 it must have done it on it's own.
I did as you said in you tutorial using the terminal and wifi is back up and running.
Now the question is will it start when I reboot.
I will mark this as solved(when I remember how)
Thanks again

---

### Post by kevdog on 2008-04-06
Well, that's hard to say.  Make sure the ath_pci is listed in /etc/modules.  This will automatically load the kernel module at boot (preventing the modprobe crap).  If your wired connection is plugged in, Im going to guess that might take preference, but that is a guess.

Marking a thread solved is under thread tools located under page 4 of 4 towards the top of the page.

---

### Post by DXM31 on 2008-04-06
It's not plugged in but I lost wireless again.
Time to search for a solution to the wireless loosing it's connection.
At least it works...sort of.:)

---

### Post by kevdog on 2008-04-06
That sucks if the connection keeps dropping..sorry about that..might want to try turning off ipv6??

---

