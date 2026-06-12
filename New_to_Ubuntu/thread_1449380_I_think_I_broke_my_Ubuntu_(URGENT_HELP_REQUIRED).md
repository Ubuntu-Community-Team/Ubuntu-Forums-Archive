---
title: "I think I broke my Ubuntu (URGENT HELP REQUIRED)"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by craigd741 on 2010-04-07
OK, so I've searched high and low for a solution to my problems (I have a lot of them) but I can't seem to find an answer. I am completely new to Ubuntu (I've had it three days now. Windows failed me majorly) so explain things in lehmans terms please.
Well, the first day everything was fine. I had a look around the software center, installed a few games and a media player without any hassle whatsoever. Then all my problems started when I was trying to get DVD playback to work. I tried using the terminal for the first time. I typed in these command that I found on a website:

"sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3

sudo /usr/share/doc/libdvdread3/install-css.sh"

but it gets as far as "reading package lists" and then tells me that 

"the package lists or status file could not be parsed or opened."

I have no idea what this means. In fact, I don't even know what a package list is. Is there something I haven't installed or something? I won't lie. I typed a lot of codes into that terminal and none of them worked so I figure there must be some common problem.
My other problems are:
- the software center refuses to load. It says there are 2,000+ applications available but when I click on something, e.g. Games, it tells me that there are 0 applications available.
- Ubuntu will not update. I'm running version 9.10 and when I try to update I get as far as "reading package lists" and then I get a big fail sign and another message that reads:

"An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Read error - read (5: Input/output error), E:The package lists or status file could not be parsed or opened.'

I would really appreciate any help as I have to use Ubuntu (my activation key for Windows XP has been used too many times, apparently) and I really like the things that ARE working. Would I be better off just installing it again and starting from scratch (I may have buggered it up using the terminal somehow) or am I doing something completely wrong? PLEASE HELP!

---

### Post by Directive 4 on 2010-04-07
[http://www.medibuntu.org/](http://www.medibuntu.org/)


this place has a guide which will get everything running

---

### Post by Rasa1111 on 2010-04-07
if youve only had it for 3 days,
 i would just reinstall it myself. 
 it doesnt take that long. 

and after you reinstall it, if you do...

 do your updates first before anything, 
 then open software center again, and get VLC player and also Ubuntu restricted Extras. 

 then try your dvd again. 

 and dont be sticking commands in if you dont know what they are,
 to be honest.. you really shouldnt even need the terminal to get everything setup and running perfectly.

 i am a newb also..
only had ubuntu about 3-ish months,
and i swear.. I didnt use the terminal for the first month, 
and i had everything set up how i wanted it. 

dont mess with that until you understand it more. 

 download the ebooks, Ubuntu Kung Fu,
Ubuntu PocketGuide, 
and Ubuntu hacks/tips~

 they will help allot

---

### Post by 3rdalbum on 2010-04-07
The list of available packages is corrupted, possibly sitting on a bad block of your hard disk. all yourr error messages are related. Try running:

sudo apt-get update

Otherwise a reinstall might be the only way to solve this freak problem. It almost certainly won't happen again unless your disk is dying.

---

### Post by craigd741 on 2010-04-07
Thanks for the help. I tried this and got to the "adding the repository" stage. I run the command in the terminal and I got this:

E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

The same message I always get when trying to do anything with the terminal.

---

### Post by wojox on 2010-04-07
Post back what it says when you run:

```
sudo apt-get check
```

---

### Post by craigd741 on 2010-04-07
Thanks people. I'll reinstall, do the updates immediately, download the software I need and keep my hands far away from the terminal. Cheers everyone! You saved me from further frustration and confusion. 

Just one question more question... is reinstalling as simple as popping the disk back in and pressing F11?

---

### Post by wojox on 2010-04-07
So did my command render anything? 

Half the fun of Linux is breaking it and learning to put it back together. 

If you want to just reinstall, yeah pop in the CD and press F11 if that's the command to boot from CD-Drive first. You'll lose everything so anything you installed as far as documents and what not you'll need to back up. :)

---

### Post by craigd741 on 2010-04-07
> **wojox said:**
> Post back what it says when you run:

```
sudo apt-get check
```

I got as far as "reading package lists 53%" and then the same old fail message

---

### Post by wojox on 2010-04-07
Okay one more thing:

```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
```

```
gksudo gedit /etc/apt/sources.list
```

Then add this, save and run an update:

```

deb http://ftp.usf.edu/pub/ubuntu/ karmic main restricted
deb-src http://ftp.usf.edu/pub/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.usf.edu/pub/ubuntu/ karmic-updates main restricted
deb-src http://ftp.usf.edu/pub/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.usf.edu/pub/ubuntu/ karmic universe
deb-src http://ftp.usf.edu/pub/ubuntu/ karmic universe
deb http://ftp.usf.edu/pub/ubuntu/ karmic-updates universe
deb-src http://ftp.usf.edu/pub/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.usf.edu/pub/ubuntu/ karmic multiverse
deb-src http://ftp.usf.edu/pub/ubuntu/ karmic multiverse
deb http://ftp.usf.edu/pub/ubuntu/ karmic-updates multiverse
deb-src http://ftp.usf.edu/pub/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://ftp.usf.edu/pub/ubuntu/ karmic-security main restricted
deb-src http://ftp.usf.edu/pub/ubuntu/ karmic-security main restricted
deb http://ftp.usf.edu/pub/ubuntu/ karmic-security universe
deb-src http://ftp.usf.edu/pub/ubuntu/ karmic-security universe
deb http://ftp.usf.edu/pub/ubuntu/ karmic-security multiverse
deb-src http://ftp.usf.edu/pub/ubuntu/ karmic-security multiverse

```

---

### Post by craigd741 on 2010-04-07
Wojox, I tried this but as I ran the Update I got a message saying:

"An unresolvable problem occurred while initializing package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

E:Read error - read (5: Input/output error), E:The package lists or status file could not be parsed or opened"

---

### Post by sandyd on 2010-04-07
try this.
```

sudo rm /var/cache/apt/pkgcache.bin
sudo rm /var/cache/apt/srcpkgcache.bin

```
that should clear the apt pkgcache

if it still doesnt work, try
```

sudo touch /var/cache/apt/pkgcache.bin  
sudo touch /var/cache/apt/srcpkgcache.bin

```

---

### Post by craigd741 on 2010-04-07
Thanks Carlee. The first ones didn't work but with the second ones nothing happened. I'm not sure what that means, whether it worked or not...

---

### Post by Rasa1111 on 2010-04-07
So did you reinstall yet? 

 I think the more commands people throw out at you, 
being only a few days with Ubuntu, 
it will just bring more frustration and mess ups. 

really bro, save yourself the stress.
if you have a fresh, new install, 
you wont have to touch the terminal until after yer all set up n running with everything you need/want. 
and not even then if you dont feel comfy. . :)

---

### Post by sandyd on 2010-04-07
> **craigd741 said:**
> Thanks Carlee. The first ones didn't work but with the second ones nothing happened. I'm not sure what that means, whether it worked or not...

nothing visible was supposed to happen.
try running
```

sudo apt-get update
```

---

### Post by craigd741 on 2010-04-07
> **Rasa1111 said:**
> So did you reinstall yet? 

 I think the more commands people throw out at you, 
being only a few days with Ubuntu, 
it will just bring more frustration and mess ups. 

really bro, save yourself the stress.
if you have a fresh, new install, 
you wont have to touch the terminal until after yer all set up n running with everything you need/want. 
and not even then if you dont feel comfy. . :)

