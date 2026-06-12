---
title: "System info"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by beano0528 on 2009-10-23
Is there some way that I can pull up system information on Ubuntu about my computer?  Things like what processor I am using, video cards, RAM space, hard disk space, etc.

---

### Post by arrange on 2009-10-23
Try [hardinfo]("http://hardinfo.berlios.de/HomePage").

---

### Post by The Real Dave on 2009-10-23
if you open terminal, and type in 

```
sudo lshw > hardware.txt
```

it will give you a big long list of your hardware, as a text file named hardware in your home directory

---

### Post by diesch on 2009-10-23
hardinfo is available in the universe repository.

---

### Post by Jaraxle on 2009-10-23
You can also use cat /proc/cpuinfo to show info for your processor, and cat /proc/meminfo will show system memory.

You can run sudo lspci to show PCI bus info, including any PCI video cards. There's also a command to show hard drive info but I can't remember what it is.

---

### Post by AlphaLexman on 2009-10-23
> **arrange said:**
> Try [hardinfo]("http://hardinfo.berlios.de/HomePage").

I like hardinfo, but I don't like to keep it running/open all the time if you are looking for a option to monitor usage, try conky or gkrellm. Both are in the repo's.

---

### Post by cascade9 on 2009-10-23
> **arrange said:**
> Try [hardinfo]("http://hardinfo.berlios.de/HomePage").

+1. Brilliant little program

---

### Post by beano0528 on 2009-10-23
> **diesch said:**
> hardinfo is available in the universe repository.
I'm a beginner here.  Could you explain this?

---

### Post by diesch on 2009-10-23
You can install hardinfo by installing the package "hardinfo" using Synaptic.

---

### Post by beano0528 on 2009-10-23
K.  Thanks, but now where do I go to use it?

---

### Post by QIII on 2009-10-23
There is also an application in Synaptic called sysinfo.

If you are unfamiliar with how to use the Synaptic Package manager, have a look at the free .pdf file here...

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)


SysInfo gives you a nice graphical interface and probably more detail than you care to look at.  

hardinfo is great if you really want the nuts and bolts technical stuff.

---

### Post by cascade9 on 2009-10-23
> **beano0528 said:**
> K.  Thanks, but now where do I go to use it?

I cant remember where it goes in the..er...start menu? (yes, I know, someone will set me right) but console-> hardinfo    will bring it up

---

### Post by QIII on 2009-10-23
Applications | System/tools?

---

### Post by jmszr on 2009-10-23
In 8.04, at least, hardinfo is under System > Preferences > System Profiler and Benchmark.

---

