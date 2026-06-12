---
title: "Double install ?"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by superharas on 2009-11-02
Hi,

Please give me an answer to this question, I really need help!

Now, had Ubuntu 9.04 before, now I am going to install 9.10 on my computer,
But this time I would like to install it on another partition, which is a 20 GiB partition.

**Now, how can I delete ubuntu from that other partition**(which was just 2.5GiB - I need more space, so I would like to have 20GB in one partition to keep it easy) **?**

I haven't clicked on the install button yet, I hope I get a quick answer.

---

### Post by kansasnoob on 2009-11-02
In order to help you I'd need to see a screenshot of Gparted. It's in System > Administration.

---

### Post by mikewhatever on 2009-11-02
You can use the Partition Manager under System->Admin. It's an easy graphical tool. There is also an option of deleting a partition during manual partitioning, which is the path you'd have to take, since you plan installing on an existing partition.

---

### Post by superharas on 2009-11-02
Oh, OK.
So, do I just delete the partition, or what ?

---

### Post by danastasio on 2009-11-02
well, deleting ubuntu is as simple as system->administration->gparted
but in order to completly remove it, you also need to reconfigure how grub will boot your computer, but if your just going to re-install ubuntu, then it wont be nessicary as grub will just be re-installed anyway.

---

