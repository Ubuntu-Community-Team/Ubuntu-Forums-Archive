---
title: "Can not install pidgin help please!"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by xketch on 2009-12-03
I started installin pidgin and mid process, computer crashed. Now i can not uninstall it or reinstall pidgin, i keep gettin errors that don't allow me to do either. I use ubuntu 9.10, i tried force uninstalling and the other simple methods, i want to uninstall it so i can do a fresh reinstall so it can run. As of now, it says pidgin is installin but not fully installed. I've looked at other threads and none of the commands thus far have helped and havent seen anyone with my problem. Thanks in advance.

Removing pidgin ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing pidgin (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 pidgin
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by earthpigg on 2009-12-03
hi,

have you tried this:

sudo apt-get clean

---

### Post by xketch on 2009-12-04
I typed in 
sudo apt-get clean
but nothin happned after, no messages appeared.

---

### Post by earthpigg on 2009-12-04
nothing is supposed to. did you try installing/uninstalling pidgin after running that command?

---

### Post by xketch on 2009-12-04
E: pidgin: subprocess installed pre-removal script returned error exit status 2

Im still gettin errors when tryin to uninstall it, same ones for other methods, and the error above is from tryin to remove the package from synaptic package manager.

---

### Post by xketch on 2009-12-04
bump

---

### Post by M!K3_$ on 2009-12-04
why dont you download and compile the source?

---

### Post by xketch on 2009-12-04
how exactly is that done and will that override the errors that i am receiving?

---

### Post by M!K3_$ on 2009-12-04
you can download it from here,
[http://pidgin.im/]("http://pidgin.im/")

to compile source follow this,
[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by xketch on 2009-12-04
i couldnt do the first step of the easy install instructions. towards the end of the process, in terminal i received this error.

Processing triggers for man-db ...
Setting up pidgin (1:2.6.3-1ubuntu1~pidgin1.9.10) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing pidgin (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up checkinstall (1.6.1-8ubuntu1) ...
Setting up libstdc++6-4.4-dev (4.4.1-4ubuntu8) ...
Setting up g++-4.4 (4.4.1-4ubuntu8) ...
Setting up g++ (4:4.4.1-1ubuntu2) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.

Setting up build-essential (11.4) ...
Errors were encountered while processing:
 pidgin
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by M!K3_$ on 2009-12-04
this is all very obscure. what version of ubuntu are you using. everything before 9.10 has pidgin installed by default. you should only have to do
```
sudo apt-get install pidgin
```

---

### Post by xketch on 2009-12-04
It seems that this problem is bigger than i let on. It now appears that i can not install any new packages or delete any because i get the same error as the one i've been listing. it is somehow interfering with every install/uninstall option. There has to be someone that has experienced this problem before.

---

### Post by M!K3_$ on 2009-12-04
> **xketch said:**
> It seems that this problem is bigger than i let on. It now appears that i can not install any new packages or delete any because i get the same error as the one i've been listing. it is somehow interfering with every install/uninstall option. There has to be someone that has experienced this problem before.

Wow. :-k

can you do a regular 
```
sudo apt-get update
```
or a
```
sudo apt-get upgrade
```

---

### Post by xketch on 2009-12-04
I was able to do the first one, as for the second, i received same message. I am using ubtuntu 9.10


sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up pidgin (1:2.6.3-1ubuntu1~pidgin1.9.10) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing pidgin (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 pidgin
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by M!K3_$ on 2009-12-04
this guy seemded to find a solution
[http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/]("http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/")

---

### Post by k3lt01 on 2009-12-04
First things first, it is often best not to try to compile anything from source if you haven't found the problem in the first place. You may just exacerbate things.

Now have you gone to Synaptic and checked for broken packages? That is in the "Custom Filters" button on the left side of Synaptic. Click on Broken packages and see if there are any there.

If there are right click on them and "Mark for Complete Removal". If that works then try installing Pidgin through Synaptic not by source.

---

### Post by M!K3_$ on 2009-12-04
> **M!K3_$ said:**
> this guy seemed to find a solution
[http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/]("http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/")

check this out

---

### Post by xketch on 2009-12-04
> **M!K3_$ said:**
> this guy seemded to find a solution
[http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/](http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/)


One problem with that, after deleting the selection, it is not allowin me to save, tellin me i do not have privilages to save. I am admin and there are no other users, and password is typed in. Any way around this or reason this is happenin?

I tried the Broken filter, same error, then it was removed from Broken package filter without any change in the uninstallin/installin

---

### Post by xketch on 2009-12-04
Now when i try to login as root "su -" followed by password, i get,

su: Authentication failure

Is this an entirely new problem? I am 100% sure i am admin, and password is correct, seein as this is a fresh install of ubuntu. Is there a simple way to check the root password or to change it? I dont see why it would be a problem since i only ever entered one password at install.

---

### Post by M!K3_$ on 2009-12-04
> **xketch said:**
> One problem with that, after deleting the selection, it is not allowin me to save, tellin me i do not have privilages to save. I am admin and there are no other users, and password is typed in. Any way around this or reason this is happenin?

I tried the Broken filter, same error, then it was removed from Broken package filter without any change in the uninstallin/installin

you will need to run your text editor with sudo.

```
sudo gedit bla.txt
```

that will let you save after you make changes

---

### Post by xketch on 2009-12-04
> **M!K3_$ said:**
> you will need to run your text editor with sudo.

```
sudo gedit bla.txt
```that will let you save after you make changes


Genius......thanks for your help, much appreciated. Now to figure out how to mark as solved.

---

### Post by j2bv16 on 2009-12-04
try > sudo apt-get autoremove  and paste this in a terminal 
> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

> echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

update and try to install pidgin now. compile is to hard to do

---

### Post by M!K3_$ on 2009-12-04
> **xketch said:**
> Genius......thanks for your help, much appreciated. Now to figure out how to mark as solved.
under thread tools there is an option to mark thread as solved

---

