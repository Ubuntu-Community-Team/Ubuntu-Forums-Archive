---
title: "Beginners problem with Flash - I guess!?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by black.sfcro on 2009-05-10
Hi, I am new user of Linux OS, Ubuntu 9.04 distribution. Until two days ago I have only used MS Windows operating systems for many, many years. I wanted to see for myself what is all this hype about. :)

 

 First impressions are very positive and I am learning as I go &#8230; Unfortunately I have a problem with watching YouTube videos. I have sound (not really good quality) but picture (video) is not running smoothly.
 I have read forum advices but nothing worked so far, also I have received some advices from Ubuntu community back home, but also without any results.  
 

 Just to mention I have no problem in watching any kind of video files on my computer.  
 

 Please, consider that I am beginner in Linux when giving advices. :(

 

 Sorry for my English.  
 

 Thanks in advance.

---

### Post by Sef on 2009-05-10
1) How did you download flash?

2) Are you running 32 or 64 bit?

---

### Post by LesterPalooza on 2009-05-10
So this means you have tried installing flashplugin-nonfree? Maybe this is an issue of hardware drivers? Maybe it's an old PC? Which version of Ubuntu 9.04 are you using? The 32-bit? or 64-bit?

Please post here your computer specifications. :)

---

### Post by black.sfcro on 2009-05-10
well, I am running 32 bit ... 

this is what i did based on advices so far ... I hope this helps ...

am2x2@am2x2-desktop:~$ sudo updatedb
[sudo] password for am2x2: 
am2x2@am2x2-desktop:~$ locate libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
am2x2@am2x2-desktop:~$ 


am2x2@am2x2-desktop:~$ dpkg -l|grep -i flash
ii  adobe-flashplugin                          10.0.22.87-1                       Adobe Flash Player plugin version 10
ii  libswfdec-0.8-0                            0.8.4-1                            SWF (Macromedia Flash) decoder library
ii  swfdec-gnome                               2.26.0-1                           Tools to play SWF files (Macromedia Flash) o
am2x2@am2x2-desktop:~$

am2x2@am2x2-desktop:~$ dpkg -l|grep -i flash
ii  adobe-flashplugin                          10.0.22.87-1                       Adobe Flash Player plugin version 10
ii  flashplugin-installer                      10.0.22.87ubuntu2                  Adobe Flash Player plugin installer
ii  flashplugin-nonfree                        10.0.22.87ubuntu2                  Adobe Flash Player plugin installer (transit
ii  libswfdec-0.8-0                            0.8.4-1                            SWF (Macromedia Flash) decoder library
ii  swfdec-gnome                               2.26.0-1                           Tools to play SWF files (Macromedia Flash) o
am2x2@am2x2-desktop:~$ sudo updatedb
[sudo] password for am2x2: 
am2x2@am2x2-desktop:~$ locate libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
am2x2@am2x2-desktop:~$ 

am2x2@am2x2-desktop:~$ sudo apt-get --purge autoremove adobe-flashplugin swfdec-gnome
[sudo] password for am2x2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcurl3
The following packages will be REMOVED:
  adobe-flashplugin* libcurl3* swfdec-gnome*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 11.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 104593 files and directories currently installed.)
Removing adobe-flashplugin ...
Removing libcurl3 ...
Purging configuration files for libcurl3 ...
Removing swfdec-gnome ...
Purging configuration files for swfdec-gnome ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
am2x2@am2x2-desktop:~$

---

### Post by LesterPalooza on 2009-05-10
> **black.sfcro said:**
> ...
The following packages will be REMOVED:
  **adobe-flashplugin*** libcurl3* swfdec-gnome*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 11.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 104593 files and directories currently installed.)
Removing adobe-flashplugin ...
Removing libcurl3 ...
Purging configuration files for libcurl3 ...
Removing swfdec-gnome ...
Purging configuration files for swfdec-gnome ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
am2x2@am2x2-desktop:~$

