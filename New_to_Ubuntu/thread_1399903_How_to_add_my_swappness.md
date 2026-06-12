---
title: "How to add my swappness???"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Yanno on 2010-02-06
Hi,there!
   I just add my memory from 2 to 4Gb,which my swap(now 5Gb) is too small to load.It's only 2.4 of the 4Gb available,so I wanna add my swap to 10Gb.I searched the forums with no answer,any idea here?I'd appreciate that if someone could help me out!Thx!!!
                                                                                     Yanno:P

---

### Post by ankspo71 on 2010-02-06
Here is a link that has alot of info about swap, and swappiness too.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by warfacegod on 2010-02-06
If you have 4 GB RAM then a 5 GB swap should be more than enough room.

---

### Post by Yanno on 2010-02-06
I've learned somewhere the swap should be at least as twice of your RAM...but I still don't know why...

---

### Post by Yanno on 2010-02-06
Thank you,ankspo!!!!

---

### Post by qamelian on 2010-02-06
> **Yanno said:**
> I've learned somewhere the swap should be at least as twice of your RAM...but I still don't know why...
That's only still true for systems with limited RAM where swapping will be common or if you are doing extrmely memory intensive tasks.

---

### Post by 2hot6ft2 on 2010-02-06
> **qamelian said:**
> That's only still true for systems with limited RAM where swapping will be common or if you are doing extrmely memory intensive tasks.
Exactly. With 4GB of RAM and setting the swappiness to say 10 you'll probably never even use any swap.

The default is set to 60 (meaning it will only use 40% of your RAM before it starts using swap. Setting it to 10 means it would not use swap until you reach using 90% of RAM)

You can set it like this
```
sudo sysctl vm.swappiness=10
```
sets your swappiness variable to 10
To get turn your swap off (and get everything which is needed back into memory)
```
sudo swapoff -a
```
To turn it back on (being empty and it should stay almost empty because of vm.swappiness=10)
```
sudo swapon -a
```

If you like your new settings you can make it more permanent by adding this line:
> vm.swappiness=10

to /etc/sysctl.conf by using your favorite editor :
```
sudo gedit /etc/sysctl.conf
```

After reboot vm.swappiness is 10

---

### Post by warfacegod on 2010-02-06
> **Yanno said:**
> I've learned somewhere the swap should be at least as twice of your RAM...but I still don't know why...

Unless you are doing some very heavy video encoding, a 10 GB swap is unneeded.

---

### Post by Yanno on 2010-02-06
Yeah.I play Nexuiz!!!It will take a lot of memory.Actually it doesn't work by adding the swap. Now The problem solved after installing the kernel with pae,it is getting faster!

---

### Post by warfacegod on 2010-02-06
I assume you are using Karmic 64, if not, you can't use all of your 4 GB RAM.

---

### Post by Yanno on 2010-02-06
2hot:How did you know my swappiness is 10?You mean I should make it 90?Thx

---

### Post by Yanno on 2010-02-06
I'm using Karmic32!!!I made it after installing the kernel with pae.Now 3.9 of the 4Gb available.

---

### Post by 2hot6ft2 on 2010-02-06
> **Yanno said:**
> 2hot:How did you know my swappiness is 10?You mean I should make it 90?Thx
If you make it 90 then it will start using your swap when you get to using 10% of your RAM. RAM is faster than swap so it should be set to 10.
Think of it like this:
Start using swap when I only have ##% of RAM left available!!!
NOT like this:
Use ##% of my RAM before using swap!!!

So setting swappiness to 10 will make it use 90% of your RAM not the other way around.

I got it from a Ubuntu tweaking guide but I don't have the link handy.

EDIT: Here's the link (some of it may be outdated but there is a lot that still works) It actually suggests setting it to "0"
[Tweaking Ultimate]("http://forumubuntusoftware.info/viewtopic.php?f=7&t=7")

And Welcome

---

### Post by durand on 2010-02-06
You will almost definitely not need 10GB of swap. 4GB is probably enough and even then, you probably won't use much of that except when hibernating. Nexiuz won't go over your ram limit.

---

### Post by Yanno on 2010-02-06
Thank you...then make it 0...

---

### Post by mcduck on 2010-02-07
> **2hot6ft2 said:**
> If you make it 90 then it will start using your swap when you get to using 10% of your RAM. RAM is faster than swap so it should be set to 10.
Think of it like this:
Start using swap when I only have ##% of RAM left available!!!
NOT like this:
Use ##% of my RAM before using swap!!!

So setting swappiness to 10 will make it use 90% of your RAM not the other way around.

I got it from a Ubuntu tweaking guide but I don't have the link handy.

EDIT: Here's the link (some of it may be outdated but there is a lot that still works) It actually suggests setting it to "0"
[Tweaking Ultimate]("http://forumubuntusoftware.info/viewtopic.php?f=7&t=7")

And Welcome

Actually thew swap use is a lot more complicated than that, and swappiness is just one of the factors the kernel uses to decide how much and when swap should be used. But for sure swappiness isn't just some limit to tell how much memory to use before swapping. :)

*distress* is a value telling how much troubles kernel is having freeing memory. it starts from zero and grows up to 100 based on how many attempts the kernel needs to do until it's able to allocate memory for something.

*mapped_ratio* is approximate percentage of how much of the system's total memory is mapped.

*vm_swappiness* is a parameter used to configure how much kernel should prefer swapping versus dropping cached data.

The actual swap usage, *swap_tendency* is then calculated like this:
***swap_tendency* = *mapped_ratio*/2 + *distress* + *vm_swappiness***

The result is that even with swappiness set to 0, the kernel will still use swap if it needs to (if the distress value gets high enough). It's just less likely to do that when compared to having swappiness set to 100.

---

