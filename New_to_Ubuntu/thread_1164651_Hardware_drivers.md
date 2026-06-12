---
title: "Hardware drivers"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by moodooda on 2009-05-19
If I do a full Ubuntu install on my PC and wipe Windows will my Ethernet connection work?


Do I need the drivers that came pre installed with my PC?

---

### Post by Zzl1xndd on 2009-05-19
Normally installing additional drivers are not required with Ubuntu. However I would recommend trying the Live CD first to ensure everything works.

---

### Post by HDave on 2009-05-19
Linux has built in support for almost every Ethernet driver made.  Other things may have issues, but not ethernet.

If you want to be sure, boot from an Ubuntu live CD and check it out.  If it works that way, it'll work when you install it.

---

### Post by moodooda on 2009-05-19
> **HDave said:**
> Linux has built in support for almost every Ethernet driver made.  Other things may have issues, but not ethernet.

If you want to be sure, boot from an Ubuntu live CD and check it out.  If it works that way, it'll work when you install it.
I have it installed inside Windows I am thinking of taking the dive and doing the full install.

Everything works fine I think I will take the dive fingers crossed.

Thanks for the quick answers.

If Ubuntu can do this why can't windows?

---

### Post by 3rdalbum on 2009-05-19
> **HDave said:**
> Linux has built in support for almost every Ethernet driver made.

HDave actually means "Linux has built-in support for almost every Ethernet **controller** made". You don't actually use Windows drivers on Linux. I second the suggestion of trying the live CD (which is actually called the Desktop CD) to see how things work before doing the installation.

---

### Post by HDave on 2009-05-19
3rdalbum is correct -- thanks.

When you say you are running it inside windows do you mean from having used WUBI or within a virtual machine like vmware?

If you've been using WUBI and it works, then a full install will work.

Ubuntu can do many things that Windows can't do.  Microsoft has lots of programmers on staff, but nobody can match the millions of committed Linux users and programmers who work hard to make it better every day.  So welcome! :D

---

### Post by moodooda on 2009-05-19
> **HDave said:**
> 3rdalbum is correct -- thanks.

When you say you are running it inside windows do you mean from having used WUBI or within a virtual machine like vmware?

If you've been using WUBI and it works, then a full install will work.

Ubuntu can do many things that Windows can't do.  Microsoft has lots of programmers on staff, but nobody can match the millions of committed Linux users and programmers who work hard to make it better every day.  So welcome! :D

Well I have done the full install and Windows is gone.

Everything I want to use just works.

If I install the wrong copy of Windows I would need to search for drivers not an easy thing to do with no connection driver.

Why can't windows just do the same?

And everyone thanks for the help.:)

---

### Post by 3rdalbum on 2009-05-19
> **moodooda said:**
> If I install the wrong copy of Windows I would need to search for drivers not an easy thing to do with no connection driver.

Why can't windows just do the same?

That's an excellent question. I don't know the reason for sure, but this is why I believe Microsoft doesn't ship drivers.

On Linux, there is a lot of code reuse. Code that is used within multiple drivers tends to get loaded only once, and each driver that requires it will just call it. This is done for efficiency. It can be done on Linux because the drivers are open-source, and are maintained by community individuals.

On Windows, drivers are proprietary and are written by hardware manufacturers. Hardware manufacturers are not interested in extra efficiency if it means having to expose part of their code to competitors. As a result, drivers on Windows tend to be pretty big and comparatively not well-behaved - they are all completely self-contained and there's no interest in testing different combinations of hardware and software.

If Microsoft shipped a large number of drivers with Windows, then Windows would take up two DVDs and be rather unstable because all the different drivers are competing with eachother.

The real solution is for all hardware manufacturers to adopt standards. The reason why you don't need an extra driver in order to use a DVD burner or a USB flash drive is because all the manufacturers agreed on a standard for interacting with these devices, and so all operating system developers could write a single driver that interacts with a whole class of devices.

Unfortunately, most things don't have a standard driver, but we can always write to hardware manufacturers and try and push them along! A standard driver means that all supported devices will work out-of-the-box on all platforms, have much fewer bugs, support won't be broken with new operating systems... and manufacturers can cut software development costs or put the saved money into building better devices. A win-win situation for everybody!

---

### Post by moodooda on 2009-05-19
> **3rdalbum said:**
> That's an excellent question. I don't know the reason for sure, but this is why I believe Microsoft doesn't ship drivers.

On Linux, there is a lot of code reuse. Code that is used within multiple drivers tends to get loaded only once, and each driver that requires it will just call it. This is done for efficiency. It can be done on Linux because the drivers are open-source, and are maintained by community individuals.

On Windows, drivers are proprietary and are written by hardware manufacturers. Hardware manufacturers are not interested in extra efficiency if it means having to expose part of their code to competitors. As a result, drivers on Windows tend to be pretty big and comparatively not well-behaved - they are all completely self-contained and there's no interest in testing different combinations of hardware and software.

If Microsoft shipped a large number of drivers with Windows, then Windows would take up two DVDs and be rather unstable because all the different drivers are competing with eachother.

The real solution is for all hardware manufacturers to adopt standards. The reason why you don't need an extra driver in order to use a DVD burner or a USB flash drive is because all the manufacturers agreed on a standard for interacting with these devices, and so all operating system developers could write a single driver that interacts with a whole class of devices.

Unfortunately, most things don't have a standard driver, but we can always write to hardware manufacturers and try and push them along! A standard driver means that all supported devices will work out-of-the-box on all platforms, have much fewer bugs, support won't be broken with new operating systems... and manufacturers can cut software development costs or put the saved money into building better devices. A win-win situation for everybody!

Thanks you know your stuff.

---

