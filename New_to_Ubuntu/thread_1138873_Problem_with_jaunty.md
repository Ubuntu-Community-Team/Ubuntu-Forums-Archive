---
title: "Problem with jaunty"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by swampdude on 2009-04-26
i just installed ubuntu jaunty and everything seems to work fine, the only problem i am having, is it keeps tell me to update, so i do, but then it says i can only do a partial upgrade, so i do that, and then in do the upgrade and it tells me the same amount of packages are either going to be installed or updated, i continue on and the partial upgrade is done. Then a little bit later it will ask me to do the exact same thing and then exact same things need to be upgraded and the exact same things cant be upgraded and its just a loop. What do i do?

---

### Post by NightwishFan on 2009-04-26
Run this command in a terminal window:

```

sudo apt-get update && sudo apt-get upgrade

```

Tell me what you get. If it asks you to remove a bunch of packages do not say yes!

---

### Post by Bodsda on 2009-04-26
Hi, does it say why they cant be updated?

The following command run from a terminal might help

```

sudo apt-get --fix-broken && sudo apt-get --fix-missing

```

Hope this helps,

Bodsda

---

### Post by erm27 on 2009-04-26
Try to check your System/Administration/Software Sources, go to Updates tab. At the bottom there is a section that says Release Upgrade. If you have it set to _Long Term Support releases only_ then you won't get the option to do an upgrade. You need to set to _Normal_. Then you run Update Manager again, hit cancel for the Partial Update prompt. You will see a new button that says Upgrade toward the top right hand corner. Click that and you will upgrade to Jaunty.

---

### Post by 5carby on 2009-04-26
Try rebooting.

---

### Post by H4F on 2009-04-26
> **Bodsda said:**
> Hi, does it say why they cant be updated?

The following command run from a terminal might help

```

sudo apt-get --fix-broken && sudo apt-get --fix-missing

```

Hope this helps,

Bodsda

```
sudo apt-get update --fix-broken && sudo apt-get update --fix-missing
```

---

### Post by swampdude on 2009-04-26
Ok i have allready upgraded to jaunty, and its doing this in jaunty and This is what i got when i ran > sudo apt-get update && sudo apt-get upgrade

```
Ign http://repoubuntusoftware.info harty Release.gpg
Ign http://repoubuntusoftware.info harty/all Translation-en_CA
Ign http://repoubuntusoftware.info harty Release                               
Ign http://repoubuntusoftware.info harty/all Packages                          
Hit http://archive.ubuntu.com jaunty Release.gpg                               
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_CA     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_CA       
Hit http://archive.ubuntu.com jaunty/main Translation-en_CA                    
Hit http://archive.ubuntu.com jaunty/restricted Translation-en_CA              
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_CA    
Ign http://repoubuntusoftware.info harty/all Packages                          
Err http://repoubuntusoftware.info harty/all Packages                          
  404 Not Found
Ign http://security.ubuntu.com hardy-security/main Translation-en_CA           
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_CA     
Ign http://archive.ubuntu.com jaunty/universe Translation-en_CA                
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_CA              
Hit http://archive.ubuntu.com jaunty-updates Release.gpg                       
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_CA            
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_CA      
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_CA        
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_CA      
Hit http://archive.ubuntu.com jaunty-security Release.gpg                      
Hit http://security.ubuntu.com hardy-security Release                          
Ign http://archive.ubuntu.com jaunty-security/main Translation-en_CA           
Ign http://archive.ubuntu.com jaunty-security/restricted Translation-en_CA
Hit http://us.archive.ubuntu.com hardy Release.gpg                   
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_CA  
Hit http://us.archive.ubuntu.com hardy-updates Release               
Ign http://archive.ubuntu.com jaunty-security/universe Translation-en_CA       
Ign http://archive.ubuntu.com jaunty-security/multiverse Translation-en_CA     
Hit http://archive.ubuntu.com jaunty Release                                   
Hit http://archive.ubuntu.com jaunty-updates Release                           
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://us.archive.ubuntu.com hardy Release                                 
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_CA               
Hit http://archive.ubuntu.com jaunty-security Release                          
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://archive.canonical.com hardy Release                                 
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages             
Hit http://archive.ubuntu.com jaunty/main Packages                             
Hit http://archive.ubuntu.com jaunty/restricted Packages             
Hit http://archive.ubuntu.com jaunty/main Sources                              
Hit http://archive.ubuntu.com jaunty/restricted Sources                        
Hit http://archive.ubuntu.com jaunty/universe Packages                         
Hit http://archive.ubuntu.com jaunty/universe Sources                          
Hit http://archive.ubuntu.com jaunty/multiverse Packages                       
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Ign http://archive.canonical.com hardy/partner Sources                         
Hit http://us.archive.ubuntu.com hardy/multiverse Sources            
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com jaunty/multiverse Sources
Hit http://archive.ubuntu.com jaunty-updates/main Packages
Hit http://archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://archive.ubuntu.com jaunty-updates/main Sources
Hit http://archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://archive.ubuntu.com jaunty-updates/universe Packages
Hit http://archive.ubuntu.com jaunty-updates/universe Sources
Hit http://archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://archive.ubuntu.com jaunty-security/main Packages
Ign http://archive.canonical.com hardy/partner Packages
Hit http://archive.ubuntu.com jaunty-security/restricted Packages
Hit http://archive.canonical.com hardy/partner Sources
Hit http://archive.canonical.com hardy/partner Packages
Hit http://archive.ubuntu.com jaunty-security/main Sources
Hit http://archive.ubuntu.com jaunty-security/restricted Sources
Hit http://archive.ubuntu.com jaunty-security/universe Packages
Hit http://archive.ubuntu.com jaunty-security/universe Sources
Hit http://archive.ubuntu.com jaunty-security/multiverse Packages
Hit http://archive.ubuntu.com jaunty-security/multiverse Sources
W: Failed to fetch http://repoubuntusoftware.info/dists/harty/all/binary-amd64/Packages  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Bodsda on 2009-04-26
Hmm, what is this repo?

[http://repoubuntusoftware.info/dists/harty/all/binary-amd64/Packages](http://repoubuntusoftware.info/dists/harty/all/binary-amd64/Packages)

Can you please paste the output of the following command

```

