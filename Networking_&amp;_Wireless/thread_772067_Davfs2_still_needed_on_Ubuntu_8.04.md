---
title: "Davfs2 still needed on Ubuntu 8.04 ?"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by pascal_s on 2008-04-28
Hello,

I want to access a sharepoint server via WebDAV from my Ubuntu 8.04 machine. I first tried to simply connect using “Connect to server…” and then the WebDAV option, but it fails (authorization fails). I search for support info on the forums, and found some old messages indicating that davfs2 should be used for WebDAV (I tried to install it, but it crashed...).

Question: is the installation of davfs2 still required? On 8.04, WebDAV seems to be a valid option on "Connect to server...". 

Thanks for any help

Pascal

---

### Post by bfisk on 2009-03-25
On my sharepoint server, I had to enable basic authentication under IIS and the sharepoint website which fixed my login problems.

To be able to copy to the sharepoint, overwrite files, etc:  login to your sharepoint site and go to your shared documents folder.  Go into document library settings, versioning settings, require documents to be checked out before they can be edited, and set to no.  When you overwrite files they will still be made as a new version.

One other note that I have not figured out yet is that mounting with davfs does not seem to support using spaces in a folder or file on the sharepoint server.  This is anoying because you want to go into the folder "shared documents" on your sharepoint server which doesnt show up.

---

