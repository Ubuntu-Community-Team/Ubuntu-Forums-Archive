---
title: "Setting Automatic Proxy Script for Synaptic, Automatix Etc"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by MozUK on 2006-11-27
I'm at university, my university uses a auto proxy config address in this format:

[http://wwwcache.lancs.ac.uk](http://wwwcache.lancs.ac.uk)

But I can only configure this in firefox to work and I have added it to network proxy in preferences.

I have also added:
```

export http_proxy="http://wwwcache.lancs.ac.uk:3128/"
export ftp_proxy="http://wwwcache.lancs.ac.uk:3128/"

```
and
```

export http_proxy="http://wwwcache.lancs.ac.uk:8080/"
export ftp_proxy="http://wwwcache.lancs.ac.uk:8080/"

```
to the files

**~/.bashrc** and **/etc/bash.bashrc** after reading about my problem, both of these attempts to no avail.

When I connect to synaptic I cannot reload the universe updates and when I connect to Automatix I cannot download all the appropriate keys to continue.  I am guessing this is because of my proxy problem, I cannot set an automatic script in all my programs that don't work, Gaim does connect either.

Can anyone help ?

---

### Post by MozUK on 2006-11-27
okay okay I've made progress updating a couple of scripts but now I'm getting errors like these when trying to install packages from automatix2:(:

```

WARNING: The following packages cannot be authenticated!
  libgtk2-trayicon-perl libcrypt-ssleay-perl libxml-namespacesupport-perl
  libxml-sax-perl libxml-libxml-common-perl libxml-libxml-perl libxml-simple-perl
  libcrypt-blowfish-perl libfreezethaw-perl libcompress-zlib-perl checkgmail
E: There are problems and -y was used without --force-yes

!!SCRIPT OUTPUT END!!
[11/28/2006 - 03:03.44] - ERRORS OR WARNINGS WHERE REPORTED
[11/28/2006 - 03:03.44] - FATAL - Checkgmail - An apt-based error occured and installation was unsuccessful

```


```

Err http://gb.archive.ubuntu.com edgy/universe alsa-oss 1.0.11-1
  Could not connect to gb.archive.ubuntu.com:80 (195.248.90.38), connection timed out
Err http://archive.ubuntu.com edgy/universe alsa-oss 1.0.11-1                         
  Could not connect to archive.ubuntu.com:80 (195.248.90.38), connection timed out
Err http://archive.ubuntu.com edgy/multiverse libmp4v2-0 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3
  Could not connect to archive.ubuntu.com:80 (195.248.90.38), connection timed out

```

Can anyone please help! I've had so many problems trying to get ubuntu working but i'm just getting over the last of them hopefully! :cool:

---

### Post by MozUK on 2006-11-28
Anyone ? I'm getting disillusioned here! lol

---

### Post by arnieboy on 2006-11-28
[http://getautomatix.com/wiki/index.php?title=Proxy_configuration](http://getautomatix.com/wiki/index.php?title=Proxy_configuration)

---

### Post by MozUK on 2006-11-28
already tried this but I tried again:

```

ACQUIRE {
http::proxy "http://wwwcache.lancs.ac.uk:8080/"
}

```

when I tried to do the update section I spotted some errors:

```

Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025) edgy Release.gpg
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025) edgy/restricted Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025) edgy Release     
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025) edgy/main Packages
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025) edgy/restricted Packages
Err cdrom://Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025) edgy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025) edgy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 http://archive.ubuntu.com edgy-backports Release.gpg [191B]              
Get:2 http://gb.archive.ubuntu.com edgy Release.gpg [191B]                     
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US            
Get:3 http://www.getautomatix.com edgy Release.gpg [189B]                      
Ign http://gb.archive.ubuntu.com edgy/main Translation-en_US                   
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US      
Ign http://gb.archive.ubuntu.com edgy/restricted Translation-en_US             
Get:4 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Ign http://www.getautomatix.com edgy/main Translation-en_US                    
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US        
Ign http://gb.archive.ubuntu.com edgy/multiverse Translation-en_US             
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US      
Ign http://gb.archive.ubuntu.com edgy/universe Translation-en_US               
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Get:5 http://gb.archive.ubuntu.com edgy-updates Release.gpg [189B]             
Get:6 http://www.getautomatix.com edgy Release [4147B]                         
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Ign http://gb.archive.ubuntu.com edgy-updates/main Translation-en_US           
Get:7 http://archive.ubuntu.com edgy-updates Release.gpg [189B]                
Ign http://gb.archive.ubuntu.com edgy-updates/restricted Translation-en_US     
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US              
Ign http://gb.archive.ubuntu.com edgy-updates/multiverse Translation-en_US     
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US        
Ign http://gb.archive.ubuntu.com edgy-updates/universe Translation-en_US       
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US          
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US      
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US        
Get:8 http://archive.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Ign http://archive.ubuntu.com edgy-security/main Translation-en_US             
Get:9 http://gb.archive.ubuntu.com edgy Release [34.7kB]                       
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en_US       
Hit http://security.ubuntu.com edgy-security Release                           
Ign http://archive.ubuntu.com edgy-security/universe Translation-en_US         
Get:10 http://gb.archive.ubuntu.com edgy-updates Release [19.6kB]              
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en_US       
Get:11 http://archive.ubuntu.com edgy Release.gpg [191B]                       
Ign http://archive.ubuntu.com edgy/main Translation-en_US                   
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US             
Ign http://archive.ubuntu.com edgy/universe Translation-en_US               
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US                
Hit http://archive.ubuntu.com edgy-backports Release                           
Get:12 http://www.getautomatix.com edgy/main Packages [437B]                   
Get:13 http://gb.archive.ubuntu.com edgy/main Packages [938kB]                 
Hit http://security.ubuntu.com edgy-security/main Packages                     
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Hit http://archive.ubuntu.com edgy-updates Release                             
Get:14 http://archive.ubuntu.com edgy-security Release [27.3kB]                
Get:15 http://security.ubuntu.com edgy-security/multiverse Packages [2234B]    
Hit http://security.ubuntu.com edgy-security/universe Packages                 
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://archive.ubuntu.com edgy Release                                     
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Get:16 http://security.ubuntu.com edgy-security/multiverse Sources [14B]       
Hit http://archive.ubuntu.com edgy-backports/main Packages                     
Hit http://security.ubuntu.com edgy-security/universe Sources                  
Hit http://archive.ubuntu.com edgy-backports/restricted Packages               
Hit http://archive.ubuntu.com edgy-backports/universe Packages                 
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages               
Hit http://archive.ubuntu.com edgy-updates/main Packages                       
Hit http://archive.ubuntu.com edgy-updates/restricted Packages                 
Get:17 http://archive.ubuntu.com edgy-updates/universe Packages [14B]          
Get:18 http://archive.ubuntu.com edgy-updates/multiverse Packages [14B]        
Get:19 http://archive.ubuntu.com edgy-security/main Packages [21.0kB]          
Get:20 http://archive.ubuntu.com edgy-security/restricted Packages [3266B]     
Get:21 http://archive.ubuntu.com edgy-security/universe Packages [6760B]       
Get:22 http://archive.ubuntu.com edgy-security/multiverse Packages [2234B]     
Hit http://archive.ubuntu.com edgy/main Packages                               
Hit http://archive.ubuntu.com edgy/restricted Packages  
Hit http://archive.ubuntu.com edgy/universe Packages                           
Hit http://archive.ubuntu.com edgy/multiverse Packages                         
Get:23 http://gb.archive.ubuntu.com edgy/restricted Packages [5594B]        
Get:24 http://gb.archive.ubuntu.com edgy/multiverse Packages [116kB]           
Get:25 http://gb.archive.ubuntu.com edgy/universe Packages [3497kB]            
Get:26 http://gb.archive.ubuntu.com edgy/main Sources [274kB]                  
Get:27 http://gb.archive.ubuntu.com edgy/restricted Sources [1436B]            
Get:28 http://gb.archive.ubuntu.com edgy/multiverse Sources [45.0kB]           
Get:29 http://gb.archive.ubuntu.com edgy/universe Sources [1068kB]             
Get:30 http://gb.archive.ubuntu.com edgy-updates/main Packages [14B]           
Get:31 http://gb.archive.ubuntu.com edgy-updates/restricted Packages [14B]     
Get:32 http://gb.archive.ubuntu.com edgy-updates/multiverse Packages [14B]     
Get:33 http://gb.archive.ubuntu.com edgy-updates/universe Packages [14B]       
Get:34 http://gb.archive.ubuntu.com edgy-updates/main Sources [14B]            
Get:35 http://gb.archive.ubuntu.com edgy-updates/restricted Sources [14B]      
Get:36 http://gb.archive.ubuntu.com edgy-updates/multiverse Sources [14B]      
Get:37 http://gb.archive.ubuntu.com edgy-updates/universe Sources [14B]        
Fetched 6069kB in 17s (351kB/s)                                                
Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025)]/dists/edgy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025)]/dists/edgy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Then I updated the other file

```

# You can set the default proxies for Wget to use for http and ftp.
# They will override the value in the environment.
http_proxy = http://wwwcache.lancs.ac.uk:8080/
ftp_proxy = http://wwwcache.lancs.ac.uk:8080/

# If you do not want to use proxy at all, set this to off.
use_proxy = on

```

And it stills not connecting when I go to update something in automatix, stays stuck at 0% when trying to connect to download packages.

---

### Post by arnieboy on 2006-11-28
remove the local cdrom repos from your /etc/apt/sources.list and do a 
```
sudo apt-get update
```
If you do not know how to do it, ask.
and paste the following:
```
cat ~/.automatix/activity.log
```

---

### Post by MozUK on 2006-11-28
To remove the CD stuff I commented out the top line hope this was the right way to do it, heres my sources.list file anyway...

```

# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025)]/ edgy main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe


#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt edgy main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
#AUTOMATIX REPOS END

```

I think its removed the earlier parts of my activity log heres all it had anyway...

```

Recommended packages:
  libcrypt-simple-perl
The following NEW packages will be installed:
  checkgmail libcompress-zlib-perl libcrypt-blowfish-perl libcrypt-ssleay-perl
  libfreezethaw-perl libgtk2-trayicon-perl libxml-libxml-common-perl
  libxml-libxml-perl libxml-namespacesupport-perl libxml-sax-perl libxml-simple-perl
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 660kB of archives.
After unpacking 2703kB of additional disk space will be used.

!!SCRIPT OUTPUT END!!
[11/28/2006 - 15:35.56] - !!SCRIPT OUTPUT START!!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libartsc0 libdvdread3 libfaac0 libggi2 libgii1 libgii1-target-x liblame0 libmp4v2-0
  libmpcdec3 libungif4g libxvidcore4 libxvmc1 mplayer-skins
Suggested packages:
  libggi-target-emu libggi-target-monotext libggimisc2 w32codecs libdvdcss
  mplayer-doc
Recommended packages:
  libggi-target-x libggi-target
The following NEW packages will be installed:
  libartsc0 libdvdread3 libfaac0 libggi2 libgii1 libgii1-target-x liblame0 libmp4v2-0
  libmpcdec3 libpostproc0 libungif4g libxvidcore4 libxvmc1 mencoder mozilla-mplayer
  mplayer mplayer-fonts mplayer-skins
0 upgraded, 18 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.2MB of archives.
After unpacking 31.5MB of additional disk space will be used.
Reading package lists... Doneubuntu.com (195.248.90.38)]
Building dependency tree       
Reading state information... Done
Package mplayer-amd64 is not installed, so not removed
Package mplayer-fonts is not installed, so not removed
Package mozilla-mplayer is not installed, so not removed
E: Couldn't find package mencoder-amd64
received 
mv: cannot stat `/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a_backup': No such file or directory
mv: cannot stat `/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.la_backup': No such file or directory
mv: cannot stat `/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so_backup': No such file or directory
mv: cannot stat `/usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt_backup': No such file or directory
Finished
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcompress-zlib-perl libcrypt-blowfish-perl libcrypt-ssleay-perl
  libfreezethaw-perl libgtk2-trayicon-perl libxml-libxml-common-perl
  libxml-libxml-perl libxml-namespacesupport-perl libxml-sax-perl libxml-simple-perl
Recommended packages:
  libcrypt-simple-perl
The following NEW packages will be installed:
  checkgmail libcompress-zlib-perl libcrypt-blowfish-perl libcrypt-ssleay-perl
  libfreezethaw-perl libgtk2-trayicon-perl libxml-libxml-common-perl
  libxml-libxml-perl libxml-namespacesupport-perl libxml-sax-perl libxml-simple-perl
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 660kB of archives.
After unpacking 2703kB of additional disk space will be used.
0% [Connecting to gb.archive.ubuntu.com (195.248.90.35)]Finished
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package checkgmail is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Finished
Package `beep-media-player-wma' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Finished
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcompress-zlib-perl libcrypt-blowfish-perl libcrypt-ssleay-perl
  libfreezethaw-perl libgtk2-trayicon-perl libxml-libxml-common-perl
  libxml-libxml-perl libxml-namespacesupport-perl libxml-sax-perl libxml-simple-perl
Recommended packages:
  libcrypt-simple-perl
The following NEW packages will be installed:
  checkgmail libcompress-zlib-perl libcrypt-blowfish-perl libcrypt-ssleay-perl
  libfreezethaw-perl libgtk2-trayicon-perl libxml-libxml-common-perl
  libxml-libxml-perl libxml-namespacesupport-perl libxml-sax-perl libxml-simple-perl
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 660kB of archives.
After unpacking 2703kB of additional disk space will be used.
Reading package lists... Doneubuntu.com (195.248.90.38)]
Building dependency tree       
Reading state information... Done
Package checkgmail is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Finished

!!SCRIPT OUTPUT END!!
[11/28/2006 - 15:38.12] - !!Starting Automatix 1.1-1.11!!
[11/28/2006 - 15:38.16] - Updated keys with ED8A569E
[11/28/2006 - 15:38.16] - Updated keys with 3B2EA15A
[11/28/2006 - 15:38.16] - Updated keys with DD4D5088
[11/28/2006 - 15:38.16] - Updated keys with 2F30665
[11/28/2006 - 15:38.16] - Updated keys with 2F306651
[11/28/2006 - 15:39.47] - Updated APT
[11/28/2006 - 15:41.53] - !!SCRIPT OUTPUT START!!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcompress-zlib-perl libcrypt-blowfish-perl libcrypt-ssleay-perl
  libfreezethaw-perl libgtk2-trayicon-perl libxml-libxml-common-perl
  libxml-libxml-perl libxml-namespacesupport-perl libxml-sax-perl libxml-simple-perl
Recommended packages:
  libcrypt-simple-perl
The following NEW packages will be installed:
  checkgmail libcompress-zlib-perl libcrypt-blowfish-perl libcrypt-ssleay-perl
  libfreezethaw-perl libgtk2-trayicon-perl libxml-libxml-common-perl
  libxml-libxml-perl libxml-namespacesupport-perl libxml-sax-perl libxml-simple-perl
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 660kB of archives.
After unpacking 2703kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libgtk2-trayicon-perl libcrypt-ssleay-perl libxml-namespacesupport-perl
  libxml-sax-perl libxml-libxml-common-perl libxml-libxml-perl libxml-simple-perl
  libcrypt-blowfish-perl libfreezethaw-perl libcompress-zlib-perl checkgmail
E: There are problems and -y was used without --force-yes

!!SCRIPT OUTPUT END!!
[11/28/2006 - 15:41.53] - ERRORS OR WARNINGS WHERE REPORTED
[11/28/2006 - 15:41.53] - FATAL - Checkgmail - An apt-based error occured and installation was unsuccessful
[11/28/2006 - 15:51.46] - !!Starting Automatix 1.1-1.11!!
[11/28/2006 - 15:51.50] - Updated keys with ED8A569E
[11/28/2006 - 15:51.50] - Updated keys with 3B2EA15A
[11/28/2006 - 15:51.51] - Updated keys with DD4D5088
[11/28/2006 - 15:51.51] - Updated keys with 2F30665
[11/28/2006 - 15:51.51] - Updated keys with 2F306651
[11/28/2006 - 15:52.10] - !!SCRIPT OUTPUT START!!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package tcl8.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  docker imlib-base imlib11 libmad0 libungif4g libvorbisfile3 sox tcl8.4 tcltls tk8.4
Suggested packages:
  mozilla galeon konqueror imagemagick imlib-progs tclreadline
The following NEW packages will be installed:
  amsn docker imlib-base imlib11 libmad0 libungif4g libvorbisfile3 sox tcl8.4 tcltls
  tk8.4
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 5174kB of archives.
After unpacking 16.1MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  imlib-base libungif4g imlib11 tcl8.4 libmad0 libvorbisfile3 sox tk8.4 docker tcltls
  amsn
E: There are problems and -y was used without --force-yes

!!SCRIPT OUTPUT END!!
[11/28/2006 - 15:52.10] - ERRORS OR WARNINGS WHERE REPORTED
[11/28/2006 - 15:52.10] - FATAL - AMSN 0.95 - An apt-based error occured and installation was unsuccessful
[11/28/2006 - 15:52.29] - !!Starting Automatix 1.1-1.11!!
[11/28/2006 - 15:52.33] - Updated keys with ED8A569E
[11/28/2006 - 15:52.33] - Updated keys with 3B2EA15A
[11/28/2006 - 15:52.34] - Updated keys with DD4D5088
[11/28/2006 - 15:52.34] - Updated keys with 2F30665
[11/28/2006 - 15:52.34] - Updated keys with 2F306651
[11/28/2006 - 15:52.57] - !!SCRIPT OUTPUT START!!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package tcl8.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  docker imlib-base imlib11 libmad0 libungif4g libvorbisfile3 sox tcl8.4 tcltls tk8.4
Suggested packages:
  mozilla galeon konqueror imagemagick imlib-progs tclreadline
The following NEW packages will be installed:
  amsn docker imlib-base imlib11 libmad0 libungif4g libvorbisfile3 sox tcl8.4 tcltls
  tk8.4
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 5174kB of archives.
After unpacking 16.1MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  imlib-base libungif4g imlib11 tcl8.4 libmad0 libvorbisfile3 sox tk8.4 docker tcltls
  amsn
E: There are problems and -y was used without --force-yes

!!SCRIPT OUTPUT END!!
[11/28/2006 - 15:52.57] - ERRORS OR WARNINGS WHERE REPORTED
[11/28/2006 - 15:52.57] - FATAL - AMSN 0.95 - An apt-based error occured and installation was unsuccessful
[11/28/2006 - 19:13.26] - !!Starting Automatix 1.1-1.11!!
[11/28/2006 - 19:13.29] - Updated keys with ED8A569E
[11/28/2006 - 19:13.29] - Updated keys with 3B2EA15A
[11/28/2006 - 19:13.30] - Updated keys with DD4D5088
[11/28/2006 - 19:13.30] - Updated keys with 2F30665
[11/28/2006 - 19:13.30] - Updated keys with 2F306651
[11/28/2006 - 19:15.08] - !!SCRIPT OUTPUT START!!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libatk1.0-0 is already the newest version.
libc6 is already the newest version.
libglib2.0-0 is already the newest version.
libpango1.0-0 is already the newest version.
libx11-6 is already the newest version.
libxext6 is already the newest version.
The following packages were automatically installed and are no longer required:
  totem-gstreamer
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc-3.3-base liba52-0.7.4 libartsc0 libatk1.0-dev libavcodec0d libavformat0d
  libc6-dev libcairo2-dev libdc1394-13 libdvbpsi4 libdvdnav4 libdvdread3
  libexpat1-dev libfaad2-0 libfontconfig1-dev libfreetype6-dev libglib2.0-dev libgsm1
  libgtk2.0-dev libice-dev libid3-3.8.3c2a libid3tag0 libiso9660-4 libmad0
  libmodplug0c2 libmpcdec3 libmpeg2-4 libpango1.0-dev libpng12-dev libpostproc0d
  libsdl-image1.2 libsm-dev libtar libvcdinfo0 libvlc0 libvorbisfile3 libwxbase2.6-0
  libwxgtk2.6-0 libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxine1 libxinerama-dev libxosd2 libxrandr-dev
  libxrender-dev libxvmc1 linux-libc-dev vlc-nox x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
Suggested packages:
  glibc-doc manpages-dev libcairo2-doc libglib2.0-doc libgtk2.0-doc libpango1.0-doc
  xfonts-base-transcoded mozilla-plugin-vlc
Recommended packages:
  libxine-extracodecs videolan-doc
The following packages will be REMOVED:
  totem-gstreamer
The following NEW packages will be installed:
  beep-media-player beep-media-player-dev bmp-mp4 gcc-3.3-base liba52-0.7.4 libartsc0
  libatk1.0-dev libavcodec0d libavformat0d libc6-dev libcairo2-dev libdc1394-13
  libdvbpsi4 libdvdnav4 libdvdread3 libexpat1-dev libfaad2-0 libfontconfig1-dev
  libfreetype6-dev libglib2.0-dev libgsm1 libgtk2.0-dev libice-dev libid3-3.8.3c2a
  libid3tag0 libiso9660-4 libmad0 libmodplug0c2 libmpcdec3 libmpeg2-4 libpango1.0-dev
  libpng12-dev libpostproc0d libsdl-image1.2 libsm-dev libstdc++5 libtar libvcdinfo0
  libvlc0 libvorbisfile3 libwxbase2.6-0 libwxgtk2.6-0 libx11-dev libxau-dev
  libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxine1
  libxinerama-dev libxosd2 libxrandr-dev libxrender-dev libxvmc1 linux-libc-dev
  totem-xine vlc vlc-nox vlc-plugin-arts vlc-plugin-esd wxvlc x11proto-core-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 73 newly installed, 1 to remove and 0 not upgraded.
Need to get 30.1MB of archives.
After unpacking 98.2MB of additional disk space will be used.

!!SCRIPT OUTPUT END!!
[11/28/2006 - 19:15.15] - !!SCRIPT OUTPUT START!!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libatk1.0-0 is already the newest version.
libc6 is already the newest version.
libglib2.0-0 is already the newest version.
libpango1.0-0 is already the newest version.
libx11-6 is already the newest version.
libxext6 is already the newest version.
The following packages were automatically installed and are no longer required:
  totem-gstreamer
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc-3.3-base liba52-0.7.4 libartsc0 libatk1.0-dev libavcodec0d libavformat0d
  libc6-dev libcairo2-dev libdc1394-13 libdvbpsi4 libdvdnav4 libdvdread3
  libexpat1-dev libfaad2-0 libfontconfig1-dev libfreetype6-dev libglib2.0-dev libgsm1
  libgtk2.0-dev libice-dev libid3-3.8.3c2a libid3tag0 libiso9660-4 libmad0
  libmodplug0c2 libmpcdec3 libmpeg2-4 libpango1.0-dev libpng12-dev libpostproc0d
  libsdl-image1.2 libsm-dev libtar libvcdinfo0 libvlc0 libvorbisfile3 libwxbase2.6-0
  libwxgtk2.6-0 libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxine1 libxinerama-dev libxosd2 libxrandr-dev
  libxrender-dev libxvmc1 linux-libc-dev vlc-nox x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
Suggested packages:
  glibc-doc manpages-dev libcairo2-doc libglib2.0-doc libgtk2.0-doc libpango1.0-doc
  xfonts-base-transcoded mozilla-plugin-vlc
Recommended packages:
  libxine-extracodecs videolan-doc
The following packages will be REMOVED:
  totem-gstreamer
The following NEW packages will be installed:
  beep-media-player beep-media-player-dev bmp-mp4 gcc-3.3-base liba52-0.7.4 libartsc0
  libatk1.0-dev libavcodec0d libavformat0d libc6-dev libcairo2-dev libdc1394-13
  libdvbpsi4 libdvdnav4 libdvdread3 libexpat1-dev libfaad2-0 libfontconfig1-dev
  libfreetype6-dev libglib2.0-dev libgsm1 libgtk2.0-dev libice-dev libid3-3.8.3c2a
  libid3tag0 libiso9660-4 libmad0 libmodplug0c2 libmpcdec3 libmpeg2-4 libpango1.0-dev
  libpng12-dev libpostproc0d libsdl-image1.2 libsm-dev libstdc++5 libtar libvcdinfo0
  libvlc0 libvorbisfile3 libwxbase2.6-0 libwxgtk2.6-0 libx11-dev libxau-dev
  libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxine1
  libxinerama-dev libxosd2 libxrandr-dev libxrender-dev libxvmc1 linux-libc-dev
  totem-xine vlc vlc-nox vlc-plugin-arts vlc-plugin-esd wxvlc x11proto-core-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 73 newly installed, 1 to remove and 0 not upgraded.
Need to get 30.1MB of archives.
After unpacking 98.2MB of additional disk space will be used.
Reading package lists... Doneubuntu.com (195.248.90.38)] [Connecting to security.ubunt
Building dependency tree       
Reading state information... Done
Package totem-xine is not installed, so not removed
Package vlc is not installed, so not removed
Package vlc-plugin-arts is not installed, so not removed
Package wxvlc is not installed, so not removed
Package beep-media-player is not installed, so not removed
Package vlc-plugin-esd is not installed, so not removed
Package bmp-mp4 is not installed, so not removed
Package beep-media-player-dev is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Finished

!!SCRIPT OUTPUT END!!
[11/28/2006 - 19:32.20] - !!Starting Automatix 1.1-1.11!!
[11/28/2006 - 19:32.23] - Updated keys with ED8A569E
[11/28/2006 - 19:32.23] - Updated keys with 3B2EA15A
[11/28/2006 - 19:32.23] - Updated keys with DD4D5088
[11/28/2006 - 19:32.24] - Updated keys with 2F30665
[11/28/2006 - 19:32.24] - Updated keys with 2F306651
[11/28/2006 - 19:32.46] - !!SCRIPT OUTPUT START!!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libatk1.0-0 is already the newest version.
libc6 is already the newest version.
libglib2.0-0 is already the newest version.
libpango1.0-0 is already the newest version.
libx11-6 is already the newest version.
libxext6 is already the newest version.
The following packages were automatically installed and are no longer required:
  totem-gstreamer
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc-3.3-base liba52-0.7.4 libartsc0 libatk1.0-dev libavcodec0d libavformat0d
  libc6-dev libcairo2-dev libdc1394-13 libdvbpsi4 libdvdnav4 libdvdread3
  libexpat1-dev libfaad2-0 libfontconfig1-dev libfreetype6-dev libglib2.0-dev libgsm1
  libgtk2.0-dev libice-dev libid3-3.8.3c2a libid3tag0 libiso9660-4 libmad0
  libmodplug0c2 libmpcdec3 libmpeg2-4 libpango1.0-dev libpng12-dev libpostproc0d
  libsdl-image1.2 libsm-dev libtar libvcdinfo0 libvlc0 libvorbisfile3 libwxbase2.6-0
  libwxgtk2.6-0 libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxine1 libxinerama-dev libxosd2 libxrandr-dev
  libxrender-dev libxvmc1 linux-libc-dev vlc-nox x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
Suggested packages:
  glibc-doc manpages-dev libcairo2-doc libglib2.0-doc libgtk2.0-doc libpango1.0-doc
  xfonts-base-transcoded mozilla-plugin-vlc
Recommended packages:
  libxine-extracodecs videolan-doc
The following packages will be REMOVED:
  totem-gstreamer
The following NEW packages will be installed:
  beep-media-player beep-media-player-dev bmp-mp4 gcc-3.3-base liba52-0.7.4 libartsc0
  libatk1.0-dev libavcodec0d libavformat0d libc6-dev libcairo2-dev libdc1394-13
  libdvbpsi4 libdvdnav4 libdvdread3 libexpat1-dev libfaad2-0 libfontconfig1-dev
  libfreetype6-dev libglib2.0-dev libgsm1 libgtk2.0-dev libice-dev libid3-3.8.3c2a
  libid3tag0 libiso9660-4 libmad0 libmodplug0c2 libmpcdec3 libmpeg2-4 libpango1.0-dev
  libpng12-dev libpostproc0d libsdl-image1.2 libsm-dev libstdc++5 libtar libvcdinfo0
  libvlc0 libvorbisfile3 libwxbase2.6-0 libwxgtk2.6-0 libx11-dev libxau-dev
  libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxine1
  libxinerama-dev libxosd2 libxrandr-dev libxrender-dev libxvmc1 linux-libc-dev
  totem-xine vlc vlc-nox vlc-plugin-arts vlc-plugin-esd wxvlc x11proto-core-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 73 newly installed, 1 to remove and 0 not upgraded.
Need to get 30.1MB of archives.
After unpacking 98.2MB of additional disk space will be used.

!!SCRIPT OUTPUT END!!
[11/28/2006 - 19:32.52] - !!SCRIPT OUTPUT START!!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libatk1.0-0 is already the newest version.
libc6 is already the newest version.
libglib2.0-0 is already the newest version.
libpango1.0-0 is already the newest version.
libx11-6 is already the newest version.
libxext6 is already the newest version.
The following packages were automatically installed and are no longer required:
  totem-gstreamer
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc-3.3-base liba52-0.7.4 libartsc0 libatk1.0-dev libavcodec0d libavformat0d
  libc6-dev libcairo2-dev libdc1394-13 libdvbpsi4 libdvdnav4 libdvdread3
  libexpat1-dev libfaad2-0 libfontconfig1-dev libfreetype6-dev libglib2.0-dev libgsm1
  libgtk2.0-dev libice-dev libid3-3.8.3c2a libid3tag0 libiso9660-4 libmad0
  libmodplug0c2 libmpcdec3 libmpeg2-4 libpango1.0-dev libpng12-dev libpostproc0d
  libsdl-image1.2 libsm-dev libtar libvcdinfo0 libvlc0 libvorbisfile3 libwxbase2.6-0
  libwxgtk2.6-0 libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxine1 libxinerama-dev libxosd2 libxrandr-dev
  libxrender-dev libxvmc1 linux-libc-dev vlc-nox x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
Suggested packages:
  glibc-doc manpages-dev libcairo2-doc libglib2.0-doc libgtk2.0-doc libpango1.0-doc
  xfonts-base-transcoded mozilla-plugin-vlc
Recommended packages:
  libxine-extracodecs videolan-doc
The following packages will be REMOVED:
  totem-gstreamer
The following NEW packages will be installed:
  beep-media-player beep-media-player-dev bmp-mp4 gcc-3.3-base liba52-0.7.4 libartsc0
  libatk1.0-dev libavcodec0d libavformat0d libc6-dev libcairo2-dev libdc1394-13
  libdvbpsi4 libdvdnav4 libdvdread3 libexpat1-dev libfaad2-0 libfontconfig1-dev
  libfreetype6-dev libglib2.0-dev libgsm1 libgtk2.0-dev libice-dev libid3-3.8.3c2a
  libid3tag0 libiso9660-4 libmad0 libmodplug0c2 libmpcdec3 libmpeg2-4 libpango1.0-dev
  libpng12-dev libpostproc0d libsdl-image1.2 libsm-dev libstdc++5 libtar libvcdinfo0
  libvlc0 libvorbisfile3 libwxbase2.6-0 libwxgtk2.6-0 libx11-dev libxau-dev
  libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxine1
  libxinerama-dev libxosd2 libxrandr-dev libxrender-dev libxvmc1 linux-libc-dev
  totem-xine vlc vlc-nox vlc-plugin-arts vlc-plugin-esd wxvlc x11proto-core-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 73 newly installed, 1 to remove and 0 not upgraded.
Need to get 30.1MB of archives.
After unpacking 98.2MB of additional disk space will be used.
Reading package lists... Doneubuntu.com (195.248.90.35)] [Connecting to security.ubunt
Building dependency tree       
Reading state information... Done
Package totem-xine is not installed, so not removed
Package vlc is not installed, so not removed
Package vlc-plugin-arts is not installed, so not removed
Package wxvlc is not installed, so not removed
Package beep-media-player is not installed, so not removed
Package vlc-plugin-esd is not installed, so not removed
Package bmp-mp4 is not installed, so not removed
Package beep-media-player-dev is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Finished

!!SCRIPT OUTPUT END!!

```

---

### Post by arnieboy on 2006-11-28
apt seems to be working fine but lets double check. We need to also figure out if wget (used for direct downloads) is working or not. When you have both apt and wget correctly configured, AX2 will work flawlessly.
Try the following and paste the results here:
```
sudo apt-get install conky
wget http://easynews.dl.sourceforge.net/sourceforge/checkgmail/checkgmail-1.10.1.tar.bz2
```

---

### Post by MozUK on 2006-11-28
looks like that went ok to me:

```

moz@moz-desktop:~$ sudo apt-get install conky
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  conky
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 131kB of archives.
After unpacking 393kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com edgy/universe conky 1.4.2-1 [131kB]
Fetched 131kB in 0s (445kB/s)
Selecting previously deselected package conky.
(Reading database ... 87149 files and directories currently installed.)
Unpacking conky (from .../conky_1.4.2-1_amd64.deb) ...
Setting up conky (1.4.2-1) ...

moz@moz-desktop:~$ wget http://easynews.dl.sourceforge.net/sourceforge/checkgmail/checkgmail-1.10.1.tar.bz2
--21:22:34--  http://easynews.dl.sourceforge.net/sourceforge/checkgmail/checkgmail-1.10.1.tar.bz2
           => `checkgmail-1.10.1.tar.bz2'
Resolving wwwcache.lancs.ac.uk... 148.88.0.8, 148.88.0.9, 148.88.0.10, ...
Connecting to wwwcache.lancs.ac.uk|148.88.0.8|:8080... connected.
Proxy request sent, awaiting response... 200 OK
Length: 47,637 (47K) [application/x-bzip2]

100%[====================================>] 47,637        68.49K/s             

21:22:36 (68.33 KB/s) - `checkgmail-1.10.1.tar.bz2' saved [47637/47637]


```

---

### Post by arnieboy on 2006-11-28
yes AX2 should work fine now.

---

### Post by MozUK on 2006-11-28
it doesn't its still just sitting there at 0% and timing out eventually.](*,)  :-?

This is what it looks like after it has timed out once (takes about 5minutes):

[[IMG]http://img72.imageshack.us/img72/1708/screenshotgc9.th.jpg[/IMG]](http://img72.imageshack.us/my.php?image=screenshotgc9.jpg)

---

### Post by arnieboy on 2006-11-28
have you by any chance installed anon-proxy?

---

### Post by MozUK on 2006-11-28
not as far as I know.  Would you like me to post any config files to help? Im depeserate to sort this problem out.

---

### Post by arnieboy on 2006-11-28
try deleting the following lines :
> export http_proxy="http://wwwcache.lancs.ac.uk:3128/"
export ftp_proxy="http://wwwcache.lancs.ac.uk:3128/"
from ~/.bashrc and /etc/bashrc
and restarting your computer.

---

### Post by MozUK on 2006-11-28
OK done that, no difference to my problem I'm afraid.

---

### Post by arnieboy on 2006-11-28
> **MozUK said:**
> OK done that, no difference to my problem I'm afraid.

I am out of ideas on this one (sorry about that).... I will discuss this with the other AX devs and see what they have to say.

---

### Post by MozUK on 2006-12-01
any updates?

---

### Post by penguin007 on 2007-01-28
See this: [Link]("http://www.ubuntuforums.org/showthread.php?t=331497") 

If you are on a Windows LAN, chances are that the proxy requires a userid / password.

---

### Post by MozUK on 2007-02-17
doesnt work :( maybe its just my university blocking it, i've tried everything you have given me I've enquired to my univeristy.

---

