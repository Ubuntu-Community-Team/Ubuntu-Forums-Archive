---
title: "Excitement!! I got it to BLINK! Trendnet tew424 USB net adapter"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by garpt on 2009-01-17
Hi All,
  I've been working on my biggest problem so far since installing ubuntu 8.10. Wireless Internet. I'm on my 3rd adapter- after Belkin, US robotics, now trendnet. Using some helpful post on this forum, I took the drivers off the install CD, and installed the .inf driver with ndiswrapper. That took a couple hours to figure out- (VERY newbie, but great w/ windoze) After MANY false starts, I got it to start blinking upon rebooting. It seems to be a rhythmic blinking, if you know what I mean. Doesn't seem to be blinking in response to data. And i can't "see" it or "find" it in the network manager. I suppose or guess I need to "point" the Network mgr. to add it? Or input some data like Mac or SSD? Anyway, what do I do next? I'm very excited to get this far--I've been working on this for WEEKS! Please advise!!

THANX!!
GARY

---

### Post by handydan918 on 2009-01-17
TRy posting the output of ```
lsmod | grep ndiswrapper
```

and ```
sudo ndiswrapper -l
```

and ```
sudo iwlist scan
```

and ```
sudo iwconfig
```

---

### Post by garpt on 2009-01-17
Hi handydan918
 Some good news, but first I would like you to check the output of what you asked for....I left it for a couple of hours. When I came back, I saw the little signal strength bars on the taskbar. I unplugged my ethernet cable, and it said the wireless network was active! Sure enough, it worked- but was S-L-O-W!!! I clicked the SStrength icon, and found I was on a neighbor's connection! SO, I found mine, (there were four connections listed), and it was better. But I'm STILL only getting about 2000kbs, and on the wired connection, I get 25,000kbs. Thats over 10x faster. And my upload is faster than my download---strange (i think). Perhaps you can help me with tips to tune the speed, or something that's not set right? Anyway, to possibly help you, see below::

garwyn@garwyn-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           196380  0 
usbcore               148848  8 rtl8187,gspca_spca561,gspca_main,ndiswrapper,usbhid,ehci_hcd,ohci_hcd
garwyn@garwyn-laptop:~$ 

ALSO:

garwyn@garwyn-laptop:~$ sudo ndiswrapper -l
[sudo] password for garwyn: 
net8187b : driver installed
	device (0BDA:8189) present (alternate driver: rtl8187)
sis163u : driver installed
garwyn@garwyn-laptop:~$ 

NEXT:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:1F:33:E4:FB:BF
                    ESSID:"garpt"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:21:29:B4:B8:EC
                    ESSID:"SMITH"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:30:BD:C3:DD:2E
                    ESSID:"WLAN"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

FINALLY:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"garpt"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:33:E4:FB:BF   
          Bit Rate=11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Encryption key:4850-9EBB-A316-F0E6-09EC-7282-8253-7DEE   Security mode:restricted
          Power Management:off
          Link Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

garwyn@garwyn-laptop:~$

Anything there that might need to be tuned/ tweaked? I realize this isn't a top of the line adapter, but 802.11 G is 80211.G, right? My previous laptop that "blew up" used the same, and the speed was close to thr wired connection. My wireless router is high quality, a netgear WNR2000, current high-end. Same I used w/ the other, cheap compaq laptop. This is a built like a tank Alienware laptop only 2 years old, using Linux cause my WINDOZ got corrupted, and I wasn't going to pay for a new version! Anything you see above that I can look at? 
Thanx!!
Gary

---

