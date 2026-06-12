---
title: "disk check at startup"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by frank002 on 2011-01-30
Hello:
  How can I keep Ubuntu from doing the startup disk check? It does this every 28 boot ups or so.
 Thanks.

---

### Post by weedeater64 on 2011-01-30
Probably in init scripts somehwere in

/etc

---

### Post by TechZilla on 2011-01-30
[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)


This post shows how to change the frequency of the checks, i'm sure you can change the frequency to 0.  that usually disables something.    I could be wrong though.

---

### Post by CharlesA on 2011-01-30
You can set it in fstab as well, but IMHO it's not a good idea to turn off error checking.

---

### Post by [Snc] on 2011-01-30
> **frank002 said:**
> Hello:
  How can I keep Ubuntu from doing the startup disk check? It does this every 28 boot ups or so.
 Thanks.

It is actually every 30 boots or 30 days, whichever comes first ...

```
sudo tune2fs -c 0 /dev/hda1
```
With the "-c X", if X=0 acting as "disable", else "days between" so:

```
sudo tune2fs -c 39 /dev/hda1
```
would mean check every 39 days

(samples assuming, the disk is in consideration being "hda1", modify it to the real disk name)

---

### Post by [Snc] on 2011-01-30
> **CharlesA said:**
> ...IMHO it's not a good idea to turn off error checking.

I forgot to mention ;) I wouldn't do that either ... The check is fast and normally people don't even see it.

---

### Post by CharlesA on 2011-01-30
> **'[Snc] said:**
> I forgot to mention ;) I wouldn't do that either ... The check is fast and normally people don't even see it.
Indeed. It's typically very quick if you are using ext4 (which has been the default in Ubuntu since 9.10)

---

### Post by frank002 on 2011-01-30
Thank you all for the quick replies.

---

