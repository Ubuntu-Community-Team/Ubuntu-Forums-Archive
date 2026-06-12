---
title: "Updates require computer to reboot. Why?"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by mastablasta on 2010-03-09
I am asking here because i read there shouldn't be rebooting after every update.
 
So far i got a promt to update after isntalation. Ok done that 256 MB too a while to download. After they were installed i was prompted to reboot so that updates might work (just like in WinXP). A week later again updates available i click update - about 40MB took a while again, occupied my computer when it was done i was prompted to reboot. Every time after the update there is a new Kernel in Grub and they keep adding more and more of them. Is this normal? wouolnd't the list grow a bit long after a while?
 
I am a newbie and i just follow the suggestions prompted by Ubuntu. 
 
I was told that it shouldn't be prompted to reboot after every update. My bro has 25 days uptime despite updates (running 9.04 at work) did i do somethng wrong at the install? 
 
also are these updates going to be like this every week? because they are worse than windows i mean much bigger. windows has it every month and they take about 5-8 MB while here it's 40 MB. :o
 
Also Mint does a better job at saying which updates are necessary, while here i don't know do i need to install all of them or just some.

---

### Post by MichealH on 2010-03-09
Sometimes the computer will download Linux-headers and Core Components and That will require a reboot such apps like firefox,empathy will NOT need it to restart.

---

### Post by Dayofswords on 2010-03-09
if it replaces/changes the core components, you need to restart it 

if its a programs you use, no restart

---

### Post by perham on 2010-03-09
on a side note, to clear old kernels download and install ubuntu tweak from [here]("http://ubuntu-tweak.com/") and in aplications section choose package cleaner, then click unlock and enter your password and you find your old kernels in clean kernels section. uninstall them if you like.
you can also delete the menu entries by editing /boot/grub/menu.lst or /boot/grub/grub.cfg if you have the new grub2 package.

---

### Post by J V on 2010-03-09
But then new kernels aren't *absolutley neccesary*, you don't have to restart right away, just do it later on...

Of course theres a linux module thats supposed to allow you to update the kernel without rebooting, which is cool...

---

### Post by Bradtek on 2010-03-09
> **mastablasta said:**
>  because they are worse than windows i mean much bigger. windows has it every month and they take about 5-8 MB while here it's 40 MB. :o 

Windows only updates windows

Ubuntu updates potentially every piece of software on your installation.

Will it be like that every week ? that will depend on what software has been updated / tested / added to the repository.

BTW you do not have to update anything, although security updates are advised.

---

### Post by 3rdalbum on 2010-03-09
Whenever the kernel is updated, or part of the system that can't be shut down without shutting down all programs, you need to reboot to get the updates to take effect.

If you don't like rebooting, you can check out Ksplice.

The kernel usually gets updated for security reasons. If the list is starting to grow long, you can remove the kernels you don't use (good idea to keep at least one backup though). Just remove the old kernels in Synaptic.

---

### Post by howefield on 2010-03-09
> **perham said:**
> you can also delete the menu entries by editing [*snip*] /boot/grub/grub.cfg

... which isn't meant to be edited.

---

### Post by steve-shinn on 2010-03-09
> **howefield said:**
> ... which isn't meant to be edited.

Agreed 100% : The main menu file, /boot/grub/grub.cfg, is not meant to be edited, even by 'root'. 

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

