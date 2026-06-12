---
title: "gnome desktop shortcut problem"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by henrik winther jensen on 2010-05-11
Hi,

I am trying to create a shortcut on my desktop to run idea. The shortcut is created allright,
but nothing happens when I click on it. I can run program from the command line.
I am new to gnome, but under KDE I would have configured the program to run in a command line
box. That way I would be able to see what fails. I do not seem to be able to find a similar facility
under gnome. Any suggestions?

TIA
Henrik

---

### Post by Cabs21 on 2010-05-11
> **henrik winther jensen said:**
> Hi,

I am trying to create a shortcut on my desktop to run idea. The shortcut is created allright,
but nothing happens when I click on it. I can run program from the command line.
I am new to gnome, but under KDE I would have configured the program to run in a command line
box. That way I would be able to see what fails. I do not seem to be able to find a similar facility
under gnome. Any suggestions?

TIA
Henrik


What is Idea?  Is it windows based or linux based?  Is it a program or a script?

---

### Post by henrik winther jensen on 2010-05-12
Oops, sorry to be so long, I thought replies would be sent to my mailbox.

First of all, I am using a brand new 10.04 with a gnome desktop. I try to make a desktop icon
to start a program. What I do is to right-click on the desktop, select shortcut and fill in the form.
I have tried to do this to start the nano editor, and my Intellij IDE, both Linux of course.
I have not specified anything else than program path and icon name.

In both cases the icon changes color when I click on it, but nothing else happens.

Probably some error on my part, but I cannot seem to find any tools to help me figure out what I am
doing wrong, do you know of anything I could use?

Kind regards
Henrik

---

### Post by henrik winther jensen on 2010-05-12
Just had an idea: I tried dragging a program from the menu to the desktop. This new icon exhibits
the behavior as my "homemade" short-cuts!

This is insane.

Is it because it is not possible to run programs from the desktop in gnome? Impossible!
Maybe my installation is somehow flawed? Maybe I should try to install on a different machine, I have
used quite a bit of time to set up the machine in question :-(


Any idea is appreciated!
Henrik

---

### Post by ankspo71 on 2010-05-12
Hi,
Whenever you want to create a shortcut to a terminal application in gnome-terminal, you need to use "gnome-terminal -e" first so that it knows to launch gnome-terminal first then execute nano within it.

So the command would be:
```
gnome-terminal -e nano
```

Using other terminals may be different.

I'm not sure about the Intellij IDE launcher though.

---

### Post by ankspo71 on 2010-05-12
Hi  again,
I noticed you said you switched from KDE to Gnome. Gnome in Ubuntu uses double click by default, so some Kubuntu users might be caught off guard by that.

If double clicking is not your preference you can open your home folder (from within Gnome desktop's Places menu so that Nautilus file manager will open), click on Edit > Preferences > Behaviour (tab), then choose single click.

---

### Post by henrik winther jensen on 2010-05-12
That made my day!

Now I am getting somewhere. You were quite right, I did not know that you have to double-click 
to start a program. The gnome-terminal -e trick took care of the of the nano editor. I tried to wrap
my IDE in a scrip that had sleep 10 at the end, combined with the gnome-terminal -e thing. It turns
out that the problem is with my environment when I run programs from the desktop.

That is fixable.

Thanks a lot
Henrik

---

