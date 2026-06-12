---
title: "Anyone Know Where I Can Find Gnome-Do's Cache?"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by moore.bryan on 2010-01-17
Gnome-Do won't use my new icons and although the devs say this is solved in the latest package--that I have--I'm still having that old problem.

Any ideas where Gnome-Do hides its cache?

---

### Post by moore.bryan on 2010-01-27
*Nobody* knows?

---

### Post by chaanakya_chiraag on 2010-01-27
Try the following commands in a Terminal (Applications->Accessories->Terminal):
```
sudo updatedb
```
and then
```
locate gnome-do | grep /home/$USER
```
That should give you an idea of where things are located.
Most likely, they are located in /home/$USER/.local/share/gnome-do or something similar.

---

### Post by moore.bryan on 2010-01-27
Thanks, chaanakya_chiraag, but I tried this one; no dice. There is a random thread in the Google Groups for gnome-do about GNOME saving two copies of icons (old & new) and gnome-do is confused about which to use, but it also doesn't give any directions on how to find and/or delete those files.

---

### Post by chaanakya_chiraag on 2010-01-27
Have you tried restarting gnome-do after changing the icon theme?  Sometimes that helps.  Same thing with newly added menu items - restart to make them available in Gnome-Do.  I think it should automatically use the new icons...

---

### Post by moore.bryan on 2010-01-27
Yeah... I've not only restarted Gnome-Do, but gone to the length of completely rebooting the machine. No luck for me.

---

### Post by chaanakya_chiraag on 2010-01-27
Now what exactly are these new icons?  Did you install a new icon theme?  Did you change a menu item's icon?

---

### Post by moore.bryan on 2010-01-27
I wrote a couple of scripts and made a menu entry for them. I decided I didn't like the icons I chose, so I switched them. They show-up fine in the menu, now, but gnome-do chooses not to notice.

---

### Post by chaanakya_chiraag on 2010-01-27
That's weird...I have no idea where the cache is, although i've looked in .cache, etc. There's nothing in .local/share.  Try moving  the .local/share/gnome-do to .local/share/gnome-do-backup and restart gnome-do. Does that change anything?

---

### Post by falconindy on 2010-01-27
Gnome-Do uses .desktop files to determine the icons for programs. Beyond that I can't help you. In the time I used Gnome-Do, I was never able to determine where the actual cache was. I have to believe that it's within your $HOME.

---

### Post by moore.bryan on 2010-01-28
> **chaanakya_chiraag said:**
> That's weird...I have no idea where the cache is, although i've looked in .cache, etc. There's nothing in .local/share.  Try moving  the .local/share/gnome-do to .local/share/gnome-do-backup and restart gnome-do. Does that change anything?
I'll have to try this one when I get home...

> **falconindy said:**
> Gnome-Do uses .desktop files to determine the icons for programs. Beyond that I can't help you. In the time I used Gnome-Do, I was never able to determine where the actual cache was. I have to believe that it's within your $HOME.
Already checked there, to no avail...

---

### Post by moore.bryan on 2010-01-28
> **chaanakya_chiraag said:**
> That's weird...I have no idea where the cache is, although i've looked in .cache, etc. There's nothing in .local/share.  Try moving  the .local/share/gnome-do to .local/share/gnome-do-backup and restart gnome-do. Does that change anything?
No dice.

---

### Post by chaanakya_chiraag on 2010-01-28
Did you have gnome-do open while you did that?

---

### Post by moore.bryan on 2010-01-29
> **chaanakya_chiraag said:**
> Did you have gnome-do open while you did that?
Nope.

---

### Post by SpadeIV on 2010-03-23
> **moore.bryan said:**
> I wrote a couple of scripts and made a menu entry for them. I decided I didn't like the icons I chose, so I switched them. They show-up fine in the menu, now, but gnome-do chooses not to notice.

I don't believe it - I wrote the solution to this problem about 5-6 times now but everytime i click "submit" it gets deleted... So now one more time with opera.

Okay, here is what I got.
My problem, same as yours: Wrote a script, made an icon, added icon to script, added script to gnome-menu, added to gnome-do, changed icon in menu, gnome-do did NOT DO it.

My solution:
Deleted the icon i created, started gnome-do in terminal, looked up my script in gnome do, got an icon error in  /home/USERNAME/.local/share/applications
Went there, found a copy of my script WITHOUT an icon (i just deleted that, right?), added my new icon. Started gnome-do. New icon shows up. Finish.

Please let me know if it works for you... or somebody else.

Cheers.

---

### Post by chaanakya_chiraag on 2010-03-24
I've actually stopped using Gnome-Do and started using Kupfer, which is transparent with respect to cache, config, etc. It also automatically updates the cache with new files, new apps, etc.

---

### Post by moore.bryan on 2010-03-24
I've switched over to Gnome-Shell, so this is also moot for me.

---

### Post by chaanakya_chiraag on 2010-03-24
I've switched over to Fluxbox :D

---

### Post by jeffltw on 2010-08-19
> **SpadeIV said:**
> I don't believe it - I wrote the solution to this problem about 5-6 times now but everytime i click "submit" it gets deleted... So now one more time with opera.

Okay, here is what I got.
My problem, same as yours: Wrote a script, made an icon, added icon to script, added script to gnome-menu, added to gnome-do, changed icon in menu, gnome-do did NOT DO it.

My solution:
Deleted the icon i created, started gnome-do in terminal, looked up my script in gnome do, got an icon error in  /home/USERNAME/.local/share/applications
Went there, found a copy of my script WITHOUT an icon (i just deleted that, right?), added my new icon. Started gnome-do. New icon shows up. Finish.

Please let me know if it works for you... or somebody else.

Cheers.

Thanks this works for me.

---

### Post by isleshocky77 on 2010-09-18
> **SpadeIV said:**
> 
My solution:
Deleted the icon i created, started gnome-do in terminal, looked up my script in gnome do, got an icon error in  /home/USERNAME/.local/share/applications
Went there, found a copy of my script WITHOUT an icon (i just deleted that, right?), added my new icon. Started gnome-do. New icon shows up. Finish.

Please let me know if it works for you... or somebody else.

Cheers.

Awesome! Thanks so much for helping me get going in the right direction for this. I've been trying to solve this problem sporadically for over a year or two. I've found it to be a little easier than that though.

```

cd /home/$USER/.local/share/applications
grep "pdt" *

```

Here I noticed that there was a problem with the "Icon" attribute"

```

alacarte-made-2.desktop:Icon[en_US]=/opt/pdt/php_icon.png
alacarte-made-2.desktop:Icon=/opt/pdt/eclipse/icon.xpm

```

It appears that when it updated it only changed the en_US version and left the default the same. I change the "Icon" to be the same as the "Icon[en_US]", restarted gnome-do and viola, it works.

Hope this helps someone else out there.

---

### Post by WiNeOS on 2010-10-02
Deleting desktop files from here:
cd /home/$USER/.local/share/applications

Solved my problems with Do too.

Greetz

---

