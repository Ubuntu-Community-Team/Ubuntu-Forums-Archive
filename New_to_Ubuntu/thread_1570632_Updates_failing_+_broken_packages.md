---
title: "Updates failing + broken packages :/"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by hennnerz on 2010-09-08
Hi, total n00b here, so please be gentle!

I get this message when trying to update via Update Manager:
```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```

Then the text box below says:

> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.

I can't run programs through Wine and I think thats because I cant update it?

Any help please? :)

---

### Post by arochester on 2010-09-08
Open a Terminal.

Issue the command: gksudo gedit /etc/apt/source.list

Copy and paste the results here

---

### Post by hennnerz on 2010-09-08
It opened the source.list file with gedit. But this file was blank :-S

---

### Post by plucky on 2010-09-08
> **arochester said:**
> Open a Terminal.

Issue the command: gksudo gedit /etc/apt/source.list

Copy and paste the results here

It is sources.list not source.list

Use ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by hennnerz on 2010-09-08
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

---

### Post by techningeer on 2010-09-08
Run "aptitude upgrade" then run "apt-get update" then run "aptitude upgrade" again.

---

### Post by DougieFresh4U on 2010-09-08
From terminal I would go through the following:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```

Also in the** Software Sources**, which would be under Administration>Software Sources,  what do you have checked for updating?

---

### Post by hennnerz on 2010-09-08
> **techningeer said:**
> Run "aptitude upgrade" then run "apt-get  update" then run "aptitude upgrade" again.

This first run came up with the following:

hen@hen:~$ aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by plucky on 2010-09-08
```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
[color=red]deb http://archive.ubuntu.com/ubuntu/ hardy multiverse[/color]
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted 
```

Put a # in front of the line in red and then reload and see what happens.

Good Luck

---

### Post by hennnerz on 2010-09-08
> **DougieFresh4U said:**
> From terminal I would go through the following:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```Also in the** Software Sources**, which would be under Administration>Software Sources,  what do you have checked for updating?

I tried this, looks like some worked, some didn't:

```
hen@hen:~$ sudo apt-get update
[sudo] password for hen: 
Hit http://dell-mini.archive.canonical.com hardy Release.gpg                   
Ign http://dell-mini.archive.canonical.com hardy/main Translation-en_GB        
Ign http://dell-mini.archive.canonical.com hardy/universe Translation-en_GB
Ign http://dell-mini.archive.canonical.com hardy/multiverse Translation-en_GB
Ign http://dell-mini.archive.canonical.com hardy/restricted Translation-en_GB
Hit http://dell-mini.archive.canonical.com hardy-updates Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-updates/main Translation-en_GB
Ign http://dell-mini.archive.canonical.com hardy-updates/universe Translation-en_GB
Ign http://dell-mini.archive.canonical.com hardy-updates/multiverse Translation-en_GB
Ign http://dell-mini.archive.canonical.com hardy-updates/restricted Translation-en_GB
Hit http://dell-mini.archive.canonical.com hardy-security Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-security/main Translation-en_GB
Ign http://dell-mini.archive.canonical.com hardy-security/universe Translation-en_GB
Ign http://dell-mini.archive.canonical.com hardy-security/multiverse Translation-en_GB
Ign http://dell-mini.archive.canonical.com hardy-security/restricted Translation-en_GB
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Translation-en_GB
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Translation-en_GB
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Translation-en_GB
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Translation-en_GB
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Translation-en_GB
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Translation-en_GB
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Translation-en_GB
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Translation-en_GB
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/public Translation-en_GB
Hit http://dell-mini.archive.canonical.com hardy Release    
Hit http://dell-mini.archive.canonical.com hardy-updates Release
Hit http://dell-mini.archive.canonical.com hardy-security Release
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release          
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release
Hit http://dell-mini.archive.canonical.com hardy/main Packages                 
Hit http://dell-mini.archive.canonical.com hardy/universe Packages
Hit http://dell-mini.archive.canonical.com hardy/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy/main Sources
Hit http://dell-mini.archive.canonical.com hardy/universe Sources
Hit http://dell-mini.archive.canonical.com hardy/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/main Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/main Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-security/main Packages
Hit http://dell-mini.archive.canonical.com hardy-security/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-security/main Sources
Hit http://dell-mini.archive.canonical.com hardy-security/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/public Packages 
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/public Sources  
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Hit http://archive.ubuntu.com hardy Release.gpg
Hit http://archive.ubuntu.com hardy/multiverse Translation-en_GB
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Hit http://archive.ubuntu.com hardy Release    
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Ign http://archive.ubuntu.com hardy/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Err http://archive.ubuntu.com hardy/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
hen@hen:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hen@hen:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmtp7 obex-data-server libbeagle1 libnm-util0 libdns35
  libpt-1.10.10-plugins-alsa libggzmod4 libsqlite0 libsgutils1 libpt-1.10.10
  libgpod3 guile-1.6-libs libmusicbrainz4c2a dhcdbd libggz2 libqthreads-12
  libopal-2.2 libgpod-common firefox-3.0-gnome-support libggzcore9
  xulrunner-1.9-gnome-support libisc32 libguile-ltdl-1 transmission-common
  libopenobex1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hen@hen:~$ sudo dpkg --configure -a
```

---

### Post by beew on 2010-09-08
Just ignore it and try later. It just means that it can't connect to the server that hosts the repository, maybe it is down temporarily or you have a bad connection. Nothing to worry about, happens to me all the time because of weak wireless.

