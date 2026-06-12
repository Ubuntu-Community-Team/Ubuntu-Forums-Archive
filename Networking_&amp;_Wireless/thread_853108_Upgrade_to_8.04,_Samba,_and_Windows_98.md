---
title: "Upgrade to 8.04, Samba, and Windows 98"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by mrwonx on 2008-07-08
Here's a doozy for all of you:

I set up shares on an ubuntu box for people in the office to dump files. I have 3 shares. 85% of the people connected to it are windows 98 users and rely on it for our daily publication (small town newspaper). I had installed 7.10.

I wasn't in yesterday, and my boss decided that letting it run the update to Hardy was worth trying to see if it would solve another problem we've been having with some of the macs in the building. It finished downloading this morning and we installed it.

Came back fine, and when everyone went to turn on their machines, all the 98 could no longer log in to the shares, while the very few Macs and xp machines can.

We're a few months from upgrading our system, but being that we do things daily, we can't really sit back and say "Oh, it's not working - well, it'll be fixed in a couple months"

Also, I've read and tried most every fix for samba/hardy glitch, and the macs and xp are working, so it seams to be just in talking with the 98's.

---

### Post by superprash2003 on 2008-07-08
are the 98's able to ping the ubuntu machine??whats the error you get when you try accessing \\x.x.x.x ( where x.x.x.x is the ip of the ubuntu machine) from the windows explorer

---

### Post by jetsam on 2008-07-08
Have a look at this post:
[http://ubuntuforums.org/showthread.php?t=815382]("http://ubuntuforums.org/showthread.php?t=815382")

I think it covers two settings in your smb.conf that you'll need to uncomment to let the win98 computers authenticate to Samba.  

HTH...

---

### Post by mrwonx on 2008-07-08
Wow! Thanks. That one did it. Went the day relying on a Windows NT 4.0 server to house everything. 

Give me another 3-4 months, and all the 98 computer will be gone and I won't have to tip-toe around them anymore.

---

### Post by RealG187 on 2009-03-24
[http://ubuntuforums.org/showthread.php?t=815382](http://ubuntuforums.org/showthread.php?t=815382)

I am having trouble with this

---

