---
title: "Secondary drive mount issues..."
date: 2010-06-23
forum: New to Ubuntu
---

### Post by akelsall on 2010-06-23
I have a secondary drive that isn't mounting quite the way I expect. When I boot and look in the /media directory, none of the three partitions are showing up. 

The odd thing is if I go to Places, they show up there, and if I access them from under Places, THEN they appear on my desktop (as an icon), AND, they appear in the /media directory. 

Is there a way to mount these upon boot, and if so, how do I do that?

Thanks,

Andy

---

### Post by cariboo on 2010-06-23
You can mount the partitions on boot, by adding them to /etc/fstab. Have a look at this [page]("https://help.ubuntu.com/community/Fstab") for more on fstab.

---

### Post by akelsall on 2010-06-27
Thanks cariboo907. That's exactly what I needed. Working great now!

---

