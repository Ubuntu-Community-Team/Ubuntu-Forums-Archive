---
title: "Switching Between Ubuntu and Windows"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by HelpMeWithOSS on 2009-07-12
Hello,
 
Can someone help me? 
 
Is there any way I can switch between Windows and Ubuntu without turning off the computer? Right now I just hit the Restart button then insert the CD and have Ubuntu run.
 
Thanks!!!

---

### Post by nynoah on 2009-07-12
NO.......... not unless you are running virtual box.  Ubuntu is not a program it is a whole operating system.

---

### Post by esalnoj on 2009-07-12
Install ubuntu as your main OS, then run windows in virtualbox3.

Be sure to backup your documents from windows first!

---

### Post by Rocket2DMn on 2009-07-12
Are you currently running Ubuntu from a live session on the desktop CD?  A computer can only have 1 operating system running at a time since it controls the hardware.  If you need quick access to another operating system but don't want to reboot, the best option is to install the other OS in a virtual machine (VM) using a program like VirtualBox, which is pretty user friendly.  So, say you're in Ubuntu and want to access a Windows program - if you have Windows installed in a VM, you can just turn this on without shutting down the computer.  It's not as useful for doing intensive operations like playing high end videogames, but it is useful.

---

### Post by nhasian on 2009-07-12
you would need to install both operating systems on the computer and then dual boot, or run one of the operating systems in a virtual machine.  another method no one has suggested yet is if you have two separate computers you can attach one keyboard/monitor/mouse with a kvm switch (not to be confused with the kvm program)

> **HelpMeWithOSS said:**
> 
Is there any way I can switch between Windows and Ubuntu without turning off the computer? Right now I just hit the Restart button then insert the CD and have Ubuntu run.

---

### Post by peakpc on 2009-07-12
If you are still using the CD to run Ubuntu you have two options if you want to keep your current Windows setup.  Option one is to load Ubuntu using WUBI which installs Ubuntu on a virtual drive which can be uninstalled like a windows program (it is alittle slower than option two but not as slow as running from the CD).  Option two is to install Ubuntu in a dual boot setup Partitioning a section of the hard drive for Ubuntu to live and Grub will control which Operating System will start. either setup however, will require a reboot the switch between them.

---

