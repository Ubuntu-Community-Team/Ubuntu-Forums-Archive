---
title: "Swap file default size"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by riph72 on 2009-07-02
Hello all,
 
I installed Ubuntu on a laptop with 2Gb RAM, I allowed Ubuntu to choose the default swap partition size and it decided on ~1019Mb.
 
Apart from being an odd size to pick, it's also smaller than the physical RAM, so I suspected hibernation might not work, however it did. I guess this is related to the amount of applications using RAM at the time, i.e. very few? If I were using 75% of physical RAM, how would the hibernation fail? Would it just refuse to hibernate?
 
Given the general rule of thumb (by my understanding anyway) is to make the swap partition somewhere between "RAM" and "RAM * 2", why did Ubuntu choose such a small swap partition, given the amount of RAM?
 
This is for my own curiosity only; I have since changed the swap partition to be 2048Mb. I didn't want to go to 4096Mb because I am only using 20% of my HDD for Ubuntu at the moment, which is ~22Gb.
 
Regards,
Richard.

---

### Post by Tyke91 on 2009-07-02
1019 swap should be ok unless you're trying to hibernate when you are using 100% of your ram.

You shouldn't be using much swap on a daily basis, since if you do it means that you are constantly overfilling ram. You would notice a performance hit long before you filled up your swap.

---

### Post by frunns on 2009-07-02
Haven't checked my usage that often, but as far as I know I barely use the swap space at all...

---

### Post by riph72 on 2009-07-02
> **Tyke91 said:**
> 1019 swap should be ok unless you're trying to hibernate when you are using 100% of your ram.
 
You shouldn't be using much swap on a daily basis, since if you do it means that you are constantly overfilling ram. You would notice a performance hit long before you filled up your swap.
 Given your answer, I think I'll just aim for swap partition == physical RAM, sounds like this would suffice 99% of the time.
I was concerned though, because I tend to use hibernation frequently!
 
Thanks,
Richard.

---

### Post by twright on 2009-07-02
The default amount is usually quite reliable but it will make the swap smaller if you have less space being used for ubuntu overall. I don't think that I have ever had more than 1gb of RAM being used myself on Ubuntu but if you want to be safe and hibernate a lot then the swap should ideally be at least as big as the RAM. Another thing to consider is that Ubuntu does (I think) compress the contents of RAM while hibernating so this will make it less of an issue. If for some reason Ubuntu does not have enough swap space to hibernate it will just tell you and continue running so there is no risk of loosing work.

---

### Post by bodhi.zazen on 2009-07-02
In general, the less RAM you have the more swap you need.

In general, swap = RAM X 2 

Max Swap size = 1 Gb (some people say 512 kb )

Unless you have a laptop and wish to use sleep / hibernation in which case 

Swap == Ram + 128 kb (IMO).

---

