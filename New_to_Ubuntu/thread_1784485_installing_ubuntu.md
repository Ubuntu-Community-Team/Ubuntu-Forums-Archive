---
title: "installing ubuntu"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by shibu_sawyer on 2011-06-17
hi,
i want to install ubuntu as the only os in my desktop,(in my laptop i installed through wubi(inside windows)),i came to know i need to allocate space for root,home and swap(new to this terms),so i wanna know what those terms are and how much space should i give to these root,home,swap.

My harddisk size is 250 gb..
help please. 
thanks in advance

---

### Post by curts on 2011-06-17
I typically allocate around 20 GB for /root and at least 40 GB for /home.  I'm running with 1 GB of RAM and found with 11.04 I definitely need a swap partition.  Rule of thumb is to use a swap size that is twice your physical RAM size, which is what I'm using.

If you will be building a lot of Open Source projects from source, you might consider adding another 20 GB partition for /usr/local.  If you plan on installing a lot of prepackaged software, you might want to bump up /root to 32 GB.

Set aside the rest of the drive as a data partition.

Hope this helps,

Curt

---

### Post by mister_playboy on 2011-06-17
As a new user, I feel it would be easier for you to only use a root (/) partition and a swap partition, rather than try to estimate your needs for each different part of the filesystem... which can cause headaches later if you find you didn't estimate well. ;)

How much RAM to you have?  That will decide the size of your swap... I'd just use the rest as /.

---

### Post by mastablasta on 2011-06-17
> **shibu_sawyer said:**
> hi,
i want to install ubuntu as the only os in my desktop,(in my laptop i installed through wubi(inside windows)),i came to know i need to allocate space for root,home and swap(new to this terms),so i wanna know what those terms are and how much space should i give to these root,home,swap.
 
My harddisk size is 250 gb..
help please. 
thanks in advance
 
you don't have to alocate. you just need an empty (non formatted partition) the installer will do the rest automaticly. if needed you can add a home partition later after install.

---

### Post by amauk on 2011-06-17
If you don't have multiple hard disks, there's little point in setting up separate mount-points

---

### Post by shibu_sawyer on 2011-06-17
@curts: thanks it is useful...

---

### Post by shibu_sawyer on 2011-06-17
@mister_playboy: thanks my ram size is 2gb

---

### Post by shibu_sawyer on 2011-06-17
> **mastablasta said:**
> you don't have to alocate. you just need an empty (non formatted partition) the installer will do the rest automaticly. if needed you can add a home partition later after install.

sorry i couldn understand...i haven don this before..

---

### Post by Paqman on 2011-06-17
> **shibu_sawyer said:**
> @mister_playboy: thanks my ram size is 2gb

You only need to decide how much swap you need if you're going to do manual partitioning. I'd just let the installer sort that out for you, it's not important.

The swap partition is used as extra memory space if you start to run low on RAM. With 2GB you're unlikely to run low on RAM very often (or at all), so it won't really be used much. The only thing it might get used for is if you want to hibernate the machine, when the contents of RAM are written into your swap partition.

The old advice about swap being twice the size of RAM is a bit obsolete now that computers have gigabytes of RAM.

---

### Post by Paqman on 2011-06-17
> **shibu_sawyer said:**
> sorry i couldn understand...i haven don this before..

The installer can create all the partitions you need automatically. You can either leave an empty space on the drive and install into that, or the installer can shrink any existing partitions down to make room.

---

### Post by mister_playboy on 2011-06-17
> **shibu_sawyer said:**
> @mister_playboy: thanks my ram size is 2gb

I would suggest you use 2GB of swap.  This will be more than enough to cover even compilation of fairly large programs.  You are free to use more than that if you wish, but it will almost surely lay there unused.  Swap memory is very slow compared to RAM, so we really don't want to use it if we don't have to.

I also have 2GB of RAM, I use 2GB as swap and my swap almost never goes above ~650MB even with mutiple browsers and JVMs running.

Use the rest of your drive for your / partition.

---

### Post by ExileAmongYou on 2011-06-17
The easiest way to install Ubuntu is to just let the installer automatically use the whole hard drive, which will give you a ~5gb (I think) swap partition and then one big partition containing everything else (/ and /home).

You can also put / and /home on separate partitions if you choose the manual partitioning option during the install. The advantage of this is if your system breaks, all your personal files should be intact, and you can just reinstall the OS into the / partition and keep your settings and files in /home. You don't have to do it this way, but it might (if you're lucky, no guarantees) protect you in the case of a horrible system failure. If you're going to do it manually like this, I'd recommend 30-40GB for / (probably a little large, but it leaves you a lot of room for installing programs, especially games, which can be pretty big), 5GB for swap, and the rest for /home.

---

### Post by shibu_sawyer on 2011-06-17
> **mister_playboy said:**
> I would suggest you use 2GB of swap.  This will be more than enough to cover even compilation of fairly large programs.  You are free to use more than that if you wish, but it will almost surely lay there unused.  Swap memory is very slow compared to RAM, so we really don't want to use it if we don't have to.

I also have 2GB of RAM, I use 2GB as swap and my swap almost never goes above ~650MB even with mutiple browsers and JVMs running.

Use the rest of your drive for your / partition.

thank you,now i'm cleared...

---

### Post by shibu_sawyer on 2011-06-17
> **ExileAmongYou said:**
> The easiest way to install Ubuntu is to just let the installer automatically use the whole hard drive, which will give you a ~5gb (I think) swap partition and then one big partition containing everything else (/ and /home).

You can also put / and /home on separate partitions if you choose the manual partitioning option during the install. The advantage of this is if your system breaks, all your personal files should be intact, and you can just reinstall the OS into the / partition and keep your settings and files in /. You don't have to do it this way, but it might (if you're lucky, no guarantees) protect you in the case of a horrible system failure. If you're going to do it manually like this, I'd recommend 30-40GB for / (probably a little large, but it leaves you a lot of room for installing programs, especially games, which can be pretty big), 5GB for swap, and the rest for /home.

thank you very much, now i have got an idea to install ubuntu properly..

---

