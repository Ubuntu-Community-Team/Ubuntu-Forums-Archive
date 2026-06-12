---
title: "Update Manager Does not work"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Horizon101 on 2009-04-17
Hi,

I'm Using Ubuntu8.04. 
The update manager does not work and it gives a notofication saying "Update information is outdated. This may be caused by network problems. Please update manually by clicking on this icon and then selecting"Chexk""

when I try to do this it gived an error message saying"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead."

Please Help.

Thanks

---

### Post by cmnorton on 2009-04-17
Start with these. They might help. Using launchpad to search and ask questions -- if you don't feel it's a bug -- is IMHO a good thing to do.

[https://answers.launchpad.net/ubuntu/+question/51324](https://answers.launchpad.net/ubuntu/+question/51324)
[https://answers.launchpad.net/ubuntu/+question/11276](https://answers.launchpad.net/ubuntu/+question/11276)


[http://ubuntuforums.org/showthread.php?t=368473](http://ubuntuforums.org/showthread.php?t=368473)
[http://ubuntuforums.org/showthread.php?t=1078737](http://ubuntuforums.org/showthread.php?t=1078737)

---

### Post by taurus on 2009-04-17
You have warty repo in your /etc/apt/sources.list!  :?

```
cat /etc/apt/sources.list
```

---

### Post by sadaruwan12 on 2009-04-17
Hi,

I think you might have to rebuild your repository list. You cant do that using the synaptic manager you've to got to the terminal to do that So try this.

Lunch terminal then type this command,
```
sudo apt-get update
```

and it'll ask for you for a password give the password you use to log in to ubuntu. Then this will rebuild your repo list after finishing this use this command to apply the updates,

```
sudo apt-get ugrade
```

After finishing both the steps try using the update manager. I think this will solve your proiblem.

---

### Post by Horizon101 on 2009-04-17
Hi all,
I did sudo apt-get update and it gave me the following output

roy@roy-desktop:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Translation-en_US    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty Release                          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release               
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release              
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Packages                        
  404 Not Found [IP: 91.189.88.45 80]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Sources
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

When I did sudo apt-get ugrade it gives me this,
roy@roy-desktop:~$ sudo apt-get ugrade
E: Invalid operation ugrade

I even tried changing the server. Still no luck.
What should I do?

---

### Post by taurus on 2009-04-17
You need to edit your /etc/apt/sources.list and remove the warty repo.  Otherwise, update/upgrade will never work.

```
gksudo gedit /etc/apt/sources.list
```

p.s.  Not sure how you managed to get warty in there anyway.

---

### Post by sadaruwan12 on 2009-04-17
> **taurus said:**
> You need to edit your /etc/apt/sources.list and remove the warty repo.  Otherwise, update/upgrade will never work.

```
gksudo gedit /etc/apt/sources.list
```

p.s.  Not sure how you managed to get warty in there anyway.

 Well after seeing your out put I've to agree with turus it seems like you've no other way than editing your sources.list heres how to do it.

open the terminal and then go to type

```
sudo gedit /etc/apt/sources.list
```

after giving the password you'll get your sorces.list for editing and I so you're from Sri Lanka I'm also from SL so heres my sources.list constance I've edited it so it'll only contain the default values try over writing your one with this, Please tell if this works

```

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://lk.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://lk.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://lk.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://lk.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://lk.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://lk.archive.ubuntu.com/ubuntu/ hardy universe
deb http://lk.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://lk.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://lk.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://lk.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://lk.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://lk.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://lk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://lk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by Horizon101 on 2009-04-17
Hi,
Sandaruwan, I saved the repository list you gave me so that it overwrites the existing list. And "sudo apt-get update" worked fine but ,
roy@roy-desktop:~$ sudo apt-get ugrade
E: Invalid operation ugrade
 :(
But anyway, the package manager indicated  for new updates (it didn't show any updates up to now). But when i try to update it asks me to do a "Partial update" since some of the updates cannot be retrieved.

I started installing the updates ignoring the ones that cannot be retrieved.

I'll let you all know what happened.

Thanks
KIT

---

### Post by mikechant on 2009-04-17
It's 'upgrade' not 'ugrade'

---

### Post by Horizon101 on 2009-04-17
Ah...hehe

my mistake!!

Now sudo apt-get upgrade worked fine.

But when I started the update manager, still it asks me to do a partial update. here's what it says
"Not all Updates Can be Installed
Run a partial upgrade, to install as many updates as possible.
This can be caused by:
A previous upgrade which didn't complete
Problems with some of the installed software
Unofficial software packages not provided by Ubuntu
Normal changes of a pre-release version of Ubuntu"

What shall I do next??

---

### Post by Horizon101 on 2009-04-17
Hi

I did the partial upgrade and now the update manager seemed to be working because now it says that the system is up-to-date. :)

Thanks a lot to all of you.

P.S: By the way what is warty repo?

---

### Post by lavinog on 2009-04-17
warty was ubuntu 4.10 (really old)
I wonder how it got into your repositories
Did you follow a how-to recently?

---

### Post by Horizon101 on 2009-04-18
Hi,

yeah, I did.
The thing is  that I don't know how to get certain things done with Ubuntu so I have to do a bit of searching and follow whatever  is on the web. May be this have happened as a result of that.

Last week I tried to add more repositories and yesterday i tried to install OpenOffice3 in my system. One of them might have resulted in this disaster. hehe

My system is up and running again, thanks to you all.

Have a nice day!!

---

