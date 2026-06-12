---
title: "Fresh Hardy install, cannot install vlc"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by knowlittle on 2010-07-10
dash4g, 

I could not install VLC. I did what you suggested and get the following:


xxx@xxx-laptop:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.not.working.list
xxx@xxx-laptop:~$ gksudo gedit /etc/apt/sources.list
xxx@xxx-laptop:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy/main Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy/restricted Translation-en_AU
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security/main Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy/universe Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy/multiverse Translation-en_AU
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates/main Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates/restricted Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security/restricted Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security/universe Translation-en_AU
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release [65.9kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB] 
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [278kB]          
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages [1,178kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [11.3kB]  
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [86.3kB]        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [935B]     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [130kB]     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [25.9kB]     
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages [6,986B]            
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources [338kB]                    
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources [1,488B]             
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages [4,293kB]             
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources [1,323kB]              
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages [179kB]             
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources [60.9kB]             
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages [505kB]           
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages [11.3kB]    
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources [156kB]            
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources [935B]       
Fetched 8,770kB in 28s (310kB/s)                                               
Reading package lists... Done
xxx@xxx-laptop:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: libcucul0 (>= 0.99.beta13b-1) but it is not going to be installed
E: Broken packages



Could you or anyone help please?

---

### Post by ramjet_1953 on 2010-07-10
You need to fix the broken package first.

1. Open Synaptic Package Manager

2. Click on Edit > Fix Broken Packages

3. Try installing now.

Regards,
Roger:D

---

