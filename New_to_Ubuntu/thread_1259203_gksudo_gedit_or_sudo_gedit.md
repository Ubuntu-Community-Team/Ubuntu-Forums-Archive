---
title: "gksudo gedit or sudo gedit?"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by billdotson on 2009-09-06
I heard it is a bad idea to run gksudo nautilus because of somethingwith home folder permissions, is sudo gedit ok?

---

### Post by Malta paul on 2009-09-06
If you are using 'Nautilus' Gksudo is best, but I use Sudo in the terminal for text items like 'sudo apt-get autoclean'

Perhaps you would like to check:[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
For a more detail explanation.

:D

---

### Post by eyeyoubin on 2009-09-06
both gksudo and sudo give you root permissions anyway. when using gedit, the only difference is gksudo prompts GUI for password whereas sudo asks for password through terminal.
i rarely use gksudo especially when using gedit. as long as you remember to save when you are done, they shouldn't matter too much.
if sudo doesn't seem to work. use gksudo.

---

### Post by scragar on 2009-09-06
It really depends on what you are doing, but remember that anything done in sudo is done as root, so editing a new file with `sudo gedit` will leave the file belonging to root, and unable to access as a normal user, nautilus has similar problems.

In general it can be much easier to use `gksu nautilus` or `gksu gedit`, but you should always be cautious to check perms and owners after modifing content to ensure that you will be OK as a normal user afterwards.

---

### Post by TeoBigusGeekus on 2009-09-06
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by jnorthr on 2009-09-06
Permissions are only in place to allow/prevent access to files and folders in the filesystem. 'sudo' makes you like god so you have access to everything. Many times this is unnecessary. In normal day-to-day activities, sudo is overkill. Run without it first, to see if you can edit a file. gedit is a fine text editor and should allow you to work as a user on user kinda files. I only tend to sudo when working on system level changes to wireless settings, user profiles, printer setup, etc, not for day-to-day programming.

---

### Post by mcduck on 2009-09-06
> **eyeyoubin said:**
> both gksudo and sudo give you root permissions anyway. when using gedit, the only difference is gksudo prompts GUI for password whereas sudo asks for password through terminal.
i rarely use gksudo especially when using gedit. as long as you remember to save when you are done, they shouldn't matter too much.
if sudo doesn't seem to work. use gksudo.

It does mater which one you use.

"sudo" doesn't load root user's environment variables for graphical applications. This means that when you launch a graphical application with sudo you are running it with root's permissions but using your normal user's settings and configuration files.

Depending on the program you run this can result in your normal user's configuration files becoming owned by root, which will prevent the normal user from changing program settings any more. Or, in worst cases, from logging in at all.

Sure, Gedit is one of the programs that runs fine with "sudo". But not all do, and finding out which ones work and which ones break is definitely harder thing to do than just learning the habit of *always* using gksudo with graphical applications.

---

### Post by eyeyoubin on 2009-09-06
> **mcduck said:**
> It does mater which one you use.

"sudo" doesn't load root user's environment variables for graphical applications. This means that when you launch a graphical application with sudo you are running it with root's permissions but using your normal user's settings and configuration files.

Depending on the program you run this can result in your normal user's configuration files becoming owned by root, which will prevent the normal user from changing program settings any more. Or, in worst cases, from logging in at all.

Sure, Gedit is one of the programs that runs fine with "sudo". But not all do, and finding out which ones work and which ones break is definitely harder thing to do than just learning the habit of *always* using gksudo with graphical applications.

I get your point but I have to disagree in relation to gedit... and gedit was the main question here.

---

### Post by mcduck on 2009-09-06
> **eyeyoubin said:**
> I get your point but I have to disagree in relation to gedit... and gedit was the main question here.

The point was that it's pretty insane to even try to figure out which programs are safe to use with "sudo" and which are not. So it's better to just use "gksudo" for all graphical apps, and you can be sure you'll never break anything just because you've grown into bad habbit of using sudo for GUI apps. If you prefer "sudo" just to save yourself from typing two extra letters, "gksu" does the same thing as "gksudo" and  isn't even any longer to type than "sudo".

---

