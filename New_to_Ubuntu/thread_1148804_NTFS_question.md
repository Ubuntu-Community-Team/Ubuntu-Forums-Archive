---
title: "NTFS question"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by heddleston on 2009-05-04
is it possible to have my /home formatted as NTFS? i will be dual booting and it might be neccessary at my job to have all my harddrive space other than my /boot partition be NTFS.

---

### Post by y_garti on 2009-05-04
you can mount NTFS do whatever directory you want but this is not a smart move it will probably cause you a lot of problem or even will not let you log in (try to this in a lab environment )
but the main question is why to do this i don't see any reason to do this you can mount NTFS for a specific folder in the users home directory (like desktop and etc)

---

### Post by kansasnoob on 2009-05-04
Well, I've never tried, but I don't like the idea!

How about creating very small Linux partitions - like:

/ 4GB
/home 5 to 6GB
SWAP 1GB (or more if needed for hibernation)

Then you could create an NTFS partition that would be easily shared by Win and whatever Linux OS by installing ntfsprogs.

I run a multiboot just for that purpose!

---

