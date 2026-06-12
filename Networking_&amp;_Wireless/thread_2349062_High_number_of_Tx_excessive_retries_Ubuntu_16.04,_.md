---
title: "High number of Tx excessive retries: Ubuntu 16.04,  tl-wn722n"
date: 2017-01-10
forum: Networking &amp; Wireless
---

### Post by begthehessian on 2017-01-10
I'm new to Ubuntu and, stupidly, at[ATTACH]273130[/ATTACH][ATTACH]273131[/ATTACH] one point I deleted Network-Manager, and everything has been a mess since.  Can someone help me reconfigure correctly?  

My network will work for a few minutes, but will quickly deteriorate, with Tx excessive retries in the dozens to a hundred per web page load, and sometimes it will not load at all.  It makes my connection unstable and often I can't connect or apt-get update at all.   


iwconfig...
```
wlan0     IEEE 802.11  ESSID:"MangoRot"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: F4:F2:6D:9C:7C:2C   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:546  Invalid misc:22   Missed beacon:0
```

And I have attached my wireless-info.txt
lo        no wireless extensions.

I saw a similar thread posted a few years ago ([https://ubuntuforums.org/showthread.php?t=1996768](https://ubuntuforums.org/showthread.php?t=1996768)) but disabling wireless_n just seemed to muck everything up further.

---

### Post by begthehessian on 2017-01-10
So much for the attached wireless info.  Here it is..

---

### Post by begthehessian on 2017-01-12
Still no luck here.  I'm back to wired internet, works without a hitch.  Wireless still hates me.  If anyone else has a similar problem, please pipe up.  
I am on Ubuntu 16.04 
Kernel 4.8.3-040803-generic
ath9k chipset,

---

### Post by jeremy31 on 2017-01-12
Do you have static IP's and DNS set up?  In your Network Manager settings for the wireless connections I see
```
[ipv4] method=manual
[ipv6] method=auto
```

My IPv4 is usually auto and I disable IPv6

I have the same USB dongle that I have only for a backup for my Lenovo and it has worked great.  I have included a pic of my IPv4 settings
[ATTACH=CONFIG]273165[/ATTACH]

---

