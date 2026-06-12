---
title: "How do I enable 3rd party sources list in Jaunty?"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Brian_Newbie on 2009-04-26
When I upgraded to Jaunty Jackalope from Intrepid I got an error that read: 

"3rd party entries in sources.list were disabled. Enable with software properties or package manager after upgrade."

Are these 3rd party entries to be found in "software sources" then "third party software?" 

The boxes in that section are all unchecked and there are 3 "disabled on upgrade to Jaunty" entries there as well as 2 "unsupported updates" boxes that are also unchecked.

How do I enable or re-enable 3rd party sources list in Jaunty?

Brian

---

### Post by zvacet on 2009-04-26
I don´t use Jaunty at the moment but I hope thing are the same as they use to be.In that case under third party check ones you want and refresh after that.Under updates tab you can check first two.

---

### Post by ubuntu27 on 2009-04-26
You can enable them by checking the boexes. But, I recommend you to NOT to do that.

The current 3rd party repository that you have is for the previous version of Ubuntu.
It is never a good idea to mix repos for different version of Ubuntu.

So what you have to do is to remove those 3rd party repositories and add them again with their appropiate address for Ubuntu 9.04


In order to know if you really have Ubuntu 9.04 (Jaunty), type the following in the terminal:

```
cat /etc/lsb-release
```

It should say:

> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"


Now, type the following command to the terminal, and paste it into this thread.

```
cat /etc/apt/sources.list
```

That command will provide the list of repositories that you have.

We will see which one of those needs to be replaced.

---

### Post by Brian_Newbie on 2009-04-26
These are the results of the 2 commands you requested.

brian@ubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04" 

and this one:


brian@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) jaunty main # disabled on upgrade to jaunty

brian@ubuntu:~$

---

### Post by ubuntu27 on 2009-04-26
> **Brian_Newbie said:**
> 

The following (in Black) is for the old version of Ubuntu so, you can leave it disabled or delete it.

brian@ubuntu:~$ cat /etc/apt/sources.list
**# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted**


> **Brian_Newbie said:**
> 
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
[B]# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid [/B]partner

brian@ubuntu:~$


You can replace the above with this one (In bold) for Ubuntu 9.04:

> ## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
[B]deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner[/B]
To modify your sources.list (Repository list), open the terminal and type:

```
gksu gedit /etc/apt/sources.list
```

A Text Editor called Gedit will be open. Delete or replace the lines that I have bolded above.


Save it and close it.

And then 

```
sudo apt-get update
```

That command checks to see if there is anything new on the repository.

That is all :KS

---

### Post by steve101101 on 2009-04-26
you can also add any third party repository through the synaptic gui.

---

### Post by zvacet on 2009-04-26
> The current 3rd party repository that you have is for the previous version of Ubuntu.

If you do upgrade correctly (uncheck all third party repos before upgrade) then 3rd party repos after upgrade belongs to upgraded version.

---

### Post by Brian_Newbie on 2009-04-27
Hi everyone:

Thanks Ubuntu27. I followed your last post instructions and it deleted my intrepid sources successfully.

But since I was still getting lilo errors (when I used Grub to boot my system) as well as other errors, I saved my home folders files to a CD and tried a fresh install for a change. 

The fresh install worked perfectly with no errors. It's as if I bought the computer new from a store today. I'm very happy I did this. Although I expect there will be some bugs with even a fresh install, all applications I've downloaded so far work great.

Thanks to everyone.

---

