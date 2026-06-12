---
title: "Cannot install new software"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by tekwrytr on 2011-02-27
Downloaded Ubuntu yesterday, wubi on Windows. I go to Software Center, select an app (in this case, NetBeans), click Install. The NetBeans label grays out, an Authentication dialog box pops up. I enter password, click Authenticate. The NetBeans label remains grayed out for three-four minutes, then returns to the normal display. I check for the software, nothing there. 
 
The instructions I am using indicates that when the software is downloaded, the Install button should change to a Remove button (indicating the software has been downloaded). In this case, it simply goes back to the original display (Install) and the Authenticate dialog box stays onscreen. Password is correct. Multiple tries, same result.
 
Any suggestions would be greatly appreciated.
Thanks!

---

### Post by davidmohammed on 2011-02-27
It worth checking first just in-case your "package manager" is having issues.

open a terminal and type

sudo apt-get update

sudo apt-get upgrade

are there any errors reported?  If so, please copy and paste the output and post in a reply here - in [CODE] tags please.

---

### Post by tekwrytr on 2011-02-27
> **davidmohammed said:**
> It worth checking first just in-case your "package manager" is having issues.

open a terminal and type

sudo apt-get update

sudo apt-get upgrade

are there any errors reported?  If so, please copy and paste the output and post in a reply here - in [CODE] tags please.

There is no JRE and no support for the default language, but nothing else that looks like an error. Last screen (of MANY) is below. Thanks.

Setting up openoffice.org-writer (1:3.2.1-7ubuntu1.1) ...
Processing triggers for python-central ...
Setting up openoffice.org-emailmerge (1:3.2.1-7ubuntu1.1) ...
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package openoffice.org-java-common
is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml
Copying: mailmerge.py
Enabling: mailmerge.py
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package openoffice.org-java-common
is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml

unopkg done.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Warning: No support for locale: en_US.utf8
tekwrytr@ubuntu:~$

---

### Post by davidmohammed on 2011-02-27
looks like some updates needed installing.

Can you repeat the update & upgrade steps again - you should get a much smaller output this time since nothing more needs to be downloaded and installed.

If no errors - try installing again from software centre.

---

### Post by deepakjoy on 2011-02-27
JDK 5 or 6 is a requirement for Netbeans, maybe thats your problem...

---

### Post by tekwrytr on 2011-02-27
> **deepakjoy said:**
> JDK 5 or 6 is a requirement for Netbeans, maybe thats your problem...
 
I tried downloading a Python IDE and the same thing happened. The label grays out, three-four minutes go by, the label reverts to normal color with Install button. Authenticate dialog box still shows.

---

### Post by davidmohammed on 2011-02-27
try running software-centre from the terminal - are there any error messages displayed in the terminal when you are trying to install from software-centre?

run in the terminal session

/usr/bin/software-center

---

### Post by tekwrytr on 2011-02-27
> **davidmohammed said:**
> try running software-centre from the terminal - are there any error messages displayed in the terminal when you are trying to install from software-centre?
 
run in the terminal session
 
/usr/bin/software-center
 
Apparently something was wonky with the wubi download. I downloaded the desktop on a thumb drive, set it up on dedicated partition and it works great now. Thanks for the help!

---

