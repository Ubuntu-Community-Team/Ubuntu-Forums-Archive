---
title: "Could not download all repository indexes"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Dibbling Dave on 2009-09-09
Hello, I'm having problems upgrading my system. A while ago I wanted Opera browser but could not find it in the repository so I downloaded the latest version. Opera works fine but when I get updates I get the following message

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

The following screenshot may help

[IMG]http://space.davethould.fastmail.fm/public/sources.jpeg[/IMG]

Regards Dave

---

### Post by wojox on 2009-09-09
Run in a terminal:

```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -

```

And for some reason you have an index pointing at edgy. Comment it out of /etc/apt/sources.list

---

### Post by Dibbling Dave on 2009-09-09
Thanks for the reply

I now get the following error message

W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

Dave

---

### Post by Eltern on 2009-09-09
I second that Opera is not showing up in the repositories. I have the Canonical partner repository enabled, but Opera doesn't show up. Maybe my problem is related to yours.

---

### Post by nandemonai on 2009-09-10
> **Dibbling Dave said:**
> Thanks for the reply

I now get the following error message

W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

Dave

Try this:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \ F9A2F76A9D1A0061
```

I'm not sure if the key will be there or not. If not you'll need to manually install the key. Instructions should be in the same place you got the repo address from.

---

### Post by Dibbling Dave on 2009-09-10
HI, I've just tried what you said but get this message

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Thanks, dave

---

### Post by nandemonai on 2009-09-10
> **Dibbling Dave said:**
> HI, I've just tried what you said but get this message

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Thanks, dave

I'm not getting any responses on that IP. Could the mirror be down?

Please post your /etc/apt/sources.list file.

---

### Post by Dibbling Dave on 2009-09-10
Hi, Here is my list

[IMG]http://space.davethould.fastmail.fm/public/sources.jpeg[/IMG]

Dave

---

### Post by nandemonai on 2009-09-10
> **Dibbling Dave said:**
> Hi, Here is my list

[IMG]http://space.davethould.fastmail.fm/public/sources.jpeg[/IMG]

Dave

Actually need the 'Ubuntu Software' tab, or idealy from terminal:

```
cat /etc/apt/sources.list
```

Copy and paste the output from that command please ;)

---

### Post by Dibbling Dave on 2009-09-10
Ok, 

dave@dave-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe ##
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
dave@dave-desktop:~$ 

Thanks, Dave

---

### Post by nandemonai on 2009-09-10
> **Dibbling Dave said:**
> Ok, 

dave@dave-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe ##
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
dave@dave-desktop:~$ 

Thanks, Dave

aha! Here's the offending line:

```
deb http://us.archive.ubuntu.com/ubuntu edgy universe ##
```

You'll need to remove that line, also the 

```
deb http://wine.budgetdedicated.com/apt edgy main
```

They're for Ubuntu Edgy, a very old version of Ubuntu.

You can edit that file via this command in terminal:

```
gksudo gedit /etc/apt/sources.list
```

Make the modifications, save the file then close it.

Back in terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Dibbling Dave on 2009-09-10
Hello, that did the trick. I no longer get the error message and my system upgrades. The terminal shows the following output.

dave@dave-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for dave: 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_GB          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg                         
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_GB           
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release              
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_GB                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages                      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources             
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@dave-desktop:~$ 

Many thanks, Dave.

---

### Post by Eltern on 2009-09-14
Hey, Dave, here's my repository list. I'm still unable to see Opera, but I don't have the Edgy repos. Any thoughts?

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

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
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main 

deb http://getswiftfox.com/builds/debian unstable non-free
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main #X-Updates PPA
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main #X-Updates PPA
```

---

### Post by Dibbling Dave on 2009-09-14
Hello, sorry to hear you are still having problems. I have Opera version 10 installed downloaded from the Opera site [http://www.opera.com/]("http://www.opera.com/") You could try installing that. However it isn't an official Ubuntu version. I suppose it depends whether or not you trust Opera. 

Regards Dave.

---

### Post by nigj on 2009-09-17
The Esyest way is normally the best way to fix problems, thanks for your help.

---

### Post by stewieX on 2009-10-19
Hi there,

I'm a complete noob, but I was having the same problem and this seems to have fixed it:

Add ```
deb http://deb.opera.com/opera/ stable non-free
``` to /etc/apt/sources.list.

[INDENT]An easy way to edit it is to open it in a terminal window with:
```
sudo nano /etc/apt/sources.list
```
[/INDENT]
Then run this command that nandemonai posted, but with this different key:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \ 6A423791
```

Then run:
```
sudo apt-get update
```

If you check System>Administration>Update Manager for new updates, the error message should be gone.

---

### Post by mscir on 2010-08-24
> **nandemonai said:**
> Try this:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \ F9A2F76A9D1A0061
```

I'm not sure if the key will be there or not. If not you'll need to manually install the key. Instructions should be in the same place you got the repo address from.

Thanks nandemonai, that fixed mine.

---

