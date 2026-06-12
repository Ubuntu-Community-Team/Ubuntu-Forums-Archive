---
title: "Wireless keeps droping"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by russell5 on 2007-12-08
Ok so my network connection keeps dropping out on me. I am using ndiswrapper with mrc8000c driver. I had it working before then i did a fresh install of gusty and not randomly my connection just drops. I still have a valid ip but cant ping anything. The only way to fix this is reload ndiswrapper module and reconnect. Other pcs on my network work without any issues. I have used versions 1.48 , 1.49 , 1.50 and the svn of ndiswrapper and it happens in all of them.

This is the device i have
00:0b.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

Any suggestions?

---

### Post by coolbrook on 2007-12-08
What do you see in terminal when you type iwconfig

---

### Post by russell5 on 2007-12-08
This is what i see when its dropped

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"heisthenot"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:14:BF:D6:ED:A6   
          Bit Rate=24 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by coolbrook on 2007-12-08
A weak signal.

What do you see when you type

iwlist wlan0 scan

---

### Post by russell5 on 2007-12-08
The odd thing is that this never happened before i did a fresh install of 7.10


wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:D6:ED:A6
                    ESSID:"heisthenot"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by russell5 on 2007-12-08
The signal strength changes alot too i just did another scan and here is what came up

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:D6:ED:A6
                    ESSID:"heisthenot"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by coolbrook on 2007-12-08
That is unusual.  Do you have admin access to change the wireless channel on your router?  Perhaps try a new frequency and see if you get a better signal.  Ensure that nothing is touching your adapter.

---

### Post by russell5 on 2007-12-08
Changed the channel on my router a couple of times and still happens and nothing is in the way of my card.

---

### Post by russell5 on 2007-12-09
I just figured out his only happens when i have azureus open. So i installed ktorrent and it still happens with that. Its odd because i can downoad lage files like the ubuntu iso and it doesn't happen.

---

