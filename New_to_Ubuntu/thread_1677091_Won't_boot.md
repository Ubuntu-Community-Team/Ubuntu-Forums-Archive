---
title: "Won't boot"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by Pirate Zoro on 2011-01-28
I recently installed Ubuntu 10.4 on my Asus Eee PC 1001 netbook, and loved it. It worked like a dream, making my netbook work better than straigh out of the box. Then upgraded to 10.10. It worked perfectly for that whole day, until I logged off and shut down the computer. In the morning, when I tried to turn it on, it wouldn't boot. What comes up is this DOS looking login prompt, that just opens a terminal. That happened a couple times, but more often then that, I didn't get anything at all, just black.What do I need to do to correct this? Is there a fix? Do I need to reinstall the os? Please help

---

### Post by runeh76 on 2011-01-28
Hi
Try this:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by fabricator4 on 2011-01-28
Without knowing what error messages you're getting no-one can guess at what the problem may be.

I can only suggest that you revert to 10.4 and do a fresh install because:

A: It the LTS release and...

B: You know it works perfectly.

---

### Post by mharrison on 2011-01-28
I agree, I would do a fresh install of 10.04.  If you really want to try out 10.10 I would suggest booting to it through the live cd/usb and testing it that way.  Even though it has improved, I still avoid upgrading distro versions through the Update Manager and just simply backup and reinstall.

---

### Post by Rubi1200 on 2011-01-28
Hi and welcome to the forums Pirate Zoro :-)

What graphics card do you have installed?

This may simply be a graphics issues which can be fixed with a few commands, thus negating the need for a complete reinstall.

---

### Post by Pirate Zoro on 2011-01-28
I did a clean install, and now it's working perfectly. I assume there was a problem with the upgrade, but the install fixed it. Thanks anyways, guys, it was appreciated :D

---

### Post by Rubi1200 on 2011-01-28
You are welcome, glad you got it sorted out :-)

---

### Post by runeh76 on 2011-01-29
Good that u get it working.
Now when its working, u should create another account (user without admin rights), so in the future if u mess it up, u have ur admin-account in safe. When u are log in as user, u can allways temporary change (user) to admin group, if u need update or install something.
And there is really good backup programs, if u google a little ;)
Enjoy Linux!

---

### Post by theozzlives on 2011-01-29
@Pirate Zoro, please mark this Thread as solved so people don't try to hijack it.

---

### Post by Pirate Zoro on 2011-01-29
> **theozzlives said:**
> @Pirate Zoro, please mark this Thread as solved so people don't try to hijack it.

It is marked as solved though

---

