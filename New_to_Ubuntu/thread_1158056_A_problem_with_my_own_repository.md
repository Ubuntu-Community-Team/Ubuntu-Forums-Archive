---
title: "A problem with my own repository"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-05-13
I created my own repository, and added the ubuntu-restricted-extras to the package.gz and all that stuff, then changed my sources.list so it only has my deb file  repository folder.

root@eric:/home/mydebs# apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse icedtea-gcjwebplugin libdvdread3
  liblame0 msttcorefonts unrar
The following NEW packages will be installed:
  ubuntu-restricted-extras
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3662B of archives.
After this operation, 32.8kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  ubuntu-restricted-extras
Install these packages without verification [y/N]? y
Err file: mydebs/ ubuntu-restricted-extras 15
  File not found
Failed to fetch file:///home/./ubuntu-restricted-extras_15_i386.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@eric:/home/mydebs# autorepo
 ** Packages in archive but missing from override file: **
  mplayer ubuntu-restricted-extras

 Wrote 2 entries to output Packages file.
root@eric:/home/mydebs# apt-get update
Ign file: mydebs/ Release.gpg
Ign file: mydebs/ Translation-en_US                      
Ign file: mydebs/ Release                                
Ign file: mydebs/ Packages                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Reading package lists... Done
root@eric:/home/mydebs# apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse icedtea-gcjwebplugin libdvdread3 liblame0 msttcorefonts
  unrar
The following NEW packages will be installed:
  ubuntu-restricted-extras
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3662B of archives.
After this operation, 32.8kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  ubuntu-restricted-extras
Install these packages without verification [y/N]? y
Err file: mydebs/ ubuntu-restricted-extras 15
  File not found
Failed to fetch file:///home/./ubuntu-restricted-extras_15_i386.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?





I tried to do the apt-get update, it didnt work, I cant figure out how to do --fix-missing.

Any suggestions? It will be much appreciated.

---

### Post by ericeclifford on 2009-05-13
same thing with 3d chess I downloaded it and added it to mydebs(my repository) the /dev/null stuff and scanpackages from the ubuntu documentation and got this.


root@eric://# cd home/mydebs
root@eric://home/mydebs# autorepo
 ** Packages in archive but missing from override file: **
  3dchess mplayer ubuntu-restricted-extras

 Wrote 3 entries to output Packages file.
root@eric://home/mydebs# apt-get update
Ign file: mydebs/ Release.gpg
Ign file: mydebs/ Translation-en_US       
Ign file: mydebs/ Release                 
Ign file: mydebs/ Packages                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Reading package lists... Done
root@eric://home/mydebs# apt-get install 3dchess
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  3dchess: Depends: xaw3dg (>= 1.5+E-1) but it is not installable
E: Broken packages
root@eric://home/mydebs#

---

### Post by ericeclifford on 2009-05-13
I try to install the missing package of the 3dchess game, and this is what I got.



root@eric://home/mydebs# autorepo
 ** Packages in archive but missing from override file: **
  3dchess mplayer ubuntu-restricted-extras xaw3dg

 Wrote 4 entries to output Packages file.
root@eric://home/mydebs# apt-get update
Ign file: mydebs/ Release.gpg
Ign file: mydebs/ Translation-en_US                      
Ign file: mydebs/ Release                                
Ign file: mydebs/ Packages                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Reading package lists... Done
root@eric://home/mydebs# apt-get install 3dchess
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  xaw3dg
The following NEW packages will be installed:
  3dchess xaw3dg
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/190kB of archives.
After this operation, 631kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  xaw3dg 3dchess
Install these packages without verification [y/N]? y
Err file: mydebs/ xaw3dg 1.5+E-15
  File not found
Err file: mydebs/ 3dchess 0.8.1-13
  File not found
Failed to fetch file:///home/./xaw3dg_1.5+E-15_i386.deb  File not found
Failed to fetch file:///home/./3dchess_0.8.1-13_i386.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@eric://home/mydebs#

---

