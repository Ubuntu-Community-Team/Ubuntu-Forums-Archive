---
title: "installArchives() failed: dpkg: error"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by bashishtha on 2011-08-02
I am geting following error when trying to install any software package through Ubuntu Software center. It was earlier working perfectly.
Following error message is received after download of package :
¨

installArchives() failed: dpkg: error: parsing file '/var/lib/dpkg/status' near line 34072 package 'ghostscript-cups': 
 duplicate value for `Package' field 

¨

Thanks,

bashishtha
Ubuntu 11.04

---

### Post by plucky on 2011-08-02
> **bashishtha said:**
> I am geting following error when trying to install any software package through Ubuntu Software center. It was earlier working perfectly.
Following error message is received after download of package :
¨

installArchives() failed: dpkg: error: parsing file '/var/lib/dpkg/status' near line 34072 package 'ghostscript-cups': 
 duplicate value for `Package' field 

Thanks,

bashishtha
Ubuntu 11.04


Welcome to the Forum.

You could try editing the file using ```
gksudo gedit /var/lib/dpkg/status
``` and going to line 34072 and seeing what is there.

**Post whatever is on line 34072**

It should look like ```
Package: ghostscript-cups
Status: install ok installed
Priority: optional
Section: text
Installed-Size: 176
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: ghostscript
Version: 8.71.dfsg.1-0ubuntu5.3
Depends: libc6 (>= 2.4), libcups2 (>= 1.4.0), libcupsimage2 (>= 1.4.0), libgnutls26 (>= 2.7.14-0), libgssapi-krb5-2 (>= 1.6.dfsg.2), libpaper1, zlib1g (>= 1:1.1.4), ghostscript (>= 8.64.dfsg.1-0ubuntu10), cups-client, cups
Conflicts: cups (<< 1.3.9-4), ghostscript (<< 8.64.dfsg.1-0ubuntu10)
Description: The GPL Ghostscript PostScript/PDF interpreter - CUPS filters
 Ghostscript is used for PostScript/PDF preview and printing.  Usually as
 a back-end to a program such as ghostview, it can display PostScript and PDF
 documents in an X11 environment.
 .
 This package contains the CUPS filters, drivers, and PPDs which come with
 Ghostscript. To not make Ghostscript itself requiring CUPS these files are
 in a separate package now.
Homepage: http://www.ghostscript.com/
Original-Maintainer: Masayuki Hatta (mhatta) <mhatta@debian.org>
```

Or you could run these commands

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.broken
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Then run ```
sudo apt-get update
``` to see if you still get the same error.

Good Luck

---

### Post by jtarin on 2011-08-02
[Fixing /var/lib/dpkg/status corruption]("http://thepcspy.com/read/fixing-dpkg-status-corruption/")

---

### Post by bashishtha on 2011-08-05
> **plucky said:**
> Welcome to the Forum.
 
You could try editing the file using ```
gksudo gedit /var/lib/dpkg/status
``` and going to line 34072 and seeing what is there.
 
**Post whatever is on line 34072**
 
It should look like ```
Package: ghostscript-cups
Status: install ok installed
Priority: optional
Section: text
Installed-Size: 176
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: ghostscript
Version: 8.71.dfsg.1-0ubuntu5.3
Depends: libc6 (>= 2.4), libcups2 (>= 1.4.0), libcupsimage2 (>= 1.4.0), libgnutls26 (>= 2.7.14-0), libgssapi-krb5-2 (>= 1.6.dfsg.2), libpaper1, zlib1g (>= 1:1.1.4), ghostscript (>= 8.64.dfsg.1-0ubuntu10), cups-client, cups
Conflicts: cups (<< 1.3.9-4), ghostscript (<< 8.64.dfsg.1-0ubuntu10)
Description: The GPL Ghostscript PostScript/PDF interpreter - CUPS filters
 Ghostscript is used for PostScript/PDF preview and printing.  Usually as
 a back-end to a program such as ghostview, it can display PostScript and PDF
 documents in an X11 environment.
 .
 This package contains the CUPS filters, drivers, and PPDs which come with
 Ghostscript. To not make Ghostscript itself requiring CUPS these files are
 in a separate package now.
Homepage: http://www.ghostscript.com/
Original-Maintainer: Masayuki Hatta (mhatta) <mhatta@debian.org>
```
 
Or you could run these commands
 
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.broken
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
```
 
Then run ```
sudo apt-get update
``` to see if you still get the same error.
 
Good Luck
I used following commands as suggested by you in terminal and after update of package list, I downloaded 7zip package to verify.

[COLOR=blue]sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.broken[/COLOR]
[COLOR=blue]sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status[/COLOR]
[COLOR=blue]sudo apt-get update[/COLOR]
 
This time, I got unhandlable error again. Then I ran following command to upgrade and got the success.
[COLOR=blue]sudo apt-get upgrade[/COLOR]
[COLOR=black]**Thanks.**[/COLOR]

---

