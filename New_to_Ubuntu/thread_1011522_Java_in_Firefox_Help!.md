---
title: "Java in Firefox Help!"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by ArcticWalrus on 2008-12-14
How do I install Java in to Firefox? Specifically I wanted to play Chess and Backgammon on Yahoo games and tried to execute the most obvious methods which occurred to me but as a tremendous noob I failed. I tried searching for information but came up with nothing. Sorry for the stupid question but please help.

---

### Post by ArcticWalrus on 2008-12-14
Help please

---

### Post by taurus on 2008-12-14
Open a terminal and type in one line at a time.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the licensing screen, press the Tab key to highlight the <OK> and Return to accept it.

Now, restart firefox.

---

### Post by ArcticWalrus on 2008-12-14
> **taurus said:**
> Open a terminal and type in one line at a time.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the licensing screen, press the Tab key to highlight the <OK> and Return to accept it.

Now, restart firefox.

Thank you... I had all but given up

---

### Post by nicklikesfire on 2008-12-16
Hello, so I've been trying this, and for some reason I can't find the plugin! I've tried using synaptic too.

> Reading package lists... Done
nick@burn-desktop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
nick@burn-desktop:~$ 


Any ideas?

---

### Post by taurus on 2008-12-16
> **nicklikesfire said:**
> Hello, so I've been trying this, and for some reason I can't find the plugin! I've tried using synaptic too.

Any ideas?

Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by nicklikesfire on 2008-12-16
Sure thing, thanks for the quick reply.

> nick@burn-desktop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
nick@burn-desktop:~$ 



---

### Post by taurus on 2008-12-16
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the # in blue.

```

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
**[COLOR="Blue"]#[/COLOR]**deb http://archive.canonical.com/ubuntu intrepid partner
**[COLOR="Blue"]#[/COLOR]**deb-src http://archive.canonical.com/ubuntu intrepid partner

```
Save it and close down gedit editing window.  Then run

```
sudo apt-get update
sudo apt-get install sun-java6-plugin
```

---

### Post by nicklikesfire on 2008-12-16
This didn't work,it's possible I messed it up, but I have the same problem still.

> nick@burn-desktop:~$ gksudo gedit /etc/apt/sources.list
nick@burn-desktop:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg [189B]                 
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Get:2 [http://archive.canonical.com](http://archive.canonical.com) intrepid Release [7007B]                    
Get:3 [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages [14B]             
Get:4 [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources [446B]             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US         
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg [189B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                              
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release [51.2kB]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources                   
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages [254kB]      
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages [3852B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources [79.3kB]      
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources [1169B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages [29.2kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources [5727B]  
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages [1922B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources [803B] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Fetched 435kB in 2min1s (3578B/s)
Reading package lists... Done
nick@burn-desktop:~$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
nick@burn-desktop:~$ gksudo gedit /etc/apt/sources.list
nick@burn-desktop:~$ 


I'm running the AMD64 version of Intrepid, if that makes any difference (sorry I didn't say that to begin with).

---

### Post by taurus on 2008-12-16
I don't think there is a java plugin for 64bit unless I was wrong on that.

---

### Post by nicklikesfire on 2008-12-16
Sun Provides 64-bit Java plugin for Linux:

[http://www.phoronix.com/scan.php?page=news_item&px=NjkyOQ](http://www.phoronix.com/scan.php?page=news_item&px=NjkyOQ)

I have no idea what to do with this now, I guess I had just assumed it would work. hmm. Any help? Sorry I spaced on that before.

---

### Post by taurus on 2008-12-16
In that case, you want to download the .bin version.

[http://www.java.net/download/jdk6/6u12/promoted/b02/binaries/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin](http://www.java.net/download/jdk6/6u12/promoted/b02/binaries/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin)

it's probably saved to your ~/Desktop so you can move it to /opt and unpack it from there.

```
cd ~/Desktop
chmod 755 jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
sudo mv jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin /opt
sudo ./jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
```
That would create a new java directory and in there, there should be a plugin which you can link it to your ~/.mozilla or /usr/share/mozilla.

It's best to remove the version from the repos.

---

### Post by jamesstansell on 2008-12-16
> **nicklikesfire said:**
> Sun Provides 64-bit Java plugin for Linux:

[http://www.phoronix.com/scan.php?page=news_item&px=NjkyOQ](http://www.phoronix.com/scan.php?page=news_item&px=NjkyOQ)

I have no idea what to do with this now, I guess I had just assumed it would work. hmm. Any help? Sorry I spaced on that before.

Note that it's not an actual release.  It's an "early access" release which means it's being provided for testing only right now.  Sun plans to release java 6u12 in February.

For a supported java plugin right now you'll want the icedtea6-plugin package from the main repository.  There's information in a sticky in the 64-bit forum. (This java version is 95% Sun's code, but the plugin is not completely compatible with Sun's browser plugin; it mostly depends on how the applet was written.)

---

