---
title: "is it posible to move a ubuntu installation from old hard drive to new hard drive?"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by legolas_w on 2009-04-29
Hi
Thank you for reading my post.
I am wondering whether it is possible to move a ubuntu installation from one hard disk to another hard disk or not?

I want to remove my old hard disk and move the installation to the new hard disk for further safety and security but I do not know whether it is feasible or not.

thanks.

---

### Post by didiercool on 2009-04-29
I would just install ubuntu on the hd you're moving to, and then mount the old hd (from Places) and move all your files over.  That's the easiest way I know to do it!

---

### Post by hesjnet on 2009-04-29
Everything is possible. THIS is just to much work for it even to be worth it. 

While you probably could copy all the files in the harddrive, you would still have troubles with the master boot records (MBR) not finding your Ubuntu OS. Ever seen the "No operating system installed" error message?

My tip:

[LIST][*]Backup your home folder[*]Write down the programs you are using[*]do a fresh install on the new harddrive[*]transfer files from home folder backup[*]install programs

Edit: Like didiercool said: you could mount(connect) the old drive to your machine, if you have a availiable slot in your machine or have a external harddrive capsule for your laptop. That would save you some time.



[/LIST]

---

### Post by anjilslaire on 2009-04-29
Why don't you just clone the drive with [Clonezilla]("http://clonezilla.org/") and then put the image on the new drive?

---

