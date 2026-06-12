---
title: "uninstall lxde"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by dzon65 on 2010-03-23
This is a minimal gnome install.A while back I installed lxde to be able to log in in a lxde session.But,(posted this on the forum),since in lxde I couldn't set the default progs to open files,I decided to uninstall it and hoped there was a update to resolve that problem (it's a known bug).However,uninstalling and reinstalling lxde didn't solve the problem.But what's more,lxde opens with the same configuration as before,with which I mean,same wallpaper,icons...you name it.How can I get lxde to be opened "fresh",default?

---

### Post by patchwork on 2010-03-23
Did you remove or did you purge lxde before?
Removing will retain the configuration files.  Purging gets rid of everything related to the package.

---

### Post by bodhi.zazen on 2010-03-23
lxde is a meta package and uses a ton of applications, primarily openbox and lxde-panel

Your configurations are stored in ~ (your home directory) in hidden or . files.

You would need to delete these config files if you wish to change the defaults.

I am not familiar with all the lxde packages to know all the . files, but are you sure anything has really changed in terms of the defaults ?

---

### Post by dzon65 on 2010-03-23
Yep,same outcome.

---

### Post by bodhi.zazen on 2010-03-23
> **patchwork said:**
> Did you remove or did you purge lxde before?
Removing will retain the configuration files.  Purging gets rid of everything related to the package.

  Purge will not remove config, or . files in your home directory.

---

### Post by dzon65 on 2010-03-23
Mr B.Will check it out.Btw,about that default problem I posted.Here's what I meant:[http://ubuntuforums.org/showthread.php?t=1419726](http://ubuntuforums.org/showthread.php?t=1419726)
It's strange cause I tried to install lxde on some old pc's and always the problem was there,so I had to install thunar as file manager.When installing slitaz to those same pc's ,that prob wasn't there.In fact,friends of mine don't have that problem when installing lxde.
Anyway,will check and delete the files you mentioned and I'll post the outcome.Thanks for the replies.
Kind regards,J.

---

### Post by dzon65 on 2010-03-23
Okay,just checked the home directory,but I'm not quite sure which files you mean."Hidden",and ".files" aren't there.

---

### Post by dzon65 on 2010-03-23
Deleted the whole lxde file in .config.Logged in in lxde,same outcome.Gonna purge and remove all lxde related files and see what it gives.Will post the outcome.

---

### Post by kerry_s on 2010-03-23
i thought you was going to try a fresh lubuntu install?

to truly start fresh, i would log into fail safe terminal and wipe out everything in /home/you/* or just create a new user & delete the old 1, make sure you give the new user admin permission.

in fail safe terminal:
```

sudo su
rm -rf /home/you/*
exit
exit

```

everything will be made new like you were logging in for the first time.

did you add the lubuntu ppa? they got the more updated stuff.
```
sudo add-apt-repository ppa:lubuntu-desktop/ppa
```

---

### Post by dzon65 on 2010-03-23
Kerry,first this.Uninstalled lxde and all it's parts,deleted all files remotely related to lxde.Reinstalled lxde(and all it needs).Rebooted,logged in in lxde.Most things were back to normal,exept for the wallpaper.Tried to log out but as soon as I hit the logout button everything was a goner (panel,menu....).Had to use the power button to get back.

---

### Post by dzon65 on 2010-03-23
> **kerry_s said:**
> i thought you was going to try a fresh lubuntu install?

to truly start fresh, i would log into fail safe terminal and wipe out everything in /home/you/* or just create a new user & delete the old 1, make sure you give the new user admin permission.

in fail safe terminal:
```

sudo su
rm -rf /home/you/*
exit
exit

```everything will be made new like you were logging in for the first time.

did you add the lubuntu ppa? they got the more updated stuff.
```
sudo add-apt-repository ppa:lubuntu-desktop/ppa
```

Okay kerry.Don't really need lubuntu.I suppose it's your only OS?If I install lubuntu desktop on top of ubuntu,there's some uther weird stuff happening.Some aps are (sorry for my english) appearing double in the menus.For example twice synaptics,twice OB (menu...)whatever.We spent some times on this already on the forum for this.For some weird reason lxde or lubuntu for that matter simply do not work.As I mentioned before in this thread,running slitaz live.....no prob whatsoever.I really don't get it.Tell you what,gonna do a TOTAL reinstall and see what happens.That's for tommorow though,but I sure will post the outcome.
Anyway,thanks for the replies people.Kind regards,J.

---

### Post by kerry_s on 2010-03-23
> **dzon65 said:**
> Kerry,first this.Uninstalled lxde and all it's parts,deleted all files remotely related to lxde.Reinstalled lxde(and all it needs).Rebooted,logged in in lxde.Most things were back to normal,exept for the wallpaper.Tried to log out but as soon as I hit the logout button everything was a goner (panel,menu....).Had to use the power button to get back.


i don't know, sounds to me like you got some screwed up permission issues. try doing the new user & make sure you add the user to the admin group. it would be a fresh profile so i would assume it would work right, unless you got something messed up in the base.

---

### Post by dzon65 on 2010-03-23
Yes perhaps.This whole lxde issue got me a bit ...je ne sais quoi.Like I said,gonna start allover again.This is about the third or fourth time I do it though.It IS a known bug.Not much to be googled/found however.
One more thing.If I open pictures/images in pcmanfm/lxde there aren't any thumbnails,only some icons.This is indeed a really weird thing.
Tommorow.

---

### Post by kerry_s on 2010-03-23
> **dzon65 said:**
> Yes perhaps.This whole lxde issue got me a bit ...je ne sais quoi.Like I said,gonna start allover again.This is about the third or fourth time I do it though.It IS a known bug.Not much to be googled/found however.
One more thing.If I open pictures/images in pcmanfm/lxde there aren't any thumbnails,only some icons.This is indeed a really weird thing.
Tommorow.

write down that lubuntu ppa, after you do your cli/mini install add the lubuntu repo(sudo add-apt-repository ppa:lubuntu-desktop/ppa) & "sudo apt-get install lubuntu-desktop" that should get you a fully updated lubuntu install.

mines working sweet, i'm fully updated, the boot splash has been working, i have had no crashes from anything. i found out openbox can be set to maximize all windows, so i got rid of maximus. i edited the theme for a larger border & made it so i can grab the top left corner to move the windows around, added some programs to not maximize(aka:whitelist). the trash right click empty works. the applications section works, some thing i don't think is needed, i would rather have "My Computer"(aka:root,/) like in the "Go" menu section.
i'm very happy all the same.

---

### Post by dzon65 on 2010-03-24
Kerry,made a new thread for this.[http://ubuntuforums.org/showthread.php?t=1437636](http://ubuntuforums.org/showthread.php?t=1437636)

---

