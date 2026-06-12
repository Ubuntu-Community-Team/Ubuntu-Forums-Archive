---
title: "driver upgrade issues."
date: 2010-07-08
forum: New to Ubuntu
---

### Post by deathstalker205 on 2010-07-08
I was upgrading from Nvidia drivers 185 to 195. Well uninstalling 185 went smooth. But when i tried to install 195, i get this error,

deathstalker@Deathstalker-PC:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up nvidia-current (195.36.24-0ubuntu1~10.04) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)
deathstalker@Deathstalker-PC:~$ 

So....I tried to uninstall the failed installation and yet again, I get basicly the same error,

deathstalker@Deathstalker-PC:~$ sudo apt-get purge nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-current*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 133MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 147228 files and directories currently installed.)
Removing nvidia-current ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing nvidia-current (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)
deathstalker@Deathstalker-PC:~$ 

I have tried everything I can think of short of just pulling out the shotgun in the closet and having some fun.

---

### Post by gordintoronto on 2010-07-08
I'm surprised you are not using Administration/Hardware Drivers.

---

### Post by deathstalker205 on 2010-07-09
Hehe, sometimes the gui loves to **** me off by telling me I can't do something so when i do anything with editing or installing if I can I use terminal, reminds me of using dos. who needs a gui!

---

