---
title: "Get rid of Kubuntu login menu"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by kleinempfaenger on 2010-06-05
Hi,
I use lucid.
Some weeks ago I wanted to try out Kubuntu. It didn't really work, but when I saw all those colors I decided to go back to the gnome desktop and changed it back.
But at startup still appears the Kubuntu Login and I want to get rid of it.
I've already tried some things in the administration menu, but couldn't solve it.
Thanks.

---

### Post by Yayestechlab on 2010-06-05
Just run this command in the terminal  (Applications -> Accessories ->Terminal )
```
sudo dpkg-reconfigure kdm && sudo apt-get remove kdm
```When the reconfigure command asks you whether you want gdm or kdm chose gdm.

---

### Post by kleinempfaenger on 2010-06-05
Thank you for the answer, 
Yayestechlab. But it didn't solve my problem.
After typing

sudo dpkg-reconfigure kdm && sudo apt-get remove kdm

I got the message that kdm isn't installed. So I thought it might be a problem of gdm. Reinstalled gdm, but still I see the Kubuntu screen at login. Than I typed

sudo dpkg-reconfigure gdm && sudo apt-get remove gdm

After that I wasn't able to boot, I think because gdm was removed. So I booted in recovery mode and reinstalled gdm. But still I have that superfluous Kubuntu screen at the beginning.
Is there a way to edit gdm?

---

### Post by kleinempfaenger on 2010-06-05
I have solved the problem and I think I was wrong. Because what I saw at the beginning may be wasn't a Kubuntu screen, but only appears since I tried out Kubuntu. 
I made some modifications in the System - Administration - Users and groups menu, and now I go directly to the password and the gnome desktop. The annoying screen doesn't appear any more.

---

### Post by kleinempfaenger on 2010-06-05
This is solved, but I can't find the link. If anybody could mark it like this?!

---

