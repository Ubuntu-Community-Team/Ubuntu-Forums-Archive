---
title: "[SOLVED] File permissions"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by bitrocker on 2008-12-12
Hi,

I am going to describe what I do, including the tools I use. But I don`t think that the problem is with the tools, but about file permissions.

I am using CodeSurfer (a tool that "listens" during compilation and produces some analysis output) to analyze SPEC.
To run SPEC I need a terminal with root access, since SPEC sets some temporary environment variables, and those (I found out via try and error) can only be set with root access. To do that, I open a terminal, say
```
sudo dolphin
```
and then open another terminal out of dolphin, within the directory I want my project to be. This terminal than has a '#' at the end. Guess that that indicates, that I am root now?
After that, I invoke CodeSurfer and tell it to run the SPEC compilation. SPEC compiles well (maybe someone likes to know that this wont`t work with MinGW under Windows), but when it comes to build the CodeSurfer project, I get an error "Couldn`t open /media/deviceB/projects/proj_xy/store"

I tried to change permissions for the "projects" folder with dolphin ( I did both invoking dolphin as user and as root (sudo dolphin) ). There were no erorr message, but when I came back to check permissions, the were set to default again!?!
I also tried to change ownership of the working folder from "user: userA - group: root" to "root / root", this time I got the message "...insufficient file access"

To sum up: What can I do to give some program permissions to write - whatever it wants - to some directory?

---

### Post by spiderbatdad on 2008-12-12
Is the "project folder" a removable device that is mounted/unmounted by a program you are running?
I believe dolphin is a graphical file browser? You should launch graphical programs as root with: gksudo <program>

I'm thinking the permissions of your device are specified in /etc/fstab

---

### Post by Sunny-Cab on 2008-12-12
To sum up: What can I do to give some program permissions to write - whatever it wants - to some directory?

gksudo "Programm u want"

After that, I invoke CodeSurfer and tell it to run the SPEC compilation

Perhaps this is the Point

gksudo CodeSurfer

Hope this Helps

---

### Post by bitrocker on 2008-12-13
mea culpa,

I am sorry for boring you with a problem that was my own fault. I simply forgot to start CodeSurfers license-manager (I am too used to Windows, where it starts on its own). What let to those useless error messages ;(
A look in the log file - that tells things very different from the shell output - helped.

Thank for your suggestions. Little hint from my side:

If you start a terminal and say

```
sudo dolphin
```

then start a new terminal out of dolphin, with right-click -> start terminal here,  you will be root. That should (I think) solve problems with permissions (progam wants to write output - has no access).

---

