---
title: "Problem Installing Netgear A6100 Wifi USB mini adapter ac600 Dual band Ubuntu 14.04"
date: 2014-08-21
forum: Networking &amp; Wireless
---

### Post by bouha on 2014-08-21
Hi, im new to ubuntu i don't know much, im on ubuntu 14.04 amd64.

i'm trying to install Netgear A6100 Wifi USB mini adapter ac600 Dual band, i tried this [http://ubuntuforums.org/showthread.php?t=1806839](http://ubuntuforums.org/showthread.php?t=1806839) but it seems to be outdated the names of folders and files have changed, the commands don't work.

I don"t know what to do and what to begin with, please help.

---

### Post by chili555 on 2014-08-21
Welcome to the forums and Ubuntu! We are happy to help you. First, let's identify your device. Please open a terminal Ctrl+Alt+t and run and post:```
lsusb
```Thanks.

---

### Post by bouha on 2014-08-21
ty,

abdelkader@abdelkader-EasyNote-ST85-M-011FR:~$ lsusb
Bus 002 Device 004: ID 04f2:b029 Chicony Electronics Co., Ltd 1.3M UVC Webcam
Bus 002 Device 002: ID 0846:9052 NetGear, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 03f0:a407 Hewlett-Packard 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by chili555 on 2014-08-21
Your device uses the rare and elusive driver 8812au. Please get a temporary wired ethernet or similar connection, go back to the terminal and do:```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd ~/rtl8812AU_8821AU_linux
make
sudo make install
sudo modprobe 8812au
```Your wireless should now be working.

Post back any errors; warnings are probably alright. I will have one additional step.

---

### Post by bouha on 2014-08-21
Thank you very much it works well i did:

```
cd rtl8812AU_8821AU_linux/ 
```

instead of :

```
cd rtl8812au
```

Thanks again.

---

### Post by chili555 on 2014-08-21
I'm glad it's working! You have compiled the driver for your current kernel version only. When Update Manager installs a later linux-image, recompile:```
cd rtl8812AU_8821AU_linux/
make clean
make
sudo make install
sudo modprobe 8812au
```Please retain the file and these instructions for that time.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by bouha on 2014-08-21
ok, i will do that, thank you.

---

### Post by FrankFu on 2014-11-02
Hi, Guys, I met the same problem today, same device. But I got the Error like:

frank@frank-PC:~$ sudo apt-get install linux-headers-generic build-essential git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
linux-headers-generic set to manually installed.
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.7 git-man libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl liberror-perl libstdc++6-4.7-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.7-multilib gcc-4.7-doc libstdc++6-4.7-dbg
  git-daemon-run git-daemon-sysvinit git-doc git-el git-arch git-cvs git-svn git-email
  git-gui gitk gitweb libstdc++6-4.7-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.7 git git-man libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl liberror-perl libstdc++6-4.7-dev
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.7 MB/17.8 MB of archives.
After this operation, 45.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libstdc++6-4.7-dev g++-4.7 g++ dpkg-dev build-essential fakeroot liberror-perl
  git-man git libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main libstdc++6-4.7-dev i386 4.7.3-1ubuntu1
  404  Not Found [IP: 91.189.91.15 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main g++-4.7 i386 4.7.3-1ubuntu1
  404  Not Found [IP: 91.189.91.15 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main g++ i386 4:4.7.3-1ubuntu10
  404  Not Found [IP: 91.189.91.15 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main dpkg-dev all 1.16.10ubuntu1
  404  Not Found [IP: 91.189.91.15 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main build-essential i386 11.6ubuntu4
  404  Not Found [IP: 91.189.91.15 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main fakeroot i386 1.18.4-2ubuntu1
  404  Not Found [IP: 91.189.91.15 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main git-man all 1:1.8.1.2-1
  404  Not Found [IP: 91.189.91.15 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main git i386 1:1.8.1.2-1
  404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.7/libstdc++6-4.7-dev_4.7.3-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.7/libstdc++6-4.7-dev_4.7.3-1ubuntu1_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.7/g++-4.7_4.7.3-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.7/g++-4.7_4.7.3-1ubuntu1_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.7.3-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.7.3-1ubuntu10_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.16.10ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.16.10ubuntu1_all.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.6ubuntu4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.6ubuntu4_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.18.4-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.18.4-2ubuntu1_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/git/git-man_1.8.1.2-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/git/git-man_1.8.1.2-1_all.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/git/git_1.8.1.2-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/git/git_1.8.1.2-1_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
frank@frank-PC:~$ ^C

---

### Post by chili555 on 2014-11-02
> Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) [COLOR="#FF0000"]raring[/COLOR]/main libstdc++6-4.7-dev i386 4.7.3-1ubuntu1
404 Not Found [IP: 91.189.91.15 80]It seems that you are using an Ubuntu version that has reached end-of-life: [http://fridge.ubuntu.com/2014/01/28/ubuntu-13-04-raring-ringtail-end-of-life-reached-on-january-27-2014/](http://fridge.ubuntu.com/2014/01/28/ubuntu-13-04-raring-ringtail-end-of-life-reached-on-january-27-2014/)> This is a follow-up to the End of Life warning sent last month to confirm that as of today (Jan 27, 2014), Ubuntu 13.04 **is no longer supported**. No more package updates will be accepted to 13.04I suggest you upgrade to 14.04 LTS or 14.10.

---

### Post by jmunita on 2015-04-25
Hey guys. I install Ubuntu 15.04. I tried to install this USB Wifi, but when i tried to execute the make command, i receive this error message:

/home/user/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5087:2: warning: (near initialization for ‘rtw_cfg80211_ops.mgmt_tx’)
scripts/Makefile.build:257: recipe for target '/home/user/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.o' failed
make[2]: *** [/home/user/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.o] Error 1
Makefile:1394: recipe for target '_module_/home/user/rtl8812AU_8821AU_linux' failed
make[1]: *** [_module_/home/user/rtl8812AU_8821AU_linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-15-generic'
Makefile:1040: recipe for target 'modules' failed
make: *** [modules] Error 2

i need a extra package or my source have a problem?

Please help me.

Regards.

---

### Post by chili555 on 2015-04-25
> **jmunita said:**
> Hey guys. I install Ubuntu 15.04. I tried to install this USB Wifi, but when i tried to execute the make command, i receive this error message:

/home/user/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5087:2: warning: (near initialization for ‘rtw_cfg80211_ops.mgmt_tx’)
scripts/Makefile.build:257: recipe for target '/home/user/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.o' failed
make[2]: *** [/home/user/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.o] Error 1
Makefile:1394: recipe for target '_module_/home/user/rtl8812AU_8821AU_linux' failed
make[1]: *** [_module_/home/user/rtl8812AU_8821AU_linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-15-generic'
Makefile:1040: recipe for target 'modules' failed
make: *** [modules] Error 2

i need a extra package or my source have a problem?

Please help me.

Regards.Post #3 here will probably solve your problem: [http://ubuntuforums.org/showthread.php?t=2275054&highlight=8812au](http://ubuntuforums.org/showthread.php?t=2275054&highlight=8812au)

---

### Post by jmunita on 2015-04-25
Thank you!! It's Works!!

---

### Post by boucher-aaron on 2015-05-07
hi there, any idea how to get ubuntu to keep these settings after a kermel update? it a pain to have to keep putting code in to make the wifi work every time the machine updates
cheers Aaron

---

### Post by chili555 on 2015-05-07
> **boucher-aaron said:**
> hi there, any idea how to get ubuntu to keep these settings after a kermel update? it a pain to have to keep putting code in to make the wifi work every time the machine updates
cheers AaronI do not. Often, there is included in these packages a guide to doing so with *dkms*; not so here. Sorry.

---

### Post by jettles on 2015-05-08
Mine produces the same error on make. I'm using 14.04
Any assistance gratefully received

---

### Post by chili555 on 2015-05-08
> **jettles said:**
> Mine produces the same error on make. I'm using 14.04
Any assistance gratefully receivedEven after you try my suggestion above?

---

### Post by savayreon on 2015-08-01
I am trying this solution, but after the command github clone ... github is asking for username and password. Since I don't know that, I get a fatal: Authentications failed error. How do I get around that?

---

### Post by chili555 on 2015-08-01
> **savayreon said:**
> I am trying this solution, but after the command github clone ... github is asking for username and password. Since I don't know that, I get a fatal: Authentications failed error. How do I get around that?Please try this instead and, for the benefit of the searchers, let us know how it works: [http://askubuntu.com/questions/623048/help-with-belkin-dual-band-wireless-adapter-ac867/623126#623126](http://askubuntu.com/questions/623048/help-with-belkin-dual-band-wireless-adapter-ac867/623126#623126)

---

### Post by ethan30 on 2015-11-11
I have this same usb adapter, but I do not have any way of connecting to an alternate internet source to bypass this problem and install the usb adapter. What can I do?

---

### Post by chili555 on 2015-11-11
> **ethan30 said:**
> I have this same usb adapter, but I do not have any way of connecting to an alternate internet source to bypass this problem and install the usb adapter. What can I do?Please start a new thread and include:```
lsusb
uname -r
```The exact process varies according to your kernel version. Thanks.

---

### Post by ethan30 on 2015-11-11
Thanks I will boot Ubuntu and try this!

I will finish taking my Command line course, then try again. I have no idea what I'm doing

---

### Post by chili555 on 2015-11-11
> **ethan30 said:**
> I will finish taking my Command line course, then try again. I have no idea what I'm doingLet's see if I can help you. Please open a terminal with these keys: Ctrl+Alt+t. Type in:```
lsusb
```Press Enter. All the USB devices will be listed (Get it? LiSt USB!!) Either copy them all in your reply or pick out your USB wireless device. We specifically need all those numbers. Here is an example from my machine:```
chili@T410:~$ lsusb
[COLOR="#FF0000"]Bus 002 Device 011: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n[/COLOR]
Bus 002 Device 010: ID 1852:7022 GYROCOM C&C Co., LTD 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```The item I highlighted is a USB wireless. If you recognize yours, you can post it instead of all the rate hubs, etc.

Do the same with:```
uname -r
```Again, here is an example:```
4.2.0-18-generic
```Once we have those details, we can propose a complete solution.

Please see my sample.

[ATTACH=CONFIG]265502[/ATTACH]

---

### Post by jcorio on 2015-11-12
I also need help

Thank you for your help Chili..

jason@shuttlebox2:~/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux$ lsusb
Bus 001 Device 003: ID 0846:9052 [COLOR=#ff0000]NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU][/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jason@shuttlebox2:~/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux$

jason@shuttlebox2:~/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux$ uname -r
4.2.0-18-generic



I've tried your original post as you see my folder directory. 
Everything produced an on screen result except the last command
 sudo modprobe 8812au
did not give me any sort of output in console.

---

### Post by chili555 on 2015-11-12
> sudo modprobe 8812au
did not give me any sort of output in console.Excellent! That means that the driver got built and loads with no warnings and no errors!!!

Let's check a few more things:```
iwconfig
rfkill list all
dmesg | grep 8812
```

Note to searchers: This builds perfectly in Ubuntu 15.10: [https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git](https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git)

---

### Post by jcorio on 2015-11-12
jason@shuttlebox2:~$ iwconfig
lo        no wireless extensions.

enp2s0    no wireless extensions.
jason@shuttlebox2:~$ rfkill list all
jason@shuttlebox2:~$ dmesg | grep 8812
jason@shuttlebox2:~$

---

### Post by chili555 on 2015-11-12
> jason@shuttlebox2:~$ dmesg | grep 8812
jason@shuttlebox2:~$There should be *something* if the module is loaded properly. Let's try again:```
sudo modprobe 8812au
dmesg | grep -e 8812 -e rtl
```

---

### Post by jcorio on 2015-11-12
jason@shuttlebox2:~$ sudo modprobe 8812au
[sudo] password for jason: 
jason@shuttlebox2:~$ dmesg | grep -e 8812 -e rtl
[10303.368211] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[10303.370672] RTL871X: rtl8812au v4.3.8_12175.20140902
[10303.370727] usbcore: registered new interface driver rtl8812au
jason@shuttlebox2:~$

---

### Post by chili555 on 2015-11-12
Now we're getting there! Does it appear here now?```
iwconfig
```Does it scan and see networks?```
sudo iwlist scan
```If it scans, it ought to connect.

---

### Post by jcorio on 2015-11-12
it does not.

jason@shuttlebox2:~$ iwconfig
lo        no wireless extensions.

enp2s0    no wireless extensions.

jason@shuttlebox2:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

jason@shuttlebox2:~$

---

### Post by chili555 on 2015-11-12
> Bus 001 Device 003: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]And you promise solemnly that the USB wireless is plugged in, correct? If so, I'm not sure I have any other explanation or suggestions. 

Could it be defective?

---

### Post by ethan30 on 2015-11-12
I did some research and this wifi reciever uses the realtek chipset and the drivers can be downloaded here:

[https://sites.google.com/site/easylinuxtipsproject/file-closet/rtl8812AU_8821AU_linux.tar.gz?attredirects=0&d=1](https://sites.google.com/site/easylinuxtipsproject/file-closet/rtl8812AU_8821AU_linux.tar.gz?attredirects=0&d=1)

download it to a usb drive and load it to your ubuntu from the usb drive

mine is:
Bus 001 Device 003: ID 0846:9052
I don't remember everything listed after that on the same line. its hard to remember everything when everytimt i have something new to try, i have to reboot my computer.

a helpful website for aid in installation if you have a means of internet without the reciever is here:

[https://sites.google.com/site/easylinuxtipsproject/reserve-7](https://sites.google.com/site/easylinuxtipsproject/reserve-7)

---

### Post by ethan30 on 2015-11-13
okay I downloaded the package and I got a butt ton of txt docs with code in them. what do i do from here? do I take the code and create a file with the correct file type extension to make it a runnable program?

---

### Post by chili555 on 2015-11-13
> **ethan30 said:**
> okay I downloaded the package and I got a butt ton of txt docs with code in them. what do i do from here? do I take the code and create a file with the correct file type extension to make it a runnable program?Ordinarily, you would right-click the file and extract it. Then, assuming you have installed the packages *linux-headers-generic* and *build-essential*, you would compile the driver:```
cd ~/Desktop/rtl8812-whatever-wherever
make
sudo make install
sudo modprobe 8812au
```However, this assumes that this package is, in some way, superior to the package I linked from github, which I doubt. I doubt it because the vintage and origin of the Google code version is unknown to me. It may or may not build on your exact gcc and kernel version.

Do you have the prerequisites installed?```
sudo dpkg -s build-essential
sudo dpkg -s linux-headers-generic
```

---

### Post by ethan30 on 2015-11-13
thank you, I will try that!

---

### Post by ethan30 on 2015-11-13
I downloaded those packages and extracted them to my desktop for easy access in the terminal, but I cannot figure out how to install them. is there a video tutorial on this? i am a very visual person, so I sometimes have trouble learning what to do from lists of text.

---

### Post by chili555 on 2015-11-13
> is there a video tutorial on this?I'm unaware of one, but it seems that just about everything is on Youtube. You might search to see.

Sorry.

---

### Post by G_Andersson on 2015-11-14
Hi,
Im looking for advice.
I tried to follow
[COLOR=#000000]Your device uses the rare and elusive driver 8812au. Please get a temporary wired ethernet or similar connection, go back to the terminal and do:[/COLOR][COLOR=#000000]Code:
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git [COLOR=#ff0000]<< Have problem here[/COLOR]
git clone [https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git](https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git)
cd ~/rtl8812AU_8821AU_linux
make
sudo make install
sudo modprobe 8812au[/COLOR]
[COLOR=#000000]
[FONT=arial black]**I have:**[/FONT]
[/COLOR]pi@raspberrypi ~ $ lsusb
Bus 001 Device 006: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mous                  e
Bus 001 Device 005: ID 0e8f:0021 GreenAsia Inc. Multimedia Keyboard Controller
Bus 001 Device 004: ID 0846:9052 NetGear, Inc.
Bus 001 Device 003: ID 0424:ec00 Standard Microsystems Corp. SMSC9512/9514 Fast                   Ethernet Adapter
Bus 001 Device 002: ID 0424:9514 Standard Microsystems Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
pi@raspberrypi ~ $ uname -r
4.1.7-v7+
[FONT=arial black]**Problem 1 is that I can't get/fetch**[/FONT] "[COLOR=#000000][FONT=Ubuntu Mono]linux-headers-generic[/FONT][/COLOR]"


pi@raspberrypi ~ $ sudo apt-get install linux-headers-generic build-essential git
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-headers-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'linux-headers-generic' has no installation candidate



Suggestions???

---

### Post by chili555 on 2015-11-14
Please try:```
sudo apt-get install linux-headers-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~.

