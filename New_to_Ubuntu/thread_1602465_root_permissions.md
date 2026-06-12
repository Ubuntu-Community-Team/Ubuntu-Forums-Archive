---
title: "root permissions"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by Legeril on 2010-10-21
I've tried a few times to copy files to /user/share.. but I don't have permission, I know you can get permission through "sudo" in the terminal. How do I get permission to move files around in Gnome?

I'm trying to install a new theme from [http://gnome-look.org/content/show.php/Divergence+IV+-+%22A+New+Hope%22?content=133892&PHPSESSID=649c02031c6879c50017d5a350b6cecc](http://gnome-look.org/content/show.php/Divergence+IV+-+%22A+New+Hope%22?content=133892&PHPSESSID=649c02031c6879c50017d5a350b6cecc) . It saying the first step is to copy the file the the ../themes folder but I can't do it :(

help appreciated, thank you

---

### Post by uRock on 2010-10-21
```
gksudo nautilus
``` will open nautilus in root mode, which will allow you to copy/edit from the / folders. Beware of what you do as you can damage your system this way.

---

### Post by Legeril on 2010-10-21
How long does this last? Is it a 15minute window like normal sudo? A know permininant root access can be dangerous I just want to copy 1 folder to my ../themes

---

### Post by uRock on 2010-10-21
I think it lasts as long as you have it open.

---

### Post by CharlesA on 2010-10-21
Until you close the window.

---

### Post by AngusH on 2010-10-21
Root perms apply to that process for as long as it lasts (whether you use sudo or gksudo). Sudo (and therefore gksudo) have a timestamp that means you can reactivate root perms without a password if you have used one of them WITH a password in the last 15 mins.
Essentially closing the window will kill root perms. If your worried about someone accessing your computer in the next 15 mins and abusing that timestamp run "sudo -k" to clear it.
Angus

---

### Post by Legeril on 2010-10-21
OK thank you guys, as always very quick replies. 

I'll mark as solved as soon as I've tried and tested

---

### Post by Legeril on 2010-10-21
Worked great, thanks guys for a great little tip.

Although I haven't managed to install me theme (again) I will now mark this thread as closed.

---

