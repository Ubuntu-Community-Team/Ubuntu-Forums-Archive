---
title: "my ubuntu is deathly slow on resolving with the wifi. it's fine via cable connect?!"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by ijason on 2007-11-09
hello all. 

since a few days ago, my ubuntu (7.04) laptop has been deathly slow on the internets. sites often fail out before they can resolve, and my AIM often can not log on successfully. this is all via the default wifi built into my Dell laptop. before a few days ago everything worked perfectly - wifi wise - and now i can barely get a web site to load.

i tried connecting to my router via a cable, and suddenly everything worked fine. sites resolved just as quick as normal. for a short while after disconnecting the cable, everything was back up to speed on the wifi, and now they've slowed back down.

more importantly, there are several other machines using various wifi solutions connected to the same router, and they are getting fine performance. these are windows machines. most importantly, the delay does not affect all web applications. i can play an online game without lag, and ftp transfers are fine... but web pages, aim, telnet, apt-get are all horribly slow.

any help would be much appreciated!

---

### Post by Lambert on 2007-11-10
> **ijason said:**
> hello all. 

since a few days ago, my ubuntu (7.04) laptop has been deathly slow on the internets. sites often fail out before they can resolve, and my AIM often can not log on successfully. this is all via the default wifi built into my Dell laptop. before a few days ago everything worked perfectly - wifi wise - and now i can barely get a web site to load.

i tried connecting to my router via a cable, and suddenly everything worked fine. sites resolved just as quick as normal. for a short while after disconnecting the cable, everything was back up to speed on the wifi, and now they've slowed back down.

more importantly, there are several other machines using various wifi solutions connected to the same router, and they are getting fine performance. these are windows machines. most importantly, the delay does not affect all web applications. i can play an online game without lag, and ftp transfers are fine... but web pages, aim, telnet, apt-get are all horribly slow.

any help would be much appreciated!

Post the output of 

```

sudo iwconfig

```

---

### Post by ijason on 2007-11-11
thanks for a reply! finally! :) here's the output :

> 
jason@jason-laptop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"ZyXEL"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:49:AE:58:4E   
          Bit Rate:24 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:A1E2-2F41-2A   Security mode:restricted
          Power Management:off
          Link Quality=77/100  Signal level=-33 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:81  Invalid misc:0   Missed beacon:1

jason@jason-laptop:~$ 


it seems almost intermittent. for a short while the internet will work fine in all aspects, and then other (much longer) periods i'll have almost no usable internet connection at all. while the other computers on the network will have consistently good performance.

---

### Post by jjustin01 on 2007-11-15
I'm bumping this up because I am having the same problem.  Here's the output of my iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"OSUWIRELESS"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0B:86:CC:FD:A0   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key: off
          Power Management: off
          Link Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:671  Invalid misc:20824   Missed beacon:0


I am running on a Dell 1721 with a Broadcom bcm4328 card.

---

### Post by jjustin01 on 2007-11-15
Try the following steps to get DNS cached to see if that speeds things up for you.  So far it seems to be working for me.

- Install dnsmasq with Synaptic
- go System -> Administration -> Networking
- click the DNS tab
- press the Add button and type 127.0.0.1 and press enter
- click on a different entry so that 127.0.0.1 isn’t highlighted and then click and drag 127.0.0.1 to the top of the list
- press OK and you’re done!

If that doesn't work, follow the steps on this page.
[http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)

One of commenters did recommend using opendns.com for your DNS servers instead of your own ISP.  This would definitely work a lot better if you go from place to place on your laptop.

Hopefully this will work for you.

---

