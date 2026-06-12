---
title: "True, controlled and efficient SETTINGS backup??"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by Enginirical on 2010-04-16
Hi 

I have read loads of posts on backing up settings and none seem to provide a straightforward answer...

ok, what do I mean by settings? I'm talking about:
[LIST]
[*]Visual settings, compiz, metacity, fonts, themes, desktop layout etc.
[*]Program settings, firefox (soon to change to chrome), tomboy notes, games, vlc, wine etc. [example: I keep notes on my system in tomboy but can't even find them in /home/.tomboy]
[*]Network settings
[/LIST]

All I want is the ability to format, upgrade or whatever with confidence that setting have been saved. I DONT just want to copy and paste my home folder because 1) after a few iterations of distros it will just get bloated with redundant files that newer versions (or programs) might not use and 2)I've done it before many times and it NEVER recovers all settings.

With constant distro updates it is a proper ball ache doing all this from scratch every time. I am more than happy to re-install programs and plugins as that guarantees fresh up to date files.

So what are the individual files I should aim to backup?
I understand it would be a mix of files from /home /etc /usr /var?

I also found this which looks a use full tool but I still need to know WHAT to backup: 
[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html]("http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html")

ANY direction on this would be muchly appreciated to once and for all understand what goes where in an ubuntu file system. Perhaps we can develop a straight forward list for all those who wish to do a true, controlled and efficient backup of settings.

Thanks for reading :)

---

### Post by -humanaut- on 2010-04-16
Why don't you just make a copy of your settings e-mail yourself and save it in a .txt file and put it in the cloud?

---

### Post by switch10 on 2010-04-16
> **Enginirical said:**
> Hi 

I have read loads of posts on backing up settings and none seem to provide a straightforward answer...

ok, what do I mean by settings? I'm talking about:
[LIST]
[*]Visual settings, compiz, metacity, fonts, themes, desktop layout etc.
[*]Program settings, firefox (soon to change to chrome), tomboy notes, games, vlc, wine etc. [example: I keep notes on my system in tomboy but can't even find them in /home/.tomboy]
[*]Network settings
[/LIST]

All I want is the ability to format, upgrade or whatever with confidence that setting have been saved. I DONT just want to copy and paste my home folder because 1) after a few iterations of distros it will just get bloated with redundant files that newer versions (or programs) might not use and 2)I've done it before many times and it NEVER recovers all settings.

With constant distro updates it is a proper ball ache doing all this from scratch every time. I am more than happy to re-install programs and plugins as that guarantees fresh up to date files.

So what are the individual files I should aim to backup?
I understand it would be a mix of files from /home /etc /usr /var?

I also found this which looks a use full tool but I still need to know WHAT to backup: 
[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html]("http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html")

ANY direction on this would be muchly appreciated to once and for all understand what goes where in an ubuntu file system. Perhaps we can develop a straight forward list for all those who wish to do a true, controlled and efficient backup of settings.

Thanks for reading :)

all of the config files are located in your /home folder, hidden in your user dir.  For example, .compiz is all of your compiz settings.  

I use rsync in a cron job to automatically backup my /home folder.  I also run the following in a cron job to make a list of all installed packages, and backup /etc/apt/sources.list. 

```
 sudo dpkg --get-selections > /home/dave/upgrade/installed_packages
sudo rsync -a /etc/apt/sources.list /home/dave/upgrade/

```

I recommend backing up /etc/fstab, or anything else you may have edited outside of /home.

Then to restore sources.list, and install all of your packages on a new system, after recovering your /home dir, I run the following as part of a script.

```
#replace sources.list
sudo cp /home/dave/upgrade/sources.list /etc/apt/
sudo apt-get update


##install packages
sudo dpkg --set-selections < /home/dave/upgrade/installed_packages    
##install dselect
sudo apt-get install dselect
sudo dselect


###Upgrade all packages
sudo apt-get --yes upgrade

```

it is unnecessary to backup anything other than /home, and some random files in /etc.  Using this method, all of your settings/effects, even the fonts are saved.  It truly is a flawless method.

---

### Post by oOarthurOo on 2010-04-16
What you describe isn't possible. You can't switch distros and expect nothing to change. Fedora does thinks differently than Ubuntu, which does things differently than Debian. Never mind different methods, but even different versions of applications will do things differently, sometimes. Things get deprecated. Things change. 

