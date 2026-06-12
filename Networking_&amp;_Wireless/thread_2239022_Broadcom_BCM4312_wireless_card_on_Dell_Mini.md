---
title: "Broadcom BCM4312 wireless card on Dell Mini"
date: 2014-08-11
forum: Networking &amp; Wireless
---

### Post by stevesy on 2014-08-11
Hi, I recently reinstalled lubuntu 13.04 and cannot get wireless working. 

```
lspci -nn -d 14e4:
```

gives me

```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```

So the pci.id and revision version for driver installation are 

[14e4:4315] (rev 01)

Can you please advise me on where to go from here, thanks.

---

### Post by Jonathan Precise on 2014-08-11
I think it would receive better support in the "Networking and wireless" section. ask a mod or an admin to move your post.

---

### Post by stevesy on 2014-08-11
Will do Jonathan, thanks : ]

---

### Post by oldfred on 2014-08-11
Moved to Networking & Wireless.

---

### Post by stevesy on 2014-08-11
I've tried```
sudo apt-get install firmware-b43-installer
```

and got

```
steve@steve-Inspiron-910:~$ sudo apt-get install firmware-b43-installer
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  hyphen-en-us libaudio2 liblcms1 libmng1 libmysqlclient18 libqt4-dbus
  libqt4-declarative libqt4-network libqt4-script libqt4-sql libqt4-sql-mysql
  libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 mysql-common mythes-en-au
  openoffice.org-hyphenation qdbus qtchooser transmission-gtk
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.5 kB of archives.
After this operation, 111 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  b43-fwcutter firmware-b43-installer
Install these packages without verification [y/N]? y
Err [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring/main b43-fwcutter i386 1:015-14
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring/multiverse firmware-b43-installer all 1:015-14
  404  Not Found [IP: 193.1.193.69 80]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_015-14_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_015-14_i386.deb)  404  Not Found [IP: 193.1.193.69 80]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-installer_015-14_all.deb](http://ie.archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-installer_015-14_all.deb)  404  Not Found [IP: 193.1.193.69 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
steve@steve-Inspiron-910:~$ 

```

```
sudo apt-get update
``` gives

```
steve@steve-Inspiron-910:~$ sudo apt-get update
[sudo] password for steve: 
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring Release.gpg
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates Release.gpg
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports Release.gpg
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security Release.gpg
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring Release
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates Release
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports Release
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security Release
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/multiverse Sources/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/restricted Sources/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/universe Sources/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/main Sources/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/restricted i386 Packages/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/main i386 Packages/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/universe i386 Packages/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/multiverse i386 Packages/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/multiverse Sources/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/restricted Sources/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/universe Sources/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/main Sources/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/restricted i386 Packages/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/main i386 Packages/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/universe i386 Packages/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/multiverse i386 Packages/DiffIndex
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources
  404  Not Found
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/restricted Sources/DiffIndex
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages
  404  Not Found
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/universe Sources/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/multiverse Sources/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/main Sources/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/restricted i386 Packages/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/universe i386 Packages/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/multiverse i386 Packages/DiffIndex
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/main i386 Packages/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/main Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/main Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/multiverse Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/multiverse Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/restricted Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/restricted Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/universe Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/universe Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/main Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/main Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/multiverse Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/multiverse Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/restricted Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/restricted Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/universe Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/universe Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/main Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/main Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/multiverse Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/multiverse Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/restricted Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/restricted Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/universe Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/universe Translation-en
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/multiverse Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/restricted Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/universe Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/main Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/restricted i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/main i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/universe i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/multiverse i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/main Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/main Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/multiverse Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/multiverse Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/restricted Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/restricted Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/universe Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-security/universe Translation-en
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/multiverse Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/restricted Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/universe Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/main Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/restricted i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/main i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/universe i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring/multiverse i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/multiverse Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/restricted Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/universe Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/main Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/restricted i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/main i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/universe i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-updates/multiverse i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/restricted Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/universe Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/multiverse Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/main Sources
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/restricted i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/universe i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/multiverse i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) raring-backports/main i386 Packages
  404  Not Found [IP: 193.1.193.69 80]
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources](http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages](http://ie.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages)  404  Not Found [IP: 193.1.193.69 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
steve@steve-Inspiron-910:~$ 
```

and software updater says "Failed to download repository information..."


My sources.list file looks like this

```
# deb cdrom:[Lubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1)]/ raring main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring restricted main
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring multiverse restricted universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring-updates restricted main
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring-updates multiverse restricted universe main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring universe
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring-backports restricted universe multiverse main
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring-backports restricted universe multiverse main #Added by software-properties

deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring-security restricted main
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring-security multiverse restricted universe main #Added by software-properties
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring-security universe
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main

```
Please help!

---

### Post by chili555 on 2014-08-11
I suspect the repositories no longer work because: [http://fridge.ubuntu.com/2014/01/28/ubuntu-13-04-raring-ringtail-end-of-life-reached-on-january-27-2014/](http://fridge.ubuntu.com/2014/01/28/ubuntu-13-04-raring-ringtail-end-of-life-reached-on-january-27-2014/)> This is a follow-up to the End of Life warning sent last month to confirm that as of today (Jan 27, 2014), Ubuntu 13.04 is no longer supported. No more package updates will be accepted to 13.04, and it will be archived to old-releases.ubuntu.com in the coming weeks.I suggest you upgrade to 14.04.

---

### Post by stevesy on 2014-08-14
> **chili555 said:**
> I suspect the repositories no longer work because: [http://fridge.ubuntu.com/2014/01/28/ubuntu-13-04-raring-ringtail-end-of-life-reached-on-january-27-2014/](http://fridge.ubuntu.com/2014/01/28/ubuntu-13-04-raring-ringtail-end-of-life-reached-on-january-27-2014/)I suggest you upgrade to 14.04.

Ok chili555 I upgraded to 14.04 LTS using LinuxLive USB creator which worked nicely.  Based on the advise I found at [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43) I then did ```
sudo apt-get install firmware-b43-installer
```

and rebooted.

I now have a wlan0 interface icon on the taskbar with an exclamation mark, and it says  "Connection has limited or no connectivity".  I don't have the wireless connection icon i used to have, and cannot view available wireless networks.  I have been reading through a similar thread that you have posted in [http://ubuntuforums.org/showthread.php?t=2216887](http://ubuntuforums.org/showthread.php?t=2216887) and here are the results of
```
iwconfig
``` ```
rfkill list all
``` and ```
sudo iwlist wlan0 scan
```
```
steve@steve-Inspiron-910:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

steve@steve-Inspiron-910:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
steve@steve-Inspiron-910:~$ sudo iwlist wlan0 scan
[sudo] password for steve: 
wlan0     Scan completed :
          Cell 01 - Address: 4C:72:B9:85:7E:36
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000346a70399a
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 0009555043323536393939
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 4E:72:B9:85:7E:38
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000346a6e3d35
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000F486F72697A6F6E2057692D46726565
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 14:49:E0:AC:F9:E9
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000d6af4de
                    Extra: Last beacon: 220ms ago
                    IE: Unknown: 000F486F72697A6F6E2057692D46726565
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0103FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000017127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 07064E4C20010D10
          Cell 04 - Address: 14:49:E0:E0:46:98
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004e068aecb
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000C555043323435303034373632
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0103FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160B010400000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05050016127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706494520010D10
                    IE: Unknown: DDA70050F204104A0001101044000102103B00010310470010BC329E001DD811B286011449E0E046981021001A43656C656E6F20436F6D6D756E69636174696F6E2C20496E632E1023001743656C656E6F20576972656C65737320415020322E344710240006434C313830301042000831323334353637381054000800060050F20400011011000C43656C656E6F4150322E344710080002210C103C0001011049000600372A000120
          Cell 05 - Address: 14:49:E0:E0:46:99
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004ddabfd08
                    Extra: Last beacon: 260ms ago
                    IE: Unknown: 000F486F72697A6F6E2057692D46726565
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0103FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160B010400000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05050018127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706494520010D10
          Cell 06 - Address: 14:49:E0:AC:F9:E8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000022ee21aa
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000C555043323435333534363239
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0103FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000017127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 07064E4C20010D10
                    IE: Unknown: DDA70050F204104A0001101044000102103B00010310470010BC329E001DD811B286011449E0ACF9E81021001A43656C656E6F20436F6D6D756E69636174696F6E2C20496E632E1023001743656C656E6F20576972656C65737320415020322E344710240006434C313830301042000831323334353637381054000800060050F20400011011000C43656C656E6F4150322E344710080002210C103C0001011049000600372A000120
          Cell 07 - Address: 8E:04:FF:7A:B5:DD
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000039756bbef9
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000F486F72697A6F6E2057692D46726565
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD090010180200000C0000
                    IE: Unknown: DD180050F20201018C0003A4000027A4000042435E0062322F00
          Cell 08 - Address: 88:F7:C7:46:3B:64
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=16 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000111ded8f2
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000A55504332353238363138
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 8C:04:FF:7A:B5:DB
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000039756bb5cb
                    Extra: Last beacon: 44ms ago

```
The following did not resolve the missing network manager icon [http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

```
ps aux | grep network-manager
```
```
steve@steve-Inspiron-910:~$ ps aux | grep network-manager
root      1110  0.0  0.3   5516  3092 ?        S    17:21   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /run/sendsigs.omit.d/network-manager.dhclient-eth0.pid -lf /var/lib/NetworkManager/dhclient-73bd7f44-2df0-4d3f-98cd-493d450bed56-eth0.lease -cf /var/lib/NetworkManager/dhclient-eth0.conf eth0
nobody    1114  0.0  0.1   6772  1436 ?        S    17:22   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
steve     1936  0.0  0.0   5908   840 pts/0    S+   18:15   0:00 grep --color=auto network-manager
```

```
sudo service network-manager start
```

```
steve@steve-Inspiron-910:~$ sudo service network-manager start
start: Job is already running: network-manager
```

```
lsmod | grep -e wl -e b43
```

```
steve@steve-Inspiron-910:~$ lsmod | grep -e wl -e b43
b43                   356470  0 
bcma                   42043  1 b43
mac80211              545990  1 b43
cfg80211              409394  2 b43,mac80211
ssb                    51854  1 b43
```

```
dmesg | grep -e wl -e b43
```

```
steve@steve-Inspiron-910:~$ dmesg | grep -e wl -e b43
[    9.979473] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   10.139292] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   14.232291] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   19.793632] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.794778] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```
Please advise, thank you.

---

### Post by Hadaka on 2014-08-14
from a wired connection connected to the internet please do.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-firmware-nonfree
sudo modprobe -rf b43
sudo modprobe b43
```

---

### Post by stevesy on 2014-08-14
> **Hadaka said:**
> from a wired connection connected to the internet please do.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-firmware-nonfree
sudo modprobe -rf b43
sudo modprobe b43
```

```
sudo apt-get update
```


```
steve@steve-Inspiron-910:~$ sudo apt-get update
[sudo] password for steve: 
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty InRelease
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-updates InRelease                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                  
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-backports InRelease
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease  
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-updates Release.gpg                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-backports Release.gpg
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-security Release.gpg
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [59.7 kB]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty Release                                
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-updates Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release              
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-backports Release                      
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-security Release                       
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/restricted Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/main Sources                   
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/restricted i386 Packages       
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/main i386 Packages             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                       
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/universe i386 Packages         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                 
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/multiverse i386 Packages         
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [39.0 kB]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/main Translation-en                   
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/restricted Translation-en              
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]     
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/universe Translation-en                
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [11.3 kB]    
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-updates/multiverse Sources             
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [699 B]    
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-updates/universe Sources               
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [123 kB]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-updates/main Sources          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-updates/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-updates/multiverse i386 Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-updates/main Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [45.4 kB]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1,398 B]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-updates/universe Translation-en      
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [61.6 kB]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en 
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-backports/main Sources         
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-backports/restricted i386 Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-backports/universe i386 Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-backports/main i386 Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-backports/universe Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-security/multiverse Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-security/restricted Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-security/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-security/main Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-security/restricted i386 Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-security/main i386 Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-security/universe i386 Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-security/multiverse i386 Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-security/main Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty-security/universe Translation-en
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) trusty/universe Translation-en_US
Fetched 343 kB in 1s (182 kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) trusty/restricted i386 Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) trusty-updates/main i386 Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) trusty-updates/restricted i386 Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) trusty-backports/main i386 Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) trusty-backports/restricted i386 Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) trusty-backports/universe i386 Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) trusty-backports/multiverse i386 Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
steve@steve-Inspiron-910:~$ 

```
```
sudo apt-get upgrade
```  A lot of output for this one, couldn't copy the start of it by the time it finished, sorry..

```
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Setting up bash (4.3-7ubuntu1) ...
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode
(Reading database ... 105635 files and directories currently installed.)
Preparing to unpack .../dpkg_1.17.5ubuntu5.3_i386.deb ...
Unpacking dpkg (1.17.5ubuntu5.3) over (1.17.5ubuntu5) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up dpkg (1.17.5ubuntu5.3) ...
(Reading database ... 105635 files and directories currently installed.)
Preparing to unpack .../mount_2.20.1-5.1ubuntu20.1_i386.deb ...
Unpacking mount (2.20.1-5.1ubuntu20.1) over (2.20.1-5.1ubuntu20) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up mount (2.20.1-5.1ubuntu20.1) ...
(Reading database ... 105635 files and directories currently installed.)
Preparing to unpack .../tzdata_2014e-0ubuntu0.14.04_all.deb ...
Unpacking tzdata (2014e-0ubuntu0.14.04) over (2014b-1) ...
Setting up tzdata (2014e-0ubuntu0.14.04) ...

