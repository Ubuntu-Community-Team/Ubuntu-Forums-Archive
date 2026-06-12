---
title: "Software center apears empty"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by Trandre on 2010-03-15
I had a thread on this issue without knowing what was wrong(error in Ubuntu). Now the issue is singeled I posted a new thread wich is more tidy and with one question.

Service center opens but apears empty and synaptics will not open and returns an error message which says:
E: Problem parsing dependency Conflicts
E: Error occurred during processing of Xserve xorg-video-cirrus (NewVersion1)
E: Problem with MergeList / var / lib / dpkg / status
E: The package lists or statusfil could be read or opened.
E: _cache-> open () failed, please report.

I ran the command ubuntu-bug service center and recieved this output:


famfem @ famfem-desktop: ~ $ ubuntu-bug service center 
Trace Back (most recent call last): 
File "/ usr / share / apport / apport-gtk", line 348, in <Module> 
app.run_argv () 
File "/ usr/lib/python2.6/dist-packages/apport/ui.py", line 435, in run_argv 
return self.run_report_bug () 
File "/ usr/lib/python2.6/dist-packages/apport/ui.py", line 345, in run_report_bug 
self.collect_info (symptom_script) 
File "/ usr/lib/python2.6/dist-packages/apport/ui.py", line 601, in collect_info 
icthread.exc_raise () 
File "/ usr/lib/python2.6/dist-packages/apport/REThread.py", line 36, in run 
self._retval = self.__target (* self.__args, ** self.__kwargs) 
File "/ usr/lib/python2.6/dist-packages/apport/ui.py", line 65, in thread_collect_info 
report.add_package_info (package) 
File "/ usr/lib/python2.6/dist-packages/apport/report.py", line 186, in add_package_info 
version = packaging.get_version (package) 
File "/ usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 65, in get_version 
pkg = self._apt_pkg (package) 
File "/ usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 58, in _apt_pkg 
return self._cache () [package] 
File "/ usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 49, in _cache 
self._apt_cache = apt.Cache () 
File "/ usr/lib/python2.6/dist-packages/apt/cache.py", line 72, in __init__ 
self.open (progress) 
File "/ usr/lib/python2.6/dist-packages/apt/cache.py", line 108, in open 
self._cache = apt_pkg.GetCache (progress) 
System Error: E: Problem parsing dependency Conflicts, E: Error occurred during processing of Xserve xorg-video-cirrus (NewVersion1), E: Problem with MergeList / var / lib / dpkg / status, E: Package list or state file could not be interpreted or opens

---

### Post by Trandre on 2010-03-16
Please, could anyone assist me on this issue?

Trandre

---

### Post by J V on 2010-03-16
run ```
sudo apt-get update
```

---

### Post by fatality_uk on 2010-03-16
An update will almost certainly solve the problem
Please post back if it doenst

---

### Post by Trandre on 2010-03-16
Thank you for your answer. I have run sudo apt-get update it seems to have a depenency conflict. 

This is what I have tried:
- sudo apt-get update
- Manually search for best repository in the attached picture program sources. 
- located  var / lib / dpkg / status, this is wright protected     and I cannot delete it. Further it comes in status and status.old as seen on attached print screen. 

- Deleted deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/)  stable non-free main in the sources.list which removed some warnings.

- And i have a red warning sign on the taskbar beside the time in the upper right corner.





Result sudo apt-get update

