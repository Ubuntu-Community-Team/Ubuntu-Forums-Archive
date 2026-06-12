---
title: "Unable to setup Atheros AR2413 with madwifi"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by pkpkpkpk on 2008-01-05
Hi,

I followed the instructions below, and before that built madwifi based on other posts on this forum.

I am unable to get it to work.

Here is some info abt my system

 [COLOR="Red"]ubuntu:~$ lspci | grep Ath
01:08.0 Ethernet controller: Atheros Communications, Inc. **AR2413 **802.11bg NIC (rev 01)
[/COLOR]
now, 

[COLOR="Red"]ubuntu:~$ sudo dmesg | grep ath_hal
[   49.339097] ath_hal: module license 'Proprietary' taints kernel.
[   49.343667] ath_hal: 0.9.30.13 (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)[/COLOR]

So, it does look like my model is not supported. 

On the steps below, 

I ran
[COLOR="Red"]ubuntu:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu:~# iwconfig ath0 channel 11
ubuntu:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results
[/COLOR]

Can someone please help me find the right version of the Madwifi Hal.
I am unable to proceed on this.

TIA!

---

### Post by marcocec on 2008-01-27
I've got the same card Atheros AR2413
this is my output
root@spud:~# lspci | grep Ath
09:04.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
root@spud:~# dmesg | grep ath_hal
[   32.436976] ath_hal: module license 'Proprietary' taints kernel.
[   32.439569] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)

---

### Post by pkpkpkpk on 2008-01-27
I don't have a solution yet but others have this problem as well and I plan to monitor these threads

[http://forums.suselinuxsupport.de/index.php?showtopic=64261&pid=261067&st=0&#entry261067](http://forums.suselinuxsupport.de/index.php?showtopic=64261&pid=261067&st=0&#entry261067)

---

### Post by Stoneface on 2008-07-15
@PKPKPKPK I have exactly the same problem now as well. I have been struggling with my Atheros wireless card for some time now. I have the card running, but somehow the functioning seems to be limited because it is propriety software. Maybe it has something to do with the fact that I removed restricted modules in Synaptic Package Manager to get madwifi to work. It worked only until the next restart :-(

---

