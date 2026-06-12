---
title: "Why did 32bit XP run slow on 64bit Virtualbox"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by afz12 on 2010-03-28
Hi 

I tried a 64 bit Ubuntu 9.10 on my notebook and it went well. Then I installed a 64 bit Virtualbox version on my notebook and it installed OK. Then I installed XP as a virtual machine and this went OK. However every application ran extremely slow - sometimes 1~2 seconds delay per keystroke. 

I returned the OS to a 32 bit Ubuntu 9.10 and then 32 bit Virtualbox. This combination worked well before. Running XP as a virtual machine now runs extremely well. 

I have 4 GB ram on an acer5920 and I thought 64bit Ubuntu would access all this and it did report all the RAM. With 32bit Ubuntu it only reports 3GB as expected. However the machine runs well with 32bits Ubuntu 32 bits Virtualbox.

I am perplexed and wonder if anyone can explain why a 64 bit Virtualbox on a 64 bit OS interacts very poorly with a 32 bit virtual OS? I had thought the 64bit OS / Virtualbox combination would have made better use of the notebook's resources and therefore run better- apparently not! Any comments are welcome.

---

### Post by OriginalName on 2010-04-07
I guess the VM has addition overhead translating between the different processor architectures. Did you test this with 64-bit Windows XP?

---

### Post by seenthelite on 2010-04-07
I have 64 bit 10.04 and 64 bit virtual box with 32 bit XP and it is working fine. I had same with 9.10 also worked OK. I get virtual box from here. 

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by undecim on 2010-04-07
Make sure that you have VT-x/AMD-v enabled.

---

### Post by uRock on 2010-04-07
XP runs very slow in the VBox on my wife's 64bit ubuntu also. How much RAM did you allocate to the VBox. Blaming ubuntu for this is completely wrong. I have had the same set up on my desktop and it was blazing fast or as fast as XP can get, anyway.

Unless you have the PAE kernel installed on a 32 bit system, you can only use3.x GB of RAM.

---

### Post by Calash on 2010-04-07
> **undecim said:**
> Make sure that you have VT-x/AMD-v enabled.

Look for this first.  My work box is x64 and runs two x32 Windows XP VM's with no problem.

---

