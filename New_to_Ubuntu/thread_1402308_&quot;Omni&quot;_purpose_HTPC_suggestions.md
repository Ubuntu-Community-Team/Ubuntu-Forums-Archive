---
title: "&quot;Omni&quot; purpose HTPC suggestions"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by ilya_hhjj on 2010-02-09
I've been thinking of turning my current computer into an "omni" purpose HTPC. (if that word even exists) I don't want to waste so much processing power so here's a list of things I want it to do: 
-TV HDPVR
-HTPC
-Home network server
-Firewall/gateway
-Wireless access point
-Printer server
-Filestorage
-Oldschool Arcade
-Folding computer
-Maybe even some modern games

The computer is a q6600 o/c to 3.3ghz with an 8800gt so I'm pretty sure it can handle this and more.

I was originally thinking of using mythbuntu and virtual boxing puppy arcade but then I realized, how am I going to use this as a wireless router/gateway/firewall and all that?
Should I virtualbox something like ClearOS? But if I wanted wifi router capability wouldn't I need something like Linux LiveCD Router? But then if I emulate the firewall on a virtual machine wouldn't that defeat the purpose of the firewall since the internet connection goes through the main machine?
Or would it be easier to run Clear OS and then install mythtv and emulate puppy arcade?

So if anyone has tried to do something like this before or knows a thing or two about this and would like to make some suggestions that would be appreciated.

---

### Post by jimmy the saint on 2010-02-09
[http://www.howtoforge.com/perfect-server-ubuntu-9.10-karmic-koala-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-9.10-karmic-koala-ispconfig-2)

A good starting point with the server tasks.  Everything else can be added up from there.

---

### Post by lijcam on 2010-02-09
I use XBMC on both my media centres with mythtv for TV backend only problem with is there is no TV interface with XBMC so the appear as video steams. A detected front end will be coming up in the few months.
To install XBMC.
```
sudo add-apt-repository ppa:team-xbmc && apt-get update
sudo apt-get install xbmc
```For games I found Play-on-Linux makes installing windows games on linux dead easy
[http://www.playonlinux.com]("http://www.playonlinux.com/")

---

### Post by jward3010 on 2010-02-09
I would never recommend THAT much on a single machine even if it was quad core with 16GB's of RAM. At the end of the day, even with heaps of processing power, there is only one CPU and one bunch of RAM and everything vying for it. The first 7 things might be ok together but the last three should be separate.

---

