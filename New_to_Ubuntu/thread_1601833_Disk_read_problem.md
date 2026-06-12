---
title: "Disk read problem?"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by thombark on 2010-10-20
My first serious system-related problem. It happens in  Synaptic Package Manager and Ubuntu software center also crashes.
Using 10.04
The directory exists.

E: Read error - read (21: Is a directory)
E: Problem opening /var/lib/apt/lists/Ubuntu%2010.04%20LTS%20%5fLucid%20Lynx%5f%20-%20Release%20i386%20(20100429)_dists_lucid_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Thanks

T

---

### Post by LowSky on 2010-10-20
open a terminal

type

```
sudo dpkg --configure -a
```

then type

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by thombark on 2010-10-20
Thanks, tried it and got similar output:

ubuntu@ubuntu:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
ubuntu@ubuntu:~$ sudo dpkg --configure -a
ubuntu@ubuntu:~$ sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US   
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [38.5kB]               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [93.7kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [1,994B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [45.1kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [33.4kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]
Fetched 213kB in 2s (87.2kB/s)
Reading package lists... Error!
E: Read error - read (21: Is a directory)
E: Problem opening /var/lib/apt/lists/Ubuntu%2010.04%20LTS%20%5fLucid%20Lynx%5f%20-%20Release%20i386%20(20100429)_dists_lucid_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
ubuntu@ubuntu:~$

---

### Post by soldier1st on 2010-10-22
it looks like there is a problem with the restricted extras package, can you try to reinstall it? if not try to remove it then go to a terminal and type sudo restart gdm and it will ask for password then it will restart the gdm then reinstall ubuntu restricted extras.

---

### Post by linux-hack on 2010-10-22
did you try this :

```
sudo apt-get install -f
```

---

### Post by wildmanne39 on 2012-08-05
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

