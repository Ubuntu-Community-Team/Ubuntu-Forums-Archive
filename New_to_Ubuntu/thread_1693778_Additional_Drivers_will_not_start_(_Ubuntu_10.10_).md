---
title: "Additional Drivers will not start ( Ubuntu 10.10 )"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by hengchuen on 2011-02-23
Hi everyone, I am beginner to Ubuntu and just installed Ubuntu few minutes ago.

Now I am facing a problem of Additional Drivers. When I run the Additional Drivers ( System > Administration > Additional Drivers).

It prompt out a window stating ' Downloading and updating package indexes..' ... and nothing happen after the downloading/updating finishes...

Anyone please help me to solve my problem.

---

### Post by Perfect Storm on 2011-02-23
Do you have internet access on your computer, or it may also be your sourcelist that something wrong with?

Try close the Additional Driver software and open the terminal;
```
sudo apt-get update && sudo apt-get upgrade
```
Try the additional driver again.

---

### Post by hengchuen on 2011-02-23
I failed to connect to my.archive.ubuntu.com ..

---

### Post by Perfect Storm on 2011-02-23
Please give me the output of this:

```
cat /etc/apt/sources.list
```

---

### Post by G4Oblivion on 2011-02-23
I had this problem yesterday when trying to get Broadcom STA driver.

It gave me some error message like:
Failed to connect to "us.archive.ubuntu.com/ubuntu/pool/b/something/something"

I went to that link on my browser and downloaded it myself, no problems.
Somethings up?

I haven't tried to install any drivers since yesterday, so I don't know if the error is still there.


It checked for drivers fine, just wouldn't download the driver.

---

### Post by hansolo4949 on 2011-02-23
Are you connected to the Internet? Because the errors you are describing would stem from that. You have to be connected to sudo update, and to get the restricted drivers.

---

### Post by G4Oblivion on 2011-02-23
I know for a fact I was connected to the internet when I was getting the error. I already had the B43 driver, but it had issues, so I wanted to try the STA (STA is sooo~ much better)

Issues meaning: I had horrible DL speeds, and speed was unstable, too.
I DL'd my gfx driver just fine using the B43 driver, so I don't think thats the issue.

---

### Post by hengchuen on 2011-02-24
> **Artificial Intelligence said:**
> Please give me the output of this:

```
cat /etc/apt/sources.list
```

#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
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

---

### Post by hengchuen on 2011-02-24
when I tried to the 
sudo apt-get update && sudo apt-get upgrade

my terminal stuck at the point shown in the picture and not more than few secs later.. a bunch of error stating failed to fetch something appears.

[[IMG]http://img203.imageshack.us/img203/2731/screenshotgac.png[/IMG]](http://img203.imageshack.us/i/screenshotgac.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by darknomel on 2011-02-24
Are you behind a proxy?

---

### Post by hengchuen on 2011-02-24
> **darknomel said:**
> Are you behind a proxy?

nope...

---

### Post by Perfect Storm on 2011-02-24
I guess "my" is Malaysia. There could be some troubles with their servers there. Try change to another server by change to another country or erase **my.** infront of the source line in your source list.
```
gksu gedit /etc/apt/sources.list
```

eg.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick main restricted

to

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted

or

deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) maverick main restricted

---

### Post by fdcoiea on 2011-02-24
> **Artificial Intelligence said:**
> I guess "my" is Malaysia. There could be some troubles with their servers there. Try change to another server by change to another country or erase **my.** infront of the source line in your source list.
```
gksu gedit /etc/apt/sources.list
```

eg.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick main restricted

to

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted

or

deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) maverick main restricted


Thanks! This solve the same problem I have with this person who posted this. Seriously "my" gave a tones of issue.

---

### Post by hengchuen on 2011-02-27
> **Artificial Intelligence said:**
> I guess "my" is Malaysia. There could be some troubles with their servers there. Try change to another server by change to another country or erase **my.** infront of the source line in your source list.
```
gksu gedit /etc/apt/sources.list
```eg.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick main restricted

to

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted

or

deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) maverick main restricted

Thank you for helping me to solve the problem ^^

---