cat /etc/apt/sources.list

```

Thanks,

Bodsda

---

### Post by swampdude on 2009-04-26
```
joe@joe-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
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
# deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse

#ULTAMATIX REPOS START

deb http://repoubuntusoftware.info harty all

deb-src http://us.archive.ubuntu.com/ubuntu hardy-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu hardy-updates multiverse

deb-src http://us.archive.ubuntu.com/ubuntu hardy multiverse

deb http://us.archive.ubuntu.com/ubuntu hardy multiverse

deb http://repoubuntusoftware.info harty all

deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://security.ubuntu.com/ubuntu hardy-security multiverse

deb-src http://security.ubuntu.com/ubuntu hardy-security universe

deb http://security.ubuntu.com/ubuntu hardy-security universe

deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted

deb http://security.ubuntu.com/ubuntu hardy-security main restricted

deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.canonical.com/ubuntu hardy partner
#ULTAMATIX REPOS END
```

---

### Post by erm27 on 2009-04-26
> **swampdude said:**
> Ok i have allready upgraded to jaunty, and its doing this in jaunty and This is what i got when i ran 


I don't believe you have Jaunty fully installed. As you can see you still have repo entries for Hardy. I did this earlier in the week, if you will, just try and check your Sources. See if you have the Release Upgrade set to "Long Term Support only". If so, you won't upgrade fully until you set this to "Normal". You will actually see an extra button appear at the top of your Update Manager window. This will say their is a new distribution available. Then hit Upgrade.

---

### Post by swampdude on 2009-04-26
im new to ubuntu, but i downloaded jaunty, burned jaunty and installed jauntu. I put linux on my comp yestarday.

---

### Post by swampdude on 2009-04-26
Oh wait i fixed it (i think). First the partial update or whatever, i think that was because my update server was a server in my city and perhaps they did not have all the files? Because i changed it to main server and everything updated. 


Also i just found out the hardy repos are from a program called ultamatix, which was designed for hardy and not jaunty hence the hardy repos?

---

### Post by erm27 on 2009-04-26
> **swampdude said:**
> Oh wait i fixed it (i think). First the partial update or whatever, i think that was because my update server was a server in my city and perhaps they did not have all the files? Because i changed it to main server and everything updated. 


Also i just found out the hardy repos are from a program called ultamatix, which was designed for hardy and not jaunty hence the hardy repos?

I was just about to post that I'm not sure why you are showing Hardy repo's if you did a clean install. This is a clean install for me as well, with nothing added. 

Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages


No mention of Hardy anywhere. Again, check your Sources. Disable anything that says Pre-released or Unsupported updates within the Updates tab.

---

### Post by Miljet on 2009-04-26
Take a look at this:  [http://qense.nl/ubuntu-nl-warns-for-ultimatix](http://qense.nl/ubuntu-nl-warns-for-ultimatix)

---

