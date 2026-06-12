---
title: "RTL8187 Wireless - No Connect"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by harusp3x on 2007-01-07
I tried native drivers, but I couldn't connect. Then I tried ndiswrapper drivers, but there was no detection. So I moved back to native drivers.

I am currently running the driver that came default with ubuntu 6.10. It seems to be picking up a signal, but not using it. Here are various command results.

*iwconfig*
```
wlan0     802.11b/g link..  ESSID:"InterScube"  
          Mode:Managed  Channel=11  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


*ifconfig*
```
wlan0     Link encap:Ethernet  HWaddr 00:15:AF:05:9F:6A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10791 (10.5 KiB)  TX bytes:0 (0.0 b)
```



*iwlist scan*
```
wlan0     Scan completed :
          Cell 01 - Address: <CORRECT WIRELESS MAC ADDRESS>
                    ESSID:"InterScube"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:15  Signal level:0  Noise level:11
                    Extra: Last beacon: 3ms ago
```


*sudo lshw*
```
wlan0     Link encap:Ethernet  HWaddr 00:15:AF:05:9F:6A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10791 (10.5 KiB)  TX bytes:0 (0.0 b)

```


It found the right channel and AP mac address. (I had given it manually in the past, but I have since reformatted. So it must be detecting the router.)

I have been working on this for 5 days and I am on my last leg here. Any solutions/suggestions?

Thank you very much.

---

### Post by n00b@linux on 2007-01-07
> wlan0     802.11b/g link..  ESSID:"InterScube"  
          Mode:Managed  Channel=11  [COLOR=Red]Access Point: Not-Associated[/COLOR]   
          Bit Rate=11 Mb/s   
          Retry:0n   Fragment thr:0ff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0You need to configure your wlan0 interface:```
sudo iwconfig wlan0 mode managed essid InterScube
```Then restart networking:```
sudo /etc/init.d/networking restart
```Also, I'm not sure about> wlan0     Scan completed:
          Cell 01 - Address: <CORRECT WIRELESS MAC ADDRESS>
                    ESSID:"InterScube"
                    Protocol:IEEE 802.11g
                    [COLOR=Red]Mode:Master[/COLOR]
                    Channel:11
                    Encryption key:0ff
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:15  Signal level:0  Noise level:11
                    Extra: Last beacon: 3ms agoI've never seen that before.  Have you got your access point set up correctly?

---

### Post by harusp3x on 2007-01-07
After I restarted networking, it started its DHCP discovery process and gives me what it always gives me when I run dhclient.

```
Listening on LPF/wlan0/00:15:af:05:9f:6a
Sending on   LPF/wlan0/00:15:af:05:9f:6a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by phossal on 2007-01-07
What kind of wireless dongle do you have?

---

### Post by harusp3x on 2007-01-07
It is the Asus WiFi-AP Solo that came integrated with my P5W DH Deluxe mobo. It has the Realtek R8187 chipset in it.

---

### Post by n00b@linux on 2007-01-08
To eliminate the possibility of a weak radio signal being the cause, I suggest you physically move your PC or access point so that they are next to each other and keep it there until your problem is solved.  I wasted approx. 2hrs figuring this out when I had problems with setting up WPA.

---

### Post by naht on 2007-01-14
Try a newer version of ndiswrapper (i use 1.33) with older(!!!) win98 drivers. The most recent drivers from realteks page didn't work for me, the ones shipped with the board (driver cd) work like a charm. Took me weeks to find out. =)

---

