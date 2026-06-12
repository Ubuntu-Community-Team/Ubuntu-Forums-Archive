---
title: "How to make LAN connetion between Ubuntu 7.04 &amp; winXP SP2?"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by sirvaan on 2007-11-25
Hi every1
i am new two ubuntu need some help

I have PC that i install ubuntu 7.04 on it & laptop that running on winXP SP2,I want to make connection via LAN card to share file,printer & internet,my PC connect to internet and PC have printer.I want tu use internet & printer in my loptop from my pc that have ubuntu!
how can I do somthing like that?
I am new on this OS & need a good description  !
thx 

best regard
sirvaan

---

### Post by sirvaan on 2007-12-11
any idea?

---

### Post by sowelie on 2007-12-11
Do you have a router / switch.  I am assuming you have a broadband connection.  If so all you need is a router with a built in switch.  You'll then need to set up samba to share files between your linux and windows box.  Samba is easy to install:

```
sudo apt-get install samba
```

Or you can just go to system -> administration -> shared folders and it'll ask if you want to install samba / nfs.

Then if you go to places -> network, you should see your windows pc listed.  You'll also need to set up a file share on your windows pc.

As far as the printer goes, I am not sure how to do that in ubuntu, I've never attempted sharing a printer in ubuntu.  However, [this]("http://www.watchingthenet.com/connecting-to-shared-printers-on-windows-computers.html") looks like a pretty good article.

If you're looking to go the other way with your printer, [this]("https://help.ubuntu.com/community/NetworkPrintingFromWinXP") looks like a pretty good article.

---

