---
title: "Update manager is not finding updates"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by amenotatsujin on 2009-02-08
My Update Manager is not finding any updates. I'm using Firefox 3.0.5, so I know there's at least one update available. I was not able to use the update manager before, and I used this post to solve it:
[http://ubuntuforums.org/showthread.php?t=1054906#9](http://ubuntuforums.org/showthread.php?t=1054906#9)

Now it acts like there are no updates. I do not get an error message. I've also tried sudo apt-get update and sudo apt-get upgrade, and I still have the problem.

---

### Post by Temposs on 2009-02-08
What makes you think there should be an update? Firefox 3.0.5 is the current version for Ubuntu 8.10.

---

### Post by hyper_ch on 2009-02-08
updates in the programs themselves aren't automatically included in the repositories. First - if at all - they have to be implemented. During a release cycle this is mostly the case if there's a security bug... just versioning updates normally won't be included.

---

### Post by ugm6hr on 2009-02-08
> **amenotatsujin said:**
> Now it acts like there are no updates. I do not get an error message. I've also tried **sudo apt-get update** and **sudo apt-get upgrade**, and I still have the problem.

Post the output from these commands.

---

### Post by amenotatsujin on 2009-02-08
[http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/)
This says 3.0.6 is the latest version.


***sudo apt-get update***
```
Hit http://us.archive.ubuntu.com intrepid Release.gpg
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US               
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US        
Hit http://packages.medibuntu.org hardy Release.gpg                            
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US         
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US           
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US         
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg                  
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US       
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US   
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US 
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US  
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US  
Hit http://security.ubuntu.com intrepid-security Release                       
Hit http://us.archive.ubuntu.com intrepid Release                              
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://packages.medibuntu.org hardy Release                                
Hit http://us.archive.ubuntu.com intrepid-updates Release                      
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://us.archive.ubuntu.com intrepid/main Packages                        
Hit http://us.archive.ubuntu.com intrepid/restricted Packages                  
Hit http://us.archive.ubuntu.com intrepid/main Sources                         
Hit http://us.archive.ubuntu.com intrepid/restricted Sources                   
Hit http://us.archive.ubuntu.com intrepid/universe Packages                    
Hit http://security.ubuntu.com intrepid-security/restricted Packages           
Hit http://packages.medibuntu.org hardy/non-free Packages                      
Hit http://us.archive.ubuntu.com intrepid/universe Sources                     
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages                  
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://ppa.launchpad.net intrepid Release.gpg
Ign http://ppa.launchpad.net intrepid/main Translation-en_US
Hit http://ppa.launchpad.net intrepid Release
Ign http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Packages
Reading package lists... Done
```

***sudo apt-get upgrade***
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Temposs on 2009-02-08
The latest released version of Firefox is 3.0.6, but that doesn't mean Ubuntu is going to release version 3.0.6 to the repositories.

Currently Ubuntu 8.10 is using version 3.0.5.

If you wish to try upgrading manually to 3.0.6, feel free, although the best thing is to use the version supplied in the repositories, which currently is 3.0.5.

---

### Post by amenotatsujin on 2009-02-08
I suppose my limited knowledge shows, but I haven't had any updates in about two weeks.

---

### Post by Temposs on 2009-02-08
One thing you might change is your medibuntu repository entry. You're set to get the hardy versions of the medibuntu programs. Look at these lines from your output:

```
Hit http://packages.medibuntu.org hardy/non-free Packages
```

Open System->Administration->Software Sources, then click "Third Party Sources", then edit your medibuntu entries and replace "hardy" with "intrepid".

---

### Post by amenotatsujin on 2009-02-08
Thank you, everything is working fine now.

---

