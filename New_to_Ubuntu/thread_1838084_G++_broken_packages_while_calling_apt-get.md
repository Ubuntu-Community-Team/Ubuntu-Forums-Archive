---
title: "G++ broken packages while calling apt-get"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by Pixel_Outlaw on 2011-09-02
Hello,

I've recently installed Debian (ARM 8505 netbook version "Abrasive") everything is set up OK. My main issue is that I would like to compile some very basic C++ code.

I need to install some libraries but I am getting the following error message.

```

Reading package lists...
Building dependency tree...
Reading state information...
libcairo2 is already the newest version.
libcairo2 set to manually installed.
libclutter-1.0-0 is already the newest version.
libclutter-1.0-0 set to manually installed.
libclutter-gtk-0.10-0 is already the newest version.
libclutter-gtk-0.10-0 set to manually installed.
libcups2 is already the newest version.
libcups2 set to manually installed.
libc-bin is already the newest version.
libc-bin set to manually installed.
libc-dev-bin is already the newest version.
libc-dev-bin set to manually installed.
libc6-dev is already the newest version.
libc6-dev set to manually installed.
libc6 is already the newest version.
linux-libc-dev is already the newest version.
linux-libc-dev set to manually installed.
libcanberra-gtk0 is already the newest version.
libcanberra-gtk0 set to manually installed.
libcanberra0 is already the newest version.
libcanberra0 set to manually installed.
libcroco3 is already the newest version.
libcroco3 set to manually installed.
perl-modules is already the newest version.
perl-modules set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kolab-libcyrus-imap-perl : Conflicts: libcyrus-imap-perl
                            Conflicts: libcyrus-imap-perl21
                            Conflicts: libcyrus-imap-perl22
 libcunit1-ncurses : Conflicts: libcunit1 but 2.1-0.dfsg-9 is to be installed
 libcunit1-ncurses-dev : Conflicts: libcunit1-dev but 2.1-0.dfsg-9 is to be installed
 libcurl4-gnutls-dev : Conflicts: libcurl-dev
 libcurl4-openssl-dev : Conflicts: libcurl-dev
 libcyrus-imap-perl22 : Conflicts: libcyrus-imap-perl
                        Conflicts: libcyrus-imap-perl21
error broken packages

```

---

