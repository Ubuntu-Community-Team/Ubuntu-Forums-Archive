---
title: "Webmin installation - Error"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by sujeewa on 2011-02-01
Dear All,

I just installed ubuntu 8.10 web server and try to install wenmin.

downloaded from the following command

wget [http://garr.dl.sourceforge.net/sourceforge/webadmin/webmin_1.441_all.deb](http://garr.dl.sourceforge.net/sourceforge/webadmin/webmin_1.441_all.deb)

downloaded correctly.

then i used below command for the installation

sudo dpkg -i webmin_1.441_all.deb

but below errors coming.

-----------------------------------------------------

Preparing to replace webmin 1.441 (using webmin_1.441_all.deb) ...
Unpacking replacement webmin ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on libio-pty-perl; however:
  Package libio-pty-perl is not installed.
 webmin depends on libmd5-perl; however:
  Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin

------------------------------------------

then i used below command


sudo aptitude install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl


then came below errors

--------------------------------------------------


Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
No candidate version found for libnet-ssleay-perl
No candidate version found for libauthen-pam-perl
No candidate version found for libio-pty-perl
No candidate version found for libmd5-perl
No candidate version found for libnet-ssleay-perl
No candidate version found for libauthen-pam-perl
No candidate version found for libio-pty-perl
No candidate version found for libmd5-perl
The following packages are BROKEN:
  webmin
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  webmin: Depends: libnet-ssleay-perl which is a virtual package.
          Depends: libauthen-pam-perl which is a virtual package.
          Depends: libio-pty-perl which is a virtual package.
          Depends: libmd5-perl which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
webmin

Score is 119


PLS HELP ME TO OVER COME THIS PROBLEM.

THANKS IN ADVANCE.

---

### Post by The Flash on 2011-02-01
I've run into similar problems. Correct me if I'm wrong...
Do you have Perl installed?
I don't know about the top, but the bottom error seems to be missing several perl packages.

*ADDITIONAL:*

Yes, after re-reading the post, it looks like perl is missing. try installing/re-installing perl.

---

