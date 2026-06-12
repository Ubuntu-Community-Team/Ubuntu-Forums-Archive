---
title: "Scan and Connect Commands"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by ChrisSmith on 2006-08-30
Hello I tried using some commands I found in this forum to scan for wireless networks. It seemed to find the network (WIRENET01) but then when I tried to use the command to connect to the network it failed. Does anyone have any advice?

```
ubuntu@ubuntu:~$ iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:0F:B5:C0:10:5A
                    ESSID:"WIRENET01"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/94  Signal level=-57 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f20 2
          Cell 02 - Address: 00:0F:B5:C0:10:5A
                    ESSID:"WIRENET01"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/94  Signal level=-56 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f20 2

ubuntu@ubuntu:~$ iwconfig ath0 essid "WIRENET01" key ************
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; Operation not permitted.
ubuntu@ubuntu:~$

```

Please please please help I need to get the internet working on ubuntu.

chris xxxxxxxx

---

### Post by NetworkGuy on 2006-08-30
Hmmm,

Why does your ATH0 card see the same access point twice?

What type of WiFi card are you using?

---

### Post by ChrisSmith on 2006-08-30
no idea mate, first time I scaned tho it showed the access point once but the ESSID was blank which was even stranger.

Any ideas what Im doing wrong with the iwconfig command?

thanks for replying.

---

### Post by insyzygy on 2006-08-30
To actually alter network configuration (setting the SSID) you need to be root. Use sudo 

```
sudo iwconfig <whatever> 
```

---

### Post by ChrisSmith on 2006-08-31
how can you set the key because I used
```
sudo iwconfig key "mypassword"
```
and it says that its an invalid argument.

I'm using a netgear WG311T by the way. Which is said to work with fresh ubuntu :sad:

---

### Post by insyzygy on 2006-08-31
You have to specify which device you want to set the key on, e.g. 

```
 sudo iwconfig ath0 key <key> 
```

where you should replace ath0 by eth1 or wlan0 or whatever your wifi card is.

---

