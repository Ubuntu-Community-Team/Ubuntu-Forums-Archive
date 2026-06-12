---
title: "Disk check frequency."
date: 2009-01-16
forum: New to Ubuntu
---

### Post by k3lt01 on 2009-01-16
Is there a way to change the disk check (that comes up in the uSplash screen) frequency from the apparent standard 26 boots to once a week?

The reason I ask is it can come up at inopportune times. If I can get it to check the disk say on a Saturday morning each week then its not going to get bypassed for the next 5 to 10 boots till the next Saturday morning comes.

It wont wreck my life if I can't but hey I thought I'd ask.
Michael.

---

### Post by drs305 on 2009-01-16
tune2fs can change the frequency of the fsck check. You can set the interval to count mounts, days, weeks, etc. 
Refer to:
```

man tune2fs

```

There is also an app that will check the disks on shutdown instead of on boot if that is more convenient. I used to use it. I'll look it up and edit this post if I find the name.

---

### Post by jerome1232 on 2009-01-16
Yes you can check "man tune2fs" for more info.

The way to do it should be like this.

--edited for correct date format---
that's what happens when you glance at the man page too fast :)

```
sudo tune2fs -c 0 /dev/sdxx        # that tells the system to ignore the amount of times the file system has been mounted
sudo tune2fs -i 1w /dev/sdxx       # sets the check to be run once a week
sudo tune2fs -T 20090110 /dev/sdxx # tells the file-system that it was last checked last saturday, so in one week it'll run the check again at boot-up again on saturday
```

---

### Post by k3lt01 on 2009-01-16
> **drs305 said:**
> tune2fs can change the frequency of the fsck check. You can set the interval to count mounts, days, weeks, etc. 
Refer to:
```

man tune2fs

```

There is also an app that will check the disks on shutdown instead of on boot if that is more convenient. I used to use it. I'll look it up and edit this post if I find the name.Thanks drs305.

> **jerome1232 said:**
> Yes you can check "man tune2fs" for more info.Thanks Jerome, that got it except for one things but it was easy to figure out once I knew where to look.

> **jerome1232 said:**
> ```
sudo tune2fs -T 01102009 /dev/sdxx # tells the file-system that it was last checked last saturday, so in one week it'll run the check again at boot-up again on saturday
```

I did the date format like you suggested and it wouldn't work so I checked the man tune2fs page and it said the date format is like this 
```
YYYYMMDD
```

---

### Post by expatCM on 2009-01-17
hmmm ...  I am sure all of this thread is right but it is hard ....

Try autofsck ...  that is easy and it works (you get a gui under System / Administrator).  I think the main advantage is that the disk check is scheduled as the machine powers down and so you are not delayed at all waiting for the check to complete.

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

---

### Post by boof1988 on 2009-01-17
In a pinch, you can use the escape key or delete key(I believe).  This will just delay the check until the next boot.

---

### Post by drs305 on 2009-01-17
expatCM identified the app I was trying to remember. I thought that was the name but it isn't listed in synaptic.

Here is the wiki for AutoFsck. It contains a link to the download:
[https://wiki.ubuntu.com/AutoFsck]("https://wiki.ubuntu.com/AutoFsck")

---

### Post by k3lt01 on 2009-01-17
Thanks one and all, I would mark this as solved if I could, but I cant so I shant. I followed Jerome's suggestion along with the information from "man tune2fs" and now both my disk checks operate in the first boot on the Saturday.

---

### Post by kaivalagi on 2009-02-04
Thanks for the heads up on autofsck...now set to check on shutdown :)

---

### Post by northwestuntu on 2009-03-08
so what would the command be to not have it run at all at boot?

---

