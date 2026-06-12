---
title: "slow slow ftp over local LAN"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by jynyl on 2008-02-16
Transferring files between Linux boxes on my local LAN (wired, not wireless) is very slow.  The client appears to go slowly through each of the files selected for download, one by one, taking about 30 to 60 seconds each.  After this, it does the data transfer at normal speed (around 10 - 15 MB/s or so).

The Linux boxes are running Kubuntu 7.10, and the server is running pure-ftp.  Earlier versions of Kubuntu didn't have this problem.

TIA

Peter

---

### Post by couzin2000 on 2008-02-16
This sounds like a problem with the application - the FTP client itself. Which one are you using? And, did you try another one?

Also, when you log in to the server, are the files you're trying to download symlinks? (Meaning, in the server, you would have the files in one place, but you click on the symlink to download the file). I've seen certain machines take a lot of time just trying to figure out the symlink.

Last, what you can do is open passive ports on your server box, which *could* shorten the whole ordeal - but I think that in your case this sounds more like the server is taking its sweet time accepting the client request for a file. My guess is by either trying a different client or a different server software, you'll end this problem. If you decide to switch server software, give vsftpd a try - highly reliable.

---