### Post by Jakobskadkaer on 2012-03-21
I have this exact same problem in the 11.10 version.
I get this after running 'sudo apt-get update && sudo apt-get upgrade'

[PHP]Ign http://security.ubuntu.com oneiric-security InRelease
Ign http://dk.archive.ubuntu.com oneiric InRelease                            
Ign http://dk.archive.ubuntu.com oneiric-updates InRelease                    
Ign http://dk.archive.ubuntu.com oneiric-backports InRelease
Ign http://extras.ubuntu.com oneiric InRelease 
Hit http://security.ubuntu.com oneiric-security Release.gpg
Hit http://dk.archive.ubuntu.com oneiric Release.gpg
Hit http://dk.archive.ubuntu.com oneiric-updates Release.gpg         
Hit http://dk.archive.ubuntu.com oneiric-backports Release.gpg       
Hit http://security.ubuntu.com oneiric-security Release              
Hit http://extras.ubuntu.com oneiric Release.gpg                     
Hit http://dk.archive.ubuntu.com oneiric Release                      
Hit http://dk.archive.ubuntu.com oneiric-updates Release                       
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://dk.archive.ubuntu.com oneiric-backports Release            
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://dk.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://dk.archive.ubuntu.com oneiric/multiverse i386 Packages     
Hit http://dk.archive.ubuntu.com oneiric/main TranslationIndex        
Hit http://dk.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://dk.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://dk.archive.ubuntu.com oneiric/universe TranslationIndex   
Hit http://dk.archive.ubuntu.com oneiric-updates/main Sources        
Hit http://dk.archive.ubuntu.com oneiric-updates/restricted Sources  
Hit http://dk.archive.ubuntu.com oneiric-updates/universe Sources    
Hit http://dk.archive.ubuntu.com oneiric-updates/multiverse Sources  
Hit http://dk.archive.ubuntu.com oneiric-updates/main i386 Packages  
Hit http://dk.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://dk.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://extras.ubuntu.com oneiric/main Sources                    
Hit http://security.ubuntu.com oneiric-security/restricted Sources   
Hit http://security.ubuntu.com oneiric-security/universe Sources
Hit http://security.ubuntu.com oneiric-security/multiverse Sources   
Hit http://security.ubuntu.com oneiric-security/main i386 Packages   
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://dk.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://dk.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://dk.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://dk.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://dk.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://extras.ubuntu.com oneiric/main i386 Packages              
Ign http://extras.ubuntu.com oneiric/main TranslationIndex           
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://security.ubuntu.com oneiric-security/main Translation-en  
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Get:1 http://dk.archive.ubuntu.com oneiric/main Sources [1,095 kB]   
Hit http://dk.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://extras.ubuntu.com oneiric/main Translation-en
Get:2 http://dk.archive.ubuntu.com oneiric/universe Sources [5,792 kB]
Hit http://dk.archive.ubuntu.com oneiric/multiverse Sources
Get:3 http://dk.archive.ubuntu.com oneiric/main i386 Packages [1,583 kB]
Hit http://dk.archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://dk.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://dk.archive.ubuntu.com oneiric-backports/universe Sources
Hit http://dk.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://dk.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://dk.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://dk.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://dk.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://dk.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://dk.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://dk.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://dk.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://dk.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://dk.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://dk.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://dk.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://dk.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://dk.archive.ubuntu.com oneiric-backports/main Sources
Hit http://dk.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://dk.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://dk.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://dk.archive.ubuntu.com oneiric-backports/universe Translation-en
Get:4 http://dk.archive.ubuntu.com oneiric/main Translation-en [861 kB]
Get:5 http://dk.archive.ubuntu.com oneiric/universe Translation-en [3,919 kB]
Hit http://dk.archive.ubuntu.com oneiric-updates/main Translation-en
Fetched 5 B in 1s (2 B/s)      
W: Failed to fetch gzip:/var/lib/apt/lists/partial/dk.archive.ubuntu.com_ubuntu_dists_oneiric_main_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/dk.archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/dk.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/dk.archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Translation-en  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/dk.archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Translation-en  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/PHP]

---

### Post by coffeecat on 2012-03-21
Old thread closed.

@Jakobskadkaer, I see that you have started your own thread with the identical post.

---