Current default time zone: 'Europe/Dublin'
Local time is now:      Thu Aug 14 19:00:46 IST 2014.
Universal Time is now:  Thu Aug 14 18:00:46 UTC 2014.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

(Reading database ... 105635 files and directories currently installed.)
Preparing to unpack .../util-linux_2.20.1-5.1ubuntu20.1_i386.deb ...
Unpacking util-linux (2.20.1-5.1ubuntu20.1) over (2.20.1-5.1ubuntu20) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up util-linux (2.20.1-5.1ubuntu20.1) ...
(Reading database ... 105635 files and directories currently installed.)
Preparing to unpack .../libdbus-1-3_1.6.18-0ubuntu4.1_i386.deb ...
Unpacking libdbus-1-3:i386 (1.6.18-0ubuntu4.1) over (1.6.18-0ubuntu4) ...
Preparing to unpack .../libjson-c2_0.11-3ubuntu1.2_i386.deb ...
Unpacking libjson-c2:i386 (0.11-3ubuntu1.2) over (0.11-3ubuntu1) ...
Preparing to unpack .../libselinux1_2.2.2-1ubuntu0.1_i386.deb ...
Unpacking libselinux1:i386 (2.2.2-1ubuntu0.1) over (2.2.2-1) ...
Preparing to unpack .../libc6_2.19-0ubuntu6.1_i386.deb ...
Unpacking libc6:i386 (2.19-0ubuntu6.1) over (2.19-0ubuntu6) ...
Setting up libc6:i386 (2.19-0ubuntu6.1) ...
Setting up libselinux1:i386 (2.2.2-1ubuntu0.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
(Reading database ... 105635 files and directories currently installed.)
Preparing to unpack .../libuuid1_2.20.1-5.1ubuntu20.1_i386.deb ...
Unpacking libuuid1:i386 (2.20.1-5.1ubuntu20.1) over (2.20.1-5.1ubuntu20) ...
Setting up libuuid1:i386 (2.20.1-5.1ubuntu20.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
(Reading database ... 105635 files and directories currently installed.)
Preparing to unpack .../libblkid1_2.20.1-5.1ubuntu20.1_i386.deb ...
Unpacking libblkid1:i386 (2.20.1-5.1ubuntu20.1) over (2.20.1-5.1ubuntu20) ...
Setting up libblkid1:i386 (2.20.1-5.1ubuntu20.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
(Reading database ... 105635 files and directories currently installed.)
Preparing to unpack .../libcgmanager0_0.24-0ubuntu7_i386.deb ...
Unpacking libcgmanager0:i386 (0.24-0ubuntu7) over (0.24-0ubuntu5) ...
Preparing to unpack .../udev_204-5ubuntu20.3_i386.deb ...
Adding 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
Unpacking udev (204-5ubuntu20.3) over (204-5ubuntu20) ...
Preparing to unpack .../libudev1_204-5ubuntu20.3_i386.deb ...
Unpacking libudev1:i386 (204-5ubuntu20.3) over (204-5ubuntu20) ...
Preparing to unpack .../ifupdown_0.7.47.2ubuntu4.1_i386.deb ...
Unpacking ifupdown (0.7.47.2ubuntu4.1) over (0.7.47.2ubuntu4) ...
Preparing to unpack .../libjson0_0.11-3ubuntu1.2_i386.deb ...
Unpacking libjson0:i386 (0.11-3ubuntu1.2) over (0.11-3ubuntu1) ...
Preparing to unpack .../upstart_1.12.1-0ubuntu4.2_i386.deb ...
Unpacking upstart (1.12.1-0ubuntu4.2) over (1.12.1-0ubuntu4) ...
Preparing to unpack .../libc-bin_2.19-0ubuntu6.1_i386.deb ...
Unpacking libc-bin (2.19-0ubuntu6.1) over (2.19-0ubuntu6) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up libc-bin (2.19-0ubuntu6.1) ...
(Reading database ... 105636 files and directories currently installed.)
Preparing to unpack .../libapt-pkg4.12_1.0.1ubuntu2.1_i386.deb ...
Unpacking libapt-pkg4.12:i386 (1.0.1ubuntu2.1) over (1.0.1ubuntu2) ...
Setting up libapt-pkg4.12:i386 (1.0.1ubuntu2.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.1) ...
(Reading database ... 105636 files and directories currently installed.)
Preparing to unpack .../gpgv_1.4.16-1ubuntu2.1_i386.deb ...
Unpacking gpgv (1.4.16-1ubuntu2.1) over (1.4.16-1ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up gpgv (1.4.16-1ubuntu2.1) ...
(Reading database ... 105636 files and directories currently installed.)
Preparing to unpack .../gnupg_1.4.16-1ubuntu2.1_i386.deb ...
Unpacking gnupg (1.4.16-1ubuntu2.1) over (1.4.16-1ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Setting up gnupg (1.4.16-1ubuntu2.1) ...
(Reading database ... 105636 files and directories currently installed.)
Preparing to unpack .../apt_1.0.1ubuntu2.1_i386.deb ...
Unpacking apt (1.0.1ubuntu2.1) over (1.0.1ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up apt (1.0.1ubuntu2.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.1) ...
(Reading database ... 105636 files and directories currently installed.)
Preparing to unpack .../bsdutils_1%3a2.20.1-5.1ubuntu20.1_i386.deb ...
Unpacking bsdutils (1:2.20.1-5.1ubuntu20.1) over (1:2.20.1-5.1ubuntu20) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up bsdutils (1:2.20.1-5.1ubuntu20.1) ...
(Reading database ... 105636 files and directories currently installed.)
Preparing to unpack .../libmount1_2.20.1-5.1ubuntu20.1_i386.deb ...
Unpacking libmount1:i386 (2.20.1-5.1ubuntu20.1) over (2.20.1-5.1ubuntu20) ...
Setting up libmount1:i386 (2.20.1-5.1ubuntu20.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.1) ...
(Reading database ... 105636 files and directories currently installed.)
Preparing to unpack .../libapt-inst1.5_1.0.1ubuntu2.1_i386.deb ...
Unpacking libapt-inst1.5:i386 (1.0.1ubuntu2.1) over (1.0.1ubuntu2) ...
Preparing to unpack .../libtasn1-6_3.4-3ubuntu0.1_i386.deb ...
Unpacking libtasn1-6:i386 (3.4-3ubuntu0.1) over (3.4-3) ...
Preparing to unpack .../libgnutls-openssl27_2.12.23-12ubuntu2.1_i386.deb ...
Unpacking libgnutls-openssl27:i386 (2.12.23-12ubuntu2.1) over (2.12.23-12ubuntu2) ...
Preparing to unpack .../libgnutls26_2.12.23-12ubuntu2.1_i386.deb ...
Unpacking libgnutls26:i386 (2.12.23-12ubuntu2.1) over (2.12.23-12ubuntu2) ...
Preparing to unpack .../file_1%3a5.14-2ubuntu3.1_i386.deb ...
Unpacking file (1:5.14-2ubuntu3.1) over (1:5.14-2ubuntu3) ...
Preparing to unpack .../libmagic1_1%3a5.14-2ubuntu3.1_i386.deb ...
Unpacking libmagic1:i386 (1:5.14-2ubuntu3.1) over (1:5.14-2ubuntu3) ...
Preparing to unpack .../libssl1.0.0_1.0.1f-1ubuntu2.5_i386.deb ...
Unpacking libssl1.0.0:i386 (1.0.1f-1ubuntu2.5) over (1.0.1f-1ubuntu2) ...
Preparing to unpack .../resolvconf_1.69ubuntu1.1_all.deb ...
Unpacking resolvconf (1.69ubuntu1.1) over (1.69ubuntu1) ...
Preparing to unpack .../libgirepository-1.0-1_1.40.0-1ubuntu0.1_i386.deb ...
Unpacking libgirepository-1.0-1 (1.40.0-1ubuntu0.1) over (1.40.0-1) ...
Preparing to unpack .../gir1.2-freedesktop_1.40.0-1ubuntu0.1_i386.deb ...
Unpacking gir1.2-freedesktop (1.40.0-1ubuntu0.1) over (1.40.0-1) ...
Preparing to unpack .../gir1.2-glib-2.0_1.40.0-1ubuntu0.1_i386.deb ...
Unpacking gir1.2-glib-2.0 (1.40.0-1ubuntu0.1) over (1.40.0-1) ...
Preparing to unpack .../python3-gi_3.12.0-1ubuntu1_i386.deb ...
Unpacking python3-gi (3.12.0-1ubuntu1) over (3.12.0-1) ...
Preparing to unpack .../libgtk-3-common_3.10.8-0ubuntu1.2_all.deb ...
Unpacking libgtk-3-common (3.10.8-0ubuntu1.2) over (3.10.8-0ubuntu1) ...
Preparing to unpack .../libgail-3-0_3.10.8-0ubuntu1.2_i386.deb ...
Unpacking libgail-3-0:i386 (3.10.8-0ubuntu1.2) over (3.10.8-0ubuntu1) ...
Preparing to unpack .../libcupsppdc1_1.7.2-0ubuntu1.1_i386.deb ...
Unpacking libcupsppdc1:i386 (1.7.2-0ubuntu1.1) over (1.7.2-0ubuntu1) ...
Preparing to unpack .../libcupsmime1_1.7.2-0ubuntu1.1_i386.deb ...
Unpacking libcupsmime1:i386 (1.7.2-0ubuntu1.1) over (1.7.2-0ubuntu1) ...
Preparing to unpack .../libjbig0_2.0-2ubuntu4.1_i386.deb ...
Unpacking libjbig0:i386 (2.0-2ubuntu4.1) over (2.0-2ubuntu4) ...
Preparing to unpack .../libtiff5_4.0.3-7ubuntu0.1_i386.deb ...
Unpacking libtiff5:i386 (4.0.3-7ubuntu0.1) over (4.0.3-7) ...
Preparing to unpack .../libcupsfilters1_1.0.52-0ubuntu1.2_i386.deb ...
Unpacking libcupsfilters1:i386 (1.0.52-0ubuntu1.2) over (1.0.52-0ubuntu1) ...
Preparing to unpack .../libcupsimage2_1.7.2-0ubuntu1.1_i386.deb ...
Unpacking libcupsimage2:i386 (1.7.2-0ubuntu1.1) over (1.7.2-0ubuntu1) ...
Preparing to unpack .../libcupscgi1_1.7.2-0ubuntu1.1_i386.deb ...
Unpacking libcupscgi1:i386 (1.7.2-0ubuntu1.1) over (1.7.2-0ubuntu1) ...
Preparing to unpack .../libk5crypto3_1.12+dfsg-2ubuntu4.2_i386.deb ...
Unpacking libk5crypto3:i386 (1.12+dfsg-2ubuntu4.2) over (1.12+dfsg-2ubuntu4) ...
Preparing to unpack .../libgssapi-krb5-2_1.12+dfsg-2ubuntu4.2_i386.deb ...
Unpacking libgssapi-krb5-2:i386 (1.12+dfsg-2ubuntu4.2) over (1.12+dfsg-2ubuntu4) ...
Preparing to unpack .../libkrb5-3_1.12+dfsg-2ubuntu4.2_i386.deb ...
Unpacking libkrb5-3:i386 (1.12+dfsg-2ubuntu4.2) over (1.12+dfsg-2ubuntu4) ...
Preparing to unpack .../libkrb5support0_1.12+dfsg-2ubuntu4.2_i386.deb ...
Unpacking libkrb5support0:i386 (1.12+dfsg-2ubuntu4.2) over (1.12+dfsg-2ubuntu4) ...
Preparing to unpack .../cups-daemon_1.7.2-0ubuntu1.1_i386.deb ...
cups stop/waiting
Unpacking cups-daemon (1.7.2-0ubuntu1.1) over (1.7.2-0ubuntu1) ...
Preparing to unpack .../cups-filters-core-drivers_1.0.52-0ubuntu1.2_i386.deb ...
Unpacking cups-filters-core-drivers (1.0.52-0ubuntu1.2) over (1.0.52-0ubuntu1) ...
Preparing to unpack .../cups-core-drivers_1.7.2-0ubuntu1.1_i386.deb ...
Unpacking cups-core-drivers (1.7.2-0ubuntu1.1) over (1.7.2-0ubuntu1) ...
Preparing to unpack .../cups-server-common_1.7.2-0ubuntu1.1_all.deb ...
Unpacking cups-server-common (1.7.2-0ubuntu1.1) over (1.7.2-0ubuntu1) ...
Preparing to unpack .../ghostscript_9.10~dfsg-0ubuntu10.2_i386.deb ...
Unpacking ghostscript (9.10~dfsg-0ubuntu10.2) over (9.10~dfsg-0ubuntu10) ...
Preparing to unpack .../ghostscript-x_9.10~dfsg-0ubuntu10.2_i386.deb ...
Unpacking ghostscript-x (9.10~dfsg-0ubuntu10.2) over (9.10~dfsg-0ubuntu10) ...
Preparing to unpack .../libfontconfig1_2.11.0-0ubuntu4.1_i386.deb ...
Unpacking libfontconfig1:i386 (2.11.0-0ubuntu4.1) over (2.11.0-0ubuntu4) ...
Preparing to unpack .../fontconfig-config_2.11.0-0ubuntu4.1_all.deb ...
Unpacking fontconfig-config (2.11.0-0ubuntu4.1) over (2.11.0-0ubuntu4) ...
Preparing to unpack .../libfreetype6_2.5.2-1ubuntu2.2_i386.deb ...
Unpacking libfreetype6:i386 (2.5.2-1ubuntu2.2) over (2.5.2-1ubuntu2) ...
Preparing to unpack .../libgs9-common_9.10~dfsg-0ubuntu10.2_all.deb ...
Unpacking libgs9-common (9.10~dfsg-0ubuntu10.2) over (9.10~dfsg-0ubuntu10) ...
Preparing to unpack .../libgs9_9.10~dfsg-0ubuntu10.2_i386.deb ...
Unpacking libgs9 (9.10~dfsg-0ubuntu10.2) over (9.10~dfsg-0ubuntu10) ...
Preparing to unpack .../cups-client_1.7.2-0ubuntu1.1_i386.deb ...
Unpacking cups-client (1.7.2-0ubuntu1.1) over (1.7.2-0ubuntu1) ...
Preparing to unpack .../libcups2_1.7.2-0ubuntu1.1_i386.deb ...
Unpacking libcups2:i386 (1.7.2-0ubuntu1.1) over (1.7.2-0ubuntu1) ...
Preparing to unpack .../cups_1.7.2-0ubuntu1.1_i386.deb ...
Unpacking cups (1.7.2-0ubuntu1.1) over (1.7.2-0ubuntu1) ...
Preparing to unpack .../cups-filters_1.0.52-0ubuntu1.2_i386.deb ...
Unpacking cups-filters (1.0.52-0ubuntu1.2) over (1.0.52-0ubuntu1) ...
Preparing to unpack .../cups-ppdc_1.7.2-0ubuntu1.1_i386.deb ...
Unpacking cups-ppdc (1.7.2-0ubuntu1.1) over (1.7.2-0ubuntu1) ...
Preparing to unpack .../libfontembed1_1.0.52-0ubuntu1.2_i386.deb ...
Unpacking libfontembed1:i386 (1.0.52-0ubuntu1.2) over (1.0.52-0ubuntu1) ...
Preparing to unpack .../cups-common_1.7.2-0ubuntu1.1_all.deb ...
Unpacking cups-common (1.7.2-0ubuntu1.1) over (1.7.2-0ubuntu1) ...
Preparing to unpack .../libgtk-3-0_3.10.8-0ubuntu1.2_i386.deb ...
Unpacking libgtk-3-0:i386 (3.10.8-0ubuntu1.2) over (3.10.8-0ubuntu1) ...
Preparing to unpack .../gir1.2-gtk-3.0_3.10.8-0ubuntu1.2_i386.deb ...
Unpacking gir1.2-gtk-3.0 (3.10.8-0ubuntu1.2) over (3.10.8-0ubuntu1) ...
Preparing to unpack .../libasprintf0c2_0.18.3.1-1ubuntu3_i386.deb ...
Unpacking libasprintf0c2:i386 (0.18.3.1-1ubuntu3) over (0.18.3.1-1ubuntu2) ...
Preparing to unpack .../gettext-base_0.18.3.1-1ubuntu3_i386.deb ...
Unpacking gettext-base (0.18.3.1-1ubuntu3) over (0.18.3.1-1ubuntu2) ...
Preparing to unpack .../im-config_0.24-1ubuntu4.1_all.deb ...
Unpacking im-config (0.24-1ubuntu4.1) over (0.24-1ubuntu4) ...
Preparing to unpack .../language-selector-gnome_0.129.2_all.deb ...
Unpacking language-selector-gnome (0.129.2) over (0.129) ...
Preparing to unpack .../libsystemd-login0_204-5ubuntu20.3_i386.deb ...
Unpacking libsystemd-login0:i386 (204-5ubuntu20.3) over (204-5ubuntu20) ...
Preparing to unpack .../dbus_1.6.18-0ubuntu4.1_i386.deb ...
Unpacking dbus (1.6.18-0ubuntu4.1) over (1.6.18-0ubuntu4) ...
Preparing to unpack .../accountsservice_0.6.35-0ubuntu7.1_i386.deb ...
Unpacking accountsservice (0.6.35-0ubuntu7.1) over (0.6.35-0ubuntu7) ...
Preparing to unpack .../libaccountsservice0_0.6.35-0ubuntu7.1_i386.deb ...
Unpacking libaccountsservice0:i386 (0.6.35-0ubuntu7.1) over (0.6.35-0ubuntu7) ...
Preparing to unpack .../language-selector-common_0.129.2_all.deb ...
Unpacking language-selector-common (0.129.2) over (0.129) ...
Preparing to unpack .../libelf1_0.158-0ubuntu5.1_i386.deb ...
Unpacking libelf1:i386 (0.158-0ubuntu5.1) over (0.158-0ubuntu5) ...
Preparing to unpack .../libpam-systemd_204-5ubuntu20.3_i386.deb ...
systemd-logind stop/waiting
Unpacking libpam-systemd:i386 (204-5ubuntu20.3) over (204-5ubuntu20) ...
Preparing to unpack .../systemd-services_204-5ubuntu20.3_i386.deb ...
Unpacking systemd-services (204-5ubuntu20.3) over (204-5ubuntu20) ...
Preparing to unpack .../libsystemd-daemon0_204-5ubuntu20.3_i386.deb ...
Unpacking libsystemd-daemon0:i386 (204-5ubuntu20.3) over (204-5ubuntu20) ...
Preparing to unpack .../libxml2_2.9.1+dfsg1-3ubuntu4.3_i386.deb ...
Unpacking libxml2:i386 (2.9.1+dfsg1-3ubuntu4.3) over (2.9.1+dfsg1-3ubuntu4) ...
Preparing to unpack .../libnspr4_2%3a4.10.2-1ubuntu1.1_i386.deb ...
Unpacking libnspr4:i386 (2:4.10.2-1ubuntu1.1) over (2:4.10.2-1ubuntu1) ...
Preparing to unpack .../libcamel-1.2-45_3.10.4-0ubuntu1.1_i386.deb ...
Unpacking libcamel-1.2-45 (3.10.4-0ubuntu1.1) over (3.10.4-0ubuntu1) ...
Preparing to unpack .../evolution-data-server-common_3.10.4-0ubuntu1.1_all.deb ...
Unpacking evolution-data-server-common (3.10.4-0ubuntu1.1) over (3.10.4-0ubuntu1) ...
Preparing to unpack .../libedataserver-1.2-18_3.10.4-0ubuntu1.1_i386.deb ...
Unpacking libedataserver-1.2-18 (3.10.4-0ubuntu1.1) over (3.10.4-0ubuntu1) ...
Preparing to unpack .../libebook-contacts-1.2-0_3.10.4-0ubuntu1.1_i386.deb ...
Unpacking libebook-contacts-1.2-0 (3.10.4-0ubuntu1.1) over (3.10.4-0ubuntu1) ...
Preparing to unpack .../libabiword-3.0_3.0.0-4ubuntu1.1_i386.deb ...
Unpacking libabiword-3.0:i386 (3.0.0-4ubuntu1.1) over (3.0.0-4ubuntu1) ...
Preparing to unpack .../libavutil52_6%3a9.16-0ubuntu0.14.04.1_i386.deb ...
Unpacking libavutil52:i386 (6:9.16-0ubuntu0.14.04.1) over (6:9.11-2ubuntu2) ...
Preparing to unpack .../libavcodec54_6%3a9.16-0ubuntu0.14.04.1_i386.deb ...
Unpacking libavcodec54:i386 (6:9.16-0ubuntu0.14.04.1) over (6:9.11-2ubuntu2) ...
Preparing to unpack .../libavformat54_6%3a9.16-0ubuntu0.14.04.1_i386.deb ...
Unpacking libavformat54:i386 (6:9.16-0ubuntu0.14.04.1) over (6:9.11-2ubuntu2) ...
Preparing to unpack .../libavresample1_6%3a9.16-0ubuntu0.14.04.1_i386.deb ...
Unpacking libavresample1:i386 (6:9.16-0ubuntu0.14.04.1) over (6:9.11-2ubuntu2) ...
Preparing to unpack .../gir1.2-dbusmenu-glib-0.4_12.10.3+14.04.20140612-0ubuntu1_i386.deb ...
Unpacking gir1.2-dbusmenu-glib-0.4 (12.10.3+14.04.20140612-0ubuntu1) over (12.10.3+14.04.20140319-0ubuntu1) ...
Preparing to unpack .../libdbusmenu-glib4_12.10.3+14.04.20140612-0ubuntu1_i386.deb ...
Unpacking libdbusmenu-glib4:i386 (12.10.3+14.04.20140612-0ubuntu1) over (12.10.3+14.04.20140319-0ubuntu1) ...
Preparing to unpack .../libdbusmenu-gtk3-4_12.10.3+14.04.20140612-0ubuntu1_i386.deb ...
Unpacking libdbusmenu-gtk3-4:i386 (12.10.3+14.04.20140612-0ubuntu1) over (12.10.3+14.04.20140319-0ubuntu1) ...
Preparing to unpack .../libdbusmenu-gtk4_12.10.3+14.04.20140612-0ubuntu1_i386.deb ...
Unpacking libdbusmenu-gtk4:i386 (12.10.3+14.04.20140612-0ubuntu1) over (12.10.3+14.04.20140319-0ubuntu1) ...
Preparing to unpack .../libdebian-installer4_0.88ubuntu5_i386.deb ...
Unpacking libdebian-installer4:i386 (0.88ubuntu5) over (0.88ubuntu4) ...
Preparing to unpack .../libgl1-mesa-dri_10.1.3-0ubuntu0.1_i386.deb ...
Unpacking libgl1-mesa-dri:i386 (10.1.3-0ubuntu0.1) over (10.1.0-4ubuntu5) ...
Preparing to unpack .../libgbm1_10.1.3-0ubuntu0.1_i386.deb ...
Unpacking libgbm1:i386 (10.1.3-0ubuntu0.1) over (10.1.0-4ubuntu5) ...
Preparing to unpack .../libgl1-mesa-glx_10.1.3-0ubuntu0.1_i386.deb ...
Unpacking libgl1-mesa-glx:i386 (10.1.3-0ubuntu0.1) over (10.1.0-4ubuntu5) ...
Preparing to unpack .../libwayland-egl1-mesa_10.1.3-0ubuntu0.1_i386.deb ...
Unpacking libwayland-egl1-mesa:i386 (10.1.3-0ubuntu0.1) over (10.1.0-4ubuntu5) ...
Preparing to unpack .../libegl1-mesa-drivers_10.1.3-0ubuntu0.1_i386.deb ...
Unpacking libegl1-mesa-drivers:i386 (10.1.3-0ubuntu0.1) over (10.1.0-4ubuntu5) ...
Preparing to unpack .../libglapi-mesa_10.1.3-0ubuntu0.1_i386.deb ...
Unpacking libglapi-mesa:i386 (10.1.3-0ubuntu0.1) over (10.1.0-4ubuntu5) ...
Preparing to unpack .../libopenvg1-mesa_10.1.3-0ubuntu0.1_i386.deb ...
Unpacking libopenvg1-mesa:i386 (10.1.3-0ubuntu0.1) over (10.1.0-4ubuntu5) ...
Preparing to unpack .../libegl1-mesa_10.1.3-0ubuntu0.1_i386.deb ...
Unpacking libegl1-mesa:i386 (10.1.3-0ubuntu0.1) over (10.1.0-4ubuntu5) ...
Preparing to unpack .../libgpgme11_1.4.3-0.1ubuntu5.1_i386.deb ...
Unpacking libgpgme11:i386 (1.4.3-0.1ubuntu5.1) over (1.4.3-0.1ubuntu5) ...
Preparing to unpack .../libgphoto2-port10_2.5.3.1-1ubuntu2.2_i386.deb ...
Unpacking libgphoto2-port10:i386 (2.5.3.1-1ubuntu2.2) over (2.5.3.1-1ubuntu2) ...
Preparing to unpack .../libgphoto2-6_2.5.3.1-1ubuntu2.2_i386.deb ...
Unpacking libgphoto2-6:i386 (2.5.3.1-1ubuntu2.2) over (2.5.3.1-1ubuntu2) ...
Preparing to unpack .../libgstreamer1.0-0_1.2.4-0ubuntu1_i386.deb ...
Unpacking libgstreamer1.0-0:i386 (1.2.4-0ubuntu1) over (1.2.3-1) ...
Preparing to unpack .../libgstreamer-plugins-base1.0-0_1.2.4-1~ubuntu1_i386.deb ...
Unpacking libgstreamer-plugins-base1.0-0:i386 (1.2.4-1~ubuntu1) over (1.2.3-1) ...
Preparing to unpack .../libgtk2.0-common_2.24.23-0ubuntu1.1_all.deb ...
Unpacking libgtk2.0-common (2.24.23-0ubuntu1.1) over (2.24.23-0ubuntu1) ...
Preparing to unpack .../gtk2-engines-pixbuf_2.24.23-0ubuntu1.1_i386.deb ...
Unpacking gtk2-engines-pixbuf:i386 (2.24.23-0ubuntu1.1) over (2.24.23-0ubuntu1) ...
Preparing to unpack .../libgtk2.0-0_2.24.23-0ubuntu1.1_i386.deb ...
Unpacking libgtk2.0-0:i386 (2.24.23-0ubuntu1.1) over (2.24.23-0ubuntu1) ...
Preparing to unpack .../libgudev-1.0-0_1%3a204-5ubuntu20.3_i386.deb ...
Unpacking libgudev-1.0-0:i386 (1:204-5ubuntu20.3) over (1:204-5ubuntu20) ...
Preparing to unpack .../libido3-0.1-0_13.10.0+14.04.20140423-0ubuntu1_i386.deb ...
Unpacking libido3-0.1-0:i386 (13.10.0+14.04.20140423-0ubuntu1) over (13.10.0+14.04.20140407-0ubuntu1) ...
Preparing to unpack .../libwebkitgtk-3.0-common_2.4.3-1ubuntu2_all.deb ...
Unpacking libwebkitgtk-3.0-common (2.4.3-1ubuntu2) over (2.4.0-1ubuntu2) ...
Preparing to unpack .../libwebkitgtk-3.0-0_2.4.3-1ubuntu2_i386.deb ...
Unpacking libwebkitgtk-3.0-0:i386 (2.4.3-1ubuntu2) over (2.4.0-1ubuntu2) ...
Preparing to unpack .../libjavascriptcoregtk-3.0-0_2.4.3-1ubuntu2_i386.deb ...
Unpacking libjavascriptcoregtk-3.0-0:i386 (2.4.3-1ubuntu2) over (2.4.0-1ubuntu2) ...
Preparing to unpack .../liblzo2-2_2.06-1.2ubuntu1.1_i386.deb ...
Unpacking liblzo2-2:i386 (2.06-1.2ubuntu1.1) over (2.06-1.2ubuntu1) ...
Preparing to unpack .../libsane_1.0.23-3ubuntu3.1_i386.deb ...
Unpacking libsane:i386 (1.0.23-3ubuntu3.1) over (1.0.23-3ubuntu3) ...
Preparing to unpack .../libsane-common_1.0.23-3ubuntu3.1_i386.deb ...
Unpacking libsane-common (1.0.23-3ubuntu3.1) over (1.0.23-3ubuntu3) ...
Preparing to unpack .../libsdl1.2debian_1.2.15-8ubuntu1.1_i386.deb ...
Unpacking libsdl1.2debian:i386 (1.2.15-8ubuntu1.1) over (1.2.15-8ubuntu1) ...
Preparing to unpack .../libspectre1_0.2.7-2ubuntu1.1_i386.deb ...
Unpacking libspectre1:i386 (0.2.7-2ubuntu1.1) over (0.2.7-2ubuntu1) ...
Preparing to unpack .../libswscale2_6%3a9.16-0ubuntu0.14.04.1_i386.deb ...
Unpacking libswscale2:i386 (6:9.16-0ubuntu0.14.04.1) over (6:9.11-2ubuntu2) ...
Preparing to unpack .../libwbclient0_2%3a4.1.6+dfsg-1ubuntu2.14.04.3_i386.deb ...
Unpacking libwbclient0:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.3) over (2:4.1.6+dfsg-1ubuntu2) ...
Preparing to unpack .../libxatracker2_10.1.3-0ubuntu0.1_i386.deb ...
Unpacking libxatracker2:i386 (10.1.3-0ubuntu0.1) over (10.1.0-4ubuntu5) ...
Preparing to unpack .../libxfont1_1%3a1.4.7-1ubuntu0.1_i386.deb ...
Unpacking libxfont1:i386 (1:1.4.7-1ubuntu0.1) over (1:1.4.7-1) ...
Preparing to unpack .../lightdm_1.10.1-0ubuntu1_i386.deb ...
Unpacking lightdm (1.10.1-0ubuntu1) over (1.10.0-0ubuntu3) ...
Preparing to unpack .../initramfs-tools_0.103ubuntu4.2_all.deb ...
Unpacking initramfs-tools (0.103ubuntu4.2) over (0.103ubuntu4) ...
Preparing to unpack .../initramfs-tools-bin_0.103ubuntu4.2_i386.deb ...
Unpacking initramfs-tools-bin (0.103ubuntu4.2) over (0.103ubuntu4) ...
Preparing to unpack .../linux-image-3.13.0-24-generic_3.13.0-24.47_i386.deb ...
Done.
Unpacking linux-image-3.13.0-24-generic (3.13.0-24.47) over (3.13.0-24.46) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
Preparing to unpack .../libsmbclient_2%3a4.1.6+dfsg-1ubuntu2.14.04.3_i386.deb ...
Unpacking libsmbclient:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.3) over (2:4.1.6+dfsg-1ubuntu2) ...
Preparing to unpack .../samba-libs_2%3a4.1.6+dfsg-1ubuntu2.14.04.3_i386.deb ...
Unpacking samba-libs:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.3) over (2:4.1.6+dfsg-1ubuntu2) ...
Preparing to unpack .../ubuntu-drivers-common_1%3a0.2.91.5_i386.deb ...
Unpacking ubuntu-drivers-common (1:0.2.91.5) over (1:0.2.91.4) ...
Preparing to unpack .../multiarch-support_2.19-0ubuntu6.1_i386.deb ...
Unpacking multiarch-support (2.19-0ubuntu6.1) over (2.19-0ubuntu6) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for libglib2.0-0:i386 (2.40.0-2) ...
Processing triggers for ufw (0.34~rc-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up multiarch-support (2.19-0ubuntu6.1) ...
(Reading database ... 105637 files and directories currently installed.)
Preparing to unpack .../apt-utils_1.0.1ubuntu2.1_i386.deb ...
Unpacking apt-utils (1.0.1ubuntu2.1) over (1.0.1ubuntu2) ...
Preparing to unpack .../iputils-ping_3%3a20121221-4ubuntu1.1_i386.deb ...
Unpacking iputils-ping (3:20121221-4ubuntu1.1) over (3:20121221-4ubuntu1) ...
Preparing to unpack .../locales_2.13+git20120306-12.1_all.deb ...
Unpacking locales (2.13+git20120306-12.1) over (2.13+git20120306-12) ...
Preparing to unpack .../apt-transport-https_1.0.1ubuntu2.1_i386.deb ...
Unpacking apt-transport-https (1.0.1ubuntu2.1) over (1.0.1ubuntu2) ...
Preparing to unpack .../iputils-tracepath_3%3a20121221-4ubuntu1.1_i386.deb ...
Unpacking iputils-tracepath (3:20121221-4ubuntu1.1) over (3:20121221-4ubuntu1) ...
Preparing to unpack .../krb5-locales_1.12+dfsg-2ubuntu4.2_all.deb ...
Unpacking krb5-locales (1.12+dfsg-2ubuntu4.2) over (1.12+dfsg-2ubuntu4) ...
Preparing to unpack .../ltrace_0.7.3-4ubuntu5.1_i386.deb ...
Unpacking ltrace (0.7.3-4ubuntu5.1) over (0.7.3-4ubuntu5) ...
Preparing to unpack .../openssh-client_1%3a6.6p1-2ubuntu2_i386.deb ...
Unpacking openssh-client (1:6.6p1-2ubuntu2) over (1:6.6p1-2ubuntu1) ...
Preparing to unpack .../openssl_1.0.1f-1ubuntu2.5_i386.deb ...
Unpacking openssl (1.0.1f-1ubuntu2.5) over (1.0.1f-1ubuntu2) ...
Preparing to unpack .../synaptic_0.81.1ubuntu1_i386.deb ...
Unpacking synaptic (0.81.1ubuntu1) over (0.81.1) ...
Preparing to unpack .../lxsession-default-apps_0.4.9.2+git20140410-0ubuntu1.1_i386.deb ...
Unpacking lxsession-default-apps (0.4.9.2+git20140410-0ubuntu1.1) over (0.4.9.2+git20140410-0ubuntu1) ...
Preparing to unpack .../lxsession-data_0.4.9.2+git20140410-0ubuntu1.1_all.deb ...
Unpacking lxsession-data (0.4.9.2+git20140410-0ubuntu1.1) over (0.4.9.2+git20140410-0ubuntu1) ...
Preparing to unpack .../lxsession-logout_0.4.9.2+git20140410-0ubuntu1.1_i386.deb ...
Unpacking lxsession-logout (0.4.9.2+git20140410-0ubuntu1.1) over (0.4.9.2+git20140410-0ubuntu1) ...
Preparing to unpack .../lxsession_0.4.9.2+git20140410-0ubuntu1.1_i386.deb ...
update-alternatives: using /usr/bin/openbox-session to provide /usr/bin/x-session-manager (x-session-manager) in auto mode
Unpacking lxsession (0.4.9.2+git20140410-0ubuntu1.1) over (0.4.9.2+git20140410-0ubuntu1) ...
Preparing to unpack .../python3-update-manager_1%3a0.196.12_all.deb ...
Unpacking python3-update-manager (1:0.196.12) over (1:0.196.11) ...
Preparing to unpack .../update-manager-core_1%3a0.196.12_all.deb ...
Unpacking update-manager-core (1:0.196.12) over (1:0.196.11) ...
Preparing to unpack .../update-manager_1%3a0.196.12_all.deb ...
Unpacking update-manager (1:0.196.12) over (1:0.196.11) ...
Preparing to unpack .../rsync_3.1.0-2ubuntu0.1_i386.deb ...
Unpacking rsync (3.1.0-2ubuntu0.1) over (3.1.0-2) ...
Preparing to unpack .../uuid-runtime_2.20.1-5.1ubuntu20.1_i386.deb ...
Unpacking uuid-runtime (2.20.1-5.1ubuntu20.1) over (2.20.1-5.1ubuntu20) ...
Preparing to unpack .../abiword-common_3.0.0-4ubuntu1.1_all.deb ...
Unpacking abiword-common (3.0.0-4ubuntu1.1) over (3.0.0-4ubuntu1) ...
Preparing to unpack .../abiword_3.0.0-4ubuntu1.1_i386.deb ...
Unpacking abiword (3.0.0-4ubuntu1.1) over (3.0.0-4ubuntu1) ...
Preparing to unpack .../app-install-data_14.04.1_all.deb ...
Unpacking app-install-data (14.04.1) over (14.04.0) ...
Preparing to unpack .../grub-pc_2.02~beta2-9ubuntu1_i386.deb ...
Unpacking grub-pc (2.02~beta2-9ubuntu1) over (2.02~beta2-9) ...
Preparing to unpack .../grub-pc-bin_2.02~beta2-9ubuntu1_i386.deb ...
Unpacking grub-pc-bin (2.02~beta2-9ubuntu1) over (2.02~beta2-9) ...
Preparing to unpack .../grub2-common_2.02~beta2-9ubuntu1_i386.deb ...
Unpacking grub2-common (2.02~beta2-9ubuntu1) over (2.02~beta2-9) ...
Preparing to unpack .../grub-common_2.02~beta2-9ubuntu1_i386.deb ...
Unpacking grub-common (2.02~beta2-9ubuntu1) over (2.02~beta2-9) ...
Preparing to unpack .../python3-problem-report_2.14.1-0ubuntu3.3_all.deb ...
Unpacking python3-problem-report (2.14.1-0ubuntu3.3) over (2.14.1-0ubuntu3) ...
Preparing to unpack .../python3-apport_2.14.1-0ubuntu3.3_all.deb ...
Unpacking python3-apport (2.14.1-0ubuntu3.3) over (2.14.1-0ubuntu3) ...
Preparing to unpack .../apport_2.14.1-0ubuntu3.3_all.deb ...
apport stop/waiting
Unpacking apport (2.14.1-0ubuntu3.3) over (2.14.1-0ubuntu3) ...
Preparing to unpack .../apport-gtk_2.14.1-0ubuntu3.3_all.deb ...
Unpacking apport-gtk (2.14.1-0ubuntu3.3) over (2.14.1-0ubuntu3) ...
Preparing to unpack .../dbus-x11_1.6.18-0ubuntu4.1_i386.deb ...
Unpacking dbus-x11 (1.6.18-0ubuntu4.1) over (1.6.18-0ubuntu4) ...
Preparing to unpack .../evince_3.10.3-0ubuntu10.1_i386.deb ...
Unpacking evince (3.10.3-0ubuntu10.1) over (3.10.3-0ubuntu10) ...
Preparing to unpack .../libevdocument3-4_3.10.3-0ubuntu10.1_i386.deb ...
Unpacking libevdocument3-4 (3.10.3-0ubuntu10.1) over (3.10.3-0ubuntu10) ...
Preparing to unpack .../libevview3-3_3.10.3-0ubuntu10.1_i386.deb ...
Unpacking libevview3-3 (3.10.3-0ubuntu10.1) over (3.10.3-0ubuntu10) ...
Preparing to unpack .../libnautilus-extension1a_1%3a3.10.1-0ubuntu9.3_i386.deb ...
Unpacking libnautilus-extension1a (1:3.10.1-0ubuntu9.3) over (1:3.10.1-0ubuntu8) ...
Preparing to unpack .../evince-common_3.10.3-0ubuntu10.1_all.deb ...
Unpacking evince-common (3.10.3-0ubuntu10.1) over (3.10.3-0ubuntu10) ...
Preparing to unpack .../nautilus-data_1%3a3.10.1-0ubuntu9.3_all.deb ...
Unpacking nautilus-data (1:3.10.1-0ubuntu9.3) over (1:3.10.1-0ubuntu8) ...
Preparing to unpack .../file-roller_3.10.2.1-0ubuntu4.1_i386.deb ...
Unpacking file-roller (3.10.2.1-0ubuntu4.1) over (3.10.2.1-0ubuntu4) ...
Preparing to unpack .../firefox_31.0+build1-0ubuntu0.14.04.1_i386.deb ...
Unpacking firefox (31.0+build1-0ubuntu0.14.04.1) over (28.0+build2-0ubuntu2) ...
Preparing to unpack .../fontconfig_2.11.0-0ubuntu4.1_i386.deb ...
Unpacking fontconfig (2.11.0-0ubuntu4.1) over (2.11.0-0ubuntu4) ...
Preparing to unpack .../gdebi_0.9.5.3ubuntu2_all.deb ...
Unpacking gdebi (0.9.5.3ubuntu2) over (0.9.5.3) ...
Preparing to unpack .../gdebi-core_0.9.5.3ubuntu2_all.deb ...
Unpacking gdebi-core (0.9.5.3ubuntu2) over (0.9.5.3) ...
Preparing to unpack .../gir1.2-gudev-1.0_1%3a204-5ubuntu20.3_i386.deb ...
Unpacking gir1.2-gudev-1.0 (1:204-5ubuntu20.3) over (1:204-5ubuntu20) ...
Preparing to unpack .../gir1.2-webkit-3.0_2.4.3-1ubuntu2_i386.deb ...
Unpacking gir1.2-webkit-3.0 (2.4.3-1ubuntu2) over (2.4.0-1ubuntu2) ...
Preparing to unpack .../gir1.2-javascriptcoregtk-3.0_2.4.3-1ubuntu2_i386.deb ...
Unpacking gir1.2-javascriptcoregtk-3.0 (2.4.3-1ubuntu2) over (2.4.0-1ubuntu2) ...
Preparing to unpack .../iputils-arping_3%3a20121221-4ubuntu1.1_i386.deb ...
Unpacking iputils-arping (3:20121221-4ubuntu1.1) over (3:20121221-4ubuntu1) ...
Preparing to unpack .../libgtk-3-bin_3.10.8-0ubuntu1.2_i386.deb ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking libgtk-3-bin (3.10.8-0ubuntu1.2) over (3.10.8-0ubuntu1) ...
Preparing to unpack .../liblightdm-gobject-1-0_1.10.1-0ubuntu1_i386.deb ...
Unpacking liblightdm-gobject-1-0 (1.10.1-0ubuntu1) over (1.10.0-0ubuntu3) ...
Preparing to unpack .../liblwp-protocol-https-perl_6.04-2ubuntu0.1_all.deb ...
Unpacking liblwp-protocol-https-perl (6.04-2ubuntu0.1) over (6.04-2) ...
Preparing to unpack .../libminiupnpc8_1.6-3ubuntu2.14.04.1_i386.deb ...
Unpacking libminiupnpc8 (1.6-3ubuntu2.14.04.1) over (1.6-3ubuntu2) ...
Preparing to unpack .../network-manager-gnome_0.9.8.8-0ubuntu4.3_i386.deb ...
Unpacking network-manager-gnome (0.9.8.8-0ubuntu4.3) over (0.9.8.8-0ubuntu4) ...
Preparing to unpack .../libnm-gtk0_0.9.8.8-0ubuntu4.3_i386.deb ...
Unpacking libnm-gtk0 (0.9.8.8-0ubuntu4.3) over (0.9.8.8-0ubuntu4) ...
Preparing to unpack .../libnm-gtk-common_0.9.8.8-0ubuntu4.3_all.deb ...
Unpacking libnm-gtk-common (0.9.8.8-0ubuntu4.3) over (0.9.8.8-0ubuntu4) ...
Preparing to unpack .../libpurple0_1%3a2.10.9-0ubuntu3.1_i386.deb ...
Unpacking libpurple0 (1:2.10.9-0ubuntu3.1) over (1:2.10.9-0ubuntu3) ...
Preparing to unpack .../whoopsie_0.2.24.6_i386.deb ...
whoopsie stop/waiting
Unpacking whoopsie (0.2.24.6) over (0.2.24.5) ...
Preparing to unpack .../libwhoopsie0_0.2.24.6_i386.deb ...
Unpacking libwhoopsie0 (0.2.24.6) over (0.2.24.5) ...
Preparing to unpack .../light-locker-settings_1.2.1-0ubuntu1.1_all.deb ...
Unpacking light-locker-settings (1.2.1-0ubuntu1.1) over (1.2.1-0ubuntu1) ...
Preparing to unpack .../linux-firmware_1.127.5_all.deb ...
Unpacking linux-firmware (1.127.5) over (1.127) ...
Preparing to unpack .../linux-headers-3.13.0-24_3.13.0-24.47_all.deb ...
Unpacking linux-headers-3.13.0-24 (3.13.0-24.47) over (3.13.0-24.46) ...
Preparing to unpack .../linux-headers-3.13.0-24-generic_3.13.0-24.47_i386.deb ...
Unpacking linux-headers-3.13.0-24-generic (3.13.0-24.47) over (3.13.0-24.46) ...
Preparing to unpack .../linux-image-extra-3.13.0-24-generic_3.13.0-24.47_i386.deb ...
Unpacking linux-image-extra-3.13.0-24-generic (3.13.0-24.47) over (3.13.0-24.46) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
Preparing to unpack .../patch_2.7.1-4ubuntu1_i386.deb ...
Unpacking patch (2.7.1-4ubuntu1) over (2.7.1-4) ...
Preparing to unpack .../pidgin-data_1%3a2.10.9-0ubuntu3.1_all.deb ...
Unpacking pidgin-data (1:2.10.9-0ubuntu3.1) over (1:2.10.9-0ubuntu3) ...
Preparing to unpack .../pidgin_1%3a2.10.9-0ubuntu3.1_i386.deb ...
Unpacking pidgin (1:2.10.9-0ubuntu3.1) over (1:2.10.9-0ubuntu3) ...
Preparing to unpack .../pm-utils_1.4.1-13ubuntu0.1_all.deb ...
Unpacking pm-utils (1.4.1-13ubuntu0.1) over (1.4.1-13) ...
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.1_all.deb ...
Unpacking python-cupshelpers (1.4.3+20140219-0ubuntu2.1) over (1.4.3+20140219-0ubuntu2) ...
Preparing to unpack .../python-gi_3.12.0-1ubuntu1_i386.deb ...
Unpacking python-gi (3.12.0-1ubuntu1) over (3.12.0-1) ...
Preparing to unpack .../python-gobject_3.12.0-1ubuntu1_all.deb ...
Unpacking python-gobject (3.12.0-1ubuntu1) over (3.12.0-1) ...
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.3_i386.deb ...
Unpacking python-libxml2 (2.9.1+dfsg1-3ubuntu4.3) over (2.9.1+dfsg1-3ubuntu4) ...
Preparing to unpack .../software-properties-common_0.92.37.1_all.deb ...
Unpacking software-properties-common (0.92.37.1) over (0.92.36) ...
Preparing to unpack .../software-properties-gtk_0.92.37.1_all.deb ...
Unpacking software-properties-gtk (0.92.37.1) over (0.92.36) ...
Preparing to unpack .../python3-software-properties_0.92.37.1_all.deb ...
Unpacking python3-software-properties (0.92.37.1) over (0.92.36) ...
Preparing to unpack .../xdg-utils_1.1.0~rc1-2ubuntu7.1_all.deb ...
Unpacking xdg-utils (1.1.0~rc1-2ubuntu7.1) over (1.1.0~rc1-2ubuntu7) ...
Preparing to unpack .../simple-scan_3.12.1-0ubuntu1_i386.deb ...
Unpacking simple-scan (3.12.1-0ubuntu1) over (3.12.0-0ubuntu1) ...
Preparing to unpack .../system-config-printer-common_1.4.3+20140219-0ubuntu2.1_all.deb ...
Unpacking system-config-printer-common (1.4.3+20140219-0ubuntu2.1) over (1.4.3+20140219-0ubuntu2) ...
Preparing to unpack .../system-config-printer-gnome_1.4.3+20140219-0ubuntu2.1_all.deb ...
Unpacking system-config-printer-gnome (1.4.3+20140219-0ubuntu2.1) over (1.4.3+20140219-0ubuntu2) ...
Preparing to unpack .../transmission-gtk_2.82-1.1ubuntu3.1_i386.deb ...
Unpacking transmission-gtk (2.82-1.1ubuntu3.1) over (2.82-1.1ubuntu3) ...
Preparing to unpack .../transmission-common_2.82-1.1ubuntu3.1_all.deb ...
Unpacking transmission-common (2.82-1.1ubuntu3.1) over (2.82-1.1ubuntu3) ...
Preparing to unpack .../transmission_2.82-1.1ubuntu3.1_all.deb ...
Unpacking transmission (2.82-1.1ubuntu3.1) over (2.82-1.1ubuntu3) ...
Preparing to unpack .../usb-creator-gtk_0.2.56.1_i386.deb ...
Unpacking usb-creator-gtk (0.2.56.1) over (0.2.56) ...
Preparing to unpack .../usb-creator-common_0.2.56.1_i386.deb ...
Unpacking usb-creator-common (0.2.56.1) over (0.2.56) ...
Preparing to unpack .../xfce4-power-manager_1.2.0-3ubuntu4.1_i386.deb ...
Unpacking xfce4-power-manager (1.2.0-3ubuntu4.1) over (1.2.0-3ubuntu4) ...
Preparing to unpack .../xfce4-power-manager-data_1.2.0-3ubuntu4.1_all.deb ...
Unpacking xfce4-power-manager-data (1.2.0-3ubuntu4.1) over (1.2.0-3ubuntu4) ...
Preparing to unpack .../xserver-xorg-video-radeon_1%3a7.3.0-1ubuntu3.1_i386.deb ...
Unpacking xserver-xorg-video-radeon (1:7.3.0-1ubuntu3.1) over (1:7.3.0-1ubuntu3) ...
Preparing to unpack .../xserver-xorg-video-ati_1%3a7.3.0-1ubuntu3.1_i386.deb ...
Unpacking xserver-xorg-video-ati (1:7.3.0-1ubuntu3.1) over (1:7.3.0-1ubuntu3) ...
Preparing to unpack .../xul-ext-ubufox_2.9-0ubuntu0.14.04.1_all.deb ...
Unpacking xul-ext-ubufox (2.9-0ubuntu0.14.04.1) over (2.8-0ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for libglib2.0-0:i386 (2.40.0-2) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for lubuntu-software-center (0.0.8-0ubuntu1) ...
Creating package database in /var/cache/lsc_packages.db
Reading package lists... Done
Building dependency tree       
Reading state information... Done
prefixsuffix: package not found
xnetcardconfig: package not found
ubuntuone-control-panel-qt: package not found
dia-gnomeler-app: package not found
magicicada: package not found
kradioripper: package not found
bokken: package not found
dia-gnomenara: package not found
gnome-utils: package not found
maitreya: package not found
dia-gnome-gnome: package not found
insanity-tools: package not found
gstreamer0.10-ffmpeg: package not found
nvidia-96: package not found
vavoom: package not found
kita2: package not found
rdsconsole: package not found
abuse: package not found
python3.3: package not found
arkose-gui: package not found
idle-python3.3: package not found
ubuntuone-control-panel-qt: package not found
edubuntu-desktop-kde: package not found
atris: package not found
Creating table utils
Creating table universalaccess
Creating table audiovideo
Creating table games
Creating table graphic
Creating table network
Creating table education
Creating table scienze
Creating table system
Creating table devel
Creating table tweaks
Creating table fonts
Creating table office
Creating table packages
mame: not found
drascula-french: not found
mess: not found
love: not found
grr.app: not found
tomahawk: not found
clustalx: not found
drascula-spanish: not found
fcitx-qimpanel-configtool: not found
Done
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Setting up libdbus-1-3:i386 (1.6.18-0ubuntu4.1) ...
Setting up libjson-c2:i386 (0.11-3ubuntu1.2) ...
Setting up libcgmanager0:i386 (0.24-0ubuntu7) ...
Setting up libudev1:i386 (204-5ubuntu20.3) ...
Setting up udev (204-5ubuntu20.3) ...
udev stop/waiting
udev start/running, process 24755
Removing 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up ifupdown (0.7.47.2ubuntu4.1) ...
Installing new version of config file /etc/init/network-interface.conf ...
Setting up libjson0:i386 (0.11-3ubuntu1.2) ...
Setting up libapt-inst1.5:i386 (1.0.1ubuntu2.1) ...
Setting up libtasn1-6:i386 (3.4-3ubuntu0.1) ...
Setting up libgnutls26:i386 (2.12.23-12ubuntu2.1) ...
Setting up libgnutls-openssl27:i386 (2.12.23-12ubuntu2.1) ...
Setting up libmagic1:i386 (1:5.14-2ubuntu3.1) ...
Setting up file (1:5.14-2ubuntu3.1) ...
Setting up libssl1.0.0:i386 (1.0.1f-1ubuntu2.5) ...
Setting up resolvconf (1.69ubuntu1.1) ...
Setting up libgirepository-1.0-1 (1.40.0-1ubuntu0.1) ...
Setting up gir1.2-glib-2.0 (1.40.0-1ubuntu0.1) ...
Setting up gir1.2-freedesktop (1.40.0-1ubuntu0.1) ...
Setting up python3-gi (3.12.0-1ubuntu1) ...
Setting up libgtk-3-common (3.10.8-0ubuntu1.2) ...
Setting up libkrb5support0:i386 (1.12+dfsg-2ubuntu4.2) ...
Setting up libk5crypto3:i386 (1.12+dfsg-2ubuntu4.2) ...
Setting up libkrb5-3:i386 (1.12+dfsg-2ubuntu4.2) ...
Setting up libgssapi-krb5-2:i386 (1.12+dfsg-2ubuntu4.2) ...
Setting up libcups2:i386 (1.7.2-0ubuntu1.1) ...
Setting up fontconfig-config (2.11.0-0ubuntu4.1) ...
Installing new version of config file /etc/fonts/conf.avail/30-metric-aliases.conf ...
Setting up libfreetype6:i386 (2.5.2-1ubuntu2.2) ...
Setting up libfontconfig1:i386 (2.11.0-0ubuntu4.1) ...
Setting up libgtk-3-0:i386 (3.10.8-0ubuntu1.2) ...
Setting up libgail-3-0:i386 (3.10.8-0ubuntu1.2) ...
Setting up libcupsppdc1:i386 (1.7.2-0ubuntu1.1) ...
Setting up libcupsmime1:i386 (1.7.2-0ubuntu1.1) ...
Setting up libjbig0:i386 (2.0-2ubuntu4.1) ...
Setting up libtiff5:i386 (4.0.3-7ubuntu0.1) ...
Setting up libcupsfilters1:i386 (1.0.52-0ubuntu1.2) ...
Setting up libcupsimage2:i386 (1.7.2-0ubuntu1.1) ...
Setting up libcupscgi1:i386 (1.7.2-0ubuntu1.1) ...
Setting up cups-daemon (1.7.2-0ubuntu1.1) ...
cups start/running, process 25003
Setting up cups-filters-core-drivers (1.0.52-0ubuntu1.2) ...
Setting up cups-core-drivers (1.7.2-0ubuntu1.1) ...
Setting up cups-server-common (1.7.2-0ubuntu1.1) ...
Setting up libgs9-common (9.10~dfsg-0ubuntu10.2) ...
Setting up libgs9 (9.10~dfsg-0ubuntu10.2) ...
Setting up ghostscript (9.10~dfsg-0ubuntu10.2) ...
Setting up ghostscript-x (9.10~dfsg-0ubuntu10.2) ...
Setting up cups-common (1.7.2-0ubuntu1.1) ...
Setting up cups-client (1.7.2-0ubuntu1.1) ...
Setting up cups-ppdc (1.7.2-0ubuntu1.1) ...
Setting up libfontembed1:i386 (1.0.52-0ubuntu1.2) ...
Setting up cups-filters (1.0.52-0ubuntu1.2) ...
.
Setting up cups (1.7.2-0ubuntu1.1) ...
Updating PPD files for cups ...
Updating PPD files for cups-filters ...
Updating PPD files for foomatic-db-compressed-ppds ...
Updating PPD files for openprinting-ppds ...
Updating PPD files for gutenprint ...
Setting up gir1.2-gtk-3.0 (3.10.8-0ubuntu1.2) ...
Setting up libasprintf0c2:i386 (0.18.3.1-1ubuntu3) ...
Setting up gettext-base (0.18.3.1-1ubuntu3) ...
Setting up im-config (0.24-1ubuntu4.1) ...
Setting up libsystemd-login0:i386 (204-5ubuntu20.3) ...
Setting up libaccountsservice0:i386 (0.6.35-0ubuntu7.1) ...
Setting up libelf1:i386 (0.158-0ubuntu5.1) ...
Setting up libsystemd-daemon0:i386 (204-5ubuntu20.3) ...
Setting up libxml2:i386 (2.9.1+dfsg1-3ubuntu4.3) ...
Setting up libnspr4:i386 (2:4.10.2-1ubuntu1.1) ...
Setting up libcamel-1.2-45 (3.10.4-0ubuntu1.1) ...
Setting up evolution-data-server-common (3.10.4-0ubuntu1.1) ...
Setting up libedataserver-1.2-18 (3.10.4-0ubuntu1.1) ...
Setting up libebook-contacts-1.2-0 (3.10.4-0ubuntu1.1) ...
Setting up libabiword-3.0:i386 (3.0.0-4ubuntu1.1) ...
Setting up libavutil52:i386 (6:9.16-0ubuntu0.14.04.1) ...
Setting up libavcodec54:i386 (6:9.16-0ubuntu0.14.04.1) ...
Setting up libavformat54:i386 (6:9.16-0ubuntu0.14.04.1) ...
Setting up libavresample1:i386 (6:9.16-0ubuntu0.14.04.1) ...
Setting up libdbusmenu-glib4:i386 (12.10.3+14.04.20140612-0ubuntu1) ...
Setting up gir1.2-dbusmenu-glib-0.4 (12.10.3+14.04.20140612-0ubuntu1) ...
Setting up libdbusmenu-gtk3-4:i386 (12.10.3+14.04.20140612-0ubuntu1) ...
Setting up libdbusmenu-gtk4:i386 (12.10.3+14.04.20140612-0ubuntu1) ...
Setting up libdebian-installer4:i386 (0.88ubuntu5) ...
Setting up libgl1-mesa-dri:i386 (10.1.3-0ubuntu0.1) ...
Setting up libgbm1:i386 (10.1.3-0ubuntu0.1) ...
Setting up libglapi-mesa:i386 (10.1.3-0ubuntu0.1) ...
Setting up libgl1-mesa-glx:i386 (10.1.3-0ubuntu0.1) ...
Setting up libegl1-mesa:i386 (10.1.3-0ubuntu0.1) ...
Setting up libwayland-egl1-mesa:i386 (10.1.3-0ubuntu0.1) ...
Setting up libopenvg1-mesa:i386 (10.1.3-0ubuntu0.1) ...
Setting up libegl1-mesa-drivers:i386 (10.1.3-0ubuntu0.1) ...
Setting up libgpgme11:i386 (1.4.3-0.1ubuntu5.1) ...
Setting up libgphoto2-port10:i386 (2.5.3.1-1ubuntu2.2) ...
Setting up libgphoto2-6:i386 (2.5.3.1-1ubuntu2.2) ...
Setting up libgstreamer1.0-0:i386 (1.2.4-0ubuntu1) ...
Setting up libgstreamer-plugins-base1.0-0:i386 (1.2.4-1~ubuntu1) ...
Setting up libgtk2.0-common (2.24.23-0ubuntu1.1) ...
Setting up libgtk2.0-0:i386 (2.24.23-0ubuntu1.1) ...
Setting up gtk2-engines-pixbuf:i386 (2.24.23-0ubuntu1.1) ...
Setting up libgudev-1.0-0:i386 (1:204-5ubuntu20.3) ...
Setting up libido3-0.1-0:i386 (13.10.0+14.04.20140423-0ubuntu1) ...
Setting up libwebkitgtk-3.0-common (2.4.3-1ubuntu2) ...
Setting up libjavascriptcoregtk-3.0-0:i386 (2.4.3-1ubuntu2) ...
Setting up libwebkitgtk-3.0-0:i386 (2.4.3-1ubuntu2) ...
Setting up liblzo2-2:i386 (2.06-1.2ubuntu1.1) ...
Setting up libsane-common (1.0.23-3ubuntu3.1) ...
Setting up libsane:i386 (1.0.23-3ubuntu3.1) ...
Setting up libsdl1.2debian:i386 (1.2.15-8ubuntu1.1) ...
Setting up libspectre1:i386 (0.2.7-2ubuntu1.1) ...
Setting up libswscale2:i386 (6:9.16-0ubuntu0.14.04.1) ...
Setting up libwbclient0:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up libxatracker2:i386 (10.1.3-0ubuntu0.1) ...
Setting up libxfont1:i386 (1:1.4.7-1ubuntu0.1) ...
Setting up initramfs-tools-bin (0.103ubuntu4.2) ...
Setting up initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.13.0-24-generic (3.13.0-24.47) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.13.0-24.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.13.0-24.46 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up samba-libs:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up libsmbclient:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up ubuntu-drivers-common (1:0.2.91.5) ...
Setting up apt-utils (1.0.1ubuntu2.1) ...
Setting up iputils-ping (3:20121221-4ubuntu1.1) ...
Setting up locales (2.13+git20120306-12.1) ...
Generating locales...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZM.UTF-8... done
  en_ZW.UTF-8... done
  ga_IE.UTF-8... done
  ja_JP.UTF-8... up-to-date
Generation complete.
Setting up apt-transport-https (1.0.1ubuntu2.1) ...
Setting up iputils-tracepath (3:20121221-4ubuntu1.1) ...
Setting up krb5-locales (1.12+dfsg-2ubuntu4.2) ...
Setting up ltrace (0.7.3-4ubuntu5.1) ...
Setting up openssh-client (1:6.6p1-2ubuntu2) ...
Setting up openssl (1.0.1f-1ubuntu2.5) ...
Setting up synaptic (0.81.1ubuntu1) ...
Setting up lxsession-default-apps (0.4.9.2+git20140410-0ubuntu1.1) ...
Setting up lxsession-data (0.4.9.2+git20140410-0ubuntu1.1) ...
Setting up lxsession-logout (0.4.9.2+git20140410-0ubuntu1.1) ...
Setting up lxsession (0.4.9.2+git20140410-0ubuntu1.1) ...
update-alternatives: renaming x-session-manager.1.gz slave link from /usr/share/man/man1/x-session-manager.1.gz to /usr/share/man/man1/lxsession-manager.1.gz
update-alternatives: using /usr/bin/lxsession to provide /usr/bin/x-session-manager (x-session-manager) in auto mode
update-alternatives: warning: skip creation of /usr/share/man/man1/lxsession-manager.1.gz because associated file /usr/share/man/man1/lxsession.1.gz (of link group x-session-manager) doesn't exist
Setting up python3-update-manager (1:0.196.12) ...
Setting up update-manager-core (1:0.196.12) ...
Setting up update-manager (1:0.196.12) ...
Setting up rsync (3.1.0-2ubuntu0.1) ...
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match rsync Default-Stop values (none)
 System start/stop links for /etc/init.d/rsync already exist.
Setting up uuid-runtime (2.20.1-5.1ubuntu20.1) ...
Setting up abiword-common (3.0.0-4ubuntu1.1) ...
Setting up abiword (3.0.0-4ubuntu1.1) ...
Setting up app-install-data (14.04.1) ...
Setting up grub-common (2.02~beta2-9ubuntu1) ...
Setting up grub2-common (2.02~beta2-9ubuntu1) ...
Setting up grub-pc-bin (2.02~beta2-9ubuntu1) ...
Setting up grub-pc (2.02~beta2-9ubuntu1) ...
Installing for i386-pc platform.
Installation finished. No error reported.
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up python3-problem-report (2.14.1-0ubuntu3.3) ...
Setting up python3-apport (2.14.1-0ubuntu3.3) ...
Setting up apport (2.14.1-0ubuntu3.3) ...
apport start/running
Setting up apport-gtk (2.14.1-0ubuntu3.3) ...
Setting up libevdocument3-4 (3.10.3-0ubuntu10.1) ...
Setting up libevview3-3 (3.10.3-0ubuntu10.1) ...
Setting up libnautilus-extension1a (1:3.10.1-0ubuntu9.3) ...
Setting up evince-common (3.10.3-0ubuntu10.1) ...
Setting up evince (3.10.3-0ubuntu10.1) ...
Setting up nautilus-data (1:3.10.1-0ubuntu9.3) ...
Setting up file-roller (3.10.2.1-0ubuntu4.1) ...
Setting up firefox (31.0+build1-0ubuntu0.14.04.1) ...
Installing new version of config file /etc/apparmor.d/usr.bin.firefox ...
Please restart all running instances of firefox, or you will experience problems.
Setting up fontconfig (2.11.0-0ubuntu4.1) ...
Regenerating fonts cache... done.
Setting up gdebi-core (0.9.5.3ubuntu2) ...
Setting up gdebi (0.9.5.3ubuntu2) ...
Setting up gir1.2-gudev-1.0 (1:204-5ubuntu20.3) ...
Setting up gir1.2-javascriptcoregtk-3.0 (2.4.3-1ubuntu2) ...
Setting up gir1.2-webkit-3.0 (2.4.3-1ubuntu2) ...
Setting up iputils-arping (3:20121221-4ubuntu1.1) ...
Setting up libgtk-3-bin (3.10.8-0ubuntu1.2) ...
Setting up liblightdm-gobject-1-0 (1.10.1-0ubuntu1) ...
Setting up liblwp-protocol-https-perl (6.04-2ubuntu0.1) ...
Setting up libminiupnpc8 (1.6-3ubuntu2.14.04.1) ...
Setting up libnm-gtk-common (0.9.8.8-0ubuntu4.3) ...
Setting up libnm-gtk0 (0.9.8.8-0ubuntu4.3) ...
Setting up libpurple0 (1:2.10.9-0ubuntu3.1) ...
Setting up libwhoopsie0 (0.2.24.6) ...
Setting up whoopsie (0.2.24.6) ...
whoopsie start/running, process 1763
Setting up light-locker-settings (1.2.1-0ubuntu1.1) ...
Setting up linux-firmware (1.127.5) ...
Setting up linux-headers-3.13.0-24 (3.13.0-24.47) ...
Setting up linux-headers-3.13.0-24-generic (3.13.0-24.47) ...
Setting up linux-image-extra-3.13.0-24-generic (3.13.0-24.47) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.13.0-24.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.13.0-24.46 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up patch (2.7.1-4ubuntu1) ...
Setting up pidgin-data (1:2.10.9-0ubuntu3.1) ...
Setting up pidgin (1:2.10.9-0ubuntu3.1) ...
Setting up pm-utils (1.4.1-13ubuntu0.1) ...
Setting up python-cupshelpers (1.4.3+20140219-0ubuntu2.1) ...
Setting up python-gi (3.12.0-1ubuntu1) ...
Setting up python-gobject (3.12.0-1ubuntu1) ...
Setting up python-libxml2 (2.9.1+dfsg1-3ubuntu4.3) ...
Setting up python3-software-properties (0.92.37.1) ...
Setting up software-properties-common (0.92.37.1) ...
Setting up software-properties-gtk (0.92.37.1) ...
Setting up xdg-utils (1.1.0~rc1-2ubuntu7.1) ...
Setting up simple-scan (3.12.1-0ubuntu1) ...
Setting up system-config-printer-common (1.4.3+20140219-0ubuntu2.1) ...
Setting up system-config-printer-gnome (1.4.3+20140219-0ubuntu2.1) ...
Setting up transmission-common (2.82-1.1ubuntu3.1) ...
Setting up transmission-gtk (2.82-1.1ubuntu3.1) ...
Setting up transmission (2.82-1.1ubuntu3.1) ...
Setting up usb-creator-common (0.2.56.1) ...
Setting up usb-creator-gtk (0.2.56.1) ...
Setting up xfce4-power-manager-data (1.2.0-3ubuntu4.1) ...
Setting up xserver-xorg-video-radeon (1:7.3.0-1ubuntu3.1) ...
Setting up xserver-xorg-video-ati (1:7.3.0-1ubuntu3.1) ...
Setting up xul-ext-ubufox (2.9-0ubuntu0.14.04.1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up upstart (1.12.1-0ubuntu4.2) ...
Installing new version of config file /etc/cron.daily/upstart ...
Setting up dbus (1.6.18-0ubuntu4.1) ...
Setting up accountsservice (0.6.35-0ubuntu7.1) ...
Setting up language-selector-common (0.129.2) ...
Installing new version of config file /etc/fonts/conf.avail/69-language-selector-zh-hk.conf ...
Installing new version of config file /etc/fonts/conf.avail/69-language-selector-zh-sg.conf ...
Installing new version of config file /etc/fonts/conf.avail/69-language-selector-zh-cn.conf ...
Installing new version of config file /etc/fonts/conf.avail/69-language-selector-zh-tw.conf ...
Installing new version of config file /etc/fonts/conf.avail/69-language-selector-zh-mo.conf ...
Setting up language-selector-gnome (0.129.2) ...
Setting up systemd-services (204-5ubuntu20.3) ...
Installing new version of config file /etc/systemd/logind.conf ...
Setting up libpam-systemd:i386 (204-5ubuntu20.3) ...
systemd-logind start/running, process 8746
Setting up lightdm (1.10.1-0ubuntu1) ...
Setting up dbus-x11 (1.6.18-0ubuntu4.1) ...
Setting up network-manager-gnome (0.9.8.8-0ubuntu4.3) ...
Installing new version of config file /etc/xdg/autostart/nm-applet.desktop ...
Setting up xfce4-power-manager (1.2.0-3ubuntu4.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.1) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
steve@steve-Inspiron-910:~$ 
```

```
sudo apt-get install linux-firmware-nonfree

```
```
steve@steve-Inspiron-910:~$ sudo apt-get install linux-firmware-nonfree
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 3,943 kB of archives.
After this operation, 8,982 kB of additional disk space will be used.
Get:1 [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) trusty/multiverse linux-firmware-nonfree all 1.14ubuntu1 [3,943 kB]
Fetched 3,943 kB in 2s (1,572 kB/s)                 
Selecting previously unselected package linux-firmware-nonfree.
(Reading database ... 105660 files and directories currently installed.)
Preparing to unpack .../linux-firmware-nonfree_1.14ubuntu1_all.deb ...
Unpacking linux-firmware-nonfree (1.14ubuntu1) ...
Setting up linux-firmware-nonfree (1.14ubuntu1) ...
steve@steve-Inspiron-910:~$
```

```
sudo modprobe -rf b43
```

```
steve@steve-Inspiron-910:~$  sudo modprobe -rf b43
[sudo] password for steve: 
steve@steve-Inspiron-910:~$

```
```
sudo modprobe b43
```

```
steve@steve-Inspiron-910:~$ sudo modprobe b43
[sudo] password for steve: 
steve@steve-Inspiron-910:~$
```

Nothing happened with the last two commands.

---

### Post by Hadaka on 2014-08-14
they aren't suppose to say anything. please remove the ethernet
cable, boot and test wireless. report back please.

---

### Post by stevesy on 2014-08-14
> **Hadaka said:**
> they aren't suppose to say anything. please remove the ethernet
cable, boot and test wireless. report back please.

Hi Hadaka, I rebooted, clicked on the wlan0 icon and got a list of available networks.  I selected my SSID but when I entered the encryption key i didn't get a wireless connection/nothing happened.

---

### Post by Hadaka on 2014-08-14
please edit your connection in network manager to look like the attached
[ATTACH=CONFIG]255489[/ATTACH][ATTACH=CONFIG]255490[/ATTACH]
click save after changes,boot and test wireless
the dns server is 8.8.8.8,8.8.4.4 google

---

### Post by stevesy on 2014-08-14
Will do.  Will get back to you.

---

### Post by stevesy on 2014-08-15
> **Hadaka said:**
> please edit your connection in network manager to look like the attached
[ATTACH=CONFIG]255489[/ATTACH][ATTACH=CONFIG]255490[/ATTACH]
click save after changes,boot and test wireless
the dns server is 8.8.8.8,8.8.4.4 google

Apologies for the delay Hadaka.  When I open network connections my wireless connection is not showing so I can't edit it.  Only my ethernet/wired connection appears there.  There is an option to "Add" a wireless connection, but I wouldn't be entirely sure of the correct settings to use in the "General", "Wi-Fi" and "Wi-Fi Security" tabs.

---

### Post by varunendra on 2014-08-15
stevesy,

It is a HUGE pain to scroll down such huge wall of text as in a couple of your earlier posts. Please ALWAYS use 'Code' tags for ALL terminal commands as well as outputs (especially outputs!). It seems you already know how to use 'Code' tags, but if not, please follow the "Use Code Tags" link in my signature below.

Regarding the problem, can we see a wireless_script report showing current status please? I'd recommend the report of this one : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by stevesy on 2014-08-15
> **varunendra said:**
> stevesy,

It is a HUGE pain to scroll down such huge wall of text as in a couple of your earlier posts. Please ALWAYS use 'Code' tags for ALL terminal commands as well as outputs (especially outputs!). It seems you already know how to use 'Code' tags, but if not, please follow the "Use Code Tags" link in my signature below.

Regarding the problem, can we see a wireless_script report showing current status please? I'd recommend the report of this one : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

```
wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script
```

gives the following report

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

steve-Inspiron-910 3.13.0-34-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Atom(TM) CPU N270   @ 1.60GHz
Memory : 991 MB
Uptime : 14:36:49 up 18:38,  2 users,  load average: 0.17, 0.37, 0.35


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:04b5]
    Kernel driver in use: b43-pci-bridge
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:02b0]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 0c45:63e4 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: hci0: Bluetooth                  no            no
1: phy0: Wireless LAN               no            no
2: compal-wifi: Wireless LAN        no            no
3: compal-bluetooth: Bluetooth      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

b43                   356470  0 
bcma                   42043  1 b43
mac80211              546051  1 b43
cfg80211              409394  2 b43,mac80211
ssb                    51854  1 b43


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | r8169  | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.0.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             89.101.160.4
    DNS:             89.101.160.5
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | b43    | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    UPC2528618:      Infra, <MAC C-05 UPC2528618>, Freq 2437 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    UPC245354629:    Infra, <MAC C-06 UPC245354629>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    Horizon Wi-Free: Infra, <MAC C-04 Horizon Wi-Free>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    Horizon Wi-Free: Infra, <MAC C-01 Horizon Wi-Free>, Freq 2437 MHz, Rate 54 Mb/s, Strength 84 WPA2 Enterprise
    UPC245004762:    Infra, <MAC C-07 UPC245004762>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    Horizon Wi-Free: Infra, <MAC C-03 Horizon Wi-Free>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA2 Enterprise
    UPC256999:       Infra, <MAC C-02 UPC256999>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA
    UPC1383820:      Infra, <MAC C-09 UPC1383820>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    eircom93894972:  Infra, <MAC C-08 eircom93894972>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    UPC2267791:      Infra, <MAC C-NA UPC2267791 1>, Freq 2417 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.618/0.900/1.182/0.282 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.089/0.098/0.107/0.009 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : en_IE.UTF-8)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Horizon Wi-Free>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Horizon Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000045b31247cd
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 02 - Address: <MAC C-02 UPC256999>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"UPC256999"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000045b3123f5c
                    Extra: Last beacon: 36ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Horizon Wi-Free>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Horizon Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000203e05bfa
                    Extra: Last beacon: 244ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC C-04 Horizon Wi-Free>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Horizon Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000c7c9f3
                    Extra: Last beacon: 236ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC C-05 UPC2528618>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"UPC2528618"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000125a8bbbe6
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 UPC245354629>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"UPC245354629"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000c7a0f0
                    Extra: Last beacon: 240ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 UPC245004762>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"UPC245004762"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000203dffe03
                    Extra: Last beacon: 248ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 eircom93894972>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"eircom93894972"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003fde2538d
                    Extra: Last beacon: 12260ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 UPC1383820>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"UPC1383820"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000df6b977a8
                    Extra: Last beacon: 1132ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 Horizon Wi-Free>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Horizon Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000df773fdfe
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[b43]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     42BAE2DB9BADE3E7ECA2CC0
depends:        bcma,ssb,mac80211,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        

[mac80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/ssb/ssb.ko
srcversion:     3DE188310F77C566C2E8CB3
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (b43)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-34-generic root=UUID=1dbf390f-ad78-4e66-beb4-d9519f9fc7de ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.224741] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.225510] audit: initializing netlink socket (disabled)
[    2.131561] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.140343] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    2.140374] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    2.140397] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    2.140426] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    2.140451] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    2.226054] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    8.323659] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.847511] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    8.989628] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   12.972925] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   18.541404] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.553060] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========


```

---

### Post by varunendra on 2014-08-15
Evidently, no connection attempt was made at all as per the script. It might have given us some hints if you could run the script AFTER attempting a connection. But let's move forward with what 'should' work -

In Network Connection settings,

1) Under "Wireless" tab, click "Add" > put your AP's SSID in "SSID" field under "Wireless" tab (leave the rest at defaults)
2) Under "Wireless Security" tab, select the correct security type and fill in the required information correctly. All the listed APs in your report are either WPA/WPA2 Personal networks or 'Enterprise' networks of the same kind. Choose the security type accordingly.
3) Leave the remaining two tabs (IPv4 and IPv6 Settings) at defaults or set them as Hadaka showed in his screenshots.
4) Make sure "Connect Automatically" and "Available to all users" checkboxes are checked.
5) Save > Close > Try to connect > report back the result with a fresh wireless_script report if it still fails.

If the description above doesn't match what you see in your Network Connections settings boxes, please post their screenshots.
If you are not sure about the security settings, please tell us which of the listed Access-Points (in the report above) you are trying to connect to.

---

### Post by Hadaka on 2014-08-15
hi, unplug your wired connection and see if the wireless network symbol
shows up, also be sure to leave the ethernet cable unplugged when you
run the wireless script as varun requested.
thanks.

---

### Post by stevesy on 2014-08-15
> **Hadaka said:**
> hi, unplug your wired connection and see if the wireless network symbol
shows up, also be sure to leave the ethernet cable unplugged when you
run the wireless script as varun requested.
thanks.

Hey, the wireless network symbol doesn't show up when the ethernet cable is unplugged.  Running the wireless script with the ethernet cable unplugged gives:

```
steve@steve-Inspiron-910:~$ wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script
--2014-08-15 16:58:13--  https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script
Resolving dl.dropbox.com (dl.dropbox.com)... failed: Name or service not known.
wget: unable to resolve host address ‘dl.dropbox.com’
steve@steve-Inspiron-910:~$
```

---

### Post by varunendra on 2014-08-15
That method you used above is meant for the state when the computer has a working internet connection. For offline computers, there is a different method which is also mentioned in the same post that I originally linked to.

But now that you already have the wireless_script in your home directory (due to previous attempt), simply run the following command in a terminal to run it again -
```
bash ./wireless_script
```
..then follow the prompts like before. Make sure to delete the report file (wireless-info.txt) before running the script as mentioned above, to avoid confusion.

I am assuming you have followed the instructions in my/Hadaka's previous posts to create a new connection. If not, do that before any of this.

---

### Post by stevesy on 2014-08-15
> **varunendra said:**
> Evidently, no connection attempt was made at all as per the script. It might have given us some hints if you could run the script AFTER attempting a connection. But let's move forward with what 'should' work -

In Network Connection settings,

1) Under "Wireless" tab, click "Add" > put your AP's SSID in "SSID" field under "Wireless" tab (leave the rest at defaults)
2) Under "Wireless Security" tab, select the correct security type and fill in the required information correctly. All the listed APs in your report are either WPA/WPA2 Personal networks or 'Enterprise' networks of the same kind. Choose the security type accordingly.
3) Leave the remaining two tabs (IPv4 and IPv6 Settings) at defaults or set them as Hadaka showed in his screenshots.
4) Make sure "Connect Automatically" and "Available to all users" checkboxes are checked.
5) Save > Close > Try to connect > report back the result with a fresh wireless_script report if it still fails.

