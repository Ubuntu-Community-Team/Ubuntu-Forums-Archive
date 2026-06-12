---
title: "unbuntu 9.04"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by mylnx on 2009-09-05
This newbie needs some serious A-b-C steps help.
I am enclosing the examples of files that I have extracted to my desktop along with the error messages that I got.

                                 "AdbeRdr9.1.2-1_i486linux_enu.bin%20(2)" cannot be opened
 No application suitable for automatic installation is available for handling this kind of file.
 

 "npjp2_linux_jasper_pthread.so" cannot be opened
 No application is known for this kind of file.
 

 "RealPlayer11GOLD.bin%20(2)" cannot be opened
 No application suitable for automatic installation is available for handling this kind of file.


Your input is greatly appreciated.

---

### Post by overdrank on 2009-09-05
Hi and welcome, moved to Absolute Beginner Talk

---

### Post by falconindy on 2009-09-05
bin files aren't generally executable. They need to be read by something else. Where did you get them from and what are you trying to accomplish? Similarly, .so files are compiled object files and aren't generally executable on their own.

Context, man, context. The more detail you provide, the easier it is for people to help you. And welcome to the forums.

---

### Post by Paqman on 2009-09-05
> **mylnx said:**
> 
Your input is greatly appreciated.

Top tip that will make your life easier: on Linux, you don't get your software by manually downloading and installing it by hand. You open your package manager (System > Admin > Synaptic OR Applications > Add/Remove) and just pick what you want. It's all done automatically for you.

*Adobe Reader*: You don't actually need this. Your system can open .pdfs already.

*npjp2_linux_glibc2.1_jasper_pthread*:
From a quick Google:
> Description: This is a static version of the plugin linked with jasper and have pthread support. **Simply put the file npjp2_linux_jasper_pthread.so in your browser plugin directory and enjoy it !**


You'll find Firefox's plugin directory inside /home/username/.mozilla/

*RealPlayer11GOLD.bin*: Realplayer is available, but you have to enable the [Medibuntu]("http://www.medibuntu.org/") repository. Medibuntu is full of all sorts of good stuff. To enable it, open a terminal window (Applications . Accesories > Terminal, and paste this horrible block of gobbledegook into it:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

After which you'll be able t get Realplayer from Synaptic.

---

### Post by Bölvaður on 2009-09-05
> **mylnx said:**
> 
 No application suitable for automatic installation is available for handling this kind of file.
 

if this is an executable file but doesnt have that kind of flag on it you'll have to put it up by:

right click on the file
select properties
click permissions
allow execute as a file

---

### Post by 3rdalbum on 2009-09-06
Forget about Realplayer, you don't need it. Just install the "non-free-codecs" package from the Medibuntu repository and all your media players will be able to play Realplayer files. Your ordinary media players will also be able to play old Realplayer files from 10 years ago, which is something that the official Realplayer can't actually do!

The first thing I do when I install Ubuntu is enable the Medibuntu repository. It has DVD playback support, all the non-free codecs, Google Earth, Skype, Realplayer (if you wanted it) and Acrobat Reader.

If you do want to run binary installers, you need to make them executable first, then run them as root in a terminal, to satisfy the Linux security system.

---