---

### Post by G_Andersson on 2015-11-14
Sorry for not using right syntax. See that its possible to edit but not delete a entry :)
pi@raspberrypi ~ $ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-headers-4.1.7-v7
E: Couldn't find any package by regex 'linux-headers-4.1.7-v7'

---

### Post by G_Andersson on 2015-11-14
[FONT=arial black]**Result is still not right...**[/FONT]


pi@raspberrypi ~ $ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-headers-4.1.7-v7
E: Couldn't find any package by regex 'linux-headers-4.1.7-v7'

---

### Post by G_Andersson on 2015-11-14
[FONT=arial black]**Still problem to resolve, ......**[/FONT]


pi@raspberrypi ~ $ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-headers-4.1.7-v7
E: Couldn't find any package by regex 'linux-headers-4.1.7-v7'

---

### Post by chili555 on 2015-11-14
> 4.1.7-v7I don't know where you got the kernel image 4.1.7-v7 for ARM, but I'm sure it wasn't the usual Ubuntu repositories. Wherever you got it may have the headers, too. Google shows us this as a possibility: [http://www.niksula.hut.fi/~mhiienka/Rpi/linux-headers-rpi/](http://www.niksula.hut.fi/~mhiienka/Rpi/linux-headers-rpi/)

DISCLAIMER: I know nothing about ARM, Pi (except pecan) nor non-standard Ubuntu packages. Your mileage may vary, read and follow all the safety warnings, I am not an attorney and all that.

