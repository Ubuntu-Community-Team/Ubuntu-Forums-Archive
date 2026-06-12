---
title: "Ubuntu 16.04 Unable to join an ad hoc network"
date: 2017-11-06
forum: Networking &amp; Wireless
---

### Post by pchan2 on 2017-11-06
Hi all,

I have a laptop HP ZBOOK G2. I have to install Ubuntu 16.04 for a project.
I would like to create an ad hoc network but it seems my laptop is unable to join it.
I add the following lines in /etc/network/interfaces:

auto wlp61s0

iface wlp61s0 inet static
        address 10.0.0.1
        netmask 255.255.255.0
        wireless-essid HADHOCK
        wireless-channel 5
        wireless-mode ad-hoc
        wireless-power on

Iwconfig and ifconfig give this results:

administrator@PTCTT001:~$ iwconfig
wlp61s0   IEEE 802.11  ESSID:"HADHOCK"  
          Mode:Ad-Hoc  Frequency:2.432 GHz  Cell: Not-Associated   
          Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

administrator@PTCTT001:~$ ifconfig wlp61s0
wlp61s0   Link encap:Ethernet  HWaddr a4:c4:94:a9:83:c3  
          inet adr:10.0.0.1  Bcast:10.0.0.255  Masque:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)


administrator@PTCTT001:~$ dmesg | grep wlp61s0
[    7.862351] iwlwifi 0000:3d:00.0 wlp61s0: renamed from wlan0
[    8.145541] IPv6: ADDRCONF(NETDEV_UP): wlp61s0: link is not ready
[   10.981590] wlp61s0: Trigger new scan to find an IBSS to join
[   14.821406] wlp61s0: Trigger new scan to find an IBSS to join
[   16.837383] wlp61s0: Creating new IBSS network, BSSID 7e:77:74:93:58:0b
[   16.840481] wlp61s0: Failed to join IBSS, driver failure: -22
[   18.821231] wlp61s0: Trigger new scan to find an IBSS to join
[   18.845374] wlp61s0: Creating new IBSS network, BSSID 42:85:e6:a7:9c:25
[   18.848073] wlp61s0: Failed to join IBSS, driver failure: -22
[   20.841139] wlp61s0: Creating new IBSS network, BSSID 02:c9:f5:65:5e:da
[   20.843726] wlp61s0: Failed to join IBSS, driver failure: -22

This laptop has a dual boot with windows 7 Pro 64bit and I have no trouble to create and join an ad hoc. 
My wireless card is an Intel Corporation Dual Band WIreless-N 7260, this is the result of "lshw -C network":
 *-network
       description: Interface réseau sans fil
       produit: Wireless 7260
       fabriquant: Intel Corporation
       identifiant matériel: 0
       information bus: pci@0000:3d:00.0
       nom logique: wlp61s0
       version: 6b
       numéro de série: a4:c4:94:a9:83:c3
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-28-generic firmware=17.459231.0 ip=10.0.0.1 latency=0 link=no multicast=yes wireless=IEEE 802.11
       ressources: irq:37 mémoire:d0100000-d0101fff

Can you help me?
Thanks

---

### Post by pchan2 on 2017-11-07
Hello,

Yesterday I forgot to say that my wireless card doesn't have any trouble to connect to a wifi hotspot.

Any idea?

Thanks

---

### Post by jeremy31 on 2017-11-07
A lot of operating systems don't trust ad-hoc networks anymore.  And by the info you provided, it appears you may have created an ad-hoc network on the Ubuntu laptop, you just might need to see if a Windows PC can join

---

### Post by pchan2 on 2017-11-08
Hi
Thank you for your reply.
A windows PC can't join my ad hoc network.
I would like to create an ad hoc network in order to connect my Ubuntu laptop and a rasberry Pi with Ubuntu Mate 16.04 installed. The rasberry seems not to have any trouble with ad hoc.
Why Ubuntu doesn't trust ad hoc network anymore if we are able to create it on it?

---

