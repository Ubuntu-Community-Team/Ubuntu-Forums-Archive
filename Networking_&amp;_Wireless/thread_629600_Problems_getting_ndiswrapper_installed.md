---
title: "Problems getting ndiswrapper installed"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by hal10001 on 2007-12-02
I've been trying to get ndiswrapper installed, but I just can't seem to get it working.

The first method I tried was from the source via the instructions from ndiswrapper on sourceforge, but I got a bunch of errors, mostly files/directories not found -- too many to copy here. Their wiki suggested that Ubuntu might have some problems and suggested a different approach.

The second method I tried was from the package installed from the CD-ROM, and the Ubuntu Wiki said it should be called ndis... it wasn't on the CD when I browsed from the administration > package installer. This wasn't a live boot either, so I know that wasn't the problem.

The final method I tried was outlined on the Ubuntu Wiki at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper). The errors I got when entering the proper commands was "failed to open package info file '/var/lib/dpkg/tmp.ci/control' for reading: No such file or directory".

I don't have wired Internet via the computer with Ubuntu, so I can't use apt-get install, but is this my only other option? This is really frustrating -- I can't get any method to work, and I am following the instructions exactly with each method I listed. I am using Ubuntu 7.04. Thanks.

(I apologize if this is a double-post -- I thought I posted this earlier, but it didn't show up -- I think I closed it down in preview mode.)

---

### Post by sethvath on 2007-12-02
Where exactly did you get the error message: "failed to open package info file '/var/lib/dpkg/tmp.ci/control' for reading: No such file or directory"?

Make sure the 3 debs are not corrupted when you download them. 
[http://packages.ubuntu.com/feisty/misc/ndiswrapper-common](http://packages.ubuntu.com/feisty/misc/ndiswrapper-common)
[http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/feisty/net/ndisgtk](http://packages.ubuntu.com/feisty/net/ndisgtk)

---

### Post by hal10001 on 2007-12-02
How would I know if they are corrupted? I have to burn them to CD to get them over to the computer with Ubuntu -- could that corrupt them possibly?

When I ran the following commands is when I got the errors:

sudo dpkg -i ndiswrapper-common_*.deb
sudo dpkg -i ndiswrapper-utils*.deb
sudo dpkg -i --force-depends ndisgtk_*.deb

Replacing the "*" of course with the proper file version.

---

### Post by kevdog on 2007-12-02
Take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by sethvath on 2007-12-02
That might, I've had corrupted files moving them from windows to linux and vice versa. 

I see you forced-dependencies on ndisgtk, make sure you have the appropriate python modules required.

---

