---
title: "Package Manager Error"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by sevenX on 2010-03-21
I cannot get into my synaptic package manager anymore... I have the following error:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I was getting error prior to this when opening package manager but i would just click ok and it let me in and download packages still. So here is screenshots of errors I was getting... first one i dont have copy + paste of error just screenshot but second pic is of what I am getting now.

---

### Post by patchwork on 2010-03-21
Open a terminal and type```
sudo dpkg --configure -a
```

---

### Post by sevenX on 2010-03-21
Awsome that solved my latest problem :) I can get into package maanger again! but.... my old error is still popping up it reads:

W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_karmic_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_karmic-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_karmic-security_multiverse_binary-i386_Packages)

Would you know about this.. maybe I've installed two of somthing???

---

### Post by patchwork on 2010-03-21
Did you manually edit your /etc/apt/sources.list?

You have multiple entries of the same repository.

---

### Post by sevenX on 2010-03-21
I belive I did... I am still fresh meat to the linux world and cant remember what I was doing but following a tutorial for somthing...  Is there a way to undo this?

---

### Post by patchwork on 2010-03-21
Manually edit your /etc/apt/sources.list and remove the duplicate entries of

[http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/multiverse Packages

Ensure only one instance of this repo remains (and you only delete the duplicate instances, not a different repo with a similar name)
```
gksu gedit /etc/apt/sources.list
```

EDIT:  When you're finished, run
```
sudo apt-get update
``` to update the repository list

---

### Post by sevenX on 2010-03-21
SOLVED! :D PATCHWORK YOU ROCK!! THANK YOU! THANK YOU! :popcorn:

---

### Post by Daisymorrigan on 2010-03-22
Ditto that. I found this to be very helpful. Thank you.:-)

---

