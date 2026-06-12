---
title: "Lubuntu 14.04 *** wicd **** offline install"
date: 2017-08-26
forum: Networking &amp; Wireless
---

### Post by empfire on 2017-08-26
I have an 2x183+1GB\RAM laptop, will be running Lubuntu 14.04 LTS.

TO THE ISSUE:
When installing 17.04 or 16.04 network-manager-gnome smooth connection to the laptop is established.

When installing 14.04 network manager senses the connections available, but does not establish connection -not in mini, alternate or desktop install.
When 14.04 is installed, adding the network connections to panel shows two icons - eth0 and wifi-adapther. Pointing on them shows little or no connectivity. Though the available connections list appears for some seconds and the disappears. Clicking on available connections produces nothing more than the list disappearing.
AND THIS IS INSTALLATION OUT OF THE BOX. WHY IS AN IMAGE OF SO LONG EXISTING SYSTEM WITH LTS NOT WORKING OUT OF BOX\FRESH INSTALL,
WHEN OTHER LUBUNTU VERSIONS POSE NO PROBLEMS WHATSOEVER???

**SOLUTION**
will be an offline WICD install.

Have already tried this "wicd_1.7.4.tar.bz2" [https://ubuntuforums.org/showthread.php?t=1524810](https://ubuntuforums.org/showthread.php?t=1524810), with no installation success.
Have tried wicd*.tar.xz but ./configure plainly does nothing.
Have purge network-gnome-managerand installedwicd, but no result.
And did this [https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD) but the process in wicd looped at the status bringing up the structure or something, just before obtaining IP address.

1.ANY INTERFERENCES BETWEEN NETWORK-MANAGER-GNOME AND WICD EXISTS? MUST FIRST NEED TO BE UNINSTALLED FOR THE OTHER TO WORK?
2.DO I NEED TO UPGRADE NETWORK-MANAGER-GNOME? BEFORE INSTALLING WICD,
[B]3.AND A VERY IMPORTANT QUESTION AS WELL IS exactly WHICH WICD DEPENDENCIES ARE ALREADY SATISFIED BY 14.04.5 LTS, AND WHICH ONES ARE NOT -
SINCE THERE ARE SO MANY + WHICH RECOMMENDED ARE TO BE INSTALLED WHEN OPTING FOR AN OFF-LINE DEB PACKAGE INSTALLATION FOR THE SMOOTH NO WIRES CONNECTION?[/B]

Again no issues exist with the network and\or hardware since 16.04 and 17.04 do their job smoothly.

---

### Post by praseodym on 2017-08-27
1.) It is enough to deactivate NWM in autostart

2.) No

3.) You need the ones in Red from here:

[https://packages.ubuntu.com/trusty/wicd](https://packages.ubuntu.com/trusty/wicd)

BTW: Lubuntu 14.04 is EoS, use 16.04 instead

---

### Post by chili555 on 2017-08-27
>  WHY IS AN IMAGE OF SO LONG EXISTING SYSTEM WITH LTS NOT WORKING OUT OF BOX\FRESH INSTALL,
WHEN OTHER LUBUNTU VERSIONS POSE NO PROBLEMS WHATSOEVER???I am quite confident that the wireless driver version and its dependencies; likely cfg80211 and mac80211, included in the older kernel in 14.04 is not quite as refined as those in 16.04 and later. The kernel developers (not the Ubuntu developers) do not routinely (or ever, that I've seen} backport improvements in device drivers to older kernels. > SOLUTION
will be an offline WICD install.
I am also quite confident that Wicd is not going to help here.

If 16.04 works as expected, I recommend that you use it.

---

### Post by Bucky Ball on 2017-08-27
Welcome. As praseodym mentioned, Lubuntu 14.04 is and older release and no longer supported, so good thing the wireless works in supported releases without issue. :)

---

