---
title: "Switching to (future) Lynx"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2010-04-03
Hy folks!

I am using Hardy since it appeared in 2008, and now, because the next LTS release is almost here, I think is time for an upgrade.
I have a couple of question regarding this transition. 
First of all, I will mention that I will do a clean install, not an upgrade. My system is an ASUS Laptop, AMD Turion 64 processor, nVidia GEFORCE GO 7600 video card and 2 GB of RAM.
I have 3 partition on my hard drive (4, if you count the swap partition too): one with Windows XP (which I keep only as backup, I haven't used it in over a year),a boot partition and a /home partition.Linux partition are ext3.
My questions are:
1.I know that the default filesystem in 10.04 will be ext4. Do I still have the option to choose ext3? Would it be a problem if the boot partition is ext4 and the home partition is ext3?
2.The classical question:32 or 64 bits? I know that my processor is 64 bit capable and I read lots of post with this argument (32 VS 64) but still haven't made up my mind. I won't plan of using more then 4 GB of RAM on this machine (as a matter of fact, I don't plan any RAM upgrades) so this is not as issue for me (I know that the classical example in this argument was that you can use more than 4 GB of RAM). My primary concern is about software (I heard that flash has issues in 64 bits, for example) .Would I find all the programs in 64 bits? If not, can I install a 32 bit program on a 64 bit OS? Is the processor performance so noticeable?
Thanks allot for any answers you can give me and sorry for the long post.

---

### Post by johngreth on 2010-04-03
If you don't have too much ram 64 bit will do little for your computer's performance. I have seen programs that don't work on 64bit, but that is very uncommon nowadays. If you use a lot of old software that is no longer supported it may be wise to use 32bit, but I'm using 64bit with no problems.

You will have the option of ext3 and ext4, and you can leave your home directory ext3 but have the boot partition ext4. This is not a problem.

---

### Post by thomas144 on 2010-04-03
I'm not sure about the first question. But, as to the 64-bit vs. 32-bit question, I would recommend 64-bit. I'm not sure about Flash Player and its problems. I do know that 64-bit tends to work better with things that put a heavy load on your computer. I would recommend that you go with 64-bit unless you have a reason not to. It is likely to give you better performance. As for Flash, I'm not the person to know about that. The bottom line is that if Flash 64-bit's problems are minor and/or you don't care about it that much, go for 64-bit, especially if you used 64-bit with Hardy.

---

### Post by sandyd on 2010-04-03
> **Troll_the_Great said:**
> Hy folks!

I am using Hardy since it appeared in 2008, and now, because the next LTS release is almost here, I think is time for an upgrade.
I have a couple of question regarding this transition. 
First of all, I will mention that I will do a clean install, not an upgrade. My system is an ASUS Laptop, AMD Turion 64 processor, nVidia GEFORCE GO 7600 video card and 2 GB of RAM.
I have 3 partition on my hard drive (4, if you count the swap partition too): one with Windows XP (which I keep only as backup, I haven't used it in over a year),a boot partition and a /home partition.Linux partition are ext3.
My questions are:
1.I know that the default filesystem in 10.04 will be ext4. Do I still have the option to choose ext3? Would it be a problem if the boot partition is ext4 and the home partition is ext3?
2.The classical question:32 or 64 bits? I know that my processor is 64 bit capable and I read lots of post with this argument (32 VS 64) but still haven't made up my mind. I won't plan of using more then 4 GB of RAM on this machine (as a matter of fact, I don't plan any RAM upgrades) so this is not as issue for me (I know that the classical example in this argument was that you can use more than 4 GB of RAM). My primary concern is about software (I heard that flash has issues in 64 bits, for example) .Would I find all the programs in 64 bits? If not, can I install a 32 bit program on a 64 bit OS? Is the processor performance so noticeable?
Thanks allot for any answers you can give me and sorry for the long post.
1. no. fstab will set the partition types for ya.
3. 32-bit. 64-bit is still a bit messy (esp flash & adobe reader)

---

### Post by johngreth on 2010-04-03
> 1. no. fstab will set the partition types for ya.

Can't you say custom partitioning during installation and format the / partition as ext3?

---

### Post by howefield on 2010-04-03
> **Troll_the_Great said:**
> I know that the default filesystem in 10.04 will be ext4. Do I still have the option to choose ext3? Would it be a problem if the boot partition is ext4 and the home partition is ext3?

As you are doing a clean install, you will be able to choose whatever file system you want for each partition. You can mix and match ext3/ext4 as you wish.

> The classical question:32 or 64 bits?

I'd say if your machine is 64 bit capable, then use it, especially if you plan on doing some processor intensive stuff like video encoding. If you aren't doing such stuff with your machine, then most likely you won't see any difference in performance. 32 bit applications can be installed if necessary.

---

### Post by Troll_the_Great on 2010-04-03
Thank you all for your answers. So, from what you told me, I understand that I can have the boot partition ext4 and home ext3 without any problems, right? What you suggest to do? Do I gain performance or stability is the boot partition is ext4?

> **howefield said:**
> I'd say if your machine is 64 bit capable, then use it, especially if you plan on doing some processor intensive stuff like video encoding. If you aren't doing such stuff with your machine, then most likely you won't see any difference in performance. 32 bit applications can be installed if necessary.
I don't do any processor intensive stuff. Basically I surf the net, listen to music, a little document work and occasionally play (especially Warcraft III via wine). So, from what you are saying, if I need a 32 bit program I can install it on a 64 bit OS?

---

### Post by durand on 2010-04-03
If possible, use ext4 for everything, except maybe /boot where it isn't really necessary. You get a pretty huge performance boost when using ext4.

EDIT: Yes, it should be pretty seamless to run 32bit programs on 64bit.

---

### Post by howefield on 2010-04-03
> **Troll_the_Great said:**
> I don't do any processor intensive stuff. Basically I surf the net, listen to music, a little document work and occasionally play (especially Warcraft III via wine). So, from what you are saying, if I need a 32 bit program I can install it on a 64 bit OS?

Then the benefit of 64 bit is pretty negligible, I personally would still use 64 bit, but knowing that 32 bit will do you fine, you have little reason to opt for 64 and the possible issues that it may bring even if they are unlikely to materialise.

---

### Post by Troll_the_Great on 2010-04-03
> **durand said:**
> If possible, use ext4 for everything, except maybe /boot where it isn't really necessary. You get a pretty huge performance boost when using ext4.

EDIT: Yes, it should be pretty seamless to run 32bit programs on 64bit.

I can't use ext4 for /home partition, because I don't want to format that partition, so I will remain ext3. My question was if I should use ext4 on the boot partition. From what you are saying I understand that it will make no difference if I use ext4 on it, so I think I will remain with ext3.

---

### Post by sandyd on 2010-04-03
> **johngreth said:**
> Can't you say custom partitioning during installation and format the / partition as ext3?

that was what I meant. If you do ext3 at setup, it will specify that it is ext3 in fstab and it will work....

---

### Post by sandyd on 2010-04-03
> **Troll_the_Great said:**
> I can't use ext4 for /home partition, because I don't want to format that partition, so I will remain ext3. My question was if I should use ext4 on the boot partition. From what you are saying I understand that it will make no difference if I use ext4 on it, so I think I will remain with ext3.

you can convert ext3 to ext4. without formating.

---

### Post by durand on 2010-04-03
> **Troll_the_Great said:**
> I can't use ext4 for /home partition, because I don't want to format that partition, so I will remain ext3. My question was if I should use ext4 on the boot partition. From what you are saying I understand that it will make no difference if I use ext4 on it, so I think I will remain with ext3.

Why can't you make the root partition ext4? It really is a major boost, you won't regret it. As for home, as carlee said, you can convert the ext3 one to ext4 without any loss of data, however, I don't think you can get it to be exactly like a fresh ext4 partition and you won't get as big a speed boost. I do still think it would be worth trying.

---

### Post by Troll_the_Great on 2010-04-04
First of all, HAPPY EASTER everyone!
Thank you for your answers, I found out some things I didn't know, but please elaborate a bit.
How can I switch from ext3 to ext4 without formating? It is safe, are you sure I won't loose anything?

---

### Post by 3rdalbum on 2010-04-04
> **Troll_the_Great said:**
> First of all, HAPPY EASTER everyone!
Thank you for your answers, I found out some things I didn't know, but please elaborate a bit.
How can I switch from ext3 to ext4 without formating? It is safe, are you sure I won't loose anything?

Doing anything to a filesystem is risky, and you definitely want a backup.

Changing Ext3 to Ext4 can be done, apparently, but I have heard that you'll get more performance from a native Ext4 partition rather than a converted one. Since you're backing up everything anyway, you could erase the partition and make a new Ext4 filesystem, and then copy everything back and you'll have a full-featured Ext4.

---

### Post by durand on 2010-04-04
3rdalbum makes a lot of good points, but here's how you do it: [http://www.webupd8.org/2009/04/convert-your-ext3-file-system-to-ext4.html](http://www.webupd8.org/2009/04/convert-your-ext3-file-system-to-ext4.html)

---

### Post by Troll_the_Great on 2010-04-04
Thank you all for your answers.
Regarding the first question, I am clarified. I will use ext4 on the boot partition and decide later for the home partition.
But I'm still waiting more opinions about the 32 64 bits thing. Carlee said that 64 still have issues and I would be better of with 32 bit Ubuntu. Is the performance gain so noticeable? What things exactly still have issues with 64 bits?

---

### Post by durand on 2010-04-04
I've been using 64bit ubuntu for about 2 years now, and the *only* problem seems to be adobe flash (basically, flash is a bit slow in fullscreen, however, it only seems to affect nvidia cards as it works perfectly on my friend's laptop with integrated intel graphics). You could probably get around it by using 32bit flash instead, but I don't really like using flash in the first place. In any case, you could always just try it from a live cd before installing. I'm not really sure about the performance difference between 32bit and 64bit, but I think processor intensive applications are much faster. The other thing is that 64bit is the future so you may as well move to it.

---

### Post by sandyd on 2010-04-04
> **Troll_the_Great said:**
> Thank you all for your answers.
Regarding the first question, I am clarified. I will use ext4 on the boot partition and decide later for the home partition.
But I'm still waiting more opinions about the 32 64 bits thing. Carlee said that 64 still have issues and I would be better of with 32 bit Ubuntu. Is the performance gain so noticeable? What things exactly still have issues with 64 bits?
mostly adobe stuff : flash player, adobe reader
+ there are still programs that only support 32-bit and you will have to dpkg --force archietecture in order to install them.

personally, other than the problems described above, there is not much difference between 32 and 64 bit, which is why I reccomended 32 bit. Some users that are using <4GB of RAM have also reported some slowdowns, but I dont have less than 4GB of ram (I have 8GB), So I cant check.

---

