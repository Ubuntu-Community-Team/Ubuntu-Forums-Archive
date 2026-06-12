---
title: "updates not authenticated"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by paul88 on 2010-01-17
I have gone to do the software up date and got a message when going to install.

Is it safe to install the updates that are not authenticated? as it is saying that an individual can damage files for take control of my machine.

Does it just mean that there is a digital signature missing?

or have I enabled access to some unverified packages?

Will it harm my computer if I install them?

Thank you

---

### Post by audiomick on 2010-01-17
It most likely means there is a signature missing. If you disable any repositories that you may have installed that aren't from Ubuntu, maybe the error will stop. Then you can see what was causing the problem and see about getting the signature.

---

### Post by fooman on 2010-01-17
like audiomick said,  probably a GPG signature error/warning.....open a terminal (applications > accessories > terminal) and type or copy/paste the following into it:

```
sudo apt-get update
```press enter,  then look for the error at the end of the output.  copy and paste the entire error back here and we should be able to show you a fix.

---

### Post by paul88 on 2010-01-17
Here is the output

```
paul@paul-laptop:~$ sudo apt-get update
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_GB          
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_GB    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_GB      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_GB    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_GB              
Hit http://archive.canonical.com karmic Release                                
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Sources                    
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
62% [Connecting to gb.archive.ubuntu.com (2a01:450:10:1::10)]       
```

it doesn't seem to move from 62%

---

