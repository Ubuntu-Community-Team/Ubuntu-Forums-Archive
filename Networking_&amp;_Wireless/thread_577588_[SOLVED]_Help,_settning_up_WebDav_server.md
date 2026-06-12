---
title: "[SOLVED] Help, settning up WebDav server"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by ollebolle on 2007-10-16
Hi!

Me and my friends have lots of photos that we want to share over the internet.

Back in the days when i was a windows user, I had an FTP-server running, and it worked, but i don't like FTP. WebDav is much cooler 8)

I have a small server running Ubuntu 6.06, and I want to set up a WebDav share that my friends can access from their computers so we can share our photos and files.

So, I found this guide:

[http://ubuntuforums.org/showthread.php?t=119228](http://ubuntuforums.org/showthread.php?t=119228)
I followed the webdav-part of this guide, and got some things working:
This is my server:
[http://85.228.32.54/davhome/](http://85.228.32.54/davhome/)
I can browse this with my webbrowser, so: Apache is working.

I want to connect to my server from a windows computer like they do in this guide:
[http://blog.dreamhosters.com/kbase/index.cgi?area=2913](http://blog.dreamhosters.com/kbase/index.cgi?area=2913)

That seems so cool 8)

But I can't do that:(. I have tried to connect both from linux and windows...
If anyone want to try, the username is "test" and the password is "fish"


Does anybody know what's wrong, and what to do to make my webdav server running :?:

Thanks! 

Olle Norell in Sweden

---

### Post by aos101 on 2007-10-17
Webdav seems to be working fine for me (and I've never used webdav before).  I just browsed to webdav://85.228.32.54/davhome/ in Konqueror under Kubuntu, logged in and uploaded webdav_test.txt

Edit: You've got a nice upload speed as well for a broadband connection - I can pull nearly 4Mb/sec according to wget,  Makes my 448Kb/sec upload look a bit poor.

---

### Post by ollebolle on 2007-10-17
**Wow! It's working!** I can see your document!
I thought it didn't work :)

I think i will try  Konqueror now 8)

Thank you for the help, aos101!

ps. Yes, i like my internet connection! Fiber :)

Webdav is cool 8)

---

### Post by ollebolle on 2007-10-17
Guess what i'm doing more on my server? 
Seeding Linux-distrubutions over bittorrent with deluge bittorrent client :D

Im seeding different versions of Ubuntu Kubuntu Xubuntu, and others... ;)

---

### Post by aos101 on 2007-10-17
Ah thought it might be fiber.  That'll definitely help with seeding the torrents :)

---

