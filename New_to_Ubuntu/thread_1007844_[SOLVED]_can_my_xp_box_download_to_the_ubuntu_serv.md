---
title: "[SOLVED] can my xp box download to the ubuntu server?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-10
If I set up samba server on ubuntu 8.10 Can I then "on my xp box" choose to download files from the net directly to the ubuntu server instead of saving them to the xp box? Thanks

---

### Post by Hospadar on 2008-12-10
Yes, but what will probably happen in reality is that they will get cached to your XP machine and then moved to the ubuntu machine, so the time savings will probably be minimal.

If you are bittorrenting stuff, I'd suggest a webui for a bittorrent client to be run on your server.  Deluge has a really nice web UI that let's you control it from a web browser.  Transimission also has a great webUI called clutch, but it's a little more difficult to set up.

If you're just straight downloading files, probably the quickest way to get it done is by logging into your server with ssh (with a client like putty) and using wget (try "man wget" for info, but basically "wget <url of file to download>")

If it's a big file and you don't want to be logged in the whole time it's running, try "nohup" it let's you start a command and then logout and it will keep running until it's done.

L-tron

---

### Post by pshootr on 2008-12-10
> **Hospadar said:**
> Yes, but what will probably happen in reality is that they will get cached to your XP machine and then moved to the ubuntu machine, so the time savings will probably be minimal.

If you are bittorrenting stuff, I'd suggest a webui for a bittorrent client to be run on your server.  Deluge has a really nice web UI that let's you control it from a web browser.  Transimission also has a great webUI called clutch, but it's a little more difficult to set up.

L-tron

Thanks for the fast reply. The reason I want to do this is because I use my xp laptop the most, and it has limited space, so basicly I would like to download to a network drive directly. Preferably to the ubuntu server.

---

### Post by jimmy the saint on 2008-12-10
I would recommend deluge if you want to go the torrent-to-server approach.  They have seperated the gui from the program in the last version, so you can use one interface to contro the installation on your main box, as well as the installation on your server.  That is perfect for situations where you may want to send large files to the server, but smaller ones to your main box.
[http://deluge-torrent.org/](http://deluge-torrent.org/)

You would install it on the server as well as on your xp box.  You would run the deluge daemon on your server, and control it via the gui on your xp box.  It is a lot simpler than it sounds.

---

### Post by Hospadar on 2008-12-10
> **pshootr said:**
> Thanks for the fast reply. The reason I want to do this is because I use my xp laptop the most, and it has limited space, so basicly I would like to download to a network drive directly. Preferably to the ubuntu server.

You should be fine doing that.  Since your issue is limited space (and not so much speed I assume?) I don't think you have anything to worry about.  The way I suspect XP handles a samba drive is by caching blocks of data locally and then writing them back to the drive a) when your local drive is full  or b) whenever XP feels like it.

The bottom line is that XP probably isn't going to download the whole file to your disk before moving it to the Ubuntu samba drive.  Also of course XP will handle deleting whatever temp data it saves to your local disk in the process, so you don't need to worry about samba transfers taking up local disk space.

---

### Post by pshootr on 2008-12-10
> **jimmy the saint said:**
> I would recommend deluge if you want to go the torrent-to-server approach.  They have seperated the gui from the program in the last version, so you can use one interface to contro the installation on your main box, as well as the installation on your server.  That is perfect for situations where you may want to send large files to the server, but smaller ones to your main box.
[http://deluge-torrent.org/](http://deluge-torrent.org/)

You would install it on the server as well as on your xp box.  You would run the deluge daemon on your server, and control it via the gui on your xp box.  It is a lot simpler than it sounds.

Thanks for the suggestion. I will to check out the new deluge.

---

### Post by pshootr on 2008-12-10
> **Hospadar said:**
> You should be fine doing that.  Since your issue is limited space (and not so much speed I assume?) I don't think you have anything to worry about.  The way I suspect XP handles a samba drive is by caching blocks of data locally and then writing them back to the drive a) when your local drive is full  or b) whenever XP feels like it.

The bottom line is that XP probably isn't going to download the whole file to your disk before moving it to the Ubuntu samba drive.  Also of course XP will handle deleting whatever temp data it saves to your local disk in the process, so you don't need to worry about samba transfers taking up local disk space.

Thank you very much for your replies! I really appreciate it. Actually, my xp laptop is connecting to an older linksys router which only supports 11mbs. So I guess this is going to slow things down alot eh?

---

### Post by rhcm123 on 2008-12-11
> **pshootr said:**
> Thank you very much for your replies! I really appreciate it. Actually, my xp laptop is connecting to an older linksys router which only supports 11mbs. So I guess this is going to slow things down alot eh?

quite actually. On ethernet (1000mbps, both my server and laptop), and the fastest i've pulled is about 100 mbps. Over wifi (54 mbps), i crawl at 3 mbps. Which is why i don't do wifi transfers.

---

### Post by pshootr on 2008-12-11
> **rhcm123 said:**
> quite actually. On ethernet (1000mbps, both my server and laptop), and the fastest i've pulled is about 100 mbps. Over wifi (54 mbps), i crawl at 3 mbps. Which is why i don't do wifi transfers.

Wow, sounds bad for me on a 11mbps router lol. Anyway I was thinking that since a lot of my downloads from the net are below 1mbps, shouldn't the network be able to keep up?

---

### Post by rhcm123 on 2008-12-11
> **pshootr said:**
> Wow, sounds bad for me on a 11mbps router lol. Anyway I was thinking that since a lot of my downloads from the net are below 1mbps, shouldn't the network be able to keep up?

It should, but I wouldent really know, as I have a 20 mbps downstream link (wicked fast, you should get some). But if you are on a slower connection, then the network will keep up fine, assuming it pulls 11 mbps. Which it won't do. It i'll get like 2, max 3. :)

---

