---
title: "installing ZD1211B IEEE 802.11 b+g  Dapper drake"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by silvernode on 2007-03-14
Hey guys I have been having a major problem installing the PSP wifi max ZD1211B IEEE 802.11 b+g  on ubuntu Version 6.06 LTS for PC. The first time I tried to do this I had a buddy help me since he knew about linux a little. After forum searching and apt updates we managed to get Ubuntu to at least see the dongle. Well, thats all nice and dandy but we still couldn't get it to connect to our wireless router. We searched forums some more and installed some patches which ultimately made the dongle turn off. Since then I have uninstalled the same version of ubuntu 3 times and just now I have installed it again. This time my friend is not here and since i am downstairs and not close enough to plug my computer into my router directly, I cant get internet without using my dongle. Right now i am using xp to post this by the way :-) Anyway Im quite positive that a fresh install of ubuntu just isn't going to cut it when trying to install the drivers for the dongle. I have the disc with linux drivers on it and I figured why not try and install them from the disc again. Well I have a makefile and I do believe to run that i need to type in terminal "install - "Desktop/Foldername/makefile   but it says permission denied. Then I tried using sudo but that failed when it told me no such file or directory. My question is this: How do I install makefiles and if it wont work then what would i need to get to make this dongle work? I am hoping someone has some knowledge about this dongle and has successfully installed it on my ubuntu version. Thanks guys

---

### Post by chili555 on 2007-03-14
Here is a pretty good how-to on your dongle. [http://ubuntuforums.org/showthread.php?t=288753](http://ubuntuforums.org/showthread.php?t=288753)

The part I draw your attention to includes: ```
sudo apt-get install build-essential kernel-package gcc libncurses5   libncurses5-dev libqt3-mt-dev wireless-tools libssl-dev
```and```
sudo apt-get install linux-headers-2.6.17-10 linux-headers-2.6.17-10-386 linux-headers-2.6.17-10-generic linux-headers-386 linux-headers-generic linux-source
```Of course, these items need to match your running kernel which you can determine with:```
uname -r
``` Your sudo make command is failing because it is looking for one or more of these pieces and...no such file or directory.

So, how can we get these packages without an internet connection? ```
sudo gedit /etc/apt/sources.list
```See if there is a line that looks something like this:```
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted
```That line is intended to allow you to get packages from the CDROM that may not have been installed in the default installation. But, see that little # in front of the line? That comments out the line so it will be skipped, in deference to online sources that are more up-to-date. Simply remove the # and save and close.

Then sudo apt-get install all those packages. Ignore the complaints that apt-get is unable to contact the on-line repositories.

If you are able to get all the packages off the CDROM, go back to make and procede. If not, let us know and we'll conjure up some other magic.

---

### Post by silvernode on 2007-03-14
Ok i will try these. Internet will not be needed at this point am I correct? I'm gonna switch hard drives and boot up Linux.

---

### Post by silvernode on 2007-03-14
# deb cdrom:  was not in sources.list

---

### Post by chili555 on 2007-03-14
There is another way to do it. Plop your install CD in the drive and then:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install <all_that_stuff>
```Let us know.

---

### Post by silvernode on 2007-03-14
Ok man lol I just loaded up windows again but oh well back to ubuntu (linux is less annoying anyway haha) Btw do you have aim my friend? If so i will PM you with my username :-) Much faster way of getting answers to my problems.

---

