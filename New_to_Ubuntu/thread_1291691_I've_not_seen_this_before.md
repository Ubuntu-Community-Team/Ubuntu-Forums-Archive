---
title: "I've not seen this before"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by jediknight64 on 2009-10-15
I've looked in the forums and I'm sure it's probably just a simple thing, but it's got me scratching my head past midnight. I have an Acer Aspire 5335 dual boot Jaunty. I punch a command in the terminal and this is what I get in response.



```
john@ubuntu:~$ sudo apt-get install
E: Malformed line 56 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
john@ubuntu:~$ sudo apt-get install -f
E: Malformed line 56 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.

```    

  Just point me in the right direction please and I would be much obliged. Thank You.

---

### Post by jeremyswalker on 2009-10-15
Well, I would be curious to see your /etc/apt/sources.list. Could you post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by jediknight64 on 2009-10-15
Here you go. Thank
you.


  ```
john@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiversedeb http://repository.cairo-dock.org/ubuntu jaunty cairo-dock # For Ubuntu 9.04


deb http://repository.cairo-dock.org/ub


untu jaunty cairo-dock ## Cairo-Dock-Stable

john@ubuntu:~$ 

```

---

### Post by nvikram on 2009-10-15
Ah, the last two lines are disconnected (55 + 56), make sure you put them together. 

It should look like this
```
deb http://repository.cairo-dock.org/ubuntu jaunty cairo-dock
```

After fixing that...Re run
```
sudo apt-get install -f
```

And it should work. Hope it works :)

---

### Post by jediknight64 on 2009-10-15
What do I need to do to put them together?

---

### Post by SkyNet2029 on 2009-10-15
you need to manually adjust them using a text editor, so...do this
 
```
$sudo gedit /etc/apt/sources.list
```
 
then edit the file so that line is not carried over into the next. it should
end up looking like this:
 
```
deb http://repository.cairo-dock.org/ubuntu jaunty cairo-dock
```
 
save the file, then
```
sudo apt-get update
```
 
that should fix it up for you.

---

### Post by jediknight64 on 2009-10-15
I thank you SkyNet2029. I did exactly as you told me and now we're back in business!:guitar:

---

