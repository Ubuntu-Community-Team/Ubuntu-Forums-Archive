---
title: "Using A Package manger to save .deb files"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by rideburton56 on 2009-11-05
Hi All,

Is there a way to get synaptic, dpkg, apt-get or anything else to download the original .debs to a location from the repositories?  I need to save a bunch of .debs (wicd + all dependecies for kubuntu) to a USB card and then bring them on to a computer that does not have an internet connection.  It seems like there must be an easier way than on the package list website.  Thanks!

---

### Post by oldos2er on 2009-11-05
sudo apt-get -d <package name>

---

### Post by uberg on 2009-11-05
I am glad you asked that.  I have an answer.  Use Synaptic.  Pick all those packages you want to download as if you are installing or upgrading and then from "File" hit "Generate package download script".  If you then run the script it will only download the packages for you.

---

### Post by alphaniner on 2009-11-05
**aptitude download *package***

Use this if you want to download to your current directory and have the file owned by you (as opposed to root).


In contrast, **[sudo] apt-get -d <package name>** will download them to /var/cache/apt/archives/ and the files will be owned by root.

---

### Post by bodhi.zazen on 2009-11-05
> **rideburton56 said:**
> Hi All,

Is there a way to get synaptic, dpkg, apt-get or anything else to download the original .debs to a location from the repositories?  I need to save a bunch of .debs (wicd + all dependecies for kubuntu) to a USB card and then bring them on to a computer that does not have an internet connection.  It seems like there must be an easier way than on the package list website.  Thanks!

There is also aptoncd

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by rideburton56 on 2009-11-05
Thanks!!  I guess I should have read the man page a little better :-s

---

### Post by mac9416 on 2009-11-07
> **rideburton56 said:**
> Hi All,

Is there a way to get synaptic, dpkg, apt-get or anything else to download the original .debs to a location from the repositories?  I need to save a bunch of .debs (wicd + all dependecies for kubuntu) to a USB card and then bring them on to a computer that does not have an internet connection.  It seems like there must be an easier way than on the package list website.  Thanks!

Another easy way to do this is using [Keryx]("http://keryxproject.org"). With Keryx, you create a "snapshot" of the offline computer, take this on a flash drive to an online computer, download your .debs, then take them back to your offline computer to install. If you like, you can use APTOnCD to create a CD archive of these .debs and install them.

---

