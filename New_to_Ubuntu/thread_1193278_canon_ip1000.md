---
title: "canon ip1000"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by ddg on 2009-06-21
Hallo every body,

I am using Ubuntu 8.04 with Canon printer Pixma IP 1000.
But I could not get the printer working. It was running well with ubuntu 7.10.
I tried all option available from the net.
I downloaded deb package and tried to install it but it always failed and it said that I have not installed libglib1.2 package. I can not install this package because the replacement package does not allow that to happen. The replacement package is something libglip...ldbl

I tried other option and that is by adding a line to a file. But I can not finished the steps.
Can some body help me please??

Rgds,
Ddg

---

### Post by LewRockwell on 2009-06-21
[http://ubuntuforums.org/showthread.php?t=468652](http://ubuntuforums.org/showthread.php?t=468652)

---

### Post by LewRockwell on 2009-06-21
[http://ubuntuforums.org/showthread.php?t=730598](http://ubuntuforums.org/showthread.php?t=730598)

---

### Post by ddg on 2009-06-21
> **LewRockwell said:**
> [http://ubuntuforums.org/showthread.php?t=468652](http://ubuntuforums.org/showthread.php?t=468652)

Hi,

I installed Ubuntu 8.04 (I think this is Hardy Heron) on Pentium III. No additional software or accessories. I could not installed the driver and that is the problem.

The printer is already detected from System--> Administration --> Printing but when I tried to print test page it says CUPS error.

I tried to follow the link you gave me but there is no driver in /usr/share/ppd/pstocanonbj.

I tried to download by using this command:
# apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj 

This is the output:
bjfilter-2.5 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pstocanonbj: Depends: libcupsys2-gnutls10 (>= 1.1.23-1) but it is not installable
E: Broken packages

And I could not find the package from Synaptic package manager.
I hope it is clear now. 

Thanks,
ddg

---

