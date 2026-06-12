---
title: "install multimedia codecs offline"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by dinesh_ddt on 2009-02-01
How to install mp3 and other audio and video codecs offline in ubuntu 8.10 ? 
i dont have internet connection :( can u help me out?? :o

---

### Post by mgmiller on 2009-02-01
Hi, you will need a machine somewhere that has internet access to download the package files.  They will be saved as .deb's so once you have them, just copy them to the offline machine and double click to install.  You can find a list of all the intrepid packages here:
[http://packages.ubuntu.com/intrepid/allpackages](http://packages.ubuntu.com/intrepid/allpackages)

scroll down to ubuntu-restricted-extras and download the architecture you need, either i386 or amd64.  You will see a list of about 15 packages that are recomended for all the restricted codecs.  You will need to download each one as a seperate .deb

For other restricted things, go to:
[http://packages.medibuntu.org/intrepid/index.html](http://packages.medibuntu.org/intrepid/index.html)

and download w32 codecs and anything else that looks interesting.

You may want to verify that all the dependencies for these downloads are met.  If they don't work after installing them, go back and make sure you have all the files listed as dependancies.

It's kind of a "pita"  when you don't have an internet connection.

That should do it, good luck.

---

### Post by EXCiD3 on 2009-02-02
Check out using Keryx, its like synaptic but you can use it from any computer (such as a work machine, etc) so that you can easily get the packages you need. Its intended for just this type of problem.

---

### Post by zwygart on 2009-02-02
Seems that other people have offlines machines while the world works online.
Personnaly I worked with the site nonetdebs until it disappear, then I heard about keryx wich not really meet my needs. Now I am discovering the best off the way's. But this needs some knowledge off linux. 
The method I will discibe here works for me and allows to use synaptic offline with all it's features.

Are you using x86, or amd64?
If you use amd64 or other, replace all i-386 with amd64
First, on a drive run this script in a empty directory
```
mkdir intrepid-security/
mkdir intrepid-security/main/
mkdir intrepid-security/main/binary-i386/
mkdir intrepid-security/main/debian-installer/
mkdir intrepid-security/main/debian-installer/binary-i386
mkdir intrepid-security/main/source/
mkdir intrepid-security/multiverse/
mkdir intrepid-security/multiverse/binary-i386/
mkdir intrepid-security/multiverse/debian-installer/
mkdir intrepid-security/multiverse/debian-installer/binary-i386
mkdir intrepid-security/multiverse/source/
mkdir intrepid-security/restricted/
mkdir intrepid-security/restricted/binary-i386/
mkdir intrepid-security/restricted/debian-installer/
mkdir intrepid-security/restricted/debian-installer/binary-i386
mkdir intrepid-security/restricted/source/
mkdir intrepid-security/universe/
mkdir intrepid-security/universe/binary-i386/
mkdir intrepid-security/universe/debian-installer/
mkdir intrepid-security/universe/debian-installer/binary-i386
mkdir intrepid-security/universe/source/
wget -c -O intrepid-security/main/binary-i386/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Release
wget -c -O intrepid-security/main/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.bz2
wget -c -O intrepid-security/main/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz
wget -c -O intrepid-security/main/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages
wget -c -O intrepid-security/main/debian-installer/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/debian-installer/binary-i386/Packages.bz2
wget -c -O intrepid-security/main/debian-installer/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/debian-installer/binary-i386/Packages
wget -c -O intrepid-security/main/debian-installer/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/debian-installer/binary-i386/Packages.gz
wget -c -O intrepid-security/main/source/Sources.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.bz2
wget -c -O intrepid-security/main/source/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Release
wget -c -O intrepid-security/main/source/Sources http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources
wget -c -O intrepid-security/main/source/Sources.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz
wget -c -O intrepid-security/multiverse/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages
wget -c -O intrepid-security/multiverse/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz
wget -c -O intrepid-security/multiverse/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.bz2
wget -c -O intrepid-security/multiverse/binary-i386/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Release
wget -c -O intrepid-security/multiverse/source/Sources.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.bz2
wget -c -O intrepid-security/multiverse/source/Sources http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources
wget -c -O intrepid-security/multiverse/source/Sources.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz
wget -c -O intrepid-security/multiverse/source/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Release
wget -c -O intrepid-security/restricted/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz
wget -c -O intrepid-security/restricted/binary-i386/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Release
wget -c -O intrepid-security/restricted/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages
wget -c -O intrepid-security/restricted/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.bz2
wget -c -O intrepid-security/restricted/debian-installer/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/debian-installer/binary-i386/Packages.bz2
wget -c -O intrepid-security/restricted/debian-installer/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/debian-installer/binary-i386/Packages
wget -c -O intrepid-security/restricted/debian-installer/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/debian-installer/binary-i386/Packages.gz
wget -c -O intrepid-security/restricted/source/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Release
wget -c -O intrepid-security/restricted/source/Sources http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources
wget -c -O intrepid-security/restricted/source/Sources.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz
wget -c -O intrepid-security/restricted/source/Sources.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.bz2
wget -c -O intrepid-security/universe/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages
wget -c -O intrepid-security/universe/binary-i386/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Release
wget -c -O intrepid-security/universe/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz
wget -c -O intrepid-security/universe/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.bz2
wget -c -O intrepid-security/universe/debian-installer/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/debian-installer/binary-i386/Packages.gz
wget -c -O intrepid-security/universe/debian-installer/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/debian-installer/binary-i386/Packages
wget -c -O intrepid-security/universe/debian-installer/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/debian-installer/binary-i386/Packages.bz2
wget -c -O intrepid-security/universe/source/Sources.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.bz2
wget -c -O intrepid-security/universe/source/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Release
wget -c -O intrepid-security/universe/source/Sources http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources
wget -c -O intrepid-security/universe/source/Sources.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz
mkdir intrepid/
mkdir intrepid/main/
mkdir intrepid/main/binary-i386/
mkdir intrepid/main/debian-installer/
mkdir intrepid/main/debian-installer/binary-i386
mkdir intrepid/main/source/
mkdir intrepid/multiverse/
mkdir intrepid/multiverse/binary-i386/
mkdir intrepid/multiverse/debian-installer/
mkdir intrepid/multiverse/debian-installer/binary-i386
mkdir intrepid/multiverse/source/
mkdir intrepid/restricted/
mkdir intrepid/restricted/binary-i386/
mkdir intrepid/restricted/debian-installer/
mkdir intrepid/restricted/debian-installer/binary-i386
mkdir intrepid/restricted/source/
mkdir intrepid/universe/
mkdir intrepid/universe/binary-i386/
mkdir intrepid/universe/debian-installer/
mkdir intrepid/universe/debian-installer/binary-i386
mkdir intrepid/universe/source/
wget -c -O intrepid/main/binary-i386/Release http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Release
wget -c -O intrepid/main/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.bz2
wget -c -O intrepid/main/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz
wget -c -O intrepid/main/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages
wget -c -O intrepid/main/debian-installer/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid/main/debian-installer/binary-i386/Packages.bz2
wget -c -O intrepid/main/debian-installer/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid/main/debian-installer/binary-i386/Packages
wget -c -O intrepid/main/debian-installer/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid/main/debian-installer/binary-i386/Packages.gz
wget -c -O intrepid/main/source/Sources.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.bz2
wget -c -O intrepid/main/source/Release http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Release
wget -c -O intrepid/main/source/Sources http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources
wget -c -O intrepid/main/source/Sources.gz http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz
wget -c -O intrepid/multiverse/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages
wget -c -O intrepid/multiverse/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz
wget -c -O intrepid/multiverse/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.bz2
wget -c -O intrepid/multiverse/binary-i386/Release http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Release
wget -c -O intrepid/multiverse/source/Sources.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.bz2
wget -c -O intrepid/multiverse/source/Sources http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources
wget -c -O intrepid/multiverse/source/Sources.gz http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz
wget -c -O intrepid/multiverse/source/Release http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Release
wget -c -O intrepid/restricted/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz
wget -c -O intrepid/restricted/binary-i386/Release http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Release
wget -c -O intrepid/restricted/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages
wget -c -O intrepid/restricted/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.bz2
wget -c -O intrepid/restricted/debian-installer/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/debian-installer/binary-i386/Packages.bz2
wget -c -O intrepid/restricted/debian-installer/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/debian-installer/binary-i386/Packages
wget -c -O intrepid/restricted/debian-installer/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/debian-installer/binary-i386/Packages.gz
wget -c -O intrepid/restricted/source/Release http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Release
wget -c -O intrepid/restricted/source/Sources http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources
wget -c -O intrepid/restricted/source/Sources.gz http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz
wget -c -O intrepid/restricted/source/Sources.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.bz2
wget -c -O intrepid/universe/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages
wget -c -O intrepid/universe/binary-i386/Release http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Release
wget -c -O intrepid/universe/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz
wget -c -O intrepid/universe/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2
wget -c -O intrepid/universe/debian-installer/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/debian-installer/binary-i386/Packages.gz
wget -c -O intrepid/universe/debian-installer/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/debian-installer/binary-i386/Packages
wget -c -O intrepid/universe/debian-installer/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/debian-installer/binary-i386/Packages.bz2
wget -c -O intrepid/universe/source/Sources.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.bz2
wget -c -O intrepid/universe/source/Release http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Release
wget -c -O intrepid/universe/source/Sources http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources
wget -c -O intrepid/universe/source/Sources.gz http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz
mkdir intrepid-updates/
mkdir intrepid-updates/main/
mkdir intrepid-updates/main/binary-i386/
mkdir intrepid-updates/main/debian-installer/
mkdir intrepid-updates/main/debian-installer/binary-i386
mkdir intrepid-updates/main/source/
mkdir intrepid-updates/multiverse/
mkdir intrepid-updates/multiverse/binary-i386/
mkdir intrepid-updates/multiverse/debian-installer/
mkdir intrepid-updates/multiverse/debian-installer/binary-i386
mkdir intrepid-updates/multiverse/source/
mkdir intrepid-updates/restricted/
mkdir intrepid-updates/restricted/binary-i386/
mkdir intrepid-updates/restricted/debian-installer/
mkdir intrepid-updates/restricted/debian-installer/binary-i386
mkdir intrepid-updates/restricted/source/
mkdir intrepid-updates/universe/
mkdir intrepid-updates/universe/binary-i386/
mkdir intrepid-updates/universe/debian-installer/
mkdir intrepid-updates/universe/debian-installer/binary-i386
mkdir intrepid-updates/universe/source/
wget -c -O intrepid-updates/main/binary-i386/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Release
wget -c -O intrepid-updates/main/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.bz2
wget -c -O intrepid-updates/main/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz
wget -c -O intrepid-updates/main/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages
wget -c -O intrepid-updates/main/debian-installer/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/debian-installer/binary-i386/Packages.bz2
wget -c -O intrepid-updates/main/debian-installer/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/debian-installer/binary-i386/Packages
wget -c -O intrepid-updates/main/debian-installer/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/debian-installer/binary-i386/Packages.gz
wget -c -O intrepid-updates/main/source/Sources.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.bz2
wget -c -O intrepid-updates/main/source/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Release
wget -c -O intrepid-updates/main/source/Sources http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources
wget -c -O intrepid-updates/main/source/Sources.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz
wget -c -O intrepid-updates/multiverse/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages
wget -c -O intrepid-updates/multiverse/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz
wget -c -O intrepid-updates/multiverse/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.bz2
wget -c -O intrepid-updates/multiverse/binary-i386/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Release
wget -c -O intrepid-updates/multiverse/source/Sources.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.bz2
wget -c -O intrepid-updates/multiverse/source/Sources http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources
wget -c -O intrepid-updates/multiverse/source/Sources.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz
wget -c -O intrepid-updates/multiverse/source/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Release
wget -c -O intrepid-updates/restricted/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz
wget -c -O intrepid-updates/restricted/binary-i386/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Release
wget -c -O intrepid-updates/restricted/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages
wget -c -O intrepid-updates/restricted/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.bz2
wget -c -O intrepid-updates/restricted/debian-installer/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/debian-installer/binary-i386/Packages.bz2
wget -c -O intrepid-updates/restricted/debian-installer/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/debian-installer/binary-i386/Packages
wget -c -O intrepid-updates/restricted/debian-installer/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/debian-installer/binary-i386/Packages.gz
wget -c -O intrepid-updates/restricted/source/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Release
wget -c -O intrepid-updates/restricted/source/Sources http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources
wget -c -O intrepid-updates/restricted/source/Sources.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz
wget -c -O intrepid-updates/restricted/source/Sources.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.bz2
wget -c -O intrepid-updates/universe/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages
wget -c -O intrepid-updates/universe/binary-i386/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Release
wget -c -O intrepid-updates/universe/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz
wget -c -O intrepid-updates/universe/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.bz2
wget -c -O intrepid-updates/universe/debian-installer/binary-i386/Packages.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/debian-installer/binary-i386/Packages.gz
wget -c -O intrepid-updates/universe/debian-installer/binary-i386/Packages http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/debian-installer/binary-i386/Packages
wget -c -O intrepid-updates/universe/debian-installer/binary-i386/Packages.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/debian-installer/binary-i386/Packages.bz2
wget -c -O intrepid-updates/universe/source/Sources.bz2 http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.bz2
wget -c -O intrepid-updates/universe/source/Release http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Release
wget -c -O intrepid-updates/universe/source/Sources http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources
wget -c -O intrepid-updates/universe/source/Sources.gz http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz
```

Then go to your offline machine and edit the source.lst
```
sudo gedit /etc/apt/sources.list
```
Comment out all the lines and add these ones at the end
```
deb file:/media/Data/ubuntu/ intrepid main restricted universe multiverse
deb-src file:/media/Data/ubuntu/ intrepid main restricted universe multiverse

deb file:/media/Data/ubuntu/ intrepid-updates main restricted universe multiverse
deb-src file:/media/Data/ubuntu/ intrepid-updates main restricted universe multiverse

deb file:/media/Data/ubuntu/ intrepid-security main restricted universe multiverse
deb-src file:/media/Data/ubuntu/ intrepid-security main restricted universe multiverse
```
Remove the name off the ones you don't want and replace Data/ubuntu with the path to your drive.

Then go in synaptic and press the reload button. Chose all what you want and instead off installing chose file>generate download script. Save this script on your drive and execute it on a machine with internet. This will download all the files mentioned by mgmiller including the dependencies. 
Back to your off line you need to install all them. 
A shortcut is to run dpkg -i * in the directory with the debs. But it's not harmless so be carefull.

If any problem please post. I am improving this method now since it is not perfect.

---

