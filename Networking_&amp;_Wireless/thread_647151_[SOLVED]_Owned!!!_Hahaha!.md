---
title: "[SOLVED] Owned!!! Hahaha!"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by mLes-_- on 2007-12-22
Well guys I am embarrassed to say I just got OWNED! Okay, I am on my third install of Ubuntu 7.10, and attempting to make my Linksys WUSB54GSC work. I have been following this "How To": [http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206) and I got an error on the first step!!! HAHAHA. This is what it said:

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu9_i386.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

What did I do wrong?


Edit: I am dual booting Ubuntu and WinXpPro.  I also searched the CD and FOUND what it had a "Hash Sum Mismatch" error with. Sooooo.... haha please help me im so confused and been trying for a week to get this working.

---

### Post by finito on 2007-12-22
that looks like either you don't have the Gutsy 7.10 CD in the Drive or The cd is scratched and damaged.

Try burning a new CD or mount the ISO you have

---

### Post by jfinkels on 2007-12-22
Or just download the file and get it to your machine from [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by mLes-_- on 2007-12-22
Thank you so much for the reply.  What is the difference between the Gutsy packages and the Gutsy-backports?

---

### Post by finito on 2007-12-22
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.47_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.47_i386.deb)
[http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu9_i386.deb](http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu9_i386.deb)

Here just get these

---

### Post by mLes-_- on 2007-12-22
okay if I get them then what do I do?  Please excuse the noob questions I have never used linux before.

---

### Post by finito on 2007-12-22
click on them as you would an exe it will show you a wizard follow it and then do what ever you were doin when you got that error.

---

### Post by mLes-_- on 2007-12-22
see just translate it to windows terms for me and ill understand it haha tyvm

---

### Post by jfinkels on 2007-12-22
> **mLes-_- said:**
> Thank you so much for the reply.  What is the difference between the Gutsy packages and the Gutsy-backports?

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by mLes-_- on 2007-12-22
MAKING TONS OF PROGRESS THANKS SO MUCH GUYS!

I now am reciveing this error when trying to reload some software sources???.... I entered each address into IE, but no d/l started.  Any idea on how to gain these files?
I am doing this to get my internet working, but it says i must have an internet connection ROFL!

[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:) Could not resolve 'archive.ubuntu.com'

---

### Post by mLes-_- on 2007-12-22
WOW I GOT IT WOWOWOWOWOOWOWOW <3333333333 Thanks for the help guys!!! Now how do i marked this solved?

---

### Post by PreviousN on 2007-12-22
Hey there, two things:

1. To mark as solved: click on the post, then there should be a tools menu. Click on that and it will drop down and you can select "mark as solved". 

2. You may want to consider doing this: 
* Open a terminal 
* Type "sudo gedit /etc/apt/sources.list" 
* On the first or second line it'll say like " cd://" or something. Put a "#" in front of that. This is "commenting out" the cd as a source. There's no point in keeping it, because once you install you've got the latest stuff on the cd. In my experience it just gets in the way of installing security updates. 

Cheers!

---

