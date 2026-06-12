---
title: "Getting Really desperate"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by TDKING on 2009-09-23
Hi people right i want to re-install my ubuntu on my comp there is no other operating system on the comp its self 

I have 2 80gb hard drives that i wont to be able to access and put files in them 
but when i do the install when it gets to the Hard drive partion bit i get lost and i dont know what to do can someone please help me so i do this right 

Thank you so much

---

### Post by howefield on 2009-09-23
Here is a 10 minute video that might help your understanding.

[http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning](http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning)

---

### Post by dream_coder on 2009-09-23
just use the settings that Ubuntu recommends or your Ubuntu install then for your second drive simply make a ext3 partition and mount it with a name that is suitable for you eg "/Second"

---

### Post by TDKING on 2009-09-23
av watched the vid was very helpful thanks just have one more question 

coz am not doing a duel boot using xp 

if i set ubuntu up on harddrive one 

then on the secound hard drive do i set the whole thing up using ext4  /home so i can access the harddrive or will that not work ?

---

### Post by howefield on 2009-09-23
Yes, that will work, set first drive as / and second drive as /home

It is a good idea to have a seperate /home partition or disk.

---

### Post by TDKING on 2009-09-23
so set the first drive as root yeh then secound as home but wont that mean i have like 70gb of free unused space on the first drive ? 

will this also solve the problem of the permissions when i try to create a file in there or move a file in to it ? 

thanks

---

### Post by scrooge_74 on 2009-09-23
before you go any further.

First install XP on the first drive (remember XP likes to be alone in PC)

Then you install Ubuntu and you partition the second drive and any part of first drive as you like.

Example , split first drive so XP is on first partition, Ubuntu on second part of that drive, make / to go in this firs drive. Then second drive you can devote it to your /home so all your personal data is safe from any hardrive crash or the eventuallity you get bored with ubuntu and want to install another linux version then you wont lost your data.

You can also go with learning ubuntu then you install Virtual Box and you can run XP as a virtual Pc from inside your Ubuntu box

Have fun, I do

---

### Post by TDKING on 2009-09-23
that seems alot more complicated 

will it not be easier to do it how i said ? 

not poo pooin it or anythin

---

### Post by howefield on 2009-09-23
I think I misinterpreted what you were asking. 

If it were my disks, I would put 3 partitions on the first disk,  /, /home and /swap. (If the disk was big enough, I'd have a 4th partition for installing and testing alphas/betas of the next version).

The second disk I'd use for data storage/backup/virtual machines/ect. I would sort out the second disk after setting Ubuntu up on the first one, don't worry about setting permissions, it couldn't be simpler.

---

### Post by howefield on 2009-09-23
> **scrooge_74 said:**
> before you go any further.

First install XP on the first drive...

The poster doesn't want XP on the computer,..

---

### Post by TDKING on 2009-09-23
once i have set up ubuntu again would you be able to help me further mate at all either on msn or via e-mail as at the moment i have tried to access my secound drive and it says am not the owner 
really struggling to get it done on my own and my mate who said am an expert really screwed all this up last night and left me to it on my own lol

---

### Post by howefield on 2009-09-23
> **TDKING said:**
> once i have set up ubuntu again would you be able to help me further mate at all either on msn or via e-mail as at the moment i have tried to access my secound drive and it says am not the owner 
really struggling to get it done on my own and my mate who said am an expert really screwed all this up last night and left me to it on my own lol

No worries. Just ask.

---

### Post by TDKING on 2009-09-23
could you pm me your msn ? 

Thanks

---

### Post by LewRockwell on 2009-09-23
> **howefield said:**
> The poster doesn't want XP on the computer,..

yeah, that one was a real zinger

.

---

