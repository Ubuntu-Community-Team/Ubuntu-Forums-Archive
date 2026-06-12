---
title: "update manager won't"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by Calais225 on 2011-01-14
I was attempting to install a new item in third party sources (Remastersys) and my internet stopped during the process.

Now, Update Manager does not work, it returns this error message:

E:Malformed line 55 in source list/etc/apt/sources.list (dist parse)

and E: the list of sources could not be read

the same error messages appear in a terminal after typing:  sudo apt-get update

Also Synaptic Package Manager is not working, same sort of error message.

There must be some way to correct this in Terminal but I am too inexperienced to know what to try.

Thanks for any help.

---

### Post by SuaSwe on 2011-01-14
Would you be able to go into Terminal and do:

```

sudo cat /etc/apt/sources.list

```

and let us know what it says? Looks like your sources.list is a bit unhappy. :D

---

### Post by Calais225 on 2011-01-14
okay here is what came up

```

```wjsm@wjsm-Vostro:~$ sudo apt-get update
[sudo] password for wjsm: 
E: Malformed line 55 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
wjsm@wjsm-Vostro:~$ sudo cat /etc/apt/sources.list
[sudo] password for wjsm: 
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic
deb-src [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic
wjsm@wjsm-Vostro:~$ sudo vi /etc/apt/sources.list

---

### Post by Calais225 on 2011-01-14
I think this is what I was trying to add to the software sources so that I could install remastersys

# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

but I can't remember if I included the # Remastersys part

It said this was okay for Karmic and Lucid, but I am on Maverick

---

### Post by Calais225 on 2011-01-14
in reading the text in my terminal, does it mean I need to remove the # from the four lines mentioned to uncomment them?

If so, how do I get my cursor up to those lines to do that----how is that for a new person question?  I don't even know how to scroll or move around in the terminal.

I am looking this up in my Beginning Ubuntu book, but it's 700 pages and it may take a while.

:p

---

### Post by Calais225 on 2011-01-14
It's bedtime for this senior citizen, I will wrestle with this tomorrow.

---

### Post by 3rdalbum on 2011-01-14
In the terminal, type (or copy and paste in) this:

```
gksudo gedit /etc/apt/sources.list[/code

This brings up a text editor where you can modify your sources.list. Remove the last two lines that end in "karmic", and then press the Save button (or Control-S).

Now you can run:

[code]sudo apt-get update
```

in the terminal, to bring things back to the way they were before you ever discovered Remastersys.

Now you can try again the instructions that you found. Instead of directly modifying the /etc/apt/sources.list file, you should instead use the Software Sources program - go into Ubuntu Software Center and select "Software Sources" from the menus there. You can add a new repository that way, and it ensures that the repository line is not "malformed" before adding it.

---

### Post by Calais225 on 2011-01-15
Thanks, 3rdAlbum, that got me back to where synaptic package manager and update manager are now working.

Ironic isn't it?  I was trying to install a backup program so as to preserve my setup/system and that endangered what I was trying to protect.

I have been tweaking my system and thought I would like to preserve the way it was.  

I did not install remastersys so may look for a different one or give it a go later.

Thanks to SuaSwe as well.

I will mark this thread as solved.

Cheers.

---