famfem @ famfem-desktop: ~ $ sudo apt-get update
[sudo] password for famfem:
Found [http://ftp.port80.se](http://ftp.port80.se) karmic Release.gpg
Found [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic / partner Translation-nb
Found [http://ftp.port80.se](http://ftp.port80.se) karmic / main Translation-nb
Found [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Found [http://ftp.port80.se](http://ftp.port80.se) karmic / restricted Translation-nb
Found [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic / free Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic / universe Translation-nb
Found [http://ftp.port80.se](http://ftp.port80.se) karmic / multiverse Translation-nb
Found [http://archive.canonical.com](http://archive.canonical.com) karmic / partner Packages
Get: 1 [http://ftp.port80.se](http://ftp.port80.se) karmic-updates Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic / non-free Translation-nb
Found [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/main Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/restricted Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/universe Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/multiverse Translation-nb
Extract: 2 [http://ftp.port80.se](http://ftp.port80.se) karmic-security Release.gpg [189B]
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-security/main Translation-nb
Found [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic / free Packages
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-security/restricted Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-security/universe Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-security/multiverse Translation-nb
Found [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic / non-free Packages
Get: 3 [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed Release.gpg [189B]
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/restricted Translation-nb
Get: 4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/main Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/multiverse Translation-nb
Ign [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/universe Translation-nb
Found [http://ftp.port80.se](http://ftp.port80.se) karmic Release
Get: 5 [http://ftp.port80.se](http://ftp.port80.se) karmic-updates Release [44.1 KB]
Get: 6 [http://ftp.port80.se](http://ftp.port80.se) karmic-security Release [44.1 KB]
Get: 7 [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed Release [44.1 KB]
Found [http://ftp.port80.se](http://ftp.port80.se) karmic / main Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic / restricted Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic / universe Packages
Found [http://ftp.port80.se](http://ftp.port80.se) karmic / multiverse Packages
Get: 8 [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/main Packages [188kB]
Retrieve: 9 [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/restricted Packages [14B]
Extract: 10 [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/universe Packages [110kB]
Extract: 11 [http://ftp.port80.se](http://ftp.port80.se) karmic-updates/multiverse Packages [7 369B]
Extract: 12 [http://ftp.port80.se](http://ftp.port80.se) karmic-security/main Packages [78.6 kB]
Extract: 13 [http://ftp.port80.se](http://ftp.port80.se) karmic-security/restricted Packages [14B]
Extract: 14 [http://ftp.port80.se](http://ftp.port80.se) karmic-security/universe Packages [37.6 kB]
Extract: 15 [http://ftp.port80.se](http://ftp.port80.se) karmic-security/multiverse Packages [1 666B]
Extract: 16 [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/restricted Packages [14B]
Extract: 17 [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/main Packages [68.6 kB]
Extract: 18 [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/multiverse Packages [14B]
Extract: 19 [http://ftp.port80.se](http://ftp.port80.se) karmic-proposed/universe Packages [18.6 kB]
Ign [http://dl.google.com](http://dl.google.com) stable / main Translation-nb
Extract: 20 [http://dl.google.com](http://dl.google.com) stable Release [2 540B]
Extract: 21 [http://dl.google.com](http://dl.google.com) stable / main Packages [922B]
Retrieved 647kB in 2min 5s (5 173B / s)
Reading package lists ... Wrong
E: Problem parsing dependency Conflicts
E: Error occurred during processing of Xserve xorg-video-cirrus (NewVersion1)
E: Problem with MergeList / var / lib / dpkg / status
E: Package list or state file could not be interpreted or open.

---

### Post by Trandre on 2010-03-16
I ran this command after I read a post and got:

famfem @ famfem-desktop: ~ $ sudo dpkg-reconfigure-a
dpkg-query: parsing error in file '/ var / lib / dpkg / status' near line 19225 package 'Xserve xorg-video-cirrus':
 "Replaces" field, missing package name, or root, where it would be a package name
/ usr / sbin / dpkg-reconfigure: acpi-support is not installed

My  var / lib / dpkg / status is block for editing.

Any Suggestions?

When I look at Properties it is root that is the owner and I cant edit it. How can I change this?

---

### Post by lidex on 2010-03-16
This command:
```
gksudo gedit /var/lib/dpkg/status
```

---

### Post by Trandre on 2010-03-20
Thank you all for your help, the software center is now working. 

Summary of solution:
I ran(thanks to lidex) gksudo gedit /var/lib/dpkg/status
And deleted the code below from my status document.
Then I ran sudo apt-get update

Presto I'm back in business.

```
Package: xserver-xorg-video-cirrus
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 164
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 1:1.3.1-1ubuntu2
Replaces: xserver-xorg (<< 6.8.2-35), 
Provides: xserver-xorg-video-5
Depends: libc6 (>= 2.4), xserver-xorg-core (>= 2:1.6.2)
Conflicts: 
Description: X.Org X server -- Cirrus display driver
 This package provides the driver for the Cirrus Logic family of video
 cards.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This package is built from the X.org xf86-video-cirrus driver module.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
```

result sudo apt-get update:popcorn:

```
famfem@famfem-desktop:~$ gksudo gedit /var/lib/dpkg/status
famfem@famfem-desktop:~$ sudo apt-get update
Funnet http://archive.canonical.com karmic Release.gpg
Ign http://archive.canonical.com karmic/partner Translation-nb                
Funnet http://ftp.port80.se karmic Release.gpg                                
Funnet http://packages.medibuntu.org karmic Release.gpg                        
Ign http://packages.medibuntu.org karmic/free Translation-nb                   
Funnet http://archive.canonical.com karmic Release                             
Funnet http://ftp.port80.se karmic/main Translation-nb                         
Ign http://packages.medibuntu.org karmic/non-free Translation-nb               
Funnet http://packages.medibuntu.org karmic Release                            
Hent:1 http://dl.google.com stable Release.gpg [189B]                          
Funnet http://ftp.port80.se karmic/restricted Translation-nb                   
Ign http://ftp.port80.se karmic/universe Translation-nb                        
Funnet http://archive.canonical.com karmic/partner Packages                    
Funnet http://packages.medibuntu.org karmic/free Packages   
Funnet http://archive.canonical.com karmic/partner Sources
Funnet http://packages.medibuntu.org karmic/non-free Packages
Funnet http://packages.medibuntu.org karmic/free Sources    
Funnet http://packages.medibuntu.org karmic/non-free Sources
Funnet http://ftp.port80.se karmic/multiverse Translation-nb
Hent:2 http://ftp.port80.se karmic-updates Release.gpg [189B]
Ign http://ftp.port80.se karmic-updates/main Translation-nb
Ign http://ftp.port80.se karmic-updates/restricted Translation-nb
Ign http://ftp.port80.se karmic-updates/universe Translation-nb
Ign http://ftp.port80.se karmic-updates/multiverse Translation-nb
Hent:3 http://ftp.port80.se karmic-security Release.gpg [189B]
Ign http://ftp.port80.se karmic-security/main Translation-nb
Ign http://ftp.port80.se karmic-security/restricted Translation-nb
Ign http://ftp.port80.se karmic-security/universe Translation-nb
Ign http://ftp.port80.se karmic-security/multiverse Translation-nb
Hent:4 http://ftp.port80.se karmic-proposed Release.gpg [189B]
Ign http://ftp.port80.se karmic-proposed/restricted Translation-nb
Ign http://ftp.port80.se karmic-proposed/main Translation-nb
Ign http://ftp.port80.se karmic-proposed/multiverse Translation-nb
Ign http://ftp.port80.se karmic-proposed/universe Translation-nb
Funnet http://ftp.port80.se karmic Release
Hent:5 http://ftp.port80.se karmic-updates Release [44,1kB]   
Hent:6 http://ftp.port80.se karmic-security Release [44,1kB]      
Hent:7 http://ftp.port80.se karmic-proposed Release [44,1kB]           
Funnet http://ftp.port80.se karmic/main Packages                        
Funnet http://ftp.port80.se karmic/restricted Packages
Funnet http://ftp.port80.se karmic/universe Packages            
Funnet http://ftp.port80.se karmic/multiverse Packages
Hent:8 http://ftp.port80.se karmic-updates/main Packages [191kB]
Hent:9 http://ftp.port80.se karmic-updates/restricted Packages [14B]
Hent:10 http://ftp.port80.se karmic-updates/universe Packages [112kB]
Hent:11 http://ftp.port80.se karmic-updates/multiverse Packages [7*369B] 
Hent:12 http://ftp.port80.se karmic-security/main Packages [81,3kB]      
Hent:13 http://ftp.port80.se karmic-security/restricted Packages [14B]    
Hent:14 http://ftp.port80.se karmic-security/universe Packages [38,8kB]   
Hent:15 http://ftp.port80.se karmic-security/multiverse Packages [1*666B]    
Hent:16 http://ftp.port80.se karmic-proposed/restricted Packages [14B]       
Hent:17 http://ftp.port80.se karmic-proposed/main Packages [69,4kB]          
Hent:18 http://ftp.port80.se karmic-proposed/multiverse Packages [544B]   
Hent:19 http://ftp.port80.se karmic-proposed/universe Packages [21,0kB]   
Ign http://dl.google.com stable/main Translation-nb                            
Hent:20 http://dl.google.com stable Release [2*540B]
Hent:21 http://dl.google.com stable/main Packages [920B]
Hentet 659kB på 2min 0s (5*460B/s)
Leser pakkelister ... Ferdig

```

---

