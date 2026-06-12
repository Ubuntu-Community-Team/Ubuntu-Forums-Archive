---
title: "HDD disappearing and inaccessible after mounting"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by twipley on 2011-07-01
Hello. I have been fiddling to resolve this problem for the biggest part of the day. The totality of my personal files are inaccessible to me right now, and that causes inconvenience to me right now, as some of those files are work related.

The problem is that, under a fresh installation of Ubuntu 11.04, which I have reinstalled several times already, the ext4 partition I want to access disappears from Places > Computer once mounted or opened. The hard-disk icon just disappears.

To make it reappear, I have to go to the "Disk Utility," and unmount it from there. There, the "check filesystem" button reports no problem, though.

I also have tried browsing to the mount point, at /media/storage, but it tells me upon opening that "the folder contents could not be displayed," and that "you do not have the permissions necessary to view the contents of "storage."

I had about the same problem today, where I could not copy files over my data partition, but I figured out it could have been because it was residing inside an extended partition, and moved it out of there into a non-extended, standalone partition. Then, I have reinstalled Ubuntu, and made the necessary updates through the "update manager," but nothing works.

It has been days since I have switched to Linux, and is the only serious problem I have encountered. I have Googled my way around all day, to no avail.

I am staying tuned about here if anybody has any suggestions at all. I have no way to tell it right now because I have no extra disk space upon which to create extra partitions, but upon creating the said (data) partition using "disk utility" earlier I had left the "ownership" mention ticked by default. I think it said something about ownership, or something similar. I have let that ticked on, just so you know.

---

### Post by wildmanne39 on 2011-07-01
> I also have tried browsing to the mount point, at /media/storage, but it tells me upon opening that "the folder contents could not be displayed," and that "you do not have the permissions necessary to view the contents of "storage."Hi, this part of the problem is an ownership issue. You can run this command in a terminal while the drive is mounted to get ownership with read and write previlages.
```
sudo chown -R username:username /media/storage

```

---

### Post by twipley on 2011-07-01
Thanks man, I think that is the right way to do it. Just "gaining the privileges."

```
sudo chown -R <desired_owner_and_group_names> /media/<filesystem_label>
```

The problem apparently was, which I discovered through running

```
ls -l /media
```

, that both user and group ownerships were set to the obscure string of "999."

Hope that is going to help other people searching their way. I wonder how those 999s have gotten set there, though. Should be noted, however, that I have used the "disk utility" software through the "try Ubuntu" disc module to create the then-problematic partition -- leaving "take ownership of filesystem" ticked -- if that has anything to do with it.

Anyhow, warm thanks, my friend, wildmanne39 -- for having come to my rescue. :popcorn:


EDIT: one should chown the lost+found folder back to root:root after using such a recursive (-R) command, though.

---

### Post by wildmanne39 on 2011-07-01
Hi, your welcome,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

