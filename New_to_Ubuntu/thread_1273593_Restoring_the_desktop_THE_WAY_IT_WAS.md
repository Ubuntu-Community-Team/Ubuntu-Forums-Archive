---
title: "Restoring the desktop THE WAY IT WAS"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by BobJam on 2009-09-23
I want to know how to restore the desktop to the way I have it configured, **NOT THE DEFAULT DESKTOP.**

Someone told me that backing up and then restoring my /home partition won't do that, but if that is true, then where is my current desktop config?  In my / directory?

I have Sbackup.  If I use that to make a backup of my /home directory (on another partition), would that do it with the Sbackup restore function?

Or can I just backup a single file instead of the entire /home directory?

---

### Post by Cypher on 2009-09-23
If you backup your /home directory wholesale, and re-use that on another installion of Ubuntu, it will retain your configuration. The desktop settings are stored in your home directory in the directories (.gnome2, .gconf, .gconfd, .gnome2_private) and probably others. Your nautilus changes are saved in .nautilus and so on.

Drop to a terminal and type
```

ls -a

```
and you'll see all of the hidden directories for various applications. These directories contain all the info..

Regards

---

### Post by BobJam on 2009-09-23
I found an explanation listed [here]("http://www.cahilig.org/restore-broken-ubuntu-desktop") that says:[INDENT][FONT=Arial][COLOR=Blue][B][I]I screwed up my Ubuntu desktop. I accidentally deleted the panels and the icons on my Ubuntu desktop. The whole desktop is messed up, I can't figure out how to restore it?

After googling around, I found a solution how to fix this mess. To restore the Desktop settings, just run these command in the console:

[/I][/B][/COLOR][/FONT]```
cd /home/username
rm -rf .gnome2 .gconf .gconfd .metacity

```[FONT=Arial][COLOR=Blue][B][I]
Then reboot your computer[/I][/B][/COLOR][/FONT]
[/INDENT]This would seem to be related to what you said.  Would it work instead of doing a backup?

Don't misunderstand . . . I still intend to do a backup and I'm certainly not questioning your solution, but I just want to know if this will work too.

---

### Post by rustutzman on 2009-09-23
I believe those commands will reset the desktop back to the defaults. You're actually deleting the custom configuration files.

Russ

---

### Post by Bölvaður on 2009-09-23
> **Cypher said:**
> .[COLOR="Blue"]gnome2[/COLOR], .[COLOR="SeaGreen"]gconf[/COLOR], .[COLOR="SandyBrown"]gconfd[/COLOR], .gnome2_private

> **BobJam said:**
> ```
..[COLOR="Blue"]gnome2[/COLOR], .[COLOR="SeaGreen"]gconf[/COLOR], .[COLOR="SandyBrown"]gconfd[/COLOR] .metacity

```

All your settings and files should be stored in your home. The only things that do with the UI that aren't are system themes, those are the ones you install via Synaptic Package manager.

There are some hidden directories under home that you need to backup, but you cannot go back in time by removing directories (the rm command you quoted).

---

### Post by BobJam on 2009-09-23
OK . . . so as I'm understanding it:
[INDENT]1.  That command I found is **NO GOOD** for restoring existing settings, only the default.

2.  Backing up and restoring my home directory will put my desktop back the way I had it.

Is that correct?
[/INDENT]A follow-up question.

If I screw up my desktop settings, would it be sufficient to restore my /home directory, or would I have to do a clean install of Ubuntu also?  If so, is there any order necessary, e.g. Ubuntu first, and then the /home directory, or is there not any difference in the sequence?

---

### Post by earthpigg on 2009-09-23
ill try to clarify what this whole confusing mess is about by giving you the full who/what/when/where/why.

those files and folders in your /home/username/ that start with a dot (.) are called 'dotfiles'. they are the personal non-default settings for various applications.

whenever you bookmark something in firefox, change the desktop background, save your progress in a game, add an account in pidgin, or add something to the desktop panel, it saves those changes to the corresponding dotfile in your /home.

when you start a program (just about any program, including your graphical ubuntu desktop), it looks for those dotfiles.

if it finds them, it uses them.

if it does not find them, it creates them using the defaults. this is what happens with every program the first time you run it on a fresh install. this is also what happens when you delete the dotfiles because you messed a program up and just want it to go back to defaults.

so, if you put your own dotfiles there on a fresh install, the program will see them and use them. there is no command needed to do this. boot your fresh install, use the 'nautilus' graphical file manager to copy over your dotfiles from a thumb drive or cd, and select the option to replace the existing dotfiles. reboot, and BAM, those are the dotfiles that every program will use -- including ubuntu's graphical desktop.


