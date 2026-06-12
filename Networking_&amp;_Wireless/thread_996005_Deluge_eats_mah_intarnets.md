---
title: "Deluge eats mah intarnets?"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by DPic on 2008-11-28
Alright so i'm having problems and i think that either (or possibly both) deluge and my router are to blame. 

Symptoms: When i run deluge, internet surfing becomes impossible or, at the very least, very very slow and it seems to affect all the computers in the house. 

Setup: I have verizon FiOS 20 MiB/s upload and download. So far, with deluge, i've been able to get close to 2.5 MiB upload or download which is when it gets impossible to drowse the web. I usually keep the limit at 2 MiB but even lowering it to 1.5 MiB doesn't seem to make surfing much faster. I've taken the speed test and the bittorrent throttling test and everything seems like it should work at full speed. 

Deluge settings: Deluge is set to use ports 6881 to 689 (i unchecked use random ports in hopes that might make a difference for some reason). DHT is enabled. UPnP, NAT-PMP, Peer Exchange, and LSD are all checked. Encryption is enabled for all inbound and outbound with level set to "Either" and "Encrypt entire stream" is checked. 

Global Bandwidth Usage
Max Connections: 200
Max Upload Slots: 4
Max Download: -1
Max Upload: 2000 KiB/s
Max Half-Open Connections: -1
Max Connection Attempts per Second: 20
Ignore limits on local network: Yes

I used this to help me: [http://dev.deluge-torrent.org/wiki/Faq#WhatbandwidthsettingsshouldIuse](http://dev.deluge-torrent.org/wiki/Faq#WhatbandwidthsettingsshouldIuse)

I didn't set a limit for half-open connections because it only said to do so for Faildoze XP and Vista. It also says i should be able to set my upload limit to 80% of my upload speed which would be 16 MiB/s but i can only get 2.5 at most. 

Can anyone make a good diagnosis here? I know i seed a lot of torrents, but i should be able to without killing my internet!/Thank you so much to anyone who can help

---

### Post by xpod on 2008-11-28
> Setup: I have verizon FiOS 20 MiB/s upload and download. So far, with deluge, i've been able to get close to 2.5 MiB upload or download which is when it gets impossible to drowse the web. I usually keep the limit at 2 MiB but even lowering it to 1.5 MiB doesn't seem to make surfing much faster. I've taken the speed test and the bittorrent throttling test and everything seems like it should work at full speed.

I`m not too sure what you mean by 20/2.5 MiB`s but i think you mean 20Mb`s(Megabits)I have a 20Mb connection too although the upload is only a measly 728Kb`s.Not that it makes much odd`s to me in reality.

> It also says i should be able to set my upload limit to 80% of my upload speed which would be 16 MiB/s but i can only get 2.5 at most.

20Mb`s = 2.5MB`s so if you were downloading/uploading at practically full speed(2.5MB`s is full speed) surely that itself would be enough to slow everything else down.

I use Deluge myself on occasion and rarely ever get the full 20Mb/2.5MB/2500Kb`s when downloading but when i am my browsing also suffers.

EDIT:Simple solution is just to do your downloads while you sleep so your not hogging all the bandwidth during the Day;-)

---

### Post by DPic on 2008-11-28
> **xpod said:**
> I`m not too sure what you mean by 20/2.5 MiB`s but i think you mean 20Mb`s(Megabits)I have a 20Mb connection too although the upload is only a measly 728Kb`s.Not that it makes much odd`s to me in reality.



20Mb`s = 2.5MB`s so if you were downloading/uploading at practically full speed(2.5MB`s is full speed) surely that itself would be enough to slow everything else down.

I use Deluge myself on occasion and rarely ever get the full 20Mb/2.5MB/2500Kb`s when downloading but when i am my browsing also suffers.

EDIT:Simple solution is just to do your downloads while you sleep so your not hogging all the bandwidth during the Day;-)

Sorry, Deluge seems to measure in MiB (Mebibytes) and my internet speed is 20 Mb/s (Megabits) UL&DL. Mebibytes are pretty close to Megabytes so i guess that solves the mystery. I feel stupid. Thanks!

---

### Post by xpod on 2008-11-28
> Sorry, Deluge seems to measure in MiB (Mebibytes) and my internet speed is 20 Mb/s (Megabits) UL&DL. Mebibytes are pretty close to Megabytes so i guess that solves the mystery

It`s an easy mistake to make.I used to spend a bit of time on my ISP`s forum so the only reason i really know myself is all the people shouting about their nice new 20Mb connections only showing  2MB:-k

> I feel stupid. Thanks! 

It seems you weren`t around during *my* first year then:-\"
There`s not much difference now mind you,other than knowing how to use Google  a bit better.

---

