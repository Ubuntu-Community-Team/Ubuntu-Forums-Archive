---
title: "Do these partitions look normal?"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by GumpTron on 2011-09-06
Thanks for taking the time to read this. I decided to create a partition to install Ubuntu 11.04 on but I was not asked to select anything when I installed Ubuntu.

Currently, Ubuntu installed successfully and I am even able to read the files located on my Windows 7 partition which is pretty cool and I guess it means Ubuntu 11.04 installed correctly. By the way, it's a duel boot install Windows 7 and Ubuntu 11.04.

My question is this. Can you please take a look at the partitions Windows 7 is reporting to me and let me know if I can erase the 61gb partition. I think it's not being used by either OS. Thank you ):P

---

### Post by idoitprone on 2011-09-06
> **GumpTron said:**
> Thanks for taking the time to read this. I decided to create a partition to install Ubuntu 11.04 on but I was not asked to select anything when I installed Ubuntu.

Currently, Ubuntu installed successfully and I am even able to read the files located on my Windows 7 partition which is pretty cool and I guess it means Ubuntu 11.04 installed correctly. By the way, it's a duel boot install Windows 7 and Ubuntu 11.04.

My question is this. Can you please take a look at the partitions Windows 7 is reporting to me and let me know if I can erase the 61gb partition. I think it's not being used by either OS. Thank you ):P

I believe that 61gb should be your ubuntu partition. Windows cannot read linux filesystems on default. Try looking at your partitings using linux utilities such as gparted, fdisk, or even blkid

Note the last 2 are terminal commands

```
fdisk -l
blkid
```

---

### Post by GumpTron on 2011-09-06
thank you :)

---

### Post by GumpTron on 2011-09-06
This is what I see when checking from within Ubuntu.


Extended 70GB

66GB ext4 / 4.3GB Swap Space

As I recall, when I created the free partition I made it 65GB. Does that mean everything looks kosher? :popcorn:

---

### Post by nothingspecial on 2011-09-06
Looks that way :)

---

### Post by GumpTron on 2011-09-06
One other thing haha :popcorn:

I chose Ubuntu 32 bit because it said recommended. I do have a 64 bit system and that's how Windows 7 runs, did I make a mistake? Even a tiny one?:guitar:

Ubuntu seems to run well as is ...

---

### Post by nothingspecial on 2011-09-06
That depends on whether or not you have over 4 gigs of ram. If so the 32bit version will not be able to use it, if not you will have no problems....


ssh.... don't mention this but I (who may look like some sort of expert with all those beans and stuff, even though I'm not really) installed the latest 32 bit version on my 64 bit desktop by mistake because I didn't read the cd. I haven't bothered rectifying the situation and everything is fine.

---

### Post by nipunshakya on 2011-09-06
> **GumpTron said:**
> One other thing haha :popcorn:

I chose Ubuntu 32 bit because it said recommended. I do have a 64 bit system and that's how Windows 7 runs, did I make a mistake? Even a tiny one?:guitar:

Ubuntu seems to run well as is ...

The reason why ubuntu might recommend a 32 bit over 64 bit is maybe that only beta version of adobe flash player plug-in is available for firefox....i guess....because like yours, i have a 64 bit windows 7 but with a dual boot with ubuntu 11.04 amd64...doesn't make any difference...its just that u reduced some computing capacity of your computer....gege...

---

