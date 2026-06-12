---
title: "Broadcom 4306 Feisty AMD 64bit install question"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by Snyper64 on 2007-04-30
Has anybody got their bcm4306(I think mines rev3) internal card to work on the 64bit version of Ubuntu? I have tried to follow [THIS]("http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm4306") guide(I'm guessing this just installs the firmware for the 43xx driver?) and have gotten the card to sort of work, and when i say sort of the only thing that seems to work is the little blue light on the wireless button. Though once the light come on it doesn't seem to want to turn off no matter how many times I push it. Anyways heres my iwconfig output:```
snyper64@ubuntuSnyper64:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
I remember on Edgy eth0 was my wired NIC and eth1 was my wireless(that I never could get to work on Edgy). So any ideas or a how to from someone on how to get this card to work or should I just spend the money and buy myself a D-Link PCMCIA wireless card?

Thanks

---

