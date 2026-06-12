---
title: "Problems with software installation (Im a real newb)"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by cello on 2009-07-22
So from what I understand, to install a new software I have to download the needed packages for it from a repository, but no matter which server I use I get this error:
---------
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://ftp.linux.edu.lv/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://ftp.linux.edu.lv/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.linux.edu.lv/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://ftp.linux.edu.lv/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.linux.edu.lv/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://ftp.linux.edu.lv/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.linux.edu.lv/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://ftp.linux.edu.lv/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) 404 Not Found
---------
So I cant even get the list of packages.
Anyone has any ideas of what Im doing wrong? :confused:

---

### Post by Sidewinder1 on 2009-07-22
First of all, WELCOME to Ubuntu Forums!!!
I prefer to use Synaptic Package Manager (included natively with ubuntu).
Go to: System---->Administration---->Synaptic Package Manager....
You'll find about 25,000 software programs that can be downloaded and installed by Synaptic. The beauty is that it handles all of the dependencies for you, automatically.

HTH,
Side

---

### Post by VCoolio on 2009-07-22
Those are Gutsy Gibbon (Ubuntu 7.10) repos. Gutsy Gibbon is no longer supported. If you use Gutsy, either upgrade to Hardy (long term support version, Ubuntu 8.04) or even Jaunty (latest) or find the archived repos for Gutsy. If you don't use Gutsy, enable the proper repos for your Ubuntu version.
Check [this thread]("http://ubuntuforums.org/showthread.php?t=1133291").

---

### Post by mapes12 on 2009-07-22
You can check what repos you are contacting by having a look in System>Administration>Software Sources. If you want to see the file that holds this data it's in Places>Computer>etc>apt>sources.list If you're new to Ubu then use the GUI (Software Sources) to make any changes.

Also, for media software check out: [http://www.medibuntu.org/](http://www.medibuntu.org/)

And this is an easy to follow HowTo: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by snowpine on 2009-07-22
VCoolio is correct; you are using an old, unsupported version of Ubuntu.

I recommend you re-install using the current version (9.04 Jaunty Jackolope).

---

### Post by credobyte on 2009-07-22
Gusty is dead - you should be using Jaunty ( or at least 8.04 LTS ) ;)

---

### Post by cello on 2009-07-22
Hey, thanks a lot guys. Im new to ubuntu and I got this pc with it and thats why it has the old version, I didnt set it up myself, but its a fresh installation. I managed to update to 8.04, but now I get this error when I try to open synaptic package manager:
[U]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/U]

Also looks like this prevents me from updating to the newer 9 version. :/
Any suggestions for this.

---

### Post by snowpine on 2009-07-22
Personally, I would never keep an existing install on a used computer (you never know what "tweaks" the previous owner made). 

If you want to try and salvage your current install, try the terminal command:

```
sudo dpkg --configure -a
```

and see what happens.

---

### Post by cello on 2009-07-22
Yeah, I would reinstall at some point as well, but atm I prefer to get it working and get used to it. yeah, looks like its working now, thanks a lot all! :)

---

### Post by cello on 2009-07-22
Okey, sorry for posting a doublepost, but one small question. I want to test the quake wars game (which has linux version), but the download gives me a file .run. How can I install something like this and what it is, I cant really open it with GDebi package installer hmm?

---

### Post by mapes12 on 2009-07-23
This HowTo may help:

[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

