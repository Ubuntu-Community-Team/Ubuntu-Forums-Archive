---
title: "[SOLVED] Synaptic hangs up while wu-ftpd is being installed"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by &amp;wP*!) on 2008-02-18
Subject explains.

I am just trying to install wu-ftpd. But the installation never finishes. Here is the stdout of the details:

```
Preconfiguring packages ...
Selecting previously deselected package wu-ftpd.
(Reading database ... 96103 files and directories currently installed.)
Unpacking wu-ftpd (from .../wu-ftpd_2.6.2-28ubuntu1_i386.deb) ...
Setting up wu-ftpd (2.6.2-28ubuntu1) ...
Installing new version of config file /etc/ftpusers ...

```
... and Synaptic stays so... About the the ftpusers file:
```
utku:~> ls -l /etc/ftpusers
-rw-r--r-- 1 root root 132 2007-08-01 01:25 /etc/ftpusers

```
And it includes:
utku:~> more !:$
more /etc/ftpusers
```
# /etc/ftpusers: list of users disallowed FTP access. See ftpusers(5).

root
daemon
bin
sys
sync
games
man
lp
mail
news
uucp
nobody
utku:~> 

```

Does it have to do with that Synaptic is trying to update this file? Synaptic installation windows is still there. Nothing moves now.

What move next?

---

### Post by &amp;wP*!) on 2008-02-18
After having waited for 30 minutes, I have terminated the installation.

```
dpkg: error processing wu-ftpd (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 wu-ftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up wu-ftpd (2.6.2-28ubuntu1) ...
```

Now I will do it again...

---

### Post by &amp;wP*!) on 2008-02-18
Re-installation worked:
```
Preconfiguring packages ...
(Reading database ... 96168 files and directories currently installed.)
Preparing to replace wu-ftpd 2.6.2-28ubuntu1 (using .../wu-ftpd_2.6.2-28ubuntu1_i386.deb) ...
Unpacking replacement wu-ftpd ...
Setting up wu-ftpd (2.6.2-28ubuntu1) ...

```
Nothing changed...
It seems to have been solved.
Thanks folks, for your help!

---

