---
title: "RT61 Dropping Connection"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by thebucksstop on 2007-11-11
I'm one of the lucky ones - my RT61 wireless card works out of the box, it's what I'm using to post this at the moment.

The trouble is, though, that when I start ramping up the bandwidth (e.g. firing up p2p), the connection  randomly drops out. I can't then reconnect through network-manager.
Output of iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"my network name"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:F0:55:B7:2F   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Anyone able to help me out?

---

### Post by jamestech on 2007-11-11
I think I have the same problem, if you go to the terminal and type 'dmesg' what does it return?

I get the following just before my connection drops...

> [  353.481623] Inbound IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0b:6a:7b:8c:9e:08:00 SRC=192.168.1.134 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=24520 PROTO=UDP SPT=138 DPT=138 LEN=209 
[  591.962637] Inbound IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0b:6a:7b:8c:9e:08:00 SRC=192.168.1.134 DST=192.168.1.255 LEN=238 TOS=0x00 PREC=0x00 TTL=128 ID=27363 PROTO=UDP SPT=138 DPT=138 LEN=218 
[ 1071.120776] Inbound IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0b:6a:7b:8c:9e:08:00 SRC=192.168.1.134 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=37712 PROTO=UDP SPT=138 DPT=138 LEN=209 
[ 1347.644068] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
[ 1347.644071] Please file bug report to [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).


I also get...
> [   90.072257] wlan0: duplicate address detected!

but this is quite some time before the connection drops, I assume this is not related?


The complete dmesg log is here: [http://www.onedump.com/show.php?id=b79ee4314303f23d1e7337641f27a5f5](http://www.onedump.com/show.php?id=b79ee4314303f23d1e7337641f27a5f5)

---

### Post by thebucksstop on 2007-11-11
Hi,

I've not had it yet today, I'll check out the log when it happens again. I think I might've solved it though, by limiting p2p connections to less than 150 globally, and limiting upload to 50kb/s total. I'll report back later on today whether it's still hanging in or not.

---

### Post by thebucksstop on 2007-11-12
Sorry for not posting this earlier yesterday - things got a bit hectic around the house.

Basically, I've not solved it. I thought for a while reducing global connections and upload speed had fixed it - Deluge was happily running for several hours, downloading at about 58-60kb/s average from several torrents. Eventually, though, the connection dropped. As I wasn't around, I don't know when so can't retrieve the log for the relevant time - i've left it running today, so should be able to get something from when it drops this morning!

Anyone else able to help us out with this?

---

### Post by wieman01 on 2007-11-12
You could try 2 things:

1. Change the wireless radio settings (beacon interval) and do a bit of testing. Check out various settings and see if it get any better.

2. Replace the current Ralink driver with "ndiswrapper" (see signature).

---

### Post by thebucksstop on 2007-11-12
wieman01: Thanks for that, I'll check it out when I get home this evening. I'll try faffing around with the beacon interval etc, and see if that works. Failing that, i'll make use of you (apparently) very clear HOWTO for ndiswrapper. 

Cheers for the help - I'll post back the results tomorrow.

---

### Post by supertux on 2007-12-18
Someone with some results here? I have the same issues.

---

### Post by wieman01 on 2007-12-18
Yes, I think "ndiswrapper" has solved the issue for a few users.

---

### Post by thebucksstop on 2007-12-19
I gave up in the end and bought a 30m cable. Definitely not elegant, or subtle, but it does the job. 

Sorry I can't be of more use.

---

