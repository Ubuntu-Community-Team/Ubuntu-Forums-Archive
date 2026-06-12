---
title: "The order of creation of the partitions is important?"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by leus on 2009-05-08
I would like to know the order of the partitions , from home user :o

My setup  to boot the Ubuntu partition of a dual boot (Windows XP)

1. Installing windows xp  30-35gb 

2. boot with Ubuntu , and partition manually add

I read some tutorials but I have an existential question!

first / Root 10-12 GB  ( this is ok )

**2 Second ? /Swap or /home ???  or   /home or /Swap ???**


Thanks!!

---

### Post by Pjotrovitz on 2009-05-08
It doesnt matter which order you put them in.

---

### Post by 73ckn797 on 2009-05-08
Install should take care of necessary swap space on its own.

---

### Post by leus on 2009-05-08
> **73ckn797 said:**
> Install should take care of necessary swap space on its own.

So? swap 1g (i have 2g of ram).


first / Root 10-12 GB ( this is ok ) primary Begining

2 Second ? /Swap or /home ??? or /home or /Swap ??? ( 1gb) It doesnt matter which order ?  Swap Area                 

*primary or logical???

3 . /home ( the rest of the disc) Begining

Thanks

---

### Post by leus on 2009-05-09
Can anybody help me?

---

### Post by Einsamkeit on 2009-05-09
I don't think the order really matters.
Also, you can put all your Linux-related partitions as logical, no need for primary in those, the only primary needed is WinXP as it seems to require to be primary to even work.

---

### Post by Didius Falco on 2009-05-09
The order you create them in, as in which you make first, doesn't matter.

Definitely install Windows first, in the first Primary partition. That will be the way that makes it easiest.

After that, it doesn't really matter what order you create them in, but I'd recommend making an Extended patition and creating the Ubuntu partitions as Logical drives inside the Extended partition. 

Just be sure and set the / and /Home partitions in the install when the partitioner comes up. Choose the **Manual (advanced)** option and you can choose your own partitions.

Do this by highlighting the, for example, partition you want to be your /Home partition on the partitioner screen, click the "**edit partition**" button and set it to "use" EXT3 (or EXT4 if you want to, but that's still a bit bleeding edge) and the type as "/Home" without the quotes - you'll see the option on the screen.

Do the same thing for your "/" partition. As long as you formatted the swap partition as a "linux swap" type, you won't need to do anything to that one.

Then just let the installer finish and you'll be all set.

Regards,

Didius

---

### Post by leus on 2009-05-09
Thank you very much for the help now proceed to install:)

---

### Post by Didius Falco on 2009-05-09
Have fun and welcome to the Community!!

Regards,

Didius

P.S. After you get it installed, post one last time in here to tell the results, then mark this thread as solved, using the HowTo in my signature.

---

