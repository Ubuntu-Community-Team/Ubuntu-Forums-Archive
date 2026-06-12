---
title: "Not enough space to upgrade to 10.04: why is 9.10's / partition so full?!"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by kingbco on 2010-05-07
Hi folks,

I'm hoping that someone can make some suggestions here. I'm presently running 9.10, upgraded from the original 9.04. I want to upgrade to 10.04. However, when I run the update from within the Update Manager, I get the error message:

"[FONT=Arial]Not enough free disk space

The upgrade is now aborted. The upgrade needs a total of 4,012M free space on disk '/'. Please free at least an additional 2,765M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.[/FONT]"

[FONT=Verdana]A quick typing in of:

prompt:~$ df -H

yields:

Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda5               11G   8.7G   1.4G  87% /
udev                   1.1G   398k   1.1G   1% /dev
none                   1.1G   189k   1.1G   1% /dev/shm
none                   1.1G   209k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda4              1.1G   9.6M   1.1G   1% /media
/dev/sda1               35G    17G    18G  49% /media/C
/dev/sda2               39G   5.5G    34G  14% /media/E
/dev/sda7               72G   5.9G    63G   9% /home
/dev/sdb1              250G   153G    98G  61% /media/WD Passport

Okay, great! sda5 is 87% free and only has 1.4G available, which is less than the required 4ish GB.

THE QUESTION IS: why is my 11G partition 87% full?!!!!
I've removed all older versions of the linux kernel, but that only freed a few hundred MB of space. I've also run "sudo apt-get clean."

I've looked at other similar threads. However, they seem focussed on people whose partitions are far too small for Ubuntu, and on repartitioning or creating a symlink to a larger partition for the install files.

But I'm wondering if there's something I can do to pare down that 8.7G and then just do a straight install. Do I have too many applications installed?

I'd appreciate any insight or suggestions.

Cheers,

Brian
[/FONT]

---

### Post by narendraD on 2010-05-07
Have you tried clearing your /var/cashe/apt/archive. That where all the dowloaded packages are stored. Having said that i do not know whether sudo apt-get clean also does the same. Also no matter how many apps you have installed 8.7GB is a lot of space.

---

