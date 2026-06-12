---
title: "Ubuntu 10.04 crashes. (Programs,applications stop automatically)"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by sharmaneha on 2011-06-24
I have the following config:

AMD Phenom 2 processor
Asus motherboard
500 GB Hard disk (Seagate)
2 * 2GB RAM DDR2

When I first installed ubuntu 10.04 (32 bit)  everythng worked fine, but i messed up d screen resolution and couldn't make it right. So I decided to re-install (Another reason to do this was that I had Windows XP - and I wanted single OS on my PC)
 
When I installed this time, my pc kept on crashing. No application runs more than 5-10 mins. After few minutes the program stops automatically and after that I am not able to access any program/application. 
I have to restart everytime in order to finish my work. Any download from Ubuntu Software Centre results in an error/failed download.

Also I am not able to get rid of the problem by re-installing. ( I have tried that with multiple CDs and different OS including ubuntu 11.04, Kubuntu, Windows XP--All these installations fail at preliminary levels ending in gibberish error on black screen) 

I am fairly new to Ubuntu and any suggestion to my problem will b welcome
Right now using Ubuntu 10.04 Live CD

---

### Post by bruno9779 on 2011-06-24
What you describe sounds like an hardware failure.

Can you run a live CD? If so, do a memtest to see if your ram is corrupted.

Also, why are you installing a 32 bit distro on a 64 bit processor? It takes away the advantage of having 64 bit (someone may disagree, but they are a minority ;))

PS: the screen resolution issue was probably caused by GPU drivers. Post the maker and model of you GPU, I can probably help with that

---

### Post by sharmaneha on 2011-06-24
Thank you so much for replying. :)
I can run a live CD but only 1 i.e Ubuntu 10.04 (32 bit)
I cannot run the following live cds :
Kubuntu (64 bit)
ubuntu 10.10 (64 bit) and
Ubuntu 11.04 (64 bit)

I tried installing 64 bit Os to get maximum output from my pc but the installation always fails
I will sound really really silly when i ask this but how do you run a memtest?

---

### Post by rg_stephens on 2011-06-24
Memtest was included on the Ubuntu Live CD until about version 9. I don´t know why they stopped including it.

You can download an ISO from Memtest.org and make a bootable CD or USB drive. Let it run for at least an hour or so. A small defect in a ram stick (or cpu, or ...,) can cause all sorts of weird problems.

---

### Post by sharmaneha on 2011-06-24
Allright...thanks. I will try that and get back to you

Have a good day :)

---

### Post by bruno9779 on 2011-06-25
Have you tried 10.04 64 bit? 
Maybe it is an hardware incompatibility of sorts with the version, instead than with the architecture

---

### Post by sharmaneha on 2011-06-27
Hello everyone!

Ok so I ran memtest86 for both my ram... turns out one of them was in fact corrupted. 
After removing it my pc seems to work fine.
All my hardware is still under warranty so I can easily get a replacement.
[B][COLOR=Black]Thank you all soo much for helping me out!
Love you all and have a great day! :)
[/COLOR][/B]

---

