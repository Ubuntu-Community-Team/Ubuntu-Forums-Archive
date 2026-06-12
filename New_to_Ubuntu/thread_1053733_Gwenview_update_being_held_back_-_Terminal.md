---
title: "Gwenview update being held back - Terminal"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Firestem4 on 2009-01-28
When i try to upgrade in CLI, i get this. 

```
icarus@icarus-linux:~$ sudo apt-get upgrade
[sudo] password for icarus:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  gwenview
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
icarus@icarus-linux:~$


```

i tried sudo apt-get upgrade -f or sudo apt-get install -f, neither works (to be honest im sure if that would even work lol. Its what adept recommended when i was upgrading to KDE 4.2

Can anyone please help me resolve this issue?

Would uninstalling and then installing Gwenview help?

---

### Post by icheyne on 2009-01-29
I'm guessing here, but what happens if you type:
```
sudo apt-get dist-upgrade
```

---

### Post by Firestem4 on 2009-01-29
It says the same thing as before. 1 not upgraded - Gwenview

---

### Post by icheyne on 2009-01-29
```
sudo aptitude reinstall gwenview
```

---

### Post by Firestem4 on 2009-01-29
Hm. well it did a sucessful reinstall of gwenview but it still shows that the upgrade is being held back.

i tried sudo aptitude upgrade but it says the same thing too.

---

### Post by icheyne on 2009-01-29
```
sudo aptitude unhold gwenview
```

Otherwise I'm out of ideas - sorry.

---

### Post by Firestem4 on 2009-01-29
It looks as if it is doing something but then it doesn't in the end.

```
icarus@icarus-linux:~$ sudo aptitude unhold gwenview
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

icarus@icarus-linux:~$

```

Thanks for the help. Gwenview Does work atleast so i guess i can forget about this problem.

---

### Post by unutbu on 2009-01-29
I'm not sure I can help you, but just in case, would you please post```

apt-cache policy gwenview
lsb_release -a

```

---

### Post by Firestem4 on 2009-01-29
```
icarus@icarus-linux:~$ apt-cache policy gwenview
gwenview:
  Installed: 4:4.1.3-0ubuntu1~intrepid1
  Candidate: 4:4.2.0-0ubuntu1~intrepid1~ppa3
  Version table:
     4:4.2.0-0ubuntu1~intrepid1~ppa3 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
 *** 4:4.1.3-0ubuntu1~intrepid1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
        100 /var/lib/dpkg/status
     4:4.1.2-0ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
icarus@icarus-linux:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid
icarus@icarus-linux:~$
```

---

### Post by unutbu on 2009-01-29
It looks like you have gwenview version 4.1.3-0ubuntu1~intrepid1
installed (from the official repo). The newer version  4.2.0-0ubuntu1~intrepid1~ppa3 comes from ppa.launchpad.net. 

Unless there is functionality in version 4.2.0 that you want and which is missing from 4.1.3, I wouldn't worry about upgrading.

However, if you'd like to find out why the package is being held back, please post ```
apt-cache show gwenview
```

This will show the dependencies required for version 4.2.0.

---

### Post by Firestem4 on 2009-01-29
```
icarus@icarus-linux:~$ apt-cache show gwenview
Package: gwenview                             
Source: kdegraphics                           
Priority: extra                               
Section: graphics                             
Installed-Size: 2300                          
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Architecture: i386                                             
Version: 4:4.2.0-0ubuntu1~intrepid1~ppa3                       
Replaces: gwenview-kde4                                        
Depends: kdebase-runtime (>= 4:4.1.96), kdelibs5 (>= 4:4.1.96), libc6 (>= 2.4), libexiv2-4, libgcc1 (>= 1:4.1.1), libjpeg62, libkipi6, libqt4-dbus (>= 4.4.3), libqt4-network (>= 4.4.3), libqt4-svg (>= 4.4.3), libqt4-xml (>= 4.4.3), libqtcore4 (>= 4.4.3), libqtgui4 (>= 4.4.3), libsoprano4 (>= 2.1.64), libstdc++6 (>= 4.1.1)     
Conflicts: gwenview-kde4                                                          
Filename: pool/main/k/kdegraphics/gwenview_4.2.0-0ubuntu1~intrepid1~ppa3_i386.deb 
Size: 1293576                                                                     
MD5sum: dd66ddce81aeb59bb4740a6c4cb149d7                                          
Description: image viewer for KDE 4                                               
 Gwenview is an image viewer, ideal for browsing and displaying a collection of   
 images.  It is capable of showing images in a full-screen slideshow view and     
 making simple adjustments, such as rotating or cropping images.                  
 .                                                                                
 This package is part of the KDE 4 graphics module.                               

Package: gwenview
Priority: extra  
Section: graphics
Installed-Size: 2084
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: i386                                                             
Source: kdegraphics                                                            
Version: 4:4.1.3-0ubuntu1~intrepid1                                            
Replaces: gwenview-kde4                                                        
Depends: kdebase-runtime (>= 4:4.1.2), kdelibs5 (>= 4:4.1.3), libc6 (>= 2.4), libexiv2-4, libgcc1 (>= 1:4.1.1), libjpeg62, libkipi5, libqt4-svg (>= 4.4.3), libqtcore4 (>= 4.4.3), libqtgui4 (>= 4.4.3), libstdc++6 (>= 4.1.1)                        
Conflicts: gwenview-kde4                                                          
Filename: pool/main/k/kdegraphics/gwenview_4.1.3-0ubuntu1~intrepid1_i386.deb      
Size: 1218134                                                                     
MD5sum: de83a15fed2a3af71cb9c2d4ed34cdb2                                          
SHA1: 930e62133d4301db4d69e332fc58720fcecb2c60                                    
SHA256: 73e7594f670fb43e56cf1a9e31f3e7e649a8777c945210bed49b792bf7da0b77          
Description: image viewer for KDE 4
 Gwenview is an image viewer, ideal for browsing and displaying a collection of
 images.  It is capable of showing images in a full-screen slideshow view and
 making simple adjustments, such as rotating or cropping images.
 .
 This package is part of the KDE 4 graphics module.
Homepage: http://www.kde.org/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: kubuntu-desktop, edubuntu-desktop-kde

Package: gwenview
Priority: optional
Section: graphics
Installed-Size: 2080
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: i386
Source: kdegraphics
Version: 4:4.1.2-0ubuntu3
Replaces: gwenview-kde4
Depends: kdebase-runtime (>= 4:4.1.2), kdelibs5 (>= 4:4.1.2), libc6 (>= 2.4), libexiv2-4, libgcc1 (>= 1:4.1.1), libjpeg62, libkipi5, libqt4-svg (>= 4.4.3), libqtcore4 (>= 4.4.3), libqtgui4 (>= 4.4.3), libstdc++6 (>= 4.1.1)
Conflicts: gwenview-kde4
Filename: pool/main/k/kdegraphics/gwenview_4.1.2-0ubuntu3_i386.deb
Size: 1217498
MD5sum: aef3f41cf81ea5faf5dc29df0715c829
SHA1: 66f44b1249585d3b4513de720e7efac3462ff598
SHA256: 214e2813bf3edb65fa800fb20761e3ca444f3f77ffea90bea8b3b2309cb22068
Description: image viewer for KDE 4
 Gwenview is an image viewer, ideal for browsing and displaying a collection of
 images.  It is capable of showing images in a full-screen slideshow view and
 making simple adjustments, such as rotating or cropping images.
 .
 This package is part of the KDE 4 graphics module.
Homepage: http://www.kde.org/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: kubuntu-desktop, edubuntu-desktop-kde


```

---

### Post by unutbu on 2009-01-29
Okay. Note that in the "apt-cache show" output the dependencies for version 4.2.0 are these:

```
Depends: kdebase-runtime (>= 4:4.1.96), kdelibs5 (>= 4:4.1.96), libc6 (>= 2.4), libexiv2-4, libgcc1 (>= 1:4.1.1), libjpeg62, libkipi6, libqt4-dbus (>= 4.4.3), libqt4-network (>= 4.4.3), libqt4-svg (>= 4.4.3), libqt4-xml (>= 4.4.3), libqtcore4 (>= 4.4.3), libqtgui4 (>= 4.4.3), libsoprano4 (>= 2.1.64), libstdc++6 (>= 4.1.1)
``` 

So let's run:

```
apt-cache policy kdebase-runtime kdelibs5 libc6 libexiv2-4 libgcc1 libjpeg62 libkipi6 libqt4-dbus libqt4-network libqt4-svg libqt4-xml libqtcore4 libqtgui4 libsoprano4 libstdc++6   
```  
This will show us what version of these packages you have installed, and what the highest version available is. 

I'm guessing that whoever compiled gwenview version 4.2.0 at ppa.launchpad.net
used a custom-compiled version of one of these packages which is newer than the ones offered in the official repos. You'll have to compile this newer version or enable a third-party repository that offers it in order to upgrade gwenview.

---

### Post by Firestem4 on 2009-01-29
```
icarus@icarus-linux:~$ apt-cache policy kdebase-runtime kdelibs5 libc6 libexiv2-4 libgcc1 libjpeg62 libkipi6 libqt4-dbus libqt4-network libqt4-svg libqt4-xml libqtcore4 libqtgui4 libsoprano4 libstdc++6                                             
kdebase-runtime:                                                                  
  Installed: 4:4.2.0-0ubuntu1~intrepid1~ppa3                                      
  Candidate: 4:4.2.0-0ubuntu1~intrepid1~ppa3                                      
  Version table:                                                                  
 *** 4:4.2.0-0ubuntu1~intrepid1~ppa3 0                                            
        500 http://ppa.launchpad.net intrepid/main Packages                       
        100 /var/lib/dpkg/status                                                  
     4:4.1.3-0ubuntu1~intrepid1 0                                                 
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages           
     4:4.1.2-0ubuntu6 0                                                           
        500 http://us.archive.ubuntu.com intrepid/main Packages                   
kdelibs5:                                                                         
  Installed: 4:4.2.0-0ubuntu1~intrepid1~ppa3                                      
  Candidate: 4:4.2.0-0ubuntu1~intrepid1~ppa3                                      
  Version table:                                                                  
 *** 4:4.2.0-0ubuntu1~intrepid1~ppa3 0                                            
        500 http://ppa.launchpad.net intrepid/main Packages                       
        100 /var/lib/dpkg/status                                                  
     4:4.1.3-0ubuntu1~intrepid4 0                                                 
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages           
     4:4.1.2-0ubuntu10 0                                                          
        500 http://us.archive.ubuntu.com intrepid/main Packages                   
libc6:                                                                            
  Installed: 2.8~20080505-0ubuntu8                                                
  Candidate: 2.8~20080505-0ubuntu8                                                
  Version table:                                                                  
 *** 2.8~20080505-0ubuntu8 0                                                      
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages           
        100 /var/lib/dpkg/status                                                  
     2.8~20080505-0ubuntu7 0                                                      
        500 http://us.archive.ubuntu.com intrepid/main Packages                   
libexiv2-4:                                                                       
  Installed: 0.17-1ubuntu1                                                        
  Candidate: 0.17-1ubuntu1                                                        
  Version table:                                                                  
 *** 0.17-1ubuntu1 0                                                              
        500 http://us.archive.ubuntu.com intrepid/main Packages                   
        100 /var/lib/dpkg/status                                                  
libgcc1:                                                                          
  Installed: 1:4.3.2-1ubuntu12                                                    
  Candidate: 1:4.3.2-1ubuntu12                                                    
  Version table:                                                                  
 *** 1:4.3.2-1ubuntu12 0                                                          
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages           
        100 /var/lib/dpkg/status                                                  
     1:4.3.2-1ubuntu11 0                                                          
        500 http://us.archive.ubuntu.com intrepid/main Packages                   
libjpeg62:                                                                        
  Installed: 6b-14                                                                
  Candidate: 6b-14                                                                
  Version table:                                                                  
 *** 6b-14 0                                                                      
        500 http://us.archive.ubuntu.com intrepid/main Packages                   
        100 /var/lib/dpkg/status                                                  
libkipi6:                                                                         
  Installed: (none)                                                               
  Candidate: 4:4.2.0-0ubuntu1~intrepid1~ppa3                                      
  Version table:                                                                  
     4:4.2.0-0ubuntu1~intrepid1~ppa3 0                                            
        500 http://ppa.launchpad.net intrepid/main Packages                       
libqt4-dbus:                                                                      
  Installed: 4.4.3-0ubuntu1.1                                                     
  Candidate: 4.4.3-0ubuntu1.1                                                     
  Version table:                                                                  
 *** 4.4.3-0ubuntu1.1 0                                                           
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages           
        100 /var/lib/dpkg/status                                                  
     4.4.3-0ubuntu1 0                                                             
        500 http://us.archive.ubuntu.com intrepid/main Packages                   
libqt4-network:                                                                   
  Installed: 4.4.3-0ubuntu1.1                                                     
  Candidate: 4.4.3-0ubuntu1.1                                                     
  Version table:                                                                  
 *** 4.4.3-0ubuntu1.1 0                                                           
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages           
        100 /var/lib/dpkg/status                                                  
     4.4.3-0ubuntu1 0                                                             
        500 http://us.archive.ubuntu.com intrepid/main Packages                   
libqt4-svg:                                                                       
  Installed: 4.4.3-0ubuntu1.1                                                     
  Candidate: 4.4.3-0ubuntu1.1                                                     
  Version table:                                                                  
 *** 4.4.3-0ubuntu1.1 0                                                           
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages           
        100 /var/lib/dpkg/status                                                  
     4.4.3-0ubuntu1 0                                                             
        500 http://us.archive.ubuntu.com intrepid/main Packages                   
libqt4-xml:                                                                       
  Installed: 4.4.3-0ubuntu1.1                                                     
  Candidate: 4.4.3-0ubuntu1.1                                                     
  Version table:
 *** 4.4.3-0ubuntu1.1 0
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages
        100 /var/lib/dpkg/status
     4.4.3-0ubuntu1 0
        500 http://us.archive.ubuntu.com intrepid/main Packages
libqtcore4:
  Installed: 4.4.3-0ubuntu1.1
  Candidate: 4.4.3-0ubuntu1.1
  Version table:
 *** 4.4.3-0ubuntu1.1 0
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages
        100 /var/lib/dpkg/status
     4.4.3-0ubuntu1 0
        500 http://us.archive.ubuntu.com intrepid/main Packages
libqtgui4:
  Installed: 4.4.3-0ubuntu1.1
  Candidate: 4.4.3-0ubuntu1.1
  Version table:
 *** 4.4.3-0ubuntu1.1 0
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages
        100 /var/lib/dpkg/status
     4.4.3-0ubuntu1 0
        500 http://us.archive.ubuntu.com intrepid/main Packages
libsoprano4:
  Installed: 2.1.64+dfsg.1-0ubuntu1~intrepid1~ppa1
  Candidate: 2.1.64+dfsg.1-0ubuntu1~intrepid1~ppa1
  Version table:
 *** 2.1.64+dfsg.1-0ubuntu1~intrepid1~ppa1 0
        500 http://ppa.launchpad.net intrepid/main Packages
        100 /var/lib/dpkg/status
     2.1.1+dfsg.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com intrepid/main Packages
libstdc++6:
  Installed: 4.3.2-1ubuntu12
  Candidate: 4.3.2-1ubuntu12
  Version table:
 *** 4.3.2-1ubuntu12 0
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages
        100 /var/lib/dpkg/status
     4.3.2-1ubuntu11 0
        500 http://us.archive.ubuntu.com intrepid/main Packages
icarus@icarus-linux:~$

```

Apparantly I don't have libkipi6 installed with the packages.

---

### Post by unutbu on 2009-01-29
Huh. That is interesting. You are right, apt-cache shows libkipi6 is not installed.

The Intrepid version of gwenview (version 4.1.3) depends on libkipi5, rather than libkipi6. According to "man apt-get", the "apt-get upgrade" command will under no circumstances install new packages. Since no version of libkipi6 was installed, upgrading gwenview failed.

So perhaps what you need to do is
```

sudo apt-get install libkipi6
sudo apt-get upgrade

```

---

### Post by Firestem4 on 2009-01-29
That worked. It removed libkipi-common and libkipi5, and upgraded gwenview.

Thanks so much for the help unutbu!


Edit: I didn't need to upgrade after i installed libkipi6, It upgraded gwenview in the process.

---

### Post by icheyne on 2009-01-30
Good work Unutbu. That was well out of my league.

---

### Post by mbugno on 2009-02-19
Thanks all. Gwenview was being held back on the auto update cycle in the apt gui. I was reading the thread and said to myself, self try **[SIZE="3"]sudo apt-get install gwenview[/SIZE]**. This WORKED! 1 packed upgraded, 5 packages discarded etc. the new lib was part of the install. It did it all alone without any pre library dependency to install. Database took care of it. 

Once again thanks all. I was stumped as to why it was held back.

Thanks.

matt

**_Lord, today keep your arm on my shoulder and your hand over my mouth. _**

---

