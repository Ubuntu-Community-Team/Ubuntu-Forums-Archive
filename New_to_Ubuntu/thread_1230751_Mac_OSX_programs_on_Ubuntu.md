---
title: "Mac OSX programs on Ubuntu?"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by Grifulkin on 2009-08-03
Okay so I was on Wikipedia just looking up random stuff and came across the fact that Mac OSX is a unix system.  And I know the linux kernel is a derivative of the Unix kernel.  Now my question is, is it theoretically possible to use programs written for mac and install them on Ubuntu?

This question comes about because I read the other day that the Linux kernel can run programs designed for the Unix kernel without much problem.

---

### Post by llamabr on 2009-08-03
If you can get the source, probably.  mac osx uses a sort of bsd kernel.

Most of the things you'll find for download will be closed source, and so not compiled for use on your system.

What, exactly, app did you have in mind?

---

### Post by juancarlospaco on 2009-08-03
CocoTron can run OS X programs on Linux, 
still under development, 
its kinda wine thing but for running OS X apps

---

### Post by cabrey on 2009-08-03
No as OS X apps usually use the Cocoa framework which is proprietary. Unless a project is started that does what WINE does but for the Mac, I don't see OS X apps ever running on Linux.

---

### Post by OutOfReach on 2009-08-03
> **Grifulkin said:**
> Okay so I was on Wikipedia just looking up random stuff and came across the fact that Mac OSX is a unix system.  And I know the linux kernel is a derivative of the Unix kernel.  Now my question is, is it theoretically possible to use programs written for mac and install them on Ubuntu?

This question comes about because I read the other day that the Linux kernel can run programs designed for the Unix kernel without much problem.

No Mac OS and Linux are not directly related, so no I would say that Mac apps cannot natively run on Linux unless it was made cross-platform compatible

---

### Post by Grifulkin on 2009-08-03
Thank you, everyone, I was just wondering thats all, just curious.

---

### Post by schauerlich on 2009-08-03
Most OS X apps use Cocoa, which is proprietary and not Unix related. However, anything written for the POSIX API (not much) should run on Ubuntu without issue.

---

### Post by juancarlospaco on 2009-08-05
> **cabrey said:**
> OS X apps usually use the Cocoa framework which is proprietary. Unless a project is started that does what WINE does but for the Mac,

CocoTron is reverse ingeneering the Cocoa thing, 
but still under development ATM.

Remember that Wine started as a 
*"project to try to run Windows 3.0 apps on Linux"*
 and see what they do with years of development.
*Some day...*

---

