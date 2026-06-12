---
title: "How do I set a program to autostart when Ubuntu loads?"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by Mashuteichou on 2009-07-13
I read on place that it was in sessions under preferences, but I don't have sessions.  

I found the startup manager under administration, but I can't figure that out.  

Basically, I would like Firestarter to load, and Pidgin.  

Simply put, I have no idea what to do, where to go, how to do it.  I'm still used to the Window's msconfig for startup programs.  

How do I start these two programs in Ubuntu 9.04?

---

### Post by AndThenWhat on 2009-07-13
Its name has been changed to "Startup Applications."

(System -> Preferences -> Startup Applications)

---

### Post by starcraft.man on 2009-07-13
System > Preferences > Startup Applications

Add > Fill form:
Name : Name you want it called.
Command: *pidgin* for one entry, then *firestarter* for a second one. Only one command per entry please.
Comment: Descriptive comment, appears under name.

Also, you might be interested in options tab of the menu. There is a function that will start up the applications you had open when you shut down. An alternative at least.

---

### Post by Mashuteichou on 2009-07-13
I have both pidgin and firestarter already in the startup part, but they never start.  And the option to load stuff that was already running on shutdown is already active.  But, it never works.  >_<  I always have to manually load both.

---

### Post by raintree710 on 2009-07-13
Yes I have the same problem.  I have set firestarter to start but whenever I log into Ubuntu it gives me the prompt **you must have root user privileges to use firestarter**.  I have asked this question on linuxforums.org but I haven't fixed it yet.  Please help!!!!!!

---

### Post by Mashuteichou on 2009-07-13
Same with me.  I don't have the privllege to start it.  (Pidgin works now for some reason...)

---

### Post by Jimleko211 on 2009-07-13
> **raintree710 said:**
> Yes I have the same problem.  I have set firestarter to start but whenever I log into Ubuntu it gives me the prompt **you must have root user privileges to use firestarter**.  I have asked this question on linuxforums.org but I haven't fixed it yet.  Please help!!!!!!
maybe in the command, you should put in "sudo firestarter"?

---

### Post by Defrector on 2009-07-13
For the command, use "gksudo firestarter" - make sure you have gksudo installed in synaptic. gksudo will raise a password prompt in gnome for you to enter it in.

I do not know how to make it sudo automatically.

---

### Post by Jimleko211 on 2009-07-13
Yeah gksudo would be better, I guess, since that's more for graphical things.

---

### Post by Omen_20 on 2009-08-04
Just something for convenience. Instead of entering the text manually, just open up Startup Applications. Then click on the Gnome menu, navigate to the program you want and then drag it into the Startup App list. It will automatically pop it in there with the icon and all fields entered.

---

