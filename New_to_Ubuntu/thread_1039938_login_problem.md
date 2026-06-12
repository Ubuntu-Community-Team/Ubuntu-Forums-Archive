---
title: "login problem?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Chaos_Spear on 2009-01-15
Hi,

So while attempting to fix my graphics driver(unrelated) I had to go into runlevel 3 while not loading kdm.  I accomplished this, but when it asks for login, things get WEIRD.

I type in the correct username and password, and it DOESN'T WORK.  Not only that, but it starts displaying the first letter of the username before the password prompt, and after hit enter after I type in my password, it displays the first letter of the password.

It's not something I messed up in runlevel 3, I've had it happen before but I fudged my way through it somehow.

Please help, I am getting desperate enough that I'm close to completely reinstalling Kubuntu.

---

### Post by Vantrax on 2009-01-15
Try logging in on tty1, that will show if its your login or your KDE.

---

### Post by stefangr1 on 2009-01-15
Ubuntu does not have runlevel 3. Also: going to tty1 when X is running might not work, since I assume (since you were trying runlevel 3) that what you want to do requires X to be down.

What I always do is when I am at the gui login, go to the options menu, and choose konsole login.

---

### Post by Chaos_Spear on 2009-01-15
> **Vantrax said:**
> Try logging in on tty1, that will show if its your login or your KDE.

tty1 is where it's happening.

> **stefangr1 said:**
> Ubuntu does not have runlevel 3. Also: going to tty1 when X is running might not work, since I assume (since you were trying runlevel 3) that what you want to do requires X to be down.

What I always do is when I am at the gui login, go to the options menu, and choose konsole login. 

I configured Ubuntu to have runlevel 3, it's basically runlevel 2 with kdm disabled, since I CAN'T run the GUI, my display driver is borked completely, and the installation doesn't work from runlevel 1.

---

### Post by Chaos_Spear on 2009-01-15
If there is another way to get into runlevel 2 without going into the GUI, that would help me as well.

---

### Post by stefangr1 on 2009-01-15
If you have openssh installed and have another computer available, you can ssh into it and fix it from there.

---

### Post by Chaos_Spear on 2009-01-15
I think I might just do a clean re-install.  My machine's less than a month old and I should be able to safely copy the files to a second drive.

---

