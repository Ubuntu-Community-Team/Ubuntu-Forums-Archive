---
title: "No ability to enable mediabuntu repositories with Android USB Tethering"
date: 2013-10-09
forum: Networking &amp; Wireless
---

### Post by euanbuntu2 on 2013-10-09
Hi, am on 13.04 64bit, using a samsung galaxy s3 tethered to my laptop, which is working fine to post these questions, generally surf, etc., but when I try to add repositories from the terminal I get this:


christmaspudding@Christmas:~$ sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2013-10-10 00:55:07--  [http://www.medibuntu.org/sources.list.d/raring.list](http://www.medibuntu.org/sources.list.d/raring.list)
Resolving [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org](www.medibuntu.org))... 88.191.127.22
Connecting to [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org)|88.191.127.22|:80](www.medibuntu.org)|88.191.127.22|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-10-10 00:55:07 ERROR 404: Not Found.



Does anyone have any ideas how I can sort this out please?

---

### Post by euanbuntu2 on 2013-10-09
Also tried this:

christmaspudding@Christmas:~$ sudo apt-get update && sudo apt-get upgrade

And got this back:

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release.gpg [933 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg [72 B]             
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release.gpg [933 B]             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                          
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports Release.gpg [933 B] 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release.gpg                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security Release.gpg [933 B]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release [40.8 kB]                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release [40.8 kB]               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports Release [40.8 kB]             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security Release [40.8 kB]              
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Sources [963 kB]                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_GB                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                        
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Sources [5,987 B]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Sources [5,838 kB]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Sources [171 kB]            
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main amd64 Packages [1,170 kB]         
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted amd64 Packages [9,636 B]    
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe amd64 Packages [5,396 kB]     
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse amd64 Packages [130 kB]     
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main i386 Packages [1,168 kB]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_GB                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_GB                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted i386 Packages [9,623 B]     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_GB                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe i386 Packages [5,405 kB]      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_GB                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse i386 Packages [131 kB]      
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en_GB [73.8 kB]       
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en [673 kB]           
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free amd64 Packages                   
  404  Not Found
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en_GB [63.5 kB] 
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en [98.4 kB]    
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free amd64 Packages               
  404  Not Found
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en_GB [2,358 B] 
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en [2,767 B]    
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free i386 Packages                    
  404  Not Found
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en_GB [4,620 B]   
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en [3,736 kB]     
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free i386 Packages                
  404  Not Found
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free Translation-en_GB                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free Translation-en                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free Translation-en_GB            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free Translation-en               
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Sources [74.4 kB]         
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Sources [14 B]      
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Sources [72.8 kB]     
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Sources [2,266 B]   
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main amd64 Packages [190 kB]   
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted amd64 Packages [14 B]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe amd64 Packages [149 kB]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse amd64 Packages [3,715 B]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main i386 Packages [188 kB]    
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted i386 Packages [14 B]
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe i386 Packages [150 kB]
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse i386 Packages [3,864 B]
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en [89.5 kB]  
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en [1,826 B]
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en [14 B]
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en [77.2 kB]
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Sources [902 B]         
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Sources [14 B]    
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Sources [5,532 B]   
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Sources [1,403 B] 
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main amd64 Packages [565 B]  
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted amd64 Packages [14 B]
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe amd64 Packages [6,505 B]
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse amd64 Packages [1,357 B]
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main i386 Packages [565 B]   
Get:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted i386 Packages [14 B]
Get:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe i386 Packages [6,490 B]
Get:57 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse i386 Packages [1,345 B]
Get:58 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Translation-en [269 B]  
Get:59 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Translation-en [1,040 B]
Get:60 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Translation-en [14 B]
Get:61 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Translation-en [5,066 B]
Get:62 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main Sources [46.6 kB]        
Get:63 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted Sources [14 B]     
Get:64 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe Sources [9,271 B]    
Get:65 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse Sources [2,266 B]  
Get:66 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main amd64 Packages [121 kB]  
Get:67 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted amd64 Packages [14 B]
Get:68 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe amd64 Packages [38.4 kB]
Get:69 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse amd64 Packages [3,715 B]
Get:70 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main i386 Packages [120 kB]   
Get:71 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted i386 Packages [14 B]
Get:72 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe i386 Packages [39.0 kB]
Get:73 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse i386 Packages [3,864 B]
Get:74 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main Translation-en [62.4 kB] 
Get:75 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse Translation-en [1,826 B]
Get:76 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted Translation-en [14 B]
Get:77 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe Translation-en [23.8 kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en_GB            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en_GB        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Translation-en_GB          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Translation-en_GB    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Translation-en_GB    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main Translation-en_GB           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse Translation-en_GB     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted Translation-en_GB     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe Translation-en_GB       
Fetched 26.7 MB in 15s (1,724 kB/s)                                            
W: Failed to fetch [http://packages.medibuntu.org/dists/raring/free/binary-amd64/Packages](http://packages.medibuntu.org/dists/raring/free/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://packages.medibuntu.org/dists/raring/non-free/binary-amd64/Packages](http://packages.medibuntu.org/dists/raring/non-free/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://packages.medibuntu.org/dists/raring/free/binary-i386/Packages](http://packages.medibuntu.org/dists/raring/free/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://packages.medibuntu.org/dists/raring/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/raring/non-free/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by hansdown on 2013-10-09
Hi euanbuntu2.

Medibuntu has closed.

---

### Post by QIII on 2013-10-09
Hello!


Medibuntu is no longer maintained.

---

### Post by deadflowr on 2013-10-09
It's unfortunate, but alas you can still get the libdvdcss package following the suggestions in post #1 here
[http://ubuntuforums.org/showthread.php?t=2174110](http://ubuntuforums.org/showthread.php?t=2174110)

Don't know which other packages anyone else might use, but that tends to be the most sought after.

---

### Post by euanbuntu2 on 2013-10-10
Thanks for all the info everyone.

Could someone walk me through how to do this please as I've not done it before and don't want to mess things up.

Thanks in advance :)

---

