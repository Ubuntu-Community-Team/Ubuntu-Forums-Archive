---
title: "Advance partition problem Ubuntu 10.10?"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by steigerjb on 2010-10-10
I did a dual boot/advance partition with Windows 7 and Ubuntu 10.10 Maverick Meerkat. I was trying to have / as 20gb, swap as 4gb, and /home as the remaining space.

After installing a looking at it in gparted, why is / (sda3) outside the sda4? Shouldn't it be inside? From what I can tell, Ubuntu booted fine.

---

### Post by Quackers on 2010-10-10
I suspect that sda3 is a primary partition, while sda5 and sda6 are logical partitions within sda4, which is an extended partition.

---

### Post by steigerjb on 2010-10-10
> **Quackers said:**
> I suspect that sda3 is a primary partition, while sda5 and sda6 are logical partitions within sda4, which is an extended partition.

what, if anything should I do about it?

---

### Post by Quackers on 2010-10-10
I wouldn't do anything about it as it shouldn't be a problem. You seem to have what you wanted with regard to sizes (more or less) and the system boots ok. Enjoy :-)

---

### Post by jtarin on 2010-10-10
Nothing unless you just like to be organized. I suspect you created the / partition first then the other two and hit apply. You can only have a total of 4 primary partitions.Your Windows takes up two. 4GB's swap is a little much unless you work for Dreamworks.

---

### Post by steigerjb on 2010-10-10
> **Quackers said:**
> I wouldn't do anything about it as it shouldn't be a problem. You seem to have what you wanted with regard to sizes (more or less) and the system boots ok. Enjoy :-)

k

---

### Post by sandyd on 2010-10-10
> **jtarin said:**
> Nothing unless you just like to be organized. I suspect you created the / partition first then the other two and hit apply. You can only have a total of 4 primary partitions.Your Windows takes up two. 4GB's swap is a little much unless you work for Dreamworks.
or if you love hibernating and have 4GB of ram

---

### Post by Quackers on 2010-10-10
Aha! I forgot about that (hibernate has never worked on my laptop).

---

### Post by jtarin on 2010-10-10
> **sandyd said:**
> or if you love hibernating and have 4GB of ram
Hibernate and Laptops are areas I know nothing about. I use a normal setup.

---

