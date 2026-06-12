---
title: "usr/bin/dpkg returned an error code (2)"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by Escher9000 on 2009-05-09
Sorry to have my very first post be a request for aid. . . but my Google-fu has failed me and I just don't have sufficient experience to solve it by tinkering yet.

I'm attempting to add some applications and getting an error message.

Selecting previously deselected package libmikmod2.
(Reading database . . .  dpkg: unrecoverable fatal error, aborting:
files list file for package 'winbind' is missing final newline
E: Sub-process usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover

and then just the blinking cursor.

Any suggestions?

---

### Post by Partyboi2 on 2009-05-10
Hi, open a terminal and try
```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/winbind.list
```

---

### Post by 3rdalbum on 2009-05-10
Try checking the contents of the file "/var/lib/dpkg./info/winbind.list".

I had the same problem recently; the contents of the file were gibberish. I deleted the offending file but dpkg complained of the same problem with another package. I ran fsck which found some problems, but it didn't fix the problem.

I bit the bullet and reinstalled Ubuntu - no loss to me as the original system was only a couple of hours old anyway. I'd love to know if there was an easy way to get the package manager working again.

---

### Post by Didius Falco on 2009-05-10
I did a bit of Googling and found this, along with a few reports of people reporting success with this method:

> **by Fernan Aguero**
1. The package list files are in /var/lib/dpkg/info

  In my case /var/lib/dpkg/info/libgtk1.2.list was corrupted
  (its contents were binary cruft).

  So the best way to go about this is to

2. Manually reinstall the affected package 

  # move the info dir containing corrupted data out of the
  # way, and create a new 'info' dir
  cd /var/lib/dpkg
  sudo mv info info.bak
  sudo mkdir info

  # reinstall the affected package, in my case this was
  sudo apt-get --reinstall install libgtk1.2

  # this will print lots of warnings about missing list
  # files for the dependencies, which is obvious.
  # now move the newly generated files in 'info/' to the 
  # 'info.bak/' directory containing info for all packages
  # this will replace the information for the package 
  # we just installed
  sudo mv info/* info.bak/

  # and now get things back to where they were
  sudo rm -rf info
  sudo mv info.bak info

Here is a link:

[https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html)

I hope this solves the problem for you...

Regards,

Didius

---

### Post by ihavenoideax2 on 2011-10-30
> **Didius Falco said:**
> I did a bit of Googling and found this, along with a few reports of people reporting success with this method:



Here is a link:

[https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html)

I hope this solves the problem for you...

Regards,

Didius

This just saved my install. Thanks.

(Sorry to bring a old thread back to life)

---

### Post by oldos2er on 2011-10-31
Closed for necromancy.

---

