---
title: "hidden folders in home directory"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by fwin on 2010-02-12
Hi,

1)I just would like to know what are the hidden folders in the home directory for?

all of these start with "." i.e.  .purple or .cache

2) can i delete them?


thanks

---

### Post by halitech on 2010-02-12
most of them are where the personal settings are kept for programs so only delete if you want to have your settings removed

---

### Post by fwin on 2010-02-12
Thanks for replying halitech, 

So, if i uninstall a program via the synaptic manager, will it get rid of all the files and FOLDERS related to it even this ones in the home directroy?

---

### Post by halitech on 2010-02-12
only if you select remove all

---

### Post by lukeiamyourfather on 2010-02-12
> **halitech said:**
> most of them are where the personal settings are kept for programs so only delete if you want to have your settings removed

Ditto. Just ignore them, especially don't delete something if you don't know ***exactly*** what it is. Cheers!

---

### Post by fwin on 2010-02-12
so the programs themselves (executables) are installed in a different location, and the home directory is just for the settings of these programs, am i right? 

I am just trying to understand how the OS works

---

### Post by halitech on 2010-02-12
yes, programs are installed in places like /usr/bin and /opt and just the settings files are in the home folder in the hidden folders

---

### Post by fwin on 2010-02-12
Thank you everyone for the help, I'm going to mark this thread as solved.

---

### Post by Riverside on 2010-02-14
> **fwin said:**
> Thanks for replying halitech, 

So, if i uninstall a program via the synaptic manager, will it get rid of all the files and FOLDERS related to it even this ones in the home directroy?No.  If you "Mark for Complete Removal" a package using Synaptic Package Manager then click Apply, Synaptic will remove all of the files installed by the package when it was installed (if you "Mark for Removal" instead, it will remove all of the files installed by the package when it was installed except for those files within the package which are configuration files).

Synaptic will not, however, remove files created by executable files within a package once it has been installed and run, no matter what Synaptic Package Manager option that you select.

To view all files which are part of any installed package, you can use dpkg -L at the command line for example:

anthony@riverside:~$ dpkg -L ipcalc
/.
/usr
/usr/bin
/usr/bin/ipcalc
/usr/share
/usr/share/doc
/usr/share/doc/ipcalc
/usr/share/doc/ipcalc/contributors
/usr/share/doc/ipcalc/README
/usr/share/doc/ipcalc/copyright
/usr/share/doc/ipcalc/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/ipcalc.1.gz
/usr/share/man/man1/ipcalc_cgi.1.gz
/usr/share/images
/usr/share/images/ipcalc
/usr/share/images/ipcalc/ipcalc.gif
/usr/share/images/ipcalc/ipcalculator.png
/usr/lib
/usr/lib/cgi-bin
/usr/lib/cgi-bin/ipcalc

---

### Post by fwin on 2010-02-14
Thanks Riverside,

Now i understand what synaptic does.

---

### Post by bruno9779 on 2010-02-14
synaptic will remove everything (included .folders) if you issue the command:

```
sudo apt-get purge $packagename
```

---

### Post by mcduck on 2010-02-14
> **bruno9779 said:**
> synaptic will remove everything (included .folders) if you issue the command:

```
sudo apt-get purge $packagename
```

No, it won't.

If you purge a package (or select "Complete Removal" in Synaptic, apt will remove the *system-wide* configuration fiels for that package. But not user's personal configuration files located in their home directories.

This is because the personal configuration files cab often contain information and settings users might want to keep even if the original program is removed, and to protect user's configurations in case administrator needs to temporarily remove some program from the system.

For example if you had to remove Firefox and install it again, for example to solve a dpendency issue or broken package, you wouldn't want to loose all your bookmarks and saved passwords etc in the process. Not to mention how happy all the users would be on a multi-user system should such admin tasks destroy their personal information.

Because of this, the personal configuration files are on the user's responsibility to remove, should he want to do so. Not that they'd usually take any noticeable amount of disk space, as most are just small text files. ;)

---

