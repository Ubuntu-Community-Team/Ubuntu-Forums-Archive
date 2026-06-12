---
title: "How to find certain information"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by VideoAddicted on 2010-06-16
Many times when trying to download a file, I have to know whether or not I am using 64-bit or 32-bit.  Also, among other things, I want to know what my processing power is.  Now I know that this is a very noobie question but where can you find out this kind of information.  Without it, it is very difficult to download anything because I don't know which file I need to download.  Any help would be greatly appreciated.

I read that you can use sysinfo.  So I installed and ran it, but nothing happened...

I'm using 8.04 if that helps...

---

### Post by spiky001 on 2010-06-16
in terminal 
```
uname -a
```

32 bit reports I686
64 bit is x86_64

---

### Post by tendonstrength on 2010-06-16
Try going to System -> Administration -> System Monitor. The system tab should have all the info you need. If it doesn't say anything about x64 on that tab, I'm pretty sure that means you are running 32-bit.

---

### Post by tendonstrength on 2010-06-16
Actually the system monitor may not have info about 64 vs. 32-bit, but it will have your processor info. 

Also it would be x86_64 instead of x64 (which you can find using uname as stated).

---

### Post by bodhi.zazen on 2010-06-16
cat /proc/cpuinfo

---

### Post by VideoAddicted on 2010-06-22
thx, that helped a lot

---

### Post by Matt__ on 2010-06-22
This will probably suit your needs in a more GUI way :P

```
sudo apt-get install hardinfo
```it will appear under Applications - system tools as System Profiler and Benchmark, or you can open a terminal and type hardinfo.



[COLOR=White].[/COLOR]

---

