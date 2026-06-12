---
title: "nvidia driver problem, please help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by antez on 2009-06-14
hello, i have an nvidia geforce 9400 gt and use a philips ftv, tried to enable the drivers but when they are enabled i loose some from the right and some from the left of the screen, also the effects can not be enabled. i also tried to use the envy drivers but same things happen.Then tried to change the screens resolution and guess what? same thing. Also downloaded the drivers from nvidia site but when i am going to the tt1, killing all the gdm and trying to install the drivers from there, it says something for my kernel and tries to connect to the internet to download something for the kernel at the [www.nvidia.com](www.nvidia.com) but it cannot connect to it (maybe because i use a wifi, i don't know) and says that it will create a new kernel or something. the kernel that makes is not working at all and after the restart drops me to a tt1 and it says that the x is not working properly or something. 

PLEASE HELP AND IF YOU HELP I WILL NOT SAY THE WORD "SOMETHING" FOR THE REST OF MY LIFE

---

### Post by Celauran on 2009-06-14
Can you post specific errors, rather than "It doesn't work or something"?

If X isn't starting at all, try commenting out the Driver line in Section "Device"

---

### Post by antez on 2009-06-14
i will write it tomorrow, also can you say me how to connect to the inernet from the tt1?

 thnx in advance

---

### Post by camper365 on 2009-06-14
Drivers in Linux are part of the kernel, so if you need to update a driver, you are updating the kernel.

I don't mean to sound harsh, but why did you enable the proprietary driver in the first place? If you were trying to get the 3d effects that makes sense but if there was already a driver available, why not just use that one?

---

### Post by klemperal on 2009-06-14
Also, are you using a seperate x screen, or twinview?  Is xinerama enabled?  Have you tried changing the resolution to you tv from within nvidia-settings to see if it makes a difference?

---

