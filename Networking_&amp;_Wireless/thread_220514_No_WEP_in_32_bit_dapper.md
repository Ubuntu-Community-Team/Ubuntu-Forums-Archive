---
title: "No WEP in 32 bit dapper"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by electrocutioner on 2006-07-21
I've been experimenting with 6.06 lately on my compaq presario R4225ca laptop-originally had the 64bit AMD version running,and managed to get the wireless running with wep encription fairly quickly.
 I decided to install 32 bit because there were so many problems with 64 bit drivers/programs not ready for prime time (yet).
 Surprisingly,I have been having a tougher time getting the 32 bit driver for my broadcom wireless adapter than I did for the 64 bit.I messed around with a couple different scripts,installed manager and finally wifi radar.Figured I was going to need a fresh install and try it again,when wifi radar started to detect my network.
 However,It will not retrieve an ip address under wep encription.If I remove any encription from the router,it works fine.
 I have been reading all kinds of posts,but nothing seems to help.I even installed wpa_supplicant thinking I should try it,but can find no interface,don't know the commands,am unfamiliar with this encription,and wonder if it will be way more complicated than getting wep going.
 Any suggestions?

---

### Post by tturrisi on 2006-07-21
Try setting the wep key as such:  (w/ a hyphen after every 4 chars)
abcd-efgh-ij

---

### Post by electrocutioner on 2006-07-21
no go,thanks tho-
I tried the hyphens in etc/networks/interfaces and in network config.
 this is what i get from % iwconfig

eth0      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and from :~$ iwlist eth0 scan
eth0      Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    ESSID:"xxxxxxxxx"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:0/100  Signal level:-75 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

here is my interfaces script

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
wireless-essid xxxxxxxxx
wireless-key xxxxxxxxxx

---

