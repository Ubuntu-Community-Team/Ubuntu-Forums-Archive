---
title: "Full install on USB Flash Drive"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by virtualsamana on 2009-08-07
Is it possible to load a full install (not a live cd) version of 9.04 on a flash drive. If so how and what are the minimal storage requirements in GB?

---

### Post by snowpine on 2009-08-07
Yup, it`s easy... just use the regular installer (as though installing to a hard drive) but choose your flash drive instead of the HDD from the partitioner menu. When you get to the last step, choose Advanced Options, and make sure you install the Grub bootloader to the correct device (the flash drive). If you are worried, just disconnect the hard drive, that way nothing can go wrong. :)

A 4gb drive should work, but 8gb or larger will give you room for your documents.

---

### Post by LIB53 on 2009-08-07
I have a question that's congruent with this topic:

After you do a regular install of Ubuntu on a flash drive, will it only be usable on that particular computer, or will it work with any other computer? If the answer is no, do you mean it wouldn't even boot on identical hardware?

---

### Post by snowpine on 2009-08-07
> **LIB53 said:**
> I have a question that's congruent with this topic:

After you do a regular install of Ubuntu on a flash drive, will it only be usable on that particular computer, or will it work with any other computer? If the answer is no, do you mean it wouldn't even boot on identical hardware?

It will work on any computer, with one possible exception. I have read this on the forums--but can't speak from personal experience--that switching between computers with different video cards can cause some minor graphics problems.

---

### Post by Dark Aspect on 2009-08-07
> **LIB53 said:**
> I have a question that's congruent with this topic:

After you do a regular install of Ubuntu on a flash drive, will it only be usable on that particular computer, or will it work with any other computer? If the answer is no, do you mean it wouldn't even boot on identical hardware?

You can use it across computers so long as you don't install 3D drivers, also make you that you can boot off USB in your bios. I also think that you might wanna look into [Puppy Linux]("http://www.puppylinux.org/"), its smaller and made for USB installation where as Ubuntu didn't necessary have that in mind.

---

### Post by MelDJ on 2009-08-08
try [www.pendrivelinux.com](www.pendrivelinux.com)

---

