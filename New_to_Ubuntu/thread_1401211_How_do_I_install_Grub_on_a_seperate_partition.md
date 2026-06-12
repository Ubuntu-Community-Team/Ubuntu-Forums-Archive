---
title: "How do I install Grub on a seperate partition?"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by Dullstar on 2010-02-07
I was looking into triple booting Mac, Linux, and Windows and I read that you need to install GRUB in the Windows partition.  How do I do this?  I could ask it in the topic, but I feel asking this part of the question in a seperate topic will make the information easier to find fo anyone else who needs to install Grub on a certain partition for whatever reason.

---

### Post by theozzlives on 2010-02-07
> **Dullstar said:**
> I was looking into triple booting Mac, Linux, and Windows and I read that you need to install GRUB in the Windows partition.  How do I do this?  I could ask it in the topic, but I feel asking this part of the question in a seperate topic will make the information easier to find fo anyone else who needs to install Grub on a certain partition for whatever reason.

I'm not sure, but I don't think you can install MAC OS and Windows on the same box without some kind of virtual software.

---

### Post by Dullstar on 2010-02-07
FYI, it has been done before, apparently.

---

### Post by audiomick on 2010-02-07
It should work on Mac hardware with an Intel CPU.

I have never done this, but:
I would suggest following the Mac instructions to dual boot with windows (must be some somewhere, I know quite a few people who have that set up), and then install Ubuntu last.
As far as I know, Ubuntu / Grub will see the other two OSs and sort things out so they work.

You might want to have a look around in the "mac users" section of the forum, and see if you can find anything there.

---

### Post by Dullstar on 2010-02-07
All I want to know is how to install Grub on the partition I read it has to be installed on.

---

### Post by mechro on 2010-02-07
How to make a Dedicated GRUB Partition...

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

Grub booting from Windows may be possible by "chainloading", but from reading the following I don't think it's worth the grief!...

[http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows](http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows)

---

### Post by Dullstar on 2010-02-10
bump

---

### Post by mechro on 2010-02-11
> **Dullstar said:**
> bump

My post above gives you some links to information about installing Grub on separate partitions. Is there something you don't understand?

---

