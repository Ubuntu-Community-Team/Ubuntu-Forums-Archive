---
title: "Monitoring network traffic per application"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by infinitejones on 2008-05-29
I've got a little applet called Netspeed running on my panel. It's telling me that upload bandwidth is varying between 250-450KB/s, and I don't think I'm uploading anything. I'm certainly not running a web/ftp server or anything like that.

How can I find out which application/process is generating that bandwidth?

---

### Post by jetsam on 2008-05-29
Nethogs is the only application I know of that does this easily.  Install with:
```
sudo apt-get install nethogs
```
run with:
```
sudo nethogs eth0
```
Change eth0 in the command above to the name of your network interface if it isn't eth0.

Nethogs has some limitations-- it works on standard traffic but can't always find all traffic.  If it doesn't work for you, you may have to packet sniff with wireshark and interpret what it says to track it down.

---

### Post by neaj on 2008-06-06
In my case, I'm showing inbound data and I'm not downloading anything as far as I know. I tried nethogs, but it's very unhelpful:

```
PID   USER     PROGRAM      DEV        SENT      RECEIVED       
0     root     unknown                 0.116     51.743 KB/sec
6710  jean     firefox-bin  eth0       0.378     0.470 KB/sec
```

What's this unknown program with PID 0?

I suppose packet sniffing is the next stop, but I don't know so much about that ..

---

### Post by jetsam on 2008-06-06
> What's this unknown program with PID 0?

I don't really have a good understanding of that.  It's something I've seen before, and it's one of the limitations of nethogs I was referring to.  

I _think_ that's nethogs' catch-all entry for traffic that it knows exists but can't locate the process for.

Unfortunately, I don't know of a good alternative that can tell you more about the exact process responsible.  

One program that can give you some more information is **iftop**.  It's in the repositories.  Install with **sudo apt-get install iftop**, and run with:
```
sudo iftop -i eth0 -P
```
It will show you the ports and ip addresses (or web addresses if they're known) of the connections making the traffic, most traffic on top.  

Wireshark for packet sniffing is easy to run, but hard to understand what it's telling you.  You run it with **sudo wireshark**, then use the gui (**capture menu--> interfaces-->eth0--> start button**) to tell it to start capturing packets on your eth0 interface.  Hit ok when it gives you a warning about running as root.  If you don't run as root, it won't sniff your network.  You could just give it a try, and see if it sheds any light.  

To be honest, I wing it myself with wireshark.  Sometimes it's helpful to me even though I only have a vague understanding of all the packets and protocols.  

Close down firefox to take it out of the picture.  (Although, you might want to experiment with it on a bit.  Try reloading a webpage and looking at the results in either of the programs.)

---

### Post by micuintus on 2008-07-10
Thank's a lot for the tip! This NetHogs tool is **really** usefull!

> **neaj said:**
> What's this unknown program with PID 0?

AFAICS this is traffic with a port no application is listening to (these packages are rejected). For example, if you start  ktorrent with uploads and downloads going on, you see the traffic caused by it listed under ktorrent in the NetHogs table. If you then kill ktorrent, your peers still try to reach you (since they don't know you killed your torrent client) but there is no more application receiving this stuff and it is listed under "root     unknown".

---

