---
title: "gnome-do launching terminator without arguments"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by zorblek on 2009-06-20
I recently switched from using the keyboard launcher Launchy to Gnome-Do, and I'm having a problem that I never had with Launchy. I use Terminator for my terminal, and I always launch it with the options -mb, which make it launch maximized and without window borders. I've modified the command wherever it appears in Gnome preferences to use these options, eg. in the menu entries, preferred applications, etc. When I used Launchy, Terminator started using those options. But when I start it using Gnome-Do, it just starts in a normal window. Where does Gnome-Do get its list of applications from, and can the entries be modified?

Thanks in advance for any info!

---

### Post by synapsys on 2009-06-20
I'm not familiar with gnome-do, but with most launcher applications you can right click (or some other way) go to the properties of the shortcut and change the command to include the -mb option.

---

### Post by zorblek on 2009-06-20
Unfortunately that doesn't work in Gnome-Do. But thanks for the suggestion!

---

### Post by zorblek on 2009-06-21
I solved this problem by using locate terminator.desktop, and then editing all the files that came up in a text editor so their "Exec" lines read "terminator -mb". The ones in my home directory were already correct, the rest I had to use sudo to access. There were .desktop files in several locations. I'm still not sure where Gnome-do looks to make its list.

---

