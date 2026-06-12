---
title: "(NEED HELP) update manager doesn't work on karmic koala 9.10"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by aray_rio on 2010-02-14
Dear All,

Im a newbie at using Linux & UBUNTU

now im using karmic koala 9.10

and i don't know why the update manager doesn't work

and there's some notification like this:confused:

[[IMG]http://img190.imageshack.us/img190/1959/screenshotqp.png[/IMG]](http://img190.imageshack.us/i/screenshotqp.png/)

and when i want to open the update manager, then it's show like this,:sad:

[[IMG]http://img10.imageshack.us/img10/8349/screenshot1yj.png[/IMG]](http://img10.imageshack.us/i/screenshot1yj.png/)

is there anyone could help me to resolve it....:idea:

tku

---

### Post by byStanderone on 2010-02-14
...hope this helps: [http://ubuntuforums.org/archive/index.php/t-713664.html](http://ubuntuforums.org/archive/index.php/t-713664.html)

---

### Post by mwcrowley on 2010-02-14
can you post that your /etc/apt/sources.list

---

### Post by aray_rio on 2010-02-19
> **mwcrowley said:**
> can you post that your /etc/apt/sources.list

how can i do that? 
i'd already try to typed this in the terminal, but it seems it didn't work

oot@ario-ubuntu:~# etc/apt/sources/list
bash: etc/apt/sources/list: No such file or directory
root@ario-ubuntu:~# etc/apt/sources.list
bash: etc/apt/sources.list: No such file or directory
root@ario-ubuntu:~# ^C
root@ario-ubuntu:~# ^C
root@ario-ubuntu:~# "

---

### Post by rustutzman on 2010-02-19
> **aray_rio said:**
> how can i do that? 
i'd already try to typed this in the terminal, but it seems it didn't work

oot@ario-ubuntu:~# etc/apt/sources/list
bash: etc/apt/sources/list: No such file or directory
root@ario-ubuntu:~# etc/apt/sources.list
bash: etc/apt/sources.list: No such file or directory
root@ario-ubuntu:~# ^C
root@ario-ubuntu:~# ^C
root@ario-ubuntu:~# "

You need the first slash before etc
```
gksudo gedit /etc/apt/sources.list 
```

Russ

---

### Post by aray_rio on 2010-02-20
Tku Russ it works,
here is the list. could you explain to me, what is this list meant for?

i really dont understand..:confused:

[COLOR=RoyalBlue]# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic main restricted[/COLOR]
[COLOR=RoyalBlue]
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main
deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main
deb [http://kambing.ui.ac.id/ubuntu/karmic](http://kambing.ui.ac.id/ubuntu/karmic) main[/COLOR]

---

### Post by k3lt01 on 2010-02-21
> **aray_rio said:**
> 
deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main
deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main
deb [http://kambing.ui.ac.id/ubuntu/karmic](http://kambing.ui.ac.id/ubuntu/karmic) mainThese are the last 3 lines of your list. See how the last line is slightly different to the others, that is the problem. You need to make it look like this
```
deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main
deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main
deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main
```

---

### Post by aray_rio on 2010-02-21
> **k3lt01 said:**
> These are the last 3 lines of your list. See how the last line is slightly different to the others, that is the problem. You need to make it look like this
```
deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main
deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main
deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main
```

K3lto1 tku for the info,

could you help how to change it, so it can be like you've said...

im really still newbie and just started learning ubuntu...it feel like a blindfold person when using Ubuntu :confused:

---

### Post by k3lt01 on 2010-02-21
1. In a terminal copy and past this command and type in your password as you did before.
```
gksudo gedit /etc/apt/sources.list
```

2. When your sources list opens you will see this in Gedit.

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic main restricted[/COLOR]
[COLOR=RoyalBlue]
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main
deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main
deb [http://kambing.ui.ac.id/ubuntu/karmic](http://kambing.ui.ac.id/ubuntu/karmic) main[/COLOR]
```

3. Go to the last line in the list, the one that says
```
deb [http://kambing.ui.ac.id/ubuntu/karmic](http://kambing.ui.ac.id/ubuntu/karmic) main
``` and put a space between the ubuntu/ and karmic so it looks like this
```
deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main
```

4. Save and close the file then use update manager. Don't forget to click "check" at the bottom of update manager so it refreshes its package list.

---

### Post by aray_rio on 2010-02-23
Yippie it works...TKU very much K3lt01 for your help. 
Your the best...

---

### Post by k3lt01 on 2010-02-23
That's good :popcorn:, remember to help others when they have problems that you know how to fix.

Could you also mark this thread as Solved please. To do that you go to the top of the page and click on where it says Thread Tools. Then click mark as Solved. That way others who have the same question can see you have fix yours and se if it's the same as theirs.

---

