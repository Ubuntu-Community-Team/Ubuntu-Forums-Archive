---
title: "NTFS or EXT3 and Samba on Home Network"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by Drunky on 2008-04-29
I'm beginning to setup a home network and I need some advise.

I have two computers; one is running Ubuntu server only, the other is dual boot with Windows and Ubuntu Studio.

I would like to have the server computer, which is already a web server, as a file server that all computers (Linux and Windows alike) can use.  This would store pictures, music, movies, documents, Ubuntu Studio music for long term storage, et al. on a dedicated network hard drive.

Additionally, I would like to use the Linux only machine to use as a backup using cron on an dedicated backup drive. This would backup the various items stored on the network drive at various intervals.

At least that is the current plan.  But being inexperienced in networks I'm not sure which is the better course to pursue, having the network and backup drives as NTFS or using EXT3 and Samba.

Any advice or opinions?

---

### Post by jetsam on 2008-04-29
Since your server and backup jobs will be run in Linux, you'll get better performance and functionality using ext3.  You'll run into fewer compatibility problems as well.

---

### Post by superprash2003 on 2008-04-29
yes.. better use  EXT3 .. ntfs and ubuntu dont go well together

---

### Post by acelin on 2008-04-29
They are just fine, Ubuntu ( well Hardy) does perfect with it. You jsut dont want to have say NTFS on one partition and Ext 3 on another on the same HD - it will mess up badly with time. THe NTFS will become unreadable and you will never be able to format it.

---

