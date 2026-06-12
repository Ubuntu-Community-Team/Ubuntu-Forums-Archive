---
title: "Installing 10.04 over 9.10"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by pickupman on 2010-07-25
hello all
i got a new monitor since my old one pooped out and my new one does not support the res i had 9.10 set at and im due for an upgrade anyways so i downloaded 10.04 and running it off of live boot rite now but i would like to install it on the harddisk over 9.10 i have a dual boot with winxp and ubuntu. how do i get rid of 9.10 and put the 10.04 over top of it i tried installing off of the cd but it just wants to create a new partiotion i cant figure out how to get rid of the old version and put the new one over top of it...thanks in advance for the help

---

### Post by SlidingHorn on 2010-07-25
first, back up any important info on your machine.  Then you would use gparted to format the ubuntu partitions.

Once completed (probably will require a restart) then have the installer use the new unallocated space

---

### Post by Autodave on 2010-07-25
> **pickupman said:**
> hello all
i got a new monitor since my old one pooped out and my new one does not support the res i had 9.10 set at and im due for an upgrade anyways so i downloaded 10.04 and running it off of live boot rite now but i would like to install it on the harddisk over 9.10 i have a dual boot with winxp and ubuntu. how do i get rid of 9.10 and put the 10.04 over top of it i tried installing off of the cd but it just wants to create a new partiotion i cant figure out how to get rid of the old version and put the new one over top of it...thanks in advance for the help

If I were updating 9.10 to 10.4, I would just use the UPDATE MANAGER after backing up anything important.

---

### Post by pickupman on 2010-07-25
i cant get into 9.10 because my monitor does not support the old resolution so i cannot see 9.10 to update it......

---

### Post by Anuovis on 2010-07-25
Lots of people here recommend a clean install - wiping out of the old system and installing a new one in an empty partition. That is probably the safer way.

You might just use a live session of 10.04. 
It is very important you back up all the important data, then you can use gparted to format a partition where your Ubuntu was installed. After that, just install a new 10.04 there. If you made a dual-boot setup by yourself, you will be good. Otherwise, it is probably wise to search for some info about that and how to manage partitions.

---

