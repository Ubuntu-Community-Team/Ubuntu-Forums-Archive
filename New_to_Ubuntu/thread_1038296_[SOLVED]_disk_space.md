---
title: "[SOLVED] disk space"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by mro_k on 2009-01-12
Hi!

I am a bit puzzled here. When I enter "df -h" I get the following output:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4             9.7G  8.7G  592M  94% /

I have a separate root partition ~10Gb. When I was installing Ubuntu I followed a guideline which said that 4Gb should be more than enough for a root partition so I made it 10Gb just to be sure. :)
Now it shows me 94% usage. How come? I really do not have so many applications installed besides the standard ones.
Anyhow, does it mean I cannot install any additional application or even create an image of a CD?
If I am wrong, please advise, how to check the actual usage?

---

### Post by The Cog on 2009-01-12
Try **sudo du -sh /*** to see where the biggest load is. Then work down the tree. You've got an unexpected 6-7 Gig somewhere.

---

### Post by stevoo on 2009-01-12
it shouldnt really take that much space .... a  fresh installation with current updates should take 2 -3 Gb only. 

So .... let see where everything is reciding 

open a shell and go to root
then run
{ ls -lS &#8211;block-size=1 | awk &#8216; {print $5,$6,$7,$8}&#8217;; du -s &#8211;block-size=1 */ ; } | sort -nhr | less
Post us the results ... we only want the sizes. We can then see what is going where :)

---

### Post by HotShotDJ on 2009-01-12
That is a bit high... on my system, my root partition shows 4.1G used, and I have all kinds of extra software installed that is not included in the default Ubuntu installation.  Here are some things to try...

From a terminal, run the following commands:```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```
apt-get clean removes everything except lock files from /var/cache/apt/archives

apt-get autoclean removes only package files that can no longer be downloaded

apt-get autoremove will install packages that were installed as dependencies of packages that have subsequently been removed.

See if these three commands free up the needed space, if not, there are some other things to look at.

---

