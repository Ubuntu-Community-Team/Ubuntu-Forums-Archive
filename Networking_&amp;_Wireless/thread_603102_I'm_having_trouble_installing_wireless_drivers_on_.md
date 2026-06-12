---
title: "I'm having trouble installing wireless drivers on KDE"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by 449 on 2007-11-04
I'm using the guide [http://ubuntuforums.org/showthread.php?t=405990] here ](http://ubuntuforums.org/showthread.php?t=405990] here ) for KDE. Here's my konsole log:

erik@erik-desktop:~$ cd ~
erik@erik-desktop:~$ wget [http://blakecmartin.googlepages.com/bcm43xx-0.3.2-internet.tar.gz](http://blakecmartin.googlepages.com/bcm43xx-0.3.2-internet.tar.gz)
--20:18:26--  [http://blakecmartin.googlepages.com/bcm43xx-0.3.2-internet.tar.gz](http://blakecmartin.googlepages.com/bcm43xx-0.3.2-internet.tar.gz)
           => `bcm43xx-0.3.2-internet.tar.gz.3'
Resolving blakecmartin.googlepages.com... 72.14.203.118
Connecting to blakecmartin.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19,375 (19K) [application/octet-stream]

100%[====================================>] 19,375        --.--K/s

20:18:26 (237.59 KB/s) - `bcm43xx-0.3.2-internet.tar.gz.3' saved [19375/19375]

erik@erik-desktop:~$ tar xvf bcm43xx-*.tar.gzbcm43xx-0.3.2bcm43xx-0.3.2.tar.gz
tar: bcm43xx-*.tar.gzbcm43xx-0.3.2bcm43xx-0.3.2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
erik@erik-desktop:~$                               

Did I type something wrong? I've tried it multiple times with no luck. :confused:

---

### Post by wieman01 on 2007-11-04
Try this instead:
> tar -xvf bcm43xx-0.3.2-internet.tar.gz

---

### Post by 449 on 2007-11-04
> bcm43xx-0.3.2-internet/
bcm43xx-0.3.2-internet/LICENSE
bcm43xx-0.3.2-internet/installer.py
bcm43xx-0.3.2-internet/S05firmware-init-script
bcm43xx-0.3.2-internet/wcm.sh
bcm43xx-0.3.2-internet/bcm43xx.sh
bcm43xx-0.3.2-internet/bcm43xx-ndiswrapper.sh
bcm43xx-0.3.2-internet/wicd-tray.desktop
bcm43xx-0.3.2-internet/stats-logger
bcm43xx-0.3.2-internet/LICENSE-BROADCOM
bcm43xx-0.3.2-internet/READMEs/
bcm43xx-0.3.2-internet/READMEs/README-wcm-wicd
bcm43xx-0.3.2-internet/READMEs/README-installer
bcm43xx-0.3.2-internet/READMEs/README-wcm-wifi-radar
bcm43xx-0.3.2-internet/READMEs/GPLv2
bcm43xx-0.3.2-internet/READMEs/README-bcm43xx-ndiswrapper
bcm43xx-0.3.2-internet/READMEs/README-bcm43xx
bcm43xx-0.3.2-internet/READMEs/CHANGELOG
bcm43xx-0.3.2-internet/README
erik@erik-desktop:~$ cd bcm43xx-0.3.2-internet.tar.gz
bash: cd: bcm43xx-0.3.2-internet.tar.gz: Not a directory
erik@erik-desktop:~$ cd  bcm43xx-0.3.2
bash: cd: bcm43xx-0.3.2: No such file or directory
erik@erik-desktop:~$ cd bcm43xx-0.3.2-internet
erik@erik-desktop:~/bcm43xx-0.3.2-internet$ ./installer.py
Traceback (most recent call last):
  File "./installer.py", line 12, in <module>
    import pygtk
ImportError: No module named pygtk
bcm43xx-0.3.2-internet/
bcm43xx-0.3.2-internet/LICENSE
bcm43xx-0.3.2-internet/installer.py
bcm43xx-0.3.2-internet/S05firmware-init-script
bcm43xx-0.3.2-internet/wcm.sh
bcm43xx-0.3.2-internet/bcm43xx.sh
bcm43xx-0.3.2-internet/bcm43xx-ndiswrapper.sh
bcm43xx-0.3.2-internet/wicd-tray.desktop
bcm43xx-0.3.2-internet/stats-logger
bcm43xx-0.3.2-internet/LICENSE-BROADCOM
bcm43xx-0.3.2-internet/READMEs/
bcm43xx-0.3.2-internet/READMEs/README-wcm-wicd
bcm43xx-0.3.2-internet/READMEs/README-installer
bcm43xx-0.3.2-internet/READMEs/README-wcm-wifi-radar
bcm43xx-0.3.2-internet/READMEs/GPLv2
bcm43xx-0.3.2-internet/READMEs/README-bcm43xx-ndiswrapper
bcm43xx-0.3.2-internet/READMEs/README-bcm43xx
bcm43xx-0.3.2-internet/READMEs/CHANGELOG
bcm43xx-0.3.2-internet/README
erik@erik-desktop:~$ cd bcm43xx-0.3.2-internet.tar.gz
bash: cd: bcm43xx-0.3.2-internet.tar.gz: Not a directory
erik@erik-desktop:~$ cd  bcm43xx-0.3.2
bash: cd: bcm43xx-0.3.2: No such file or directory
erik@erik-desktop:~$ cd bcm43xx-0.3.2-internet
erik@erik-desktop:~/bcm43xx-0.3.2-internet$ ./installer.py
Traceback (most recent call last):
  File "./installer.py", line 12, in <module>
    import pygtk
ImportError: No module named pygtk


Different response, but still no luck.

---

### Post by wieman01 on 2007-11-04
Then do:
> cd bcm43xx-0.3.2-internet
> ./installer.py
As you have done... Now you probably have to install other packages e.g. pygtk, could that be your problem?

---

### Post by 449 on 2007-11-04
For some reason I'm having a hard time with this. I tried everything you guys posted with no success so far.

---

### Post by wieman01 on 2007-11-04
Question: Why don't you post over there and get help from the OP? I think DarkN00b will be able to help you.

---

### Post by kevdog on 2007-11-04
You want to use the bcm43xx driver, but isnt this in the linux-restricted package in Gutsy (not in Feisty)?

Do you have a wired connection?? You could just do the installation automatically.

Id recommend ndiswrapper anyway -- a lot more stable than bcm43xx is right now!

Check your chipset - not all broadcom cards are bcm43xx compatible

```

supported

    * bcm4303 (802.11b-only chips)
    * bcm4306
          o all newer revisions supported (built after about Jan 2005)
          o old revisions partially supported. Lacks some features like hw-crypto. 
    * bcm4311 rev 1 / bcm4312
    * bcm4318 

unsupported

    * The 802.11a part of the 4309 and 4312 is not supported.
    * bcm4311 rev 2
    * There is no support for any Draft 802.11n features.

```

---

### Post by 449 on 2007-11-04
Yeah, I have a wired connection, how do I do it automatically? I'm pretty sure it's compatible because it worked in ubuntu 7.10.

---

### Post by kevdog on 2007-11-04
Go into synaptic and install the linux-restricted package.

---

### Post by 449 on 2007-11-04
> **kevdog said:**
> Go into synaptic and install the linux-restricted package.
 
I don't have synaptic, I have adept. Is there a difference? Anyways I search and the closest thing are three packages called linux-restricted module and they're all installed.

---

### Post by wieman01 on 2007-11-04
> **449 said:**
> I don't have synaptic, I have adept. Is there a difference? Anyways I search and the closest thing are three packages called linux-restricted module and they're all installed.
You are on Kubuntu Gutsy. Adept will do.

---

### Post by 449 on 2007-11-04
So, what am I doing, are the linux-restriction modules files the ones that are supposed to be installed? And if so what now?

---

### Post by kevdog on 2007-11-05
When you installed them, do you have an internet connection (ethernet connection).  Some files need to be downloaded from the internet to complete the installation.

---

