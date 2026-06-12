---
title: "Getting system info"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by JavaKid on 2011-03-09
I've loaded up Server, but I think I would prefer to have the desktop.
I'm not sure, but I think I want the 64 bit, but I don't remember what processor I
have in the machine. 

What command line command can I use to get system info like that?

I think its a 64 bit processor, but I'm not sure.

Many Thanks !

---

### Post by Rubi1200 on 2011-03-09
The following commands can help:

```
uname -a
```
shows kernel version and processor type e.g. 32 or 64 bit

```
lspci
```
lists PCI devices

```
sudo lshw
```
lists hardware

---

### Post by Paddy Landau on 2011-03-09
Use this command:
```
grep -c '^flags.* lm ' /proc/cpuinfo
```If it shows 0 (zero), you have 32-bit hardware. Otherwise, you have 64-bit hardware.

Use this command:
```
uname -m
```If it shows i686, then you have 32-bit Ubuntu running, otherwise you have 64-bit Ubuntu running.

---

### Post by aeiah on 2011-03-09
as you can see, there are lots of ways. i find the best thing to do is use lshw with html output for easy viewing.

```

sudo lshw -html > hardware_profile.html
```

to see what operating system you're currently running, do uname -a as suggested

---

### Post by xptional on 2011-03-09
Thanks AEIAH, 

its so easy to read the output in html file as compared to see it on the terminal. thanks for advicing it ..

---

### Post by Paddy Landau on 2011-03-09
> **xptional said:**
> Thanks AEIAH, 

its so easy to read the output in html file as compared to see it on the terminal. thanks for advicing it ..
Agreed, it is nice and easy.

@aeiah: I'm puzzled why two of my entries are listed in red and another in pink?

---

### Post by alexis44 on 2011-03-09
I got this little program from the Software Center called SysInfo, I think.  It gives me the info, but it seems to crash a lot. ;)

---

### Post by xptional on 2011-03-09
> **Paddy Landau said:**
> Agreed, it is nice and easy.

@aeiah: I'm puzzled why two of my entries are listed in red and another in pink?

I was also surprised to see why there is color distinction ? Dont know but there should be a reason ..

---

### Post by Frogs Hair on 2011-03-09
Some of these are useful.[http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

---

### Post by Rubi1200 on 2011-03-09
> **Frogs Hair said:**
> Some of these are useful.[http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)
Excellent link! 
I've used that many times.

---

### Post by nowtejas on 2012-02-08
> **aeiah said:**
> as you can see, there are lots of ways. i find the best thing to do is use lshw with html output for easy viewing.

```

sudo lshw -html > hardware_profile.html
```

to see what operating system you're currently running, do uname -a as suggested

The best way I used so far..!! :)

Thank you AEIAH..! :)

---

### Post by oldos2er on 2012-02-08
Closed, necromancy.

---

