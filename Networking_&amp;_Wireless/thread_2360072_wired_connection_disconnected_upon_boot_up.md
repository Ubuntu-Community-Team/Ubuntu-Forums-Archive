---
title: "wired connection disconnected upon boot up"
date: 2017-05-01
forum: Networking &amp; Wireless
---

### Post by russkyca on 2017-05-01
Ubuntu Gnome, 17.04

I dual boot so I'm not always using the OS...plus, I have had some freezes or crashes.... anyway, whenever I have to boot into the OS, my internet suddenly is not connected.   This is a recent problem/issue.

I have no idea what to do or how to troubleshoot it.... 

I did find out a command brings it back.

I run:

sudo systemctl restart systemd-resolved

I shouldn't have to run a command to start up my connection every time so I am hoping someone recognizes what's going on and knows how to fix it or can at least offer some ideas ....and some tests to try or something?

---

### Post by russkyca on 2017-05-02
I fixed this problem for now.  I had messed around with my config settings.   In my /etc/NetworkManager/NetworkManager.conf file, I added a line 'dns=none'

When I took that line out, my internet connection was working when I booted up.   I was trying to fix a vpn issue and following various 'tips' and 'try this' steps by people in vpn forums.   I shouldn't have done that one. ;)

Anyway, it is fixed *for now* - aka at the moment.   Will keep fingers crossed.

---

