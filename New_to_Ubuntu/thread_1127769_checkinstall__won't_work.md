---
title: "checkinstall  won't work"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by cfree220 on 2009-04-16
I'm trying to upgrade my server from php version 5.2.6 to 5.2.9 to solve some security issues I found with Nessus. 5.2.6 is the most recent in the repositories, so I downloaded the source and tried to compile it and make it into a .deb using checkinstall. I've been trying to get this to work all afternoon, and have tried both the .tar.gz and the .tar.bz2 tarballs from the php.net download site. I'm pretty sure the issue is with checkinstall itself, as I am able to install the program using "make install". Here is there error returned by checkinstall:

```
Installing with make install...

========================= Installation results ===========================
Installing PHP SAPI module:       cgi
Installing PHP CGI binary: /usr/local/bin/
chmod: changing permissions of `/usr/local/bin/#INST@24884#': No such file or directory
make: *** [install-sapi] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

I run into a similar problem when trying to compile Apache 2.2.11

---

### Post by andrew.46 on 2009-04-16
Hi,

There is a long-standing bug with checkinstall that can be bypassed by adding:

```
--fstrans=no
```

to your checkinstall line. I suspect that this might fix your problem.

Andrew

---

### Post by cfree220 on 2009-04-17
That did it, thank you so much!

---

### Post by andrew.46 on 2009-04-17
Hi cfree220,

> **cfree220 said:**
> That did it, thank you so much!

It is my pleasure :-). I believe this rather hackish fix has been formalised in Jaunty by a similar setting in /etc/checkinstall.rc:

```

# Are we going to use filesystem translation?
# Note: checkinstall, as of 1.6.1 doesn't handle the at family of syscalls.
# This means that translation doesn't work as coreutils uses them.
TRANSLATE=0

```

This problem was noted on the [checkinstall website]("http://www.asic-linux.com.mx/~izto/checkinstall/") in 2007 and there is apparently a fix in the git repository but still no release version after almost 2 years. Hopefully soon :-).

Andrew

---

### Post by perixx on 2009-05-13
Hi andrew.46,


Many thanks for your hint. I've come across a similar posting like yours, but it's said to be a dangerous command there:
[http://ubuntuforums.org/archive/index.php/t-959729.html](http://ubuntuforums.org/archive/index.php/t-959729.html)

I've tried to compile quite some programs so far; ever so often, the installation should rather take place via a self-made .deb package, but checkinstall will refuse to do so mostly, because of 'missing permissions' on creating the neccessary folders, so it seems (sudo won't do). 
Also, using the '--install=no' option, to just create the .deb and install it later, will not do what it should, but still create folders and symlinks - thus, breaking up the installation. 

As a workaround, creating the file structure on the disc with a simple 'make install' will work, previous to 'checkinstall' - I rather use the following command: ```
checkinstall --fstrans=no --install=no
```
Of course, this seems to only be sensible for creating .deb's in the first place, as no control over the installation is given and the System's package manager isn't involved here.

But, after the .deb's been created, I use it as an uninstaller for the program previously installed via a plain 'make install' command, simply by installing and un-installing the .deb package. While it's unclear, how clean this procedure will work, it seems to do well enough so far.

I thought, this could maybe help some people out there...

greetings,


perixx

---

