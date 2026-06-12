---
title: "Clean install without affecting home partition"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by dndrich on 2009-02-10
Ubuntupals:

I have 8.10 installed with a root partition, home partition, and swap.  When 9.04 come out, how do I install it to root without affecting the home partition?

---

### Post by Dougie187 on 2009-02-10
When you go to install you do it exactly the same as you did before, except you don't repartition anything. Then when you get to the step where it lists all the partitions and you get to choose mount points and stuff you just make the root one / and you have to tell it to format it as well.

---

### Post by HotShotDJ on 2009-02-10
> **dndrich said:**
> Ubuntupals:

I have 8.10 installed with a root partition, home partition, and swap.  When 9.04 come out, how do I install it to root without affecting the home partition?You should be able to do a network upgrade (something like this: [http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Desktops%20(Recommended](http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Desktops%20(Recommended)) ). However, if you want to just reinstall, you'll have to make sure that you manually set up the partitions during the set up.  Make sure you set your home partition as /home and tell the installer NOT to format it.  It is pretty simple.  I've preserved my /home many times, across several distribution for the last 7 or 8 years. :)

---

