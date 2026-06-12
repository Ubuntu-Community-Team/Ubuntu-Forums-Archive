---
title: "Installing Adobe Flashplug-in (ubuntu 11.04)"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by Safeeq on 2011-07-09
I just installed ubuntu 11.04 and was not able to view video's in youtube. Downloaded the adobe flash plug-in but couldn't install it. Googled some forum and found that Ubuntu software centre can be used to install - launched the Ubuntu software centre and entered "Adobe Flash Plugin" which didnt bring back any plugins for installation. Tried using synaptic package manager and when I click the synaptic package manager, it prompted me to enter the password and after entering the password, its throwing an exception.

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Please help me to install the adbobe flash !!

---

### Post by zealibib slaughter on 2011-07-09
Install flash aid from here [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and that should take care of the problem.

---

### Post by Bucky Ball on 2011-07-09
You want 'flashplugin-nonfree' from the repos. That will drag in flashplugin-installer and should install all you need automagically. Use Synaptic Package Manager. (System>Administration).

---

### Post by Safeeq on 2011-07-09
Tried  [https://addons.mozilla.org/en-US/fir...don/flash-aid/]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") but still when I goto youtube, still some plugins are missing. I did clicked the "Install Missing Plugins" which says "No Suitable Plugins Found"

---

### Post by Safeeq on 2011-07-09
Sorry, what do you mean "You want 'flashplugin-nonfree' from the repos" - I couldn't use synaptic package manager as well. It throws an exception I've posted in my question.

---

### Post by zealibib slaughter on 2011-07-09
open a terminal and type
```
sudo apt-get install flashplugin-nonfree
```
this should install the latest version of flash in the repos.

---

### Post by Safeeq on 2011-07-09
even that failed with some exceptions

fara@ubuntu:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for fara: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
fara@ubuntu:~$

---

### Post by Bucky Ball on 2011-07-09
You can only have one package manager open at once. Close all package managers (update manager, Synaptics), open a terminal, try zealibib's code again, or;

Close all apps, go to Synaptics, search for 'flashplugin-nonfree', mark to install, 'Apply' and you're done. ;)

---

### Post by Safeeq on 2011-07-09
I've copied the command in the notepad and restarted the laptop again. When tried running the command I am getting the same error message??!!

---

### Post by pqwoerituytrueiwoq on 2011-07-09
after installing flash aid restart firefox and look to the right of the address bar

---

### Post by Safeeq on 2011-07-09
Yeah, I did tried that earlier and clicked the "missing plugins" to install but that ended with a message "No missing plugins found". Am I missing anything here?? I've struggling to get this work since last 3 days!!

---

### Post by wildmanne39 on 2011-07-09
> **Safeeq said:**
> Yeah, I did tried that earlier and clicked the "missing plugins" to install but that ended with a message "No missing plugins found". Am I missing anything here?? I've struggling to get this work since last 3 days!!

Hi, to fix it where you can install packages run these two commands in a terminal.
```
sudo rm /var/lib/apt/lists/* -vf
```
Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. It will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```

---

### Post by Safeeq on 2011-07-09
Executed both the commands as you told - closed the firefox and restrated it again. When I try to play the youtube video , it got the "Missing Plugins" notification just below the address bar , clicked it download the plugins and got the same message as "No Missing Plugins found".

```
fara@ubuntu:~$ sudo rm /var/lib/apt/lists/* -vf
[sudo] password for fara: 
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_multiverse_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_restricted_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_main_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_binary-amd64_Packages.IndexDiff'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_source_Sources.IndexDiff'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-amd64_Packages.IndexDiff'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_source_Sources.IndexDiff'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_source_Sources'
fara@ubuntu:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release.gpg [198 B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [27.2 kB]
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release.gpg [198 B]
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release [39.8 kB]      
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [57.0 kB]
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release [27.2 kB]             
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Sources [862 kB]       
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [7,103 B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [658 B]   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages [146 kB] 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages [14 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages [22.0 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages [1,939 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Sources [4,104 B]         
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Sources [4,380 kB]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Sources [155 kB]          
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main amd64 Packages [1,550 kB]       
Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted amd64 Packages [9,001 B]  
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe amd64 Packages [6,004 kB]   
Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse amd64 Packages [181 kB]   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe TranslationIndex               
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Sources [90.9 kB]       
Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Sources [14 B]    
Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Sources [17.9 kB]   
Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Sources [1,893 B] 
Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main amd64 Packages [265 kB] 
Get:28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted amd64 Packages [14 B]
Get:29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe amd64 Packages [68.3 kB]
Get:30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse amd64 Packages [4,186 B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Get:31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en_GB [74.5 kB]     
Get:32 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en_GB [73.4 kB]
Get:33 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en_GB [2,259 B]
Get:34 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en_GB [4,982 B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en         
Fetched 14.1 MB in 1min 4s (219 kB/s)                                          
Reading package lists... Done
fara@ubuntu:~$
```

---

### Post by pqwoerituytrueiwoq on 2011-07-09
after installing flash aid click this button

---

### Post by Safeeq on 2011-07-09
After posting my earlier message, I tried installing it using Synaptic package manager and its working now :)

Thanks to all for your help - please let me know how to make this post "Solved"

---

### Post by wildmanne39 on 2011-07-09
> **Safeeq said:**
> After posting my earlier message, I tried installing it using Synaptic package manager and its working now :)

Thanks to all for your help - please let me know how to make this post "Solved"Hi, yes that is what the commands I gave you were for to fix your package manager so you could use it to install flash player,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

