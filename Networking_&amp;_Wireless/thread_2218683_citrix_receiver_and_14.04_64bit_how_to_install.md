---
title: "citrix receiver and 14.04 64bit how to install?"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by dainis on 2014-04-21
I am on Ubuntu Gnome 14.04

I followed this guide to install citrix receiver 13 on 14.04 - did steps by 13 on 13.10 guide.
[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

Have mixed results - i can connect to some of my remote servers, but cannot to another ones. Cant find reason why - there are just those kind of errors:
THE CONNECTION TO BLABLA WAS LOST
CONNECTION TO XXX.XXX.XXX.XXX HAS BEEN LOST
  
Could someone point me in to direction how to troubleshoot citrix receiver problems? I have just read that Citrix cannot make real 64 client so they mess around with 32bit packages in 64bit OS - that all I can find :(

Worth mentioning that there are no any problems on same machine using Windows physically and/or in VirtualBox.

I had same problems on 13.10 and hoped that 14.04 will just solve those problems but wrong I am.

---

### Post by dainis on 2014-04-23
It seems that guide is correct. I did tests on virtual machines with manjaro CitrixICA and Ubuntu 14.04 different installation method - all had same problem. 
Ill keep digging where is the problem.

---

### Post by marcw on 2014-04-29
> **dainis said:**
> It seems that guide is correct. I did tests on virtual machines with manjaro CitrixICA and Ubuntu 14.04 different installation method - all had same problem. 
Ill keep digging where is the problem.

For my 64bit Citrix Receiver (v13) attempt on 14.04 I found and followed this quite lengthy and involved post to a tee and it worked terrifically:
[http://ubuntuforums.org/showthread.php?t=2181903](http://ubuntuforums.org/showthread.php?t=2181903)

It is a crying shame that Citrix can't assemble a decent 64bit deb package.  Fortunately, as usual, the Ubuntu community comes through.

---

### Post by jajodo on 2014-05-22
[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

The guide for installing on Ubuntu 13.10 does not work on Ubuntu 14.04

The above link has instructions for installing Citrix 12 on Ubuntu 14.04 that works well and is fairly easy.

---

### Post by troy-brophy on 2014-06-18
> **jajodo said:**
> [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

The guide for installing on Ubuntu 13.10 does not work on Ubuntu 14.04

The above link has instructions for installing Citrix 12 on Ubuntu 14.04 that works well and is fairly easy.


I just tried using that, but it's not finding all of the packages that the instructions tell you to get:


>sudo apt-get install libmotif4:i386 nspluginwrapper lib32z1 libc6-i386 libxp6:i386 libxpm4:i386
>Reading package lists... Done
>Building dependency tree
>Reading state information... Done
>**Package libc6-i386 is not available, but is referred to by another package.**
>This may bean that the package is missing, has been obsoleted, or
>is only available for another source
>However the following packages replace it:
>   libc6
>
>**E: Unable to locate package lib32z1**
>**E: Package 'libc6-i386' has no installation candidate**


Not sure how to proceed here.

---

### Post by Ulysses361 on 2014-10-15
Here is my alternative install procedure that can be added to a deployment bash script.

It was tested and works on Ubuntu 14.04 LTS using the latest version of Mozilla Firefox.

[http://mark911.wordpress.com/2014/06/27/how-to-install-citrix-receiver-icaclient-in-ubuntu-14-04-lts-64-bit-tested-and-working-using-mozilla-firefox/](http://mark911.wordpress.com/2014/06/27/how-to-install-citrix-receiver-icaclient-in-ubuntu-14-04-lts-64-bit-tested-and-working-using-mozilla-firefox/)

---

