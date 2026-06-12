---
title: "best multiple pc configuration"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by jt_04 on 2009-02-24
Hello all,

I have a question about the best way to configure multiple PCs on a home network.  I will have 3 computers:

pc#1:  office computer running Ubuntu 8.10, with truecrypts, username = user1
pc#2:  htpc computer with ubuntu 8.10, used for video, music, pictures
pc#3:  laptop with Windows XP

pc#2 will be a new arrival within the next month and I am already wondering what is the best way to configure them all.

Should I create a new user on pc#2 (such as "user2") and logon to it that way, then ssh/samba into PC#1 as "user1" if I need access to any of those files?  

Or should I create an account for "user1" on PC#2 and logon that way?  so then all the pcs would have the same user account on them?

can anyone tell me what is the best way to go so i avoid the typical trial-and-error hassle?

what would you recommend for accessing files and syncing folders across all 3 computers?  just samba?  realvnc?

and does anyone know a good solution for syncing firefox bookmarks/passwords across all 3 computers?

Thanks,
jt

---

### Post by llamabr on 2009-02-24
rsync?

---

### Post by sandyd on 2009-02-24
read here
[http://starangyl.livejournal.com/2486.html](http://starangyl.livejournal.com/2486.html)

for your first comp, add this into the tutorial
set the guest acount to "user1" (youll see this close to the last step, at the part where you change "Authentication mode to "Share"

**EDIT:**whoops, make sure you set the workgroup the same between your ubuntu computers and your xp computers. also, don't do anything with the firewall

---

### Post by jimmy the saint on 2009-02-24
I have a very similar similar setup (minus the XP).  I am trying to get my fiance off of windows vista (which she hates, but is afraid to give up.  Sounds more like a tier 1 substance?), but that has no access to the main network machines.  

Anyway, I setup the box that serves media as the server as well.  I store most files I may need quickly to the server, as well as ebooks and media.  You could do the same with a samba share.  If you want all of your files backed up and available, you could just use rsync to copy them on a regular basis automatically (kill two birds with one stone, backup and avaibalbility).  

In addition to all that, the box also serves music through daapd, plays video to the HDTV, and handles any torrents or large downloads, therby keeping my main box fast and sanppy.  all that on a 300 dell refurb.  Linux is good.

---

### Post by cjv8888 on 2009-02-24
ssh is very easy to use to share files.
and for syncing bookmarks Firefox has an add on called Foxmarks which works automatically once you have registered.

---

### Post by jt_04 on 2009-03-17
thanks everyone for the input.  I'll be using samba to share files back and forth...it's what i've been doing for my winxp laptop and it works good.

> **cjv8888 said:**
> ssh is very easy to use to share files.
and for syncing bookmarks Firefox has an add on called Foxmarks which works automatically once you have registered.


actually, i've been using "syncplaces" to sync my firefox bookmarks between my ubuntu desktop and winxp laptop.  it's easy to use and doesn't require registering or uploading my bookmarks/passwords to some unknown website that I don't trust.  check it out [here]("http://www.andyhalford.com/syncplaces/index.html").

---