### Post by stevoo on 2009-01-12
> **The Cog said:**
> Try **sudo du -sh /*** to see where the biggest load is. Then work down the tree. You've got an unexpected 6-7 Gig somewhere.

i was looking for that command everywhere :)

---

### Post by mro_k on 2009-01-12
Hej, you are really fast in responding. :)

The Cog, this is what I get when I use your command. (see below)
I don't understand why it shows my home partition under /home. When I use df -h it says: 
/dev/sda8              27G  6.5G   20G  26% /home
Is it somehow doubbled?


6.1M	/bin
59M	/boot
0	/cdrom
2.9M	/dev
15M	/etc
du: cannot access `/home/oleg/.gvfs': Permission denied
6.3G	/home
0	/initrd.img
0	/initrd.img.old
207M	/lib
16K	/lost+found
38G	/media
4.0K	/mnt
5.4G	/opt
du: cannot access `/proc/23508/task/23508/fd/4': No such file or directory
du: cannot access `/proc/23508/task/23508/fdinfo/4': No such file or directory
du: cannot access `/proc/23508/fd/4': No such file or directory
du: cannot access `/proc/23508/fdinfo/4': No such file or directory
0	/proc
8.5M	/root
8.4M	/sbin
200K	/srv
0	/sys
132K	/tmp
2.6G	/usr
536M	/var
0	/vmlinuz
0	/vmlinuz.old

---

### Post by Temposs on 2009-01-12
You've got something huge in your /opt. I have a pretty loaded system and my /opt only takes up 55MB, while yours is taking up 5.4GB. You should explore in there and see what's taking up so much space.

---

### Post by mro_k on 2009-01-12
> **Temposs said:**
> You've got something huge in your /opt. I have a pretty loaded system and my /opt only takes up 55MB, while yours is taking up 5.4GB. You should explore in there and see what's taking up so much space.

I am either confused or completelly dumb. Under /opt I have another /home directory. How did it get there? Is it safe to delete it?

---

### Post by WitchCraft on 2009-01-12
> **mro_k said:**
> I am either confused or completelly dumb. Under /opt I have another /home directory. How did it get there? Is it safe to delete it?

first look what's in it...

I have far more than 10 GB, I run Debian, though
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             116G   31G   80G  28% /


4.1M	/bin
36M	/boot
0	/cdrom
84K	/dev
23M	/etc
97M	/giss2007
182M	/home
0	/initrd.img
0	/initrd.img.old
175M	/lib
16K	/lost+found
32K	/media
4.0K	/mnt
641M	/opt
0	/proc
12K	/Recycled
19G	/root
4.4M	/sbin
4.0K	/selinux
4.0K	/srv
0	/sys
7.3M	/tmp
11G	/usr
366M	/var
0	/vmlinuz
0	/vmlinuz.old

```

---

### Post by mro_k on 2009-01-12
I go cd / and from there I type your command but what I get is:

[I]awk: ^ invalid char '&#65533;' in expression
du: cannot access `&#8211;block-size=1': No such file or directory[/I]

then I hit "Q" and get an additional error message:
[I]sort: invalid option -- 'h'
Try `sort --help' for more information.
ls: cannot access &#8211;block-size=1: No such file or directory
oleg@oleg-laptop:/$ [/I]

am I doing something wrong or is option "h" a misstype?

---

### Post by mro_k on 2009-01-12
I think I am getting closer. I've just checked the "/opt", it contains "/home" and "/etc" and bouth are quite large. My guess neither of them should be there. Still have no idea how they got there.
Since I've been going on your nerves for a while, could anybody confirm my guessing that home and etc do not belong there? They just got copied there at some point before. None of them has an actual "last modified" date and is safe to delete? :confused:

Sorry guys! I was too slowly with my typing, the question is already answered. :) Thanks for you patience!

---

### Post by forger on 2009-01-12
The root (/) without /home can be about 2-3GB for a fresh install, and about 8GB for an install with a looot of applications.

These commands show you your actual home and root partitions:
```

mount
df -h

```


Why are you still looking for explanations? No-one knows what you've been doing and which programs you are using, other than yourself (or the person who installed them)! :)

Explore the /opt folder:
```
gksu nautilus /opt
```

(/opt/home should not exist in a usual Ubuntu operating system)


Also, HotShotDJ recommended something you might have missed: [http://ubuntuforums.org/showthread.php?t=1038296#4](http://ubuntuforums.org/showthread.php?t=1038296#4)

---

### Post by forger on 2009-01-12
Read about /opt:
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/opt.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/opt.html)

> 
 This directory is reserved for all the software and add-on packages that are not part of the default installation. For example, StarOffice, Kylix, Netscape Communicator and WordPerfect packages are normally found here. To comply with the FSSTND, all third party applications should be installed in this directory. Any package to be installed here must locate its static files (ie. extra fonts, clipart, database files) must locate its static files in a separate **/opt/'package' or /opt/'provider'** directory tree (similar to the way in which Windows will install new software to its own directory tree C:\Windows\Progam Files\"Program Name"), where 'package' is a name that describes the software package and 'provider' is the provider's LANANA registered name.

Although most distributions neglect to create the directories **/opt/bin, /opt/doc, /opt/include, /opt/info, /opt/lib, and /opt/man** they are reserved for local system administrator use. Packages may provide "front-end" files intended to be placed in (by linking or copying) these reserved directories by the system administrator, but must function normally in the absence of these reserved directories. Programs to be invoked by users are located in the directory /opt/'package'/bin. If the package includes UNIX manual pages, they are located in /opt/'package'/man and the same substructure as /usr/share/man must be used. Package files that are variable must be installed in /var/opt. Host-specific configuration files are installed in /etc/opt. 

---

### Post by WitchCraft on 2009-01-12
home and etc definitely don't belong in /opt.

My guess is you either moved or copied it accidentially.

If you copied it, delete it, if you moved it partially, merge it back.

Caution if you have another partition mounted to /opt/home/something ...

---

