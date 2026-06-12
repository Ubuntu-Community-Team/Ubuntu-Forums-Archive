---
title: "Can't install ndiswrapper;  can't install depency g++!"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by plush on 2006-11-13
I am trying to get all the depencies to build ndiswrapper.  Unfortunately, I'm down to two, g++-4.1_4.1.1-13ubuntu5_i386.deb, which says it depends on libstdc++6-4.1-dev, which also says it depends on g++-4.1.  Uhm.  That doesn't make any sense!  Help would be much appreciated (as would an ndiswrapper binary!)  Thanks!

---

### Post by jpkotta on 2006-11-13
I see ndiswrapper packages in the repos.  The ones I see (I'm on Dapper) are 

ndiswrapper-modules-1.1  
ndiswrapper-modules-1.8  
ndiswrapper-source       
ndiswrapper-utils

You probably want the newest modules and the utils.  Remember to look in the [wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") for ndiswrapper info and help.

As for your compiler issues, which very well might be a moot point now, I'll bet that g++-4.1_4.1.1-13ubuntu5_i386.deb provides the virtual package g++-4.1.  Will the package system not let you install libstdc++6 or g++?

---

### Post by FrodoB on 2006-11-15
This should fix it from the command line:

user@ubuntu:~$ sudo apt-get update  
user@ubuntu:~$ sudo apt-get install build-essential

---

### Post by plush on 2006-11-16
> **FrodoB said:**
> This should fix it from the command line:

user@ubuntu:~$ sudo apt-get update  
user@ubuntu:~$ sudo apt-get install build-essential


Well that would help if I could get a connection :)  I'm trying to manually install build-essentials, but I can't meet the dependencies (they seem to be mutually dependent).

---

### Post by plush on 2006-11-16
> **jpkotta said:**
> I see ndiswrapper packages in the repos.  The ones I see (I'm on Dapper) are 

ndiswrapper-modules-1.1  
ndiswrapper-modules-1.8  
ndiswrapper-source       
ndiswrapper-utils

You probably want the newest modules and the utils.  Remember to look in the [wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") for ndiswrapper info and help.

As for your compiler issues, which very well might be a moot point now, I'll bet that g++-4.1_4.1.1-13ubuntu5_i386.deb provides the virtual package g++-4.1.  Will the package system not let you install libstdc++6 or g++?

No my problem is in compiling.  You need the build-essentials, which need g++ and the other package I mentioned.  Thing is, when you try to install either of them they said they depend on the other one, and so it's impossible to install either ](*,)

---

### Post by FrodoB on 2006-11-16
The packages that you are looking for are on the Ubuntu CD:

user@ubuntu:/media/cdrom/pool/main/g/gcc-4.1$ ls

g++-4.1_4.1.1-13ubuntu5_i386.deb  libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb


If you insert your CD after a few seconds you will get a message pop-up that says:

A volume with software packages has been detected.

Would you like to open it with the package manager?

Say -- Start package manager

Wait a minute or so and you will be able to pick these things in Synaptic and install them.  Good luck.

---

### Post by plush on 2006-11-16
> **FrodoB said:**
> The packages that you are looking for are on the Ubuntu CD:

user@ubuntu:/media/cdrom/pool/main/g/gcc-4.1$ ls

g++-4.1_4.1.1-13ubuntu5_i386.deb  libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb


If you insert your CD after a few seconds you will get a message pop-up that says:

A volume with software packages has been detected.

Would you like to open it with the package manager?

Say -- Start package manager

Wait a minute or so and you will be able to pick these things in Synaptic and install them.  Good luck.


Thanks for the quick replies.  Turns out the ndiswrapper-utils or common package, not sure which, installed the binary, so no need for compiling anyway.

---

### Post by rdeb06 on 2006-11-16
May I please post a question here?  I can't figure out how to start a new thread, please forgive me.

I am using Kubuntu 6.10.  I can't get into the Kubuntu forums with either firefox or IE6.

I just upgraded to 6.10.  Now, I can't connect to my wireless network.  Also, there is an additional wireless device detected besides my wlan0, which is wmaster0.  I don't know how this came about.  I followed the upgrade instructions on Kbuntu.org (or at least I think I did).  I've run all of the tests and confirmed that the windows wireless driver is properly installed and loaded.  Could someone please advise?  Thank you.

---

### Post by FrodoB on 2006-11-16
You should publish some details. Give use the output of iwconfig,

---

### Post by plush on 2006-11-25
ndiswrapper-utils-1.8 needs ndiswrapper-common, FYI (for those who don't have internet access on their linux partition), but that's it.

---

