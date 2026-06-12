---
title: "I have a couple of questions..."
date: 2009-03-11
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-03-11
Ok here goes... I had done a complete install Ubuntu 8.10 (only thing on my computer) It ran great for awhile and then all of a sudden it just went to crud!!! No INTERNET connection for about a week.

I had installed some stuff, compiz, and the like but everything was from repositories... then it went to crud, so after a week of barely a connection when I could connect at all to no connection I finally decided to do a complete reinstall. I wiped HD clean and reinstalled Ubuntu 8.10 again. No bells and whistles just the basics, and everything is working fine again.

My questions are any Ideas without going into great detail what may have caused this? and Is there a way I can clean my system of any junk I or someone else may have downloaded?

---

### Post by cariboo on 2009-03-11
There was probably a kernel update with new drivers. You don't specify how you connect, wired or wireless, so it is pretty hard to tell.

If you have other people using your computer, you should setup a limited account for them, so they don't install any software anywhere but in their home directory.

Jim

---

### Post by Leo Dragonheart on 2009-03-11
> **cariboo907 said:**
> There was probably a kernel update with new drivers. You don't specify how you connect, wired or wireless, so it is pretty hard to tell.

If you have other people using your computer, you should setup a limited account for them, so they don't install any software anywhere but in their home directory.

Jim

Yea sorry about that I connect wireless usb, and no one else uses my computer but I don't always download and install stuff the right way. Still new to that. That is why I was wondering if there is a way I can clean up after myself when I make a mess of things...

---

### Post by Leo Dragonheart on 2009-03-23
Can anyone tell me how I can revert back to a previous kernal in ubuntu 8.10 please?

---

### Post by hyper_ch on 2009-03-23
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by anewguy on 2009-03-23
I'm going to suspect something here, so bear with me if I'm wrong.  I suspect you had to follow some procedure for installing a driver for your USB wireless.  I'm also going to suspect that a kernel update was done in one of the automatic updates after you had installed your USB wireless.

Given those 2 things, a new kernel will sometimes "wipe out" a non-Ubuntu delivered driver.  Basically, in such cases you just reinstall your driver.

So, watch for new kernels in the update process, and when you see one remember to reinstall your wireless driver afterwards.

dave :)

---

### Post by billgoldberg on 2009-03-23
> **Leo Dragonheart said:**
> Can anyone tell me how I can revert back to a previous kernal in ubuntu 8.10 please?

During boot, press "esc" to view the grub options.

Then you can start Ubuntu using an older kern**e**l.

---

