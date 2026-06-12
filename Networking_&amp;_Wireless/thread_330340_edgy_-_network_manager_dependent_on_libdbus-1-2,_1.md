---
title: "edgy - network manager dependent on libdbus-1-2, 1-3 no worky"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by oranguman on 2007-01-03
hi!

 i'd been trying to get wireless on my laptop since I decided to try ubuntu edgy  2.6.17-10-generic a week ago. since the program is so community themed and dependent on an internet connection, I hope the powers that be eventually make it a bit more idiot proof; it's hell to find support when I have to restart in windows to get on the internet.. ](*,) 

ok, soapbox aside; here's the situation. I haven't been able to detect or get on any free wifi, but I think my toshiba mini wlan pci card is working.. I tried ndiswrapper with all sorts of drivers before realizing that 

x@laptop:~$ iwconfig

lo        no wireless extensions. (what is this anyway?)

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"default"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


would mean that my card (chipset 01:08.0 0200: 8086:103d  i think) is already detected. I get a networking symbol and signal level from network monitor; both are good at home but I can't resolve any web pages; that's a connection problem. But when i'm at the coffee shop and the connection is ready and able, it won't be sensed. Scanning was no help and actually that's the part that puzzled me: 

x@laptop:~$ iwlist eth1 scanning
eth1      Failed to read scan data : No data available
 

I just found
+_+_+_+_the problem was actually that I had no problem+_+_+_+_+_
that makes me a fool.. but a happy one.. :mrgreen: 
installing Wifi Radar gave me the GUI that I needed to start up my linux experience with a bang diddly bangerangeroo

smash!

---

