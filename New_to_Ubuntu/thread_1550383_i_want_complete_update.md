---
title: "i want complete update?"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by munna.cheyur on 2010-08-11
i don't have internet connection but i have connection in my office. i want to update my lucid lynx completely is it possible to download updates straightly another computer and install or update those files on my system. if possible tell me the website where to download all (security-updates) and (lucid-updates).. thank you for you clear response.....

---

### Post by kostkon on 2010-08-11
Check [*Keryx*]("http://keryxproject.org/").

---

### Post by cavalier911 on 2010-08-11
Synaptic will generate a wget download script for whatever files you mark for installation and import downloaded files for installation.
Open synaptic,"reload","mark all upgrades",File menu/Generate Package Download Script,name and save the script,shut down synaptic.Make the script executable,run the script to download the packages.
Reopen Synaptic,File menu/Add downloaded packages,browse to folder with packages,a windows opens confirming installation,click ok 
By converting the download script to a list and using the program todos I was able to import the download list into flashget in winxp.

---

### Post by mac9416 on 2010-08-13
> **cavalier911 said:**
> Synaptic will generate a wget download script for whatever files you mark for installation and import downloaded files for installation.
Open synaptic,"reload","mark all upgrades",File menu/Generate Package Download Script,name and save the script,shut down synaptic.Make the script executable,run the script to download the packages.
Reopen Synaptic,File menu/Add downloaded packages,browse to folder with packages,a windows opens confirming installation,click ok 
By converting the download script to a list and using the program todos I was able to import the download list into flashget in winxp.

Unfortunately, if your computer is offline, Synaptic does not have access to the latest package lists and you won't be able to upgrade to the latest packages.

Also, the wget script does not work in Windows.

---