If the description above doesn't match what you see in your Network Connections settings boxes, please post their screenshots.
If you are not sure about the security settings, please tell us which of the listed Access-Points (in the report above) you are trying to connect to.

Success! Thanks guys : ]    I don't have a wireless connection icon but I can connect using the wlan0 icon in the "manage networks" panel applet.  Fyi IPv4 and IPv6 are at defaults, I haven't set them as Haduka showed.

---

### Post by varunendra on 2014-08-15
Glad it worked, finally. :)

If you need help with something else (regarding the same problem of course), please feel free to ask.

If you are satisfied with the current solution, please mark the thread as **[SOLVED]** using "Thread Tools" link above the top post.

---

### Post by stevesy on 2014-08-15
> **varunendra said:**
> Glad it worked, finally. :)

If you need help with something else (regarding the same problem of course), please feel free to ask.

If you are satisfied with the current solution, please mark the thread as **[SOLVED]** using "Thread Tools" link above the top post.

Yes varunendra, I'm delighted : D  It's been a bit of a nightmare without wireless..  I'm just wondering if there is a way to get the wireless connection/network manager icon back, as I tried the fix at [http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html) which didn't work for me.  Also, to connect to other wireless networks will I need to keep adding/creating wireless connections?

---

### Post by varunendra on 2014-08-15
Please open a terminal (Ctrl-Alt-T), and try to run 'nm-applet' from there -
```
nm-applet
```
Does it bring up the Network Manager icon (it is called "nm-applet" icon by the way) in the notification area?

