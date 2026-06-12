---
title: "Support for Intel GM4500HD graphics?"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by msu3 on 2009-02-01
Hi all,

I just got Ubuntu a week ago and was wondering if I have to wait for another kernel release before I can get the video drivers on my Dell Inspiron 1545 to work. Right now, I've searched and haven't found any solutions. Do most distros right now have about the same amount of graphics drivers supported? Would I have a better shot at getting the right drivers with Fedora or openSUSE?

Thanks,
Mike

---

### Post by igknighted on 2009-02-01
What do you mean "they don't work"?

I have a 4500mhd in my laptop and works great with the Ubuntu drivers.

The intel graphics driver isn't in the kernel (well, it isn't tied to the kernel at least).  Visit [http://intellinuxgraphics.com](http://intellinuxgraphics.com), the latest version of the driver is 2.6.1 (Ubuntu ships 2.4.1).  If you want to try the latest driver, I would recommend the intel graphics testing PPA on launchpad rather than compiling from source though.

FWIW, Fedora 10 and OpenSuse 11.1 shipped with version 2.5, so it is newer than Ubuntu's.  You can also use the very latest by downloading the latest alpha release of Ubuntu 9.04.

But start with the first question... what doesn't work.  Often times there are simply some small configuration changes that can be made.

---

### Post by b_sisco on 2009-02-02
I have Fujitsu-Siemens lap-top with Intel GM4500HD and also I have problem with installing Ubuntu 8.10 (and Ubuntu 7.10).
During installation I obtain black screen.
Also I can not start live CD, there some error messages duu to display adapter.
Any suggestions?
Thanks in advanse
Mitko

---

### Post by smeech1 on 2009-02-02
> **msu3 said:**
> I just got Ubuntu a week ago and was wondering if I have to wait for another kernel release before I can get the video drivers on my Dell Inspiron 1545 to work. Right now, I've searched and haven't found any solutions. Do most distros right now have about the same amount of graphics drivers supported? Would I have a better shot at getting the right drivers with Fedora or openSUSE?


Works absolutely fine here, Ubuntu v8.10 straight out of the box (well, off the Linux Format DVD). Video, wireless, the lot. Completely removed Vista and now have XP/Kubuntu dual-boot.

---

### Post by msu3 on 2009-02-12
Perhaps I meant to ask, would there be any prospect of openGL 2.1 or better 3D performance in the future? It works fine, just wondering if I'd be able to play any games along with learning some basics of linux.

---

