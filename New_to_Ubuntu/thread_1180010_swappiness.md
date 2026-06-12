---
title: "swappiness"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by DarinB on 2009-06-06
for the heck of it i made my swappiness = 0 
i have 4gbs or ram so i thought i would see how it affects my system and wow! it pops! 
not sure what it does though and can't find a simple explanation. i think it keeps my system from swapping out to the hard drive for more ram space????? not sure but will it allow it if i ever need it to????
the explanations on line are not easy to figure out????

---

### Post by Didius Falco on 2009-06-06
> **DarinB said:**
> for the heck of it i made my swappiness = 0 
i have 4gbs or ram so i thought i would see how it affects my system and wow! it pops! 
not sure what it does though and can't find a simple explanation. i think it keeps my system from swapping out to the hard drive for more ram space????? not sure but will it allow it if i ever need it to????
the explanations on line are not easy to figure out????

Here is a little of the information contained in this FAQ:

> **Performance tuning with ''swappiness''**

 The *swappiness* parameter controls the tendency of the kernel to move processes out of physical memory and onto the swap disk. Because disks are much slower than RAM, this can lead to slower response times for system and applications if processes are too aggressively moved out of memory. 

[LIST]
[*]*swappiness* can have a value of between 0 and 100 
[*]*swappiness=0* tells the kernel to avoid swapping processes out of physical memory for as long as possible 
[*]*swappiness=100* tells the kernel to aggressively swap processes out of physical memory and move them to swap cache 
[*]Ubuntu uses a default setting of *swappiness=60* 
[/LIST]
Reducing the default value of *swappiness* will probably improve overall performance for a typical Ubuntu desktop installation.  A value of *swappiness=10* is recommended, but feel free to experiment.  **Note**: Ubuntu server installations have different performance requirements to desktop systems, and the default value of *60* is likely more suitable. 


Here is a link to the entire FAQ:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Regards,

Didius

---

### Post by DarinB on 2009-06-06
thanks that makes it clear. i am really happy at zero.
i tried opening a bunch of programs with the system monitor on and it was hard to get above 25% ram usage.
so i guess 0 is perfect for me.

---

