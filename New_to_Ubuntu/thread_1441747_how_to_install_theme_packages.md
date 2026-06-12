---
title: "how to install theme packages"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by Nisal on 2010-03-29
when i get theme packages (login windows) i can't find a .deb.can any one please tell me what the way to install them?

i got themes from here 

```
http://art.gnome.org/themes/gdm_greeterhttp://art.gnome.org/themes/gdm_greeter
```

---

### Post by lotharmat on 2010-03-29
having looked through some of the tarballs that are in the links you posted; there are 'readme's' in them - I'd follow the instructions contained therein.

---

### Post by Nisal on 2010-03-29
> **lotharmat said:**
> having looked through some of the tarballs that are in the links you posted; there are 'readme's' in them - I'd follow the instructions contained therein.

okay i downloaded this 

```
http://art.gnome.org/download/themes/gdm_greeter/1201/GDM-BlueSwirl.tar.bz2
```

and in readme it says "Use 'gdmsetup' to install."

well it kinda too short for newbie to understand does this mean i have use "gdmsetup" as a command in terminal ?

---

### Post by 3rdalbum on 2010-03-29
You can't use those themes with the version of GDM that shipped with Ubuntu 9.10 and 10.04. Normally you would have used the System > Administration > Login Window program (which is 'gksudo gdmsetup', so yes it's a terminal command) but the new version of GDM cannot be themed this way.

---

### Post by Nisal on 2010-03-29
> **3rdalbum said:**
> You can't use those themes with the version of GDM that shipped with Ubuntu 9.10 and 10.04. Normally you would have used the System > Administration > Login Window program (which is 'gksudo gdmsetup', so yes it's a terminal command) but the new version of GDM cannot be themed this way.

so how can i apply these themes or u mean i cant use them at all ?

---

### Post by lotharmat on 2010-03-29
Hmmm after googling around..


See [Here]("http://beginlinux.wordpress.com/2010/03/07/change-ubuntu-login-screen/") - Check out the comments

---

### Post by warfacegod on 2010-03-29
> well it kinda too short for newbie to understand

You might consider holding off with modifying your login screen until you are, as you put it, less of a newbie. It is fairly easy to break a 9.10 and 10.04 system if your not careful. Don't let me discourage you though. If you have your mind set on doing this then, by all means, have at it. That's what Ubuntu is all about.

If you find that things went south, especially if you're only getting text screens, these codes may help:

```
sudo apt-get purge gdm
```

```
sudo apt-get install gdm
```

---

### Post by Nisal on 2010-03-29
> **warfacegod said:**
> You might consider holding off with modifying your login screen until you are, as you put it, less of a newbie. It is fairly easy to break a 9.10 and 10.04 system if your not careful. Don't let me discourage you though. If you have your mind set on doing this then, by all means, have at it. That's what Ubuntu is all about.

If you find that things went south, especially if you're only getting text screens, these codes may help:

```
sudo apt-get purge gdm
```

```
sudo apt-get install gdm
```

well i m going to give a shot thanks

---

### Post by biswajitLinux on 2010-03-29
How to set the grub loader password??

---

### Post by Nisal on 2010-03-29
@warfacegod

i guess i got a crash :S 

[IMG]http://i41.tinypic.com/2uruzd0.png[/IMG]

---

### Post by warfacegod on 2010-03-29
Try this:

[http://ubuntuforums.org/showpost.php?p=8707543&postcount=55]("http://ubuntuforums.org/showpost.php?p=8707543&postcount=55")

I haven't used it so I can't comment on it's saftey.

I posted the codes in case something went badly for you. I wouldn't generally run them otherwise.:p

This may be useful as well:

[http://ubuntuforums.org/showthread.php?t=1332432]("http://ubuntuforums.org/showthread.php?t=1332432")

---

### Post by Nisal on 2010-03-29
well :P i got really bad effect OS crash totaly i had to install a fresh one couldn't reocver but im not stop trying till i figure this out :)

---

