---
title: "I can see available SSID's in Network Manager but internet does not work."
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by riverkarl on 2008-09-20
I recently built a computer in which I used a TP-link Wireless-N card (TL-WN951N) to provide my computer with a wireless internet connection. Unfortunately, Ubuntu (Hardy) did not see it right away, so I installed ndiswrapper to implement the Windows XP drivers for my card off the cd. This seemed to do the trick...somewhat. I can open up network manager now and see an option for a wireless network connection, unlike before, and I can even see the available SSID's in my area. But when I try to connect to an SSID I am unable to get onto the internet. 

Another thing to note is that the lights for my card only came on after the modprobe command. However, they blink in an unrandom periodic fashion. (Blink, 1 second passes, Blink, 1 second passes, Blink....)

I have tried Madwifi using several different versions of the software, (seeing as this card uses an Atheros AR5416 chip), but I have been unsuccessful. 

I feel like I am so close, but what should I try next?

---

### Post by agentbuzz on 2008-10-04
Dear riverkarl:
I had a somewhat similar problem. I installed Hardy Heron on an AMD64 platform: 
agentbuzz@mudskipper:~$ cat /proc/cpuinfo | grep model.name
model name	: AMD Phenom(tm) 9850 Quad-Core Processor

I had installed a D-Link DWA-552, which is also based on the Atheros ar5416 chipset, as is your TPLink card.

agentbuzz@mudskipper:~$ sudo lshw -C network | grep 802.11
[sudo] password for agentbuzz: 
       product: AR5416 802.11abgn Wireless PCI Adapter
       configuration: broadcast=yes driver=ath9k ip=192.168.1.67 latency=168 module=ath9k multicast=yes wireless=IEEE 802.11bgn

I built a kernel >2.6.27-rc3, because I read that Linus included support for that Atheros chipset in RC3.
agentbuzz@mudskipper:~$ uname -r
2.6.27-rc6

Both mac80211 and ath9k were built as modules.
agentbuzz@mudskipper:~$ lsmod | grep ath9
ath9k                 284984  0 
mac80211              200424  1 ath9k

I, too, could see the AP in a scan.

agentbuzz@mudskipper:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :          
          Cell 02 - Address: 00:00:00:00:00:00
                    ESSID:"2WIRE411"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/100  Signal level:-66 dBm  Noise level=-95 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000cb574aa857
                    Extra: Last beacon: 80ms ago

YET, I could not associate with this AP! It was a 2Wire Gateway, model 3800-HGV-B. It is WPA-capable, but I couldn't associate with it with WEP, WPA1, or WPA2.

On a lark, I hung a Netgear WPN824 off the 2Wire, installed wicd, and configured wireless using wicd instead of System>Administration>Network. I am writing to you using the wireless connection.

If you've come to the end of your rope with your ar5416-based card, try a different AP. That's what worked for me.

---

