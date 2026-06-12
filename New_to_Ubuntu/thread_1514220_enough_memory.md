---
title: "enough memory?"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by maroofi on 2010-06-20
hi
when i use free command in bash to get the memory status, this is the result :
                    total       used       free     shared    buffers     cached
Mem:        509152     460436      48716          0      21712     222028
-/+ buffers/cache:     216696     292456
Swap:       453624       7036     446588

i have a 512 MB ram on my laptop and as you can see the used memory is 460MB and it only has 48MB free. this is when only the bash window is open.is that enough memory?
does linux have something like pagesys in windows or maybe somehow use hard drive as memory or somethin like that? should i do somethin about it?
when i use ubuntu system the fan of my laptop always work...
laptop : hp compaq nc6000
cpu 1.4 GHz
ram 512 MB
hard 38 GB

thx

---

### Post by Pollox on 2010-06-20
Pay attention to the second line, as this indicates how much memory you are using without counting buffers/cache.  You have enough memory, although you would probably benefit from having more.  The swap acts like the pagesys in Windows, and it also takes the place of the hibernate file.

Edit: Also, "free -m" gives more readable results by using MB as the unit.

---

### Post by maroofi on 2010-06-20
aha...i got it.so it is enough...
long way to learn ubuntu.

---

### Post by nhasian on 2010-06-20
just out of curiosity, have you tried running [Lubuntu]("http://lubuntu.net/blog/lubuntu-1004-now-available-download")?  I imagine it would be a lot snappier with your system specs.

---

### Post by Ozymandias_117 on 2010-06-20
Might even be worth trying to do a minimal install and only putting on what you need.

---

### Post by k3lt01 on 2010-06-21
> **Ozymandias_117 said:**
> Might even be worth trying to do a minimal install and only putting on what you need.Or stopping start up applications and services that the PC will never use. I stop Bluetooth because my laptop doesn't have that capability so it's of no use.

---

### Post by PremiereWebDesign on 2010-06-21
I am running Xubuntu on an old Dell dimension 3000 with only 512MB of RAM. And it does fine. You may want to look at Xubuntu.

---

### Post by k3lt01 on 2010-06-21
I'm running Lucid Ubuntu on an old Acer laptop with only 256mg of RAM. Disabling services that aren't needed and uninstalling ureadahead does wonders (sorry keybuk but ureadahead is still a huge bottleneck on low RAM systems)

---

### Post by Serpher on 2010-06-21
Your swap partition is the same thing as Windows page memory.

---

### Post by maroofi on 2010-06-21
guys , microsoft windows xp was the only os i ve worked with.until my friend told me about ubuntu.i dont know about xubuntu or kubuntu or .... and after 3 days working with ubuntu,guess what?
_i realy love it _and i dont wanna switch to anything else.i am just worry about my laptop fan that works all the time i come up with ubuntu.

---