If not, you should see the error message in the terminal. Post back what it is.

**PS:**
If we can get the nm-applet up and running, you shouldn't need to manually add connection settings for new connections.

---

### Post by stevesy on 2014-08-15
> **varunendra said:**
> Please open a terminal (Ctrl-Alt-T), and try to run 'nm-applet' from there -
```
nm-applet
```
Does it bring up the Network Manager icon (it is called "nm-applet" icon by the way) in the notification area?

If not, you should see the error message in the terminal. Post back what it is.

**PS:**
If we can get the nm-applet up and running, you shouldn't need to manually add connection settings for new connections.

No sign of the icon varunendra, here's the error message:

```
steve@steve-Inspiron-910:~$ nm-applet

** (nm-applet:2806): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-qu15cEFK00: Connection refused
nm-applet-Message: using fallback from indicator to GtkStatusIcon


```

---

### Post by Hadaka on 2014-08-15
You need to remove the wired connection for the wireless icon to show
unplug the ethernet cable and boot
is the wireless showing now?

---

### Post by stevesy on 2014-08-15
> **Hadaka said:**
> You need to remove the wired connection for the wireless icon to show
unplug the ethernet cable and boot
is the wireless showing now?

The Ethernet cable was unplugged Hadaka.  I've rebooted and tried nm-applet again in the terminal and got:

