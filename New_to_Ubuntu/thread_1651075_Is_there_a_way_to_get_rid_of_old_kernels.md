---
title: "Is there a way to get rid of old kernels?"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by RichieB07 on 2010-12-22
When I boot into my computer, it gives me three different kernels I can log into for Ubuntu (the three most recent).  Is there a way to get rid of these?  And more importantly, is it safe to get rid of them?

If there isn't I'm fine with it, just wondering because Ubuntu is so flexible I figure there is a way.

Thanks for all your time and responses!

---

### Post by oldos2er on 2010-12-22
Sure, you can remove any unwanted kernels with Synaptic package Manager, search for 'linux-image' and mark the ones you don't want for removal. I like to keep at least two, "just in case."

---

### Post by lykwydchykyn on 2010-12-22
Just search for them in Synaptic or whatever package manager you use and uninstall them like any other software package.  As long as you have at least one (preferably the one currently running) you're fine.

---

### Post by drs305 on 2010-12-22
Another option if you like GUI's is Ubuntu Tweak. Here are the details:
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by RichieB07 on 2010-12-22
Thank you all so much, greatly appreciated!  I'll mark this one as solved.

---

### Post by karthick87 on 2010-12-22
- Open **Ubuntu Tweak**
- Click on **Package Cleaner** under **Applications** in the left-hand pane
- On the right side of the cleaning view press **Clean Kernels** 
- Select all kernels - I think the one in use is not listed but just in case check running 
**uname -a** in a terminal

---

### Post by RichieB07 on 2010-12-22
> **karthick87 said:**
> - Open **Ubuntu Tweak**
- Click on **Package Cleaner** under **Applications** in the left-hand pane
- On the right side of the cleaning view press **Clean Kernels** 
- Select all kernels - I think the one in use is not listed but just in case check running 
**uname -a** in a terminal


That worked amazing!  I also found a lot of junk that was left over from other programs I have deleted, thanks!

---

### Post by karthick87 on 2010-12-22
You are welcome :)

---

