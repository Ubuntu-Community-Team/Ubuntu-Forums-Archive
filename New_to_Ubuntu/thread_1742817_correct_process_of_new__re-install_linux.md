---
title: "correct process of new / re-install linux"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by Linux&amp;Gsus on 2011-04-29
OK, this might sound like a stupid question. But I've never done it that way, so I wanna make sure I'm doing the right thing.

First off, I have a separate /home partition with all my data. Also I have a backup of my data.

1) If I understand correct, during install I "simply" can mount my home partition again, so that I have all my data available. Correct? I'm just wondering how that works with user permissions... Will all the "just work"?

2) Since I make a fresh install, is there a way to save a list with all my installed programs so that install them again with one (or so) command? Or do I have to install them again 1-by-1?
What will happen with all my settings of all programs, dictionary of OpenOffice, desktop backgrounds, desktop themes, etc. Where are the desktop backgrounds stored anyway? I think, better safe the sorry, I'd like to make a backup of those things.


Thanks for any advise.
L&G

---

### Post by ~Plue on 2011-04-29
1) 
if you're the only user thats on the system then there shoudn't be any problem as the first user always gets a uid of 1000, if not, you should re-create the users in the same order as before or manually set the same uid while creating them (you can find the uid by *echo $UID*).

 2) 
 -to back up the list of applications currently installed: *dpkg --get-selections > /path/to/savefile*
-to restore it:  *sudo dpkg --set-selections < **/path/to/savefile*[I] && sudo apt-get dselect-upgrade
[/I]
as for the settings for applications, they are stored in your home folder within hidden  directies (press ctrl+H to see them)
the openoffice directory is in .config, the desktop wallpaper is reffered to in .gconf/desktop/gnome/background/, any user themes installed would be in .themes (or /usr/share/themes/ if you installed it system wide) and the default desktop backgrounds would be in /usr/share/backgrounds/ (you'll get them from the new install anyway :))

hope that helps..

---

### Post by nothingspecial on 2011-04-29
During the install process, when you get to the side by side or use the whole disc bit, choose other (or something else or whatever it is called)

Select your / partition and choose to use it as an ext4 journaling file system. Give it a mount point of / and tick/check the format box.

Select your /home partition and choose to use it as whatever file system it is. Give it a mountpoint of /home, but


[COLOR="Red"][SIZE="3"]DO NOT TICK/CHECK THE FORMAT BOX[/SIZE][/COLOR]

Swap will look after itself.

That's it.

---

### Post by Linux&amp;Gsus on 2011-04-29
Thanks lots for the help. 2 thumbs up.

Cheers,
L&G

---

### Post by Linux&amp;Gsus on 2011-04-29
There is one other question that came up while checking out the LiveCD.

Every time I upgrade, or install a new system for that matter, I have to mess around with the installed fonts. Or better say, the lack thereof. I have to search and find all my fonts again and then install them 1-by-1. There are many that are not in a pre-packed package like mscorefonts or ubuntustudio fonts.

Yes yes yes, it's my own fault that I have my fonts (.ttf files) scattered around in a few folders, shame on me, but still. Is there a way to save or package all my installed fonts and then install them on the new system afterwards?


Any advice is welcome.
L&G

---

### Post by Linux&amp;Gsus on 2011-04-30
Sorry to reply to myself, yet again. But I just had another question coming up.

Say, if I save the list of installed packages and I install the software again. Will it then install OpenOffice again, as well? Or will this be recognised somehow and all OpenOffice packages are automatically changed LibreOffice, as this is the default now?

On the other hand, I probably could also remove OpenOffice before I make the move. Shouldn't cause any trouble, I guess. Just curious.

---

### Post by ~Plue on 2011-04-30
> **Linux&Gsus said:**
>  Is there a  way to save or package all my installed fonts and then install them on  the new system afterwards?
All fonts installed using the font viewer would be stored in the .fonts folder in your home directory. You can just copy-past all the fonts you need to that folder instead of installing it one by one

> **Linux&Gsus said:**
> 
Say, if I save the list of installed packages and I install the software  again. Will it then install OpenOffice again, as well? Or will this be  recognised somehow and all OpenOffice packages are automatically changed  LibreOffice, as this is the default now?

On the other hand, I probably could also remove OpenOffice before I make  the move. Shouldn't cause any trouble, I guess. Just curious.

It'll install openoffice since it has its own packages..
The dpkg --set-selections to restore applications is effective when reinstalling the same release, but if you're installing a newer version,  it would be better to make the list of apps that you currently have yourself and install them selectively. thats because some programs that are listed from the  --get-selections option might not be needed anymore in the newer version..

---

### Post by Linux&amp;Gsus on 2011-04-30
Thanks for the advise.
I'm making the final backup on that machine right now, so I might compile a list with applications as well.

Cheers,
L&G

---

### Post by Linux&amp;Gsus on 2011-05-01
Thanks again for the help. :KS
I marked the thread as solved. My test/media machine is successfully upgraded and running Kubuntu 11.04

---

