---
title: "Wireless &amp; Atheros5005G"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by kostas_thess on 2007-05-26
Hello :) I Have A Laptop With The Atheros5005G But I cant Activated ! At the windows xp its opens the led left down at the keyboard now its not open :///// My laptop is Fujitsu - Simens - Amilo 1650G :// Any One Knows How To Make It Work ??????????

---

### Post by kostas_thess on 2007-05-26
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```lo        no wireless extensions.

it see it work at the terminal but the power managment above says off :(:(:(:(:(:(

what happens?

---

### Post by kostas_thess on 2007-05-26
hacker@hacker-laptop:~$ iwconfig ath0 power on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device ath0 ; Operation not permit

---

### Post by bren on 2007-06-10
hi kostas

it can be done!

see here [http://ubuntuforums.org/showthread.php?t=224349&highlight=amilo](http://ubuntuforums.org/showthread.php?t=224349&highlight=amilo)

bren

---

