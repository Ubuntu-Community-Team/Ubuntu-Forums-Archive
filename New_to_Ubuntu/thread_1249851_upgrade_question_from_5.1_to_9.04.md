---
title: "upgrade question from 5.1 to 9.04"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by aljoriz on 2009-08-25
Is it possible to upgrade by just using the CD for 9.04 and retaining most of my files?

---

### Post by tgeer43 on 2009-08-25
You cannot upgrade from 5.10 to 9.04 without going through the intermediate releases. Best best is to back up your important files (ie. your home directory) and do a fresh install of Jaunty.

tgeer

---

### Post by kansasnoob on 2009-08-25
I have a thought, but first, is it possible for you to post a screenshot of gparted so we can see your drive/partition layout?

---

### Post by slakkie on 2009-08-25
No, not directly.

You need to install all the intermittent releases.

You will need to upgrade to: 6.06
From 6.06 upgrade to 8.04, from 8.04 to 8.10 and finally 9.04.

Google for EOLupgrades Ubuntu.

It will take you depending on your download speed a day or two. Maybe three.

---

### Post by slakkie on 2009-08-25
> **kansasnoob said:**
> I have a thought, but first, is it possible for you to post a screenshot of gparted so we can see your drive/partition layout?

No need for a screenshot, just paste the output of the following commands.

```

df -kh
cat /etc/fstab
sudo fdisk -l

```

---

