---
title: "problems with nfs network"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by r!ots on 2007-12-03
Last week I set up my desktop as a nfs-server and my laptop as a nfs-client using [this guide]("http://ubuntuforums.org/showthread.php?t=249889"). I was able to mount the exported folders, until then everything worked out alright.

But when I started copying files from my desktop pc to the notebook the troubles began. I have a 40 GB music collection on my desktop pc which I want to transfer to my notebook but somehow the speed doesn't stay at a constant level. It starts at around 1.4 MB/s, which would be fine, but after the first 5 or so files are copied it drops to somewhere between 0 and 30 kb/s. Thus it will never finish.
Does anyone have any idea why this happens?


If I boot the desktop PC into w2k and access it from the notebook via SAMBA I get a 3 MB/s speed transfering files to the desktop PC and 1-2 MB/s transfering files from it. Why is there a speed difference between up- and downloading? Is it affected by the size of the files I transfer (the one I uploaded was 2 GB and the downloaded ones were mp3-files which were about 3-10 MB)? Why does the speed stay at a more or less high and constant level using SAMBA and doesn't using NFS? I don't get it.

btw: Do you know a good program to synchronize the content of two folders? So I see which files I got on my notebook and which I still need to put on it from the desktop pc and vice versa?

---

### Post by ClockworkAvian on 2007-12-03
rsync is probably what you want. It doesn't require a nfs/smb mount either.

Note, that it removes items that don't exist in the target that are not in the source. Make sure that you have one "master folder" with everything in it before you try to sync, or back it up if you're cautious.

---

### Post by r!ots on 2007-12-05
If I need a master folder, rsync isn't suited for me since I can't build one without a proper nfs connection.
Any other suggestions??

---

### Post by Friek on 2007-12-05
Try mounting your nfs mount with -o tcp.

---

### Post by r!ots on 2007-12-07
> **Friek said:**
> Try mounting your nfs mount with -o tcp.

That sort of worked for me. At least it stayed at 3 MB/s for a longer time (not sure how long, maybe 1.5 GB)  and then the same thing happened: the speed dropped to nearly zero and didn't come up after aborting and restarting.
Nevertheless I managed to copy my music collection. I used a wired connection on both me desktop and notebook and thus flawlessly transfered the files at a constant 11 MB/s. So I'm happy now.
Although I'm wondering what the problem was with the wireless connection. Where can I see how my wireless adapter is configured? Do you have any suggestion what might be the problem? I mean the same thing has happened with some downloads from the net: they started fast and then the speed decreased gradually to around zero. I thought it was the servers fault, but it seems as if I have a problem with my wireless adapter.
Any help would be great.

---

### Post by netztier on 2007-12-07
> **r!ots said:**
> That sort of worked for me. At least it stayed at 3 MB/s for a longer time (not sure how long, maybe 1.5 GB)  and then the same thing happened: the speed dropped to nearly zero and didn't come up after aborting and restarting.
Nevertheless I managed to copy my music collection. I used a wired connection on both me desktop and notebook and thus flawlessly transfered the files at a constant 11 MB/s. So I'm happy now.
Although I'm wondering what the problem was with the wireless connection. 

Wireless and servers don't always play well with each other, especially if both client and server are on WiFi and even more so if NFS(-over-UDP) joins the game. Running NFS-over-TCP helps a bit to mask the effects that make NFS-over-UDP suffer badly on a saturated WiFi network.

See also this posting and thread, and the thread linked in there:
[http://ubuntuforums.org/showpost.php?p=3883185&postcount=5](http://ubuntuforums.org/showpost.php?p=3883185&postcount=5)

best regards

Marc

---

### Post by r!ots on 2007-12-15
Well, I already use a wired connection from the router to the server. Only my notebook is connected via WLAN, but I'm still having problems copying files.
Yesterday I was copying a 800 MB file from the client to the server using tcp and the speed was very inconsistent. It varied from 0 to 4 MB/s, staying at one bitrate only for a short time. That means it only stayed at 4 MB/s for 5 seconds dropped to 12 kb/s and up to 700 kb/s and down again and so forth.
Why doesn't it stay at a constant speed?

---

