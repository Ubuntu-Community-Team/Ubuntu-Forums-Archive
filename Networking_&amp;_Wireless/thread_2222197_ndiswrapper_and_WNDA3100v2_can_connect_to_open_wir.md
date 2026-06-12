---
title: "ndiswrapper and WNDA3100v2 can connect to open wireless but not secure"
date: 2014-05-05
forum: Networking &amp; Wireless
---

### Post by cduston on 2014-05-05
Hey all,
     I'm on Xubuntu 12.04 with a Netgear usb wireless WNDA 3100v2. The problem is that I can connect without authentication (my router has a guest account, which works fine giving a password through a browser) but I cannot connect using any kind of authentication - my other computers connect fine (two phones, tablet, Slackware and two windows machines....) so there shouldn't be anything wrong with the network itself.

Some details to convince you everything seems to be working fine:

```
$ lsusb

Bus 002 Device 007: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]

```

```
$ ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0846:9011) present

```

```
$ iwconfig
wlan1     IEEE 802.11g  ESSID:"<MYESSID>-guest"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 98:FC:11:44:52:27   
          Bit Rate=144 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management max timeout:0us  mode:All packets received
          Link Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The problem is evident here:
```
$ dmesg | grep -e ndis -e wlan
[   12.183763] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   12.417622] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[   12.967112] wlan0: ethernet device 9c:d3:6d:01:d5:e6 using NDIS driver: bcmwlhigh5, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[   12.970187] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   12.971220] usbcore: registered new interface driver ndiswrapper
[   12.989774] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   12.989799] udevd[420]: renamed network interface wlan0 to wlan1
[   13.566729] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   13.566878] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   24.781670] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   71.748332] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  108.814846] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  124.242647] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  139.672231] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  498.077189] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  513.506622] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  528.943966] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  579.947424] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  595.469895] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  646.917675] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  662.435461] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  695.749132] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  711.184713] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  726.607633] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  760.787404] ndiswrapper: device wlan1 removed
[  763.531083] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[  764.080307] wlan0: ethernet device 9c:d3:6d:01:d5:e6 using NDIS driver: bcmwlhigh5, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[  764.083591] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  764.113692] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[  764.113718] udevd[530]: renamed network interface wlan0 to wlan1
[  764.118197] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  764.118337] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  803.142564] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  818.126471] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  833.561331] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  848.988625] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  883.166158] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  898.591552] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  914.020835] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  969.131918] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[  984.586206] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[ 1015.391430] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[ 1030.819425] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[ 1046.246578] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[ 1192.450895] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[ 1207.967086] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[ 1309.261147] wlan1: no IPv6 routers present
[ 2634.377083] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[ 2649.803124] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[ 2665.227448] ndiswrapper (iw_set_freq:437): setting configuration failed (00010003)
[ 2812.571296] wlan1: no IPv6 routers present

```
Note that the "wlan1: no IPv6" line only occurs AFTER I've connected to the open network. 

The problem seems to be with the "setting configuration failed" stuff. A similar error comes from incorrectly setting the tx-power key (See [http://sourceforge.net/apps/mediawik...etgear_WNA3100]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100")) But that didn't solve the problem (and since the guest access works....). The only strange thing I notice is the "renamed network interface" but I don't really see how that could be a big problem.

Anyone have any thoughts?

---