---

### Post by G_Andersson on 2015-11-14
Hi,
I did search further and did find my drive to my Raspberry Pi at: [https://www.raspberrypi.org/forums/viewtopic.php?f=66&t=66499&p=836818&hilit=rtl8812AU#p836818](https://www.raspberrypi.org/forums/viewtopic.php?f=66&t=66499&p=836818&hilit=rtl8812AU#p836818)
Used uname -rv to get right os revision mapped towards correct drive, including the last -v7 argument :)

---

### Post by chili555 on 2015-11-14
So, you are all set? Happy, happy? Working as expected?

---

### Post by Chloe_Thomas on 2015-11-15
Hi everybody,

First of all, sorry for my English, I'm French but I didn't find anything about the Netgear A6100 a600 in the French forum.

I recently purchased an Acer Aspire V3 371 with a Qualcomm Atheros QCA61x4 wireless network adapter. Since it's not supported by Ubuntu, I would like to buy this Wifi USB mini adapter and I would like to be sure that it will work with Ubuntu.

I did not install Ubuntu on my laptop yet, but I think I'm going to install Ubuntu 14.04.

In this case, will I have to run this on the terminal :

sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone [https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git](https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git)
cd ~/rtl8812AU_8821AU_linux
make
sudo make install
sudo modprobe 8812au

