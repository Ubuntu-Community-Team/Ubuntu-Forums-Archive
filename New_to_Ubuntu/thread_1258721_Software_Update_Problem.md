---
title: "Software Update Problem"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by JackieMc on 2009-09-05
I can't seem to install my updates below are the messages and actions taken to date.

  	 	 	 	 	 	  Original Error Message and Detail:
 

 E: /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package `libxcb-shape0' is missing final newline
 

 (Reading database...dpkg: error processing / var/ cache / apt / archives/ linux-image-2.6.24-22-lpia_2.6.24-2245netbook9_lpia.deb (--unpack):
  files list file for package 'libxcb-shape0' is missing final new line
 Errors were encountered while processing:
  /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24.22,45netbook9_lpiadeb
 Processing was halted because there were too many errors.
 E: Sub-process /usr/bin/dpkg returned an error code (1)
  A package failed to install.  Trying to recover:
 

 Tried following code in terminal:
 

 jackie@jackie:~$ echo -en '\n' | sudo tee -a /var/lib/dpkg/info/libxcb-shape0 
 [sudo] password for jackie:  
  
 jackie@jackie:~$  
 

 Got the message below after I ran the code
 

 Error Message
 

 E: /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package `libxcb-shape0' is missing final newline 
 

 Detail Message
 (Reading database...dpkg: error processing / var/cashe/apt/archives/linus-image-2.6.24-22-lpia_2.6.24-22.45netboo9_lpia.deb (--unpack):
 	files list file for package 'libxcb-shape0' is missing final new line
 Errors were encountered while processing:
  /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netboo9_lpia.deb
 Processing was halted because there were too many erros.
 E: Sub – process /usr/bin/dpkg returned an error code (1)
 A package failed to install. Trying to recover:
 :confused:

Thank you for your help.

---

### Post by Liolikas on 2009-09-05
Try:
sudo apt-get update
sudo apt-get upgrade
And post errors.

---

### Post by PorkyPie on 2009-09-05
Try this in Terminal (Applications > Accessories > Terminal):
sudo apt-get update

---

### Post by PorkyPie on 2009-09-05
> **Liolikas said:**
> Try:
sudo apt-get update
sudo apt-get upgrade
And post errors.

Sorry, didn't see your post! :)

---

### Post by JackieMc on 2009-09-06
Ok, I'll give it a shot.  Many thanks to all.

---

### Post by JackieMc on 2009-09-06
> **Liolikas said:**
> Try:
sudo apt-get update
sudo apt-get upgrade
And post errors.


Ok, ran the above and this is what I got. Also, the error reporting process (information still being gathered ) is still at it and its been a while.  Does that sound right?

==================================   	 	 	 	 	 	   

 jackie@jackie:~$ sudo apt-get update 
 [sudo] password for jackie:  
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release.gpg 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Translation-en_US 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Translation-en_US 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Translation-en_US 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Translation-en_US 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release.gpg 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Translation-en_US 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Translation-en_US 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Translation-en_US 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Translation-en_US 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release.gpg 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Translation-en_US 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Translation-en_US 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Translation-en_US 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Translation-en_US 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release.gpg 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Translation-en_US 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Translation-en_US 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Translation-en_US 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Translation-en_US 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Translation-en_US 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Translation-en_US 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Translation-en_US 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Translation-en_US 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Sources 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources 
 Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources 
 Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources 
 Reading package lists... Done 
 jackie@jackie:~$ sudo apt-get upgrade 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following packages will be upgraded: 
   firefox firefox-3.0 firefox-3.0-gnome-support firefox-gnome-support libdrm2 
   libgl1-mesa-dri-psb linux-image-2.6.24-22-lpia 
   linux-ubuntu-modules-2.6.24-22-lpia psb-video update-manager 
   update-manager-core xorg-modules-xpsb xserver-xorg-video-psb xulrunner-1.9 
   xulrunner-1.9-gnome-support 
 15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 Need to get 0B/31.0MB of archives. 
 After this operation, 119kB of additional disk space will be used. 
 Do you want to continue [Y/n]? y 
 (Reading database ... dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb (--unpack): 
  files list file for package `libxcb-shape0' is missing final newline 
 Errors were encountered while processing: 
  /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb 
 Processing was halted because there were too many errors. 
 E: Sub-process /usr/bin/dpkg returned an error code (1) 
 jackie@jackie:~$  
 

 After program ran received the following alert
 

 Error
 

 Package Problem
 

 Sorry, the package “linux-image-2.6.24-22-;pia 2.6.24-45netbook9 failed to install or upgrade
 

 You can help the developers to fix the package by reporting the problem.
 (Problem was reported)
 

 ============================================

---

### Post by Jobanjo422 on 2009-09-17
> **JackieMc said:**
> I can't seem to install my updates below are the messages and actions taken to date.

                                 Original Error Message and Detail:
 

 E: /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package `libxcb-shape0' is missing final newline
 

 (Reading database...dpkg: error processing / var/ cache / apt / archives/ linux-image-2.6.24-22-lpia_2.6.24-2245netbook9_lpia.deb (--unpack):
  files list file for package 'libxcb-shape0' is missing final new line
 Errors were encountered while processing:
  /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24.22,45netbook9_lpiadeb
 Processing was halted because there were too many errors.
 E: Sub-process /usr/bin/dpkg returned an error code (1)
  A package failed to install.  Trying to recover:
 

 Tried following code in terminal:
 

 jackie@jackie:~$ echo -en '\n' | sudo tee -a /var/lib/dpkg/info/libxcb-shape0 
 [sudo] password for jackie:  
  
 jackie@jackie:~$  
 

 Got the message below after I ran the code
 

 Error Message
 

 E: /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package `libxcb-shape0' is missing final newline 
 

 Detail Message
 (Reading database...dpkg: error processing / var/cashe/apt/archives/linus-image-2.6.24-22-lpia_2.6.24-22.45netboo9_lpia.deb (--unpack):
     files list file for package 'libxcb-shape0' is missing final new line
 Errors were encountered while processing:
  /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netboo9_lpia.deb
 Processing was halted because there were too many erros.
 E: Sub – process /usr/bin/dpkg returned an error code (1)
 A package failed to install. Trying to recover:
 :confused:

Thank you for your help.

Use the following code in terminal:
[SIZE=4][SIZE=3]cd /var/lib/dpkg/info
sudo rm  libxcb-shape0.list
sudo apt-get --reinstall install libxcb-shape0[/SIZE][/SIZE]

---

