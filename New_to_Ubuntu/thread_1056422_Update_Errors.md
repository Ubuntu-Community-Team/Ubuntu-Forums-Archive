---
title: "Update Errors"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by ashwat on 2009-01-31
I am getting the following error message for the past 7 days, whenever I am trying to update.

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.




What do I do?

---

### Post by taurus on 2009-01-31
1.  You need a key for Medibuntu's repos.

Applications -> Accessories -> Terminal
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

2.  You need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.

Save it.  Then close down gedit editing window and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ashwat on 2009-02-12
> **taurus said:**
> 1.  You need a key for Medibuntu's repos.

Applications -> Accessories -> Terminal
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

2.  You need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.

Save it.  Then close down gedit editing window and run

```
sudo apt-get update
sudo apt-get upgrade
```
I did the step 1 suggested and got this > Fetched 198B in 1s (100B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by plucky on 2009-02-13
From a terminal try this command ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```


Also don't forget to put a # in front of the "deb cdrom" lines in sources.list.It will get rid of these warnings

> W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead. 

Good Luck

---

### Post by ashwat on 2009-02-13
> **plucky said:**
> From a terminal try this command ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```


Also don't forget to put a # in front of the "deb cdrom" lines in sources.list.It will get rid of these warnings



Good Luck





Thanks. It worked :)

---

