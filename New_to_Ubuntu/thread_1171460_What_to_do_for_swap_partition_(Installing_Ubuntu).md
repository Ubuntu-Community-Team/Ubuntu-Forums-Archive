---
title: "What to do for swap partition (Installing Ubuntu)"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by 11010110 on 2009-05-27
Hi everyone,

I am finally doing an actual install of ubuntu on it's own partition (contrary to my previous ventures with wubi) and after assigning the 107 gigs as a free space by taking it from Vista through Gparted on the live CD I made the mount point "/" and now it is asking me to set a swap partition. I did not set aside the 2 gig of space that i would need (i have 2 gig ram) already but there is a 1.5 gig space that has been set aside in NTFS by windows which i assume is used for swap. 145 megs is used in the partition and i was wondering if it would be safe to use as the swap partition if indeed it was being used for windows swap as well. Now when i was using wubi it had swap somewhere but that was automatically set up so i am not sure where it was. should i go ahead and use that 1.5 gig partition or should i back out and make a new one in Gparted and restart the install?

Thanks in advace everyone and i look forward to any replies!

---

### Post by rcayea on 2009-05-27
> **11010110 said:**
> Hi everyone,

I am finally doing an actual install of ubuntu on it's own partition (contrary to my previous ventures with wubi) and after assigning the 107 gigs as a free space by taking it from Vista through Gparted on the live CD I made the mount point "/" and now it is asking me to set a swap partition. I did not set aside the 2 gig of space that i would need (i have 2 gig ram) already but there is a 1.5 gig space that has been set aside in NTFS by windows which i assume is used for swap. 145 megs is used in the partition and i was wondering if it would be safe to use as the swap partition if indeed it was being used for windows swap as well. Now when i was using wubi it had swap somewhere but that was automatically set up so i am not sure where it was. should i go ahead and use that 1.5 gig partition or should i back out and make a new one in Gparted and restart the install?

Thanks in advace everyone and i look forward to any replies!

I am not sure about the Windows information, but for swap you only need one or two GB, and from my experience two GB is plenty. One GB would be just fine to use.

---

### Post by halitech on 2009-05-27
swap space is formatted differently and you can't use NTFS for that. You can use the 1.5gig partition but you will need to assign it as swap space and therefore it will be over-written.

---

### Post by 11010110 on 2009-05-27
now if i was to overwrite it then windows would not be able to use it correct? should i just format another small partition for the ubuntu swap?

---

### Post by ugm6hr on 2009-05-27
> **11010110 said:**
> now if i was to overwrite it then windows would not be able to use it correct? should i just format another small partition for the ubuntu swap?

You must have set Windows to use a swap partition, since it defaults to using a swap file within the main partition.

But if so - you need a separate swap partition.  Not absolutely necessary (I don't on my netbook), but improved performance with if you have the space.

I recommend 6-700MB, unless you use the suspend to RAM option, in which case you should get 1.5xRAM.

---

### Post by 11010110 on 2009-05-27
I never told windows to make that partition it jsut did so by itself. if windows doesnt use it for swap then i wonder what it is for lol. it is being usded because it isnt empty... oh well ill save that for another day i think ill set aside a nice 3 gig swap becasue i do like to use sleep mode. thanks a lot everyone for all the info!

---

### Post by neo.patrix on 2009-05-27
All you need to do is make 2 Gig Swap partition like you made root 
partition. You cannot make swap on NTFS partition, but you can make swap 
on windows extended partition. 

I don't remember exactly , but you have to specify partition type as 
swap when you create it and specify size like you do for any other 
partition. 

And 3 GiG would probably not serve right, SWAP mem gives better 
performace when it is in multiple of RAM size. With 2 GiG RAM you can 
use 2 GiG or 4 GiG swap.

---

### Post by SonicSteve on 2009-05-27
I have a slightly different take on this. 

First I agree with those who are wanting to use the suspend to ram, go with their advice.

Secondly, I have a laptop with 2gb of ram. It actually never uses the swap partition. I've monitored it, it literally never gets used. I set up a 1gb swap partition on most computers I use. Suspend function still works, and the most ram I've ever seen my computers use is approx 700mb. That was with a lot of programs running, I actually opened programs and used them, then opened new programs, and more and more. If you were to work with large raw picture files, and audio, and movie making etc I think you have a different experience. Also if you run Virtual Machines you need minimum 2gb ram. I don't do much of those things and I bet 1gb would suit my needs most days. 

It's probably safe to set the swap to the same size as your ram.

---

### Post by 11010110 on 2009-05-27
thanks for the info again everyone. I set aside three gig for it and im successfully installed. its good to be back! its been a few months where ive had to use Vista and its killed me lol

Thanks again!

---

### Post by Paqman on 2009-05-27
> **neo.patrix said:**
> 
SWAP mem gives better performace when it is in multiple of RAM size.

No it doesn't.

The tiny NTFS partition is a bit weird. It's too small to be some kind of recovery partition, i'd say it's a leftover from some previous partitioning setup. Windows does not use a swap partition.

Having a swap for Linux is highly recommended. In your case i'd go for 2GB. Although if you don't anticipate ever needing to hibernate the machine you could go for 1GB instead.

---

### Post by ugm6hr on 2009-05-27
> **Paqman said:**
> Windows does not use a swap partition.

It will if you tell it to.  I certainly used to use a separate partition for my swap file on Win 2000; although it still creates a swap file within that partition.

---

### Post by Paqman on 2009-05-27
> **ugm6hr said:**
> It will if you tell it to.  I certainly used to use a separate partition for my swap file on Win 2000; although it still creates a swap file within that partition.

Indeed, and Linux can use a swap file. However, neither of them do so by default.

---

### Post by ugm6hr on 2009-05-27
> **Paqman said:**
> Indeed, and Linux can use a swap file. However, neither of them do so by default.

Sorry, thought you were contradicting my previous statement:

> **ugm6hr said:**
> You must have set Windows to use a swap partition, since it defaults to using a swap file within the main partition.

---

### Post by Paqman on 2009-05-27
Nope, I was replying to the OP's confusion regarding Windows and swap partitions:

> 
there is a 1.5 gig space that has been set aside in NTFS by windows which i assume is used for swap


---

