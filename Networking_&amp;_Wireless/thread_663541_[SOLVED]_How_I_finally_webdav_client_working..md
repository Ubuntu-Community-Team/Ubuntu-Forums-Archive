---
title: "[SOLVED] How I finally webdav client working."
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by webdr on 2008-01-10
**Objective: **
I wanted to use my hosted web server as though it were a locally mounted drive on my laptops.
My hosting provider has webdav services installed on the server, so all I needed was to get the client working on my laptop.

It didn't turn out to be nearly as straight forward as it was for me in XP or osX.
I would point nautilus to dav or davs://<hostname:2078>, etc.
Prompts for logins seemed to go smoothly, but nothing seemed to work, nautilus would claim it wasn't a folder.

**SOLUTION**
So here's what it took to get this working for me:

> sudo apt-get install davfs
> sudo mkdir /media/webdrive
> sudo mount -t davfs [https://xxxxx.net:2078](https://xxxxx.net:2078) 
/media/webdrive
(Note: replace xxxxx.net with your webserver url)
answer prompts for username and password
VIOLA! I now had an encrypted ssl connection to my webserver that participated with my system as though it were a local drive mount.

For my next trick, I will be working out a method to synchronize my /home/ to the webdrive so my home is now 'iron' agnostic.

I hope this helps, I know this was something I've been trying to get working off and on for about 6 or 8 months now, and I am glad if this save you time.

WebDr
Mark Williams

---

### Post by mikemis on 2008-04-22
Small edit:
```
apt-get install davfs2
``` works if ```
apt-get install davfs
``` will not.

---

### Post by trebor79 on 2008-05-11
Your solution worked to mount it and display the contents of the web drive. But I'm unable to copy files via drag and drop into the web drive. It gives me the following error when dragging an image from the Documents folder:

```
Error opening file '/media/webdrive/Screenshot-1.png': Permission denied
```

I'm running Hardy Heron (8.04), btw. Any suggestions? I'm new to permissions and networking.

---