```
steve@steve-Inspiron-910:~$ nm-applet
nm-applet-Message: using fallback from indicator to GtkStatusIcon



```

It seems to be hanging at the end there i.e. it doesn't go back to steve@steve-Inspiron-910:~$

---

### Post by varunendra on 2014-08-15
Looks like a broken installation to me. Let's try purging and re-installing network-manager package.

Please download the network-manager packages first, while you are connected to internet -
```
sudo apt-get install -d --reinstall network-manager network-manager-gnome
```

Then purge the whole network-manager package -
```
sudo apt-get purge network-manager-gnome network-manager
```
Reboot, and re-install it from the downloaded packages -
```
sudo apt-get install network-manager network-manager-gnome
```
Then retry -
```
nm-applet
```
Still the same error? After a second reboot?

---

### Post by stevesy on 2014-08-17
> **varunendra said:**
> Looks like a broken installation to me. Let's try purging and re-installing network-manager package.

Please download the network-manager packages first, while you are connected to internet -
```
sudo apt-get install -d --reinstall network-manager network-manager-gnome
```

Then purge the whole network-manager package -
```
sudo apt-get purge network-manager-gnome network-manager
```
Reboot, and re-install it from the downloaded packages -
```
sudo apt-get install network-manager network-manager-gnome
```
Then retry -
```
nm-applet
```
Still the same error? After a second reboot?

