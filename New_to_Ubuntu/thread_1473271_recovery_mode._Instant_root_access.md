---
title: "recovery mode. Instant root access?"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by Kankomi on 2010-05-05
Hi,
i finally decided to register and ask this question which bugs me for quite a while. I installed ubuntu 10.04 on my laptop which works really good (in fact everything worked right away) but if i start in recovery mode and choose root-shell, i get of course the root shell but i dont have to log in? I have instant root access to my computer without typing in my root password? Did i do something wrong?


greets kankomi

---

### Post by mikewhatever on 2010-05-05
You haven't done anything wrong, that's the way it has always been in Ubuntu. The rational  here is simple, physical access = root access with or without a password, since an intruder could just use a live cd.

---

### Post by Kankomi on 2010-05-06
Ah ok, thanks. Isn't there a way to prevent someone reading your data, I mean I'm not super important nor do i have confidential documents but since I'm running Linux and being a computer science student I would like to know how to keep my data private.

---

### Post by mörgæs on 2010-05-06
You can encrypt your /home directory.

---

### Post by mcduck on 2010-05-06
> **Kankomi said:**
> Ah ok, thanks. Isn't there a way to prevent someone reading your data, I mean I'm not super important nor do i have confidential documents but since I'm running Linux and being a computer science student I would like to know how to keep my data private.
No operating system feature will have any effect on security while the OS is not running, so the only (and I really mean the *only*) way to create local security if you can't make sure the computer doesn't get into wrong hands is to encrypt your data. And this of course applies to all operating systems, not just Ubuntu.

Ubuntu's installer offers you an option to encrypt your home directory, but if you just want to secure some of your files then Cryptkeeper is a nice & simple tool for creating and managing encrypted directories in Gnome.

Other than that it's juts a question of restricting who gets physical access to your machine. Like it's already been mentioned, unrestricted physical access equals having a fill access to everything on the computer, all operating system-level security features can be bypassed by booting into any live-environment, while any measures to booting into live-environments are easy to work around (changing BIOS boot order to prevent booting from CD/USB, for example, is pointless as resetting the BIOS password is a trivial and quick thing to do on almost any modern PC/Laptop)

---

### Post by Kankomi on 2010-05-07
Thanks for the answers. I guss  I'll look into that Cryptkeeper.

P.S.: That's why I love the Open Source Community, if you have a question most of the time you get a serious and good answer.

Keep up the good work.

Kankomi

---

