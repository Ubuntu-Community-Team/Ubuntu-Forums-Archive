---
title: "Dropbox Installation Freezes During Download"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2011-02-07
I am running Ubuntu 10.10 and attempting to install dropbox. The problem is, everytime I run the installation, it freezes mid download and won't finish. Is there another way to install it?

---

### Post by ikt on 2011-02-07
> **Captainflowers91 said:**
> I am running Ubuntu 10.10 and attempting to install dropbox. The problem is, everytime I run the installation, it freezes mid download and won't finish. Is there another way to install it?

Can you see what errors are coming up?

I installed dropbox just then no issues :s

---

### Post by bgf3rw on 2011-04-21
A bit late to the party, I know, but in case anyone is searching....

I had a similar problem after migrating old data to a new 10.10 install. I installed the dropbox.deb OK and launched dropbox from the main menu for the first time. The installer downloaded the dropbox software and started to install but just hung after a while and then just vanished.  

I found that renaming (or deleting) ~/.dropbox folder didn't help. BUT deleting the ~./dropbox-dist folder allowed my install to complete.

---

### Post by dwhite on 2011-04-21
also running 10.10 no problems installing, use the following in terminal.

sudo apt-get update
sudo apt-get upgrade nautilus-dropbox

i've been very happy with dropbox, sharing files between mac/pc/linux.

---

