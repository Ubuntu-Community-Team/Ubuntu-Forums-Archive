---
title: "how to update MPlayer version?"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by nachos99 on 2009-03-05
ive been trying to update my oudated mplayer v1.0rc2.  

i was following instructions below from this site ([http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)) with the hope that the "svn update" would update the MPlayer.
----------------------------------------
"Downloading MPlayer from Subversion

You can also get MPlayer via Subversion. Issue the following command to get the latest sources:

  svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer

A directory named mplayer will be created in the current directory. You can later update your sources by typing

  svn update

from within that directory. "
----------------------------
as far as i can tell, the first part just reinstalled the old version 1.0rc2.  
desktop:~$ mplayer
MPlayer 1.0rc2-4.2.4 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.06GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Usage:   mplayer [options] [url|path/]filename

im unable to do the second part,since im not sure in which directory i should be running "svn update".

:~$ whereis mplayer
mplayer: /usr/bin/mplayer /etc/mplayer /usr/share/mplayer /usr/share/man/man1/mplayer.1.gz

:~$ whereis svn
svn: /usr/bin/svn /usr/share/man/man1/svn.1.gz

second, ive tried for example,

desktop:/usr/share/man/man1$ svn update
Skipped '.'

ive tried putting in "svn update" in the other directories above with the same result - Skipped '.'.  I'm not sure what that means, but im guessing it didnt update.  


so to recap, 

1. where do i run this command to update my MPlayer?

2. is there another (easier) way of updating my MPlayer?



thanks much in advance for any help.

---

### Post by wolfen69 on 2009-03-05
do
```
gksudo gedit /etc/apt/sources.list
```
and uncomment (remove the #) from the lines that have "backports" in them. save file and close. then
```
sudo apt-get update
```
then
```
sudo apt-get install mplayer
```

after you install mplayer, go back to the sources list and put the #'s back in front of the backports lines.

then
```
sudo apt-get update
```

---

### Post by andrew.46 on 2009-03-05
Hi,

Installing the svn MPlayer is not something to be lightly undertaken but there is a guide on these forums to assist you to do just that:

[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)

Andrew

---

### Post by nachos99 on 2009-03-05
thanks everyone for the suggestions.

my need to update the MPlayer began after i updated my SMPlayer to v0.6.6 which didnt appear to work too great with my outdated v1.0rc2.  (related thread: [http://ubuntuforums.org/showthread.php?p=6846271#post6846271](http://ubuntuforums.org/showthread.php?p=6846271#post6846271))

since my need for a newer MPlayer was tied to it working well with SMPlayer, this seemed like a solution - [https://launchpad.net/~rvm/+archive/ppa/](https://launchpad.net/~rvm/+archive/ppa/) . i added ppa repository(deb [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) hardy main) through the synaptic package manager and ran the following terminal commands, per rvm4000's post. 

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A58BCAE3
sudo apt-get update
sudo apt-get install mplayer smplayer

my MPlayer has now been updated to
MPlayer SVN-r28403-4.2.4 (C) 2000-2009 MPlayer Team

and the SMPlayer v0.6.6 appears to be running smoothly after a quick check.

problem solved.  thanks again to everyone for the suggestions.

---

