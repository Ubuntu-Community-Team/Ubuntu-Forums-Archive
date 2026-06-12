---
title: "Unison, Cron and multiple directories"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by Twizzle on 2009-11-12
I have just started to play with Unison to enable me to sync folders between my server, laptop and PC.

I currently have three profiles, Music.prf, Documents.prf and Photos.prf which are basically along the lines of:

# Unison preferences file
root = /home/john/Documents
root = /home/john/SERVER/Backup/Documents

They all work if I run them individually but I would like them to run in the background every hour say to ensure I have an up to date system

I have made my crontab as follows:

# m h  dom mon dow   command
01 * * * * /usr/bin/unison -batch "Documents"
20 * * * * /usr/bin/unison -batch "Photos"
30 * * * * /usr/bin/unison -batch "Music"

but am wondering if this is a bad way to set it up. As I understand it, this will run the Documents profile at a minute past the hour, Photos at 20 minutes past etc.

What will happen though if for some reason the Photos profile takes longer than 10 minutes? Will it then fail or can it run two simultaneously?

Im also a bit worried what might happen if I loose connection to my server - will it fail or just assume the folder is empty and try to fill it / delete the contents?

---

