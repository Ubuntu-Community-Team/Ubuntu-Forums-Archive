---
title: "Doubt about boot menu entries"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by PFN on 2009-08-10
I am new to Linux and using Ubuntu-9.04 for 3 months and I am dual booting with Windows XP.
Now after some updates, there are many entries in my boot menu like:
 2.6.28.15 generic
 2.6.28.15 recovery mode
 2.6.28.14 generic
 2.6.28.14 recovery mode
 2.6.28.13 generic
 2.6.28.13 recovery mode
 2.6.28.12 generic
 2.6.28.12 recovery mode
 2.6.28.11 generic
 2.6.28.11 recovery mode
 memtest+86
 other operating systems
  Microsoft windows

This is confusing me and I like to know that am I really need all these kernels or can I remove the older versions.
If I have to do it manually then I need help.
Please spend a while for this newbie, Thanks in advance.

---

### Post by Paddy Landau on 2009-08-10
Each time you have a new kernel (an important upgrade), you get a new menu entry.

In this case, you have kernels 2.6.28.11 through 2.6.28.15, and for each one you have the normal boot and the recovery (just in case) boot.

We recommend that you keep the latest two (in your case, 2.6.28.14 and 2.6.28.15), and you can safely get rid of the rest (provided that you've successfully booted from the latest version).

Here is how to get rid of earlier kernels:

[LIST=1]
[*]Ensure that you've booted into the latest kernel (in your case, 2.6.18.15).
[*]Go to System > Administration > Synaptic Package Manager.
[*]Select Status (on the left near the bottom) > Installed (on the left near the top).
[*]Search for all of the following, and mark them for "complete removal". N.B. Ensure that you *only* select the versions that you want to get rid of; in this case, 2.6.18.11 through 2.6.28.13. Do *not* select the latest two, in this case 2.6.28.14 or 2.6.28.15.
[LIST]
[*]linux-headers
[*]linux-image
[*]linux-ubuntu-modules
[*]linux-restricted-modules
[/LIST]
 
[*]Press Apply.
[/LIST]
To clarify point 4, choose only those with the right version, e.g. linux-image-2.6.18.11-generic, but do not choose linux-image-generic.

By the way, what version of Ubuntu are you using? Your numbers seem a little out of date.

---

### Post by PFN on 2009-08-10
Thanks.

---

### Post by PFN on 2009-08-10
Thanks Paddy Landau,
I had successfully followed your suggestion and solved my problem.
But I couldn't get the last sentence of your message("By the way, what version of Ubuntu are you using? Your numbers seem a little out of date") because I did my latest update of Ubuntu-9.04 jaunty today and my kernel get updated from 2.6.28-14 to 2.6.28-15.
If I can update the kernel further please help me a little more.
Thank you once more.

---

### Post by Paddy Landau on 2009-08-10
> **PFN said:**
> I couldn't get the last sentence of your message...
Sorry, I misread "28" as "18". Oops!

---

### Post by Ric_NYC on 2009-08-10
Thanks, Paddy.

---

