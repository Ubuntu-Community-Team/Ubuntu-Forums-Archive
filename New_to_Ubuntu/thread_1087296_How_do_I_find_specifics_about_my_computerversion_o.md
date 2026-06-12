---
title: "How do I find specifics about my computer/version of Ubuntu?"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Edward B. on 2009-03-04
On Windows, I would simply go to My Computer where I could see my RAM, Processor, and version of Windows I had installed.

Where can I find this on Ubuntu?

Thanks!

---

### Post by RedSingularity on 2009-03-04
System>Administration>System Monitor.

---

### Post by RedSingularity on 2009-03-04
For a more advanced interface with ALOT more info go to terminal and type, "sudo apt-get install gnome-device-manager"
Once installed it will be under System Tools

---

### Post by linux phreak on 2009-03-04
Install sysinfo.Type "sudo apt-get install sysinfo" into the terminal.

---

### Post by wolfen69 on 2009-03-04
do 
```
man uname
```
for options

---

### Post by Kareeser on 2009-03-04
uname -a

and...

lshw

---

### Post by Edward B. on 2009-03-05
> **Shadow121 said:**
> For a more advanced interface with ALOT more info go to terminal and type, "sudo apt-get install gnome-device-manager"
Once installed it will be under System Tools

Thanks! And a follow up stupid question. How do I get to the terminal?

Also, in the system monitor screen, under file system it only shows one device... this means that (as I want it to be) there is no partitioning, just a single system?

Thanks!

---

### Post by stchman on 2009-03-05
> **Edward B. said:**
> On Windows, I would simply go to My Computer where I could see my RAM, Processor, and version of Windows I had installed.

Where can I find this on Ubuntu?

Thanks!

System--->Preferences there is a System app that shows you what you want.

---

### Post by RedSingularity on 2009-03-05
> **Edward B. said:**
> Thanks! And a follow up stupid question. How do I get to the terminal?

Also, in the system monitor screen, under file system it only shows one device... this means that (as I want it to be) there is no partitioning, just a single system?

Thanks!

Get to terminal through Accessories>Terminal.  And under file system, that just reads the different hard drives you have attached to the computer.  It does not show partitioning.  If you want to show partitioning you need to get partition editor.  Get this by typing in terminal "sudo apt-get install gparted".

---

