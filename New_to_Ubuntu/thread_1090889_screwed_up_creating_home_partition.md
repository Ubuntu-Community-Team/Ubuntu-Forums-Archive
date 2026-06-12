---
title: "screwed up creating home partition"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-03-08
i tried to create a home partition using this guide [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)  but no matter what i do i can't get past the login screen is there anything i can do please help i don't want to have to reinstall if at all possible

---

### Post by Kareeser on 2009-03-08
We need error messages to begin diagnosing your problem...

---

### Post by mamamia88 on 2009-03-08
fair enough be right back

---

### Post by mamamia88 on 2009-03-08
yes it said user mamamia88 home folder is set as _ which appears doesn't exist.

---

### Post by jimi_hendrix on 2009-03-08
try a reinstall?

what version are you running

---

### Post by mamamia88 on 2009-03-08
8.10 don't really feel like reinstalling maybe ill test out another distro till 9.04

---

### Post by itlarson on 2009-03-08
Are you getting the command prompt?  If so, you should be able to change the home directory from there. The command "usermod -d home_dir" (where home_dir is the name of the home directory you want) should set your home directory.  First you should make sure the directory exists, though.  If you are getting a loggin prompt instead of a command prompt, that's another can of worms, unless you have another user.

---

### Post by jimi_hendrix on 2009-03-08
> **mamamia88 said:**
> 8.10 don't really feel like reinstalling maybe ill test out another distro till 9.04

try 8.04

---

### Post by presence1960 on 2009-03-08
> **mamamia88 said:**
> i tried to create a home partition using this guide [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)  but no matter what i do i can't get past the login screen is there anything i can do please help i don't want to have to reinstall if at all possible

Did you read the disclaimer? I believe I had a similar problem using that how to. I wound up doing a clean install creating a separate /home partition. I had /home backed up to an external USB HDD so I lost no data.

---

### Post by itlarson on 2009-03-09
I would boot from a live cd and try mount the drive partitions to see if the data is still there.

---

