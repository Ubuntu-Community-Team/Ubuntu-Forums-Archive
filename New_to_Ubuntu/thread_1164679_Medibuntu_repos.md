---
title: "Medibuntu repos"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by SL1DEmemphis on 2009-05-19
When I enter the following in the Terminal:

[B]sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

I get a series of errors:
[/B]
W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.


is this a problem, what do I do about this?
I'm trying to get codecs so I can view movies and stuff.

---

### Post by SL1DEmemphis on 2009-05-19
btw, im getting this from here [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by taurus on 2009-05-19
Go into System -> Administration -> Software Sources and remove the check mark for your Cdrom.  Then, close it and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by SunnyRabbiera on 2009-05-19
try to manually download the keyring here:
[http://packages.medibuntu.org/hardy/medibuntu-keyring.html](http://packages.medibuntu.org/hardy/medibuntu-keyring.html)

even though the link says hardy it should work if you are using newer versions.

---

### Post by SL1DEmemphis on 2009-05-19
Thanks, that seems to have fixed that, but now i get:

W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

