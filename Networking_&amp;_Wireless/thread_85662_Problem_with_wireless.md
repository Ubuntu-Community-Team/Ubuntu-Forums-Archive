---
title: "Problem with wireless"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by Juanan on 2005-11-03
I Had installed a LINKSYS WMP54G card It doesn´t work

When I do a iwconfig

wlan0 IEEE 802.11g ESSID:off/any
Mode:Managed Frequency:2.437 GHz Access Point: 00:00:00:00:00:00
Bit Rate:54 Mb/s Tx-Power:16 dBm
RTS thr:2347 B Fragment thr:2346 B
Encryption key:off
Power Management:off
Link Quality:100/100 Signal level:-10 dBm Noise level:-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

And If I write 
iwlist wlan0 scan

wlan0 No scan results

I read in other post that I have to change the RadioState| form 1 to 0 in 
14E4:4320.conf and to Unload the ndiswrapper module ('sudo rmmod ndiswrapper') and then reload it ('sudo modprobe ndiswrapper'). 

But I have done all of that and It doesn´t work. I have a Static Ip which I configure. Can anyone help me?? Thanks

---

### Post by Juanan on 2005-11-03
At the end I have done it. Now the network works

---

### Post by pr0x on 2005-11-10
can you please explain how u managed to fix  this i have a very similar problem

---

