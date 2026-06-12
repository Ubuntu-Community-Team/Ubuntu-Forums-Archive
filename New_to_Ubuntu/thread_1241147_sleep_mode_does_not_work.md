---
title: "sleep mode does not work"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by antalves on 2009-08-15
My computer does not go to  suspend state when pressing the Sleep button
Mouse and keyboard become dead, only the Reset button works.  Is there a remedy for this problem?
I'm using Ubuntu 9.04, ASUS  K8N MB, AMD +3000, 1G RAM, swap= 512M

---

### Post by LewRockwell on 2009-08-15
> **antalves said:**
> My computer does not go to  suspend state when pressing the Sleep button
Mouse and keyboard become dead, only the Reset button works.  Is there a remedy for this problem?
I'm using Ubuntu 9.04, ASUS  K8N MB, AMD +3000, 1G RAM, swap= 512M

you have a deficiency with your swap partition

it is too small

find out what the maximum amount of ram your motherboard will handle and then enlarge the swap to that size

for example:

4GB maxram equal 4GB swap

see if that solves your trouble-call

.

---

### Post by antalves on 2009-08-15
Is it safe to change the size of Swap? No risk of damaging the Ubuntu?

---

### Post by LewRockwell on 2009-08-15
> **antalves said:**
> Is it safe to change the size of Swap? No risk of damaging the Ubuntu?

partition editing should be done via a LiveCD

attempting to use partition editor while booted from that same drive may result in undesirable and significate data loss, corruption, and failure

.

---

### Post by Paqman on 2009-08-15
Suspend to RAM shouldn't be bothered about a small swap, surely? You need swap=RAM to hibernate.

---

### Post by LewRockwell on 2009-08-15
> **Paqman said:**
> Suspend to RAM shouldn't be bothered about a small swap, surely? You need swap=RAM to hibernate.

never assume, OP and trouble-call referencing "suspend" when they might actually mean "hibernate"

english is NOT the first language of all participants of the interwebs...

.

---

### Post by antalves on 2009-08-15
What I really want is to have  CPU fan off when I hit  "sleep" in my keyboard, **similar to what happens in Windows**
I hope I've made things clearer now...

If I need to increase the swap, I have been careful to use a LiveCD

---

### Post by Paqman on 2009-08-15
Yep, that sounds like sleep/suspend, not hibernate. You can check your settings in System > Prefs > Power management.

The size of your swap partition isn't the problem, it's more likely that your motherboard has a glitch in it's ACPI implementation. This is a bit of an ongoing problem on Linux.

Do you know *exactly* what type of K8N board you have? If so, do a search of these forums for the model number and see if others have struck the same problem.

---

### Post by antalves on 2009-08-16
It is a pity that there is no easy solution. I will follow your idea of search. Thanks

---

