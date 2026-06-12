---
title: "wifi/network transfer control"
date: 2016-07-16
forum: Networking &amp; Wireless
---

### Post by alain.roger on 2016-07-16
Hi,

on my laptop i use wifi connection for my network, so to connect to router.
I have a firewall on my laptop and on my router, however when i check how many GB/Mb of data are transfered in Upload/download i would like to be sure that noone is downloading something my my laptop.
immediately after laptop starts i already have more than 30Mb of download and around 10MB of upload.

In 15 hours i noticed around 4/5 GB of upload and almost 2Gb of download which is weird from my point of view.
Ok i can understand that if i download a file from my NAS, it can increase download or if i store something on my NAS... but not with such high values.

How can i know which files are downloaded/uploaded to/from my laptop ? can i create a log or a list in order to understand what does it means ?

thx

---

### Post by Keith_Helms on 2016-07-17
A lot of the network activity may not actually be related to a file.  Some things going on that come to mind are the system checking for updates, the system synchronizing the clock with network time servers, instant messaging apps such as pidgin talking to a server, and so forth.

If you want to check for files that have been updated recently, you could run a command like this:
```
find /home/userid -user yourid -cmin -10 2>/dev/null | xargs ls -ld
```

That would show you any file changed in the last 10 minutes (-10) under your home directory and owned by your ID.  Piping it to ls -ld lets you see the timestamp.

---

