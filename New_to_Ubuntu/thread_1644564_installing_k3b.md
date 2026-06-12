---
title: "installing k3b"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by arjunlalb on 2010-12-13
Hi

help needed. When I try to install the application k3b on my Ubuntu 10.10 (Maverick Meerkat) system... I see the following error..

> arjunlal@Arjunlal-DT:~$ sudo apt-get install k3b
[sudo] password for arjunlal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 k3b : Depends: kdebase-runtime but it is not going to be installed
       Depends: libk3b6 (= 2.0.1-1ubuntu3) but it is not going to be installed
       Depends: libkde3support4 (>= 4:4.4.4) but it is not going to be installed
       Depends: libqt4-qt3support (>= 4:4.5.3) but it is not going to be installed
E: Broken packages

so, I decided to install the package 'libqt4-qt3support' first and the result is as follows

> arjunlal@Arjunlal-DT:~$ sudo apt-get install libqt4-qt3support
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqt4-qt3support : Depends: libqt4-designer (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
                     Depends: libqt4-network (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
                     Depends: libqt4-sql (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
                     Depends: libqt4-xml (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
                     Depends: libqtcore4 (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
                     Depends: libqtgui4 (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
E: Broken packages

Hence I tried to install the package 'libqtgui4' and the result is as follows... Help needed :-(

> arjunlal@Arjunlal-DT:~$ sudo apt-get install libqtgui4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqtgui4 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



I'm unable to install any packages that are dependent on the above mentioned ones :-(

---

### Post by oldos2er on 2010-12-13
Open Synaptic (System, Administration, Synaptic Package Manager), click menus Settings, Repositories, and make sure you have all repositories enabled. Click Reload, and see if you're able to install k3b now.

You can also click Edit, Fix Broken Packages if you need to.

---

### Post by arjunlalb on 2010-12-14
> **oldos2er said:**
> Open Synaptic (System, Administration, Synaptic Package Manager), click menus Settings, Repositories, and make sure you have all repositories enabled. Click Reload, and see if you're able to install k3b now.

You can also click Edit, Fix Broken Packages if you need to.


Thanks for your suggestion.. but Still no use...

---

### Post by coffeecat on 2010-12-14
Do you have either of the backports or proposed repositories enabled? These can cause problems. If you have, have a look here:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

---

