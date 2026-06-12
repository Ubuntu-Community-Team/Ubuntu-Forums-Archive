---
title: "Synaptic Package Manager Error"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by akshay1 on 2009-02-08
I keep getting this in the Synaptic Package Manager:

E: The package dcp1000lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I close the window, and the manager closes.

I have tried suggestions in previous threads such as dpkg --configure -a
 etc, but this has not worked.
I no longer need the dcp1000lpr - this was an attempt to load a Brother printer driver

Thanks in advance - i an a total beginner

---

### Post by gettinoriginal on 2009-02-09
The opening cache error is due to having more than one package manager (Synaptic/Add Remove/Terminal) open when trying to install or uninstall something.  
Since you are getting an error message about reinstalling dcp1000lpr, I would go ahead and reinstall it, as it will not hurt anything to have it.
```
sudo apt-get install dcp1000lpr
```

---

### Post by akshay1 on 2009-02-10
Thanks for your help - I tried but got this message:

akshay@UBUNTU:~$ sudo apt_get install dcp1000lpr
[sudo] password for akshay: 
sudo: apt_get: command not found
akshay@UBUNTU:~$ sudo apt-get install dcp1000lpr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package dcp1000lpr needs to be reinstalled, but I can't find an archive for it.
akshay@UBUNTU:~$

---

### Post by stumbleUpon on 2009-02-10
Try to remove the package completely

```
sudo aptitude purge dcp1000lpr
```

---

### Post by akshay1 on 2009-02-11
Sorry, but still not successful:

This is what I get:
0 packages upgraded, 0 newly installed, 3 to remove and 216 not upgraded.
Need to get 0B of archives. After unpacking 283kB will be freed.
Do you want to continue? [Y/n/?] 


and then
......
The following packages will be REMOVED:
  dcp1000lpr{p} 
