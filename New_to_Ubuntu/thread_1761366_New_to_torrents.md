---
title: "New to torrents"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by Wim Sturkenboom on 2011-05-18
I don't use torrents, but last night had to to get a crunchbang iso.

I don't mind sharing but have a limit on my internet usage of 2GByte/month (up and down together). So sharing might make me easily run out of capacity and I want to make sure that I only share when I want to share.

The questions:
[LIST=1]
[*]How can I stop sharing? Is closing Transmission sufficient? Or is there a background process that I'm not aware of?
[*]How can I verify that it is indeed stopped? netstat?
[/LIST]
While downloading using Transmission, I could see with netstat that there was activity on port 51413

This morning the download was complete and I saw 'seeding to 1 of 1 connected peers'; I assume that that is where I share with others.

I checked with netstat and saw the following
```

wim@desktop-01:~$ sudo netstat --udp --all -p
[sudo] password for wim: 
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 192.168.2.222:34612     .:domain                ESTABLISHED 3058/transmission
udp        0      0 *:51413                 *:*                                 3058/transmission
udp        0      0 *:mdns                  *:*                                 1054/avahi-daemon: 
udp        0      0 *:ipp                   *:*                                 1584/cupsd      
udp        0      0 192.168.2.222:45179     .:5351                  ESTABLISHED 3058/transmission
udp        0      0 *:48280                 *:*                                 1054/avahi-daemon: 

```
After closing Transmission
```

wim@desktop-01:~$ sudo netstat --udp --all -p
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 *:mdns                  *:*                                 1054/avahi-daemon: 
udp        0      0 *:ipp                   *:*                                 1584/cupsd      
udp        0      0 *:48280                 *:*                                 1054/avahi-daemon: 

```
I guess I'm no longer sharing but like to make sure.

---

### Post by shashanksingh on 2011-05-18
I think my torrent uses both tcp and udp. I did this while my transmission was on and it was seeding as well..
> sudo netstat -p | grep 'transmission'

and I got this

```
tcp        0      0 27.124.30.237:51413     180.215.48.12:4219      ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:45677     113.19.249.228:22541    ESTABLISHED 1977/transmission-g
tcp        0   1424 27.124.30.237:51413     triband-del-59.17:17139 ESTABLISHED 1977/transmission-g
tcp        0  14520 27.124.30.237:51413     triband-mum-59.18:60106 ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     ABTS-North-Dynamic:3585 ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     117.211.85.69:1199      ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     117.203.53.131:1598     ESTABLISHED 1977/transmission-g
tcp        0   8462 27.124.30.237:53665     114.30.72.111:31098     ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     Static-236.73.99.:62249 ESTABLISHED 1977/transmission-g
tcp        0    713 27.124.30.237:51413     2.90.100.39:4763        ESTABLISHED 1977/transmission-g
tcp        0    298 27.124.30.237:51413     Static-166.155.99:56415 ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     auh-as9045.alsham:57394 ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     auh-as6779.alsham:53645 ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     ABTS-mp-Dynamic-0:58506 ESTABLISHED 1977/transmission-g
tcp        0   1065 27.124.30.237:51413     94.166.193.149:49425    ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     2.102.236.249:60479     ESTABLISHED 1977/transmission-g
tcp        0     10 27.124.30.237:51413     59.161.47.152.sta:49975 ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:43485     mymail.wintek.co.:29993 ESTABLISHED 1977/transmission-g
tcp        0  20124 27.124.30.237:51413     117.206.232.171:wipld   ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     223.255.230.28:36865    ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     ABTS-North-Dynamic:2022 ESTABLISHED 1977/transmission-g
tcp        0  13068 27.124.30.237:51413     triband-mum-59.18:62322 ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     109.100.92.173:64195    ESTABLISHED 1977/transmission-g
tcp        0  29636 27.124.30.237:51413     auh-b16636.alsham:64219 ESTABLISHED 1977/transmission-g
tcp        0  19992 27.124.30.237:35721     59.95.167.102:23449     ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     199.7.156.42:16282      ESTABLISHED 1977/transmission-g
tcp        0  42108 27.124.30.237:51413     175-107-rev-place:11061 ESTABLISHED 1977/transmission-g
tcp        0  22316 27.124.30.237:51413     182.178.213.146:11013   ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     120.56.192.123:17184    ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     cm75.eta234.maxon:49358 ESTABLISHED 1977/transmission-g
tcp        0    588 27.124.30.237:38876     ABTS-North-Dynami:32168 ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     120.56.192.123:17184    ESTABLISHED 1977/transmission-g
tcp        0      0 27.124.30.237:51413     cm75.eta234.maxon:49358 ESTABLISHED 1977/transmission-g
tcp        0    662 27.124.30.237:38876     ABTS-North-Dynami:32168 ESTABLISHED 1977/transmission-g
tcp6       0      0 2002:1b00:39ce:a::51413 2001:0:4137:9e76::52388 ESTABLISHED 1977/transmission-g
udp        0      0 27.124.30.237:44377     27.124.3.2:5351         ESTABLISHED 1977/transmission-g
unix  3      [ ]         STREAM     CONNECTED     22201    1977/transmission-g /tmp/orbit-shashank/linc-7b9-0-29744c3a9fe7
unix  3      [ ]         STREAM     CONNECTED     22199    1977/transmission-g 
unix  3      [ ]         STREAM     CONNECTED     21275    1977/transmission-g 
unix  3      [ ]         STREAM     CONNECTED     22194    1977/transmission-g 
unix  3      [ ]         STREAM     CONNECTED     22184    1977/transmission-g 
unix  3      [ ]         STREAM     CONNECTED     22161    1977/transmission-g 
unix  3      [ ]         STREAM     CONNECTED     22160    1977/transmission-g 
unix  3      [ ]         STREAM     CONNECTED     21265    1977/transmission-g 

```


