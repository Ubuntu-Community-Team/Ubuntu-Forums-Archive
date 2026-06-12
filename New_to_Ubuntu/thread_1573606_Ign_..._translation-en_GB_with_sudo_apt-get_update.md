---
title: "Ign ... translation-en_GB with sudo apt-get update"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by tellapu on 2010-09-13
Hi!

When I update the repositories, e.g sudo apt-get update, a lot of Ign ... translation-en_GB appear, also in the Software sources: download translation-en_GB ubuntu failed. The system seems not to be bothered, but I would like to have only "Hit"s.

Any ideas? Thanks.

Here is what I get in the terminal with sudo apt-get update:
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                                                                   
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB                                    
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB        
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB          
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg                                               
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB                            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB                      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB                        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Get: 1 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]                                       
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_GB                                     
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_GB  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_GB
Get: 2 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages Sources                            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Sources                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages                                                       
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages [5,448kB]                                                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Sources                                                                           
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages [180kB]                                                   
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [295kB]                                                       
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages [3,252B]                                                    
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages [113kB]                                                               
Get: 8 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages                                                                            
Get: 9 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages [68.5kB]                                                                 
Get: 10 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages [14B]                                                                
Get: 11 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages [34.2kB]                                                   
Get: 12 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages [1,998B]

---

### Post by jgrocha on 2010-11-01
Same here, but worst.

Some repositories are interely ignored.

sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
sudo apt-get update

(...)
Ign [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu/](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu/](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu/) maverick/main Translation-pt

(...)

This happens with Ubuntu 10.10 Maverick. Never experienced this 'feature' before.

---

### Post by jgrocha on 2010-11-01
Since it seems related to the locale settings, I've tried do disable
I've tried do disable Translations in:
/etc/apt/apt.conf.d/10periodic, like:
// APT::Acquire::Languages=none;
APT::Acquire::Languages { "en"; "none" };
// Deprecated
// APT::Acquire::Translation "none";
No success, with several variations.

I reported this as a bug.
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/669493](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/669493)

---

### Post by tellapu on 2010-11-04
Thanks for working on this! Hopefully there will be a solution.

---

### Post by cyprys on 2010-11-04
I noticed this long time ago. When you install vanilla there's no such thing as translations in apt-get update dialogue, however, when you start messing around with *System -> Preferences -> Language support* you'll actually set not only locale but also some properties of apt and several other applications (like firefox xul, dictionaries - even when no language support of the given language is set, etc.). This is the problem of *Language support* applet and the bug should be triaged to this section of launchpad.

After you remove given languages configuration you'll see those translations are being ignored during the update. IMO those should be simply removed from configuration but, for some reason, they are not. Language support has many many issues and should be strongly revised (it tries to do to many things for the user leaving to few options for more advanced people who wish to had control over, e.g., their apt settings - or whatever else configuration).

OOT: I can't believe there's no topic explaining about how to address this issue stocked somewhere in this forums. I'm trying to find a solution since a year and a half now.

---

### Post by tellapu on 2010-11-04
Hi Cyprys

This is an interesting comment! I learnt something.

Cheers!

---

### Post by cyprys on 2011-08-17
Sorry, it just looked unanswered on my mobile.

---

