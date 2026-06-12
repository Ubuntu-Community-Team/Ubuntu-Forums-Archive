---
title: "Wine"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by OwNeD on 2009-12-29
When installing wine from ubuntu software center/synaptic package manager, i get Package dependencies cannot be resolved. details :wine ... what can i do to fix this??


 i need to install wine..

---

### Post by codeslicer on 2009-12-29
Well, can you post all the output please?

---

### Post by OwNeD on 2009-12-29
Package dependencies cannot be resolved.This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time. details : wine

---

### Post by codeslicer on 2009-12-29
That is strange. Try going into Applications->Accessories->Terminal and type in:

```
sudo apt-get update
sudo apt-get install wine
```

---

### Post by OwNeD on 2009-12-29
i ran it in the terminal and got this :

Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic Release.gpg
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic/main Translation-en_US                 
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic/universe Translation-en_US         
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic/multiverse Translation-en_US       
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic/main Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic/restricted Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic/main Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic/restricted Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic/universe Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic/universe Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic/multiverse Packages         
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages         
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/main Packages        
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/restricted Packages  
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/main Sources         
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/restricted Sources   
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/universe Packages    
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/universe Sources     
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/multiverse Packages  
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) karmic-updates/multiverse Sources   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Reading package lists... Done

---

### Post by MelDJ on 2009-12-29
does it end there?

---

### Post by OwNeD on 2009-12-29
Yes, it ends there.

---

### Post by MelDJ on 2009-12-29
did you add the wine repo from [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) ?

---

### Post by OwNeD on 2009-12-29
Yes i did add that.

---

### Post by synapsys on 2009-12-29
Try this:

```
sudo apt-get build-dep wine
``` to install all wine's dependencies, then install.

---

### Post by OwNeD on 2009-12-29
i got the same error when trying to install wine from ubuntu software center, but it worked from synaptic package manager. so now wine is installed.. 

  i did "sudo apt-get build-dep wine" in terminal first  then install wine trough synaptic.

Thank you.

---

### Post by wells2429 on 2009-12-29
Well all that just worked for me.  Even on my dual core lappy Ubuntu with wine running Starcraft out performed Windoz Vis*@.  Im am officialy sold.  Getting closer to wiping my Vis*@ partition!!!!!

---

### Post by Flo'Daddy on 2009-12-29
I was getting a dependancy error for ubuntu-tweak; I tried running it while I was online.  I downloaded the program and when I ran it natively it worked for me.  Then I installed wine using ubuntu-tweak and it checked on dependencies and took care of it for me.  

Just posting this for others...I learned it here :)

John

---

