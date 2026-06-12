---
title: "Disabling CD Drive."
date: 2010-04-13
forum: New to Ubuntu
---

### Post by karthick87 on 2010-04-13
My friends used to play movies in my system most of the time.So is there any way to disable CD Drive temporarily and then enable it again.?

---

### Post by Silent Warrior on 2010-04-13
I don't know. Maybe a script that unmounts the drive (unmount /media/cdrom), triggered by... something cleverly chosen? (And then remounting it!)

I'm really not sure I'd recommend this, though...

---

### Post by karthick87 on 2010-04-19
> **Silent Warrior said:**
> I don't know. Maybe a script that unmounts the drive (unmount /media/cdrom), triggered by... something cleverly chosen? (And then remounting it!)

I'm really not sure I'd recommend this, though...


No this didn't work for me.

---

### Post by Drenriza on 2010-04-19
Why dont you in the options of the drive (fstab) set so only you "if its your system" the root user is the only person who can mount & umount the drive.

the option is, ```
nouser
```
to only allow the root user to mount and umount the drive.

---

### Post by warfacegod on 2010-04-19
Go to System> Admin.> Users and Groups> click Unlock, enter password> highlight a user account> click properties> User Privileges tab> scroll down and uncheck "Use CD-ROM drives"> click OK.

Rinse and repeat as needed.

---

### Post by Drenriza on 2010-04-19
> **warfacegod said:**
> Go to System> Admin.> Users and Groups> click Unlock, enter password> highlight a user account> click properties> User Privileges tab> scroll down and uncheck "Use CD-ROM drives"> click OK.
 
Rinse and repeat as needed.
 
Wow thats a mouth full. Just to disable a cd-drive.

---

### Post by halitech on 2010-04-19
why not disable auto-login, change your password and set the screen saver to lock and ask for a password after 5 minutes. Don't give your "friends" the password to log in.

---

### Post by tom.swartz07 on 2010-04-19
> **halitech said:**
> why not disable auto-login, change your password and set the screen saver to lock and ask for a password after 5 minutes. Don't give your "friends" the password to log in.

If youre just trying to lock your cd drive,
```
eject -i on
```
will prevent the drive from opening, no matter how many times you hit the button.
then when you want to open it again,```
eject -i off
``` will unlock the drive


I use it all the time because i accidentally bump the eject key on my desktop with my chair quite often

---

### Post by warfacegod on 2010-04-19
> **Drenriza said:**
> Wow thats a mouth full. Just to disable a cd-drive.

Not really. I just did it right now. The whole process took less than 10 seconds.

---

### Post by tom.swartz07 on 2010-04-19
> **warfacegod said:**
> Not really. I just did it right now. The whole process took less than 10 seconds.

The eject method that I just said takes less than that! :P

If you set up an alias, it could be even quicker!

---

### Post by karthick87 on 2010-04-20
> **tom.swartz07 said:**
> If youre just trying to lock your cd drive,
```
eject -i on
```will prevent the drive from opening, no matter how many times you hit the button.
then when you want to open it again,```
eject -i off
``` will unlock the drive


I use it all the time because i accidentally bump the eject key on my desktop with my chair quite often


What happens if we restart the system,is it possible to eject the drive.?

---

### Post by cgroza on 2010-04-20
> **getyourkarthick said:**
> What happens if we restart the system,is it possible to eject the drive.?

Try it yourself! :)

---

### Post by tom.swartz07 on 2010-04-20
> **cgroza said:**
> Try it yourself! :)

I believe it stays with the last command until you change it, no matter what you do to the system (restart, suspend, etc). I could be wrong though.. Definitely try it!

---

