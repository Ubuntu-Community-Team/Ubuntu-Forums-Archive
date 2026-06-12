---
title: "Trying to fix USB Drive"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by crisco552 on 2009-12-04
I bought a Pico C a little more than a year ago and it worked fine until I accidently unplugged it witha window still open, I then made another mistake by reformatting it without waiting. That was in November of last year. I now want to try to get it working again. Here are some facts:
The OS I am using is Ubuntu 9.04
The drive is recognized as "USB Drive"
when I try to open it, it says "Unable to Mount Location No Media in Drive"

if I do sudo fsck /dev/sda1 will that help fix it?

---

### Post by wilee-nilee on 2009-12-04
If there is nothing on it to save try formatting it with gparted.

---

### Post by crisco552 on 2009-12-04
I tried that, It doesn't show up there.

---

### Post by cartisdm on 2009-12-04
> **crisco552 said:**
> I tried that, It doesn't show up there.

Did you try using a liveCD version of GParted or are you working within the Ubuntu desktop?

---

### Post by crisco552 on 2009-12-04
Ubuntu Desktop

---

### Post by cartisdm on 2009-12-04
> **crisco552 said:**
> Ubuntu Desktop

I've always had better luck using the LiveCD version, for me it seems to recognize those picky drives a little better.

You can download the LiveCD [here]("http://gparted.sourceforge.net/download.php")

---

