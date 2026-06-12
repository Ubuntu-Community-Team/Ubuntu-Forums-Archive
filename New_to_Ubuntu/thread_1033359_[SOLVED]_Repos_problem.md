---
title: "[SOLVED] Repos problem"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Ben Page on 2009-01-07
Hey!
I have installed 8.10 yesterday, and was admiring its speed, its noticeably faster installed "really" comparing to Wubi installation.
Everything installs fine (note: using "super"Ubuntu), drivers, progs etc. After downloading proprietary drvrs everithing works.
Now, I seem to have a problem with repositories. I cant really pinpoint the issue, but I can't add any other repository in synaptic. I click add, paste the address of the new repo, but it does nothing, only the default archive.canonical is listed. In Wubi installation I had Ubuntu main or something like that as default 3rd party repo. I had acces to ubuntustudio packages and others like streamtuner app...But now none of those are listed, i tried apt-get and I could download streamtuner, but its not listed in synaptic, also I could download ubuntustudio theme via apt-get (the only package I know from head) but synaptic doesent list any ubuntustudio packages. Also, when adding new repo to 3rd party, it does nothing, but when I close window it tells me that new repos have been added and that I should refresh the list, I do that, it downloads some package info (there are more packages after adding the repo) but none of thepacgages from that repo shows up in synaptic?!? Its confusing!
Is there a setting to show/hide some packages or something? It looks like I get new packages and repos when I add them, but I cant literally"see" them.

Any thoughts?

---

### Post by LowSky on 2009-01-07
system>admin >sources, on the main tab that is show make sure that all the boxes except source code are checked

---

### Post by evilkastel on 2009-01-07
do in a terminal

```
sudo gedit /etc/apt/sources.list
```

copy and paste the content of that file please.
That way we'll know if ubuntu is using the third party repos. also, what is superubuntu?

---

### Post by Ben Page on 2009-01-07
Checked! Except the source code, off course :)

---

### Post by Ben Page on 2009-01-07
Here it is! Hope it helps!

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://rs.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://rs.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://uk.archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://uk.archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://uk.archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://au.archive.ubuntu.com/ubuntu/ intrepid main
```

---

### Post by hyper_ch on 2009-01-07
you can edit the sources.list with an editor and you my generator to generate your repository entries. See my signature for that.

---

### Post by Ben Page on 2009-01-07
>  What is superubuntu?

Well, "super"Ubuntu is Ubuntu unofficial derivate. Its Ubuntu 8.10 with OOffice 3.0, all codecs, p2p, multimedia players, etc. software. Its distributed via mininova torrent site, created by hacktolive.org

[http://hacktolive.org/wiki/Hacktolive.org](http://hacktolive.org/wiki/Hacktolive.org)

---

### Post by Ben Page on 2009-01-07
> **hyper_ch said:**
> you can edit the sources.list with an editor and you my generator to generate your repository entries. See my signature for that.

I have tried your generator, hyper, its easy, but when I copy-paste the generated repo to my synaptic-3rd party software, it doesent show at all-nothing, only the default cannonical arhive repo...?:confused:

---

### Post by hyper_ch on 2009-01-07
> **Ben Page said:**
> when I copy-paste the generated repo to my synaptic-3rd party software

read again:

> **hyper_ch said:**
> you can edit the sources.list with an editor

---

### Post by Ben Page on 2009-01-07
Hyper_ch, if you look in my posted src list, you can see tht I added  a few generated sources, I added them through synaptic, but they are in the sources list, problem is I can't see them in synaptic! So in order to download something trough that repo I need to know "from my head" what to download, I say, apt-get works in terminal, but not in synaptic. So I cant browse the packages via synaptic, they are "invisible" but they can be downloaded...

---

### Post by hyper_ch on 2009-01-07
how do you edit a file?

---

### Post by Ben Page on 2009-01-07
> **hyper_ch said:**
> how do you edit a file?

What do you mean?
I edited it wia synaptic 3rd party sources as well as via "sudo gedit /etc/apt/sources.list"

Here is what the problem is, in sources list repos are added, but in synaptic I only get this:

[IMG]http://i198.photobucket.com/albums/aa180/babyboySR/Untitled.jpg[/IMG]

---

### Post by Ben Page on 2009-01-07
Bump...:confused:

---

### Post by Ben Page on 2009-01-07
Bump again, fellow noob in throuble!

---

### Post by hyper_ch on 2009-01-07
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by Ben Page on 2009-01-07
> **hyper_ch said:**
> [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

All that is mainly clear to me, hyper_ch, but how do I browse the packages-search through them without GUI (synaptic package manager)? I know how to add/edit repos, but how to manage the packages themselves? I know apt-get, but how to browse them, "SEE" them? Synaptic is looking blind for 3rd party repos!

---

### Post by Ben Page on 2009-01-07
Damn it! This is beginning to be frustrating, reinstalled synaptic and nothing! While I was running Ubuntu via Wubi this issue was not present.
Should I reinstall the whole OS? This way I cant browse and download the desired packages, I can only do it via apt-get in terminal.

---

### Post by Ben Page on 2009-01-07
Final cry...
Is there a list command in terminal to list available packages for download?

---

### Post by hyper_ch on 2009-01-07
```

apt-cache search

```

---

### Post by Ben Page on 2009-01-07
Thnx, that will do, shame about the synaptic gui...

---

### Post by oldos2er on 2009-01-07
> **Ben Page said:**
> Final cry...
Is there a list command in terminal to list available packages for download?

 "sudo aptitude"

---

