---
title: "VLC Installation"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by ravi kumar on 2009-08-24
hi
i have recently installed ubuntu8.04 but the default media players doesnot support many media files like .mp3,.avi,.vob.etc
so i wanted to install vlc media player. Since i dont have internet conection i downloaded vlc in a cyber cafe.
now i am finding it difficult to install vlc since both add program and synaptic methods rely on internet connection.
i have tried with command like sudo-apt but then again it is showing that it cannot read the package ...
plzzzzzzz somebody help me through this i have already wasted a lot of my time searching web for some solution.
thanx a lot in advance.....

---

### Post by jbrown96 on 2009-08-24
If you download the application you need to use dpkg. I doubt it will work. VLC has quite a few dependencies, which you will also have to install. 

Here's the dpkg command you need
```
sudo dpkg -i INSTALL_FILE
```

---

### Post by itisbasi on 2009-08-24
there are a couple of ways to do this but both requires you to have access to another machine running ubuntu with an internet connection.
If you can get a friend's machine with ubuntu, who also has an internet connection you could get the entire vlc dependency package using "aptoncd"...that's the easy way out....else follow this guide....

INSTALLATION on System without Internet Connection

Find a machine with ubuntu installed and with INTERNET connection.Then use following command.

%sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc –download-only

All files downloaded after above command are found at /var/cache/apt/archives/
Copy these files into a single folder and install them using command’
%dpkg -i *.deb (pwd must be that folder where you copied the files)

---

### Post by XCan on 2009-08-24
Can't he simply double-click on the .deb files?

---

### Post by jbrown96 on 2009-08-24
> **XCan said:**
> Can't he simply double-click on the .deb files?

The problem is that Vlc has around 20 or more dependencies, so he would have to do that for each one and in the right order. I was having trouble with Vlc a few weeks and had to reinstall it on computer w/o internet access. It's a huge pain. I was also using a development version of kde 4.3 (rc3) and it caused all kinds of library conflicts.

---

### Post by itisbasi on 2009-08-25
[http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/](http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/)

This is another good guide...

---

### Post by ravi kumar on 2009-08-25
thanks a lot .......
i have downloaded vlc 1.0.1 tar.bz2 which on unzipping creates a folder named vlc 1.0.1
can u guide me what to do next....
sorry for the inconvenience  iam very new to ubuntu does not know much about it

---

### Post by KyleRickards on 2009-08-26
[http://webupd8.blogspot.com/2009/07/install-vlc-100-final-in-ubuntu-arch.html](http://webupd8.blogspot.com/2009/07/install-vlc-100-final-in-ubuntu-arch.html)

is how I did it - and I am completely new as well so must be easy to follow!!

Kyle

---

### Post by zkriesse on 2009-08-26
This is the easiest way. [Playing DVD's in Ubuntu Jaunty Help Guide]("https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html")

---

