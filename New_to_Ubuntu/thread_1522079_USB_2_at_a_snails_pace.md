---
title: "USB 2 at a snails pace"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by Fidelio on 2010-07-01
Hi,
I think this is the only thing I've ever really come across that actually seems like a proper bug. On my old PC, which was an ageing P4, I could only copy files to and from my external hdd at about 1mb per second. I sort of hoped that on my spanking new one would do a bit better. I've noticed there are a few related bugs on launchpad, but this is a bit of a stinker for me. This seems to go back years. Have I missed something simple, or does USB 2 just not work properly on linux?
Many Thanks
F

---

### Post by cariboo on 2010-07-01
It depends on what version you are using, between 8.04 and 9.10, usb transfers were slow, Since Lucid things have improved quite a bit. I can only compare to XP, but transfers speeds are approximately the same between it and Ubuntu.

---

### Post by -humanaut- on 2010-07-01
I had problems in Jaunty with USB transfer rates but they seem all but solved now (Lucid) Also make sure your using USB2.0 ports generally on older motherboards not all of them are USB 2.0 some are USB 1.1 (I have a relativity new MCP61 and it still has two 1.1 usb ports)

---

### Post by warfacegod on 2010-07-01
For me, it depends on what type of file and their size I'm moving. If I'm moving an album's worth of mp3's, say around 100 MB, the progress window doesn't even have time to open. If I move 1 GB or under of mpegs at around 90 MB each, it takes under 10 seconds (my USB *really* likes smallish mpegs for some reason). Files of 400 MB or better and things start slowing way down. I rarely get better than 15 - 20 Mps. 10 GB or more total size transfers and it can start taking hours.

It also depends on what else my laptop is also doing at the time.

Another factor to consider is the destination itself. Your external simply may not be able to handle the information fast enough for a USB2 connection. Some Externals and indeed even some computers are still built with USB2 connections but the USB controllers are still USB1.1. The file system use are using, going from and to, can be a factor. Even the age of an HDD, external or not, can affect it's speed. 

I'm not trying to say you aren't experiencing a bug because it's certainly possible you are. I'm just looking to give you some things to consider.

---

### Post by Fidelio on 2010-07-01
Thanks for all the suggestions, but...
The PC is brand new and the ext drive is about a year old. It may be relevant to add that when I first got the drive it managed fast transfers to and from my Xp boot, but was very slow (1mb a second) on ubuntu 9.04. Then I formatted it to ext3 as I was only using it for linux at the time, and it was still slow. Now I've tried formatting it to FAT32 and NTFS and in both cases it works , still slowly with linux, but is not recognised at all by Windows 7 or XP. It does sort of seem that not only does Ubuntu read my disk very slowly, it has also rendered it useless  by windows.
It's rather perplexing.

---