0 packages upgraded, 0 newly installed, 3 to remove and 216 not upgraded.
Need to get 0B of archives. After unpacking 283kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing dcp1000lpr (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 dcp1000lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
....

Still unable to unlock the Synaptic P M

Any other suggestions? Thanks in advance.

---

### Post by oldos2er on 2009-02-11
The command is apt-get, not apt_get.

---

### Post by stumbleUpon on 2009-02-12
You seem to have some apt-get processing running in the background. Have you tried restarting the computer. This should kill all running processes.


> akshay@UBUNTU:~$ sudo apt-get install dcp1000lpr
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package dcp1000lpr needs to be reinstalled, but I can't find an archive for it.

Is this package in the ubuntu repositories...? Or did you add some other repository, tried to install it and then removed the repository from /etc/apt-get/sources.list....? I cant find this in aptitude.

---

### Post by akshay1 on 2009-02-12
I tried to install the Brother printer driver for linux. When it appeared to not install, I tried to uninstall, but am faced with this problem. I have tried to reinstall the DCP1000, but it needs the synaptics package manager, which keeps crashing. So i appear to be in a catch 22 of my own creation!
I did reboot. I think the update manager may be running in the background as I tried to update, but this also could not proceed until the Error message was resolved.

RE: Apt_Get - I did correct that to Apt-get.

Thanks again - I think my hand is getting burnt, but I do want to persevere with Ubuntu!

---

### Post by mc4100 on 2009-02-12
This should be fixable. But first, more info is needed, there is no package called dcp1000lpr, afaik. There is brother-lpr-drivers-x

Can you remember anything about the name of package?
Maybe this might find it:
```
ls /var/cache/apt/archives/ | grep brother
```

By the way, what is the printer model?

I have a feeling it's brother-lpr-drivers-laser1

---

### Post by plucky on 2009-02-12
Have you still got the downloaded .deb package for the driver?

If so ```
cd <location of .deb package>
ls 
sudo  dpkg  -i  --force-all  --force-architecture  dcp1000lpr-1.1.2-1.i386.deb
dpkg  -l  |  grep  Brother
```

The "ls" command is to make sure you are in the correct directory if you can see the .deb file.

Don't run the "dpkg" command until you are in the correct directory.

If the "dpkg" command runs correctly then the last command will look like this ```
$ dpkg -l | grep Brother
ii  dcp1000lpr                                1.1.2-1
      Brother lpr Laser Printer Definitions
$
```

To remove the driver use ```
 sudo  dpkg  -r  --force-all  --force-architecture  dcp1000lpr-1.1.2-1.i386.deb
``` where you change the -i to a -r.


Good Luck


p.s. If you need to install the drivers for Brother printers,Use the **Synaptic Package Manager** and search for DCP-1000

---

### Post by akshay1 on 2009-02-12
Here is what happened: the .deb file is on the desktop.

akshay@UBUNTU:~$ cd /home/akshay/Desktop
akshay@UBUNTU:~/Desktop$ ls
control                              fielas child summer assignment.abw
control.tar.gz                       fielas child summer hw REAL.doc
cupswrapperDCP1000-1.0.2-1.i386      glines.desktop
cupswrapperDCP1000-1.0.2-1.i386.deb  ICAINSTALL
data.tar.gz                          tsclient.desktop
dcp1000lpr-1.1.2-1.i386              untitled folder
dcp1000lpr-1.1.2-1.i386.deb          usr
debian-binary                        Welcome_Back_Cat.pdf
akshay@UBUNTU:~/Desktop$ sudo  dpkg  -i  --force-all  --force-architecture  dcp1000lpr-1.1.2-1.i386.deb
(Reading database ... 139122 files and directories currently installed.)
Preparing to replace dcp1000lpr 1.1.2-1 (using dcp1000lpr-1.1.2-1.i386.deb) ...
Unpacking replacement dcp1000lpr ...
/var/lib/dpkg/info/dcp1000lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing dcp1000lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 dcp1000lpr-1.1.2-1.i386.deb
akshay@UBUNTU:~/Desktop$ 

Should I proceed with the next line of code? Thanks

---

### Post by plucky on 2009-02-13
> /var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found


That is the error,it could not find the lpd directory.To correct the error, open a terminal and use ```
sudo mkdir /etc/init.d/lpd
``` and then re-run the same command again.Post again if any errors.


Good Luck

---

### Post by akshay1 on 2009-02-13
Tried it, but this problem is very stubborn:"permission denied"

akshay@UBUNTU:~/Desktop$ sudo  dpkg  -i  --force-all  --force-architecture  dcp1000lpr-1.1.2-1.i386.deb
(Reading database ... 139122 files and directories currently installed.)
Preparing to replace dcp1000lpr 1.1.2-1 (using dcp1000lpr-1.1.2-1.i386.deb) ...
Unpacking replacement dcp1000lpr ...
/var/lib/dpkg/info/dcp1000lpr.postrm: 3: /etc/init.d/lpd: Permission denied
dpkg: warning - old post-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: Permission denied
dpkg: error processing dcp1000lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 126
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: Permission denied
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
 dcp1000lpr-1.1.2-1.i386.deb

---

### Post by plucky on 2009-02-14
I just tried this on my test system running 8.10.

This is how I got rid of the error.

Open a terminal and ```
gksudo gedit /var/lib/dpkg/status
```
Click on **Search** and then **Find** and search for **dcp1000lpr**

This is what you should find ```
Package: dcp1000lpr
Status: deinstall reinstreq half-installed
Maintainer: Brother Industries, Ltd.
Architecture: i386
Version: 1.1.2-1
Description: Brother lpr Printer Definitions
 Copyright: 2003 Brother Industries, Ltd. All Rights Reserved
 Brother printer Driver
```

Delete it all then **Save** the file and then exit from gedit.


You will find that you can now use Synaptic Package Manager again.

You can now search Synaptic for dcp-1000 and you will find the LPR and Cupswrapper drivers for the DCP-1000 printer.Mark both for installation and apply.


Good Luck

---

### Post by akshay1 on 2009-02-15
Worked like a charm. Thanks. Did not have a clue what I was doing. Also loaded the driver. My next challenge is loading citrix metaframe....wish me luck!

---

