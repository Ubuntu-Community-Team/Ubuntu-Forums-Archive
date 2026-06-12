---
title: "Strange terminal error - apt-get update"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by CasparGrigoriNovykh on 2010-11-18
Hello everyone,

I am a brand spankin' new Ubuntu user, and couldn't be happier with the decision.  I am currently dual-booting my 2 month old Ubuntu 10.10 with Windows Vista (both 32bit).  I've found that learning Ubuntu is fast-paced, though I've been pushed out of the nest without warning!  It has been smooth, enjoyable sailing until recently, when I hit this obnoxious error.  Upon execution of ```
sudo apt-get update
```, I watch the program run smoothly, and hit all the usual sources, until it finally returns: 


```
W: Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```


This error showed up immediately after I attempted to install gdm2, and has not dissipated after restarts or the numerous commands thrown at it.  Only once have I ever manually edited my sources list, and that was near a month previous to this little problem.  I'm sure (or at least hopeful) that there is a simple fix to this problem, but it's certainly lost on me.  I will post the window's contents, below.  Thank you so much in advance for any help.  I've heard a lot of great things about this forum, and even more about Ubuntu.  I am looking forward to working past this issue so I can continue learning more about the power of this OS.  

Thanks again,
Caspar

P.S. I apologize for the length of this thread.

caspar@Pluto:~$ sudo apt-get update
[sudo] password for caspar: 
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick Release.gpg
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports Release.gpg                
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en          
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en                 
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick/main Translation-en        
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick/main Translation-en_US     
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick/multiverse Translation-en  
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick/multiverse Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_US
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_US
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_US
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_US
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick/restricted Translation-en  
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick/restricted Translation-en_US
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick/universe Translation-en    
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick/universe Translation-en_US 
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-updates Release.gpg                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en   
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/docky-core/ppa/ubuntu/](http://ppa.launchpad.net/docky-core/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/docky-core/ppa/ubuntu/](http://ppa.launchpad.net/docky-core/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en              
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/) maverick/main Translation-en
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-updates/main Translation-en
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-updates/multiverse Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US              
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports Release                    
Ign [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-updates/universe Translation-en
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-security Release.gpg               
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports/main Sources               
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-security/main Translation-en
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-security/main Translation-en_US
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-security/restricted Translation-en
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-security/universe Translation-en
Ign [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick Release                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports/restricted Sources         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports/universe Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports/multiverse Sources         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports/main i386 Packages         
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-updates Release                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports/restricted i386 Packages   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports/universe i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports/multiverse i386 Packages   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-security Release                   
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,092B]                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick/restricted Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick/universe Sources
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick/multiverse Sources
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick/main i386 Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages    
  404  Not Found
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick/restricted i386 Packages
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick/universe i386 Packages
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick/multiverse i386 Packages
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-updates/main Sources
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-updates/restricted Sources
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-updates/universe Sources
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-updates/multiverse Sources
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-updates/main i386 Packages
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-updates/restricted i386 Packages
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-updates/universe i386 Packages
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-updates/multiverse i386 Packages
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-security/main Sources
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-security/restricted Sources
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-security/universe Sources
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-security/multiverse Sources
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-security/main i386 Packages
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-security/restricted i386 Packages
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-security/universe i386 Packages
Hit [http://mirrors.pavlovmedia.net](http://mirrors.pavlovmedia.net) maverick-security/multiverse i386 Packages
Fetched 2,636B in 3s (733B/s)
W: Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by drs305 on 2010-11-18
I went to the site and there is currently no 'maverick' folder. It could be down for maintenance or some other reason. You can check back later if you know the site previously contained the maverick repositories.

In the meantime, you can eliminate the error message by unticking that ppa in Synaptic or Software Sources: Settings, Repositories: Third Party.

---

### Post by CasparGrigoriNovykh on 2010-11-18
Thank you so much!  That did it.  I will remember that for the future.  

I changed to the U.S. servers and all is well, again.  I appreciate the help and the quick reply!

---

