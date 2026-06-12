---
title: "How to modify my Sound Recorder?"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Innernet on 2010-02-06
Hello.

My Sound Recorder shows as image 1 with no MP3 choice to select,

And I want to add/have this MP3 recording capability as in image 2 


How is it done ?

---

### Post by warfacegod on 2010-02-06
You'll need to get the gstreamer good, bad, and ugly packages from Synaptic. Make sure "restricted extras" is enabled in Software Sources.

---

### Post by warfacegod on 2010-02-06
Now that I think about it, installing ubuntu restricted extras will pull in the gstreamer stuff and allot more that you might need.

---

### Post by Innernet on 2010-02-06
Thanks.
I did enter on the console :

sudo apt-get update && sudo apt-get install ubuntu-restricted-extras

as if I knew what I was doing and a bunch of "Failed to fetch" and 404 -not found  messages showed up: 	](*,)

=================================================
externet@externet-desktop:~$ sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
externet@externet-desktop:~$

---

### Post by warfacegod on 2010-02-06
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


These are the key lines. Do you have Update Manager, Synaptic, Add/Remove, or Ubuntu S.C. open?

---

### Post by warfacegod on 2010-02-06
It looks like you are using Gutsy 7.10, any way I can talk you into using a newer Ubuntu? Perhaps 9.04?

---

### Post by Innernet on 2010-02-06
Thanks.
Yes, Synaptic was open.

Closed everything and this time tried only :

sudo apt-get install ubuntu-restricted-extras

and got the following:
====================================================================

externet@externet-desktop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for externet:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract flashplugin-nonfree gcc-3.3-base gstreamer0.10-ffmpeg
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly-multiverse java-common libcdaudio1 libfaac0
  libfaad2-0 libfreebob0 libjack0 liblame0 libmjpegtools0c2a libmms0
  libmp4v2-0 libopenspc0 libquicktime1 libsoundtouch1c2 libstdc++5 libx264-54
  libxvidcore4 msttcorefonts odbcinst1debian1 sun-java6-bin sun-java6-jre
  sun-java6-plugin unixodbc unrar
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs equivs binfmt-support
  sun-java6-fonts libmyodbc odbc-postgresql libct1
Recommended packages:
  jackd gsfonts-x11
The following NEW packages will be installed:
  cabextract flashplugin-nonfree gcc-3.3-base gstreamer0.10-ffmpeg
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly-multiverse java-common libcdaudio1 libfaac0
  libfaad2-0 libfreebob0 libjack0 liblame0 libmjpegtools0c2a libmms0
  libmp4v2-0 libopenspc0 libquicktime1 libsoundtouch1c2 libstdc++5 libx264-54
  libxvidcore4 msttcorefonts odbcinst1debian1 sun-java6-bin sun-java6-jre
  sun-java6-plugin ubuntu-restricted-extras unixodbc unrar
