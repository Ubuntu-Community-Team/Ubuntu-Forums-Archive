---
title: "WEP in Edgfy eft 6.10"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by Forbuto on 2007-01-19
Hey all, having some difficulty getting WEP working under Ubuntu 6.10 with my wireless card (Dlink card, Atheros driver).  Hopefully someone can assist.

Heres what happening.

My wireless has always worked without any issues under ubuntu (without encryption).  a few days ago decided to enable WEP encyption on the router.  I made (what I thought were) the necessary adjustments to the gnome network settings (entered in Network password), didnt change essid or any other settings as they were working previously without encyption.  Now my wireless does not work.  I've made the below changes to /etc/network/interfaces to reflect my new network settings as well.  I've also pasted my iwconfig output.  It seems to be complaining about my Essid (rx invalid niws number increases constantly), but my essid entered is correct.  Here it is:

INTERFACES contents:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.1.7

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid Wazoo
wireless-key ##############
wireless-rate 54M
wireless-mode managed

auto wlan0
iface wlan0 inet dhcp

-----------------------------------
IWCONFIG:

adam@Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Wazoo"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:C0:02:C5:E9:8E   
          Bit Rate=54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=23/94  Signal level=-72 dBm  Noise level=-95 dBm
          Rx invalid nwid:2174  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

adam@Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Wazoo"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:C0:02:C5:E9:8E   
          Bit Rate=54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=24/94  Signal level=-71 dBm  Noise level=-95 dBm
          Rx invalid nwid:2215  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-------------------------------------------------

When I try to ping my router, I get this:

adam@Ubuntu:~$ ping 192.168.1.1
connect: Network is unreachable

If anyone can assist, it would be much appreciated.  Let me know if more info is required.  Thanks.

forbs

---

### Post by Forbuto on 2007-01-19
I should also mention, the machine also boots into windows , and the wireless works fine with WEP.

---

