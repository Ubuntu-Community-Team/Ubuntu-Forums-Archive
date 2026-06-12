---
title: "Wireless Drivers Install Time?"
date: 2014-04-06
forum: Networking &amp; Wireless
---

### Post by Altair011001 on 2014-04-06
Hey all, I'm posting this after getting my ubuntu compatable drivers and when I restarted like it said my wireless still wouldnt work. I went into additional drivers and  found it was not activated. I clicked activate and it brought me to a donwloading and installing driver screen. I've been here the past 2 hours with no progress, anything I did wrong or is this normal?

---

### Post by Altair011001 on 2014-04-06
Hi all, attempting to install ubuntu compatable wireless drivers via Additional drivers.When I pressed activate, a window popped up that said "downloading and installing drivers" with a black box moving back and forth in the loading area. Its been like this for 3 hours and I dont know what to do. Should it take this long? did I do something wrong?

---

### Post by Hadaka on 2014-04-06
hi, please post the output of..
```
lspci -n | egrep '0200|0280'
```
thanks.

---

### Post by QIII on 2014-04-06
Threads merged.

Please do not start similar threads in different areas of the forum.  It causes confusion and dilutes the community's efforts to help you.

---

### Post by Altair011001 on 2014-04-06
Sorry, I thought I posted in the wrong forum so I made a new one... wont do it again.
01:00.0 0280: 14e4:4365 (rev 01)
02:00.0 0200: 10ec:8136 (rev 05)
Update- tried exiting out of the prgram, wont work.

---

### Post by Hadaka on 2014-04-06
Hi, your wirless card [14e4:4365] is a rare one and seems to
only work on 64 bit machines. so let's take a look at what you have.
please post..
```
uname -a
```
thanks.

---

