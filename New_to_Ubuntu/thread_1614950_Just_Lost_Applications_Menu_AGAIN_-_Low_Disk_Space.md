---
title: "Just Lost Applications Menu AGAIN - Low Disk Space?"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by demonboy on 2010-11-06
Hello again,

I'm starting a new thread on this same problem since this has happened twice now on the same day and I suspect it's an issue that needs looking at. Unless of course there is something really obvious that I'm missing.

Once again my Applications menu has disappeared. Roughly this is the scenario:

- I recently installed 10.10. If I'm honest it was for testing and probably didn't leave enough space on its own area because I am frequently getting low disk space warnings.

- I am getting confused over how much disk space I have. Although I am accessing my old partitioned hard drive and taking stuff off there, I am still getting warnings about low disk space. Why is this? Have I installed Ubuntu in a small space that doesn't grow dynamically?

I think what's obvious is that I have two issues, but I can't help thinking they are related (perhaps naively).

Any help/pointers?

---

### Post by sikander3786 on 2010-11-06
How was Ubuntu installed? Is it a dual boot setup, Wubi or inside a virtual machine?

> Have I installed Ubuntu in a small space that doesn't grow dynamically?

This statement makes me ask that question.

---

### Post by ivarn on 2010-11-06
Ok here's what you should do.
Take a dvd backup of your ubuntu. you can use remastersys.
Now, go to windows and open up disk manager, delete the linux partition (ext4), pop in the backup cd and install linux again. but give the partition more space now.
How much space did you give ubuntu when you installed it and how much totall and available space do you have on your computer?

---

### Post by oldos2er on 2010-11-06
> **demonboy said:**
> - I recently installed 10.10. 

Can you open a terminal and run **df -h** and **sudo fdisk -l** and post the output from both commands here?

---

### Post by demonboy on 2010-11-07
Morning,

df -h results here:

```

Filesystem Size Used Avail Use% Mounted on
/dev/loop0 5.6G 5.2G 125M 98% /
none 996M 244K 996M 1% /dev
none 1002M 200K 1002M 1% /dev/shm
none 1002M 128K 1002M 1% /var/run
none 1002M 0 1002M 0% /var/lock
/dev/sda2 72G 61G 11G 85% /host

```
And sudo fdisk -l:
```

Device Boot    Start        End       Blocks          Id     System
/dev/sda1            1         784   6297448+    12     Compaq diagnostics
/dev/sda2 *         785      10059    74495096    7       HPFS/NTFS
/dev/sda3           10059   19458    75496448    7       HPFS/NTFS

```

---

### Post by Hippytaff on 2010-11-07
> **sikander3786 said:**
> How was Ubuntu installed? Is it a dual boot setup, Wubi or inside a virtual machine?



This statement makes me ask that question.
Have you got ubuntu in a virtual machine?

---

### Post by demonboy on 2010-11-07
No, dual boot.

My Windows XP install partitioned the disk to c: and d:, c: being my OS. C drive had around 3Gb left when I first installed Ubuntu and D drive had 9Gb. Ish. I have a 160Gb hard drive.

---

### Post by Verbeck on 2010-11-07
> **demonboy said:**
> 
```

**/dev/sda2 72G 61G 11G 85% /host**

``````

Device Boot    Start        End       Blocks          Id     System
/dev/sda1            1         784   6297448+    12     Compaq diagnostics
/dev/sda2 *         785      10059    74495096    7       **HPFS/NTFS**
/dev/sda3           10059   19458    75496448    7       **HPFS/NTFS**

```

i dont think thats a true dual boot...more like wubi
doesn't explain the issue at hand though..

---

### Post by demonboy on 2010-11-07
Ah, wubi. Yes.

If I'm honest I got confused as to what install I was doing. Remember I was using Ubuntu Netbook for a while before being told I was in the wrong system!

I would like to do a proper install. Perhaps what I should be doing is freeing up everything on my current Windows d: drive and using that partition to install Ubuntu and hold all data pertaining to my install and apps on that D; drive.

Is this possible? How would I best go about this? Should I follow Ivarn's instructions?

---

### Post by sikander3786 on 2010-11-07
Have you got any important files on the Wubi install? Or any configuration you want to save? If not, you can follow the community page here which is a good how-to on dual-booting.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by oldos2er on 2010-11-07
You uninstall Wubi from Windows just the same as if it was a Win* app: [http://psychocats.net/ubuntu/wubi#remove](http://psychocats.net/ubuntu/wubi#remove)

---

### Post by demonboy on 2010-11-10
Just to let you know this problem went away when I did a full install of 10.10. Thanks.

---

