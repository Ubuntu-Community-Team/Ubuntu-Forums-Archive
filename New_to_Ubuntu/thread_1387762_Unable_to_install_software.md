---
title: "Unable to install software"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by cressrt on 2010-01-22
I'm new to Linux and am struggling at the moment to install anything; trying to install Flash and Wine but the Synaptic Package Manger keeps returning errors when trying to Mark for Installation:-

For Flash-
flashplugin-nonfree:
 Depends: flashplugin-installer but it is not going to be installed

For WIne
wine:
 Depends: wine1.2 but it is not going to be installed

wine1.2:
 Depends: ia32-libs (>=1.6) but it is not installable
 Depends: lib32asound2 (>1.0.14) but it is not installable
 Depends: libc6-i386 (>=2.6-1) but it is not installable
 Depends: lib32nss-mdns (>=0.10-3) but it is not installable
 Recommends: ttf-liberation  but it is not installable
 Recommends: winbind  but it is not installable
 Recommends: wine1.2-gecko  but it is not installable
 Recommends: ttf-mscorefonts-installer  but it is not installable

Am I doing something wrong or what? Help please?

---

### Post by philinux on 2010-01-22
Hi,

Assuming you are connected to the net.

Open a terminal. Applications>accessories>terminal.

Copy and paste this command in and post back with any errors.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by cressrt on 2010-01-22
It stalled at 57% and then returned the following:

Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg  
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]
Reading package lists... Done                        
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2)  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_GB.bz2)  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_GB.bz2)  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_GB.bz2)  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_GB.bz2)  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_GB.bz2)  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_GB.bz2)  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_GB.bz2)  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by warfacegod on 2010-01-22
Go to Synaptic. Under Edit, select Fix Broken Packages.

---

### Post by philinux on 2010-01-22
Can you use the internet at all with firefox?

---

### Post by cressrt on 2010-01-22
No apparent problems with Firefox.

Clicked on Fix Broken Packages, it do not appear to do anything

---

### Post by philinux on 2010-01-22
> **cressrt said:**
> No apparent problems with Firefox.

Clicked on Fix Broken Packages, it do not appear to do anything

Ok

System>Admin>software sources.

Change the server to main. Drop down box "Download From"

Then when prompted click the reload button

---

### Post by cressrt on 2010-01-22
Thanks
That seems to have done it as I am now able to "Mark for Installation", just need to install now.
Should I leave  connected to the Main Server or revert to the local one?

---

### Post by blackened on 2010-01-22
The local server is apparently unreachable. You should either stick to the main server, or you could use the "Select Best Server" option from within the software sources dialog.

---

### Post by philinux on 2010-01-22
> **cressrt said:**
> Thanks
That seems to have done it as I am now able to "Mark for Installation", just need to install now.
Should I leave  connected to the Main Server or revert to the local one?

Run this again and see if it goes without error. You can leave it on main.

```
sudo apt-get update && sudo apt-get upgrade


```

---

### Post by cressrt on 2010-01-22
It gave a couple of errors:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by warfacegod on 2010-01-22
> **cressrt said:**
> It gave a couple of errors:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

That probably means you still have Synaptic open. Make sure Synaptic, Add/Remove, Ubuntu Software Center, and Upgrade Manager are all closed.

---

### Post by cressrt on 2010-01-22
Thanks to all.

Have re run updates and waited for about 10mins while it plodded through everything. Now to install Flash and Wine.

---

### Post by cressrt on 2010-01-22
Close thread please

---

### Post by warfacegod on 2010-01-22
Then this is solved? If so, then please mark as solved under thread tools and let us what you did.

---

### Post by Hetor on 2010-01-22
> **warfacegod said:**
> Then this is solved? If so, then please mark as solved under thread tools and let us what you did.

Obviously, he just installed wine & flash through the package manager.

---

### Post by warfacegod on 2010-01-22
> **Hetor said:**
> Obviously, he just installed wine & flash through the package manager.

No, not obviously. cressrt didn't specifically state that Wine and Flash were installed, but that he was going to. Neither was there mention of what actually worked nor has the thread been marked as Solved.

---

### Post by cressrt on 2010-01-22
Sorry,
Rerun updates and was then able to mark the relevant files for installation, then successfully installed WINE and FLASH through Package Manager, again thanks for all the help.

---

