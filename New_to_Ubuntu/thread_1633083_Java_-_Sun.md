---
title: "Java - Sun"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by sammiev on 2010-11-28
Hi Folks, read many post on java and have been reading 100s of post on it. Went to install and all looked great with no errors and updates all went perfect. Went to the java site and it says java not installed, then tried to install it again and it said I had the latest updates. So I checked the FF Browser to confirm that java was turn on which it was. 

 sam@ubuntu:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-fonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Thanks for any help. :)

---

### Post by Miljet on 2010-11-28
You might want to check Synaptic Package Manager to see if Icedtea java is installed. If it is, uninstall it. It often conflicts with Sun java.

---

### Post by GregBrannon on 2010-11-28
What 'Java site' are you going to that reports you don't have Java installed?  Post a link to the site and the exact error message.  Have you tried going to the same site with a different browser?

Also type

> java -version

and report exactly the response.

---

### Post by sammiev on 2010-11-28
Hi Miljet, yes Icedtea java uninstall but thanks for the input, it may help others. :)

---

### Post by sammiev on 2010-11-28
doubled checked if Icedtea java was again and it's removed from the Synaptic Package Manager. Does seem to point to it. :(

Hi GregBrannon, > java -version reports as this. Listed the whole screen. Thanks Hope this helps.

sam@ubuntu:~$ sudo add-apt-repository 'deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner'
[sudo] password for sam: 
sam@ubuntu:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Reading package lists... Done
sam@ubuntu:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-fonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sam@ubuntu:~$ java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.1) (6b20-1.9.1-1ubuntu3)
OpenJDK Server VM (build 17.0-b16, mixed mode)
sam@ubuntu:~$

---

### Post by beew on 2010-11-29
Ubuntu uses OpenJdk as its default java. Even if Sun-java is installed you still have to set it as the default.

You can either remove the OpenJdk packages or in the terminal type
```

sudo update-java-alternatives -s java-6-sun
```

---

### Post by sammiev on 2010-11-29
Hi beew and thank you sir! Worked great. :)

---

