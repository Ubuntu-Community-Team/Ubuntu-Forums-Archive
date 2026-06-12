---
title: "trying to figure something out"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by blockheadstudio on 2008-12-17
I have put Ubuntu 8.04 on my laptop (orig. Vista)by means of CD. Then I upgraded to 8.10. Runs great! Buuuutttt my laptop orig. had approx. 250Gb hard drive now only 60GB. Where did the rest of my hard drive go? Trying to figure it out but I am stuck. How do I get the rest back. A portion of your hard drive cant just vanish...can it?
Thanks to anyone that can answer this.

---

### Post by drs305 on 2008-12-17
Run these commands to see what you have in the way of partitions and space:
```
df -Th
sudo blkid

```

Did you do a huge delete after the install?

---

### Post by Hospadar on 2008-12-17
you might also try:  install gparted from synaptic and then run it (Alt-F2, "gksu gparted") to have a look at your drives.  Probably when you upgraded/reinstalled there was some strange partitioning happening and some partition didn't get mounted.

Maybe post a screenshot of gparted when it's open.
Furthermore, you could take a look at Applications->Disk Usage Analyzer and see if that sheds any illumination on the topic.

---

### Post by blockheadstudio on 2008-12-17
I tried the df command/ tried the app>disk ann. to see how much space and it showed 60G. I did not try that gparted thing yet thanks.

---

### Post by oldos2er on 2008-12-17
Can you post the output from "sudo fdisk -l"?

---

### Post by icanfly0307 on 2008-12-17
Your Hard Drive may be 250GB. However, if you're dual-booting, you may have allocated only 60GB for Ubuntu and 190GB for your other OS.

---

