---
title: "host file?"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by stlouis1 on 2007-08-10
i was looking at this thread, i think its pretty much the same issue im asking about

[http://ubuntuforums.org/showthread.php?t=328243](http://ubuntuforums.org/showthread.php?t=328243)

i just wanted to clarify something, because on my windows desktops at home, i use [this]("http://www.mvps.org/winhelp2002/hosts.htm") host file to stop adds and stuff from being loaded, not so much to block spyware....but i have dialup and some adds are killer for my dialup connection

so basically, just wondering if implementing that host file would help me block some of the adds from loading. it wasnt clear to me in the above thread if the host file in linux would work the same as in windows. 

i know i'd oviously have to change the formatting of it, should be easy enough, just need the open office spreadsheet to swap colums and i can export to text, should save some work

---

### Post by kerry_s on 2007-08-10
a host file can make the internet slow, your better off going with firefox adblockplus with the easyelement+eastlist & abp tracking filter for your subscriptions. i use to use the same host block file your pointing to, the thing with host files is that they make the link point to a dead end and dead end's take time to check, the bigger the block file the longer to check.

---

### Post by benanzo on 2007-08-10
I use [this]("http://everythingisnt.com/hosts") *hosts* file to block ads.  Just copy and paste to the bottom of your current /etc/hosts file.  After you're done restart your browser and do:
```
sudo /etc/init.d/dns-clean start
```
To clear your DNS cache so the ad blocking kicks in.

Good Luck!

---

### Post by stlouis1 on 2007-08-10
k cool, so i guess i've got 2 good options here

---

