---
title: "plz ,give me command no link of thread"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by magedsoft on 2010-10-27
i have a little qestion i search alot in internet i found alot of threads but i always get error 
 
 
my problem is 
 
i use ubuntu 10.10 and i have partion called software i want when i make update or install any thing i want the package download on this drive "software" to collect the package 
 
i try to remove apt folder via termianl  and make link to software but i failled again and again
 
 
how to do it my friend i wait you 
 
and thank u
 
 
i love ubuntu and any one use it 
 
goodbye

---

### Post by amjjawad on 2010-10-27
> **magedsoft said:**
> i have a little qestion i search alot in internet i found alot of threads but i always get error 
 
 
my problem is 
 
i use ubuntu 10.10 and i have partion called software i want when i make update or install any thing i want the package download on this drive "software" to collect the package 
 
i try to remove apt folder via termianl  and make link to software but i failled again and again
 
 
how to do it my friend i wait you 
 
and thank u
 
 
i love ubuntu and any one use it 
 
goodbye

Quite honestly I didn't understand what exactly are you talking about?!

---

### Post by magedsoft on 2010-10-27
ok my friend i'm sorry my english sooooooooooooooooo bad 


i want change apt folder to my another partion 

it's simple now

---

### Post by amjjawad on 2010-10-27
> **magedsoft said:**
> ok my friend i'm sorry my english sooooooooooooooooo bad 


i want change apt folder to my another partion 

it's simple now

Okay, let's start step by step.
What I understood from your thread is:
1- You have a Partition called "Software".
2- You want to save any applications you're downloading to that Partition (Software).
3- You also want to save your settings in that partition.

Am I right?

---

### Post by bioterror on 2010-10-27
$ ln /var/cache/apt/archives /media/Software

OR! you could  mount that software drive as your /var/cache/apt in /etc/fstab.
That sounds fun :D

---

### Post by cogier on 2010-10-27
The packages are downloaded to  /var/cache/apt/archives/. If I understand your request you want all the packages in a partition called "software". 

I can't find away to select where the files will end up but you could move them from the folder above to your "software" partition.

If you use **apt-get** with the **-d** switch it will only download the package and not install it. In Terminal type **man apt-get** for more details.

Hope that helps.

---

### Post by aeiah on 2010-10-27
```

mount --bind /media/drive/software /var/cache/apt/archives/

```

or, you could set startup to copy from your apt cache to your software directory on startup or at a specific time of day

---

### Post by magedsoft on 2010-10-27
ln: `/var/cache/apt/archives': hard link not allowed for directory


what i have done wrong

---

### Post by bioterror on 2010-10-27
Oh, and remember this:
```

/etc $ cat apt/apt.conf.d/20archive
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";

```

I really cant understand why you want to do this.
Or why you're interested in keeping old .deb files.

---

### Post by magedsoft on 2010-10-27
ok all of you 

thank you too much to help me 
but i want to keep old deb to make offline install or update 


thank u too much ,i so sorry 
bye

thank u [aeiah]("http://ubuntuforums.org/member.php?u=71962") your way work with me thank u toooooooooooooooooooooo much

---

### Post by Verbeck on 2010-10-27
> **magedsoft said:**
> ok all of you 

thank you too much to help me 
but i want to keep old deb to make offline install or update 


thank u too much ,i so sorry 
bye
no need to apologise, this is a support forum :)

---

### Post by mcduck on 2010-10-27
Doing that would only make the downloaded *packages* to go to that partition, it will not affect where the software is *installed*. Not very useful unless you for some reason want to store the packages. And even then it would be simpler and easier to just copy the package files from /var/cache/apt/archives every now and then. Or set up a script to do that for you, if you want.

And considering that programs aren't installed into any single location on your system, but instead each file goes to different place based on that individual file's purpose, there really is no effective way to get all your *programs* to install on a separate drive. Perhaps mounting the separate partition as /usr would get pretty close.

If you also want to keep settings on separate drive, you have two more things to consider. If it's system-wide settings, you want /etc. If it's settings for *your* programs you want /home on the separate partition.

So, the closest to what you are asking would be creating 3 new partitions, one for /usr, one for /etc, and one for /home.

(to tell you the truth, in most cases only the separate /home makes any sense)

---

### Post by Jeanke on 2010-10-27
> So, the closest to what you are asking would be creating 3 new partitions, one for /usr, one for /etc, and one for /home.

Just out of curiosity:
Is it possible to put /etc on a separate partition?
Doesn't that give problems with your fstab?

---

### Post by amjjawad on 2010-10-27
> **mcduck said:**
> (to tell you the truth, in most cases only the separate /home makes any sense)

I think that's the best option :)
Or, to be more accurate, the easiest option.

---

### Post by mcduck on 2010-10-27
> **Jeanke said:**
> Just out of curiosity:
Is it possible to put /etc on a separate partition?
Doesn't that give problems with your fstab?

You are right, you can't do it from fstab. But it can be done directly from initrd, although that's probably a bit beyond what most people would really be ready to do as separate partition for /etc isn't really that useful on any normal desktop system. (like I said, only the separate /home really makes sense, normal backups for /etc and package cache are lot easier than keeping them on separate partitions)
 
[http://blog.tuxopia.net/2010/03/booting-with-etc-in-separate-partition.html]("http://blog.tuxopia.net/2010/03/booting-with-etc-in-separate-partition.html")

---

