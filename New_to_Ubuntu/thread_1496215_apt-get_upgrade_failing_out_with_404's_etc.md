---
title: "apt-get upgrade failing out with 404's etc"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by Scribble86 on 2010-05-29
Hi, I'm having trouble with apt-get. I can install things just fine, but I can't update my version of the repositories! here's an example after using minimal archives. can anyone help me out?
First my sources.list:

>  #############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security main 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security main 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main 


now the results:


> scribble@Aria ~ % sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/chromium/ppa/ubuntu/](http://ppa.launchpad.net/chromium/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid Release.gpg                     
Ign [http://ppa.launchpad.net/frasten/ppa/ubuntu/](http://ppa.launchpad.net/frasten/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/http/ppa/ubuntu/](http://ppa.launchpad.net/http/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/https/ppa/ubuntu/](http://ppa.launchpad.net/https/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu/](http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Ign [http://deb.playonlinux.com/](http://deb.playonlinux.com/) lucid/main Translation-en_US                   
Ign [http://ppa.launchpad.net/network-manager/ppa/ubuntu/](http://ppa.launchpad.net/network-manager/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Get:1 [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid Release [1,722B]              
Ign [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/tp-fan/ppa/ubuntu/](http://ppa.launchpad.net/tp-fan/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                  
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                   
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources          
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Fetched 1B in 2s (0B/s)
W: Failed to fetch [http://ppa.launchpad.net/chromium/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/chromium/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/http/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/http/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/https/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/https/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/network-manager/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/network-manager/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/tp-fan/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/tp-fan/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
100 scribble@Aria ~ %   

---

### Post by -humanaut- on 2010-05-29
> **Scribble86 said:**
> Hi, I'm having trouble with apt-get. I can install things just fine, but I can't update my version of the repositories! here's an example after using minimal archives. can anyone help me out?
First my sources.list:



now the results:

Damn dude, thats alot of PPA's comment out the ones that are down with a # and that should fix your problem.

---

### Post by Scribble86 on 2010-05-29
hmm you're right... but none of them are included in /etc/apt/sources.list so where do I look for the ppas to clear them?

thanks!

---

### Post by sundays211 on 2010-05-29
Check the software sources program (system-administration-software sources)

---

### Post by Elfy on 2010-05-29
> **Scribble86 said:**
> hmm you're right... but none of them are included in /etc/apt/sources.list so where do I look for the ppas to clear them?

thanks!

Look in /etc/apt/sources.list.d

That should be where they are

---

### Post by Scribble86 on 2010-05-29
Thanks folks! I managed to remove the bad ppas and now it's running smoothly.

---

