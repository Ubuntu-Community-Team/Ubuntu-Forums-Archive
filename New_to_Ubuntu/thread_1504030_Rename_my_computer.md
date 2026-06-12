---
title: "Rename my computer"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by tmette on 2010-06-07
Ok, It's been about 3 weeks or so since I've had my Ubuntu machine.  I'm thinking about renaming it though.  I stupidly used my first name since I was so excited to get it up and running.  I have always used my first name for all my computers.

Now I'm thinking about picking different names for each computer I own.  Such as months of the year, star constellations, etc.  Is there a way to do this in Ubuntu and not have it screw up the current admin account?  This is the only account on the computer.

---

### Post by rampageoberon on 2010-06-07
If you want to change hostname (computer name) use the "hostname" command.

You can also change username, but it can lead to some difficulties. "usermod" would do this if you are determined to change.

---

### Post by Mariane on 2010-06-07
The most difficult part is finding a good name for it  :) . Mine is called "Trouble", and yours? 

Mariane

---

### Post by bumanie on 2010-06-07
[This]("http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name/") shows you step-by-step - very easy to do.

---

### Post by tmette on 2010-06-07
> **bumanie said:**
> [This]("http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name/") shows you step-by-step - very easy to do.

Thanks!  I will do this once I get home from work.  Yes, choosing a theme will be difficult.  I think I've narrowed it down to either batman villians, or just all DC comic characters.

---

### Post by mobilediesel on 2010-06-07
> **tmette said:**
> Thanks!  I will do this once I get home from work.  Yes, choosing a theme will be difficult.  I think I've narrowed it down to either batman villians, or just all DC comic characters.

You can also pick names at random. I use these sites:
[http://computernamer.com/](http://computernamer.com/)
[http://www.randomhostname.com/](http://www.randomhostname.com/)

---

### Post by Iowan on 2010-06-07
Unless it's changed with recent releases, you should change both */etc/hostname* and */etc/hosts* (the 127.0.1.1 line) - otherwise **sudo** will complain.

---

### Post by Iowan on 2010-06-07
Unless it's changed with recent releases, you should change both */etc/hostname* and */etc/hosts* (the 127.0.1.1 line) - otherwise **sudo** will complain.
[Here]("http://ubuntuforums.org/showthread.php?t=1391523") is a similar thread about 9.10.

---

### Post by Phil Hansen on 2010-06-08
> **Mariane said:**
> Mine is called "Trouble", and yours? Mariane
"Grumpy" works for me :p

---