---

### Post by beew on 2010-09-08
> Open a Terminal.

Issue the command: gksudo gedit /etc/apt/source.list

Copy and paste the results here

Why don't you just tell him to open synaptic, run the update again? Either the issue fixes itself or he will find the name of the repository(repositories) in question from the error message.

The issue will resolve itself and you don't need to do anything and it wouldn't interfere with other updates if only that one repo is not available for some reasons,--as oppose to say losing internet connection then obviously any upgrade will fail. 

If the message bothers him he can disable the repository in question by simply opening synaptic, then go to setting > repositories and uncheck the box of the repository in question and then reload. But if he wants the update he had better not do that, or make sure that he remembers to check the box again later.

I see absolutely no reason that he has to go to the terminal and edit the source list, and it is* sources.list*, btw. :)

---

### Post by beew on 2010-09-08
DougieFlesh4u
> From terminal I would go through the following:
```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```



I don't think so. This is to fix broken packages, but the OP's error message doesn't say he has broken packages, just that he couldn't connect to the repo (or more precisely cannot get some packages from the repo) so nothing has been downloaded, you only get broken packages when something is half installed and the installation ends abruptly.

---

### Post by Rasa1111 on 2010-09-08
you're not my buddy hennerz from the vault are you :?:  lol

---

### Post by hennnerz on 2010-09-09
> **plucky said:**
> ```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
[COLOR=red]deb http://archive.ubuntu.com/ubuntu/ hardy multiverse[/COLOR]
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted 
```Put a # in front of the line in red and then reload and see what happens.

Good Luck

I did this, not sure if anything changed tho and i may have inadvertently changed it back through all the updates etc

---

### Post by hennnerz on 2010-09-09
> **DougieFresh4U said:**
> From terminal I would go through the following:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```Also in the** Software Sources**, which would be under Administration>Software Sources,  what do you have checked for updating?

Just tried this again and it all worked without any failures now, which is promising!

Under software sources:

[IMG]http://i205.photobucket.com/albums/bb23/heners_galore/Screenshot.png[/IMG]

---

### Post by hennnerz on 2010-09-09
> **Rasa1111 said:**
> you're not my buddy hennerz from the vault are you :?:  lol

Not afaik!

---

### Post by hennnerz on 2010-09-09
> **beew said:**
> DougieFlesh4u


I don't think so. This is to fix broken packages, but the OP's error message doesn't say he has broken packages, just that he couldn't connect to the repo (or more precisely cannot get some packages from the repo) so nothing has been downloaded, you only get broken packages when something is half installed and the installation ends abruptly.

Yeah, while the error message doesn't say about broken packages, i did get an alert when trying to fix everything through updating things saying there was a broken package, so just thought it could be causing the problems!

---

### Post by beew on 2010-09-09
OK, you could have fixed the broken package from Synaptic as well. There is a "fix broken package" option on the left. I am at work so I can't tell you the exact word but you can find it easily.  Nice that it all works out. :)

---

### Post by hennnerz on 2010-09-09
Yeah, when I clicked on the broken filter, there was nothing that came up, so presumably it's ok.

I have a feeling i am still running an old version of ubuntu though, because when i went to install skype i got an error message in package installer:

> Error: Dependency is not satisfiable:libasound2

From what i can understand this comes about because of a descrepency between the different versions of ubuntu as skype uses the latest version for its latest releases?

Anyway i can check what i am running and then upgrade?

---

### Post by DougieFresh4U on 2010-09-09
> **hennnerz said:**
> Just tried this again and it all worked without any failures now, which is promising!

Under software sources:

[IMG]http://i205.photobucket.com/albums/bb23/heners_galore/Screenshot.png[/IMG]

Just being curious, what is all checked under 'Updates' in your Software Sources?

---

### Post by hennnerz on 2010-09-09
[IMG]http://i205.photobucket.com/albums/bb23/heners_galore/Screenshot-1.png[/IMG]

---

### Post by DougieFresh4U on 2010-09-09
Sorry,my mistake I meant 'Ubuntu Software'

---

### Post by hennnerz on 2010-09-09
As far as i know i dont have those options, the screenshot i posted shows all the options i have under software sources :/

---

### Post by plucky on 2010-09-10
> **DougieFresh4U said:**
> Sorry,my mistake I meant 'Ubuntu Software'

From post #5 ```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
```

This is not normal Ubuntu but the version built for the dell-mini which I think uses the atom processor.

---

### Post by hennnerz on 2010-09-10
> **plucky said:**
> From post #5 ```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
```This is not normal Ubuntu but the version built for the dell-mini which I think uses the atom processor.

Ah yeah, you're right. I forgot to mention that!

---

### Post by hennnerz on 2010-09-11
> **hennnerz said:**
> Yeah, when I clicked on the broken filter, there was nothing that came up, so presumably it's ok.

I have a feeling i am still running an old version of ubuntu though, because when i went to install skype i got an error message in package installer:

 			 				> Error: Dependency is not satisfiable:libasound2 			 		

From what i can understand this comes about because of a descrepency between the different versions of ubuntu as skype uses the latest version for its latest releases?

Anyway i can check what i am running and then upgrade?

Any ideas on this please? When i tried the windows version of skype via wine, it crashed as i went to sign in :/

---

### Post by Rasa1111 on 2010-09-12
go to **System> Administration~** and open **System monitor**. 
Then click the "system" tab, on the left, that will tell you which version you're running.

---

