---
title: "Torrents cause Entire system(8.04) to hang / crash / freeze / locks up"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by unc0nn3ct3d on 2008-08-25
I can reproduce this bug with 100% consistency now, which is odd because as of 1-2 months ago it didn't exist at all.  This kind of tells me that it isn't simply a system or OS problem but something going on because of a change or additional which has occurred over the past little while.

So every single time I start up Deluge the system will usually hang completely in under a minute.

Screen stays on everything just locks right up and stays that way.. I can alt-f1 , I can't ctrl+alt - backspace nothing works and I need to power down and power back up.

I have no idea what is going or even how to diagnose this problem so I was wondering if anyone had any advice.

I am using a Linksys 300N NIC with bcm43 setup + ndiswrapper on 2.6.24-19 (Hardy Heron 8.04)

Thanks in advance

---

### Post by ajgreeny on 2008-08-25
What about trying another torrent client (transmission?) to see if it's the torrent activity or the client you are using that causes the crash.

---

### Post by unc0nn3ct3d on 2008-08-26
Actually it is funny that you mention this because the first time I put two and two together on these system hangs was when transmission somehow became my default torrent client and loaded up at the same time as deluge.. At first I thought it was cause they were both loading at the same time, but after uninstalling transmission the problem was still there, and had been there before this just to note.

 Looking around it definitely is a ubuntu+wireless+torrent issue as apposed to anything specific to any of those 3 factors.  I read it might be an ACPI issue but that was never confirmed

---

### Post by unc0nn3ct3d on 2008-11-01
Just wanted to say that I have switched to transmission nw many months later and everything runs fine.. looks like it was deluge all along causing these problems

---

### Post by furiousmanatee on 2008-12-22
I have been having the same problem for some time now - using transmission, my whole system freezes after an apparently random amount of time. (this is a complete system crash - caps and num lock flash and the machine is totally unresponsive, requiring a hard restart). sometimes i can get a good 4 hours in, sometimes 10 mins. the crashes only happens when using a bitorrent (i have tried azaurus and utorrent as well) - otherwise my system runs fine. 

im running:
MSI L735 laptop 
8.04 lts (fresh)
AMD 64 1gb x2
nvidia geforce go 7600 with restricted drivers 
wireless 

my ubuntu kung fu is still at white belt, being a vista refugee, though im keen to learn some kick *** moves 
this problem is really annoying - torrenting half an hour at a time is no way to live, and hard restarts are very disconcerting. there are also no prior signs to aid diagnosis - system monitor shows nothing, the problem happens irrespective of what else is going on in the background or my power settings.

below is a log of the last crash. - left the house at 00.30 ish with transmission running, got home at 4 after the system had been twated for 3 hours. below is the system log 

any insight into WTF would be hugely appreciated, i havnt seen any fixes for this or similar bugs - this is my first forum post...ever! serious respect and gratitude to all the problem solvers and open source programmers out there - these forum posts have saved my system more than once and life is open source despite what we are lead to believe 

sincerely
Furious 
 
Dec 22 01:05:11 manatee syslogd 1.5.0#1ubuntu1: restart.
Dec 22 01:05:11 manatee anacron[6124]: Job `cron.daily' terminated
Dec 22 01:05:11 manatee anacron[6124]: Job `cron.weekly' started
Dec 22 01:05:11 manatee anacron[7539]: Updated timestamp for job `cron.weekly' to 2008-12-22
Dec 22 01:05:16 manatee syslogd 1.5.0#1ubuntu1: restart.
Dec 22 01:05:16 manatee anacron[6124]: Job `cron.weekly' terminated
Dec 22 01:05:16 manatee anacron[6124]: Normal exit (2 jobs run)
Dec 22 01:05:44 manatee kernel: [ 1163.126745] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:05:45 manatee kernel: [ 1163.574937] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:05:49 manatee kernel: [ 1165.149081] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:05:52 manatee kernel: [ 1166.397552] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:05:57 manatee kernel: [ 1168.360887] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:05:58 manatee kernel: [ 1168.769882] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:06:04 manatee kernel: [ 1171.152796] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:06:05 manatee kernel: [ 1171.347111] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:06:19 manatee kernel: [ 1177.117858] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:06:21 manatee kernel: [ 1177.690745] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:06:24 manatee kernel: [ 1179.122702] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:06:28 manatee kernel: [ 1180.761776] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:06:32 manatee kernel: [ 1182.311345] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:06:34 manatee kernel: [ 1182.924250] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:06:51 manatee kernel: [ 1189.921498] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:06:56 manatee kernel: [ 1191.965521] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:07:00 manatee kernel: [ 1193.533099] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:07:02 manatee kernel: [ 1194.214984] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:07:28 manatee kernel: [ 1204.729519] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:07:29 manatee kernel: [ 1205.055726] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:07:33 manatee kernel: [ 1206.733983] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:07:34 manatee kernel: [ 1207.020626] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:07:41 manatee kernel: [ 1209.923928] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:07:48 manatee kernel: [ 1212.382746] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:07:53 manatee kernel: [ 1214.710140] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:07:59 manatee kernel: [ 1216.960484] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:08:04 manatee kernel: [ 1219.129272] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:08:07 manatee kernel: [ 1220.314520] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:08:11 manatee kernel: [ 1221.910458] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:08:12 manatee kernel: [ 1222.117516] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:08:15 manatee kernel: [ 1223.508129] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:08:20 manatee kernel: [ 1225.306294] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:08:27 manatee kernel: [ 1228.340734] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:08:29 manatee kernel: [ 1228.909004] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:08:54 manatee kernel: [ 1239.133932] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:08:59 manatee kernel: [ 1241.095908] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:11:18 manatee kernel: [ 1296.461060] ACPI: EC: missing write data confirmation, don't expect it any longer.
Dec 22 01:12:41 manatee kernel: [ 1329.502731] wlan0: switched to short barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 01:12:41 manatee kernel: [ 1329.621883] wlan0: switched to long barker preamble (BSSID=00:06:25:c4:92:71)
Dec 22 04:05:06 manatee syslogd 1.5.0#1ubuntu1: restart.
Dec 22 04:05:06 manatee kernel: Inspecting /boot/System.map-2.6.24-23-generic
Dec 22 04:05:06 manatee kernel: Loaded 28514 symbols from /boot/System.map-2.6.24-23-generic.
Dec 22 04:05:06 manatee kernel: Symbols match kernel version 2.6.24.
Dec 22 04:05:06 manatee kernel: Loaded 36158 symbols from 100 modules.

---

### Post by furiousmanatee on 2008-12-22
forgot to mention: i DONT have NDISwrapper installed at all. wireless generally works fine

---

### Post by zieglerj on 2009-02-17
Bump

---

