---
title: "I sometimes lose connection."
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by giany911 on 2008-02-03
So I have a wireless ad-hoc network set up between my desktop and my laptop. It works alright but I sometimes lose connection on my laptop ( the desktop is set as a router ) and to get the connection back up and running on my laptop I have to restart the desktop. This is a little annoying since the PC's are not in the same room. Is there a way to get the conn. back up without having to physically restart the desktop ?

It's getting only worse ... I lost connection about 5 or 6 times in only a few hours.

---

### Post by giany911 on 2008-02-04
Bump for help :confused:

---

### Post by faulkes on 2008-02-04
It is entirely based upon your setup, the more information you provide, the more we can help.

What type of card are you using? 

```

lspci | grep -i net

```

What driver is it using?

```

lsmod

```

Is there anything in /var/log/messages (secure, dmesg) when it does fail?

Faulkes

---

### Post by giany911 on 2008-02-04
On my laptop I think I'm using ndiswrapper with  net5211 driver. 
lspci:  04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
I get no output on lspci | grep -i net

On my desktop I have a Corega USB - > Wifi adaptor also on ndiswrapper - cgwlusb2 got the driver from the CD supplied.

---

### Post by faulkes on 2008-02-04
I'm not familiar with either adaptor (under ndiswrapper or other driver) so I'm not sure where to start, although I would suggest looking for anything in the network drivers (does an OSS version exist?) which may be causing the issue.

Next to that, I'd post what it looks like when it's working:

```

sudo iwlist ethX scan
-where ethX is your wireless ethernet interface

and 

iwconfig

```

also helpful would be what it looks like in a non-working state.

Faulkes

---

### Post by giany911 on 2008-02-04
```
sudo iwlist wlan0 scan
```
wlan0     Scan completed :
          Cell 01 - Address: DE:62:CD:CE:CB:3E
                    ESSID:"acasa"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Frequency:2.462 GHz (Channel 11)
                    Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```
iwconfig
```
wlan0     IEEE 802.11g  ESSID:"acasa"  
          Mode:Ad-Hoc  Frequency:2.462 GHz  Cell: DE:62:CD:CE:CB:3E   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:85/100  Signal level:-41 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

This is on my laptop. 

I will do it again when it's not working. 
Using ndiswrapper ( with a lot of effort ) was the only way I got my Atheros card working.

---

### Post by faulkes on 2008-02-04
That bitrate of 54Mb/s looks kinda suspicious considering you are connecting to an 11g on the other side - that could be part of the problem you are encountering.

I'll wait for additional info.

---

### Post by giany911 on 2008-02-05
OK so I got some more info
This is what I got when I tried to restart the network on my desktop. 
```
miky@miky-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                           * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
wlanctl-ng: Operation not supported
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.
wlanctl-ng: Operation not supported
Failed to enable the device, exitcode= 1 .
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
``` 
lsusb on my desktop
```
miky@miky-desktop:~$ lsusb
Bus 004 Device 002: ID 07aa:0020 Corega K.K.
``` 

iwconfig also on my desktop
```

wlan0     IEEE 802.11b  ESSID:"acasa"  
          Mode:Ad-Hoc  Frequency:2.462 GHz  Cell: AA:7D:9D:0D:AD:7F   
          Bit Rate=11 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
sudo iwlistconfig wlan0 scan - desktop
```
miky@miky-desktop:~$ sudo iwlist wlan0 scan
[sudo] password for miky:
wlan0     Scan completed :
          Cell 01 - Address: AA:7D:9D:0D:AD:7F
                    ESSID:"acasa"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Frequency:2.462 GHz (Channel 11)
                    Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1

```

I will try Wicd for a while to see if I can reconnect somehow. I see it has an *automatically reconnect on connection loss* feauture.

Same thing, wicd didn't help.

---

### Post by giany911 on 2008-02-09
It's getting really really really really annoying ... Can't fix this someway ?

---

