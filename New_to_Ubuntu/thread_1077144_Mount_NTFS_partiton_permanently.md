---
title: "Mount NTFS partiton permanently"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by longtom on 2009-02-22
I know I have done it before, but I'm searching through my old threads and can't find a solution...:(

How can I mount my NTFS partition permanently.  I just reinstalled Windows and I'm confused...again.

regards

longtom

---

### Post by sisco311 on 2009-02-22
[http://psychocats.net/ubuntu/mountwindows]("http://psychocats.net/ubuntu/mountwindows")

---

### Post by longtom on 2009-02-22
wow - you are fast.  I have done the NTFS tools thing.  After restart drive was still unmounted again.

thanks for the link

longtom

---

### Post by Kellemora on 2009-02-22
Hi LongTom

I may be wrong about this, so don't use it unless someone verifies that it's correct.

I had a problem getting mounts to stay after a reboot too, but we fixed it, and I'm not very good with keeping understandable notes.
As in, when the writing cools down I can no longer read it, hi hi.....

It seems like (and I hope somebody fills in the blanks here)
I had to in terminal type 
```
chmod 644 .dmrc
```
and then
```
chmod 700 /home/user
``` (user is your user name of course)

We also made a change of some type in FStab, but I just looked and didn't find it anymore, since we now use a data file server instead of individual drives scattered around the place.

TTUL
Gary

---

### Post by longtom on 2009-02-23
Hi Gary,

thank you.  You know - I got it going before with an entry in fstab - and that really puzzled me - as me thinking cools down - similar to your writing...;)

However - somehow I got it right - with a little help from people here - to id my NTFS drive - checked that with what I had in my fstab - changed sdb1 to sdb2 et voilá - it worked.  Partition got itself a new name after reformating with XP....little things one (well I anyway) doesn't think about as soon as necessary.  Need to get more "streetwise" in a Ubuntu kind of way, I guess.

But as long as you guys are here to back me up - I'll be just fine.

Greetings

longtom

---

