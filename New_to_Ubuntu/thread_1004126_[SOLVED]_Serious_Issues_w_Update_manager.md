---
title: "[SOLVED] Serious Issues w/ Update manager"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by 133794m3r on 2008-12-06
Ok this is what i get when i try to update. It can't update at all and the only way it will show the archives is if i have it set to hardy which is no longer supported. So can someone please explain this to me?
```
Failed to fetch http://archive.canonical.com/ubuntu/dists/Intrepid/partner/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ppa.launchpad.net/pjbroad/ubuntu/dists/Intrepid/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://archive.canonical.com/ubuntu/dists/Intrepid/partner/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/Intrepid/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://wine.budgetdedicated.com/apt/dists/Intrepid/main/binary-i386/Packages.gz  404 Not Found [IP: 81.171.111.184 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by 2hot6ft2 on 2008-12-06
There have been issues with the repos for a while now but usually not all at once. Perhaps they are just off-line for updates. Hardy is LTS so it's still supported and will be for a couple more years.

Try it in terminal
sudo apt-get update
and see what it does.

```
hot6ft2@hot6ft2dsk-desktop:~$ sudo apt-get update
[sudo] password for hot6ft2: 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Get:1 [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty Release.gpg [1722B]                 
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty/all Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty Release                               
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty/all Packages                          
Hit [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty/all Packages                          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages           
Fetched 1722B in 11s (152B/s)                                                  
Reading package lists... Done
```

---

### Post by crazyness003 on 2008-12-06
I read somewhere that changing the Download Server may help with such situations.

Go to system -> Administration -> Software Sources and look at the combo-box labeled "Download from:" 

You can hit other and select a server close to you, or let it find the best one for you by doing a little test. The "Select best server" test takes a couple of minutes, but it calculates which connection is the fastest, and auto-selects it as the one for you. quite helpful. 

Anyway, try that and see what happens.

---

### Post by 2hot6ft2 on 2008-12-06
> **crazyness003 said:**
> I read somewhere that changing the Download Server may help with such situations.

Go to system -> Administration -> Software Sources and look at the combo-box labeled "Download from:" 

You can hit other and select a server close to you, or let it find the best one for you by doing a little test. The "Select best server" test takes a couple of minutes, but it calculates which connection is the fastest, and auto-selects it as the one for you. quite helpful. 

Anyway, try that and see what happens.

Defiantly the way to go. I got stuck on the hardy not being supported part.

---

### Post by crazyness003 on 2008-12-06
i know there are some inconsistencies in the story, but this may be oh help, if not to the OP, to someone else for sure.
Hardy's supported till 2013, no?

---

### Post by 2hot6ft2 on 2008-12-06
> **crazyness003 said:**
> i know there are some inconsistencies in the story, but this may be oh help, if not to the OP, to someone else for sure.
Hardy's supported till 2013, no?

I thought it was a 3 year LTS but I'm not sure so either 2011 or 2013 either way it's still supported now. Doesn't really help since the OP is on 8.10 Intrepid.

---

### Post by crazyness003 on 2008-12-06
yeah, but the changing of the download server had worked for me before (in gutsy), maybe the same problem.

---

### Post by 133794m3r on 2008-12-07
Ok i did the chose best server thing and i got this when i tried to run update manager.
```
Failed to fetch http://archive.canonical.com/ubuntu/dists/Intrepid/partner/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/Intrepid/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.canonical.com/ubuntu/dists/Intrepid/partner/source/Sources.gz  404 Not Found
Failed to fetch http://ppa.launchpad.net/pjbroad/ubuntu/dists/Intrepid/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://wine.budgetdedicated.com/apt/dists/Intrepid/main/binary-i386/Packages.gz  404 Not Found [IP: 81.171.111.184 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```

ok also i even tried changing the ones that were set to intrepid to Hardy and i still get this error ```
Failed to fetch http://archive.canonical.com/ubuntu/dists/Hardy/partner/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://wine.budgetdedicated.com/apt/dists/Hardy/main/binary-i386/Packages.gz  404 Not Found [IP: 81.171.111.184 80]
Failed to fetch http://ppa.launchpad.net/pjbroad/ubuntu/dists/Hardy/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/Hardy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://archive.canonical.com/ubuntu/dists/Hardy/partner/source/Sources.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

Is there anyway to fix this error? B/c i started off w/ Hardy Heron off of a Cd installed it saw that there was Intrepid which was released. Then i updated to intrepid. If there's no way to fix these errors, should i just do a complete wipe of my HDD and start from the very beginning?

---

### Post by crazyness003 on 2008-12-07
I think i see your problem. Un-capitalise the distro names. use the interpid packages and instead of* Intrepid*, use* intrepid*

I just tested all of them and with lower case they should work.

also, just a question, are you editing your /etc/apt/sources.list file, or are you doing it somewhere else?

---

### Post by 133794m3r on 2008-12-07
> **crazyness003 said:**
> I think i see your problem. Un-capitalise the distro names. use the interpid packages and instead of* Intrepid*, use* intrepid*

I just tested all of them and with lower case they should work.

also, just a question, are you editing your /etc/apt/sources.list file, or are you doing it somewhere else?

i was doing it in system->Admin-> software sources
also thanks

---

### Post by crazyness003 on 2008-12-07
did the capitalisation solution work?

---

### Post by 133794m3r on 2008-12-07
> **crazyness003 said:**
> did the capitalisation solution work?

yeah it worked great man thanks.. ^_^

---

### Post by crazyness003 on 2008-12-07
make sure you make this thread as [Solved] using the [Thread Tools]("http://ubuntuforums.org/showthread.php?t=1004126&nojs=1#goto_threadtools") 		 [IMG]http://ubuntuforums.org/images/misc/menu_open.gif[/IMG] located at the top-right of this page.

Thanks for playing and your welcome.

---

### Post by 133794m3r on 2008-12-22
ok unsolved once more... -_- it's happened again....
```
W: Failed to fetch http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2  

W: Failed to fetch http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2  

W: Failed to fetch http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2  

W: Failed to fetch http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2  

W: Failed to fetch http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-security/Release.gpg  

W: Failed to fetch http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2  

W: Failed to fetch http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2  

W: Failed to fetch http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2  

W: Failed to fetch http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2  

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg  Could not resolve 'wine.budgetdedicated.com'

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-en_US.bz2  Could not resolve 'wine.budgetdedicated.com'

W: Failed to fetch http://mirrors.easynews.com/linux/ubuntu/dists/intrepid/Release  

W: Failed to fetch http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by crazyness003 on 2008-12-23
hmm, that sux.
A number of things could have gone wrong. From your internet not working (which it dos since you posted), to the servers of all your repos being down (can happen). Have you tried running 
```
sudo apt-get update
``` in terminal. Sometimes, the gui likes to 'freak out'. Try that and see if it still doesnt work.

Also, i dont like the look of the 
> 
[http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-security/restricted/](http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-security/restricted/)**i18n/Translation-en_US.bz2** I tried to go to .../i18n/Translation-en_US.bz2 of each source, but it couldn't find it. I think maybe thats your problem. The en_US ones were not in the list (i browsed [http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-updates/main/i18n/](http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-updates/main/i18n/) it via Firefox). Plus [http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-security/restricted/](http://mirrors.easynews.com/linux/ubuntu/dists/intrepid-security/restricted/) dosnt even show an 'i18n' subdirectory.
Dont know what to tell you. try picking a diff server and see if it gives you the same prob

---

### Post by 133794m3r on 2008-12-23
yeah the terminal one worked so yeah thanks this is solved again... thanks for all of your work

---

### Post by crazyness003 on 2008-12-23
sure no prob.

---

### Post by newbie3 on 2010-11-07
hello i'm very new at this so sorry to be a bother, but i did the terminal thing as well and it still doesn't work. :(  this is what i got:

Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release 
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
  404 Not Found [IP: 91.189.88.37 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
  404 Not Found [IP: 91.189.88.37 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
  404 Not Found [IP: 91.189.88.37 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/universe Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/multiverse Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/universe Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/multiverse Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/universe Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/main Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/multiverse Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/restricted Packages
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/universe Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/main Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/multiverse Sources
  404 Not Found [IP: 91.189.92.172 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-backports/restricted Sources
  404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.172 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

what do i do?

---

