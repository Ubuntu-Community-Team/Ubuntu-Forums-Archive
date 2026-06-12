---
title: "Net gear wireless install for ubuntu 16.04"
date: 2016-12-13
forum: Networking &amp; Wireless
---

### Post by mmellisa20 on 2016-12-13
Ok so my son just received a computer from his grandpa and it is set up with ubuntu 16.04, he also got him a netgear wireless USB adapter but we are having trouble installing it. I am new to ubuntu and have tried a few things that I have found online and I can't seem to figure it out.... on a side note our internet router in on the first level and his computer is on the second level so hard wiring it is not really an option without moving the whole computer on trying to wire it through the wall which we want to avoid.... help please!

---

### Post by bijan2 on 2016-12-13
What is the model # of wireless USB adapter? Netgear adapters are usually not supported on Linux system.

Thank you,

---

### Post by chili555 on 2016-12-13
The first step is to identify the device so that we can determine the suitable driver. Please insert the device and open a terminal Ctrl+Alt+t and run:```
lsusb
```Post the result and we'll proceed.

We pray that the device doesn't contain "3100" in its name!

---

### Post by mmellisa20 on 2016-12-13
[IMG][[IMG]http://i34.photobucket.com/albums/d108/mmellisa201/IMG_0018_zpsnlntrniw.jpg[/IMG]]("http://s34.photobucket.com/user/mmellisa201/media/IMG_0018_zpsnlntrniw.jpg.html")[/IMG]

---

### Post by chili555 on 2016-12-13
Let's get our inner geek on! With a temporary working internet connection, open a terminal and do:```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/Grawp/rtl8812au_rtl8821au.git 
cd  rtl8812au_rtl8821au
make
sudo make install
sudo modprobe 8812au
```You may get a few warnings but no errors. Post back and tell us how it goes; I will have one additional step.

---

### Post by mmellisa20 on 2016-12-13
Ok so when I get to the install hit part it tells me....

Reading package list ...Done
Building dependency tree
Reading state information...Done
package git is not available, but is referred to by another package.
this means that the package is missing, has been obsoletes, or 
is only available from another source

E: Package 'git' has no installation candidate

---

### Post by chili555 on 2016-12-13
Did you do the update step first? And you are actually running 16.04? ```
lsb_release -d
```I am sure git is available.

---

### Post by mmellisa20 on 2016-12-13
Yes I did the update step first and when I do the lsb_release -d it says it's Ubuntu 16.04.1 LTS

---

### Post by chili555 on 2016-12-14
Here it is: [http://packages.ubuntu.com/xenial/git](http://packages.ubuntu.com/xenial/git)

It has several dependencies so it will be tricky to download manually. Will you please be certain that you are connected to the internet and try again:```
sudo apt-get update && sudo apt-get -y upgrade
sudo apt-get install git
```If it fails again, we'll try the manual methods.

---

