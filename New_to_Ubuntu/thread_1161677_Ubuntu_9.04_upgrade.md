---
title: "Ubuntu 9.04 upgrade"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Poincare101 on 2009-05-16
I had 8.04 (Hardy Heron)that was working great and I decided I wanted to upgrade to 9.04 . So, I wrote the alternate installation image and all and I installed it. Everything went fine. But, when I boot it up, after about 45 minutes, it says Segmentation Fault a lot of times and then it gives an address like /dev/something/something and then says abnormal exit a bunch of times. Then, it says Loading linux kernels [ok] and then in the next line it says Loading manual kernels and then it just stays like that.

Can someone please tell me what's wrong?

---

### Post by bodhi.zazen on 2009-05-16
Generally you do not directly upgrade 8.04 -> 9.04, you would go 8.04 -> 8.10 -> 9.04.

Sounds like everything did not go fine, hard to know without the exact error message.

My guess is that it is probably fastest to install 9.04 and restore your data from backup then repair your current install.

---

### Post by Poincare101 on 2009-05-17
But, how would I fix the install?

---

### Post by Ericyzfr1 on 2009-05-17
May I ask why you choose the alternate install as opposed to the classic?

---

### Post by bodhi.zazen on 2009-05-17
> **Poincare101 said:**
> But, how would I fix the install?

So you did a fresh installation ?

What are the error messages exactly and what are you doing to generate them ?

Does the system boot at all ? 45 minutes is a long time to wait for the OS to boot.

---

### Post by egalvan on 2009-05-17
> **bodhi.zazen said:**
> Generally you do not directly upgrade **8.04** -> 9.04, you would go **8.04** -> 8.10 -> 9.04.

Is this true for the **LTS** version?

Or is it LTS -> LTS   (example 5.04 -> 8.04) ?

(I had this info bookmarked, but I can't find it at the moment,
probably named it wrong)

---

### Post by durand on 2009-05-17
If you had the LTS version, you could either go via the release in between, 8.10 or you can upgrade to the next LTS version, which is 10.04, being released 11 months from now.

egalvan, 6.06 was the LTS version, not 5.04.

---

### Post by theozzlives on 2009-05-17
You can't skip versions on an upgrade, I suggest if you don't have a /home partition to back up your data. Do a fresh install, if you have a seperate /home your settings and data will be safe.

---

