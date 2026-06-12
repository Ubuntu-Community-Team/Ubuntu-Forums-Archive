---
title: "swap partion vs swap file"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by halovivek on 2009-02-26
Hi
i browse the internet and i could figure that instead of swap partion we can use swap file. my question is as below.
1. which one is better swap partion or swap file. i use 4GB ram and i have given 10 GB swap partition.
2. which one gives speed access to the files ?
3. if i want swap file. how to configure and how to do that.

---

### Post by Sirron on 2009-02-26
Have a look at [_http://ubuntuforums.org/showthread.php?t=586345_]("http://ubuntuforums.org/showthread.php?t=586345")

---

### Post by mcduck on 2009-02-26
There's no much of difference when it comes to performance. Considering how little swapping is needed with current amounts of RAM the difference would be pretty mych meaningless.

Swap partition can be shared between multiple Linux installs and could result in less fragmentation (since swapping is limited to a specific partition). Not that fragmentation would usually be much of a problem anyway.

---

### Post by tarps87 on 2009-02-26
I've always used a swap partition with GNU/Linux, I know that windows uses a swap file.
The main advantage I can see is that with a partition if you fill up your normal partition you will still have the full size of the swap partition, I don't know if this is the case with the file version.
The access speed is suppose to be the same.

This may help you to setup a swap file:
[https://help.ubuntu.com/community/SwapFaq#Example%20of%20making%20a%20swap%20file](https://help.ubuntu.com/community/SwapFaq#Example%20of%20making%20a%20swap%20file)

---

### Post by Sirron on 2009-02-26
[swapd]("http://linux.about.com/cs/linux101/g/swapd.htm") sounds like a more elegant solution, if you wanted to use a swap file, as it dynamically creates swap files as they are needed. Of course, as tarps87 rightly points out, if you fill your hard disk you'll end up with no space to use for swap.

---

### Post by billgoldberg on 2009-02-26
With 4gb of ram, I doubt you need to use your swap partition much.

Also, 10gb is way too much. You are just wasting HDD space.

You can resize it to 2gb or 5gb if you use a laptop *(and want to use suspend)*, that's more than enough.

---

### Post by halovivek on 2009-02-27
i am using vmware virtual machine in my system and i have installed windows xp in it. so i have allocated 1GB RAM to operate that one. So i am little bit worry on that.

---

### Post by presence1960 on 2009-02-27
> **halovivek said:**
> Hi
i browse the internet and i could figure that instead of swap partion we can use swap file. my question is as below.
1. which one is better swap partion or swap file. i use 4GB ram and i have given 10 GB swap partition.
2. which one gives speed access to the files ?
3. if i want swap file. how to configure and how to do that.

I have 4 Gb ram and upon careful examination have only needed swap a couple of times. 10 Gb? I would say that is unnecessary unless you are running multiple resource intensive applications at once and your ram is all used up. When I installed originally I had 1.5 times my ram as swap. After I saw I almost never needed swap I resized the swap partition.

---

### Post by brokenLockpick on 2009-02-27
I acutally use no swap at all on my netbook (2GB of ram installed) and haven't had a problem, but then again being what it is it sees pretty light duty.

Scince I assume it's a desktop with 4GB of memory being fairly uncommon on stock laptops you may not be able to get away with no swap, but like many others have said 10gb is rather excessive. I usually follow the 1 to 1 rule equal swap size as amount of ram on desktops and full feature laptops.

---

