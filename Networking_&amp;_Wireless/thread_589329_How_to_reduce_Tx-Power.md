---
title: "How to reduce Tx-Power?"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by kyaw swar on 2007-10-24
manet@manet-laptop2:~$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"manet"
          Mode:Ad-Hoc  Frequency:2.432 GHz  Cell: 02:0F:B5:94:38:98
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=12/94  Signal level=-83 dBm  Noise level=-95 dBm
          Rx invalid nwid:38517  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1748  Invalid misc:1748   Missed beacon:0

.... Please guide me how do i reduce my Tx-Power from 18dbm to Minimum.

Regards.

---

### Post by WedgeHG on 2007-10-24
From the man page for iwconfig:
>  txpower
              For cards supporting multiple transmit powers, sets the transmit power in dBm. If W is the power  in  Watt,
              the  power  in  dBm  is P = 30 + 10.log(W).  If the value is postfixed by mW, it will be automatically con&#8208;
              verted to dBm.
              In addition, on and off enable and disable the radio, and auto and fixed enable and disable  power  control
              (if those features are available).
              Examples :
                   iwconfig eth0 txpower 15
                   iwconfig eth0 txpower 30mW
                   iwconfig eth0 txpower auto
                   iwconfig eth0 txpower off


So in your case you are going to want to say 

```
sudo iwconfig ath0 txpower  <your power setting (something lower than your current 18 dBm)>
```

---

### Post by kyaw swar on 2007-10-24
Yeah.. It goes down as i set
sudo iwconfig ath0 txpower 8B26 and
my Tx-Power becomes 10dBm. But actually i wanna communicate my laptops in a short distance(eg. in a lab). And i gotta use MANET. So how much dBm i shall set?

And beside, i am in lost how to link my PCs in MANET. I mean which command to use or how to..?
I can ping my PCs. I've some soft code called "fsrd" and i got run those in GCC and Make, Make Install. But then don't know what to proceed.

---

