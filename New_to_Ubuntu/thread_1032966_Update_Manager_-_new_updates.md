---
title: "Update Manager - new updates"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by nickyn on 2009-01-06
I apparently have six new updates that should be installed, but when I run the Update Manager, and ask it to install the new updates, I get this error: 

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-2ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-2ubuntu5_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.3.9-2ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.3.9-2ubuntu5_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.3.9-2ubuntu5_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.3.9-2ubuntu5_all.deb)
  404 Not Found [IP: 91.189.88.45 80]

Then I hit close, and this notice comes up:

Not all updates can be installed
Run a partial upgrade, to install as many updates as possible.
This can be caused by :
A previous upgrade which didn't complete
Problems with some of the installed software
Unofficial software packages not provided by Ubuntu
Normal changes of a pre-release version of Ubuntu

From there I choose partial update and it asks:

Do you want to start the upgrade?
1 package is going to be removed.  3 new packages are going to be installed.  8 packages are going to be upgraded.
You have a download total of 3673k.  This download will take about 28 seconds with a 1Mbit DSL connection and about 8 minutes with a 56K modem
To prevent data loss close all open applications and documents.

Then I begin the upgrade, and within ten seconds, I get this error message:

Could not download the upgrades
The upgrade aborts now.  Please check your Internet connection or installation media and try again.  All files downloaded so far are kept.
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-2ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-2ubuntu5_i386.deb) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.3.9-2ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.3.9-2ubuntu5_i386.deb) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.3.9-2ubuntu5_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.3.9-2ubuntu5_all.deb) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.3.9-2ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.3.9-2ubuntu5_i386.deb) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.3.9-2ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.3.9-2ubuntu5_i386.deb) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.3.9-2ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.3.9-2ubuntu5_i386.deb) 404 Not Found [IP: 91.189.88.46 80]

I hit the close button, and it closes the upgrade.  I don't know what would be causing this error.  I also find that the Pidgin messenger freezes within five minutes of use.  I don't know, either, what would be causing that.  If anyone has any ideas on why this happened, or how to fix it, that would be awweesommme!
Thanks, Nicky.

---

### Post by tuxxy on 2009-01-06
Are you using a proxy by any chance?

---

### Post by nickyn on 2009-01-06
...I don't know what a proxy is.  So I'm guessing no.  :D

---

### Post by Michaelg14 on 2009-01-07
Make sure you have a working Internet connection when you are upgrading.

---

### Post by treesurf on 2009-01-07
I have this same problem occasionally because I am using the Hong Kong server for my upgrades.  The server will tell me that I need upgrades but doesn't actually have the packages for download until a day or two later than the main server.  You might try going to Administration>Software Sources and choosing a different download source from the "Download from" dropdown menu.

---

### Post by thegreatbitbucket on 2009-01-07
I checked some of those links, and it is giving me a 404 error. The server is up, but these packages don't exist. I would suggest ignoring it. It's probably nothing and it will resolve itself.

At least, that's what I'd do. :)

---

### Post by nickyn on 2009-01-08
Okay, so I checked the server I was on, and I was on the main server.  So I'm trying the Canada server, and it seems to be working a little better!  Thanks for that idea, treesurf.  I will keep you updated and let you know if it solves the problem.

---

