---
title: "error 16 and 18 msgs with a diff variation tho them"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by deboh on 2009-03-14
hi, i realised that my second harddrive may not be sitting well in my cpu casing, so i picked up another older but bigger and spacious casing and transfered my component into it, everything seemed fine and when i powered on it worked, well no biggie.
i have 2 HDD, 1x80gig is dual boots both XP and Ubuntu 8.10, the second HDD is mainly reformatted and used as storage but a slave to the first, everything worked fine until i decided to change casing which shouldnt be an issue since it didnt involve any software change or such.
immediately i started up my system after the case change, it gave a failed start but that was only once, the next moment it started up itself and gave me an 'error 18'' something about wrong cylinder and capacity, the other time i also got the ''error 16''.
the only thing i have noticed but cant understand why is that when i removed the slave and used the master as a single drive it worked fine and and i cld load either of XP or Ubuntu at will, making it a maste slave HDD it gives error 18 or 16 messages, i cant just ignore the other HDD(the slave) because thats my main storage.
what do i do, i really need any one's assistance here

thanks

---

### Post by unutbu on 2009-03-14
It sort of sounds like the BIOS is listing the drives in the opposite order than before you swapped cases. This would cause GRUB (the boot loader) to look on the wrong drive while booting up.

If this is indeed the problem, then swapping the order that the drives are connected on the data cable can solve this problem.

---

