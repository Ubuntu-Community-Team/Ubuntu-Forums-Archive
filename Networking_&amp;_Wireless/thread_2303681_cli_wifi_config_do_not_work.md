---
title: "cli wifi config do not work"
date: 2015-11-20
forum: Networking &amp; Wireless
---

### Post by kapetr on 2015-11-20
Hello I have problem.

If wifi connection to AP (without encryption) is done wit NM, then it works perfectly:
```

root@Dell:~# nmcli con up id gogo
root@Dell:~# iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"VM_DRUHLICE"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:86:E5:09:BD   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry limit:16   RTS thr:off   Fragment thr=512 B   
          Encryption key:off
          Power Management:on
          Link Quality=21/70  Signal level=-89 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11   Missed beacon:0


```


But if I shut-down NM and try to bring up the same wifi connection manually, It fails - I get no association :-(
I had read many sites about manual wifi config, but with no success.

```

root@Dell:~# nmcli con down id gogo
root@Dell:~# service network-manager stop
network-manager stop/waiting

root@Dell:~# iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
root@Dell:~# ifconfig wlan0 up

root@Dell:~# iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
root@Dell:~# iwconfig wlan0 essid VM_DRUHLICE

root@Dell:~# iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"VM_DRUHLICE"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
root@Dell:~# iwconfig wlan0 mode Managed essid VM_DRUHLICE ap 00:25:86:E5:09:BD

root@Dell:~# iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"VM_DRUHLICE"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
root@Dell:~# ifconfig wlan0 up

root@Dell:~# iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"VM_DRUHLICE"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
root@Dell:~# ifconfig wlan0 172.27.29.15/24

root@Dell:~# iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"VM_DRUHLICE"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
root@Dell:~# ifconfig wlan0 up
root@Dell:~# iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"VM_DRUHLICE"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
root@Dell:~# iwconfig wlan0 frag 512
root@Dell:~# iwconfig wlan0 retry 16
root@Dell:~# iwconfig wlan0 retry lifetime 300m
Error for wireless request "Set Retry Limit" (8B28) :
    SET failed on device wlan0 ; Invalid argument.

root@Dell:~# iwconfig wlan0 essid VM_DRUHLICE channel 6 ap 00:25:86:E5:09:BD

root@Dell:~# iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"VM_DRUHLICE"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry limit:16   RTS thr:off   Fragment thr=512 B   
          Encryption key:off
          Power Management:on
        

```

I tried add all possible combinations of options. (commit is not supported)

I'm on end ... 
Why association with NM works and manually not ?

Maybe would help to know, what sequence of commands calls NM to configure wlan iface. But I do not know how.

---

### Post by kapetr on 2015-11-20
I have found the reason:

[COLOR="#FF0000"][SIZE=4]
It is not enough to stop NM.

It is necessary to kill **wpa_supplicant** too !
[/SIZE][/COLOR]

I did try to run **airmon-ng start wlan0** and it reported that there is wpa_supplicant which _could cause problems_ (for monitoring).
I tried to kill it hoping it could maybe help by my problem too.
And it did :-)

I had read +- 15 sites about wifi config over cli.
On every was told to stop/remove NM.
But on **no one** was told that it is necessary to kill wpa_supplicant too.

I hope someone with same problem will find this post to not get almost crazy like me :-D

P.S.:

I have test this script. If NM &  wpa_supplicant are running and I call the script - I get working manual config. If I comment out the "killall wpa_supplicant" line, it works not!
```

#!/bin/bash

set -x

service network-manager stop
killall wpa_supplicant
#iwconfig wlan0
#ifconfig wlan0
ifconfig wlan0 down
ifconfig wlan0 up
iwlist wlan0 scan
iwconfig wlan0
iwconfig wlan0 essid "VM_DRUHLICE"
sleep 3
iwconfig wlan0
ifconfig wlan0 172.27.24.10/24
ip route add to default via 172.27.24.1
ping -c 3 www.centrum.cz

```

---

