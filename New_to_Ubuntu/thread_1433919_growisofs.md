---
title: "growisofs"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by chuckycheese on 2010-03-19
I am trying to use k3b to copy media. I tells me I need growisofs>=5.2 to write DL media.  growisofs - version is 1.1.  I have tried apt-get install growisofs, and it doesn't work. I have found a file growisofs.c v.7 but I don't know what to do with it.

---

### Post by srs5694 on 2010-03-19
On my Ubuntu 9.10 system, growisofs is part of the dvd+rw-tools package, which is at version 7.1-4. See if that package is installed on your system, and if it's not, or if it's old, install or upgrade it. If you're running a very old version of Ubuntu, you may need to jump through some extra hoops to upgrade your version of growisofs, though.

It's possible that you've got a locally-compiled version of growisofs. Type "whereis growisofs" to locate it, then use "dpkg -S" to see if it's owned by any package. (Note that's an *uppercase* -S!) For instance, on my system:

```

$ whereis growisofs
growisofs: /usr/bin/growisofs /usr/share/man/man1/growisofs.1.gz
$ dpkg -S /usr/bin/growisofs 
dvd+rw-tools: /usr/bin/growisofs

```

If the dpkg -S command returns the message "{filename} not found", then the version you've got isn't owned by any package. You may want or need to delete it manually, especially if it's stored in the /usr/local directory tree. That directory holds locally-compiled software, meaning that somebody probably downloaded an old source package, compiled it, and installed it without using Ubuntu's package management system.

---

### Post by chuckycheese on 2010-03-19
Ok, now I have the newest version:

* growisofs by <appro@fy.chalmers.se>, version 7.1,
  front-ending to genisoimage: genisoimage 1.1.9 (Linux)
Hiwever, in k3b Tools>Copy Medium>  DL to DL I get error message:
Growisofs>=5.20 is needed to write Double Layer DVD+R

I have uninstalled and reinstalled k3b, with no change.

btw I am running Ubuntu 9.10

---

### Post by srs5694 on 2010-03-19
Are you saying that k3b still doesn't work? If so, try the following:


[list=1]
[*]Type "whereis growisofs" at a shell prompt. If it locates any growisofs binary (probably in /usr/local/bin, but perhaps elsewhere) other than the one you've just installed, delete the extra one.
[*]If the above doesn't work, log out of your session and log back in.
[*]If step #2 doesn't work, reboot.
[/list]

---

### Post by chuckycheese on 2010-03-19
Okay:

$ whereis growisofs
growisofs: /usr/bin/growisofs /usr/share/man/man1/growisofs.1.gz

It is only where it is supposed to be. However, I found

[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/455570](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/455570)

that pretty much addresses the problem.  The fix is in release 1.90 which was uploaded to Ubuntu on 03-05-10, which apparently hasn't made it to the repository as the version in the repo is 1.68.0~alpha 3.  So unless I can figure out how to compile the code and manually install it (haha), I guess I will have to wait.

---

