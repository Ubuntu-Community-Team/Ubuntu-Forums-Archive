---
title: "Please recommend good sizes for partitons in Ubuntu? I have 160GB on HD"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by NewsAndHistory on 2009-01-20
I want to **dual-boot** Ubuntu 8.10 (x64) Intrepid with Windows XP Pro (32 bit) on my Dell Inspiron 531s  with AMD 64 chip (it has SATA and nVidia GeForce...and plenty of space for my work: 160GB on the HD), and RAM is 2GB.

Would any of you please tell me how you would partition your Ubuntu Linux system if you planned to dual-boot Windows XP Pro & use it for making movies & music on your computer?

**I'll take whatever advice I can get from, any of you who want to assist me with those issues. Thanks in advance for reading my message & helping me & others, who are just beginning to configure Debian-based Linux distros on our computers.**

---

### Post by blueridgedog on 2009-01-20
Well, I would make swap the size of your ram and create a / partition that is either big or small.

Big (100 gig) if you are going to try and do you music and video editing in Linux
Small (30 gig) if you will stick to windows for your editing

You could to 80 gig and see if you find tools you like.  

(I am always out of space, but have some paranoid backup rituals).

A few 1 T drives are in my future.

---

### Post by COLiNx86 on 2009-01-20
> **NewsAndHistory said:**
> I want to **dual-boot** Ubuntu 8.10 (x64) Intrepid with Windows XP Pro (32 bit) on my Dell Inspiron 531s  with AMD 64 chip (it has SATA and nVidia GeForce...and plenty of space for my work: 160GB on the HD), and RAM is 2GB.

Would any of you please tell me how you would partition your Arch Linux system if you planned to dual-boot Windows XP Pro & use it for making movies & music on your computer?

**I'll take whatever advice I can get from, any of you who want to assist me with those issues. Thanks in advance for reading my message & helping me & others, who are just beginning to configure Arch Linux on our computers.**
Just FYI, Ubuntu and Arch are very different. I don't know if you just missed typed something or what, but if you've never used Linux before DO NOT try arch.
And to answer your question about partition size. I would go with around 80, for linux. It gets me by.

---

### Post by kansasnoob on 2009-01-20
Arch and Ubuntu are as different as an elephant and a kangaroo!

Why ask here?

I suggest much more studying!

---

### Post by NewsAndHistory on 2009-01-20
> **blueridgedog said:**
> Well, I would make swap the size of your ram and create a / partition that is either big or small.

Big (100 gig) if you are going to try and do you music and video editing in Linux
Small (30 gig) if you will stick to windows for your editing

You could to 80 gig and see if you find tools you like.  

(I am always out of space, but have some paranoid backup rituals).

A few 1 T drives are in my future.
**Blueridgedog, thanks for helping me! I'll go with your advice. I appreciate your patience & kindness.**

> **COLiNx86 said:**
> Just FYI, Ubuntu and Arch are very different. I don't know if you just missed typed something or what, but if you've never used Linux before DO NOT try arch.
And to answer your question about partition size. I would go with around 80, for linux. It gets me by.

[COLOR=Purple] I know. Thanks for helping me & others at this forum-site.[/COLOR]

---

### Post by Bachstelze on 2009-01-20
Your root partition doesn't need to be bigger than 10G, which is already a lot. For your personal stuff, make a /home partition.

---

### Post by alienexplorers on 2009-01-20
Go with:
> / = 20GB
/home = 30GB
/swap = 2GB
and use the rest for windows.

---

### Post by blueridgedog on 2009-01-20
> **HymnToLife said:**
> Your root partition doesn't need to be bigger than 10G, which is already a lot. For your personal stuff, make a /home partition.

I agree, and I use a separate drive for /home.  However, for a first encounter with linux I have found that easing someone into multiple partitions for a single os install a safe approach.

Given that the OP wants to do video, the only real fs that the two OS's can share will be fat32, which has a 4 gig limit.  Linux will be very slow with NTFS and the windows support for ext3 is equally limited.

Other than the ease of upgrading is there a reason to have a separate partition on the same drive for /home?

---

### Post by alienexplorers on 2009-01-20
A seperate /home partition is handy in case you have to do a reload.  This way you will not loose your configurations and personnal data stored on /home.

---

### Post by Bachstelze on 2009-01-20
Off-topic:

alienexplorers, please do not use /swap for the swap partition. It is incorrect and might lead people to actually use an ext3 partition mounted on /swap. The swap partition doesn't have a mountpoint.

---

### Post by NewsAndHistory on 2009-01-21
> **HymnToLife said:**
> Your root partition doesn't need to be bigger than 10G, which is already a lot. For your personal stuff, make a /home partition.
 Thanks for helping me! Would you please tell me what size you would make your boot partition if you wanted to dual-boot Ubuntu 8.10 (x64) & Windows XP Pro (64 bit)?

> **alienexplorers said:**
> Go with:
I appreciate your help. I will follow your advice here, as well.

> **blueridgedog said:**
> I agree, and I use a separate drive for /home.  However, for a first encounter with linux I have found that easing someone into multiple partitions for a single os install a safe approach.

Given that the OP wants to do video, the only real fs that the two OS's can share will be fat32, which has a 4 gig limit.  Linux will be very slow with NTFS and the windows support for ext3 is equally limited.

Other then the ease of upgrading is there a reason to have a separate partition on the same drive for /home?
I see what you mean. I think it's OK to have a home partition of that size. Thanks again for helping me & others at this website.

---

