---
title: "Internet runs very slow"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by socaldrum on 2008-06-19
Hey guys, my internet on my PC running Hardy 8.04 goes extremely slowly. It works, it's just a big pain - I can't watch any videos or download anything just cause it takes so long. I have a wireless USB adapter that works when I plug it in and gets a good connection (it's usually in the 90% range), but still, it goes much too slow. Thanks for your help!

----------------
Now playing: [Love - AndMoreAgain](http://www.foxytunes.com/artist/love/track/andmoreagain)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by lisati on 2008-06-19
A whole bunch of stuff can affect internet speed. Is the slowness of your connection recent or has it been ongoing? Anything changed on your system?

---

### Post by EXCiD3 on 2008-06-19
Upgrade from dialup :lolflag: just kidding...i havent even followed that advice myself. :(

Anyways, has anything changed other than your operating system? Can you give us some more details on your internet connection, network setup, and usb wireless card?

---

### Post by socaldrum on 2008-06-19
The adapter is a Linksys WUSB54GC Compact Wireless-G adapter, and my computer is a Dell Dimension 2400. And no, nothing's changed since I installed Ubuntu, and it worked well before.

---

### Post by N3um0rin on 2008-08-08
I have the same usb adapter as you and just recently after an update for ubuntu..im not even sure which one..but it was right after i updated that it wouldent let me load videos on veoh or download because it kep stalling and i have good connection all the time..its really irritating

---

### Post by EXCiD3 on 2008-08-09
Could be a problem with an updated kernel. Try booting into an older kernel in your grub menu, if this works then thats a temporary fix, you can then setup grub to default boot to that entry and wait for a newer kernel to be released. Hope that helps somewhat!

---

### Post by studlychris on 2008-10-07
I have the exact same problem.  Here are the deets.  I am using a wireless USB Belkin F5D7050. 

Just installed 8.04 and it automatically configured my Wifi and shows me my network.  I am able to connect but the wifi is extremely slow.  If I connect via Eth to my other computer (Windows xp) using it as a tether I get very fast internet. The trouble shooting steps I have completed are disabling ipv6, installing the windows driver with ndiswrapper, and changing my bit rate to 54mpbs with iwconfig.  

I am brand new to Ubuntu/Linux and would really appreciate any help.  

"wlan0     IEEE 802.11g  ESSID:"don't bother it's slow"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:BB:4A:DB   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
"

---

### Post by willca on 2008-10-07
Can you try adding this to your /etc/sysctl.conf.

Before you do so, you might want to backup that file.

sudo cp /etc/sysclt.conf /etc/sysclt.conf.bak

sudo vi /etc/sysctl.conf and append these lines at the end.

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

Save the file and reload sysctl.

sudo sysctl -p

---

