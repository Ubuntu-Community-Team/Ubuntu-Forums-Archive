---
title: "Terminal installing problem"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by lilwill94 on 2011-07-18
Hey everytime i try to install something i get this and it just stays there forever



lilwill@ubuntu:~$ sudo apt-get install acetoneiso
lilwill@ubuntu:~$ sts... 0%


Please help TIA

---

### Post by jerrrys on 2011-07-18
it should load.  try **sudo apt-get update** and then try to load or try a different software source

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by lilwill94 on 2011-07-19
now im getting this...




lilwill@ubuntu:~$ sudo apt-get update acetoneiso
[sudo] password for lilwill: 
E: The update command takes no arguments
lilwill@ubuntu:~$

---

### Post by alphacrucis2 on 2011-07-19
> **lilwill94 said:**
> now im getting this...




lilwill@ubuntu:~$ sudo apt-get update acetoneiso
[sudo] password for lilwill: 
E: The update command takes no arguments
lilwill@ubuntu:~$


The error message is correct. The command should be:

```
sudo apt-get update
```

That brings your package management indexes into sync with your repositories. If you wanted to install a package called acetoneiso the command to do that is:

```
sudo apt-get install acetoneiso
```

---

### Post by LowSky on 2011-07-19
I like to use 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by alphacrucis2 on 2011-07-19
> **LowSky said:**
> I like to use 

```
sudo apt-get update && sudo apt-get upgrade
```


Yep. For the OP that means update your package management index then upgrade any packages that have been superceded by newer versions in the repositories you are using. If you don't already have the acetoneiso package installed then you will still need the **sudo apt-get install acetoneiso** command

---

### Post by lilwill94 on 2011-07-19
yea im trying to install acetoneiso but when i type in that command i get the problem from the initial post

---

### Post by lilwill94 on 2011-07-20
sudo apt-get update i get this again




