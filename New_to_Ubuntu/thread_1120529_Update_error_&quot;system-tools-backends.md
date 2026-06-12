---
title: "Update error &quot;system-tools-backends"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by Dr Mac 24 on 2009-04-09
Installing resent Updates gave the following error message shown in screen snapshot, attached hopefully.It relates to errors in processing "system-tools-backends". 

My system still works OK, so there may not be a problem?

I would appreciate any help on resolving the problem.

---

### Post by miegiel on 2009-04-09
Try:```
sudo apt-get update
sudo apt-get upgrade
```
If apt-get doesn't list any errors everything should be OK.

---

### Post by Dr Mac 24 on 2009-04-09
Tries Your suggestion. Result:

QUOTE

ddddd@EEEEEE:~$ sudo apt-get update
[sudo] password for ddddd: 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
.
.
.
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages
Reading package lists... Done
ddddd@EEEEEE:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)
ddddd@EEEEEE:~$ sudo dpkg --configure -a 
ddddd@EEEEEE:~$ 

END QUOTE

The failure still occurred. I think the latter command lists all updates not installed correctly, so I guess there is no problem, yes?

---

### Post by bapoumba on 2009-04-09
[http://ubuntuforums.org/showpost.php?p=6230536&postcount=14](http://ubuntuforums.org/showpost.php?p=6230536&postcount=14)
Looks like removal and reinstallation worked for others. Make sure you write down which packages are removed to reinstall them later on (see down the quoted thread).

---

### Post by Dr Mac 24 on 2009-04-09
> **bapoumba said:**
> [http://ubuntuforums.org/showpost.php?p=6230536&postcount=14](http://ubuntuforums.org/showpost.php?p=6230536&postcount=14)
Looks like removal and reinstallation worked for others. Make sure you write down which packages are removed to reinstall them later on (see down the quoted thread).

Thanks, your pointer to the previous thread worked [http://ubuntuforums.org/images/icons/icon7.gif](http://ubuntuforums.org/images/icons/icon7.gif). I also had a failed graphics driver install.

Note I have 8.10 AMD64.

---

### Post by bapoumba on 2009-04-09
Glad to see you fixed it :)

---

