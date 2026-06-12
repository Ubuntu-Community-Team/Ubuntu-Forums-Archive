---
title: "Duplicate sources.list entry error"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by n125 on 2010-08-08
Heya

I've been using Ubuntu for about a year now and I'm getting pretty comfortable with it, but I still don't have much confidence when it comes to fixing errors, so I figured I'd ask here.

Synaptic Package Manager and Update Manager like to throw this error out at me every now and then:

> W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)

In my sources.list (/etc/apt/), the only entries that have to do with Google are

> deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

They don't look like duplicate entries to me, but I could be wrong. Any help?

Thanks for reading.

---

### Post by Bachstelze on 2010-08-08
Anything google in /etc/apt/sources.list.d?

---

### Post by jtarin on 2010-08-08
> **_/var/lib/apt/lists/_**dl.google.com_linux_chrome_deb_dists_stable_main_b inary-i386_PackagesLook in that directory and see if for some reason you have duplicates.
Have a look to see if there is a /etc/apt/sources.list.d folder which may contain the duplicate entry. Third party entries often go into this folder, eg, medibuntu.list, and are read as if in sources.list.

---

### Post by n125 on 2010-08-08
> **Bachstelze said:**
> Anything google in /etc/apt/sources.list.d?

Hm, yeah, there are two things Google in there:

```
:~$ cd /etc/apt/sources.list.d/ && ls
google-chrome.list  google-chrome.list.save
```

> **jtarin said:**
> Look in that directory and see if for some reason you have duplicates.
Have a look to see if there is a /etc/apt/sources.list.d folder which may contain the duplicate entry. Third party entries often go into this folder, eg, medibuntu.list, and are read as if in sources.list.

In /var/lib/apt/lists, the Google-related things I see are

```
:~$ cd /var/lib/apt/lists/ && ls
dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages
dl.google.com_linux_chrome_deb_dists_stable_Release
dl.google.com_linux_chrome_deb_dists_stable_Release.gpg
dl.google.com_linux_deb_dists_testing_non-free_binary-i386_Packages
dl.google.com_linux_deb_dists_testing_Release
dl.google.com_linux_deb_dists_testing_Release.gpg
```

---

### Post by mheseltine on 2012-05-11
Hi there,

This might help if you've done something similar to what I did.

I followed the steps in [this guide]("http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/") to install Chrome on Ubuntu.

One of the steps creates a [FONT="Courier New"]google.list[/FONT] file in [FONT="Courier New"]/etc/apt/sources.list.d[/FONT]

The problem is caused because the Chrome install also creates a file in the same folder with the same content called [FONT="Courier New"]google-chrome.list[/FONT]

Removing one of the two files seems to fix it, ie

```
$ sudo rm /etc/apt/sources.list.d/google.list
```

then
```
$ sudo apt-get update
```

seems to fix the problem for me.

- mark

---

