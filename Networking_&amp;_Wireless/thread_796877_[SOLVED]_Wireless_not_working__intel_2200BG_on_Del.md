---
title: "[SOLVED] Wireless not working:  intel 2200BG on Dell d600 with Hardy"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by Ph83drus on 2008-05-16
I bought an intel 2200bg wireless card for my dell d600 with Hardy.

Because the broadcom wireless was a NIGHTMARE on Hardy.  I acually had it working before updating to Hardy, but even then the connectivity was very poor.  I figured I'd dish out 26 bucks for an Intel card that was supposed to be a shoe in for Ubuntu.

and guess what, my new Intel wireless card doesn't work either!!

I can see the wireless networks that I COULD connect to, but it will not connect with Wicd. Will not resolve ip.

phaedrus@phaedrus-laptop:~$ dmesg | grep ipw
[ 25.547967] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[ 25.547972] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[ 26.255098] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[ 28.091135] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
phaedrus@phaedrus-laptop:~$ dmesg | grep eth
[ 11.631809] eth0: Tigon3 [partno(BCM95702A20) rev 1002 PHY(5703)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:0d:56:77:6f:11
[ 11.631818] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[ 11.631822] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[ 12.702749] Driver 'sd' needs updating - please use bus_type methods
[ 12.702975] sda:<4>Driver 'sr' needs updating - please use bus_type methods
[ 1875.137422] eth1: no IPv6 routers present
[ 1619.425171] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3780.989125] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 3780.989137] tg3: eth0: Flow control is off for TX and off for RX.
[ 3780.993086] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1422.626310] eth0: no IPv6 routers present
[ 4278.637419] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 4352.461685] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1867.041490] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1867.041497] tg3: eth0: Flow control is off for TX and off for RX.
[ 1867.043211] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4370.658150] eth0: no IPv6 routers present
phaedrus@phaedrus-laptop:~$
phaedrus@phaedrus-laptop:~$


Can anyone help?!  I'd love to show off my computer to my parents, hopefully get them on the Ubuntu train.  But so far, all they've seen is my frustration with wireless.   Seems to me that there's a LOT of people frustrated with wireless on Hardy.

---

### Post by chili555 on 2008-05-16
> ADDRCONF(NETDEV_CHANGE): eth0: link becomes readyLooks like your wired ethernet is connected and has an IP address. Network Manager, which is installed by default, doesn't like that. [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) I'm not sure Wicd likes it either.

Please detach the wire and, just because I'm neurotic, reboot. Does your wireless card work better?

---

### Post by Ph83drus on 2008-05-17
Still does not work.

I unplugged my ethernet cord, and rebooted.

Nothing on wireless.  Wicd just searches and searches when trying to obtain the ip address.

---

### Post by Ph83drus on 2008-05-17
thank you for helping me! I'd really like this to work! and as far as I understand, intel 2200BG should be a really easy wireless solution for Ubuntu.

---

### Post by chili555 on 2008-05-17
> intel 2200BG should be a really easy wireless solution for UbuntuYes, it should, but it's shy today! Let's get down to basics: first, is the module loaded?```
lsmod | grep ipw
lsmod | grep ieee
```Second, does *iwconfig* see it?```
sudo iwconfig
```Third, any encryption here? WEP, WPA or Klingon? Fourth, is the wireless switch or key combination in the ON mode?```
sudo cat /var/log/messages | grep switch
```Please do your checks with the wire detached. To post the results, just leave the terminal open and copy and paste once you are back on the forum.

---

### Post by Ph83drus on 2008-05-17
Great, okay, I unplugged it, then ran everything in terminal.

phaedrus@phaedrus-laptop:~$ lsmod | grep ipw
ipw2200               146120  0 
ieee80211              35528  1 ipw2200


phaedrus@phaedrus-laptop:~$ lsmod | grep ieee
ieee80211              35528  1 ipw2200
ieee80211_crypt         7040  1 ieee80211


phaedrus@phaedrus-laptop:~$ sudo iwconfig
[sudo] password for phaedrus: 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"eclipse"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

phaedrus@phaedrus-laptop:~$ sudo cat /var/log/messages | grep switch
May 16 01:08:30 phaedrus-laptop kernel: [    8.179807] SMP alternatives: switching to UP code
May 16 10:05:19 phaedrus-laptop kernel: [    6.730795] SMP alternatives: switching to UP code
May 16 10:14:57 phaedrus-laptop kernel: [    7.910083] SMP alternatives: switching to UP code
May 16 16:17:23 phaedrus-laptop kernel: [    7.956786] SMP alternatives: switching to UP code
May 16 17:57:56 phaedrus-laptop kernel: [    7.735845] SMP alternatives: switching to UP code
May 17 12:19:00 phaedrus-laptop kernel: [    7.444170] SMP alternatives: switching to UP code
phaedrus@phaedrus-laptop:~$

---

### Post by chili555 on 2008-05-17
Looks very healthy to me! What is the result of:```
sudo iwconfig eth1 rate auto
sudo dhclient eth1
```Of course, with the wire detached.

No encryption here?

---

### Post by Ph83drus on 2008-05-17
hmm.. well, i set up the wireless router to use wpa2 encryption.

is that what you mean?

---

### Post by chili555 on 2008-05-17
Exactly! The wireless needs WPA2 setup, also. Here is the resident evil, er, I mean genius: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by Ph83drus on 2008-05-17
ahhh!!! connected!

I did apt-get wpa-supplicant, but it was already downloaded.

So then I did 

sudo apt-get install wpasupplicant 

And i noticed this:

iface eth1 inet dhcp
wpa-psk 9163bd67b07bdae563ac2526d0dcd86eb461d72f1e3c22b239e276975f66f93d
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid eclipse


next to wpa-driver it says wext!

Which I remembered being one of the options in wicd.  
I went to wicd, and chose wext.

And boom! I could connect to my wpa2 encrypted network.

yeah!  Thank you for your help!
Very much appreciated!

---

