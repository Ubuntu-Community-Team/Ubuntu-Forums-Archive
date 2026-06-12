---
title: "Install SSH"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by jimmyjean on 2009-11-11
Hi,

I'm faily new to building servers so apologies for basic questions. The distro is 9.04 Jaunty.

I'm trying to install the SSH server using the command

```
sudo apt-get install ssh
```

However, I receive an error saying that the package has no installation candidate.

Please help.

Thanks

Jim

---

### Post by meborc on 2009-11-11
try to install openssh-client and openssh-server

```
sudo apt-get install openssh-client openssh-server
```

---

### Post by desperado665 on 2009-11-11
I believe that ```
sudo apt-get install openssh
``` will install both client and server

---

### Post by meborc on 2009-11-11
> **desperado665 said:**
> I believe that ```
sudo apt-get install openssh
``` will install both client and server

hmm.. packages.ubuntu.com does not seem to think so [http://packages.ubuntu.com/search?keywords=openssh&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=openssh&searchon=names&suite=jaunty&section=all)

---

### Post by jimmyjean on 2009-11-11
I've tried all of the above but still get the message saying that the package has no installation candidate.

Could it be something to do with the repository source list. What should I have in there to be able to access to SSH packages?

Thanks

---

### Post by meborc on 2009-11-11
> **jimmyjean said:**
> I've tried all of the above but still get the message saying that the package has no installation candidate.

Could it be something to do with the repository source list. What should I have in there to be able to access to SSH packages?

Thanks

hmm... i think you don't need any extra repositories...

by searching i found this sources list file, your file should have something in the lines of :  > deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution. 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security
## team. 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team. 
# deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu
## users. 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner 
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse

not sure if it applies, as i'm far from my linux box

---

### Post by ukripper on 2009-11-11
can you post your /etc/apt/sources.list file contents, open the file using below:
```
gedit /etc/apt/sources.list
```

and post contents of the file here.

---

### Post by waspbr on 2009-11-11
all I normally do i just type the command

```
sudo apt-get install ssh
```

---

### Post by jimmyjean on 2009-11-11
Hi,

Here is the output from sources.list:

[HTML]# 
# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted

#deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse[/HTML]

Many thanks

---

### Post by ukripper on 2009-11-11
your sources.list looks fine to me. Can you run the below command and post the output here:
```
sudo apt-get install openssh-server
```

---

### Post by jimmyjean on 2009-11-11
Here is the output:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openssh-server has no installation candidate
```

---

### Post by ukripper on 2009-11-11
Is your internet working?
Can you post output of the following command:
```
ifconfig
```

---

### Post by jimmyjean on 2009-11-11
The internet is definitely working because i can ping various addresses. The error message also says that the package is referred to by another package so implies my machine is connecting to the repositories.

---

### Post by pi.boy.travis on 2009-11-11
Could you post the output of:

```
sudo apt-get update
```
```
Sudo apt-get check
```

Good Luck

---

### Post by ukripper on 2009-11-11
> **jimmyjean said:**
> The internet is definitely working because i can ping various addresses. The error message also says that the package is referred to by another package so implies my machine is connecting to the repositories.

Can you try installing some other package which is in main repo like:
```
sudo apt-get install htop
```

---

### Post by jimmyjean on 2009-11-11
This was the output of update:

```
Get: 1 http://gb.archive.ubuntu.com jaunty Release.gpg [189B]
Get: 2 http://security.ubuntu.com jaunty-security Release.gpg [189B]
Get: 3 http://archive.canonical.com jaunty Release.gpg [189B]
Get: 4 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Ign http://security.ubuntu.com jaunty-security/main Translation-en_GB
Ign http://archive.canonical.com jaunty/partner Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_GB
Get: 5 http://archive.canonical.com jaunty Release [10.5kB]
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_GB
Get: 6 http://security.ubuntu.com jaunty-security Release [57.9kB]
Get: 7 http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB [35.2kB]
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://archive.canonical.com jaunty/partner Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Get: 8 http://gb.archive.ubuntu.com jaunty/multiverse Translation-en_GB [47.5kB]
Hit http://archive.canonical.com jaunty/partner Sources
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty-updates Release.gpg
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Ign http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Ign http://gb.archive.ubuntu.com jaunty-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB
Get: 9 http://gb.archive.ubuntu.com jaunty Release [74.6kB]
Hit http://gb.archive.ubuntu.com jaunty-updates Release
Hit http://gb.archive.ubuntu.com jaunty/main Packages
Hit http://gb.archive.ubuntu.com jaunty/main Sources
Hit http://gb.archive.ubuntu.com jaunty/universe Packages
Hit http://gb.archive.ubuntu.com jaunty/universe Sources
Hit http://gb.archive.ubuntu.com jaunty/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty/multiverse Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/main Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/main Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Sources
Fetched 146kB in 0s (208kB/s)
Reading package lists...
```

After running this update I was able to install openssh-server. Thanks very much.

Is there a method to have repository and system updates happen automatically?

Thanks for the help

---

### Post by pi.boy.travis on 2009-11-11
> **jimmyjean said:**
> This was the output of update:

```
Get: 1 http://gb.archive.ubuntu.com jaunty Release.gpg [189B]
Get: 2 http://security.ubuntu.com jaunty-security Release.gpg [189B]
Get: 3 http://archive.canonical.com jaunty Release.gpg [189B]
Get: 4 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Ign http://security.ubuntu.com jaunty-security/main Translation-en_GB
Ign http://archive.canonical.com jaunty/partner Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_GB
Get: 5 http://archive.canonical.com jaunty Release [10.5kB]
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_GB
Get: 6 http://security.ubuntu.com jaunty-security Release [57.9kB]
Get: 7 http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB [35.2kB]
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://archive.canonical.com jaunty/partner Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Get: 8 http://gb.archive.ubuntu.com jaunty/multiverse Translation-en_GB [47.5kB]
Hit http://archive.canonical.com jaunty/partner Sources
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty-updates Release.gpg
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Ign http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Ign http://gb.archive.ubuntu.com jaunty-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB
Get: 9 http://gb.archive.ubuntu.com jaunty Release [74.6kB]
Hit http://gb.archive.ubuntu.com jaunty-updates Release
Hit http://gb.archive.ubuntu.com jaunty/main Packages
Hit http://gb.archive.ubuntu.com jaunty/main Sources
Hit http://gb.archive.ubuntu.com jaunty/universe Packages
Hit http://gb.archive.ubuntu.com jaunty/universe Sources
Hit http://gb.archive.ubuntu.com jaunty/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty/multiverse Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/main Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/main Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Sources
Fetched 146kB in 0s (208kB/s)
Reading package lists...
```

After running this update I was able to install openssh-server. Thanks very much.

Is there a method to have repository and system updates happen automatically?

Thanks for the help

Glad that helped!  To update your server, you need to run:
```
sudo apt-get update
```
and then:
```
sudo apt-get upgrade
```

If you don't want to have to type them both, you could do what I do, and write a script.  Check out [this guide]("https://help.ubuntu.com/community/Beginners/BashScripting#Scripting").

---

### Post by ukripper on 2009-11-11
> **jimmyjean said:**
> 
Is there a method to have repository and system updates happen automatically?

Thanks for the help

If it is a server edition you can crontab updates to check on scheduled basis. See this [http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/)

---

### Post by pi.boy.travis on 2009-11-11
> **ukripper said:**
> If it is a server edition you can crontab updates to check on scheduled basis. See this [http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/)

That also works nicely!

---

### Post by falconindy on 2009-11-11
> **ukripper said:**
> If it is a server edition you can crontab updates to check on scheduled basis. See this [http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/)
You don't need to be running server edition to run 'apt-get update' via cron. Your linked article also makes the terrifying suggestion of blindly updating via cron. You should **never** do this. If you've got gnome, there's an excellent GUI to crontab, gnome-schedule.

---

### Post by ukripper on 2009-11-11
> **falconindy said:**
> You don't need to be running server edition to run 'apt-get update' via cron. Your linked article also makes the terrifying suggestion of blindly updating via cron. You should **never** do this. If you've got gnome, there's an excellent GUI to crontab, gnome-schedule.

On ubuntu server there is no gnome for a reason! I know you can run on desktop edition too but why do that when you have update manager already on desktop version? And it is not blindly updating. If someone wants their update automatic then they may choose that route. I like my updates manually.

---

### Post by falconindy on 2009-11-11
> On ubuntu server there is no gnome for a reason!
I'm aware of this. That's why I qualified it with an 'if'. Plenty of people running the server edition choose to install a GUI which is sometimes Gnome.

> And it is not blindly updating.
Oh really? From the article you linked:
```
0 0 * * * aptitude -y update && **aptitude -y upgrade** && **aptitude -y dist-upgrade** && aptitude -y autoclean
```
That's doing 3 horrible things at once. It's not only blindly upgrading, but its running upgrade first as well. 'dist-upgrade' will perform extra dependency checks that 'upgrade' won't. Old packages are being deleted as well. Holding old packages can be extremely useful in the case of needing to downgrade to fix a compatibility issue.

---

### Post by ukripper on 2009-11-12
> **falconindy said:**
> 
That's doing 3 horrible things at once. It's not only blindly upgrading, but its running upgrade first as well. 'dist-upgrade' will perform extra dependency checks that 'upgrade' won't. Old packages are being deleted as well. Holding old packages can be extremely useful in the case of needing to downgrade to fix a compatibility issue.

Again depending upon personal needs/situation and perspective of automating tasks. I personally would never opt up for automatic updates/upgrades. But there are people who just run home media servers can automate/cron option "aptitude safe-upgrade". Again depending upon situation and perspective. Besides, i only pointed OP to that website so he/she can read and make informed decision by himself/herself as stated on that blog and comments. "If someone can type they surely don't need to be spoon fed!"

---

### Post by 3rdalbum on 2009-11-12
I think manually checking your updates is highly overrated. I've never had anything break from an update - and for the last year I've been installing from the "proposed" repository! Plus, it's not like the changelog is going to say "This update will break the GUI on the xyz chipset".

---

