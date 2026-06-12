---
title: "Problem with reaver to initialize interface mon0"
date: 2016-02-18
forum: Networking &amp; Wireless
---

### Post by Cayo_Emilio_Montei on 2016-02-18
Hello ubuntu community.
I am trying to recover my wifi password with reaver and getting some trouble. Here is what I did:
I installed reaver and aircrack-ng on ubuntu 14.04.

```
lab221@lab221:~$ sudo apt-get install reaver aircrack-ng 
```

Then I checked my wireless card:
 ```
lab221@lab221:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Lab221"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: C4:6E:1F:5D:A8:06   
          Bit Rate=21.7 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: 0ff   Fragment thr: off
          Power Management: off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:15   Missed beacon:0
```

Then I created the monitor mode:

```
lab221@lab221:~$ sudo airmon-ng start wlan0

Found 6 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!


PID    Name
27269    avahi-daemon
27271    avahi-daemon
27312    NetworkManager
27792    wpa_supplicant
29667    dhclient
29673    dhclient
Process with PID 29673 (dhclient) is running on interface wlan0


Interface    Chipset        Driver


wlan0        Atheros     ath9k - [phy0]
                (monitor mode enabled on mon0)

```
with the following response of iwconfig:

```
lab221@lab221:~$ iwconfig
mon0      IEEE 802.11bgn  Mode:Monitor  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Lab221"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: C4:6E:1F:5D:A8:06   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:20   Missed beacon:0


```


Then I searched for the BSSID with sudo airodump-ng mon0
When i try to use reaver, I get the following:

 ```
lab221@lab221:~$ reaver -i mon0 -b C4:6E:1F:5D:A8:06 -vv


Reaver v1.4 WiFi Protected Setup Attack Tool
Copyright (c) 2011, Tactical Network Solutions, Craig Heffner <cheffner@tacnetsol.com>


[-] Failed to initialize interface 'mon0'
[-] Failed to recover WPA key
[+] Nothing done, nothing to save.


```
What is wrong here? I tried to kill the programs that airmon-ng mentions but they initialyze again. How do I proceed?

Thanks in advance,
 Cayo

---

