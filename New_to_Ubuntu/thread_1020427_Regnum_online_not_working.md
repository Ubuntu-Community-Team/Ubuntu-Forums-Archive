---
title: "Regnum online not working"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Cammytea on 2008-12-24
Hi guys,

I have downloaded Regnum and it seems to be perfectly fine but whenever I click  on the Regum icon it dosent do anthing;
I have checked the permissions and they are fine.


please help:confused:confused:

---

### Post by zoundz on 2008-12-24
It could simply be an empty desktop icon you're clicking.  It may not be linked to the game.  Hold alt and press F2, type in regnum, it should fill out the program name as you type.  Try starting the game that way.

---

### Post by nhasian on 2008-12-24
we just went through this yesterday :)

[http://ubuntuforums.org/showthread.php?t=1019277](http://ubuntuforums.org/showthread.php?t=1019277)

---

### Post by Cammytea on 2008-12-24
Well, tryed that but it says cd: 1: can't cd to /home/romereactor/RegnumOnline

Any ideas?

---

### Post by Cammytea on 2008-12-24
Now it is starting to say: Sorry, but you cannot execute commands from a remote site.

---

### Post by RomeReactor on 2008-12-24
Hi. That command was just an example; you need to change "/home/romereactor/RegnumOnline" for the location on your computer. Do you know where the files were installed?

---

### Post by Cammytea on 2008-12-24
well, heres the problem I accidently moved to trash...and when I try to open from trash it says it cant open remotly, and it says I cant cant move it out of trash now!

---

### Post by djbushido on 2008-12-24
Also, shouldn't it be: ```
 cd /home/<your_name>/Regnum\ Online
```
The slash between Regnum Online needs to be there. But really you should navigate to where you installed the files, this is just syntax

---

### Post by Cammytea on 2008-12-24
Well it says there is no such file or directory

---

### Post by RomeReactor on 2008-12-24
> **djbushido said:**
> Also, shouldn't it be: ```
 cd /home/<your_name>/Regnum\ Online
```

Depends on the name of the folder where the game was installed. If I remember correctly, you can create a folder during the installation; I named mine "RegnumOnline".

Cammytea, if you still have the folder in the trash, right-click on it and select **restore**. And we need to know the location of the rolauncher file.

---

### Post by djbushido on 2008-12-24
RomeReactor is right on the trash folder. Also, don't just go pasting commands into the terminal without knowing what they are. My command was just to show syntax, was not actually intended to be run. All I was trying to do was show that you need a '\' before spaces and commas. Try restoring it from trash, and then we'll help you more.

---

### Post by Cammytea on 2008-12-24
maybe I should try reinstalling it, Im only 12 so this complicated stuff kind of confuses me and I only started ubuntu a few days ago, I think if I reinstall (do I use 32-bit or 64-bit?) I can put it where I want it and see if it will run, maybe?

---

### Post by Cammytea on 2008-12-24
When I try to get out of trash it has a padlock over it and says I dont have permission although I ticked the open as program permmission

---

### Post by djbushido on 2008-12-24
The 32 or 64 bit version depends on your system. do you know what computer you use?
Also, if you are going to re-install, then delete the copy in your trash folder so you aren't taking up too much space. But if you really don't want to find out if you need 32 or 64 bit, go with 32 because it will still work on 64 bit machines.

EDIT: as to the trash, if you really want to clear it out, here is the command you would use:
```
 sudo rm -rf /home/<your_name>/.local/share/Trash/files/*
```

note: this will remove your ENTIRE trash folder, so use with caution, and substitute your username instead of '<your_name' so if your name is brian, do this:
```
 sudo rm -rf /home/brian/.local/share/Trash/files/*
```

And please, be careful when doing this.

---

### Post by RomeReactor on 2008-12-24
Let's back up a little. Is the folder where you installed Regnum still there?

---

### Post by Cammytea on 2008-12-24
Ok it is out of trash and has full permission and no padlock but still not working

---

### Post by Cammytea on 2008-12-24
it is saved in my desktop

---

### Post by djbushido on 2008-12-24
what is the name of the folder? ex: /home/<your_name>/RegOnline?

---

### Post by RomeReactor on 2008-12-24
Allright now let's try this from the terminal:
```
ls ~/Desktop
```
To find the correct name of the folder. Please post the result of that.

---

### Post by Cammytea on 2008-12-24
it is called regnum online

---

### Post by Cammytea on 2008-12-24
sorry it is:
regnum-desktop.desktop

---

### Post by djbushido on 2008-12-24
lets go back to a previous post. If you restored it, trying typing alt-f2, entering in regnum, and see what happens then.

Also, try clicking on the desktop item, and also
```
 cd ~/Desktop
./regnum-desktop.desktop
```

If none of these work, post back the results.

---

### Post by RomeReactor on 2008-12-24
> **Cammytea said:**
> sorry it is:
regnum-desktop.desktop

Hmmm... that *does* look like a launcher. That's not a folder, is it?

---