Hi varunendra, I am on a different computer as I am without an internet connection on my netbook atm.  I am in the process of reinstalling Lubuntu 14.04 due to that and also some odd file system behaviour.

I don't have the exact output sorry, but when I rebooted and tried to reinstall from the downloaded packages I got a lot of output at the end saying "E: Unable to fetch..." . I then tried nm-applet and got something like "nm-applet can be found in the following packages: *network-manager-gnome *mythbuntu".  I rebooted, tried nm-applet again and got the same message.

Can you please advise as to what way to proceed once Lubuntu has been reinstalled?  Thanks, and sorry for the delay in getting back to you.

---

### Post by varunendra on 2014-08-17
The same way as suggested previously. If the first command completed without errors, the rest should complete without complains as well. But if the source media that you are installing from is intact, you shouldn't face such problems at all.

If you face the same issues and same errors on the fresh install as before, check your installation media for consistency : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If errors are found, it means your downloaded ISO of Lubuntu is broken itself, in which case, a fresh download would be essential. For downloading ISOs, torrents are recommended to ensure data integrity during the download.

---

### Post by stevesy on 2014-08-17
> **varunendra said:**
> The same way as suggested previously. If the first command completed without errors, the rest should complete without complains as well. But if the source media that you are installing from is intact, you shouldn't face such problems at all.

