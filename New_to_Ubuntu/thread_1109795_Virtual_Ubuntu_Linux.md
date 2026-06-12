---
title: "Virtual Ubuntu Linux"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Kyrros on 2009-03-29
Hey guys, I've used Linux before, but it's been ages. Anyway, what I wanted to know is if it's possible to run a Virtual copy of Ubuntu Linux whilst running windows at the same time?
I'd love if it didn't lag a large amount, but I don't plan on using it for much other than coding. Coding in Windows just annoys me to no end, and it feels very, very cluttered.

The reason I wish to run them at the same time is so I have access to Photoshop, as I don't mix well with Gimp. Trying to learn how to use one is confusing enough, I'd rather not try to learn using two. ;)

I've got 2G of 1066MHz RAM, 2.6 dual-core CPU, and an Nvidia 8800GT, if that helps with thinking about lag.

Thanks for any help! :KS

---

### Post by eragon100 on 2009-03-29
Do you have windows XP or Vista installed? If you have xp just make a virtual machine for ubuntu with virtualbox, and allocate it 1 GB of memory. It will run fine, and windows XP will too.
If you have vista, you might not have enough free RAM left to run it comfortably.

---

### Post by sirjoebob on 2009-03-29
you could use [virtualbox]("http://www.virtualbox.org/") to run a virtual copy. would work fine on your machine. also, you could use a program called [andlinux]("http://www.andlinux.org/") that lets you run linux within windows very nicely. 


you could allocate as little as 512 MB RAM to Ubuntu and you should still be fine. 

Hope that helps.

---

### Post by Kyrros on 2009-03-29
Thanks for the help! I'm currently running on WinXP SP3, so I'll give the virtualbox a try.

Also for when I didn't need the use of Photoshop, I went ahead and partioned 15GB of space for it. I used the Wubi installer, and then I restarted, tried to boot into Ubuntu, and it installed/verified more stuff.

I then proceeded to re-boot after it was done, and now when I select Ubuntu to start, it goes to a screen that says something similar to, "Press Esc to access the menu...", with a countdown number so I just let it go through.

Then it gives me a loading bar, and finally a command prompt that says 'Activating fileswap swap' and just stays there.
Did I do something wrong? Back when I used Ubuntu it had a Graphical Interface. :confused:

---

### Post by sirjoebob on 2009-03-29
Sounds like something went wrong. I believe with the Wubi installer you don't need to partition any space, it uses an expanding file in windows. May want to try to install normally on a partition or retry the wubi install. Never used Wubi myself since I don't want my Linux to be dependent on my Windows install. Also, I only run Ubuntu these days. Good luck.

---

### Post by Kyrros on 2009-03-29
I'll try installing from the CD. I'd never used the Wubi installer either, so I have no idea what to do with it, really lol.

---

### Post by hyper_ch on 2009-03-29
virtualbox or vmware are the best tools... I tend to think virtualbox is lighter but vmware offers more things... :) vmware server is free (although I prefer v.1.0.x over v.2)

---

