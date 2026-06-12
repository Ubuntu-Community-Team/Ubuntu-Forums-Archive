---
title: "Trouble with Ubuntu 9.04 and Linksys Router"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by ArtOfLife on 2009-09-30
Hello everyone!

I had to replace my wireless router yesterday, I was using an Apple Airport, but it completely died. I now have a Linksys WRT160N V3 and it is giving me some troubles in Ubuntu.

It works fine when I was running Windows 7 last night, but since returning to Ubuntu this morning, it will connect, and the network works a bit, but it's very random. I mean, it will be connected, and allow me to actually access websites, but after about 2 minutes or so, it loses the ability to load anything, though remains connected. About 2 or 3 minutes after that, it is able to load pages again. And at no time will it allow my Ubuntu laptop to connect to settings via 192.168.1.1 . Since it worked perfect with Windows, and works perfect on my Mac, I know it's not the router, because those setups are able to browse just fine. And my Ubuntu setup ran fine with the airport, so I feel fairly sure its nothing to do with my laptop, but maybe a setting somewhere?

I am a bit lost with this, and I appreciate any help, though I ask if you can use non-tech savvy terms, because I am very new to Linux, and am not all too good with network stuff either.

---

### Post by wobin77 on 2009-09-30
How's your signal? Does it remain the same or does the strength drop when it isn't able to connect? 
If so, you could try to install the backports-module. 
Helped me to get a 'signal-boost'

---

### Post by ArtOfLife on 2009-09-30
The signal stays completely full at all times, as I am working right now, the laptop is only on the other side of the room.

---

### Post by wobin77 on 2009-09-30
care to post your iwconfig?

---

### Post by ArtOfLife on 2009-09-30
I assume I was supposed to type that in terminal? If so, here is what it did...

```
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:69:D5:70:6C   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=97/100  Signal level:-74 dBm  Noise level=-117 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

### Post by wobin77 on 2009-09-30
Maybe this can help:
[http://ubuntuforums.org/showthread.php?t=1246140](http://ubuntuforums.org/showthread.php?t=1246140)

---

### Post by ArtOfLife on 2009-09-30
Yeah, I had seen that post earlier, thanks! But sadly it didn't really offer any help. The firmware update talked about there, is not supported on my version of the router =/ I'm searching google thoroughly, as I really don't want to return to Windows just because of this, I actually was wanting to move all my computers to Ubuntu, but if they cannot use the internet reliably, not much point :P

---

### Post by ArtOfLife on 2009-09-30
Just in case anyone else ever has this problem, I'll post how I finally got it solved :) 

I called Linksys support, but of course being this is Linux they had no idea at all. I just did some poking around, and noticed that in the "basic wireless settings" the router was set to "Network mode: Mixed" I set it to Wireless-G only, and now my connection works just fine!

Thanks taking the time to try to help me! I really appreciate it :)

---

