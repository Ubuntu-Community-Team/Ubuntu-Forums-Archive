---
title: "Gnome not working?"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by Poincare101 on 2009-08-17
I've installed ubuntu 9.04 on my dell inspiron 1100 (old). 
I have already loaded a bunch of software, updated everything. I shut it down a little while ago. But, now, whenever I try to load ubuntu (this issue comes after grub). It gives the little sound (drums) that comes before login, but the screen goes blank. I've tried Alt+f1 and that doesn't work either.

---

### Post by BslBryan on 2009-08-17
Have you tried blindly logging in?

---

### Post by rocknrolf77 on 2009-08-17
Start recovery mode in grub and then choose try to fix the xserver or something like that.

What kind of graphics-card do you have?

---

### Post by Poincare101 on 2009-08-17
> **BslBryan said:**
> Have you tried blindly logging in?

I blindly logged in, and it loaded, then I did
Ctrl+Alt+F1. It gave me a console, then I did

Ctrl+Alt+F7 and it worked.

But, why do I have to do this? How can I fix it?

EDIT: Also, it only works in old kernel. In the new kernel, even the login sounds don't occur..

---

### Post by Poincare101 on 2009-08-17
anyone?

---

### Post by BslBryan on 2009-08-17
Wow, this is really puzzling.

The first thing I would do if I was in your position would be to enter the GRUB menu (press Esc) as it boots up, and select the newest kernel that is followed by "recovery mode."  Once there, navigate to "xfix."  This process should be done in a very short time. (So short that you might not think that it actually worked! :-P)  

From there, resume normal boot.   

I've got another idea or two, but let's see if this works first. :)

---

### Post by Poincare101 on 2009-08-17
yay!

That seems to have fixed it :)

But, why did that happen in the first place? Should I report this to canonical or the members of kernel.org ?

---

### Post by BslBryan on 2009-08-17
Good.  

Your graphics card's driver probably just had different settings that no longer applied to the updated kernel.  It should be fixed now. :-)

---

