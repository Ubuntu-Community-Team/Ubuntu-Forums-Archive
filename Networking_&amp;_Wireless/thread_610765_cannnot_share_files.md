---
title: "cannnot share files"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by odindio on 2007-11-12
I tried to share files on a newer installation of Gutsy Gibbon.  But when I try to add a file to be shared, I get the following window

sharing services are not installed

you need to install at least either Samba or NFS in order to share your folders

X install unix neworks support (nfs)
x install windows network support (smb)

In this window - I click a button to install these but nothing installs, and the same window comes back up again repeatedly.  I checked in synaptic packet manager and smb was installed.  I decided to remove and reinstall it, but after removing it - it does not appear as an option to reinstall it.  An option to install unix networks support is not in synaptic manager.  Currenly samba common is installed.

how dow I fix this situation so I can share files?

---

### Post by reckless2k2 on 2007-11-12
yeah you need to install samba to share something on that machine with another. you will have to read up on samba sharing in general as well. you are setting up a samba server on your machine. the biggest hangup is that samba users and passwords are always forgotten to set up. server is "separate" from you machine. so if windows user "myuser" needs to access samba server on ubuntu, "myuser" and password needs to be setup on that server. if is independent from if "myuser" is setup on that ubuntu box. with linux, you can have 1 user on the physical box while having multiple "virtualish" users for server access. 

you getting me?

here are the official samba docs fro ubuntu:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by mpince on 2007-11-12
..

---

### Post by odindio on 2007-11-12
samba's not in synaptic packet manager, so I'm downloading it from samba.org.  The files called samba-3.0.26a.tar.gz and synaptic doesn't recognize it.  Whats the best way to go about installing this?

---

### Post by Peter09 on 2007-11-12
In Synaptic its smbclient  and smbfs that you will need to install.

---

### Post by odindio on 2007-11-12
there not listed in synaptic - that one of the problems.

---

