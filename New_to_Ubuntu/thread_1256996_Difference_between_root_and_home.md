---
title: "Difference between root and home?"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Motorhead Kaze on 2009-09-03
Sorry, but home is inside of root correct?
I just started using a conky on my desktop, and a lot of people have the amount of space used/left in Root and Home listed separately...though the numbers are identical. Why would anyone do that? Are they not always pretty much the same?

---

### Post by wojox on 2009-09-03
Some people make a separate partition for home.

---

### Post by Tibuda on 2009-09-03
See [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

It is good to have it separated. If something goes wrong with the system, you only have to reinstall to the root partition, keeping all your personal data safe.

---

### Post by Paqman on 2009-09-03
> **Motorhead Kaze said:**
> Are they not always pretty much the same?

The conceptual difference is that /home is owned by the users, while everything else is owned by the system. Plus, as mentioned, they're often on completely separate partitions.

---

### Post by lovinglinux on 2009-09-03
Also check this [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

In Linux, you can mount partitions inside partitions. For example I have a separate home too, which is great to install Ubuntu from fresh without loosing my settings. But I also have a folder inside home called "videos", which is actually a different partition on a different hard drive. Inside "videos" I have another partition, for TV recordings. So you can organize different hard disks and different partitions the way you like it. You are not obligated to set a new hard drive as H:, I: or Z: :)

---

### Post by Motorhead Kaze on 2009-09-05
A cylon penguin! Awesome.

Well now I am glad I asked. I can install fresh without losing my settings...ok, that is just a smokin' idea. Thank all of you for responding, and thanks too for the links.

Peace

---

### Post by lovinglinux on 2009-09-05
> **Motorhead Kaze said:**
> A cylon penguin! Awesome.

They have a plan... :)

> **Motorhead Kaze said:**
> Well now I am glad I asked. I can install fresh without losing my settings...ok, that is just a smokin' idea. Thank all of you for responding, and thanks too for the links.

Peace

Also check the Umarks extension on my signature. It simplifies the process of installing applications all over again, after a fresh install.

---

