---
title: "Update Manager not working."
date: 2010-07-10
forum: New to Ubuntu
---

### Post by Vege 4wd on 2010-07-10
Hi, I have not been able to use update manger all day. 
  After searching the forum and trying a couple of things what I have ended up with is when I try to update it goes through the motions without actually downloading anything.

When I click to see files individually I notice the downloads come up with "hit" and "failed" but nothing downloads. 

I would apprieciate any help for this.

---

### Post by plucky on 2010-07-10
> **Vege 4wd said:**
> Hi, I have not been able to use update manger all day. 
  After searching the forum and trying a couple of things what I have ended up with is when I try to update it goes through the motions without actually downloading anything.

When I click to see files individually I notice the downloads come up with "hit" and "failed" but nothing downloads. 

I would apprieciate any help for this.

Open a terminal (**Applications > Accessories > Terminal**) and input ```
sudo apt-get update
``` and post the output.

---

### Post by Vege 4wd on 2010-07-10
Been googling. Still not able to work it out.   Mind going a bit blurry with all the info and ideas.

---

### Post by Vege 4wd on 2010-07-10
this may be of some help. The following is the output for the above code:

Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release.gpg                             
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_AU          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_AU       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_AU   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/dtl131/ppa/ubuntu/](http://ppa.launchpad.net/dtl131/ppa/ubuntu/) lucid/main Translation-en_AU   
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_AU    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                    
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release.gpg                           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources                               
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) lucid/non-free Translation-en_AU
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release.gpg                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_AU
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid/non-free Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Packages
Reading package lists... Done
aaron@aaron-laptop:~$

---

### Post by plucky on 2010-07-10
There are no errors.

Now run ```
sudo apt-get upgrade
``` will download and install all new software updates.

Good Luck

---

### Post by Vege 4wd on 2010-07-10
bumping: anyone know how to get update manager working?

---

### Post by Vege 4wd on 2010-07-10
plucky I get this error from update manager after I ran the code:

Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.

And I get this output from the terminal:

aaron@aaron-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aaron@aaron-laptop:~$

---

### Post by plucky on 2010-07-10
> **Vege 4wd said:**
> bumping: anyone know how to get update manager working?

What happens when you run ```
sudo apt-get upgrade
```?

---

### Post by plucky on 2010-07-10
Try changing your Server to the Main Server.

Open **System > Administration > Software Sources** and on the first page select "Main Server" in the Download From dropbox.

When I click on you links it doesn't go to the repository server.It goes [Here](http://au.archive.ubuntu.com/)

According to the home page,there was an outage this morning, so there might still be problems with their network.

---

### Post by Vege 4wd on 2010-07-10
Hi plucky, the output for the code:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Even from the main server I get "hit" and "failed" when it tries to download.

Any ideas are welcome.

---

