---
title: "Swap?"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by spatiegames on 2010-11-01
Hello,

Though I'm new to this forum, I'm not new to Ubuntu. Over time I know some stuff about it, but I'm not even close to being an expert.

One step forward for me would be to understand "swap". What is it? What does it? Do you need it? What can you do to make it better?

I also got another question. I recently installed Ubuntu 10.04 en removed the 10.10 partition (not important why). Now I've got two swap-extensions on my system. I'm not sure if they both belong to my current system. They are 8.65 and 6.27 GiB, and it would safe some space if I could delete one en use it to enlarge my /home partition.

Thanks in advantage,
Spatiegames

---

### Post by ratcheer on 2010-11-01
All you have to do is have a swap partition on your disk. Ubuntu will use it if its there. There is much controversy on how large to make it, but if you have enough memory, 512 MB is fine. The general rule of thumb is 2 times installed RAM, but that seems to be overkill.

Tim

---

### Post by ubunterooster on 2010-11-01
Swap is used to supplement memory if there is not enough. Most users will not need it but it is useful to have some just in case. (I have 33GB)

---

### Post by spatiegames on 2010-11-01
Thanx!

Okay, so it's just some extra 'slow' memory for when your actual memory is stuffed. So I got 3 GiB RAM, so I guess it's best to go for 6 GiB.

Still one question.. Can I get problems on my system if I remove one of the swap-partitions? I know I have to un-swap them first, but don't I have to change settings and stuff in my system? Or does it auto-detect all the information it needs?
Just for information: I got one swap sda5 and one on sda7. I want to remove them both and create one myself (make it 6 GiB).

---

### Post by ubunterooster on 2010-11-01
Yes, it's just "slower RAM" so to speak.
The only thing you need to do is remove one. It doesn't really matter which when you have 3 GB RAM but I would figure out which of those is being used and remove the other.

It should auto detect the change

---

### Post by spatiegames on 2010-11-01
Okay, I see.
Any easy way to figure out which one is being used?

---

### Post by NertSkull on 2010-11-01
> **ubunterooster said:**
> Swap is used to supplement memory if there is not enough. Most users will not need it but it is useful to have some just in case. (I have 33GB)

You have 33 GB of swap space????  WOW. 

And to the OP.  Hard drive space is cheap, so sparing a few gigs for swap shouldn't be an issue.  You'll have plenty with 3-6 Gigs

---

### Post by ubunterooster on 2010-11-01
> **NertSkull said:**
> You have 33 GB of swap space????  WOW
VMs and the such like make extreme amounts of RAM needed.
> **spatiegames said:**
> Any easy way to figure out which one is being used?Umm.....:confused:.....

---

### Post by jmszr on 2010-11-01
spatiegames,

This may be of help: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) .

---

### Post by spatiegames on 2010-11-01
> **jmszr said:**
> spatiegames,

This may be of help: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) .

Hmm, that isn't just of help, it's definitely of help, thank you!

---

