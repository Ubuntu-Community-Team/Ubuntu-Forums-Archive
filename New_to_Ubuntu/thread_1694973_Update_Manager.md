---
title: "Update Manager"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by corto_be on 2011-02-25
When I launch the 'Update Manger' I get the following message:*

[FONT="Times New Roman"]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 60 in source list /etc/apt/sources.list'[/FONT]

---

### Post by zenwalker on 2011-02-25
Guess did you corrupted the sources.lst file?? Just use sudo command and open that file and remove the contents and paste the output from here [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by plucky on 2011-02-25
> 'E:Type 'sudo' is not known on line 60 in source list /etc/apt/sources.list'

That means there is an error in your sources.list file on line 60.

Either

Post the output of ```
cat /etc/apt/sources.list
``` so someone can tell you how to correct the error.

Or 

Edit the file with ```
gksudo gedit /etc/apt/sources.list
``` and find line 60 and correct the error.


Good Luck

---

### Post by corto_be on 2011-02-26
When I try to launch my update manager I got the following message: 

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 60 in source list /etc/apt/sources.list'

---

### Post by corto_be on 2011-02-26
what to correct in this line which is the following:*"sudo aptitude install cinelerra"

---

### Post by thefasterblueone on 2011-02-26
please post the output of this command.

```
cat /etc/apt/sources.list
```

---

### Post by corto_be on 2011-02-26
if i put "cat /etc/apt/sources.list" into the terminal nothing happens

---

### Post by Bölvaður on 2011-02-26
> **corto_be said:**
> When I try to launch my update manager I got the following message: 

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 60 in source list /etc/apt/sources.list'


I have few questions

How did you try to start the update manager?
Did you try to install some software by going by some tutorial or howto on the internet? (perhaps you copied some command beginning with sudo into "software sources")

I have no idea what version of ubuntu you have so I'll just expect you to have the latest one.


[LIST]
[*]Open the software centre
[*]In the menu find Edit &#8594; Software Sources
[*]type in your password
[*]Click Other software
[*]The bottom ones are the ones you've added. Do they all start with http:// and does any of them start with sudo?
[*]Click the one starting with sudo and then Edit.. copy this line into this forum and post.
[*]Then AFTER pasting this here you are now allowed to remove this line and hit close.
[*]Wait a little bit (you'll see processing icon in software centre) and then go into update manager and try again.
[/LIST]

---

### Post by corto_be on 2011-02-26
here is what i get


# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
sudo aptitude install cinelerra

---

### Post by thefasterblueone on 2011-02-26
Can you edit the sources.list using plucky's instructions and possibly copy and paste the contents of the sources.list so we can be sure that the correct information is deleted?

---

### Post by corto_be on 2011-02-26
here is what i get when posting 'cat /etc/apt/sources.list'

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
sudo aptitude install cinelerra

---

### Post by Habeouscorpus on 2011-02-26
that bottom line isn't supposed to be there. Remove it, and save.

---

### Post by thefasterblueone on 2011-02-26
Remove [COLOR="Red"]sudo aptitude install cinelerra[/COLOR] using plucky's instructions.

Don't forget to save the file.  File> Save> close. 

Then run this:

```
sudo apt-get update
```

---

### Post by corto_be on 2011-02-26
is it normal that he asked for the cd 'ubuntu-netbook 10.10'?

---

### Post by Bölvaður on 2011-02-26
> **Habeouscorpus said:**
> that bottom line isn't supposed to be there. Remove it, and save.
> **corto_be said:**
> 
sudo aptitude install cinelerra


If you want to install cinelerra you have to add the repository there.. not the command that you use to install from the repository.

go to : [https://launchpad.net/~cinelerra-ppa/+archive/ppa]("https://launchpad.net/%7Ecinelerra-ppa/+archive/ppa") (this link was found on their website)
and choose your version of ubuntu

then go into that software centre or the file you copy and pasted and add a line that looks like this 
```
deb [http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu](http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu) natty main
```
you'll see how your's should look like on this website I linked you to.


then when you've done this you can open up the terminal and paste in> **corto_be said:**
> 
 sudo aptitude install cinelerra

or open synaptic package manager and look for cinelerra (System &#8594; Administration &#8594; Synaptic Package manager.... OR alt+f2 and write *gksu synaptic*)

---

### Post by howefield on 2011-02-26
Duplicate threads merged.

---

### Post by Bölvaður on 2011-02-26
> **corto_be said:**
> is it normal that he asked for the cd 'ubuntu-netbook 10.10'?

not really... it is only normal in this situation with this line active in your source list

```
deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
```

please edit this one by putting a # in front of it like this


```
[SIZE=2]**#**[/SIZE] deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
```

you can also disable it when you open software sources (you can look at my top post again to see how to get it) and then look for where it says something about a cd... just disable that thing.

---

