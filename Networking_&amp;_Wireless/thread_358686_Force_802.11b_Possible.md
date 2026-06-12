---
title: "Force 802.11b? Possible?"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by Buntis on 2007-02-11
Hi. I have a broken D-link dwl G520 card. It disconnects randomly when using 802.11g even though the signalstrenght is about 50%( Tested in both linux and windows). If I set the card to use 802.11b in Windows , it works perfectly.
I have googled around, but cant find how to force the card to use 802.11b in linux. Is it possible at all? Im a little new to linux/Ubuntu so please be simple :P

---

### Post by tturrisi on 2007-02-11
> **Buntis said:**
> Hi. I have a broken D-link dwl G520 card. It disconnects randomly when using 802.11g even though the signalstrenght is about 50%( Tested in both linux and windows). If I set the card to use 802.11b in Windows , it works perfectly.
I have googled around, but cant find how to force the card to use 802.11b in linux. Is it possible at all? Im a little new to linux/Ubuntu so please be simple :P
You can set the wifi ap to use B only.

---

### Post by Buntis on 2007-02-11
> **tturrisi said:**
> You can set the wifi ap to use B only.

Yes, but I have three other computer connected to the same ap and I would like for them to use 802.11g.  :(

---

### Post by tturrisi on 2007-02-11
You could try setting the bit rate to 11 Mb maximum using iwconfig.
$# iwconfig eth0 rate 11M

$# man iwconfig

---

### Post by Buntis on 2007-02-11
root@buntis:~# iwconfig ath0 rate 11M
  root@buntis:~# iwconfig ath0
  ath0      **IEEE 802.11g**  ESSID:"fusa1"  
            Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:5A:8B:CB   
            Bit Rate=11 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
            Retry:off   RTS thr:off   Fragment thr:off
            Encryption key:FFFA-DD67-89   Security mode:restricted
            Power Management:off
            Link Quality=17/94  Signal level=-78 dBm  Noise level=-95 dBm
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Still 802.11g.

---

