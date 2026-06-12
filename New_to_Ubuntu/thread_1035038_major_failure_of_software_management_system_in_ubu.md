---
title: "major failure of software management system in ubuntu 8.10"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by oxalis on 2009-01-09
Hi all, am a very new user and got myself in a fix trying to install a Wine application as I couldn't open a disc from the OU. This has caused broken packages messages in Open/Remove programs and error messages in Synaptic Passage Manager. I tried to re install Windows from my restore disc which is on 'd'drive of my HP notebook, but got error message 'Error Ox4001100 20000 100A'. What can I do to resolve this? I don't have original Ubuntu disc, so can I re install from a website, or fix the copy I have somehow?
Also why won't Windows restore?:confused:

---

### Post by RobsterUK on 2009-01-09
Ok breathe....go back a few steps.

What program were you trying to install with Wine? Most windows software has an equivalent for Ubuntu, so someone may be able to suggest an alternative for you.

Also tell us exactly what error messages you are getting in Add/Remove Programs and Package Manager

---

### Post by Michael.Godawski on 2009-01-09
So many questions...:D

More details please. Which application you wanted to install in Wine. Why in the first place?
What error messages do you get in Synaptics?

---

### Post by oxalis on 2009-01-09
I was trying to install First Class conferencing system with the OU, as for some obscure reason they insist on using windows, I think it only works on Windows.
Anyway, here goes with error messages:
Add/Remove programmes says *This is a major failure of your software management system. Please check for broken packaghes with snaptic, check file permissions and correctness of the file '/etc./apt/sources.list' and reload software information with 'sudo apt-get update and sudo apt-get install-f'*
In synaptic package manager the message is:
[I]E: Type '--2009-01-08' is not known on line 1 in source list/etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read. Go to the repository dialogue to correct the problem.
E:_cache->open()failed, please report[/I]
There is a red disc with a white line across it like a no entry sign on the info panel which also has a message which says:
*An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: Opening the cache (E:type '--2009-01-08' is not know on  line 1 in source list /etc/apt/sources.list.d/winehq.list, E:The list of sources could not be read.)'this usually means that your installed packages have unmet dependencies*
That's the lot, hope you can make sense of it all.

---

### Post by igknighted on 2009-01-09
Can you post the output of the command 'cat /etc/apt/sources.list'?  Sounds like you just got a line in a config file wrong.  Should be a real simple fix once we can see the file (thats what that command does)

---

### Post by oxalis on 2009-01-09
reply to your command is: bash: cat/etc/apt/sources.list: No such file or directory
jill@jill-laptop:~$

---

### Post by avtolle on 2009-01-09
Command should be ```
cat /etc/apt/sources.list
```

---

### Post by oxalis on 2009-01-09
hope you can make sense of all this:
#  [Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# [Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted 

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted multiverse universe
jill@jill-laptop:~$

---

### Post by Efros on 2009-01-09
FirstClass works fine under Linux. See

[https://help.ubuntu.com/community/FirstClass](https://help.ubuntu.com/community/FirstClass)

---

### Post by oldos2er on 2009-01-09
"[I]E: Type '--2009-01-08' is not known on line 1 in source list/etc/apt/sources.list.d/winehq.list"

 Since the failure's in /etc/apt/sources.list.d/winehq.list, we'll need to see that file. "cat /etc/apt/sources.list.d/winehq.list"

[/I]

---

### Post by oxalis on 2009-01-10
Thanks Efros, but need to sort out failure of management system first. Have found the website you mentioned and downloaded everything, so hopefully ready to go once I have sorted out my first problem.

---

### Post by oxalis on 2009-01-10
Hi Ann, am copying in file for your perusal,
Jill
deb [http://wine.budgetdedicated.com/apt/](http://wine.budgetdedicated.com/apt/) intrepid main
deb-src [http://wine.budgetdedicated.com/apt/](http://wine.budgetdedicated.com/apt/) intrepid main 
# [Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# [Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted 

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted multiverse universe

---

### Post by oxalis on 2009-01-10
ps, tried your command and it says no such file or directory, so have posted what I can.
Jill

---

### Post by oldos2er on 2009-01-10
Can you run this command, and post the output:

 ls /etc/apt/sources.list.d

---

### Post by oxalis on 2009-01-11
Hi Ann, got it sorted with: deb [http://wine.budgetdedicated.com/apt/](http://wine.budgetdedicated.com/apt/) intrepid main
deb-src [http://wine.budgetdedicated.com/apt/](http://wine.budgetdedicated.com/apt/) intrepid main 

Thanks for your help.
Jillhttp://ubuntuforums.org/images/smilies/icon_razz.gif

---

