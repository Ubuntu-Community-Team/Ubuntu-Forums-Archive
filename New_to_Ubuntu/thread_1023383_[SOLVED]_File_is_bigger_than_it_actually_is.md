---
title: "[SOLVED] File is bigger than it actually is???"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-12-27
I've been downloading a large file via bittorrent and want to continue it on another PC but I'm having to move the files to the other PC via a couple of dvd's now her comes the problem...

According to the Ubuntu it's size is roughly 24gb's but I know for a fact that I've only downloaded about 16% of a 27.5gb file which works out at roughly 4.5gb's, so how do I burn this data to a dvd/s? because at the moment I'd need a trillion according to Ubuntu:lolflag:

Thanks in advance!

---

### Post by Helios1276 on 2008-12-27
Torrents allocate the space first and then the file comes down

---

### Post by halitech on 2008-12-27
if it thinks the torrent is that big you may be better off trying to network the machines and move them that way

ps. I'm half afraid to ask what it is that you are downloading that is that big

---

### Post by kamitsukai on 2008-12-28
> **halitech said:**
> if it thinks the torrent is that big you may be better off trying to network the machines and move them that way

ps. I'm half afraid to ask what it is that you are downloading that is that big

Only some video files (perfectly legal)

---

### Post by Rolcol on 2008-12-28
The file is most likely allocated with NULLs therefore there's a lot of redundancy.  A solution would be to compress the file before burning it to the DVD.  You'd then have to extract it, however.  If you have a 2+core processor, you can use pbzip2 to compress using all cores:

[http://compression.ca/pbzip2/](http://compression.ca/pbzip2/)

Curious:  What BT client are you using?

---

### Post by mapes12 on 2008-12-28
If the other machine is running Ubuntu then it's very easy to connect them and transfer over wifi or wired connection. Here's the Howto. Look at post #2 from SpaceTeddy: [http://ubuntuforums.org/showthread.php?t=793308](http://ubuntuforums.org/showthread.php?t=793308)

---

### Post by 3rdalbum on 2008-12-28
> **Rolcol said:**
> The file is most likely allocated with NULLs therefore there's a lot of redundancy.  A solution would be to compress the file before burning it to the DVD.

Excellent solution - as only 4.5 gigabytes of the file actually contains data, only a tiny amount of space would be needed to represent the rest of the file (which should pretty much be just zeroes). If you compress the file, it probably won't be noticeably bigger than 4.5 gigabytes. That's still too big to go on a DVD, but it brings it within the realm of a flash drive.

---

