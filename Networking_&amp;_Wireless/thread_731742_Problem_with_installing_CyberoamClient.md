---
title: "Problem with installing CyberoamClient"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by ksr4a0 on 2008-03-22
i am a newbie...I have cable internet connection....i installed Ubuntu 7.04 one day back(Dual boot-Windows XP)...To get connected to web,i have to first login thru the client....i am unable to install this cyberoamclient....i have downloaded the required setup thru windows xp....now i placed the tar.gz file on desktop in ubuntu...when i enter the command  "tar xvfz CyberoamLinuxClient.tar.gz" ,two files got extracted...but then when i enter the command  "./crclient -u username" , i get a message "bash: ./crclient is a directory" ........plz help me out in installing this as i can connect only by logging in thru this client

---

### Post by alphacrux on 2008-03-26
usually the way you install a program from a .tar.gz file is thus: you put the .tar.gz file into your /usr/src directory, type "tar -xvfz filet.tar.gz". Now cd into the folder it creates (usually the name of the file) so "cd file". Then you run any configuration script "./confiure" then "make" then "make install". If it is not installed in this fashion then usually there is a REAME file in one of the directories that will tell you how to do it, look for the README or INSTALL file, open with gedit or nano.

---

