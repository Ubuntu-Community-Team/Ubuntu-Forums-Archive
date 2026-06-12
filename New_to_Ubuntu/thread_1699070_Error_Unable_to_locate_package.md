---
title: "Error: Unable to locate package"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by xptional on 2011-03-03
Whenever I try to install some software, e.g. FlashPlayer, Latex, GoogleChrome, any Multimedia

**E: Unable to locate package**  "  error occurs, since two days, I could not come to install anything, 

Anyhow, internet connection is working well as i am doing websurfing, my emails etc

Could anyone diagnose it please ? thanks

---

### Post by Ben Page on 2011-03-03
Try to install something via Terminal

```
sudo apt-get install someapp
```

but first update your package list by pressing

```
sudo apt-get update
```

Then copy/paste the terminal output you get

---

### Post by xptional on 2011-03-03
Hello :)

            sudo apt-get update      doesn't work as well ...  please help me, Thanks, 

output is below



```
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick Release.gpg                          
  Could not connect to fr.archive.ubuntu.com:80 (88.191.250.131). - connect (110: Connection timed out)
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates Release.gpg                  
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
  Unable to connect to archive.canonical.com:http:
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
  Unable to connect to archive.canonical.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
  Could not connect to extras.ubuntu.com:80 (91.189.88.33). - connect (110: Connection timed out)
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
  Unable to connect to extras.ubuntu.com:http:
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release         
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
  Unable to connect to fr.archive.ubuntu.com:http:
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
  Unable to connect to fr.archive.ubuntu.com:http:
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick Release     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources    
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates Release
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/main Sources 
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/restricted Sources
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/universe Sources
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/main i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/multiverse i386 Packages
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
  Unable to connect to archive.canonical.com:http:
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources     
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/main Sources 
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/restricted Sources
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources     
  Unable to connect to extras.ubuntu.com:http:
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/universe Sources
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/main i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/multiverse i386 Packages
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
  Unable to connect to extras.ubuntu.com:http:
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/main Sources 
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/restricted Sources
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/universe Sources
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/multiverse Sources
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/main i386 Packages
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/restricted i386 Packages
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/universe i386 Packages
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/multiverse i386 Packages
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/main Sources
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/restricted Sources
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/universe Sources
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/multiverse Sources
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/main i386 Packages
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/restricted i386 Packages
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/universe i386 Packages
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.92.167). - connect (110: Connection timed out) [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to fr.archive.ubuntu.com:80 (88.191.250.131). - connect (110: Connection timed out)

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to extras.ubuntu.com:80 (91.189.88.33). - connect (110: Connection timed out)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.92.167). - connect (110: Connection timed out) [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by kirkface8 on 2011-03-03
having the exact same problem as you right now!

---

### Post by kirkface8 on 2011-03-03
au.archive.ubuntu.com/ubuntu/ 

seems to be down


and xptional please use ```

``` tags around outputs in future

---

### Post by Tony.B on 2011-03-03
> **kirkface8 said:**
> .... and xptional please use ```

``` tags around outputs in future
For your guidance, kirkface8 is referring to **code tags**. These are activated by using the Hash Key (#) in the toolbar at the top of the Message Box.

---

### Post by kirkface8 on 2011-03-03
yes!
haha

---

### Post by kirkface8 on 2011-03-03
but back to the problem
my girlfriend just tryed the exact same thing with the same output

is this a au repo issue?

---

### Post by Frogs Hair on 2011-03-03
The U.S. server was doing the same two days ago , give it time .

---

### Post by bapoumba on 2011-03-03
I am using the French repos (same as the OP) and have no issue.

Would you happen to be behind a proxy?

---

### Post by xptional on 2011-03-03
Thanks Tony for tagging help :)

Yes I am using proxy, I work in research laboratory, so alas! i cant escape from proxy :( 

Anyelse idea ? 




Imran

---

### Post by xptional on 2011-03-03
Thanks Tony for tagging help :)

**Yes I am using proxy**, I work in research laboratory, so alas! i cant escape from proxy :( 

Anyelse idea ?

---

### Post by bapoumba on 2011-03-03
[http://ubuntuforums.org/showthread.php?t=83401](http://ubuntuforums.org/showthread.php?t=83401)

Here is a quite extensive tutorial, you'll have to test the solutions depending on your situation.

Alternatively, Synaptic > Settings > Pref > Network tab.

---

### Post by ikt on 2011-03-04
> **kirkface8 said:**
> au.archive.ubuntu.com/ubuntu/ 

seems to be down

How come you don't use any of the other local mirrors?

---

### Post by xptional on 2011-03-05
First I thank you all regarding help :)

Yes it was a problem of proxy where i use internet, I tried some other isp without proxy, it works well, i installed what i want :)

Thanks again

---

### Post by bapoumba on 2011-03-06
Glad to see you solved this out :)

---