you can do ***whatever*** you want to dotfiles in your /home ***whenever*** you want. changes will take effect next time you start a given program. the worst risk you take is losing personal settings, files and folders -- ubuntu will still boot & run just fine. and as long as you have your personal dotfiles, documents, music, pictures, etc, backed up then you are risking nothing at all.

this works in ubuntu because the graphical desktop is ***not*** an integral part of the system. it is nothing more than a collection of programs that use dotfiles - just like any other program.

edit: should clarify - some programs do not use /home dotfiles in this way. those are programs that ask you to enter your password to run or anything you start with 'sudo'.

---

### Post by earthpigg on 2009-09-23
> **BobJam said:**
> If I screw up my desktop settings, would it be sufficient to restore my /home directory, or would I have to do a clean install of Ubuntu also?  If so, is there any order necessary, e.g. Ubuntu first, and then the /home directory, or is there not any difference in the sequence?

if you screw any program up that does not ask you for your password to run, it is almost always not necessary to completely reinstall ubuntu. 

find it's dotfile, delete it, and restart that specific program. you will now be using the default settings for that program.

or, find it's dotfile and replace it with the dotfile you have backed up, and restart that specific program. you will now be using the settings you backed up earlier.

example: you want to play with 5000 addons in firefox but want to be sure you can restore firefox to the way it was before. back up the /home/yourusername/.mozilla folder first, do whatever zany things you want in firefox.

instead of reinstalling firefox, just replace the /home/yourusername/.mozilla folder with the one you backed up earlier.

another example:

want to set up pidgin on another linux computer (any linux computer with pidgin installed, not just ubuntu) without having to enter all your account information over again? 

back up the /home/username/.purple folder from your current computer, and copy it over on the target computer. next time you start pidgin, your accounts, chatlogs, everything, will be all set up for you just like they where on your original computer.




understanding dotfiles makes life a whole bunch easier for any Linux user.

the hardest part is finding which dotfile it is when it isn't named something obvious. example would be that pidgin's settings are saved in .purple and not .pidgin.

---

### Post by BobJam on 2009-09-23
[FONT=monospace]@[/FONT] earthpigg,

First, thanks VERY much for the explanation.  Was something that I had only a foggy notion of at best, and now I think I understand completely.

But let me test my understanding of your excellent detail (sorry for being so dense).

The answer then to my #2 question would be YES!

And as far as the follow-up question goes, a restore of a home directory (with all the dot files of course) would be sufficient to restore the desktop to the way it was with the existing /.  No need for a fresh install of /.

(BTW, I have my / and my /home directories on different partitions.)

Do I have it right?

Thanks again for the detail.

---

### Post by earthpigg on 2009-09-23
yes, if you completely mess up your desktop (as long as it wasn't by doing something involving you entering your password) you can restore it to the way it was by restoring your backed up dotfiles -- or the entire /home including all dotfiles, if you wish.


which question are you calling 'question #2'? you have many questions in many posts lol :D

and are you using 'fresh install of /' to mean a fresh install of ubuntu on a system with a seperate / and /home partition?

if you wish, and if you have a seperate /home partition, yes you can reinstall ubuntu, select the option not to format your /home partition, and set that partition to mount as /home on the new install, and your program settings will be retained. as always of course, you want to have solid backups whenever you do anything with partitions.

(changing things in /home will not install/remove any programs... but if the dotfiles are there, the program will see/use them once that program is installed.)

---

### Post by BobJam on 2009-09-23
> **earthpigg said:**
> yes, if you completely mess up your desktop (as long as it wasn't by doing something involving you entering your password) you can restore it to the way it was by restoring your backed up dotfiles -- or the entire /home including all dotfiles, if you wish.I take it though that restoring the desktop is not as straightforward as, say, restoring Pidgin where it is simply restoring one dot file.  The desktop config seems to have quite a few dot files associated with it (enumerated in earlier posts in this thread)


> **earthpigg said:**
> which question are you calling 'question #2'? you have many questions in many posts[INDENT]> **BobJam said:**
> 2.  Backing up and restoring my home directory will put my desktop back the way I had it.
[/INDENT]> **earthpigg said:**
> and are you using 'fresh install of /' to mean a fresh install of ubuntu on a system with a seperate / and /home partition?Yes

> **earthpigg said:**
> if you wish, and if you have a seperate /home partition, yes you can reinstall ubuntuBut do I absolutely have to do that if my existing / is not corrupted?  (I think you said that one time already . . . am going back over and reading this whole thread again, but I think I'm finally getting the big picture now . . . thanks for the patience with a noob).

I think I've beaten this topic to death . . . I just need to review this thread before I ask any more questions.

---

