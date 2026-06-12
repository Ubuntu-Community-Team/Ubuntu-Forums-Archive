---
title: "USB doesn't resume after suspend"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by crf on 2009-07-20
When the computer resumes after suspend, the usb doesn't get any power. How do I restart usb without rebooting?

Before I updated Ubuntu to 9.10, I would do lsmod| grep usb, and rmmod all that came up, and finally modprobe to start them again. This would bring the usb mouse back.

But now when I do lsmod usb, there is nothing running already.

---

### Post by AClark on 2009-07-20
Here's a post describing a similar problem & solution
[http://ubuntuforums.org/showthread.php?t=1061810](http://ubuntuforums.org/showthread.php?t=1061810)

I have a similar problem on a Thinkpad - since a recent kernel update all USB is dead on resume from suspend on 9.04.

I have seen the question of how to restart USB without rebooting asked several times on the forums but haven't yet seen an answer that worked for me.

I had the same symptom on an old HP laptop and it turned out to be caused by the ethernet driver & also the wireless driver

When I added them both to the SUSPEND_MODULES list that problem was solved.

Good Luck & let us know how you make out.

---

### Post by theozzlives on 2009-07-20
> **crf said:**
> When the computer resumes after suspend, the usb doesn't get any power. How do I restart usb without rebooting?

Before I updated Ubuntu to 9.10, I would do lsmod| grep usb, and rmmod all that came up, and finally modprobe to start them again. This would bring the usb mouse back.

But now when I do lsmod usb, there is nothing running already.

9.10 is only in Alpha 2, you mean 9.04 or you posting in the wrong place?

---

