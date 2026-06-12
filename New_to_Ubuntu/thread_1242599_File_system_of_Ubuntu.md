---
title: "File system of Ubuntu?"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by gasmansteve on 2009-08-17
Hi folks
Love my new installation of 9.04 Ubuntu but struggling to understand its (and probably any Linux distro) directories and way of allocating file storage. I installed Ubuntu onto my trusty old desktop with 1/2 gig of ram,80 gig drive and dual installation with XP. 40Ggig was allocated to XP some time ago leaving me with 40gig available for Ubuntu. Reading various forums I understand I need a root directory (/) I was told by someone to allocate double ram size for this ie for me 1gig??, swap (/swap) directory again told double ram and so on. Where does Ubuntu install applications root,/home,/etc??? and what is /swap for?.If I was to start with a blank drive say 80gig what would be the best size for each of the various directories?  Also not sure what /etc is for. Guess I need a tutorial somewhere:).
If I was to update Ubutnu in the future which directories can I save untouched or does an update have to over write certain directories? so many questions so little time :):)
Regards
Steve

---

### Post by super kim on 2009-08-17
hi Steve,

sorry to disappoint you but its not all that complicated. when you do an install the partition manager will allocate the correct size for your swap. [http://ubuntuforums.org/showthread.php?t=1238273](http://ubuntuforums.org/showthread.php?t=1238273)
and with regards to understanding what the different folders are you really don't need to know what they are for, just that the home folder has a folder that has your personal files in there. the other stuff is for the system and usually you would need to be sudo'd to edit them anyway. if you use the synaptic package manager to install programs then the files are put in their correct places and the launchers are added to your menu's automatically :)
i am no expert in any way but i am pretty good at naffing it all up but i do try hard. ubuntu is hard to break and nearly impossoble to completely trash (accidentally of course)

ubuntu is linux for humans.

---

### Post by mapes12 on 2009-08-17
Hi Steve

Not part of the main site anymore but still a great guide: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

If you think of it this way:

"/" is where Windose would have all its OS files
/home is equivalent to My Documents
SWAP - Is just a piece of disc space used for extra memory on Unix based machines.

Sizes:

Aprrox 6GB should be comfortable for "/" and have this as your first partition.

Then have /home partition next with what you have left (minus SWAP)

SWAP is usually 2x RAM but I have read 1x is comfortable on machines with lots of memory.

Mark

---

### Post by mcduck on 2009-08-17
Applications are installed all around the file system, each file is put to different place depending the purpose of the file. For example the executable files for all user-level applications will go to /usr/bin, documentation goes to /usr/share/doc, icons and other pixmaps to /usr/share/pixmaps and (usr/share/icons and so on.

However this is usually irrelevant from user's point of view, as everyhting is handles automatically by the package management tools.

/swap is pretty much the same as swap space in Windows is, it's used when your applications need more memory than you have actual physical RAM installed. Linux usually puts swap in it's own partition for slighly better performance, and to keep the rest of the file system cleaner. Many Linux installs on the same computer can also share the swap partition. Swap is also used when you suspend the machine, all daa from RAm is written into swap and the computer is shut down, and when you start it again the data is returned from swap to RAM and you can continue from where you left.

If you update Ubuntu all data is reserved. However if you plan on making a fresh install of the new released version instead of upgrading the old one you might want  to make a separate /home partition. This will allow you too keep all user files and settings.

---

### Post by 3rdalbum on 2009-08-17
Your root (/) directory contains everything that is not handled by any other partition. You want to make this big, as it will contain your applications and operating system.

For swap, if you don't have a lot of RAM you will want double. If you have a lot of RAM (like, two gigs or more) then you want just a little more swap than you have RAM (maybe 100 megs more); this way you can hibernate. If you are not going to use your computer's hibernation feature, and you have lots of RAM, then you can get by with no swap.

/home contains the home directories of all your users. This should be big too, bigger than /, because it contains all your user data.

You actually don't need to put /home on a different partition. It helps if you are going to switch to another distribution, but even a fresh install of Ubuntu will preserve the contents of /home. You can run Ubuntu with one partition: /  - in fact, I used to run Ubuntu this way and my father still does.

In your situation I'd say allocate all for / except what you want to use as swap. Remember, when you don't have a seperate /home, then /home is just part of /

If you want to have a seperate /home, then have 20 gigabytes of /, follow my earlier suggestion for swap, and put the rest into /home.

If you've got only the 40 gigabytes available, then put 13 gigabytes into /  - I am using just under twelve gigabytes in /

---

### Post by Malta paul on 2009-08-17
Hi and welcome,

There are two ways to upgrade, when an upgrade comes out (9-10 in October)
you will get a reminder if you wish to update, with this option you should not loose any files (But make a backup of your data just in case!)

The second way is a clean installation by downloading the upgrade and burning to a CD disk as an ISO file to enable the CD to boot.
This method you will lose your /home files, again backup!

You might like to look at this link:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)  

Have fun the Community is here to help you :p

---

### Post by gasmansteve on 2009-08-17
Wow thanks everyone for the speedy replies. Everything much clearer now.
Feel like wiping XP off altogether now :)
Cheers
Steve

