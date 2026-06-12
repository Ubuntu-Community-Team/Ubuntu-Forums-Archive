---
title: "Well my script and my repository problem"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-05-18
I have my own live cd script, Now I have my own repository, I try to combine the two and got a my own disaster, the repository works fine, in my hard drive, but when I got into the chroot environment it get screwed up, I put the repo folder(which is my repository folder) in the edit folder(which is my chroot) And make it still does not work. I get this.


Start package installation? y/[n] y

--2009-05-18 14:39:46--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 276 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[===========================================>] 276         --.-K/s   in 0s      

2009-05-18 14:39:47 (14.5 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [276/276]

E: The method driver /usr/lib/apt/methods/fule could not be found.
E: The method driver /usr/lib/apt/methods/fule could not be found.
E: The method driver /usr/lib/apt/methods/fule could not be found.
E: The method driver /usr/lib/apt/methods/fule could not be found.
E: The method driver /usr/lib/apt/methods/fule could not be found.
E: The method driver /usr/lib/apt/methods/fule could not be found.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
W: Duplicate sources.list entry file: hardy-updates/multiverse Packages (/var/lib/apt/lists/_repo_mirror_archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package serpentine
E: The method driver /usr/lib/apt/methods/fule could not be found.
E: The method driver /usr/lib/apt/methods/fule could not be found.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: The method driver /usr/lib/apt/methods/fule could not be found.
E: The method driver /usr/lib/apt/methods/fule could not be found.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Installing Flash plugin for Firefox... cp: cannot create regular file `edit/usr/lib/firefox-3.0.10/plugins': No such file or directory
cp: cannot create regular file `edit/usr/lib/firefox-3.0.10/plugins': No such file or directory
Done

rm: cannot remove `edit/usr/share/gnome-background-properties/ubuntu-wallpapers.xml': No such file or directory
cp: cannot stat `ubuntu-wallpapers.xml': No such file or directory
update-rc.d: warning: /etc/init.d/FOO missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System startup links for /etc/init.d/FOO already exist.
cp: cannot create regular file `/edit/extract-cd/isolinux': No such file or directory
Ign file: hardy-updates Release.gpg
Ign file: hardy-updates/multiverse Translation-en_US                                
Ign file: hardy-updates Release                                                     
Ign file: hardy-updates/multiverse Packages                                         
Ign file: hardy-updates/multiverse Sources                                          
Err file: hardy-updates/multiverse Packages                                         
  File not found
Err file: hardy-updates/multiverse Sources                                          
  File not found
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy Release.gpg                                           
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Translation-en_US                                
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy Release                                               
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Packages                                         
Hit [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Packages                                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Sources
W: Failed to fetch file:/repo/mirror/archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz  File not found

W: Failed to fetch file:/repo/mirror/archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz  File not found

E: Some index files failed to download, they have been ignored, or old ones used instead.
Recompile iso? [y]/n 
root@eric:~/live# 



Any ideas?

---

### Post by sandyd on 2009-05-18
> **ericeclifford said:**
> I have my own live cd script, Now I have my own repository, I try to combine the two and got a my own disaster, the repository works fine, in my hard drive, but when I got into the chroot environment it get screwed up, I put the repo folder(which is my repository folder) in the edit folder(which is my chroot) And make it still does not work. I get this.
```


Start package installation? y/[n] y

--2009-05-18 14:39:46--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
Resolving [www.medibuntu.org]("http://www.medibuntu.org")... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80]("http://www.medibuntu.org%7C87.98.242.110%7C:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 276 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[===========================================>] 276         --.-K/s   in 0s      

2009-05-18 14:39:47 (14.5 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [276/276]

E: The method driver /usr/lib/apt/methods/fule could not be found.
E: The method driver /usr/lib/apt/methods/fule could not be found.
E: The method driver /usr/lib/apt/methods/fule could not be found.
E: The method driver /usr/lib/apt/methods/fule could not be found.
E: The method driver /usr/lib/apt/methods/fule could not be found.
E: The method driver /usr/lib/apt/methods/fule could not be found.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
W: Duplicate sources.list entry file: hardy-updates/multiverse Packages (/var/lib/apt/lists/_repo_mirror_archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package serpentine
E: The method driver /usr/lib/apt/methods/fule could not be found.
E: The method driver /usr/lib/apt/methods/fule could not be found.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: The method driver /usr/lib/apt/methods/fule could not be found.
E: The method driver /usr/lib/apt/methods/fule could not be found.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Installing Flash plugin for Firefox... cp: cannot create regular file `edit/usr/lib/firefox-3.0.10/plugins': No such file or directory
cp: cannot create regular file `edit/usr/lib/firefox-3.0.10/plugins': No such file or directory
Done

rm: cannot remove `edit/usr/share/gnome-background-properties/ubuntu-wallpapers.xml': No such file or directory
cp: cannot stat `ubuntu-wallpapers.xml': No such file or directory
update-rc.d: warning: /etc/init.d/FOO missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System startup links for /etc/init.d/FOO already exist.
cp: cannot create regular file `/edit/extract-cd/isolinux': No such file or directory
Ign file: hardy-updates Release.gpg
Ign file: hardy-updates/multiverse Translation-en_US                                
Ign file: hardy-updates Release                                                     
Ign file: hardy-updates/multiverse Packages                                         
Ign file: hardy-updates/multiverse Sources                                          
Err file: hardy-updates/multiverse Packages                                         
  File not found
Err file: hardy-updates/multiverse Sources                                          
  File not found
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy Release.gpg                                           
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Translation-en_US                                
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy Release                                               
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Packages                                         
Hit [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Packages                                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Sources
W: Failed to fetch file:/repo/mirror/archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz  File not found

W: Failed to fetch file:/repo/mirror/archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz  File not found

E: Some index files failed to download, they have been ignored, or old ones used instead.
Recompile iso? [y]/n 
root@eric:~/live# 

```


Any ideas?
use ```
 tags please.... long posts are extremely anoying.....

in your /etc/apt/sources.list

[code]
deb file:/repo/mirror/archive.ubuntu.com/ubuntu hardy-updates multiverse

and

deb-src file:/repo/mirror/archive.ubuntu.com/ubuntu hardy-updates multiverse 

```should be  
```

deb http://archive.ubuntu.com/ubuntu hardy-updates multiverse

and

deb-src http://archive.ubuntu.com/ubuntu hardy-updates multiverse

```

as for the first few errors, try 
```

dpkg-reconfigure apt
apt-get install --reinstall apt

```
seems like you broke your apt somehow...

---

### Post by ericeclifford on 2009-05-18
Well see if I do the http, it will go to the internet, I am using my own repository, that I made from apt-mirror, right now its in my filesystem in a folder called repo and in the instructions it saids point to the mirror folder for each repository that I  mirrored, it works fine on my 8.04.2 version on my hard drive, but when I put it in the chroot environment( My new root during the live cd customization script is Edit ( which is the live cd file system) it does not appear to pick it up.

it works fine on my original filesystem, but not on my chroot edit filesystem.

Also Ill try to play with apt stuff as well. Thanks for the reply.

---

### Post by ericeclifford on 2009-05-18
Anyone got any other ideas?

---

### Post by ericeclifford on 2009-05-18
bump in need of HELP ):P

---

### Post by ericeclifford on 2009-05-18
Shameful bump

---

### Post by ericeclifford on 2009-05-19
Still havnt figured it out yet.

---