### Post by mikewhatever on 2010-05-07
The output of **sudo du -sh /*** should give you an idea what's taking the space.

---

### Post by kingbco on 2010-05-07
oops, sorry - dinner break and call to g/f. Plus implementing your suggestions has taken a little time...
...
[FONT=Arial]ls /var/cache/apt/archive[/FONT] shows "lock" and an empty directory "partial."
So it looks like there's not much there - perhaps I'd cleared it as you suggested...
...
the du command gives the following (not sure if the warnings are typical!):

[FONT=Arial]6.7M    /bin
106M    /boot
0    /cdrom
784K    /dev
18M    /etc
du: cannot access `/home/kingb/.gvfs': Permission denied
5.4G    /home
0    /initrd.img
0    /initrd.img.old
707M    /lib
16K    /lost+found
163G    /media
4.0K    /mnt
181M    /opt
du: cannot access `/proc/4606/task/4606/fd/4': No such file or directory
du: cannot access `/proc/4606/task/4606/fdinfo/4': No such file or directory
du: cannot access `/proc/4606/fd/4': No such file or directory
du: cannot access `/proc/4606/fdinfo/4': No such file or directory
0    /proc
65M    /root
8.1M    /sbin
4.0K    /selinux
200K    /srv
0    /sys
31M    /tmp
6.6G    /usr
397M    /var
0    /vmlinuz
0    /vmlinuz.old[/FONT]

Looks like /usr is the offending culprit...

Okay, jumping ahead a little bit. The du command's a bit slow, so I've jumped over to Nautilus...

Within /usr, the two big offenders are lib (2.8 GB) and share (2.5 GB). lib64's not very full at all.

So would that imply that I do, indeed, have too many programs/applications installed? I do have KDE in there (for Amarok!). And I've installed a number of Science/Math packages (Sage, Labplot, Quics, Maxima, Scilab, QtOctave, extrema) as well as gimp, scribus, inkscape, krita, etc...

Thanks,

Brian

---

### Post by narendraD on 2010-05-07
Though it may not sound like the best advice, would suggest backup your data and settings and do a fresh install after thinking over a good partitioning scheme that would not present a similar situation in future. Of course it will be a pain to reinstall all those apps again. Systems will work ok till they have about 10% free space, but trouble happens when you have to do an upgrade or similar that will download a lot more data to the same partition and you run out os space.

---

### Post by lsmobrian on 2010-05-07
Have you looked at the janitor program, that might cleanup a few things

Also, you could sym link /var/cache/apt folder to one of your other drives that has more space, do the upgrade then remove the sym link

---

### Post by kingbco on 2010-05-07
Well, I've already done some work to prepare for that eventuality (dpkg actually seems to give *too much* information i.e. *all packages* rather than just "user apps," but I've kluuged a list together).

Out of curiosity, though - do you think that the issue is too many installed applications? An earlier poster suggested that was unlikely. On the other hand, /usr/share and /usr/lib seem to be the offending places...

bk

---

### Post by kingbco on 2010-05-07
... oops, sorry: FYI, Ubuntu Software Center shows 179 installed items.

---

### Post by mikewhatever on 2010-05-08
> **kingbco said:**
> ...

Out of curiosity, though - do you think that the issue is too many installed applications? An earlier poster suggested that was unlikely. On the other hand, /usr/share and /usr/lib seem to be the offending places...

bk

I think that's the case. Below is the output of *sudo du -hs /usr/** on my system.
```
146M	/usr/bin
3.5M	/usr/Brother
2.6M	/usr/games
7.7M	/usr/include
802M	/usr/lib
92K	/usr/lib64
320K	/usr/local
20M	/usr/sbin
840M	/usr/share
160M	/usr/src
208K	/usr/X11R6

```

---

### Post by lavinog on 2010-05-08
Open up synaptic, show only installed packages, then sort by size (there is a bug that might prevent the size column from being displayed until you disable it and reenable it)

If a package doesn't have the ubuntu icon next to it, you might want to uninstall it.

One application that is handy to have is bleachbit.

Also check your /usr/src size.  If you installed a custom kernel, it can be huge.

---

### Post by kingbco on 2010-05-08
Thanks, folks.


[LIST=1]
[*]@mikewhatever: Thank you for the information. The contrast with your system is significant.
[*]@lavinog: Thank you for the suggestions.
In Synaptic, there aren't any obviously unreasonable packages. Well, libqt4db (which I believe I only have because I installed the nightly build of Amarok, and which keeps on failing to update...) is 400 MB, and Lilypond (which I don't really need...) is 250 MB. Then Sage (which I need) at 200 MB or so. Strangely enough, I also have a bunch of old linux images. I *thought* I removed old kernals manually last night (following some command lines from the Net, and before I posted here...).* **I'd guess I can remove those images???***

I installed bleachbit, thank you. It freed a few hundred MB.

I also looked into Computer Janitor - but here the buzz seems to be that you need to manually check that it doesn't remove stuff you need and - while I can guess on apps - I'm not confident about KDE, etc. packages it might uninstall because I don't automatically know the dependencies...

I didn't install a custom kernel - and, indeed, /usr/src is 51 MB.
[/LIST]
So I guess one thing I'd like to know is if it's safe to remove those old linux images (obviously up to but NOT including the most recent!).

BK

---

### Post by davarino on 2010-05-08
> **kingbco said:**
> 

Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda5               11G   8.7G   1.4G  87% /
udev                   1.1G   398k   1.1G   1% /dev
none                   1.1G   189k   1.1G   1% /dev/shm
none                   1.1G   209k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda4              1.1G   9.6M   1.1G   1% /media
/dev/sda1               35G    17G    18G  49% /media/C
/dev/sda2               39G   5.5G    34G  14% /media/E
/dev/sda7               72G   5.9G    63G   9% /home
/dev/sdb1              250G   153G    98G  61% /media/WD Passport

Okay, great! sda5 is 87% free and only has 1.4G available, which is less than the required 4ish GB.

THE QUESTION IS: why is my 11G partition 87% full?!!!!
I've removed all older versions of the linux kernel, but that only freed a few hundred MB of space. I've also run "sudo apt-get clean."



At the risk of looking as though I don't understand your predicament, I would advise you to "ls" through your /dev/sda5 and find out what is on it. (Often, users can find that stuff that they want to go to other partitions can actually go to the root partition if they have not configured everything properly.)

If you'd like a nice map of sda5, you might want to use Baobab on it. I suspect you have things (media files, for instance) that should be moved to other partitions.

I would definitely NOT muck around with removing configuration or other files until I was sure that all the non-OS-essential stuff was removed from my root directory.

Good luck.

---

### Post by kingbco on 2010-05-08
@daverino: Actually, all my media files are always on an external hard drive. The "bulk" of the material on sda5 is in /usr/lib and /usr/share. There's 2000 objects in /usr/lib (most of which should be system-related), so I'm pessimistic about my ability to spot cruft there.

/usr/share seems to be mostly applications-oriented. And, indeed, there are a number of 100s of MB applications there and numerous 10s of MB there.

All my user stuff is in /home on sda7.

But thanks, anyway...

bk

---

### Post by MrWES on 2010-05-08
> **narendraD said:**
> Though it may not sound like the best advice, would suggest backup your data and settings and do a fresh install after thinking over a good partitioning scheme that would not present a similar situation in future. Of course it will be a pain to reinstall all those apps again. Systems will work ok till they have about 10% free space, but trouble happens when you have to do an upgrade or similar that will download a lot more data to the same partition and you run out os space.


Prior to a fresh install I always run this, to get a list of my installed packages dumped into a text file. That can be used to reselect the packages for install after the fresh install.

Installed Packages

sudo dpkg --get-selections > installed.software

to restore

dpkg --set-selections < installed.software

dselect

Bill

---

### Post by davarino on 2010-05-08
> **kingbco said:**
> @daverino: Actually, all my media files are always on an external hard drive. The "bulk" of the material on sda5 is in /usr/lib and /usr/share. There's 2000 objects in /usr/lib (most of which should be system-related), so I'm pessimistic about my ability to spot cruft there.

/usr/share seems to be mostly applications-oriented. And, indeed, there are a number of 100s of MB applications there and numerous 10s of MB there.

All my user stuff is in /home on sda7.

But thanks, anyway...

bk

Yes, that was why I was afraid that I'd be looking foolish with the recommendation.

Looking back at your questions, I am struck by your thought that you may have "too many" applications installed.

Looking at my own system, I see a good 8.5 GB tied up in /usr/lib and /usr/share. :eek: I *do* have a great deal of space on my root partition, though.

So, yes, you *may* have an excessive amount of applications installed for the amount of storage you have available.

How to get around it?

I would not expect you to change how much software you keep on your machine, though discarding unused software and config files would definitely help your disk "real estate" problem. (Habits are hard to break and they are usually in place for valid reasons, even if only for personal comfort.)

First of all, I would get rid of any old Ubuntu disk images (the .iso files). I see no need for them. If that solves things, you're in free. (I would doubt that you have enough disk images to make a difference, though.)

But I would not tweak things further down, that's for sure. All that will do is mask and postpone intrinsic problems, not solve them. Six months from now you could just have an overloaded system with no simple remedy.

If any further work were needed, I would do as narendraD [suggested]("http://ubuntuforums.org/showpost.php?p=9259041&postcount=5"): back up things and do a fresh install over the old installation, fixing partition size, etc.

I would also consider a new and larger hard drive for root and home (or an additional drive), if my wallet were big enough.

Again, good luck!

---

### Post by kingbco on 2010-05-08
Thanks.

One of the things I'm still curious about is receiving concrete confirmation that a very large /usr/share is a fairly definitive indication that I have too many applications installed. Or that the 179 applications from the Software Center is an indication of the same. I've definitely installed some software (alluded to before), but I also removed a bunch of applications from the base install (I'm pretty sure no one in my house needs the Swahili language package - mainly because I live alone!!)

BTW, a straight dpkg --get-selections gives me 2374 items. Of course, from *that* it's hard to figure out which packages are "user applications" and which are sort of "background process" types of things (i.e. not directly used by the user) and which are "dependent process" types of things (things upon which "user applications" depend).

But thanks for the output-redirect hint. I'd seen it somewhere before and am glad to have been reminded of it. It could definitely come in handy!

I guess one of the things that's a little unclear to me is how to figure out what are NECESSARY packages. Software Center gives me a list of what I called "user applications" before: in "more-readable" format (e.g. Adobe Reader 9 vs. acroread, but I whine...). dpkg, Synaptic, Janitor, etc. give a list of ALL installed packages. But with 2374 packages installed, it would be laborious to determine which are "my programs," which are "necessary system programs," and which are cruft. Janitor gives me a list of "unused" packages: but (a) I'm unsure of what "unused" packages might be features of an installed application that I just haven't used in a while (e.g. I haven't run the "Help" in a while) and (b) I've read that Janitor has a tendency to remove ALL non-official applications (though after cleaning up a bit, it doesn't seem to list Sage or Amarok (2.3.0) - neither of which are in the official repositories...).

I'm wondering if there's "cruft" around that I should clean up. If so, I'd prefer to trim my system before upgrading, and keep it trimmed.

If not, then it definitely seems I'd be more comfortable with a larger / partition, as I seem to suck up a lot of room for my own personal version of a "bare minimum" install (i.e. what I need to function day-to-day).

Again, thanks.

bk

---

### Post by kingbco on 2010-05-08
@daverino: our ships "passed in the night." Your points are good to bear in mind. Actually, I've got *tons* of space free in my /home partition. I just don't seem to be able to generate a lot of data. So if I can't identify any "garbage" in / then I think you're absolutely correct: I should admit that I need and will continue to need a bulky installation, and just repartition. No sweat. (Okay, sweat, but not the end of the world!)

So the only remaining issue is to find garbage. But having now removed a few superfluous packages (libqt4 debug) and a couple of installations (lilypond), and cleared caches, and even now run Janitor, it's starting to look like there's not a lot of garbage left...

Everyone's advice has been helpful in helping me narrow down the challenge, and also in figuring out what the problem *isn't*.

I'll hang on a bit longer and see if anyone can come up with something that hasn't been raised, yet...

bk

---

### Post by lavinog on 2010-05-08
You mentioned you had kde libraries installed...those can take up a substantial amount of space.
If you insist on doing an upgrade instead of a fresh install: You can boot with a live cd, start the partition editor, shrink your home partition, and grow your root partition some.

---

### Post by narendraD on 2010-05-10
> **kingbco said:**
> @daverino: our ships "passed in the night." Your points are good to bear in mind. Actually, I've got *tons* of space free in my /home partition. I just don't seem to be able to generate a lot of data. So if I can't identify any "garbage" in / then I think you're absolutely correct: I should admit that I need and will continue to need a bulky installation, and just repartition. No sweat. (Okay, sweat, but not the end of the world!)

So the only remaining issue is to find garbage. But having now removed a few superfluous packages (libqt4 debug) and a couple of installations (lilypond), and cleared caches, and even now run Janitor, it's starting to look like there's not a lot of garbage left...

Everyone's advice has been helpful in helping me narrow down the challenge, and also in figuring out what the problem *isn't*.

I'll hang on a bit longer and see if anyone can come up with something that hasn't been raised, yet...

bk


I had advised you in my first reply to consider a fresh install. I still think that it is still the best thing that you should do. While no one here can see or decide what apps you keep or remove, we can only suggest what we feel are obvious culprits. 

You may look at Synaptic and see if any packages appear as Installed (Residual Config). These are packages that were dependencies, but are orphans now because you uninstalled the parent app. You can safely remove those. So also with Janitor. But Janitor marks packages that are currently not in repos as removable, so be carefull there. 

Also having more than one DE and too many programs is only going to complicate the upgrade if you decide to and leave a few packages or funtionality broken. As someone before suggested, the way i do is to make a list of all apps on my system right down to firefox extensions, copy the settings files from the home directory and do a fresh install. Of course i also do not normally keep more than one app for most purposes and where i do i normally chose apps that are small in size with just the right funtionality that i require.

While this exercise of finding out where your Harddisk real estate got consumed may be a good one for the learnings and revelations that it will give, an upgrade might leave a very bad taste.

Best wishes and keep us posted on what you decide.

---

### Post by kingbco on 2010-05-10
Thank you, [narendraD]("http://ubuntuforums.org/member.php?u=876881").
It sounds like this is definitely the way to go. A bit frustrating, but not the end of the world. I appreciate your hints on looking for "lost" apps (i.e. orphaned dependencies). This seems like a valuable exercise. It's funny - I seem to be the opposite from a lot of users, perhaps? Not much user-data, but lots of apps! To be true, I'm still evaluating a number of open-source alternatives (e.g. Sage vs. Maxima vs. Axiom vs...., or various attempts a GUI-based scientific data-plotting packages), but that will be a lengthy process, and so many-apps will probably be my status for some while...

So now it's a matter of waiting to upgrade until I have a solid chunk of time. I know that many people have issues eventually with upgrading (or have in the past). I'd been lucky so far...

As to your package suggestions, that would be a whopping 8 MB! Not too much to gain there (translation package, plus it lists Skype as "local or obsolete").

I'm certainly curious about the disk usage - both from a personal viewpoint and because of some "olden days, hardware-limite" obsession about not using up unnecessary space. So I'll probably continue to while away at my installed apps to "optimize" my system for me - mostly for aesthetic purposes. But it looks like your advice (echoed by others) is the advice to take. So: eventual re-install... (CD's - those are the flat, round, shiny USB keys, right? ;) )

bk

---

### Post by lavinog on 2010-05-10
> **kingbco said:**
> 
So now it's a matter of waiting to upgrade until I have a solid chunk of time. I know that many people have issues eventually with upgrading (or have in the past). I'd been lucky so far...


There is nothing wrong with waiting to upgrade/install the latest version.  I have had more issues with upgrading immediately after a release, while upgrading a couple of weeks later tends to be a smoother transition.

---

### Post by kingbco on 2010-05-10
Thanks, lavanog - you're correct, I'm certain. It's just that I'm like that toddler on Christmas morning. And I *already* was a good boy by waiting a week(ish)! ;)

Oh well, "patience is a virtue..." (except if you were on the Titanic...)

bk

---

