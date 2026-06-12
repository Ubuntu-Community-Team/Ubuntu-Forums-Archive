---
title: "Updating my kernel"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by karthick87 on 2010-06-08
Currently i am using the following kernel,

```

karthick@Ubuntu-desktop:~$ uname -r
2.6.32-21-generic

```

How to upgrade the kernel..?and is it necessary to upgrade the kernel..?In what case kernel upgrade is needed..?

---

### Post by pizza-is-good on 2010-06-08
If a new kernel revision is published, the update manager will install it. As long as all your hardware is working fine, you don't really need to be using the new kernel. When the new one is installed, grub will show you all the kernels you have installed and give you the option of which one to use.

---

### Post by stewie17 on 2010-06-08
Okay, so it's alright to have an older kernel? My kernel is '2.6.28-18-generic'

---

### Post by pizza-is-good on 2010-06-08
> **stewie17 said:**
> Okay, so it's alright to have an older kernel? My kernel is '2.6.28-18-generic'

Yeah, as long as it works, there is no reason to change it. Back when I was using 9.04, I did a kernel update, which messed up several things. So I just kept booting from an older kernel, working flawlessly.
I always use the new ones as soon as they are available and the Update Manager downloads them, but that is just my particular 'philosophy'.

---

### Post by stewie17 on 2010-06-09
Thanks pizza. I just had an update a few days ago, but saw that other people had newer version. Being somewhat new to linux I wasn't sure if I should do anything about updating the kernel.

---

### Post by karthick87 on 2010-06-09
Fine,and can you tell me the way to update kernel?

---

### Post by pizza-is-good on 2010-06-09
> **stewie17 said:**
> Thanks pizza. I just had an update a few days ago, but saw that other people had newer version. Being somewhat new to linux I wasn't sure if I should do anything about updating the kernel.

No problem. Hope you enjoy linux. I started out about a year and a half ago. You learn tons in such a long time, but I sill have much to learn about.

> **getyourkarthick said:**
> Fine,and can you tell me the way to update kernel?

When there is a new revision available, the update manager will install it. My system was updated to 2.6.32-22-generic last week.

If you are using lucid, the update manager does not pop up very often, if at all, so you would have to run it manually. System >> Administration  >> Update Manager.
It should be there.

I will again say that there is no urgent need to update the kernel as long as all your hardware is working fine. Security updates are what is important. It doesn't hurt to update the kernel, but if your computer does get messed up, you can always boot from a previous kernel.

Hope this helps.

~pizza

---

### Post by snowpine on 2010-06-09
> **stewie17 said:**
> Okay, so it's alright to have an older kernel? My kernel is '2.6.28-18-generic'

You're probably running 9.04 Jaunty, in which case 2.6.28 is the correct kernel.

---

