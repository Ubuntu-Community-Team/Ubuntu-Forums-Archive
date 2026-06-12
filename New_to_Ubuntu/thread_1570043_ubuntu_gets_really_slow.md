---
title: "ubuntu gets really slow"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by jatov on 2010-09-07
I just installed ubuntu-8.04.1-desktop-powerpc. Installation  went perfectly as far as I can tell. Everything runs fine but after a  while ubuntu becomes painfully slow. Everything is working just really  slow. After a reboot everything is normal again but in time slows down again. Any ideas?

---

### Post by LowSky on 2010-09-07
what applications are you running... more than likely you might have some applications running behind the scene that are bogging down the PC.

Firefox could also be an issue because of how it caches data. take a look there.
[http://kb.mozillazine.org/index.php?title=Reducing_memory_usage_-_Firefox&printable=yes](http://kb.mozillazine.org/index.php?title=Reducing_memory_usage_-_Firefox&printable=yes)

---

### Post by Bölvaður on 2010-09-07
while you are running ubuntu, right from the start open up *System &#8594; Administration &#8594; System Monitor* and have the graphs open, when you see something abnormal you can switch to the processes tab and see which process is doing this.

at least that is the beginning.

---

### Post by sanderd17 on 2010-09-07
> **Bölvaður said:**
> while you are running ubuntu, right from the start open up *System &#8594; Administration &#8594; System Monitor* and have the graphs open, when you see something abnormal you can switch to the processes tab and see which process is doing this.

at least that is the beginning.

Certainly look for the swap percentage, if that grows too big (over 10%), the computer becomes slow.

---

### Post by jatov on 2010-09-07
> **LowSky said:**
> what applications are you running... more than likely you might have some applications running behind the scene that are bogging down the PC.

Firefox could also be an issue because of how it caches data. take a look there.
[http://kb.mozillazine.org/index.php?title=Reducing_memory_usage_-_Firefox&printable=yes](http://kb.mozillazine.org/index.php?title=Reducing_memory_usage_-_Firefox&printable=yes)

Most of the time it's just system stuff. The last time it happened I was only running the Software Update Manager.

---

### Post by Gone fishing on 2010-09-07
Try running top from a terminal I think its installed by default if not sudo apt-get install top.

It lists all the programs and how much CPU memory etc they are using

---

### Post by sanderd17 on 2010-09-08
> **jatov said:**
> Most of the time it's just system stuff. The last time it happened I was only running the Software Update Manager.

It's possible some application starts at computer startup and that app makes your computer slow. To see that, you need to check the "System Monitor" or watch "top". I find the "System Monitor" easier to watch at.

---

### Post by JohnHeikkila on 2010-09-08
Perhaps it's the text anti-aliasing. I've met people who say their computer gets slow when the text/font anti-aliasing/rendering is on.

---

