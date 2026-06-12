---
title: "How do i sync folders with  usb hard drive connected to router"
date: 2017-10-25
forum: Networking &amp; Wireless
---

### Post by folabiklan on 2017-10-25
Hello.

I have a setup where about 10 computers are networked via LAN to a router.

We have a USB hard drive plugged into the router for realtime sync and backup of documents and files from specific folders on Windows OS

I want to switch some of those computers to Ubuntu, so it is essential that we are able to continue the realtime sync/backup.

How can I do this?

Noob here.

Easy to use software preferred

---

### Post by TheFu on 2017-10-26
**rsync** is the tool. There is grsync too.

If the router is WAN facing, connecting storage to it is a huge security issue.  I wouldn't put storage on a WAN router, period.

---

