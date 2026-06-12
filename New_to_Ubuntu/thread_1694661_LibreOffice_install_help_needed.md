---
title: "LibreOffice install help needed"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by DayLite on 2011-02-24
I was helping a friend install LibreOffice on his Ubuntu10.04. This is what I told him to copy and paste in his terminal.

**sudo add-apt-repository         ppa:libreoffice/ppa**
           **sudo apt-get update         && sudo apt-get install libreoffice**
       [B]sudo apt-get install libreoffice-gnome
He **c**ouldn't find it after install and in Update Manager it said something was wrong and it could only do a partial update. He said NO.

I then had him to try the install command again in the terminal and this is what came up.

[/B]```
paul@paul-desktop:~$ sudo apt-get update && sudo apt-get install libreoffice
[sudo] password for paul: 
Sorry, try again.
[sudo] password for paul: 
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release.gpg
Ign [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release.gpg                                 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://archive.canonical.com]("http://archive.canonical.com/") lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://ppa.launchpad.net/osmoma/rec-applet/ubuntu/](http://ppa.launchpad.net/osmoma/rec-applet/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/anonbeat/guayadeque/ubuntu/](http://ppa.launchpad.net/anonbeat/guayadeque/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/](http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/) lucid/main Translation-en_US
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") lucid Release.gpg                            
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release.gpg                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security Release                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com]("http://archive.canonical.com/") lucid Release                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release                                     
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release                                     
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release                                     
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release                                     
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid Release                                 
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release                                     
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release                                     
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates Release                         
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/main Packages                    
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release                                     
Hit [http://archive.canonical.com]("http://archive.canonical.com/") lucid/partner Packages                        
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/restricted Packages              
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/universe Packages                
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/multiverse Packages              
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid/main Packages                               
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid/main Packages                               
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid/main Packages                               
Hit [http://archive.canonical.com]("http://archive.canonical.com/") lucid/partner Sources                         
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid/main Packages                           
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US  
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid/main Packages                               
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid/main Packages                               
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid/main Packages                               
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid/main Packages                               
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid/universe Packages                       
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid/multiverse Packages                     
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates/main Packages                   
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates/universe Packages               
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") lucid-updates/multiverse Packages
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") lucid Release
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") lucid/free Packages
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") lucid/non-free Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libreoffice: Depends: libreoffice-core (= 1:3.3.0-1lucid1) but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-report-builder-bin but it is not going to be installed
               Depends: libreoffice-filter-mobiledev but it is not going to be installed
               Depends: libreoffice-java-common (>= 1:3.3.0~) but it is not going to be installed
E: Broken packages
paul@paul-desktop:~$ 

```

Can you help figure this out?

---

### Post by Joeb454 on 2011-02-24
According to [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa) at 00:17 (UTC), the libreoffice package has been waiting to build for 6.5 hours.

That probably explains why you're getting the unmet dependencies error. All I can think to advise at this stage is to wait a little longer. 

It's probably also worth checking that libreoffice has built correctly before trying again (use the link above, it shows the status on the right).

---

### Post by DayLite on 2011-02-24
> **Joeb454 said:**
> According to [https://launchpad.net/~libreoffice/+archive/ppa]("https://launchpad.net/%7Elibreoffice/+archive/ppa") at 00:17 (UTC), the libreoffice package has been waiting to build for 6.5 hours.

That probably explains why you're getting the unmet dependencies error. All I can think to advise at this stage is to wait a little longer. 

It's probably also worth checking that libreoffice has built correctly before trying again (use the link above, it shows the status on the right).

Thanks for posting. I have LibreOffice on my computers with no problems. I installed mine around a month ago. Are you telling me that his request (in the terminal) was for a different build than mine?

---

### Post by paulofeastman on 2011-02-24
Hi folks
Trying to install libreoffice from update Manager

This is the message I get:

Not all updates can be installed
Run a partial upgrade, to install as many updates as possible

This can be caused by:
A previous upgrade which didn't complete
Problems with some of the installed software
Unofficial software packages not provided by ubuntu
Normal changes of a pre-release version of ubuntu

Partial upgrade or close this message

paulof eastman

---