If you face the same issues and same errors on the fresh install as before, check your installation media for consistency : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If errors are found, it means your downloaded ISO of Lubuntu is broken itself, in which case, a fresh download would be essential. For downloading ISOs, torrents are recommended to ensure data integrity during the download.

Ok varunedra Lubuntu is reinstalled and wired connection is working.  So I should go ahead and try purging and re-installing network-manager package?

---

### Post by varunendra on 2014-08-17
Only if the problem persists after installing "linux-firmware-nonfree" package as before. So install that one first, as it is required to make the native driver work -
```
sudo apt-get install linux-firmware-nonfree
```
Reboot and make sure you can connect, using the previous fix if required.

Then run "nm-applet" in a terminal again and see if it works this time. If not, and it returns the same error as in post #25, then please do an update -
```
sudo apt-get update
sudo apt-get dist-upgrade
```
..then proceed with reinstalling network-manager packages as mentioned in post #28. You can confirm whether ALL the required packages are actually downloaded to the system or not by looking in the /var/cache/apt/archives directory. Look in it BEFORE running the first command in post #28, then again AFTER running it. If there are new packages in it (especially network-manager-gnome...., network-manager.... etc.), proceed with purging/reinstalling.

---

### Post by stevesy on 2014-09-10
> **varunendra said:**
> Only if the problem persists after installing "linux-firmware-nonfree" package as before. So install that one first, as it is required to make the native driver work -
```
sudo apt-get install linux-firmware-nonfree
```
Reboot and make sure you can connect, using the previous fix if required.

