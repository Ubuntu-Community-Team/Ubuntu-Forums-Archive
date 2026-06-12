---
title: "Segmentation fault....6%"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by uniqueone-85 on 2011-08-25
For Some reason i get this error message when i try to us install and upgrade in terminal:


cj@Art-Pc:~$ sudo apt-get install 
[sudo] password for cj: 
Segmentation faultsts... 6%
cj@Art-Pc:~$ sudo apt-get upgrade 
Segmentation faultsts... 6%
cj@Art-Pc:~$ sudo apt-get install -f
Segmentation faultsts... 6%
cj@Art-Pc:~$ 

I have no idea how to even diagnose the problem let alone fix it. I was able to run install before and it gave me a list of errors, but now i can't even figure out how to show that.

---

### Post by jerrrys on 2011-08-25
to update in terminal:

sudo apt-get update

sudo apt-get upgrade

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by uniqueone-85 on 2011-08-25
i  tried sudo apt-get update and this is what i got:


Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en              
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Segmentation faultsts... 6%

---

### Post by uniqueone-85 on 2011-08-25
ok i got it fixed jus ran thru the troubleshoot procedure that can be found on this link:

[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

thanks for all your help jerrrys

---

### Post by mhgsys on 2011-08-25
I was just about to send you that..

did 
```
sudo rm /var/cache/apt/*.bin
```
do the trick?

---

