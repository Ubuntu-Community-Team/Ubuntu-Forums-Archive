---
title: "Ubuntu Wireless much slower than on Windows"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by billpaetzke on 2008-04-30
I just wiped out my Windows computer and installed Ubuntu 8.04.  My wireless internet technically works right out of the box, but it seems much slower than my old Windows setup.  I can't quantify the difference because Windows is erased from my machine now; however I am able to compare wired internet speed vs. wireless internet speed.  

On speakeasy.com's speedtest:
Wired connection stats:
Download Speed: 5850 kbps (731.3 KB/sec transfer rate)
Upload Speed: 491 kbps (61.4 KB/sec transfer rate)

Wireless connection stats:
Download Speed: 232 kbps (29 KB/sec transfer rate)
Upload Speed: 69 kbps (8.6 KB/sec transfer rate)

My wired internet is 25x faster? What the heck. How can I improve my unacceptably slow wireless speed?

My wireless card is Linksys WMP54G for the desktop computer.  

Here is my iwconfig output:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"GAW"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: ##:##:##:##:##:##   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=46/100  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Any help is appreciated. Thank you.

---

### Post by corneel on 2008-04-30
> **billpaetzke said:**
> 

My wireless card is Linksys WMP54G for the desktop computer.  



There is a bug in Ubuntu. I have the same wireless card and only on (K)Ubuntu it won't work anymory properly.

---

### Post by billpaetzke on 2008-04-30
I found a temporary solution.  Every time you start your computer, open the terminal and enter this command:  sudo iwconfig wlan0 rate 54M

It will boost you from 1MB/s to 54MB/s; I'm web surfing way faster than on Windows now.  However, it is annoying to open the terminal every time you start the computer. Hopefully someone will release a bug fix and notify us?

---