so I think you cannot be sure of torrents using only udp.

I guess closing the torrent application or better changing the settings for seeding is when you can rest asured.

---

### Post by ExileAmongYou on 2011-05-18
Closing Transmission will stop you from sharing, as long as you close it fully, i.e. it's not just minimising into the indicator on the panel/top bar.

---

### Post by -kg- on 2011-05-18
> **ExileAmongYou said:**
> Closing Transmission will stop you from sharing, as long as you close it fully, i.e. it's not just minimising into the indicator on the panel/top bar.

Exactly!  It doesn't do to just close it using the "x" on the Window...you have to use "File/Close" from the menu in order to close it fully and not allow it to continue "sharing."  Clicking the "x" only minimizes it.

Alternatively, to make sure, you can go into "Edit/Preferences", and under the "Torrents" tab, change the "Limits" ratio to "0".  That will stop any sharing whatsoever, whether you actually close Transmission or not.

---

### Post by Grenage on 2011-05-18
> **-kg- said:**
> Alternatively, to make sure, you can go into "Edit/Preferences", and under the "Torrents" tab, change the "Limits" ratio to "0".  That will stop any sharing whatsoever, whether you actually close Transmission or not.

I haven't used Transmission in a very long time, but isn't *0* normally the setting for *unlimited*?

---

### Post by qyot27 on 2011-05-18
Actually stop the torrent itself, and/or then fully close the application.  This is true of all BitTorrent clients (or at least, all that are worth using).  When you want to resume, just start the torrent itself again.  As long as the stopping part was not a case of 'and Delete Data', it'll be fine.  The BitTorrent protocol can stop and resume downloads at will with no ill effects.

---

### Post by NCLI on 2011-05-18
> **Grenage said:**
> I haven't used Transmission in a very long time, but isn't *0* normally the setting for *unlimited*?

No, that would be -1.

---

### Post by Grenage on 2011-05-18
> **NCLI said:**
> No, that would be -1.

Cheers!

---

### Post by Wim Sturkenboom on 2011-05-18
Thanks everybody for the replies.

Closing with X seems to close Transmission fully (same as file/quit). A *ps -ef* reveals that after that it's no longer running.

I've now set the ratio in edit/preferences to 10% so I can be a little bit social ;). Just before the end of each month I can see if I can allow more or not.

And I will keep a close eye on my usage for the next coming few days.

---

### Post by -kg- on 2011-05-18
Glad to hear you got that settled.

Man, I ***HATE*** those per-month caps!  :mad:

---

### Post by CVGH on 2011-05-18
After you close transmission, you will see some UDP's banging away at you for a while until they realize you have shut it down. 
Freaked me out the first time I saw udp's coming in from nigeria and other grotty locales...

---

