---
title: "mobile media converter for 64 Bit Ubuntu"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by powel212 on 2009-03-14
Hi

I recently switched over to 64Bit Ubuntu. Wow. Fast. Love it.

The only program I can't get to run in 64Bit is Mobile Media conerter. 

can I get Mobile Media Converter working in 64Bit?

powel

---

### Post by 67GTA on 2009-04-12
Just ran across your post. The i386 version will run fine. You just have to install it manually and "force" it. Download the .deb package (1.4.2 is out now). Open a terminal and run ```
sudo dpkg --force-architecture -i <path_to_package>
``` You can also type or copy/paste ```
sudo dpkg --force-architecture -i
``` into the terminal, leave a space, and then drag the package on to the terminal window.


EDIT: This will also work with most i386 packages if you can't find the 64 bit version.

---

### Post by 67GTA on 2009-04-12
For some reason the newest package doesn't install correctly under 64 bit. After installing, right click on the menu icon, select "Edit Menus". Find MMC under Sound and Video. Right click on the MMC entry and select "properties". Then change the command to ```
/opt/MIKSOFT/MobileMediaConverter/lib/mmc
```

---

### Post by hyper_ch on 2009-04-12
but you'll have to install the ia32 libs also I think... or is it ia64... search in synaptic, you'll find it.

---

### Post by 67GTA on 2009-04-12
Yes, ia32libs. I forgot about that. I don't think it was installed by default. Something else I installed pulled it in as a dependent.

---

### Post by adamsu on 2009-07-30
Thanks to you all, especially 67GTA, this was really helpful.
:P

---

### Post by prvteprts on 2009-11-25
Thanks! I had the same problem. The solution worked.

---

### Post by bangbong on 2010-03-03
+1 

Working... without fixing appli properties.
installed mmc-1.5.0

---

### Post by kashuk on 2010-06-20
I tried the  fix below , but i get the following error 


/opt/MIKSOFT/MobileMediaConverter/lib/mmc: symbol lookup error: /usr/lib32/libdirectfb-1.2.so.0: undefined symbol: fusion_config_usage


any idea?

---

### Post by waterboy0911 on 2010-09-17
I still have problem.. 

it says error: wrong architecture 'i386'

here is the code on my terminal
```

jerald@jerald-laptop:~$ sudo apt-get install mmc_1.6.1
[sudo] password for jerald: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mmc_1.6.1
jerald@jerald-laptop:~$ sudo dpkg --force-architecture -i '/home/jerald/Downloads/mmc_1.6.1_i386.deb' sudo dpkg --force-architecture -i'/home/jerald/Desktop/mmc_1.6.1_i386.deb' 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package mobilemediaconverter.
(Reading database ... 181052 files and directories currently installed.)
Unpacking mobilemediaconverter (from .../Downloads/mmc_1.6.1_i386.deb) ...
dpkg: error processing sudo (--install):
 cannot access archive: No such file or directory
dpkg: error processing dpkg (--install):
 cannot access archive: No such file or directory
dpkg: error processing --force-architecture (--install):
 cannot access archive: No such file or directory
dpkg: error processing -i/home/jerald/Desktop/mmc_1.6.1_i386.deb (--install):
 cannot access archive: No such file or directory
Setting up mobilemediaconverter (1.6.1) ...

Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_PH.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 sudo
 dpkg
 --force-architecture
 -i/home/jerald/Desktop/mmc_1.6.1_i386.deb
jerald@jerald-laptop:~$

```

thanks..

---

### Post by Brejcha on 2010-12-02
'/home/jerald/Downloads/mmc_1.6.1_i386.deb' sudo dpkg --force-architecture -i'/home/jerald/Desktop/mmc_1.6.1_i386.deb' 

Remove the (') from the beginning and end so it looks like this

/home/jerald/Downloads/mmc_1.6.1_i386.deb' sudo dpkg --force-architecture -i'/home/jerald/Desktop/mmc_1.6.1_i386.deb

that will do the trick

---

### Post by TimEnid on 2011-01-01
i keep getting this message when i try to convert something

> >> Command executed:
"/opt/MIKSOFT/MobileMediaConverter/lib/ffmpeg" -y -i "/media/WD_/Skyline - Blu ray/Skyline 2010 720p BluRay DTS x264-DNL/Skyline 2010 720p BluRay DTS x264-DNL.mkv" -f mp4 -vcodec mpeg4 -s 480x320 -r 25 -b 700k -acodec libfaac -ac 2 -ar 24000 -ab 128k -map_meta_data "/home/tim/Desktop/Skyline 2010 720p BluRay DTS x264-DNL.mp4":"/media/WD_/Skyline - Blu ray/Skyline 2010 720p BluRay DTS x264-DNL/Skyline 2010 720p BluRay DTS x264-DNL.mkv" "/home/tim/Desktop/Skyline 2010 720p BluRay DTS x264-DNL.mp4"

>> Result: 
/opt/MIKSOFT/MobileMediaConverter/lib/ffmpeg: error while loading shared libraries: libfaac.so.0: cannot open shared object file: No such file or directory
----------------------------

---

### Post by Mawy on 2011-01-02
Download the 32 bit version of libfaac from [Ubuntu’s package site]("http://packages.ubuntu.com/") and extract the files libfaac.so.0 and libfaac.so.0.0.0 to 

/opt/MIKSOFT/MobileMediaConverter/lib/mmc libs/

Cheers,
Mawy

---

### Post by Paqman on 2011-01-02
You might want to take a look at Arista Transcoder. It's a nice simple video converter that comes with presets for tons of devices. It's 64-bit and multi-threaded. You can get it from Ubuntu Software Centre.

---

