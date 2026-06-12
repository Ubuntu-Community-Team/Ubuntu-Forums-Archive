---
title: "messed up partitions"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by webwiller on 2011-02-15
Hi guys,
I messed up my partition and deleted ubuntu by mistake. I work from live cd now. I-ve lost also my win7 cause of the boot loader. Do you know how can I recover my win7 boot loader from ubuntu live cd?

---

### Post by coffeecat on 2011-02-15
If your Windows partition is still there and has the boot flag set, you can restore Windows booting with lilo from the live CD. Have a look at number 2 in this post:

[http://ubuntuforums.org/showpost.php?p=10446990&postcount=3](http://ubuntuforums.org/showpost.php?p=10446990&postcount=3)

---

### Post by hansolo4949 on 2011-02-15
Okay, do you have a windows 7 recovery cd? if you do, you can easily restore windows 7. Just boot into it like you would a livecd, then open a command prompt (cmd). The type: bootrec /fixmbr and bootrec /fixboot (notice the spaces!). Reboot, and you should have a working windows 7 back! now all you have to do is get rid of the no longer used partitions.....

---

### Post by Quackers on 2011-02-15
Or re-install Ubuntu :-)

---

### Post by hansolo4949 on 2011-02-15
Please feed the ducks!:D

But anyway, I would not reinstall Ubuntu. There is a large chance that the same problem will happen again, or something worse will muck everything up. Actually, if you just want the info in Windows 7, open up it's "hard drive" in the places menu. Good luck!

---

### Post by coffeecat on 2011-02-15
> **hansolo4949 said:**
> But anyway, I would not reinstall Ubuntu. There is a large chance that the same problem will happen

What problem? The OP accidentally deleting Ubuntu? Re-installing Ubuntu is a perfectly good solution to the situation the OP describes.

---

### Post by hansolo4949 on 2011-02-15
Sorry, I misphrased that, and just corrected it. I said that because if he/she had data on 7, that way they could get it off 7, then reinstall Ubuntu. That was what I was coming from. Now, the same issue may still occur even if they reinstall Ubuntu, but I guess if that happens, they can just go Ubuntu. 

To Ubuntu, and beyond!

---

