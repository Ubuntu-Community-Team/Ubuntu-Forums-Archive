---
title: "Processor Speed"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by unicycle boy on 2009-08-29
Hi, I've just started using ubuntu and mostley its going great - but when I try to do things such as view videos on the internet and play simple games it is very jumpy. 
I think the problem might be something to do with the processor as the system monitor has both CPU1 and CPU2 running at over 50% - often jumping up to about 80% when I am doing very little.
I ran 'cat /proc/cpuinfo' and it tells me that both my CPU's are 525MHz, which sounds very low.
The hardware I have is a AMD Turion X2 processor 2.1GHz, and Nvidia geforce 8200M graphics.
If any more infomation is needed, please say.
Thanks very much

---

### Post by Liolikas on 2009-08-29
You have proprietary nivida drivers or not?

---

### Post by NoaHall on 2009-08-29
System -> Admin -> Hardware Drivers 
(to install the drivers if you don't have them)

---

### Post by unicycle boy on 2009-08-29
Yep - I have the nvidia 180 driver (the computor was much slower before I added that, but it still seems a bit slow)

---

### Post by NoaHall on 2009-08-29
It's probably a problem cause by flash. 
Try installing the one from the official website, and see if anything changes

---

### Post by Liolikas on 2009-08-29
Maybe try bios upgrade then.

---

### Post by unicycle boy on 2009-08-29
How would I upgrade my bios? Sorry, I'm very new to this

---

### Post by NoaHall on 2009-08-29
Do not attempt to upgrade your bios if you haven't done it before! It can cause major damage, and may make your system un-usable.

It's almost certainly a flash problem. Do as I recommended.

---

### Post by donkyhotay on 2009-08-29
+1 for updating flash

Flash doesn't ever seem to run as well on linux as it does on windows.

---

### Post by earthpigg on 2009-08-29
hi,

flash is probably the problem, as others have suggested.

however, there may be a less drastic problem (and solution) before making any software changes:

> the problem might be something to do with the processor as the _***system monitor***_ has both CPU1 and CPU2 running at over 50%

run this command from a terminal:

> top

and see what is at the top of the "CPU%" column. there may be some program running in the "background" that is slowing your computer down. 'remote desktop viewer' is often a culpurit. or it could be the system monitor itself.

you should ***_not_*** be leaving the gnome system monitor applet running all the time - that thing is a horrible resource hog (including CPU%). it may constantly be spending 40% of your CPU cycles trying to calculate what is constantly using up your CPU cycles. idiocy!

if you want something with similar functionality that you can leave open to check out what your computer is doing that is *not* such a hog, install and use htop.

> sudo apt-get install htop

to run it:
> htop

---

### Post by unicycle boy on 2009-08-29
Thanks for the advice - I think I have mostly sorted it out.
The system monitor does use a lot when it is running - so i will replace it with the other program soon. The problem seemed to be that the processors were only running at 525Mhz each - so I have added panels with CPU frequency scaling at the top, and when I change it to performance mode it works well. However I still have a bit of lag when watching videos and using other programs at the same time? Is this expected from a laptop (Compaq Presario CQ60-430SA)

---

### Post by NoaHall on 2009-08-29
This is a problem due to either your graphics card or flash. Flash is most likely.

---

