---
title: "How to install Gstreamer Codecs offline(No internet Connection)"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by madhanaero on 2008-12-20
hi.
i am a first time user of linux(ubuntu 8.10 interpid)
i have been a windows user till 3 days before.so i really dont know any of the commands of linux even.after installing ubuntu i tried playing mp3 songs through totem player. it said gstreamer codecs missing.since i dont have an internet connection at home i cannot get it installed online.
i turned to help of ubuntu forums and they helped me in finding the download site of gstreamer 0.10.21. thanks a ton.
but the problem now is i dont know how to get it installed. please help me out with detailed instruction of installation
of gstreamer in ubuntu.(I DONT HAVE A INTERNET CONNECTION).
It would be of great help if the commands are also given in detailed.
the contents of the gstreamer i downloaded are as given below.

root@hyde-laptop:/home/hyde/Desktop/gstreamer-0.10.21# dir

ABOUT-NLS  
 autogen.sh 
 config.sub  
docs 
 gstreamer.doap 
 install-sh 
 Makefile.in 
 mkinstalldirs 
 RELEASE    
 tests aclocal.m4 
 ChangeLog
COPYING    
 gst
 gstreamer.spec
 libs	  
 missing
 po	
 stamp.h.in 
 win32

---

### Post by hailukah on 2008-12-20
Is there any way you can get temporary internet access to your computer?  Even by taking it to another location?  I ask because to build the source package you have you'll need to install other packages to have the proper dependencies in place.  If you can get internet access to your machine you can install a bunch of codecs and other extras that don't ship with Ubuntu by issuing the following command in a terminal.

sudo apt-get install ubuntu-restricted-extras

---

### Post by hailukah on 2008-12-20
You may want to look at [http://packages.ubuntu.com/intrepid/gstreamer0.10-ffmpeg]("http://packages.ubuntu.com/intrepid/gstreamer0.10-ffmpeg").  This is the package for mp3 playback.  You'll need to make sure you have all of the dependencies listed for this package to be able to install.  And remember that all of those packages listed as dependencies will have dependencies of their own.  But if you're willing to spend the time hunting down all of the packages you need you can then install them by issuing, in a terminal,

sudo dpkg -i <package name>

for each package.

To find out what packages you already have installed issue

dpkg --get-selections > packages.txt

This will create a file called packages.txt that will have a list of all the installed packages on your system.

---

### Post by madhanaero on 2008-12-20
i do have an internet connection at my home.i m operating on dual op sys. win xp and ubuntu. so i m trying to connect to internet through ubuntu. but still unsuccessful in installing java. same problem of not knowing how to install it offline(now i m using win xp for connecting to internet).can u help me in installing java(offline using commands in terminal) so that i m can connect to internet.

---

### Post by hailukah on 2008-12-21
What type of internet connection do you have?  It seems as though you just need to get your internet connection working in ubuntu and then you'll be all set up.  The ubuntu-restricted-extras package will install the java runtime environment.

---

### Post by madhanaero on 2008-12-21
i tried installing what have said.
sudo apt-get install ubuntu-restricted-extras
root@hyde-laptop:~# sudo apt-get install ubuntu-restricted-extras

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package ubuntu-restricted-extras

i got this message what should i do further..?

---

### Post by hailukah on 2008-12-21
Until you have your internet connection working you won't be able to use apt-get.  You'll need to get your connection up first and then run

sudo apt-get update

---

### Post by EXCiD3 on 2008-12-23
You can use Keryx to download the packages onto a USB flash drive from another computer and then you can install them using dpkg. Check it out here: [http://keryx.betaserver.org](http://keryx.betaserver.org)

---

### Post by Duck2006 on 2008-12-23
You can buy repositories dvd's or cd's to install off-line.

[http://on-disk.com/index.php/cPath/28_135_183](http://on-disk.com/index.php/cPath/28_135_183)
[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html)

---

