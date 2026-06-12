---
title: "Post-Boot Problems - Please Help"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by Mik3yb on 2011-04-02
Hi everyone.
I have two computers, a Toshiba Satellite a135 and a Dell Inspiron 1300. 
I booted Ubuntu 10.10 on both of them with a USB. I formatted both of the hard drives.

Problem is, on my Toshiba, the icons/menu bar at the top won't show up. They lead to the proper apps, but there is no image. It booted perfectly on the Dell, icons and all.

How do I fix the icons not showing up? Again, it's a Toshiba Satellite a135.

Thanks.

---

### Post by Mik3yb on 2011-04-02
I'm also finding that while my Toshiba can pick up WiFi on Ubuntu, my Dell cannot. Any ideas as to why?

---

### Post by Mik3yb on 2011-04-03
Bump for help!

---

### Post by wolfen69 on 2011-04-03
> **Mik3yb said:**
> I'm also finding that while my Toshiba can pick up WiFi on Ubuntu, my Dell cannot. Any ideas as to why?

Did you check to see if any wireless drivers are available in system>administration>additional drivers? You need a wired connection for this.

---

### Post by rosencrantz on 2011-04-03
If I understand your first post right, on the Toshiba the Gnome menu bar displays no icons but you can access the menus and programs - or is it completely invisible? And you are still booting from an USB stick, but have already formatted the hard disk.
OTOH, I can think of 3 things: a) check your screen settings, maybe the resolution is wrong and the bar has been pushed off-screen
b) If you already formatted the hard disk, it can't hurt to install Ubuntu anyway. If the problem persists, try a system upgrade with
sudo apt-get update
sudo apt-get upgrade

c) Corrupted icon package? After installing (this might also work on an USB boot), look in the output of 
aptitude search icon
for anything that looks like a gnome icon set and is preceded with an 'i' (for installed) and force a reinstall with
sudo apt-get --reinstall install <packagename>

OK, that's all I can think of...
Good luck
rosencrantz

---