Then run "nm-applet" in a terminal again and see if it works this time. If not, and it returns the same error as in post #25, then please do an update -
```
sudo apt-get update
sudo apt-get dist-upgrade
```
..then proceed with reinstalling network-manager packages as mentioned in post #28. You can confirm whether ALL the required packages are actually downloaded to the system or not by looking in the /var/cache/apt/archives directory. Look in it BEFORE running the first command in post #28, then again AFTER running it. If there are new packages in it (especially network-manager-gnome...., network-manager.... etc.), proceed with purging/reinstalling.

Hi varunendra I've been away for a while sorry for the delay in replying.  I decided to install Xubuntu 14.04.1 as Lubuntu was doing my head in.  Again, wireless is not working for me on Xubuntu.  I've installed linux-firmware-nonfree and rebooted but no luck.  I've tried creating a wireless network connection as before and that isn't working.  nm-applet (icon with an up and down arrow) is on the panel and it also appears on the panel when I enter nm-applet into the terminal, so i assume it's working ok.  Can you please help me to get this problem sorted, thanks.

---

### Post by varunendra on 2014-09-10
> **stevesy said:**
> nm-applet (icon with an up and down arrow) is on the panel..

..the up/down arrow icon usually indicates an active Ethernet connection. Can you try the wireless without the ethernet cable plugged in? Reboot with the cable unplugged if required. If the wireless doesn't detect any available networks, please try -
```
sudo iwlist scan
```
..and see if it can detect the available networks now and connect to the desired one. If not, please post a fresh report of the wireless_script.

**PS:**
You shouldn't direct your posts to specifically me when you have so many great personalities of the wireless team on your thread. :)

---

### Post by stevesy on 2014-09-10
> **varunendra said:**
> ..the up/down arrow icon usually indicates an active Ethernet connection. Can you try the wireless without the ethernet cable plugged in? Reboot with the cable unplugged if required. If the wireless doesn't detect any available networks, please try -
```
sudo iwlist scan
```
..and see if it can detect the available networks now and connect to the desired one. If not, please post a fresh report of the wireless_script.

**PS:**
You shouldn't direct your posts to specifically me when you have so many great personalities of the wireless team on your thread. :)

Thanks varunendra, yes I rebooted and tried wireless with the ethernet cable unplugged but no wireless networks were detected.


```
steve@steve-Inspiron-910:~$ sudo iwlist scan
[sudo] password for steve: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

steve@steve-Inspiron-910:~$ 


```

Wireless Script

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

steve-Inspiron-910 3.13.0-32-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Atom(TM) CPU N270   @ 1.60GHz
Memory : 991 MB
Uptime : 17:48:19 up 14 min,  3 users,  load average: 0.16, 0.36, 0.29


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:04b5]
    Kernel driver in use: b43-pci-bridge
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:02b0]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 003: ID 0c45:63e4 Microdia 
Bus 001 Device 002: ID 1058:0830 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: hci0: Bluetooth                  no            no
1: compal-wifi: Wireless LAN        no            no
2: compal-bluetooth: Bluetooth      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

b43                   356470  0 
bcma                   42043  1 b43
mac80211              546051  1 b43
cfg80211              409394  2 b43,mac80211
ssb                    51854  1 b43


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=======o========o===========o=========o===========o==============o===========
 Interface & ID             | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
============================o=======o========o===========o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired | r8169  | connected | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.0.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             89.101.160.4
    DNS:             89.101.160.5
----------------------------+-------+--------+-----------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.741/0.756/0.771/0.015 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.097/0.098/0.100/0.010 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : en_US.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

No way to aquire root rights found.


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[b43]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     42BAE2DB9BADE3E7ECA2CC0
depends:        bcma,ssb,mac80211,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/ssb/ssb.ko
srcversion:     3DE188310F77C566C2E8CB3
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=c804f558-481e-4084-9d5c-192200c75949 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.227611] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.228430] audit: initializing netlink socket (disabled)
[    2.165659] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    2.165688] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    2.165711] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    2.165733] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    2.165755] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    2.168268] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.228673] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    9.049798] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.502410] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    9.564281] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[    9.625595] b43 ssb0:0: Direct firmware load failed with error -2
[    9.625609] b43 ssb0:0: Falling back to user helper
[   11.331366] b43 ssb0:0: Direct firmware load failed with error -2
[   11.331371] b43 ssb0:0: Falling back to user helper
[   11.542175] b43 ssb0:0: Direct firmware load failed with error -2
[   11.542181] b43 ssb0:0: Falling back to user helper
[   11.545119] b43 ssb0:0: Direct firmware load failed with error -2
[   11.545125] b43 ssb0:0: Falling back to user helper
[   11.570667] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   11.570876] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   11.571083] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

    ======== Done ========


```

I take your point varunendra, I meant no offence to any of the guys on the wireless team by directing my post to you, it was just because you had been dealing with my problem in depth.  I welcome and appreciate input from all of you : ]

---

### Post by varunendra on 2014-09-10
Doesn't look like 'linux-firmware-nonfree' package is installed -
> **stevesy said:**
> ```

[   11.570667] b43-phy0 ERROR: [COLOR="#FF0000"]Firmware file "b43/ucode15.fw" not found[/COLOR]
[   11.570876] b43-phy0 ERROR: [COLOR="#FF0000"]Firmware file "b43-open/ucode15.fw" not found[/COLOR]
[   11.571083] b43-phy0 ERROR: **You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver** version. Please carefully read all instructions on this website.

    ======== Done ========


```

Please try that again, with a working wired connection -
```
sudo apt-get install linux-firmware-nonfree
```
Post back its output/errors here. If there are no errors, you should have a working wireless after a reboot.

If your ethernet connection is not working either, then to install the firmware offline : [http://ubuntuforums.org/showpost.php?p=13062169](http://ubuntuforums.org/showpost.php?p=13062169)

---

### Post by stevesy on 2014-09-10
> **varunendra said:**
> Doesn't look like 'linux-firmware-nonfree' package is installed -


Please try that again, with a working wired connection -
```
sudo apt-get install linux-firmware-nonfree
```
Post back its output/errors here. If there are no errors, you should have a working wireless after a reboot.


```
steve@steve-Inspiron-910:~$ sudo apt-get install linux-firmware-nonfree
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 98 not to upgrade.
```

---

### Post by varunendra on 2014-09-10
Hmm.. looks like it's time to go manual..

Please download the attached zip file onto your Desktop. Then open a terminal, and run the following commands in it -
```
cd Desktop
unzip b43.zip
sudo mkdir -p /lib/firmware/b43
sudo cp b43/* /lib/firmware/b43
```
Reboot, and check -
```
dmesg | grep firmware
```
If no errors, you should have a working wifi. If the error messages do show up again, please post back the output of -
```
ls /lib/firmware/b43
```

---

### Post by stevesy on 2014-09-10
> **varunendra said:**
> Hmm.. looks like it's time to go manual..

Please download the attached zip file onto your Desktop. Then open a terminal, and run the following commands in it -
```
cd Desktop
unzip b43.zip
sudo mkdir -p /lib/firmware/b43
sudo cp b43/* /lib/firmware/b43
```
Reboot, and check -
```
dmesg | grep firmware
```
If no errors, you should have a working wifi. If the error messages do show up again, please post back the output of -
```
ls /lib/firmware/b43
```

YES!! It's working varunendra : ] Thank you!

```
steve@steve-Inspiron-910:~$ dmesg | grep firmware
[   13.533552] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)


```

---

### Post by varunendra on 2014-09-10
Awesome!!

If you have a launchpad account, or if you don't mind creating one, please add yourself to the "Affects Me" list of this bug report : [https://bugs.launchpad.net/bugs/1367882](https://bugs.launchpad.net/bugs/1367882) ..adding a comment on how the usual installation of "linux-firmware-nonfree" package failed.

Thanks!

---

