---
title: "Can I download GoogleEarth and run it in Ubuntu 8.10?"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by jburrell on 2009-04-18
Hi again all.  Can I download and run Google Earth in Ubuntu 8.10?  I just went to the page and it said it was for Linux as well but when I downloaded the file it was a "bin" file and it says there's no application for it.
Thanks

---

### Post by qwertyuiop96 on 2009-04-18
First, try adding the medibuntu repo and going to syntapic, seach Google Earth, and Download it.  Let me know if that doesn't work.  Its complicated otherwise.

---

### Post by PhrankDaChickenGeek on 2009-04-18
Just add medibuntu to your respository, and you can install it with Synaptic Package Manger!

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by NightwishFan on 2009-04-18
How to add Medibuntu:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


Then use synaptic like normal, enjoy!

If you do not like links then:

IN TERMINAL:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```]

What release are you using?

Intrepid Ibex 8.10:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

---

### Post by jburrell on 2009-04-18
I ran the commands in the terminal and here's what the output is:
----------------------------------

jeff@me:~$ sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
[sudo] password for jeff: 
--2009-04-18 19:33:41--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 230 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 230         --.-K/s   in 0s      

2009-04-18 19:33:41 (9.22 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [230/230]

Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11.7kB]
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages [3518B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/main Translation-en_US
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages [8225B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/main Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/universe Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/multiverse Sources
Fetched 23.7kB in 6s (3684B/s)
Reading package lists...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 160 not upgraded.
Need to get 3448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Authentication warning overridden.
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free medibuntu-keyring 2008.04.20 [3448B]
Fetched 3448B in 0s (10.2kB/s)
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 115625 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11.7kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/main Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/universe Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Fetched 11.9kB in 26s (443B/s)
Reading package lists...
jeff@me:~$ sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
--2009-04-18 19:35:29--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 230 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 230         --.-K/s   in 0s      

2009-04-18 19:35:29 (7.58 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [230/230]

jeff@me:~$ 

---------------------
If the above is correct now what do I do?

---

### Post by llamabr on 2009-04-18
```
apt-cache search google earth
```

---

### Post by Tahakki on 2009-04-18
I used the .bin file. Go to the directory where it is and type:

> ./GoogleEarthLinux.bin

Before doing the above, make sure it's executable. Right-click on the file, hit properties then the permissions tab, and check the 'Allow Executing as program' box.

It should unpack and install.

---

### Post by mikewhatever on 2009-04-18
Here's a guide on how to install GE from the .bin file.
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by jburrell on 2009-04-18
Here is the output of that command:

jeff@me:~$ apt-cache search google earth
googleearth-package - utility to automatically build a Debian package of Google Earth
googleearth - metapackage for Google Earth!
googleearth-4.2 - Google Earth! 4.2 - binary files
googleearth-4.2-data - Google Earth! 4.2 - data files
googleearth-4.3 - Google Earth! 4.3 - binary files
googleearth-4.3-data - Google Earth! 4.3 - data files

---

### Post by qwertyuiop96 on 2009-04-18
If you installed Medibuntu proprely, and it looks like you did go to syntapic and search for google earth.  Check it, and hit apply.

---

### Post by PaulReaver on 2009-04-19
If you downloaded the binary from google remember to "chmod +x" the file to make it executable.

---