---

### Post by Sidewinder1 on 2009-08-17
I know that my Ubuntuian bretheren are going to throw rotten tomatoes at me for saying this, but here goes: don't wipe Winbloze just yet. You may find a program or two, that you currently use in winbloze that maybe somewhat difficult to find an ubuntu equivalent. It's there, but you may not have it yet. Once you are completely sure,....then and only then,...format away!!! :-)
HTH,
Side

---

### Post by Paddy Landau on 2009-08-17
> **gasmansteve said:**
> Feel like wiping XP off altogether now
I agree with Side. Don't wipe XP until you are absolutely sure that you no longer need it.

It took me a little over a year to entirely lose my dependence on it.

Also, putting [COLOR=DarkRed]/home[/COLOR] onto a different partition is one of those things that in hindsight would have been a good idea. It's not terribly hard to change your mind later, but it's easier to set it up at the start.

I have a fairly standard installation of Ubuntu with a few extra programs, and I've used only 4.3Gb in my root (i.e. [COLOR=DarkRed]/[/COLOR]) partition, so that gives you an idea.

---

### Post by super kim on 2009-08-19
> **Sidewinder1 said:**
> I know that my Ubuntuian bretheren are going to throw rotten tomatoes at me for saying this, but here goes: don't wipe Winbloze just yet. You may find a program or two, that you currently use in winbloze that maybe somewhat difficult to find an ubuntu equivalent. It's there, but you may not have it yet. Once you are completely sure,....then and only then,...format away!!! :-)
HTH,
Side
:lolflag:boo, (tomatoes being thrown):lolflag:
true though. i sometimes miss the unexplained windows system crashes that you have to look hard for to find with ubuntu. i took me ages to find the right combination of messing about to get a crash, and even that crash was disappointing. it fixed itself after a reboot, and sent an error report to hopefully stop it happening again one day!

---

### Post by Penguin Guy on 2009-08-19
_**Short Explanation of Folder Names:**_
[COLOR="Green"]root/[/COLOR] Root's home directory, root is equivalent to Administrator in Windows.
[COLOR="Green"]usr/[/COLOR] Shared system files.
[COLOR="Green"]etc/[/COLOR] Important shared system files.
[COLOR="Green"]bin/[/COLOR] (stands for binaries) Programs.
[COLOR="Green"]home/[/COLOR] Users home directories.
[COLOR="Green"]boot/[/COLOR] Files required to boot the computer.
[COLOR="Green"]proc/[/COLOR] System information like current CPU temperature.
[COLOR="Green"]mnt/[/COLOR] For mounting devices such as internal HDDs.
[COLOR="Green"]media/[/COLOR] For mounting devices such as USBs.
[COLOR="Green"]tmp/[/COLOR] For temporay files that will be deleted on shutdown.
[COLOR="Green"]var/[/COLOR] Files such as emails, game highscores, backups, etc.
[COLOR="Green"]sys/[/COLOR] System information like number of CPUs.
[COLOR="Green"]lib/[/COLOR] Libraries.
[COLOR="Green"]lost+found/[/COLOR] If your computer crashes it is possible that some files get lost, if so, they go here.

[COLOR="Green"]usr/local/[/COLOR] Programs that the admin has installed by hand
[COLOR="Green"]var/tmp/[/COLOR] For temporary files that will not be deleted on shutdown

_**Short Explanation of Linux File Structure:**_
[SIZE="3"][COLOR="Green"]/[/COLOR][/SIZE] At the start of a path means the root of the filesystem, it is equivelant to [COLOR="Green"]C:\[/COLOR] in Windows.
[SIZE="3"][COLOR="Green"]~[/COLOR][/SIZE] At the start of a path means your home directory, therefore [COLOR="Green"]~/.mozilla[/COLOR] = [COLOR="Green"]/home/<username>/.mozilla[/COLOR].
[SIZE="3"][COLOR="Green"]~[/COLOR][/SIZE] At the *end* of an item means backup (e.g. [COLOR="Green"]important-file.txt~[/COLOR]), these files are usually hidden, you can toggle this by pressing [COLOR="Green"]Ctrl + H[/COLOR] in Nautilus.
[SIZE="3"][COLOR="Green"].[/COLOR][/SIZE] At the start of an item means hidden file (e.g. [COLOR="Green"].secret-file.txt[/COLOR]), these files are usually hidden, you can toggle this by pressing [COLOR="Green"]Ctrl + H[/COLOR] in Nautilus.
[SIZE="3"][COLOR="Green"]..[/COLOR][/SIZE] The directory above, for example if you are at [COLOR="Green"]/root/Desktop[/COLOR] and type [COLOR="Green"]cd ..[/COLOR] you will then be at [COLOR="Green"]/root[/COLOR].

---

