---
title: "WiFi will not connect"
date: 2021-05-20
forum: Networking &amp; Wireless
---

### Post by dddman on 2021-05-20
I have a Toshiba Satellite that's running ubuntu 20.04 from a usb stick quite nicely, but will not connect to the wifi.  I went to the trouble shooting guide and found its a realtek rtl8188ee wireless.  If I read the below outputs correctly then everything is fine.  Yet no connection.

lshw -C network
driver=rtl8188ee  version=5.8.0-43-generic

lsmod
rtlwifi_rtl_pci,rtl8188ee,rtlwifi
cfg80211_rtlwifi,mac80211

sudo iwconfig
wlp2s0_ieee 802.11

iwlist scan not supported


The rest of the story is windows will not boot, my neighbor from down the street has had it setting in the closet.  Its not a bad setup; dual core i3 and 6G of ram.  Its daughter's old laptop.  I want to wipe windows and install ubuntu, but not without wifi.  Ubuntu runs quite nicely on this rig.  

The trouble shooter I used
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by dddman on 2021-05-20
I just noticed it says signal strength is weak.  The wifi is two feet away.

Edit
My wifi source is my phone setup as a hot spot.  So I set my phone next to it and I now have wifi.  It will not work two feet away and even next to it, still says weak signal.

Edit
It's got a 9 inch range.

---

### Post by chili555 on 2021-05-20
> sudo iwconfig
wlp2s0_ieee 802.11May we see the entire result. I suspect that it contains a few clues.

---

### Post by mikewhatever on 2021-05-20
Do you know the correct password? Make sure CAPS LOCK is off. 
I'd also be careful about replacing Windows without permission. The learning curve is usually too steep.

---

### Post by dddman on 2021-05-20
Thanks!

sudo iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:"DuraForce_5895"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: C4:21:C8:73:01:A0   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=26/70  Signal level=-84 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

And yes, it logged into my wifi with password.

I'm on the toshiba now

---

### Post by dddman on 2021-05-20
And when I set the phone two feet away

sudo iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off

---

### Post by chili555 on 2021-05-20
Nothing evidently wrong and therefore fixable so far. Does it scan and see networks?

```
sudo iwlist scan
```

Does it ping?

```
ping -c3 8.8.8.8
```

Finally:

```
ls -al /etc/resolv.conf
```

---

### Post by dddman on 2021-05-20
sudo iwlist scan
lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

wlp2s0    Scan completed :
          Cell 01 - Address: 24:7F:20:CA:8B:E6
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"MySpectrumWiFie0-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002c1dc29fab2
                    Extra: Last beacon: 368ms ago
                    IE: Unknown: 00134D79537065637472756D5769466965302D3247
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 7F0800000F0000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: C4:21:C8:73:01:A0
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
===========================================
ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=112 time=215 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=112 time=109 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=112 time=109 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 108.812/144.308/214.777/49.829 ms
ubuntu@ubuntu:~$ 
===================================================
ls -al /etc/resolv.conf
lrwxrwxrwx 1 root root 39 Feb  9 18:47 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf

---

### Post by dddman on 2021-05-20
This ticket shall remain open, but It's about to get a fresh install of Ubuntu.  I should be able to update it.  Maybe it will help?

So I'll be back folks.

---

### Post by dddman on 2021-05-20
I'm now up on a fresh and updated install of ubuntu and no change.  If my phone is not kept next to the laptop the connection is lost.  Antenna connector gone bad/lose?  I'll take it back t the neighbors and see if it works any better on a real router.

---

### Post by chili555 on 2021-05-20
> Antenna connector gone bad/lose?That's my very strong suspicion.

It's generally not hard to check on a laptop. Many have a little door held down by one captive screw that opens to reveal the wireless card.

Here is a recent post that may be helpful: [https://askubuntu.com/questions/1338052/yet-another-laptop-wifi-problem-script-log-included/1338066#1338066](https://askubuntu.com/questions/1338052/yet-another-laptop-wifi-problem-script-log-included/1338066#1338066)

---

### Post by dddman on 2021-05-21
I watched a video on removing the wifi card.  It requires removing the bottom case that is held in place with several screws.  Think I will first try it on their router just to make sure its not a quirk with my phone.

Later this day...
Well the range increase to 10/12 feet when exposed to a router, still not good enough, but mom came up with her own solution.  The Toshiba has been planted on mom's desk that is close to the modem; a cable was ran and ethernet is now in use.  Mom now has her own desktop computer and whats the first thing she tries?  Facebook of course :)

Thanks for the assist guys

---