lilwill@ubuntu:~$ sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease    
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg           
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release               
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg [198 B]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages                  
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release [27.2 kB]             
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty InRelease                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources [94.7 kB]        
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty Release.gpg                        
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty Release                            
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources [14 B]     
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources [18.5 kB]    
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources [1,893 B]  
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages [277 kB]  
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty/main amd64 Packages                
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty/main TranslationIndex              
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages [14 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages [70.1 kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages [4,186 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]         
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [27.2 kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en             
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [59.6 kB]        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en         
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]     
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [7,727 B]    
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [658 B]    
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages [153 kB]  
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages [14 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages [25.3 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages [1,939 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty/main Translation-en_US             
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty/main Translation-en                
Fetched 769 kB in 14s (54.8 kB/s)                                              
lilwill@ubuntu:~$ sts... 0%


and then it stops there

---

### Post by alphacrucis2 on 2011-07-20
Looks like it might be hanging on a repo. If you open up the synaptic program and select settings - repositories. Then the "Other Software" tab. Uncheck all your third party repos. Then close synaptic and try the sudo apt-get update again. If that works you could then try and reenable the third party repos one at a time until you identify the offender. If still no joy, try again in synaptic settings - Repositories. Under the Ubuntu Software tab try changing to a different set of mirrors ie The drop box labelled **Download From:**

---

### Post by bcschmerker on 2011-07-20
FWIW, once the bad-repository problem is solved, Synaptic should be able to update properly through the Reload function.  I found Synaptic able to track updates to PPA's that I previously added from GNOME Terminal (via bash) using: 
```
gksudo -s add-apt-repository ... 
```Good luck with this problem.

---

### Post by danieljames on 2011-07-20
It does seem like a repository problem.  I would wonder what method you have used to alter your repository list or if you have at all.  

I would copy-paste my preferred list back into the sources text file.
Download the keys fresh and then run the update and upgrade commands.
I would check the name I was using for my desired program.
Then I would try again to use apt-get install.
If it was still failing I would change the mirrors like has already been suggested and try again.

---

### Post by lilwill94 on 2011-07-20
synaptic is crashing on boot now :( wtf

---

### Post by lilwill94 on 2011-07-20
> **danieljames said:**
> It does seem like a repository problem.  I would wonder what method you have used to alter your repository list or if you have at all.  

I would copy-paste my preferred list back into the sources text file.
Download the keys fresh and then run the update and upgrade commands.
I would check the name I was using for my desired program.
Then I would try again to use apt-get install.
If it was still failing I would change the mirrors like has already been suggested and try again.
lol can u dumb it down a little im a new to this

---

### Post by wildmanne39 on 2011-07-20
Hi, try this in a terminal
```
sudo rm /var/lib/apt/lists/* -vf
```
Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. It will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```
if you have errors post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by lilwill94 on 2011-07-20
i get this again 

[lilwill@ubuntu:~$ sudo rm /var/lib/apt/lists/* -vf
[sudo] password for lilwill: 
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/private-ppa.launchpad.net_commercial-ppa-uploaders_crossover-pro_ubuntu_dists_natty_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/private-ppa.launchpad.net_commercial-ppa-uploaders_crossover-pro_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/private-ppa.launchpad.net_commercial-ppa-uploaders_crossover-pro_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_Release'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources'
lilwill@ubuntu:~$ sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                                            
Get:1 [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg [198 B]                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]
Get:3 [http://archive.canonical.com](http://archive.canonical.com) natty Release [5,916 B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg [198 B]                   
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [27.2 kB]                     
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg [198 B]                    
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release [39.8 kB]  
Get:8 [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages [6,738 B]               
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [59.6 kB]                                
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                         
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release [27.2 kB]               
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]               
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [7,727 B]    
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [658 B]                                      
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages [153 kB]                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US                                               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                           
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources [862 kB]      
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages [14 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages [25.3 kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages [1,939 B]        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US                                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en                                                       
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty InRelease                                                                       
Get:19 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty Release.gpg [316 B]                                                          
Get:20 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty Release [9,760 B]                                                            
Get:21 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty/main amd64 Packages [1,068 B]                                                
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty/main TranslationIndex                                                           
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources [4,104 B]                                                      
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources [4,380 kB]                                                       
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty/main Translation-en_US                                                          
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty/main Translation-en                                                             
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources [155 kB]                                                       
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages [1,550 kB]                                                    
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages [9,001 B]                                               
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages [6,004 kB]                                                
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages [181 kB]                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex                                                            
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources [94.7 kB]                                                    
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources [14 B]                                                 
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources [18.5 kB]                                                
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources [1,893 B]                                              
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages [277 kB]                                              
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages [14 B]                                          
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages [70.1 kB]                                         
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages [4,186 B]                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en                                                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en                                                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US                                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en                                                      
Fetched 14.0 MB in 54s (257 kB/s)                                                                                           
lilwill@ubuntu:~$ sts... 0%]

---

### Post by wildmanne39 on 2011-07-20
Hi, I think this will fix it.
```
sudo rm  /var/lib/apt/lists/partial/*
```
```
sudo apt-get update
```
I know it looks like what you just did but the first command is different and just copy and paste the command because that remove command is dangerous if you follow it by the wrong directory.

---

### Post by lilwill94 on 2011-07-20
nope still getting the same error :( this is bad..

---

### Post by amjjawad on 2011-07-20
[URL="https://help.ubuntu.com/community/SynapticHowto#How to fix broken packages"]to fix broken packages
[/URL]
Also, better to read the whole thing: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by lilwill94 on 2011-07-20
> **amjjawad said:**
> [URL="https://help.ubuntu.com/community/SynapticHowto#How to fix broken packages"]to fix broken packages
[/URL]
Also, better to read the whole thing: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

i get the following error :(

[lilwill@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for lilwill: 
lilwill@ubuntu:~$ sudo apt-get install -f
lilwill@ubuntu:~$ sts... 0%]

:confused:

---

### Post by amjjawad on 2011-07-20
> **lilwill94 said:**
> i get the following error :(

[lilwill@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for lilwill: 
lilwill@ubuntu:~$ sudo apt-get install -f
lilwill@ubuntu:~$ sts... 0%]

:confused:

Hmmm, how about trying that from Recovery Mode?

Let's see what will happen?

---

### Post by lilwill94 on 2011-07-20
> **amjjawad said:**
> Hmmm, how about trying that from Recovery Mode?

Let's see what will happen?


still i get the same error

---

### Post by &#1048;&#1075;&#1086;&#1088; on 2011-07-20
I have similar problem with kubuntu 11.04....
Some diference:before installing any of packages I've reconfig dkpg, and thats work (for this time, until next install)... After short time I lose my nervs and solve problem on this way: fresh install of Ubuntu 11.04...
P.S. sorry for my bad english...

---

### Post by wildmanne39 on 2011-07-20
> **lilwill94 said:**
> still i get the same errorHi, try this and post results of the complete thing.
```
sudo apt-get update && sudo apt-get upgrade
```
by clicking on new reply and click # and paste the information between the brackets.
Also if you have not done so already restart your system.

---

### Post by lilwill94 on 2011-07-20
> **wildmanne39 said:**
> Hi, try this and post results of the complete thing.
```
sudo apt-get update && sudo apt-get upgrade
```
by clicking on new reply and click # and paste the information between the brackets.
Also if you have not done so already restart your system.

here ya go 

[lilwill@ubuntu:~$ sudo apt-get update
[sudo] password for lilwill: 
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages                  
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Get:1 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty Release.gpg [316 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty/main amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty/main TranslationIndex
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty/main Translation-en_US             
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) natty/main Translation-en                
Fetched 316 B in 19s (17 B/s)
lilwill@ubuntu:~$ sts... 0%
lilwill@ubuntu:~$ sudo apt-get upgrade
lilwill@ubuntu:~$ sts... 0%]

---

### Post by wildmanne39 on 2011-07-21
Hi, post your source list here with these two commands.
```
cat /etc/apt/sources.list
```
```
ls /etc/apt/sources.list.d/
```
Thank you

---

### Post by amjjawad on 2011-07-21
> **lilwill94 said:**
> still i get the same error

Please check the previous post by **wildmanne39** and let us know the output.

Thank you!

---

### Post by lilwill94 on 2011-07-21
is this right?



[lilwill@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
lilwill@ubuntu:~$ ls /etc/apt/sources.list.d/
private-ppa.launchpad.net_commercial-ppa-uploaders_crossover-pro_ubuntu.list
lilwill@ubuntu:~$]

---

### Post by wildmanne39 on 2011-07-21
Hi, I believe this is your problem.
> private-ppa.launchpad.net_commercial-ppa-uploaders_crossover-pro_ubuntu.list

Open synaptic click settings,repositories,other software and uncheck or remove that ppa and I think it will work.

---

### Post by lilwill94 on 2011-07-21
synaptic crashes when i try to open it :(

---

### Post by lilwill94 on 2011-07-21
maybe i should try in safe mode or something?

---

### Post by wildmanne39 on 2011-07-22
> **lilwill94 said:**
> maybe i should try in safe mode or something?Hi, type this in a terminal 
```
gksu gedit /etc/apt/sources.list
```

Then delete that ppa, then save,exit and then restart your system.

---

### Post by lilwill94 on 2011-07-22
wait how do i delete the ppa if i cant open synaptic

---

### Post by wildmanne39 on 2011-07-22
> **lilwill94 said:**
> wait how do i delete the ppa if i cant open synapticHi, copy and paste the command I gave you in my last post into a terminal, and follow the directions from that post also.

To open a terminal hit ctrl+alt+t

---

### Post by lilwill94 on 2011-07-22
this is all that happens


lilwill@ubuntu:~$ gksu gedit/etc/apt/sources.list
lilwill@ubuntu:~$

---

### Post by wildmanne39 on 2011-07-22
> **lilwill94 said:**
> this is all that happens


lilwill@ubuntu:~$ gksu gedit/etc/apt/sources.list
lilwill@ubuntu:~$Hi, did it open a window for your to type your password into? it should have and after you enter your password it will open your source list so you can delete that ppa.

Sorry I left out a space in the command that was my fault.

I corrected the command in that post now copy and paste it and it will open the window.

---

### Post by lilwill94 on 2011-07-22
k that opened the window but what do i delete this is all thats in there

[## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main]

---

### Post by wildmanne39 on 2011-07-22
Hi, ok I am having a bad couple of days my wife has been in the hospital with a minor stroke, so lets see if I can get it right this time.
Open file manager and on the left hand side click on file system then etc,then apt,then sources.list.d and delete that ppa that I listed in my other post. Then restart your computer and run ```
sudo apt-get update && sudo apt-get upgrade
```
I think it will work then.
I am sorry for the confusion it is my fault.

---

### Post by lilwill94 on 2011-07-22
o no your fine its my fault actually.. what is filemanager; synaptic?

---

### Post by wildmanne39 on 2011-07-22
> **lilwill94 said:**
> o no your fine its my fault actually.. what is filemanager; synaptic?Hi,
synaptic is like software center but it is more powerful you can install packages from there and you can remove ppp's and add ppa's. 

Open dash this is where the applications are listed and type synaptic then click on it and see if it opens, if it does you can use my directions in one of my previous posts to remove the ppa.

As for file manager click on the side launcher and click the home folder at the top of the launcher and that is the file manager. You can then use my other directions to remove the ppa that way.

---

### Post by lilwill94 on 2011-07-22
o ok thanks

---

### Post by lilwill94 on 2011-07-22
not letting me delete it :(
There was an error deleting private-ppa.launchpad.n...rossover-pro_ubuntu.list.

---

### Post by wildmanne39 on 2011-07-22
Hi, was that with the file manager? Try to open synaptic from dash or from a terminal with this command.
```
gksu synaptic
```
then follow the directions in my earlier post for unchecking the ppa in synaptic.

---

### Post by lilwill94 on 2011-07-22
yes i think that was filemanager and synaptic crashes on boot

---

### Post by wildmanne39 on 2011-07-22
Ok we will open file manager with priviliages and see if that works.

```
gksu nautilus
```
See if you can delete it now?

Also when you open a program from the terminal like you did synaptic it will give error messages in the terminal that can tell you why the program did not open.

---

### Post by lilwill94 on 2011-07-22
hey that worked!! and it doesnt give me a error message.. just crashes

---

### Post by lilwill94 on 2011-07-22
also that still didnt fix the sts...o% error :(

---

### Post by wildmanne39 on 2011-07-22
Hi, I am going to ask a friend to take a look,but it will be a while because of time zone differences.

---

### Post by coffeecat on 2011-07-23
Hi, lilwill94, wildmanne39 asked me to have a look. I've read through the thread and I think I'm up to speed, but I may have missed something, so a few comments and questions as well as a suggestion.

First. I notice that you bracket your terminal output with [] square brackets. Please don't do that - it confuses things and at first I thought you were getting:

```
lilwill@ubuntu:~$ sts... 0%] 
```

... rather than

```
lilwill@ubuntu:~$ sts... 0%
```

See how the use of code tags make things clearer. So when you post terminal output, code or the contents of config files, please use code tags like this:

[noparse]```

Your code output here.

```[/noparse]

... which will appear in your post as:

```

Your code output here.

```

Next. This:

```
lilwill@ubuntu:~$ sts... 0%
```

Is that exactly how that appears, the "sts... 0%" appearing spontaneously in the terminal prompt? I've never seen anything like it, and a google search didn't throw anything up.

Next:

> **lilwill94 said:**
> synaptic crashes when i try to open it :(

Try to open Synaptic from the terminal, with:

```
gksu synaptic
```

It will probably crash but you will get some valuable terminal output with error messages which may be helpful. Post the terminal output with errors.

Lastly:

I'm not quite clear whether you've managed to disable the ppa repository. To do so try this:

```
gksu gedit /etc/apt/sources.list.d/
private-ppa.launchpad.net_commercial-ppa-uploaders_crossover-pro_ubuntu.list
```

The source list file for that ppa will open in gedit. It will probably be just two lines. Post the contents of the file (between code tags :wink:) and then edit it so that there is a hash sign (# - called pound sign in America) at the beginning of the file. Save the file and then try "sudo apt-get update" again.

---

### Post by lilwill94 on 2011-07-23
trying synaptic in terminal doesnt give me any output :(.
and i think i disabled the ppa beacause there's nothing in this window 
```

gksu gedit /etc/apt/sources.list.d/

```

---

### Post by amjjawad on 2011-07-23
I'm sorry if this will sound odd/negative/giving up but ... I suggest to format and install a clean fresh Ubutnu unless you have lots of settings/apps.

I wish I could suggest something else but for me, it's a matter of saving time.

I usually don't give up but something looks wrong in your case and not sure if my friends here have more suggestions :)

Sorry again and good luck!

---

### Post by wildmanne39 on 2011-07-23
Hi, I am afraid I am out of ideas as well, unless someone else has a better idea I would reinstall also. 

Are you having any other issues? Do you get a message saying low on disk space? I doubt that is the case but it is just a thought.

Also open disk utility and see if there are any problems with your hard drive.

---

### Post by coffeecat on 2011-07-23
> **lilwill94 said:**
> trying synaptic in terminal doesnt give me any output :(.
and i think i disabled the ppa beacause there's nothing in this window 
```

gksu gedit /etc/apt/sources.list.d/

```

You probably haven't disabled the ppa - the code is incomplete. Something went wrong with the formatting of the code in my post and a spurious carriage return crept in. Sorry for not noticing that. The code for editing that file should be:

```
gksu gedit /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_crossover-pro_ubuntu.list
```

---

### Post by wildmanne39 on 2011-07-23
Hi, coffecat I believe he deleted that ppa in an earlier post but he still get the same error.

---

### Post by lilwill94 on 2011-07-24
> **wildmanne39 said:**
> Hi, coffecat I believe he deleted that ppa in an earlier post but he still get the same error.

this is true

---

### Post by amjjawad on 2011-07-24
> **lilwill94 said:**
> this is true

So, what's your next step now?

---

### Post by lilwill94 on 2011-07-24
im not sure :(

---

### Post by amjjawad on 2011-07-24
> **lilwill94 said:**
> im not sure :(

Here is another suggestion :)

Read your thread (this one) from beginning and re-do all the steps mentioned in this thread.

Sometimes, it does help, trust me.

If you did that already like 10 times and still not working then ... I'm actually running out from ideas unless someone else has a much better one :)

Good luck!

---

### Post by lilwill94 on 2011-07-24
im running ubuntu from a dual boot but i kinda ****** up my windows by installing a windows 7 demo over it :( so im kinda stuck with ubuntu.. so i was trying to install acetoneiso to get another working windows but i cant install that because of that error.. :(

---

### Post by amjjawad on 2011-07-24
> **lilwill94 said:**
> im running ubuntu from a dual boot but i kinda ****** up my windows by installing a windows 7 demo over it :( so im kinda stuck with ubuntu.. so i was trying to install acetoneiso to get another working windows but i cant install that because of that error.. :(

In that case, I do prefer to wipe your entire HDD and install Ubuntu again. Try Ubuntu 10.04.3.
It's LTS (Long Time Support) and needless to say it's LESS problems than 11.04.

DO NOT forget to backup your important data first.

Good Luck!

---

### Post by lilwill94 on 2011-07-24
> **amjjawad said:**
> In that case, I do prefer to wipe your entire HDD and install Ubuntu again. Try Ubuntu 10.04.3.
It's LTS (Long Time Support) and needless to say it's LESS problems than 11.04.

DO NOT forget to backup your important data first.

Good Luck!

hey how would i wipe my hdd and will that bring my original version of windows back?\

---

### Post by amjjawad on 2011-07-24
> **lilwill94 said:**
> hey how would i wipe my hdd 


Run Ubuntu from the LiveCD or LiveUSB, backup your important files if any and then from GParted (System > Administration > GParted), remove your partitions and start all over again.


> and will that bring my original version of windows back?\

If this is a laptop and you still have a restore partition, then I think it's possible but you need to press something at the beginning when you turn your system ON. F10 or something that will bring the Restore Screen and then you can restore your system to its factory default settings with No Ubuntu of course.

---

### Post by wildmanne39 on 2011-07-24
Hi, no it will not bring windows back.
You just use the livecd and reformat your partitions, then reinstall ubuntu.

Lets have a look at the information from this script before you reformat and reinstall, you may still have windows on your system and just need to reinstall grub.

Post the information from this script so we can see where everything is located: you will need to use the livecd to do this.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by lilwill94 on 2011-07-27
here you go sorry it took so long been busy lately..
Results.txt
```


 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2             206,848    20,686,847    20,480,000   7 NTFS / exFAT / HPFS
/dev/sda3    *     20,686,848   312,579,759   291,892,912   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1977 MB, 1977614336 bytes
64 heads, 63 sectors/track, 957 cylinders, total 3862528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                 135     3,862,527     3,862,393   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       dc296331-dc3b-493c-9ef7-3306250cef7a   ext4       
/dev/sda1        07DA-0606                              vfat       DellUtility
/dev/sda2        30B4043DB40407D4                       ntfs       RECOVERY
/dev/sda3        40C00657C0065396                       ntfs       OS
/dev/sdb1        6164-3636                              vfat       CHOICE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1        /media/CHOICE            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


======================== sda3/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 40C00657C0065396
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-10-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 40C00657C0065396
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=40C00657C0065396 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.38-10-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 40C00657C0065396
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=40C00657C0065396 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 40C00657C0065396
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=40C00657C0065396 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 40C00657C0065396
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=40C00657C0065396 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 30B4043DB40407D4
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 40C00657C0065396
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= sda3/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda3/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  10.207080841 = 10.959769600   boot/grub/grub.cfg                             1
   2.098213196 = 2.252939264    boot/initrd.img-2.6.38-10-generic              3
   7.895046234 = 8.477241344    boot/initrd.img-2.6.38-8-generic               2
   3.238594055 = 3.477413888    boot/vmlinuz-2.6.38-10-generic                 3
   6.410465240 = 6.883184640    boot/vmlinuz-2.6.38-8-generic                  1
   2.098213196 = 2.252939264    initrd.img                                     3
   7.895046234 = 8.477241344    initrd.img.old                                 2
   3.238594055 = 3.477413888    vmlinuz                                        3
   6.410465240 = 6.883184640    vmlinuz.old                                    1

```

---

### Post by amjjawad on 2011-07-27
> **lilwill94 said:**
> here you go sorry it took so long been busy lately..
Results.txt
```


 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2             206,848    20,686,847    20,480,000   7 NTFS / exFAT / HPFS
/dev/sda3    *     20,686,848   312,579,759   291,892,912   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1977 MB, 1977614336 bytes
64 heads, 63 sectors/track, 957 cylinders, total 3862528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                 135     3,862,527     3,862,393   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       dc296331-dc3b-493c-9ef7-3306250cef7a   ext4       
/dev/sda1        07DA-0606                              vfat       DellUtility
/dev/sda2        30B4043DB40407D4                       ntfs       RECOVERY
/dev/sda3        40C00657C0065396                       ntfs       OS
/dev/sdb1        6164-3636                              vfat       CHOICE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1        /media/CHOICE            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


======================== sda3/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 40C00657C0065396
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-10-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 40C00657C0065396
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=40C00657C0065396 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.38-10-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 40C00657C0065396
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=40C00657C0065396 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 40C00657C0065396
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=40C00657C0065396 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 40C00657C0065396
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=40C00657C0065396 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 30B4043DB40407D4
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 40C00657C0065396
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= sda3/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda3/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  10.207080841 = 10.959769600   boot/grub/grub.cfg                             1
   2.098213196 = 2.252939264    boot/initrd.img-2.6.38-10-generic              3
   7.895046234 = 8.477241344    boot/initrd.img-2.6.38-8-generic               2
   3.238594055 = 3.477413888    boot/vmlinuz-2.6.38-10-generic                 3
   6.410465240 = 6.883184640    boot/vmlinuz-2.6.38-8-generic                  1
   2.098213196 = 2.252939264    initrd.img                                     3
   7.895046234 = 8.477241344    initrd.img.old                                 2
   3.238594055 = 3.477413888    vmlinuz                                        3
   6.410465240 = 6.883184640    vmlinuz.old                                    1

```

This is Wubi Installation. You don't even have a Linux Partition :)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Apparently, you can restore Windows, just like I already explained in my previous post.

IMHO, I'd recommend to get rid of Wubi and install Ubuntu as a Real New Installation.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

there are many guides over there, I do have one too in my signature.

When you restore Windows, Wubi should be automatically removed.

---

### Post by lilwill94 on 2011-07-27
yea i think im going to restore windows.. but im not sure if thats the right windows to restore.. i started off with "windows 7 starter"

---

### Post by amjjawad on 2011-07-27
> **lilwill94 said:**
> yea i think im going to restore windows.. but im not sure if thats the right windows to restore.. i started off with "windows 7 starter"

What do you mean? what is your current version of Windows that you are using now?

---

### Post by wildmanne39 on 2011-07-27
Hi +1
> Apparently, you can restore Windows, just like I already explained in my previous post.

IMHO, I'd recommend to get rid of Wubi and install Ubuntu as a Real New Installation.

---

### Post by lilwill94 on 2011-07-27
my current version that i have is windows 7 black but its a beta or something and i cant activate it so i wanna go back to what i started with which is windows 7 starter.

---

### Post by amjjawad on 2011-07-27
> **lilwill94 said:**
> my current version that i have is windows 7 black but its a beta or something and i cant activate it so i wanna go back to what i started with which is windows 7 starter.

OK, not sure which "F Key" you need to press once you start your machine to access the recovery menu but maybe it's F10 or something?
Try to recover your Windows and everything should be fine after that.

If you're considering to get rid of Windows and install Ubuntu with no other OS, then just backup your important data and wipe your HDD but I don't recommend that as long as you still have an active Windows Restore.

---

### Post by westie457 on 2011-07-27
> **lilwill94 said:**
> my current version that i have is windows 7 black but its a beta or something and i cant activate it so i wanna go back to what i started with which is windows 7 starter.

Hi and apologies to the others for butting in. Have read through the thread and credit to everyone involved.

In your Grub list at Boot time of the computer do you have two options for Windows after the memtest ones? 
If you do select the first one, that will run the recovery environment which will restore the computer to how it left the factory, giving you your Windows 7 Starter and any software the manufacturer installed.

The same advice as others have already stated "Back up all your personal files first, to CD/DVD or another hard drive.

If you are not 100% positive if the recovery partition is there download and burn a [SuperGrub2]("http://www.supergrubdisk.org/") disk. This will identify the all the partitions on all the hard drives (if you have more than one) and allow you to start it.

Good luck

---

### Post by lilwill94 on 2011-07-28
hey idk if i did the right restore but i did some kinda restore that has me restore to a earlier date but i get this error: (check attachment)

---

### Post by westie457 on 2011-07-28
> **lilwill94 said:**
> hey idk if i did the right restore but i did some kinda restore that has me restore to a earlier date but i get this error: (check attachment)

I missed something. can you run me through the steps you did to get to the situation of your screenshot please.

Post it something like this:- Turn on > wait for post to finish > Grub Menu selected Windows 7  > pressed F8.

This is en example of how I would like you to post and hopefully not the exact process you went through.

---

### Post by amjjawad on 2011-07-28
> **lilwill94 said:**
> hey idk if i did the right restore but i did some kinda restore that has me restore to a earlier date but i get this error: (check attachment)

NOT Windows Restore, there must be an option to restore your machine to its factory default settings just like when you bought the machine.

In Laptops, that option should be accessible upon booting once you turn your machine ON. 

By the way, I attached your screenshot after rotating it ;)

---

### Post by lilwill94 on 2011-07-29
lol thanks about the picture but idk what button to press though :(

---

### Post by amjjawad on 2011-07-29
> **lilwill94 said:**
> lol thanks about the picture but idk what button to press though :(

Sometimes, it's "Esc" OR "F2" or "F10" but it's vary from machine to machine.

---

### Post by lilwill94 on 2011-07-31
lol i tried googling still nothing i cannot find the button

---

### Post by amjjawad on 2011-08-01
> **lilwill94 said:**
> lol i tried googling still nothing i cannot find the button

Are you saying that you couldn't enter your BIOS yet?
Just try the buttons and see which one will work!

Don't you have the manual of your machine?

---

### Post by lilwill94 on 2011-08-02
ok read the manual and it brought me to this menu but the one that says "system restore" ive tried and thats the one that just restored my windows.
and the one that says "image restore" or something like that gives me a error saying no image can be found or something

---

### Post by amjjawad on 2011-08-02
> **lilwill94 said:**
> ok read the manual and it brought me to this menu but the one that says "system restore" ive tried and thats the one that just restored my windows.
and the one that says "image restore" or something like that gives me a error saying no image can be found or something

NO Matter what key to press, there "must" be something that will allow you to enter BIOS.

I'll try to read your whole thread again and see if there's another approach that we didn't try yet.

Also, I see you post back once in a while so hope you can response faster ;)

Edit:
Does that restore you always get work or not? do you still get the same error message like in here: [http://ubuntuforums.org/showpost.php?p=11094319&postcount=71](http://ubuntuforums.org/showpost.php?p=11094319&postcount=71)

---

### Post by lilwill94 on 2011-08-02
> **amjjawad said:**
> NO Matter what key to press, there "must" be something that will allow you to enter BIOS.

I'll try to read your whole thread again and see if there's another approach that we didn't try yet.

Also, I see you post back once in a while so hope you can response faster ;)

Edit:
Does that restore you always get work or not? do you still get the same error message like in here: [http://ubuntuforums.org/showpost.php?p=11094319&postcount=71](http://ubuntuforums.org/showpost.php?p=11094319&postcount=71)

sorry about replying slow, trying to fit football practice, napping and everything else in lol :D 
and the restore does not seem to be working no

---

### Post by amjjawad on 2011-08-02
> **lilwill94 said:**
> sorry about replying slow, trying to fit football practice, napping and everything else in lol :D 
and the restore does not seem to be working no

Do you have Windows CD? otherwise, you don't have another option but to format and install Ubuntu BUT please make sure to backup ALL your important data.

---

### Post by lilwill94 on 2011-08-02
no disc :( but with formatting will i have my first windows back?

---

### Post by lilwill94 on 2011-08-02
my laptop doesnt even have a disc tray

---

### Post by amjjawad on 2011-08-02
> **lilwill94 said:**
> no disc :( but with formatting will i have my first windows back?

If you will wipe the whole HDD, NO, you can't do anything later.

If you will restore, your machine will be back to the same status when you bought it first time.

Problem in your case and as per your posts, you can NOT get that restore.

---

### Post by lilwill94 on 2011-08-02
So if i format i will not have access to any os

---

### Post by amjjawad on 2011-08-03
> **lilwill94 said:**
> So if i format i will not have access to any os

Obviously, if you format, you'll lose all your data on your machine, no doubt about it.

Usually, Laptops come with a backup for Windows on the Hard Drive. It's a separate partition, sometimes called "Restore Partition".
You can access that by pressing one of the F Keys.

They don't sell Laptops with Windows CD, instead, they create that partition so user can restore Windows and the Laptop will go back to its original status when user just bought it.

If you can't access that partition for some reason, I'm not sure how could you restore your machine?

Are you able to login to Windows on that machine or you can't?

You mentioned that you have a Beta Version of something so what is it?

Let's make sure you do have a backup partition so please, check my signature ... the last link (4th) called "Boot Script".
Please, read the instructions carefully and post back the result here.
Please, don't forget to wrap up the text (result) with "CODE" tags or highlight it and click "#".

---

### Post by lilwill94 on 2011-08-03
i have the beta version of "windows 7 black" but i have no acces to the internet or anything on that i cant even activate it and that overwritten my original "windows 7 starter". here is the results 

```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2             206,848    20,686,847    20,480,000   7 NTFS / exFAT / HPFS
/dev/sda3    *     20,686,848   312,579,759   291,892,912   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1977 MB, 1977614336 bytes
64 heads, 63 sectors/track, 957 cylinders, total 3862528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                 135     3,862,527     3,862,393   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       dc296331-dc3b-493c-9ef7-3306250cef7a   ext4       
/dev/sda1        07DA-0606                              vfat       DellUtility
/dev/sda2        30B4043DB40407D4                       ntfs       RECOVERY
/dev/sda3        40C00657C0065396                       ntfs       OS
/dev/sdb1        6164-3636                              vfat       CHOICE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1        /media/CHOICE            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


======================== sda3/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 40C00657C0065396
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-10-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 40C00657C0065396
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=40C00657C0065396 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.38-10-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 40C00657C0065396
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=40C00657C0065396 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 40C00657C0065396
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=40C00657C0065396 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 40C00657C0065396
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=40C00657C0065396 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 30B4043DB40407D4
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 40C00657C0065396
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= sda3/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda3/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  10.207080841 = 10.959769600   boot/grub/grub.cfg                             1
   2.098213196 = 2.252939264    boot/initrd.img-2.6.38-10-generic              3
   7.895046234 = 8.477241344    boot/initrd.img-2.6.38-8-generic               2
   3.238594055 = 3.477413888    boot/vmlinuz-2.6.38-10-generic                 3
   6.410465240 = 6.883184640    boot/vmlinuz-2.6.38-8-generic                  1
   2.098213196 = 2.252939264    initrd.img                                     3
   7.895046234 = 8.477241344    initrd.img.old                                 2
   3.238594055 = 3.477413888    vmlinuz                                        3
   6.410465240 = 6.883184640    vmlinuz.old                                    1

```

---

### Post by amjjawad on 2011-08-03
> **lilwill94 said:**
> i have the beta version of "windows 7 black" but i have no acces to the internet or anything on that i cant even activate it and [COLOR=Red]**that overwritten my original "windows 7 starter".**[/COLOR] 


Are you 100% positive about that?
Can't you revert or go back to the previous state?



```

  => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

  [COLOR=Red]  File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM
[/COLOR] 
```

Can't you access this partition? when you turn your machine on, as I explained previously, there must be an option to access that?

Hmmm, perhaps that Windows you installed messed up with your system so you can't even access Dell Utility.

I suggest to check your "manual" and see how to rest your machine to the factory default. You should be able to restore your machine to the same state you bought it first time.

If this is impossible at this point, then either to wipe everything and install Windows (if you really want that AND have the license) OR simply format and install Ubuntu from the LiveUSB.

Perhaps, there is a way to do it but I'm not sure how?
I assume you don't even have a restore CD? I know you don't have a CD-Drive but you can use External CD-Drive so hope your vender provided a CD or something?
Eventually, there MUST be away to restore your machine. Otherwise, as I said, wipe it and install Ubuntu but that should be your last solution.

---

### Post by lilwill94 on 2011-08-03
maybe i should call dell?

---

### Post by amjjawad on 2011-08-03
> **lilwill94 said:**
> maybe i should call dell?
Good idea :)

---

### Post by wildmanne39 on 2011-08-03
WoW, I see you are still hard at it.

---

### Post by lilwill94 on 2011-08-04
> **amjjawad said:**
> Good idea :)

do you think they will be mad about the windows 7 black download?

---

### Post by lilwill94 on 2011-08-04
> **wildmanne39 said:**
> WoW, I see you are still hard at it.

lol yeah all i want is working version of windows :)

---

### Post by lilwill94 on 2011-08-04
the image restore say "no image found" so i think im screwed on that

---

### Post by bcschmerker on 2011-08-04
I have a hybrid Everex® mid-tower (orig. a TC2502 with a 200W PAU and all-VIA® mobo packing a C7-D CPU) that I fitted out with a full bag of hardware upgrades, incl. a 500W Athena® PSU and all-AMD-equipped Gigabyte® mobo.  Most aftermarket motherboards use the **DEL** key to enter the Setup routines from power-on self-test; an exception is Acer®, which uses **F2** to enter Setup from POST.

---

### Post by lilwill94 on 2011-08-04
> **bcschmerker said:**
> I have a hybrid Everex® mid-tower (orig. a TC2502 with a 200W PAU and all-VIA® mobo packing a C7-D CPU) that I fitted out with a full bag of hardware upgrades, incl. a 500W Athena® PSU and all-AMD-equipped Gigabyte® mobo.  Most aftermarket motherboards use the **DEL** key to enter the Setup routines from power-on self-test; an exception is Acer®, which uses **F2** to enter Setup from POST.

k ill give this a try

---

### Post by lilwill94 on 2011-08-04
nope doesnt work for me... F8 bring me to all my restore options that i know of but they all seem to be tied with windows 7 black some kinda way

---

### Post by amjjawad on 2011-08-04
> **lilwill94 said:**
> do you think they will be mad about the windows 7 black download?

Simply, don't tell them that. They sold a machine to you with NO manual and NO Restore CD or whatever so it's their job and responsibility to HELP you when you need them.

I don't know what's wrong with Companies these days, what happened to the "quality"? did it vanish or something? I guess so.

If the machine is still under warranty, that will be much better to.

Give them hard time ...  I mean a call :D

Let us know what will happen with you, ok? :)

---

### Post by amjjawad on 2011-08-04
> **lilwill94 said:**
> nope doesnt work for me... F8 bring me to all my restore options that i know of but they all seem to be tied with windows 7 black some kinda way

Installing any OS should NEVER mess with BIOS. I mean, there must be one key to press and that key should enable you to enter your BIOS settings, unless Dell for some weird reason had disabled that and that's NO WAY to happen.

Usually, "Esc", "Del" or "F-Keys" are the keys to Enter BIOS.
Again, unless Dell has changed that fact.

If Windows Black has overwritten your backup image and there is no way to restore that to a previous stage and Dell will NOT be able to help then I don't know of any other way but to wipe the HDD and install Ubuntu (or any other OS).

Whatever you'll decide to do, please make sure to BACKUP your important files before anything.

Keep us updated ;)

---

### Post by lilwill94 on 2011-08-04
when i wipe my hdd how will i install another os ?

---

### Post by amjjawad on 2011-08-04
> **lilwill94 said:**
> when i wipe my hdd how will i install another os ?

What OS you want to install?

I'm on my cell now. I'll post a link to you later or you can check the 2nd link in my Sig

---

### Post by amjjawad on 2011-08-04
I'll provide you with some links that will help you ;)

To wipe your HDD, you can simply boot from a LiveCD or LiveUSB and run GParted. 

If it's Ubuntu 10.04 then: System > Administration > GParted
If it's Ubuntu 11.04 then: System Settings > Gparted

System Settings can be found in Shutdown Menu.

[http://ubuntuforums.org/showpost.php?p=11101707&postcount=129](http://ubuntuforums.org/showpost.php?p=11101707&postcount=129)


General Info:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

There are lots of guides and HOWTO. You can also search here:

[www.googlubuntu.com](www.googlubuntu.com)

---

### Post by lilwill94 on 2011-08-07
hey sorry i took long.... but i would like a windows 7 pro or ultimate that would be nice! and thanks alot!!!

---

### Post by lilwill94 on 2011-08-09
wait whats a live cd?

---

### Post by jtarin on 2011-08-10
> **lilwill94 said:**
> hey sorry i took long.... but i would like a windows 7 pro or ultimate that would be nice! and thanks alot!!!Not trying to be rude, but....This is the Ubuntu forum not the Christmas Wish List Forum. Call your PC manufacturer or store where you bought it to get help with your original setup.We only do Linux here.:P

---

### Post by amjjawad on 2011-08-10
> **lilwill94 said:**
> wait whats a live cd?

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[http://en.wikipedia.org/wiki/Live_CD](http://en.wikipedia.org/wiki/Live_CD)

[http://en.wikipedia.org/wiki/Live_USB](http://en.wikipedia.org/wiki/Live_USB)

---

### Post by lilwill94 on 2011-08-10
lol you were reading it wrong @jtarin

---