You'll find distros put a lot of effort into making upgrades from on version to another without losing user preferences and settings. And even then it is not always a perfect, perfectly smooth transition. 

If you're hopping between distros that are closely related, like Ubuntu and Mint, or Debian and Sidux, then you'll find that things work usually pretty good just by backing up home. If you're going from Ubuntu Beta, to Fedora 10, things will get borked. And there is no easy way around that. It's just a price you pay for jumping between distros.

---

### Post by Enginirical on 2010-04-16
Thanks for your responses! 

To clarify I refer to transitioning to different ubuntu releases. I have considered other linux distros but would stick with debian for now until I feel like I know EXACTLY what I'm doing. Version wise I never upgrade, but rather prefer to re-format to eliminate glitches/bugs and random unexpected things occurring as it has done in the past.

I think I have previously missed the "random settings in /etc" and the sources list. Thanks for the hint in using "rsync in a cron job" no idea what that is but I'm sure google will enlighten me further. I'll be sure to try it out! 

I went from Feisty to Intrepid using the same /home folder in a separate partition and it did begin to get bloated with what I think were obsolete files after a while hence why I wanted to identify as many specific settings files as possible. 

thanks again for the advice :biggrin:

---

### Post by switch10 on 2010-04-16
rsync is a program similar to cp, but it only updates files and dirs that have changed info, and it only transfers the updated info.  a cron job is a way to automate running scripts.  Google will tell you more...

The only files you will need to backup in /etc, are files that you have made changes to.

Have you considered putting your /home on a separate partition?

---

### Post by Paqman on 2010-04-16
> **switch10 said:**
> a cron job is a way to automate running scripts.

Cron was really designed for servers which run 24/7. For desktops there's a much better system called anacron, which will run your jobs even if the machine was turned off when they were supposed to run. It's also really easy to use, unlike cron which has gnarly syntax.

If you back up all the .folders in your home, that's all your settings sorted. Residual obsolete config files isn't really a big issue IMO, as it's not often that apps switch to a completely new folder, and there's nothing stopping you from doing a little cleanout every 12 months or so if you're concerned about it.

---

### Post by oOarthurOo on 2010-04-16
> **Paqman said:**
> Cron was really designed for servers which run 24/7. For desktops there's a much better system called anacron, which will run your jobs even if the machine was turned off when they were supposed to run. It's also really easy to use, unlike cron which has gnarly syntax

My understanding is that anacron runs cron tasks that didn't execute because the machine was turned off. They work in conjunction, not exclusively.

I'd be happy to learn better if I'm wrong. I could uninstall cron!

---

### Post by Paqman on 2010-04-17
> **oOarthurOo said:**
> My understanding is that anacron runs cron tasks that didn't execute because the machine was turned off. They work in conjunction, not exclusively.

I'd be happy to learn better if I'm wrong. I could uninstall cron!

Technically yes, but you can use anacron without understanding how cron works. You just drop your script into the right directory and anacron does all the work for you.

---

### Post by switch10 on 2010-04-17
The reason that I don't use anacron, is that it can only be run once a day.  I have many cron jobs (including my backup) that run several times per day...

I prefer cron over anacron.

---

### Post by Paqman on 2010-04-17
> **switch10 said:**
> The reason that I don't use anacron, is that it can only be run once a day.  I have many cron jobs (including my backup) that run several times per day...

I prefer cron over anacron.

Well, yes. If you're running it that often then there's no reason your couldn't use cron, since it's likely to get run no matter what hours your machine is switched on.

---

### Post by jelevin on 2010-04-18
> **switch10 said:**
>  I recommend backing up /etc/fstab, or anything else you may have edited outside of /home... and **some random files in /etc** 

This is why ubuntu upgrades cause me to tear my hair out.  Is there a way that I can do a fresh install of a new system but retain my old /etc files and have the installation program give me the opportunity to keep the modified files or replace with new files?

---

### Post by switch10 on 2010-04-19
When I say "random files" I mean files that you yourself personally edited for one reason or another.  Some people have never edited any of this stuff manually, if that is the case, don't worry about it.  /etc/apt/sources.list can easily be rebuilt upon a new install.

---