### Post by Altair011001 on 2014-04-07
Sorry for the late response
.Linux ubuntu 3.11.0-19-generic #33~precise1-Ubuntu SMP Wed Mar 12 21:16:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Hadaka on 2014-04-07
Great! you have 64 bit...you lucked out.
here is the link...if you get stuck or need
help let us know...
[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

---

### Post by Altair011001 on 2014-04-07
I followed everything in first answer in your link like so: 

sudo dpkg -i wireless-bcm43142-dkms-6.20.55.19_amd64.deb



I received the following error:

dpkg:error processing wireless-bcm43142-dkms-6.20.55.19_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wireless-bcm43142-dkms-6.20.55.19_amd64.deb

---

### Post by Hadaka on 2014-04-07
ok, you should be following this link
[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)
dont forget to....
sudo apt-get install linux-headers$(uname -r | grep -Po "\-[a-z].*")
sudo apt-get install build-essential dkms

Download 64 AMD

then cd to the folder you downloaded to...if it is by default Downloads...note that the "D" is uppercase
if your default download folder is ..................................Desktop.......note that the "D" is uppercase

do...if....your default download folder is Downloads...go there and drag and drop your file to Desktop
and then issue commands.
to avoid typo...it is better to copy and paste the commnds
any problems..please post

---

### Post by Altair011001 on 2014-04-07
Sorry mate, ran acrross this problem when i copied the sudo dpkg -i wire*.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
matthew@ubuntu:~$ sudo apt-get install build-essential dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
matthew@ubuntu:~$ sudo dpkg -i wireless-bcm43142-dkms-6.20.55.19_amd64.deb
dpkg: error processing wireless-bcm43142-dkms-6.20.55.19_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wireless-bcm43142-dkms-6.20.55.19_amd64.deb
matthew@ubuntu:~$ sudo apt-get -i wireless-bcm43142-dkms-6.20.55.19_amd64.deb
E: Command line option 'i' [from -i] is not known.
matthew@ubuntu:~$ sudo dpkg -i wireless-bcm43142-dkms-6.20.55.19_amd64.deb
dpkg: error processing wireless-bcm43142-dkms-6.20.55.19_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wireless-bcm43142-dkms-6.20.55.19_amd64.deb
matthew@ubuntu:~$ cd Desktop
matthew@ubuntu:~/Desktop$     sudo dpkg -i wire*.deb
[sudo] password for matthew: 
Selecting previously unselected package wireless-bcm43142-oneiric-dkms.
dpkg: regarding wireless-bcm43142-dkms-6.20.55.19_amd64.deb containing wireless-bcm43142-oneiric-dkms:
 wireless-bcm43142-oneiric-dkms conflicts with bcmwl-kernel-source
  bcmwl-kernel-source (version 6.20.155.1+bdcom-0ubuntu0.0.2) is present and installed.
dpkg: error processing wireless-bcm43142-dkms-6.20.55.19_amd64.deb (--install):
 conflicting packages - not installing wireless-bcm43142-oneiric-dkms
Errors were encountered while processing:
 wireless-bcm43142-dkms-6.20.55.19_amd64.deb

---

### Post by chili555 on 2014-04-07
Hadaka is on a short break.> matthew@ubuntu:~$ sudo dpkg -i wireless-bcm43142-dkms-6.20.55.19_amd64.deb
dpkg: error processing wireless-bcm43142-dkms-6.20.55.19_amd64.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:You need to direct the terminal to the location where you downloaded the deb. Where is that? Downloads as Hadaka suggested previously? Then do:```
cd ~/Downloads
```List the contents of the directory:```
ls
```Is wireless-bcm43142-dkms-6.20.55.19_amd64.deb listed as one of the files in Downloads? If it is, then install it:```
sudo dpkg -i wire*.deb
```Please don't guess. In order to get this working requires precision. If in doubt, stop and ask.

---

### Post by Altair011001 on 2014-04-08
Nevermind, found I got same error... will re check everything...

---

### Post by Altair011001 on 2014-04-08
I got this
dpkg: regarding wireless-bcm43142-dkms-6.20.55.19_amd64.deb containing wireless-bcm43142-oneiric-dkms:
 wireless-bcm43142-oneiric-dkms conflicts with bcmwl-kernel-source
  bcmwl-kernel-source (version 6.20.155.1+bdcom-0ubuntu0.0.2) is present and installed.
dpkg: error processing wireless-bcm43142-dkms-6.20.55.19_amd64.deb (--install):
 conflicting packages - not installing wireless-bcm43142-oneiric-dkms
Errors were encountered while processing:
 wireless-bcm43142-dkms-6.20.55.19_amd64.deb
matthew@ubuntu:~/Downloads$ 

I downloaded some sort of kernel thing, and saw it in there. Could that be it?

---

### Post by chili555 on 2014-04-09
> I downloaded some sort of kernel thing, and saw it in there. Could that be it? Probably. Let's back up and take another look at it. Let's see what, if anything, you have installed now:```
sudo dpkg -s bcmwl-kernel-source
sudo dpkg -s wireless-bcm43142-dkms
```Once we know that result, we'll propose what I believe is a better solution.

---

### Post by Altair011001 on 2014-04-09
1.
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 4186
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: bcmwl
Version: 6.20.155.1+bdcom-0ubuntu0.0.2
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d*sv*sd*bc02sc80i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>
2.
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 4186
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: bcmwl
Version: 6.20.155.1+bdcom-0ubuntu0.0.2
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d*sv*sd*bc02sc80i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>
matthew@ubuntu:~/Downloads$ sudo dpkg -s wireless-bcm43142-dkms
Package `wireless-bcm43142-dkms' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

---

### Post by monkeybrain20122 on 2014-04-09
I don't know about 'Additional Driver', I have asked the question before and people told me that it works, only very very slowly. I cannot say for sure that it doesn't work but it may as well, I always get so fed up that I just abort after waiting forever and seeing no change. Instead I note the driver reported by AD and install from synaptic, it is done in less than a minute and I can see the progress that something is actually happening.

---

### Post by chili555 on 2014-04-09
> Package: bcmwl-kernel-source
Status: install ok [COLOR="#FF0000"]installed[/COLOR]
Priority: optional
Section: adminHere we have an interesting problem. You have the suggested package installed but it doesn't drive your device properly, if at all. 

Although you have installed 12.04:> #33~[COLOR="#FF0000"]precise[/COLOR]1-Ubuntu SMPThe 12.04.4 version includes the 3.11.0-xx kernel, the same as the latest Ubuntu version, Saucy. > Linux ubuntu [COLOR="#FF0000"]3.11.0-19-generic[/COLOR]I believe we can try the later Saucy version of bcmwl-kernel-source and abandon the itchy, twitchy wireless-bcm43142-dkms. 

With a working wired ethernet connection, copy and paste these commands:```
wget http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_amd64.deb
sudo dpkg -i bcmwl*.deb
```Assuming you have no errors, warnings, etc., detach the ethernet, reboot and let us hear your report.

---

### Post by Altair011001 on 2014-04-09
I got this but im gona restart anyway
Warning: No support for locale: en_US.utf8

---

### Post by Altair011001 on 2014-04-09
wait nvm, i just saw the rest of your post

---