Or is it different today with the updates?
If I install Ubuntu 15.10 rather than 14.04, will it work better without doing anything?

Thank you in advance

---

### Post by chili555 on 2015-11-15
Your commands are correct. I'd install 15.10 because it uses the latest kernel and several improvements. For me, at least, 15.10 works perfectly.

---

### Post by Chloe_Thomas on 2015-11-15
Ok, thank you very much. I'm going to install 15.10 instead of 14.04.

---

### Post by chili555 on 2015-11-15
> **Chloe_Thomas said:**
> Ok, thank you very much. I'm going to install 15.10 instead of 14.04.By the way, I'd love to work on your Qualcomm Atheros QCA61x4 wireless at some point. We need a willing test case to help us.

---

### Post by jcorio on 2015-11-15
Chili. I have two identical shuttleboxes so I am attempting this on shuttlebox1

> **jcorio said:**
> jason@shuttlebox2:~$ iwconfig
lo        no wireless extensions.

enp2s0    no wireless extensions.
jason@shuttlebox2:~$ rfkill list all
jason@shuttlebox2:~$ dmesg | grep 8812
jason@shuttlebox2:~$

I've repeated all steps and after these commands I have this as the output but I still don't see it working.

```
jason@shuttlebox1:~$ iwconfig
enxa063919f750c  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

enp3s9    no wireless extensions.

enp2s0    no wireless extensions.

jason@shuttlebox1:~$ rfkill list all
jason@shuttlebox1:~$ dmesg | grep 8812
[   12.738397] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[   12.885385] usbcore: registered new interface driver rtl8812au
[   13.418883] rtl8812au 1-6:1.0 enxa063919f750c: renamed from wlan0
jason@shuttlebox1:~$ 

```


