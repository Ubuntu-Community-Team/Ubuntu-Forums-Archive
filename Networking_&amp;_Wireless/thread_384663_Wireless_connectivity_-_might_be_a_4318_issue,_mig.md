---
title: "Wireless connectivity - might be a 4318 issue, might not"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by HumbleGod on 2007-03-14
I'm a fairly new Ubuntu user with a desktop computer with wireless access only--no wired access available in my part of the house, so I won't have connectivity until the wireless card is properly configured. Unfortunately, I'm cursed with a Linksys WMP54GS with the infamous Broadcom 4318 controller. I've been following two guides for getting this to work, [_here_]("http://www.ubuntuforums.org/showthread.php?t=197102") and subsequently [_here_]("http://ubuntuforums.org/showpost.php?p=1189681&postcount=105"); these two have got me closer than other guides. 

However, I'm still not connecting, and the light on my card still isn't coming on. So I'm starting to think that the card now has the right drivers, but the network needs better configuring. Though I could be wrong.

On step 18 in the latter guide (typing [FONT="Courier New"]iwconfig[/FONT] to see if everything was configured properly), I get this:
```
root@brad-ubuntu:/home/brad/Desktop# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:[FONT="System"]XXXX-XXXX-XX[/FONT]   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

So iwconfig is saying Link Quality is 0, which is absurd since I'm linked up to the network now on the Windows boot. But when I type [FONT="Courier New"]iwlist eth1 scanning[/FONT] I get this:
```
root@brad-ubuntu:/home/brad/Desktop# iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:C0:49:CC:B1:40
                    ESSID:"Ringo"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-69 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:14:6C:9C:7C:F6
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-91 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:0F:B3:8C:49:6D
                    ESSID:"grouse"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:0/100  Signal level:-84 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  

```
The network I'm trying to connect to ("Ringo") is listed, as are other networks that my card normally recognizes when I'm connecting through XP. This is why I think the driver is at least partially working and that this might be a configuration issue. On the other hand, the quality for all is still listed as 0/100.

Under Networking, I have my 10-digit WEP key entered. Would changing something else in the network properties possibly yield better results? Or do I still need to mess with the drivers some more?

Thanks!

---

### Post by HumbleGod on 2007-03-15
Bump

Could someone please provide some advice? This has me completely baffled....

---

### Post by alexorcas on 2007-03-22
I have a similar problem, I just reinstalled, I had the 64 bit version and I switched to the 32 bit because my wireless card wouldn't even show up in the 64 bit version. 

I can't find a solution either

---

### Post by HumbleGod on 2007-03-22
After a fresh install, I got my card to work using the method I describe [here]("http://ubuntuforums.org/showthread.php?t=381594") - see post #8. Maybe that'll work for you....

---

