---
title: "Can ping google OK, but cant load any pages"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by desertphotog on 2008-01-12
I can PING Google from Firefox but cannot get to any web pages.  This happened after I tried to reassign the order of preference to the WiFi.  How do I assign the default router?!!  I have no problem surfing on my neighbors across the street but I can't make my laptop connect to the one right next to me!  PLEASE help.   Dell 9200, ProIintel wireless card, Ubuntu 7.10   Have the same exact problem on my desktop using a linksys  WUSB54 card.

---

### Post by MobiusNZ on 2008-01-12
Can you please post the output you get when you run 'ifconfig' in the terminal?

---

### Post by desertphotog on 2008-01-12
karl@karl-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:62:BD:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:B3:80:92  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:feb3:8092/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1195838 (1.1 MB)  TX bytes:270218 (263.8 KB)
          Interrupt:7 Base address:0x4000 Memory:faffc000-faffcfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

karl@karl-laptop:~$

---

### Post by spade=I3= on 2008-06-12
Not sure if you have repaired your problem yet but, I had a similar problem that I worked on for 2 days. I download files off the internet like crazy and suddenly I couldn't get past my google homepage. I could look at all the pages in google likeimages, video, mail... but could not search or login to anything. AVG virus scan picks up nothing, Uniblue scans pick up nothing. So... I went to start/run/type msconfig. I looked in my startup items which I normally keep completely clear because of gaming and I found a file that was odd. The file on startup was mclwddjh.dll. This is an odd filename because it should not exist and especially in a startup location. I did a web search for this file and found nothing. Not even in the uniblue .dll file extensions search. So... I knew it shouldn't exist. I couldn't delete the file because it was in use and everytime I tried disabling it on startup, it would turn back on. So... I went into C:windows/system32/ and found the mclwddjh.dll and renamed it with some numbers before and after like 0000mclwddjh1234.dll just to confuse the program. Restarted my computer and got a error that mclwddjh.dll could not be found. YAY! I was then able to remove the file from startup under msconfig and delete the file completely. The internet works perfectly now and no other issues are to be found. 

So, if you see any odd named files in msconfig startup and they wont disable because all should... then follow my steps of searching for the extension to see if its good or bad, or exists at all. Then rename, restart, and delete that poop. Hope this helps you.

---

### Post by MobiusNZ on 2008-06-13
> **spade=I3= said:**
> Not sure if you have repaired your problem yet but, I had a similar problem that I worked on for 2 days. I download files off the internet like crazy and suddenly I couldn't get past my google homepage. I could look at all the pages in google likeimages, video, mail... but could not search or login to anything. AVG virus scan picks up nothing, Uniblue scans pick up nothing. So... I went to start/run/type msconfig. I looked in my startup items which I normally keep completely clear because of gaming and I found a file that was odd. The file on startup was mclwddjh.dll. This is an odd filename because it should not exist and especially in a startup location. I did a web search for this file and found nothing. Not even in the uniblue .dll file extensions search. So... I knew it shouldn't exist. I couldn't delete the file because it was in use and everytime I tried disabling it on startup, it would turn back on. So... I went into C:windows/system32/ and found the mclwddjh.dll and renamed it with some numbers before and after like 0000mclwddjh1234.dll just to confuse the program. Restarted my computer and got a error that mclwddjh.dll could not be found. YAY! I was then able to remove the file from startup under msconfig and delete the file completely. The internet works perfectly now and no other issues are to be found. 

So, if you see any odd named files in msconfig startup and they wont disable because all should... then follow my steps of searching for the extension to see if its good or bad, or exists at all. Then rename, restart, and delete that poop. Hope this helps you.

Yes, if you use windows this can be a problem, but I haven't come across too much spyware in linux that does this sort of thing...

---