OH and my iwlist scan output is 

```

jason@shuttlebox1:~$ sudo iwlist scan
[sudo] password for jason: 
enxa063919f750c  Scan completed :
          Cell 01 - Address: 00:19:E3:FA:DB:9E
                    ESSID:"kpwairport"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=58/100  
          Cell 02 - Address: 00:21:29:B9:E6:C2
                    ESSID:"get_in_my_belly"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=100/100  
          Cell 03 - Address: 84:61:A0:E0:7A:80
                    ESSID:"ATT128"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=54/100  
          Cell 04 - Address: 00:04:32:12:97:E9
                    ESSID:"TB Proprietary Channel. 6U"
                    Protocol:IEEE 802.11a
                    Mode:Master
                    Frequency:5.18 GHz (Channel 36)
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD390050F204104A00011010540008000B0050F204000510110020446F6E676C652020202020202020202020202020202020202020202020202020
                    Quality=0/100  Signal level=66/100  

lo        Interface doesn't support scanning.

enp3s9    Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

jason@shuttlebox1:~$ 

```



EDIT AGAIN..

Well I see my network as "get_in_my_belly" so yes it IS working.

No my ignorance is in how to connect to it. 

You rock chili

---

### Post by chili555 on 2015-11-15
> enxa063919f750c  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0Looks like it's working to me. Are available networks showing in Network Manager? Or do you have NM? Or...?

