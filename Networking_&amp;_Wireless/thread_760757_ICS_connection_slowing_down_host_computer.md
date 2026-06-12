---
title: "ICS connection slowing down host computer"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by tim22b on 2008-04-20
Hi,

I just switched my rather slow IBM laptop from XP over to 7.10 a couple of days ago and I ran into something that's becoming a problem.  Here's the setup:

USB Cable Modem <--USB--> XP Desktop <--ICS/Ethernet Cable--> Ubuntu 7.10 Laptop

Anyways, when I access some internet sites, usually when they have a lot to download, the XP computer slows down.  Not the internet on the XP box, but the computer itself.  For instance, if a game is being played (not even that hardware intensive of one), it will become horribly choppy, the same happens if a movie is being watched.  This has been an issue since I installed Ubuntu.  Occasionally it will happen if I'm trying to do Add/Remove from the applications toolbar or doing apt-get, but most of the time it occurs when using Firefox.  When the laptop was running XP also, the desktop didn't have this issue.  Anyone have any ideas?

---

### Post by CrazyGuy123 on 2008-04-20
Thats an odd problem - the XP desktop shouldn't have any trouble coping with the comparatively tiny amounts of data it needs to forward on to the ubuntu machine, unless I spose your cable connection is more than 50Mbits

Get task manager up on the XP machine by pressing Ctrl+Alt+delete, and have a look in the "processes" tab.  Sort the columns by %CPU by clicking the CPU column heading.  Note down which things are using most CPU when the computer is doing nothing, and then note them down again when loading a web page from the ubuntu PC.

When doing that, "System Idle Process" is normal, and allowed to use up most of the processor, but nothing else should use more than a few %.

Generally, if "System" uses a lot of CPU while thats happening, there's some problem with the network or modem drivers on the XP computer.  If "svchost" uses a lot of CPU, then there's probably something going on in the DNS or DHCP service part of the Internet Connection Sharing.

It might also narrow down the problem if you could establish, does the slowdown occur when browsing the web mainly, or when doing downloads?  You can use [This]("http://www3.uakron.edu/majuro/PNG/PNG-Volcano-map1.bmp") file as a download test - it's a 2.5MB image so should take less than a minute on most broadband connections.

---

### Post by tim22b on 2008-04-21
I tried to test it and found out that the *vsmon* process on the XP computer was putting waaay too much of a load on the system whenever I looked at something on the laptop.  After a brief search I determined it was the mail checker in Zone Alarm which was unneeded so I turned it off.. It seemed to help a little bit.  I think I can Add/Remove programs now without it interfering too much but If I try to look at too much on the laptop it still slows it down considerably.. (bad skipping in videos playing from the hdd).  For instance, that happened when I was trying to load two youtube videos at once on the laptop.  Occasionally *lsass* (that's an L btw) would get around 20%, but vsmon was the big problem.

---