Did that just remove adobe flash plugin? Are you using Firefox or Opera? or other web browser?

EDIT: So you still have libflashplayer.so hmm.... right?

---

### Post by Lampi on 2009-05-10
Could this be your graphic device driver? After you installed Ubuntu you should have gotten a notification about restricted drivers being available for your graphic card. Maybe you should change to one of them (ati / nvidia, proprietary driver) if you haven't done this already.

You can easily see if you have the best driver by clicking on Menu > System > Hardware - it should tell you there whether the proprietary driver is installed and running!

---

### Post by gandaran on 2009-05-10
> **black.sfcro said:**
> well, I am running 32 bit ... 

this is what i did based on advices so far ... I hope this helps ...

am2x2@am2x2-desktop:~$ sudo updatedb
[sudo] password for am2x2: 
am2x2@am2x2-desktop:~$ locate libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
am2x2@am2x2-desktop:~$ 


am2x2@am2x2-desktop:~$ dpkg -l|grep -i flash
ii  adobe-flashplugin                          10.0.22.87-1                       Adobe Flash Player plugin version 10
ii  libswfdec-0.8-0                            0.8.4-1                            SWF (Macromedia Flash) decoder library
ii  swfdec-gnome                               2.26.0-1                           Tools to play SWF files (Macromedia Flash) o
am2x2@am2x2-desktop:~$

am2x2@am2x2-desktop:~$ dpkg -l|grep -i flash
ii  adobe-flashplugin                          10.0.22.87-1                       Adobe Flash Player plugin version 10
ii  flashplugin-installer                      10.0.22.87ubuntu2                  Adobe Flash Player plugin installer
ii  flashplugin-nonfree                        10.0.22.87ubuntu2                  Adobe Flash Player plugin installer (transit
ii  libswfdec-0.8-0                            0.8.4-1                            SWF (Macromedia Flash) decoder library
ii  swfdec-gnome                               2.26.0-1                           Tools to play SWF files (Macromedia Flash) o
am2x2@am2x2-desktop:~$ sudo updatedb
[sudo] password for am2x2: 
am2x2@am2x2-desktop:~$ locate libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
am2x2@am2x2-desktop:~$ 

am2x2@am2x2-desktop:~$ sudo apt-get --purge autoremove adobe-flashplugin swfdec-gnome
[sudo] password for am2x2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcurl3
The following packages will be REMOVED:
  adobe-flashplugin* libcurl3* swfdec-gnome*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 11.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 104593 files and directories currently installed.)
Removing adobe-flashplugin ...
Removing libcurl3 ...
Purging configuration files for libcurl3 ...
Removing swfdec-gnome ...
Purging configuration files for swfdec-gnome ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
am2x2@am2x2-desktop:~$

you have been installing a lot!
remove the swfdec flash, that is whats causing your problem and you don't need more than one adobe flash plugin installed, keep the flashplugin-installer package only remove the adobe-flashplugin and flashplugin-nonfree packages

---

### Post by black.sfcro on 2009-05-10
AMD 64 X2 3600 
2 GB RAM
ATI X1950 PRO
120 GB HDD 


I am using Mozilla Firefox

---

### Post by LesterPalooza on 2009-05-10
For my case(using Firefox too), I just put libflashplayer.so in /home/<username>/.mozilla/plugins/<place libflashplayer.so here> and everything works fine...

Did you also try installing flashplugin-nonfree from Synaptic?

---

### Post by black.sfcro on 2009-05-10
Well, to be honest I am lost atm :( ... need some brake and will try again ...

thanks for advices anyway.

---

### Post by Lampi on 2009-05-10
just type

about:plugins

in the firefox navbar to find out what plugins are installed

---

### Post by black.sfcro on 2009-05-10
Problem solved!!!!!

Thanks allot for all advices...

---

### Post by LesterPalooza on 2009-05-10
How was your break? Please do come forward if you still have any questions :D

---

