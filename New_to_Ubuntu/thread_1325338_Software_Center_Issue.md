---
title: "Software Center Issue"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by estephens25 on 2009-11-13
I'm having an issue where I can't install any apps from Software Center.  SC opens up without any error and I can browse through all of the available apps -- but when I click "Install" nothing happens.  I've let it sit for several minutes but still nothing (thinking maybe I was just impatient).
 
I tried to reboot but no change (that's about the extent of my troubleshooting knowledge).
 
This is a fresh install of 9.10 (installed just two days ago).  No changes or additions have been made since.
 
Let me know if I can provide more info.
 
-Eric

---

### Post by The Funkbomb on 2009-11-13
Go into terminal and type:

```
sudo apt-get update
```

It will run an update and try to connect to the Ubuntu servers.  If that doesn't work, it will tell you that it can't connect to the server.

Then, we'll just pick out a new server for you to use.

---

### Post by estephens25 on 2009-11-13
Ran that command and this is the output:

es46789@es46789-ubuntu:~$ sudo apt-get update
[sudo] password for es46789: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done

---

### Post by The Funkbomb on 2009-11-13
So it is connecting to the servers...  weird.

What about command line installs or through synaptic package manager?  Are they working correctly?

Also, what packages specifically are giving you trouble in Software Center?  All of them?

---

### Post by ukripper on 2009-11-13
After you have done the first update. Try now installing, it should find packages now from repos. Try Ubuntu software center again

---

### Post by estephens25 on 2009-11-13
They seem to be working fine...yes.  If there's something specific I can test let me know.

---

### Post by ukripper on 2009-11-13
> **estephens25 said:**
> They seem to be working fine...yes.  If there's something specific I can test let me know.

try installing ubuntu restricted extras if you haven't installed it already from software center

---

### Post by estephens25 on 2009-11-13
ukripper,
After running the update command above I'm still not able to install packages.  Is that what you were referring to?

---

### Post by ukripper on 2009-11-13
> **estephens25 said:**
> ukripper,
After running the update command above I'm still not able to install packages.  Is that what you were referring to?

yes. Can you run following in terminal:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

See if your packages get updated if any error then post here.

what packages you are trying to install?

---

### Post by estephens25 on 2009-11-13
> **ukripper said:**
> try installing ubuntu restricted extras if you haven't installed it already from software center
Not able to install the "restricted extras" either.

Is there an easy way to remove Software Center and then reload it?

---

### Post by ukripper on 2009-11-13
can you try this package in software center - **htop**

Try to install this.

---

### Post by estephens25 on 2009-11-13
> **ukripper said:**
> can you try this package in software center - **htop**

Try to install this.
I tried installing HTOP and it also wouldn't install.  However I was able to download it from the website and used Synaptic to install it and it worked fine.

Could the software center issue be caused by a firewall blocking the installs from working.  I'd think it would get further than what it's getting.  Basically I click Install and nothing happens.  No errors.

---

### Post by estephens25 on 2009-11-13
> **ukripper said:**
> yes. Can you run following in terminal:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

See if your packages get updated if any error then post here.

what packages you are trying to install?
Ran this also and didn't receive any errors.

---