---

### Post by jcorio on 2015-11-15
heres the deal. I have been using these two shuttle boxes as guinea pigs for the last two days. This morning I was playing and was going to connect the two using a crossover cable. In the process I followed instructions that included uninstalling network-manager. I did. I reinstalled but it no longer shows in my "task manger" (lower right popup) sys tray. Also when I search apps in my K menu it doesnt find "network manager". 
I think I will reinstall fresh and follow you instructions on this machine again. It'll be the absolute first thing i do after updating the system.

I installed Wicd manager. It sees the WIFI. it sees my network. But I get a "wrong password" error and I know my password. It is on wpa 1/2 which is correct.

---

### Post by jcorio on 2015-11-15
System reinstalled. Reinstalled this driver. Works %100

I love you Chili.

---

### Post by mr_mike2 on 2015-12-29
Hello I have a Intel® Core&#8482; i7 CPU 920 @ 2.67GHz × 8 but the same mini usb wifi adapter
Bus 002 Device 002: ID 0846:9052 NetGear, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 045e:00b0 Microsoft Corp. Digital Media Pro Keyboard
Bus 007 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I am getting a different error and I figured it was because of the difference in processors. Is there another program for the Intel chip set?

here is the errors I have been receiving.

Err [http://packages.ros.org](http://packages.ros.org) $(lsb_release/-sc) amd64 Packages
  404  Not Found
Err [http://packages.ros.org](http://packages.ros.org) $(lsb_release/main amd64 Packages
  404  Not Found
Err [http://packages.ros.org](http://packages.ros.org) $(lsb_release/-sc) i386 Packages
  404  Not Found
Err [http://packages.ros.org](http://packages.ros.org) $(lsb_release/main i386 Packages
  404  Not Found
Ign [http://packages.ros.org](http://packages.ros.org) $(lsb_release/-sc) Translation-en_US
Ign [http://packages.ros.org](http://packages.ros.org) $(lsb_release/-sc) Translation-en
Ign [http://packages.ros.org](http://packages.ros.org) $(lsb_release/main Translation-en_US
Ign [http://packages.ros.org](http://packages.ros.org) $(lsb_release/main Translation-en
Fetched 3,234 kB in 5s (540 kB/s)
W: Failed to fetch http://packages.ros.org/ros/ubuntu/dists/$(lsb_release/-sc)/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://packages.ros.org/ros/ubuntu/dists/$(lsb_release/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://packages.ros.org/ros/ubuntu/dists/$(lsb_release/-sc)/binary-i386/Packages  404  Not Found

W: Failed to fetch http://packages.ros.org/ros/ubuntu/dists/$(lsb_release/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead. I am totally new to this Ubuntu.

---

### Post by chili555 on 2015-12-29
> **mr_mike2 said:**
> Hello I have a Intel® Core™ i7 CPU 920 @ 2.67GHz × 8 but the same mini usb wifi adapter
Bus 002 Device 002: ID 0846:9052 NetGear, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 045e:00b0 Microsoft Corp. Digital Media Pro Keyboard
Bus 007 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I am getting a different error and I figured it was because of the difference in processors. Is there another program for the Intel chip set?

here is the errors I have been receiving.

Err [http://packages.ros.org](http://packages.ros.org) $(lsb_release/-sc) amd64 Packages
  404  Not Found
Err [http://packages.ros.org](http://packages.ros.org) $(lsb_release/main amd64 Packages
  404  Not Found
Err [http://packages.ros.org](http://packages.ros.org) $(lsb_release/-sc) i386 Packages
  404  Not Found
Err [http://packages.ros.org](http://packages.ros.org) $(lsb_release/main i386 Packages
  404  Not Found
Ign [http://packages.ros.org](http://packages.ros.org) $(lsb_release/-sc) Translation-en_US
Ign [http://packages.ros.org](http://packages.ros.org) $(lsb_release/-sc) Translation-en
Ign [http://packages.ros.org](http://packages.ros.org) $(lsb_release/main Translation-en_US
Ign [http://packages.ros.org](http://packages.ros.org) $(lsb_release/main Translation-en
Fetched 3,234 kB in 5s (540 kB/s)
W: Failed to fetch http://packages.ros.org/ros/ubuntu/dists/$(lsb_release/-sc)/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://packages.ros.org/ros/ubuntu/dists/$(lsb_release/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://packages.ros.org/ros/ubuntu/dists/$(lsb_release/-sc)/binary-i386/Packages  404  Not Found

W: Failed to fetch http://packages.ros.org/ros/ubuntu/dists/$(lsb_release/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead. I am totally new to this Ubuntu.We have no idea what ros.org is, but it isn't Ubuntu. I doubt that we can help you. Sorry.

---

### Post by QIII on 2015-12-29
This thread was started quite some time ago and has been hijacked several times.

I suggest that those of you still seeking help start your own individual threads that can be dealt with in a less confusing manner.

Thanks for your persistence here, chili555!

Closed.

---

