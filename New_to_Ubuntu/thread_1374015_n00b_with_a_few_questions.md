---
title: "n00b with a few questions"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Spa_ced on 2010-01-06
I've just installed ubuntu 9.10 on my laptop (IBM T43)
My experience is about 4 days now.

I've installed the restricted extras to play my xvid files, along with kpowersave as it seemed to have more options that gnome power manager. 
I also installed a program called powertop to help save a bit more power.
and an on screen display for volume and brightness levels.
I was looking for a program to control the fan speed of my laptop and found this one 

[http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control](http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control)
but there didn't seem to be a version for ubuntu 9.10. 
would an older version work for it?

Can i uninstall gnome power manager without anything bad happening?
Is there any other programs you would recommend?

Another thing i read when installing ubuntu was that setting up a separate partition for "/home" would help save all my documents and pictures from being lost.
So i set that up, but just wanna know if that was accurate?

Thanks for any help given. :)

---

### Post by mikechant on 2010-01-06
Deleted - incorrect.

---

### Post by Spa_ced on 2010-01-06
> **mikechant said:**
> Deleted - incorrect.


erm.......huh?

---

### Post by mocoloco on 2010-01-06
About the fan control app, normally I would say just try it an see but in this case it's something that could break your hardware so maybe ask the developers.

You can safely remove gnome-power-manager, it will remove a metpackage called ubuntu-desktop which is safe to remove, it exists to have one package dependent on the standard Ubuntu install.

You are correct about the /home partition.  When you install a new version, you'll always need to select to manually edit partitions, then set the correct ones for / and for /home and make sure NOT to format /home.

---

### Post by K.J. on 2010-01-06
Well it doesn't save your documents per se. It simply allows you do reinstall the OS without having to backup your home directory. It does NOT protect against catastrophic failure (i.e. drive failure) or accidental deletion. You should still backup.

On another note, I've had difficulties getting the KDE powersave to function correctly in Gnome, although if its working well, removing gnome powersave shouldn't be an issue (unless it wants to remove the base install along with it).

Installing an older version shouldn't be an issue, although I'm pretty sure there are some fan control programs in the repositories.

---

### Post by nothingspecial on 2010-01-06
[[COLOR="Magenta"]How to create a home partition[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Spa_ced on 2010-01-06
> **mocoloco said:**
> About the fan control app, normally I would say just try it an see but in this case it's something that could break your hardware so maybe ask the developers.

You can safely remove gnome-power-manager, it will remove a metpackage called ubuntu-desktop which is safe to remove, it exists to have one package dependent on the standard Ubuntu install.

You are correct about the /home partition.  When you install a new version, you'll always need to select to manually edit partitions, then set the correct ones for / and for /home and make sure NOT to format /home.

thanks for the reply, ive now removed gnome power manager and will head over to the fan control people and ask them if they are planning to release a version for 9.10.

[quote=K.J]Well it doesn't save your documents per se. It simply allows you do reinstall the OS without having to backup your home directory. It does NOT protect against catastrophic failure (i.e. drive failure) or accidental deletion. You should still backup.
[/quote]

thanks for that, im looking into finding a decent backup program that can backup my files to my home server on a regular basis. and i will hopefully not have too many problems with the powersave function on kpowersave, but if i do ill look at finding another program :)

Thanks for the link [nothingspecial]("http://ubuntuforums.org/member.php?u=491516"), looks like a good amount of information on there, one for the bookmarks i think :)

---

### Post by mikechant on 2010-01-08
> Deleted - incorrect. 

> erm.......huh?

I made a post that I thought was helpful, realized it was wrong and not helpful, and 'deleted' it. You can't actually remove a post or even make it blank so I changed it to 'Deleted - incorrect'. Sorry if this was confusing!

---

