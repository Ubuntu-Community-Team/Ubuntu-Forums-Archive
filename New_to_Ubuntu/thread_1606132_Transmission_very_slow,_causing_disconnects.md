---
title: "Transmission very slow, causing disconnects"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by fireflower on 2010-10-26
Same computer, same wireless connection, using Windows XP sp3 and utorrent would yield down speeds between 400-1,000kb/s. Could browse internet simultaneously with minimal slowdown if any. 

Installed Ubuntu 10.10, ndiswrapper and drivers to get the Windows-native wireless card to work in Ubuntu, and it does. Internet browsing is even faster than with Windows. Downloading patches and updates through the OS is always hundreds of kb/s. Downloading porn I mean files through Chrome is just as fast.

However down speed for Transmission hovers between 0 and 5 kb/s for popular torrents. One has over 400 seeds, one has over 2,600 seeds, and yet Transmission only listed 2 seeds as visible and had anemic down speed for both. Simultaneous internet browsing becomes dialup-like. Wireless connection sputters, dropping and picking back up and dropping again. When I close Transmission, the problems go away.

Will be reading up on the subject while awaiting a response. I've only used Ubuntu for 2 days and I'm already in love with it. I spent 20 years frustrated and angry at Windows and Bill Gates, shaking my fists at the heavens in view of a callous god. Till now I've had no problems, or at least, no problems I could not figure out on my own. Please help me access these totally legitimate files from trustworthy sources that I have actually bought in real life and are merely backing up as is my right as a paying customer who would never pirate anything ever for any reason ever ever honest.

---

### Post by alexandari on 2010-10-26
Have you tried another torrent client?

---

### Post by LiamWilson on 2010-10-26
By default, transmission sets the maximum seeds it connects to to 60 per torrent. If you want, you can try right clicking a torrent, going to properties -> options and then increasing the number of maximum peers. 

I have had similar problems with transmission in the past, which were solved by installing another bittorrent client (Vuze is available from the software centre) or finding an updated PPA for transmission. The 1st one would probably be the best option.

If you are going to download vuze, however (As I've just discovered) you'll probably want to download it from the vuze website as opposed to from the software centre, as the version from the SC is out of date, and a bit broken :(

---

### Post by Chayak on 2010-10-26
There are quite a few ISPs that have connection limits in their modems.  You can solve those problems most of the time by using a VPN tunnel so the ISP only sees one connection and the endpoint handles all of the torrent connections.  Torrents use to kill my connection until I finally figured that out.

---

### Post by babloo75 on 2010-10-26
As per my opinion qBitTorrent is the best torrent client for ubuntu. You will simply love it like you love Ubuntu.

---

### Post by fireflower on 2010-10-26
> **alexandari said:**
> Have you tried another torrent client?
I know right. It was a combination of me still being terrified of installing things to ubuntu and the time being 4 am and I wanted to go to sleep.

> **Chayak said:**
> There are quite a few ISPs that have connection limits in their modems.  You can solve those problems most of the time by using a VPN tunnel so the ISP only sees one connection and the endpoint handles all of the torrent connections.  Torrents use to kill my connection until I finally figured that out.
But my connection was fine under Windows using µtorrent. The torrents came down two orders of magnitude faster through the same pipe using the same hardware.

> **babloo75 said:**
> As per my opinion qBitTorrent is the best torrent client for ubuntu. You will simply love it like you love Ubuntu.
I will try the thing. But it does beg the question: Why is Transmission packaged with ubuntu if people know it is, to be generous, "less than ideal?"

---

### Post by ironic.demise on 2010-10-26
> **fireflower said:**
> I know right. It was a combination of me still being terrified of installing things to ubuntu and the time being 4 am and I wanted to go to sleep.


But my connection was fine under Windows using µtorrent. The torrents came down two orders of magnitude faster through the same pipe using the same hardware.


I will try the thing. But it does beg the question: Why is Transmission packaged with ubuntu if people know it is, to be generous, "less than ideal?"

+1 qbittorrent, Transmission was causing me trouble too. This is faster easier and more reliable thanks for the heads up.

The reasons that the Ubuntu team have for including software varies, They took out GIMP because it was too large.
They may have included Transmission because it was more "new user friendly"? or perhaps it was a smaller size. As I saidm the reasons can vary... atleast you don't have to go out and pay for some necessities like AV in windows. If you REALLY need it, you can still get it quite easily, that's my two cents.

---

### Post by fireflower on 2010-10-26
+1 qbittorrent. Problem resolved. Thanks all! Now to wrassle with my printer. But that's another story. :KS

---

