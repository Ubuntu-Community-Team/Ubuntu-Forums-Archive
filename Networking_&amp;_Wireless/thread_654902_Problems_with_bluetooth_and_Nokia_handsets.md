---
title: "Problems with bluetooth and Nokia handsets"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by KNT on 2007-12-31
Hello

My hardware is an Asus F3F. I've installed Kubuntu recently on it. The install was Fiesty but I've upgraded it to Gutsy the same day.
The problem is that two mobile phones (Nokia 6680 and E61) cannot send files to my laptop. Both get the same error: "Unable to connect".
KDE configuration files were taken from my previous system, Debian, where things _worked fine_.
So I assume that this is not a hardware problem on both sides.
Bluetooth config files were unmodified from the install. Later I've added the 6680 to rfcomm.conf as rfmcomm0. No change.
The 6680 was paired all the time. The E61 was tested paired and unpaired.
In the case of an unpaired E61 a dialog window asking me should the phone be allowed or denied access appeared. But after accepting the same error message appeared.
I've tried this on distribution kernel 2.6.22-14-generic and a custom built 2.6.22.9.
All config files and command outputs are on-demand.

---

### Post by KNT on 2008-01-14
If nobody can help me, then I'll should report it as a bug?

---

### Post by pingflood on 2008-05-13
Look here:

[https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/146145](https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/146145)

and here:

[http://bluetooth.kmobiletools.org/svn-howto](http://bluetooth.kmobiletools.org/svn-howto)

Regards

---

