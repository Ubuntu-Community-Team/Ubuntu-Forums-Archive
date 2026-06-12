---
title: "Live CD ISO updated?"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by Paul T. on 2010-11-06
Hi,

due to HD problems I'm going to have to do a clean install of Ubuntu onto a new HD; now my 10.04 LiveCD was burnt many months ago since then there have been numerous updates so if I download the latest ISO will it have the updates included? 
Or should I download 10.10 instead?

---

### Post by Elfy on 2010-11-06
If you download 10.04 it will be 10.04.1 - there are likely to be some updates to be applied still though.

If you download 10.10 - it also will have updates to apply.

If you can access your existing 10.04 install from the livecd there is nothing to stop you backing up the packages in the cache and then copying them to the new 10.04 install before you update that new install.

---

### Post by P4man on 2010-11-06
You can also download a daily build for 10.10 which contains all updates:
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

As for which version is best.. try before you buy :)

---

### Post by Paul T. on 2010-11-06
Thx for the quick replies.
I can still use my current installation but have been getting warnings from the SMART data about read/write errors so have bought new HD.
10.04 has worked flawlessly so I would prefer to stick with what works for me rather than risk upgrading so will download 10.04.1.

I recently did a system recovery on a friends laptop using the recovery partition; it took about an hour to re-install Vista, but _2 DAYS_ to download and install all the updates, drove me mad with all the re-starts etc.
I was looking to avoid that with Ubuntu.

---

### Post by P4man on 2010-11-06
Someone has to mention it...

*backups*

:)

If you can still read your current install you could just clone it to your new drive, although that might no be a terribly good idea if the disk has gone bad enough to produce read errors.

---

### Post by Paul T. on 2010-11-06
> **P4man said:**
> Someone has to mention it...

*backups*

:)

If you can still read your current install you could just clone it to your new drive, although that might no be a terribly good idea if the disk has gone bad enough to produce read errors.

Yes I have backed up everything :P

Never had much success with cloning drives, usually end up with errors due to corrupted files etc. But thx for the advice.

---

### Post by coffeecat on 2010-11-06
Don't forget what forestpixie mentioned. The downloaded .deb files for all the 10.04 updates will be in /var/cache/apt/archives/ if you haven't cleaned them out. You could back those up, do a fresh install of 10.04, put the .debs in the new cache and then at least you won't have to download all the updates again.

One problem with that is if the old drive is failing, you may get some corrupted deb packages.

---

