---
title: "Broadcom 4311"
date: 2014-05-13
forum: Networking &amp; Wireless
---

### Post by mikeavison on 2014-05-13
Hi

I just installed Ubuntu 12.04 and cannot now get the wireless working.

Laptop is Acer 5220

On Board wireless adapter is Broadcom 4311

I have tried to follow
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
 installed Broadcom STA driver

but still can't get it going

here is the report from lspci

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Sorry to be so u/s

Thanks for the help

Mike

---

### Post by wildmanne39 on 2014-05-13
Hi, the answer is in the link below.
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by mikeavison on 2014-05-13
Thanks Wildman but I have tried the method described by Chili555 (that was the link I posted in my question). It appears praseodym is offering an alternative solution (for when Chili555's instructions don't work) but it is in German and I am afraid I can't read German. 

I have gone throught the Chili555 instructions several times but no wireless funcionality appears.

Probably I am doing something wrong but I can't see what it is.

Thanks for helping.

---

### Post by mikeavison on 2014-05-13
PS

When I have downloaded the linux-firmware-nonfree driver package i run "Additional Drivers" from settings. I think the first time it found the driver and allowed me to activate it (still no wireless though), subsequent times it just reports "No additional drivers are in use on this system" (or words nearly like that).

Mike

---

### Post by wildmanne39 on 2014-05-13
Please only do:
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```
Reboot
You do not need to install from additional drivers for your device as stated in the link I posted, it installs the incorrect driver in your case.
Thanks

---

### Post by mikeavison on 2014-05-14
Hi Wildman, still no joy I am afraid.

Here is the contents of the terminal after running those 3 lines you instructed:-

anila@anila-Extensa-5220:~$ sudo apt-get purge bcmwl-kernal-source
[sudo] password for anila: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernal-source
anila@anila-Extensa-5220:~$ sudo apt-get update
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [103 kB]        
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.9 kB]   
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,794 B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [412 kB]  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [96.6 kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,636 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [72 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
100% [Connecting to gb.archive.ubuntu.com (91.189.88.153)]^[[A                 
100% [Connecting to gb.archive.ubuntu.com (91.189.88.153)]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg      
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release [49.6 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources                                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex                         
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources [457 kB]                  
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources [8,028 B]           
Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources [107 kB]              
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources [8,902 B]           
Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages [801 kB]            
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages [12.2 kB]     
Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages [246 kB]        
Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages [15.5 kB]     
Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]        
Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]  
Get:28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]  
Get:29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_GB                    
Get:30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en [344 kB]           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_GB                
Get:31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en [140 kB]       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en                 
Fetched 2,907 kB in 2min 6s (22.9 kB/s)                                                    
Reading package lists... Done
anila@anila-Extensa-5220:~$ 
anila@anila-Extensa-5220:~$ sudo apt -get install linux-firmware-nonfree
sudo: apt: command not found
anila@anila-Extensa-5220:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 9 not to upgrade.
anila@anila-Extensa-5220:~$ 



Thanks

---

### Post by pdc on 2014-05-14
just a comment: wild man suggested 

> sudo apt-get purge bcmwl-[COLOR="#FF0000"]kernel[/COLOR]-source

and you seem to have typed

> sudo apt-get purge bcmwl-[COLOR="#EE82EE"]kernal[/COLOR]-source

and that is different enough................that your computer sees them as different things.............I guess you may not be able to copy and paste the commands??

you could try the command again;

---

### Post by mikeavison on 2014-05-14
Damn - thnaks for that I will execute the commands again with copy and paste

---

### Post by mikeavison on 2014-05-14
BRILLIANT

its working

Thanks Wild Man and pdc

Really appreciated

---

### Post by pdc on 2014-05-14
that's great Mike; enjoy

---