that sounds like the best idea I've heard all day :)
i think that's what i'll do.
cheers mate.

(oh, and when I do reinstall I'll let you know how I got on.)

---

### Post by craigd741 on 2010-04-07
> **carlee said:**
> nothing visible was supposed to happen.
try running
```

sudo apt-get update
```

I then got this....


E: Archive directory /var/cache/apt/archives/partial is missing.

---

### Post by Rasa1111 on 2010-04-07
> **craigd741 said:**
> that sounds like the best idea I've heard all day :)
i think that's what i'll do.
cheers mate.

(oh, and when I do reinstall I'll let you know how I got on.)


 :) please do. 
i have a feeling you'll be up and set in no time. 
 i am a n00b and all, , but i have also done near 20 Ubuntu installs/setups for different people in the last 3 months, so I do kinda got the hang of that part. lol

ohh, and i always thought that the terminal was a must if one was going to run Ubuntu, 
but learned not long ago, that that is not the case. 

the terminal can be played with and learned once youre comfy with everything else. :)

 and not long ago, I spoke with someone who had been using Ubuntu for over 2 years, and never used the terminal once. lol  

good luck bro.

---

### Post by 3rdalbum on 2010-04-07
> **craigd741 said:**
> I then got this....


E: Archive directory /var/cache/apt/archives/partial is missing.

```
sudo mkdir /var/cache/apt/archives/partial
```

---

### Post by craigd741 on 2010-04-07
> **3rdalbum said:**
> ```
sudo mkdir /var/cache/apt/archives/partial
```

I did this. Again, nothing happened so I assume it worked.
Is this going somewhere? Tomorrow I'm probably going to reinstall Ubuntu from scratch.
Thanks for your help.

---

### Post by 3rdalbum on 2010-04-07
> **craigd741 said:**
> I did this. Again, nothing happened so I assume it worked.
Is this going somewhere? Tomorrow I'm probably going to reinstall Ubuntu from scratch.
Thanks for your help.

Correct, if nothing is printed to the terminal then it means that the individual command 'worked'.

This is going somewhere... hopefully to get your package manager working without a reinstall.

---

### Post by craigd741 on 2010-04-08
OK, well I did the last thing and it worked so what next?

---

### Post by sandyd on 2010-04-08
> **craigd741 said:**
> OK, well I did the last thing and it worked so what next?
install anything you want cause everything should be working.

---

