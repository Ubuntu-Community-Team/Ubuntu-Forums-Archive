---
title: "Could not download all repository indexes?"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by masayuki on 2009-04-08
I just installed linux a month ago.  I and i'm having problems updating "repositories."  I've read up on them, but i only have a basic understanding of how they work.

I have ubuntu 8.10 intrepid ibex



Anyway, i got this notification trying to configure WINE:



""The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue.""

So i pressed "reload" i assume to update.. and it gave me this error:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

-------------------------------------------------

I've been searching everywhere to find out how to fix this, and i'm not sure what's wrong.  Any help would be much appreciated.

Thanks,

Ian

---

### Post by Stupendoussteve on 2009-04-08
This should be an easy fix...

It is looking for packages on your CD rom. Assuming you want internet repos only, open up the Software Sources application (System> Administration> Software Sources) and uncheck the checkbox next to Cdrom with Ubuntu _______.

While in there, make sure the Downloadable From Internet repositories are checked, and download from has something in there (at least "Server for the United States", if you're in the USA).

---

### Post by masayuki on 2009-04-09
Heh, sweet.  It worked just as you said.  Thank you!

Linux OS is pretty cool.

Thanks again,

Ian


=)

---

