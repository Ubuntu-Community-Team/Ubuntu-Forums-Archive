---
title: "Nouveau error message and internet connection"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by joga24 on 2011-05-08
The first problem has been bugging me for quite a while, but it doesn't seem to be anything too sinister. Whenever I hibernate, restart, or shut down, I see the following error message, usually repeated many consecutive times: 
 
```
 
 [(number.othernumber)] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table 
 
```Tried to solve it myself, but came up short. Any help is appreciated. 
 
 
 
The next problem is a little more bothersome. There seems to be something funny about my internet connection. Right now I am connected to a wireless network, and typically I work in rooms where the signal is somewhat weak. I thought this explained why I usually get download speeds of ~300kB/s.  I was working in Windows 7 recently, and there I was downloading at a speed over 1.5 megs per second. I found that discrepancy somewhat strange, 

Additionally, when I tried to update to 11.04, I received the following error message:

```
W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```Ubuntu also suggested that I may not have an internet connection at all. Curious, I performed system testing through System>Administration>System Testing. The tests there also indicated that I had no internet connection. 

Can anyone tell me what is going on with my internet connection? Again, any and all help is appreciated.

---

### Post by joga24 on 2011-05-10
^

---

### Post by wildmanne39 on 2011-05-11
> **joga24 said:**
> ^

Hi, I am not sure about the first problem but 300/kbs is about the same as what windows is recording as 1.5 megs a second just different way of looking at it.:)

---

### Post by grahammechanical on 2011-05-11
There are several things that will affect a download speed. Interference is one. Other computers accessing the same wireless router using the same wireless channel (frequency) will affect the speed of the connection. 

If data has to be re-sent because the data packet was not transmitted accurately then it will take longer for the download to complete and the average speed will show a lower figure.

The server sending the data could be running slow due to a lot of connections. A couple of weeks ago I tried to download the 11.04 CD iso. It was about 700MB in size and was going to take 5 hours or more. I was able to download the 11.04 DVD iso of some 4GB in just under 90 minutes. And this was using a wired connection and nothing to do with my computer or router/modem.

Regards.

---

