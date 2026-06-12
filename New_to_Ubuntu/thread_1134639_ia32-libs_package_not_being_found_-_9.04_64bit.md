---
title: "ia32-libs package not being found - 9.04 64bit"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by tricia56 on 2009-04-23
I have been struggling with this problem for few weeks, first in 8.10 and now in 9.04 64bit.  I am trying to follow the guide at [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) and fall at the first hurdle.  When I try to install as per these instructions I continually get this error

muriel@rimu-laptop:~$ sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar
[sudo] password for muriel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswfdec-0.8-0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  swfdec-mozilla
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 303kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 127643 files and directories currently installed.)
Removing swfdec-mozilla ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
E: Couldn't find package ia32-libs



I have had a good look round and there is Bug #190227 but it seems to only partially address my probs.  I have tried to download from the US server rather than my local but this doesn't seem to work.  And to be honest I am not really sure what I am doing when I do this. And why? 

What can I do to solve this?  My head is turning to mush on this prob that I have been working on for month on and off.

tricia

---

### Post by cariboo on 2009-04-24
I just installed Jaunty yesterday and usually the first thing I do on a clean install is to install the ubuntu-restricted-extras meta package, it includes flash, jave and most of the codecs you need for most types of audio/video media. the ia32-libs package always gets installed.

---

### Post by tricia56 on 2009-04-27
*I just installed Jaunty yesterday and usually the first thing I do on a clean install is to install the ubuntu-restricted-extras meta package, it includes flash, jave and most of the codecs you need for most types of audio/video media. the ia32-libs package always gets installed*

that is what I am trying to install,  and I am always getting the error that ia32-libs not found.

---

### Post by oldos2er on 2009-04-27
Check Software Sources to make sure you have the universe repository enabled, then run
```
sudo apt-get update && sudo apt-get install ia32-libs
```

---

### Post by tricia56 on 2009-04-28
Yes I have the universe repository enabled in software services.

Then this

muriel@rimu-laptop:~$ sudo apt-get update && sudo apt-get install ia32-libs
[sudo] password for muriel: 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release.gpg
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Translation-en_NZ                 
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Translation-en_NZ           
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Translation-en_NZ             
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Translation-en_NZ           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Translation-en_NZ         
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Translation-en_NZ   
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Translation-en_NZ     
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security Release.gpg
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/main Translation-en_NZ        
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/universe Translation-en_NZ    
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/multiverse Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security Release                       
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_NZ
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_NZ
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs


Any ideas on what next?

tricia

---

### Post by oldos2er on 2009-04-28
Seeing as how you have several "Ign" errors, have you tried different servers?

---

### Post by tricia56 on 2009-04-29
Yeah I have changed to US and Australian servers and the result is always the same.  

Don't quite know what to try next!

Full reinstall?

tricia

---

### Post by oldos2er on 2009-04-29
Here's a direct link: [http://packages.ubuntu.com/jaunty/amd64/ia32-libs/download](http://packages.ubuntu.com/jaunty/amd64/ia32-libs/download)

---

### Post by tricia56 on 2009-05-01
thanks Ann, I had already discovered those download pages but was hesitant because of the warning.  However, I went ahead and downloaded ia32libs and I now have this error

error: Wrong architecture 'amd64'

I have googled and it would indicate that I am not running 64bit but resuts of uname -a

muriel@rimu-laptop:~$ uname -a
Linux rimu-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

muriel@rimu-laptop:~$ cat /proc/version
Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009



I understood that the i686 indicated 64bit?  Sorry, I am not understanding this now.  I would just like to install ubuntu-restricted-extras. 

tricia

---

### Post by tricia56 on 2009-05-01
Never mind.  I just answered my own question.  Slaps head on desk!!!

---

### Post by constejo on 2009-05-11
> **tricia56 said:**
> muriel@rimu-laptop:~$ uname -a
Linux rimu-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
[...]
I understood that the i686 indicated 64bit?  Sorry, I am not understanding this now.  I would just like to install ubuntu-restricted-extras.

Just for reference to other users - a current Intel Core2Duo will bring as output of "uname -a" something like:

Linux hostname 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

I think the "x86_64" is the most important part... ;-)

---

