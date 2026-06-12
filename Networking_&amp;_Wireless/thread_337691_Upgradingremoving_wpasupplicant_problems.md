---
title: "Upgrading/removing wpasupplicant problems"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by macozz on 2007-01-13
Hi,
Today I was prompted to upgrade wpasupplicant but trying to do ig gave an error. Now, trying to remove it is not possible, but it is locking the installation of any other package. This is what I have:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  wpasupplicant
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 692kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 106269 files and directories currently installed.)
Removing wpasupplicant ...
dpkg: error processing wpasupplicant (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 wpasupplicant
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any idea about how to proceed?

Thanks!

---

### Post by wmatlock on 2007-01-13
Did you use the following command?

sudo apt-get remove wpasuplicant

---

### Post by macozz on 2007-01-14
Yes I do. And this is what I get:

Removing wpasupplicant ...
dpkg: error processing wpasupplicant (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 wpasupplicant
E: Sub-process /usr/bin/dpkg returned an error code (1)

Actually, the problem started when the update manager ask to upgrade this package from version 0.5.5-3v1ubuntu4 to 0.5.7+3v1ubuntu1. Accepting the upgrade, synaptic complain that the new package lacks some script. Then I try to remove the old package, but that failed as shown.
Nobody experienced this before?
Thanks!

---

### Post by rfugger on 2007-01-15
I've been having the exact same problem.  The way I fixed it was to download the wpasupplicant 0.5.5-4 Debian package from:

[http://packages.debian.org/unstable/net/wpasupplicant](http://packages.debian.org/unstable/net/wpasupplicant)

And install it with the following command:

sudo dpkg -i --force-depends-version wpasupplicant_0.5.5-4_i386.deb

(The force-depends-version option is necessary because the Debian package depends on later versions of some other packages than Ubuntu installs.)

That seems to work, and then I remove wpasupplicant altogether with:

sudo dpkg -r wpasupplicant

If you don't need WPA functionality, I would just leave it at that.  I tried reinstalling the 0.5.7-3v1ubuntu1 package, and it worked, but gave the same problems again when trying to upgrade to 0.5.7-3v1ubuntu3 package today.  Maybe the ubuntu3 package fixes the problems, but I don't use WPA and I'm not about to find out.  Good luck.

Ryan

---

### Post by macozz on 2007-01-16
Thanks! That makes the trick! Thank you very much!

Mario

---

### Post by chamberlain2006 on 2007-01-16
thank you so much!  it was getting really annoying!

---

### Post by AntiFlash on 2007-01-21
thank you for the tip also :)

it's crazy how one little thing like this can throw a wrench into so many different things...

kf

---

### Post by tchoklat on 2007-01-21
i got this response;

tony@tony:/$ sudo dpkg -r wpasupplicant
dpkg: dependency problems prevent removal of wpasupplicant:
 ubuntu-minimal depends on wpasupplicant.
dpkg: error processing wpasupplicant (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 wpasupplicant


any thoughts?

---

