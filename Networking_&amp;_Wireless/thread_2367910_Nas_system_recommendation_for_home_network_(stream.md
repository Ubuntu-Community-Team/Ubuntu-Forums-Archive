---
title: "Nas system recommendation for home network (stream movies home &amp; away)"
date: 2017-08-04
forum: Networking &amp; Wireless
---

### Post by woo10jw on 2017-08-04
Would like your best NAS system guess with what I already have and what I would need, I have (2) 4tb NAS HDD in computer already, each half full and will continue to add more (movies/tv shows), not against buying more HDDs for NAS system purchased..Some forum members think Raid 1 is not necessary for home units, I don't know, I can back up other ways. What do you think is a good way for me to go. I know that everyone has a favorite brand and whats good for you might not be good for me but I would still like to know your opinion. 
Don’t think I would ever fill a 8TB unless I combined the movies & tv shows to 1 drive (not against that either).
Thanks in advance for all recommendations. (10years with Ubuntu but not a geek)

SYSTEM: 
MB: ASRock Z270 Extreme (LGA1151) > CPU: Intel I7 7600K  > Memory: GSkill DDR4 3200-16gb (not OC) > OS: Ubuntu 14.04 (Cinnamon 3.4)(SSD-Samsung 850evo) > GPU: Zotac GT520 (no gaming) > HDD: (2) 4TB Seagate NAS HDD 1(movies) 1(TV shows) > Router: Asus TM-AC1900 > PS: Corsair TX 650w  > CASE: NZXT (ATX full tower)

---

### Post by TheFu on 2017-08-04
RAID is never a backup.  RAID solves 3 problems, but not backups. All RAID still needs backups.
Backups solve 1,001+ problems, including corrupt RAID, failed RAID, and many others.

My only suggestion is to avoid Seagate storage.

Besides that, I don't understand what you are asking.  

I would never recommend buying a separate NAS unit until you have $20K to spend. Less than around that price, a home-built storage device will provide 5x more flexibility and capacity for the price. Commercial storage solutions aren't usually a good deal on the low-end and usually only support specific disk vendors and models.

OTOH, if you have more money than time/skill, I wouldn't think it foolish to spend that money on a NAS device.

---

### Post by DuckHook on 2017-08-04
TheFu gives wise advice. My additional tuppence:

For general users, and especially for a self-professed "not-a-geek", RAID is a solution looking for a problem. Actually, that's being too kind. It is a problem waiting to happen. This is because it is difficult, obscure and frustrating to recover from a failed RAID. RAID is used for applications in which zero down-time is essential (like banks, on-line vendors, etc). The cost of such guaranteed access is high complexity, maintenance and expense, both in time and money.

As general users, we don't need RAID. We need backups. It is common for people to confuse the two. If you also want redundancy, then a second backup server is better than a standalone NAS whether RAID or not. Moreover, as TheFu again states, it is easy to spin your own backup server. You just need a relatively low-powered (cheap) machine with enough HDD for your purposes. Add Linux and rsync and you are good to go. But a backup server is not the same as actual backups. There are no shortcuts. If you don't back up, then you are just counting down the days to your own little disaster.

---

### Post by woo10jw on 2017-08-04
Probably didn't word the question correctly...I was thinking about WD MyCloud $300, Qnap $325, Synology $200 or build server with old computer. I don't know much about the first 3, thought they would be basically up and running after some settings and drives were install. 
I just want to stream some of the 2000 movies and 84 TV series I have thru my network. Trying to figure out the best way to go about this.

---

### Post by TheFu on 2017-08-04
"Best" is highly subjective.

I started with a storage sharing solution.  Found that hardware to playback the media was very picky about file formats.  The storage has always been "on the network" for me.  Having it local to the playback device just seems "wrong" and makes dealing with 3 rm playback a hassle.

Moved to a better playback device that handled about 15 different file formats, but eventually, newer files weren't supported and other media was a hassle to stream.

Moved to a more flexible playback device - an Atom-based laptop.  At the time, I didn't have any hidef content, so all formats that weren't hidef worked very well. As more and more hidef content became available, it failed. Badly. This was before GPUs had support for video decoding built-into the HW. Most $20 GPUs today support MPEG and H.264 accelerated decoding in hardware, so it isn't an issue for a recent computer. Even the cheapest on-board intel GPUs support it as proven by every chromebook made.

Moved to a more powerful, cheap, AMD APU (CPU + GPU) all in one.  It had a Radeon GPU - support was dropped and the CPU couldn't handle 720+ resolutions.

By this point, I had a few different playback devices - silent, cheap, but picky about file formats.  The worst are a Roku and Chromecast.  Newer content streamed from the web was fine, but older, local, stuff wouldn't steam at all. xvid, divx, mpeg2, aren't supported.  It was time to graduate to a real streaming server that could transcode as needed to whatever the playback device demands.

About 3 yrs ago, I built a storage + plex media server + Calibre + NAS + about 10 other things.  It is built on Ubuntu Server.  At the time, I spent $100 on a motherboard + CPU combo and have never regretted that.  The G3258 CPU can transcode 2 hidef streams into whatever format and/or resolution required for the playback device.  The machine now has about 20TB of storage installed. Not bad for $126 outlay (MB+CPU+RAM). Everything else was from left-over parts from other systems.

If I had gone with a commercial storage device, I would have been stuck, limited.  As you can read above, I'd already been stuck before and didn't want that again.  Where I live, TV broadcast is currently mpeg2-ts, but in a few years, it will be changing to some new format, probably h.265. None of my playback devices can handle that at 1080 directly, so transcoding will be required, unless I want to replace 6 playback devices.  No thanks.

Have 2 raspberry pis, which are the main playback devices here for a number of reasons instead of the roku/chromecast.  They are very flexible on file formats, but have trouble with h.265 and some other odd hidef content encodings. Stuttering when there isn't hardware support at 1080p resolutions. The Plex server transcodes to h.264 which the raspberry pis support with hardware acceleration. Currently running OSMC (which is based on Kodi) on the R-Pis.  They will not do 4K video, if that is important.  I don't own any 4K viewing devices.

4K video will change almost everything required, I suspect. I do not have any experience with it, but would expect that my Plex Server would need a little stronger CPU to handle transcoding in real-time. However, I do not know if that is true.

Plex has multiple ways to stream - DLNA, Plex protocol, and there is a web interface. Plex isn't F/LOSS, but it is free.  I don't have a plex account. It isn't required.  Using a SOCKS proxy or VPN, it can be used to stream content from home to anywhere in the world over the internet.

I've been burned a few times over the years.  I will be again, but it won't be in this area.  I've learned.

I've also learned to avoid CIFS/Samba for sharing files and to avoid wifi.

Whether any of this is useful to you, I cannot say.

---

### Post by QIII on 2017-08-04
Even a Raspberry Pi can do hardware accelerated 1920x1080 playback using omxplayer.  Not much in the way of shiney controls, but it works on the cheap.  And if you stream to it over your network it's silent.  I do that from my home website using rtmp.

---

### Post by woo10jw on 2017-08-04
Thanks for your reply...not up on this that's why I'm asking for opinions. Started with Ubuntu 10yrs ago and everything I've learned has come from
this forum. Again Thank you

---

