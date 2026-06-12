---
title: "Not seeing all the RAM...."
date: 2011-03-11
forum: New to Ubuntu
---

### Post by Jim2029 on 2011-03-11
I have Ubuntu 10.10 64bit installed. I have 4GB ram in this laptop. I have 128MB going to video as its the max allowed in the bios... But yet Ubuntu only see 3.6GB ram.

So where did the rest go???

Thanks.

---

### Post by blind2314 on 2011-03-11
What tool/command did you use to see the available RAM? copy/paste results if possible

---

### Post by Jim2029 on 2011-03-11
> **blind2314 said:**
> What tool/command did you use to see the available RAM? copy/paste results if possible

Just using the System monitor in Ubuntu. [http://goput.it/str/442.png](http://goput.it/str/442.png)

---

### Post by Joe of loath on 2011-03-11
My laptop says similar. I'm assuming you have integrated graphics?

---

### Post by Jim2029 on 2011-03-11
> **Joe of loath said:**
> My laptop says similar. I'm assuming you have integrated graphics?

Yes I do, but I ahve 128mb going to video leaving 272mb just out having a good time somewhere??? I know its not much, but just wondering where it went.

---

### Post by uRock on 2011-03-11
The missing RAM is being used by the system for graphics. 128MB on the GPU is not enough.

---

### Post by clhsharky on 2011-03-11
Jim2029


Depending on MB BIOs, many devices and chips are mapped in memory.
I have dedicated video card, and my board takes .1 GiB memory.
Also are you using 32bit or 64bit OS?


Sharky

---

### Post by b0b138 on 2011-03-11
Im sure its fine. Look at the output of the free command

---

### Post by Jim2029 on 2011-03-11
> **b0b138 said:**
> Im sure its fine. Look at the output of the free command

root@jim-HP-Pavilion-dv6700-Notebook-PC:/home/jim# free
             total       used       free     shared    buffers     cached
```
Mem:       3799760    1541488    2258272          0     113668     833476
-/+ buffers/cache:     594344    3205416
Swap:     11128828          0   11128828
```
I've only been using this since last December when I tried 10.10 and everything on this laptop worked.

---

