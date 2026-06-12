---
title: "VNC Password Authentication Failed"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by phoenix_1983 on 2007-06-11
Hi There hope someone can help.

I managed to get VNC over SSH working perfectly between my XP box and a Fiesty Ubuntu system.  Then, for no reason i'm getting VNC password authentication failed message when i try to login.

I've manually connected to the box and checked the passwords under remote desktop and reset with

sudo vncpasswd ~/.vnc/passwd

The password is 7 characters long so i'm inside the limit.

I'm using the X11VNC package.

Does anyone have any thoughts on what may be going on?

Thanks in advance.

---

### Post by krunge on 2007-06-11
Are you sure you are running x11vnc?  I am not sure what you mean by "under remote desktop" x11vnc has no gui settings that I know of...   

What command line was used to start x11vnc? What is used for the -rfbauth option? 

Also when you type "sudo vncpasswd ~/.vnc/asswd" the ~ will be expanded to your $HOME, not roots.  So you may be pointing to the incorrect vnc passwd file.

---