0 upgraded, 31 newly installed, 0 to remove and 186 not upgraded.
Need to get 39.6MB of archives.
After unpacking 112MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  java-common odbcinst1debian1 unixodbc gcc-3.3-base libstdc++5 sun-java6-bin
  sun-java6-jre cabextract flashplugin-nonfree gstreamer0.10-ffmpeg
  libcdaudio1 libfreebob0 libjack0 libmms0 libopenspc0 libsoundtouch1c2
  gstreamer0.10-plugins-bad libmp4v2-0 libfaac0 libfaad2-0 libquicktime1
  libmjpegtools0c2a libx264-54 libxvidcore4
  gstreamer0.10-plugins-bad-multiverse liblame0
  gstreamer0.10-plugins-ugly-multiverse msttcorefonts sun-java6-plugin
  ubuntu-restricted-extras unrar
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main java-common 0.26ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main odbcinst1debian1 2.2.11-16
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main unixodbc 2.2.11-16
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main gcc-3.3-base 1:3.3.6-15ubuntu2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libstdc++5 1:3.3.6-15ubuntu2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse sun-java6-bin 6-03-0ubuntu2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse sun-java6-jre 6-03-0ubuntu2
  404 Not Found [IP: 91.189.88.46 80]
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe cabextract 1.2-2 [53.9kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse flashplugin-nonfree 9.0.48.0.2+really0ubuntu12
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe gstreamer0.10-ffmpeg 0.10.2-2ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe libcdaudio1 0.99.12p2-3 [44.9kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe libfreebob0 1.0.3+svn443-2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe libjack0 0.103.0-6ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe libmms0 0.3-5ubuntu2
  404 Not Found [IP: 91.189.88.46 80]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe libopenspc0 0.3.99a-2 [27.0kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe libsoundtouch1c2 1.3.0-2.1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe gstreamer0.10-plugins-bad 0.10.5-4ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse libmp4v2-0 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5
  404 Not Found [IP: 91.189.88.46 80]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse libfaac0 1.24clean-0ubuntu4 [55.2kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse libfaad2-0 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe libquicktime1 2:1.0.0+debian-4ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse libmjpegtools0c2a 1:1.8.0-0.2ubuntu5 [219kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse libx264-54 1:0.svn20070309-4ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse libxvidcore4 2:1.1.2-0.1ubuntu2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse gstreamer0.10-plugins-bad-multiverse 0.10.5-1
  404 Not Found [IP: 91.189.88.46 80]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse liblame0 3.97-0.0 [185kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse gstreamer0.10-plugins-ugly-multiverse 0.10.6-0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse msttcorefonts 2.2            
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse sun-java6-plugin 6-03-0ubuntu2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse ubuntu-restricted-extras 10  
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse unrar 1:3.7.3-1.1            
  404 Not Found [IP: 91.189.88.46 80]
Fetched 585kB in 8s (71.6kB/s)                                                 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.26ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.26ubuntu1_all.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst1debian1_2.2.11-16_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst1debian1_2.2.11-16_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/unixodbc_2.2.11-16_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/unixodbc_2.2.11-16_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/gcc-3.3-base_3.3.6-15ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/gcc-3.3-base_3.3.6-15ubuntu2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-03-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-03-0ubuntu2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-03-0ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-03-0ubuntu2_all.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.2-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.2-2ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/libf/libfreebob/libfreebob0_1.0.3+svn443-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/libf/libfreebob/libfreebob0_1.0.3+svn443-2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/j/jack-audio-connection-kit/libjack0_0.103.0-6ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/j/jack-audio-connection-kit/libjack0_0.103.0-6ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/libm/libmms/libmms0_0.3-5ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/libm/libmms/libmms0_0.3-5ubuntu2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/s/soundtouch/libsoundtouch1c2_1.3.0-2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/soundtouch/libsoundtouch1c2_1.3.0-2.1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.5-4ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.5-4ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libfaad2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libfaad2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime1_1.0.0+debian-4ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime1_1.0.0+debian-4ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/x/x264/libx264-54_0.svn20070309-4ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/x/x264/libx264-54_0.svn20070309-4ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.2-0.1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.2-0.1ubuntu2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-bad-multiverse0.10/gstreamer0.10-plugins-bad-multiverse_0.10.5-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-bad-multiverse0.10/gstreamer0.10-plugins-bad-multiverse_0.10.5-1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.6-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.6-0ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/m/msttcorefonts/msttcorefonts_2.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/m/msttcorefonts/msttcorefonts_2.2_all.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-03-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-03-0ubuntu2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_10_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.3-1.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.3-1.1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
externet@externet-desktop:~$ 

=============================================

I DO want to get into a newer version, but my compfuser choked trying 9.04,
and I went back to 7.10 that works great! for my needs..    My not fast connection would take too long to download a 9.10 live disc to re-try.

---

### Post by warfacegod on 2010-02-06
I think the reason it's failing to fetch those is because Gutsy isn't supported anymore. I don't think it is anyway. You'll have to update your sources at the very least. If you have a slow connection, perhaps downloading while you are asleep is an alternative.

---

### Post by Innernet on 2010-02-07
After doing the above detailed installation -or aborted install-,  [www.sky.fm](www.sky.fm) does not work.  Nothing sounds. ](*,)

How to reverse or diagnose ?

---

### Post by warfacegod on 2010-02-07
> After doing the above detailed installation -or aborted install-

I need more details on "aborted". What exactly did you do?


Do you have any sound at all?

---

### Post by Innernet on 2010-02-07
Hi.
I call it 'aborted' as with so many "Failed to fetch" and "404 not found" , most of the components did not load/install.  Cannot rcognize if any of the list actually got installed.  I only did what shows in the earlier posts.

---

### Post by warfacegod on 2010-02-07
I don't suppose it's set to mute?

---

### Post by Innernet on 2010-02-07
No.
The 'wait' or 'loading' wormy icon goes round and round forever.  Audio from youtube does work fine.

---

### Post by warfacegod on 2010-02-07
This doesn't sound like a sound issue. *Say "sound like a sound" ten times fast!* Look in the troubleshooting section:

[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by Innernet on 2010-02-08
Well,... went to  System > Preferences > Sound > Devices > Sound capture > ALSA and all others > Test
And garbage pulsing clicks is all that shows up on all choices in that option.  The other options all work. The screen froze, [COLOR="Magenta"]cannot remove[/COLOR] the "Failed to construct test pipeline..." window.

Went to the console, typed <top> and this shows up (snapshot)
Does anyone see any weirdness?

I DO think it is a sound issue.

---

### Post by audiomick on 2010-02-09
Hallo.
I can't help you much, I am afraid. I seem to have a different sound set up to you; my sound preferences window looks nothing like yours.
What I do notice is that your computer seems to be working very hard. Nearly all of your RAM is in use, and, if I have read your "top" output correctly, there is something using 97.7% of your CPU.
I went to that SKY-FM site, and my system way using 540MB RAM when listening, with only  Firefox running.

edit: I went back to sky-fm for a second look, and could not play the stream. Same behaviour that you described.
You tube works.

---

