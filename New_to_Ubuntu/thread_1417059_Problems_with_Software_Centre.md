---
title: "Problems with Software Centre"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by tomba1977 on 2010-02-26
I installed ubuntu 9.10 yesterday. I like it.

I needed a bandwidth monitor (my ISP has a 'fair usage' policy). 

I tried to download a program called bandwidthd but the installation failed. It seems to have messed up Software Centre. SC will not let me install or remove anything but thinks I'm still trying to install bandwidthd. 

Every program I try to install gets to 3% and fails with the message put up on-screen that 'the installation of bandwidthd may have to be done manually'.

Help!

---

### Post by sandyd on 2010-02-26
open up a terminal.
```

sudo rm /var/lib/dpkg/info/bandwidthd*
sudo dpkg --remove --force-remove-reinstreq bandwidthd 

```

---

### Post by tomba1977 on 2010-02-26
Thanks Carlee, but it didn't work...

I get:

tomba@tomba-desktop:~$ sudo apt-get --purge bandwidthd
E: Invalid operation bandwidthd
tomba@tomba-desktop:~$ 

Software Centre still thinks I'm trying to download it. Nothing I try to install will get beyond 3%.

Edit: This is also in Update Manager. I clicked 'update' to see if it did anything. It did. But the process failed and returned this message:

E: /var/cache/apt/archives/bandwidthd_2.0.1+cvs20071208-3_i386.deb: subprocess new pre-removal script returned error exit status 2

Does that shed any further light on the problem?

---

### Post by marshmallow1304 on 2010-02-26
Edit: Fixed above so post is unnecessary.

---

### Post by sandyd on 2010-02-26
> **tomba1977 said:**
> Thanks Carlee, but it didn't work...

I get:

tomba@tomba-desktop:~$ sudo apt-get --purge bandwidthd
E: Invalid operation bandwidthd
tomba@tomba-desktop:~$ 

Software Centre still thinks I'm trying to download it. Nothing I try to install will get beyond 3%.

Edit: This is also in Update Manager. I clicked 'update' to see if it did anything. It did. But the process failed and returned this message:

E: /var/cache/apt/archives/bandwidthd_2.0.1+cvs20071208-3_i386.deb: subprocess new pre-removal script returned error exit status 2

Does that shed any further light on the problem?
fixed typo.

---

### Post by tomba1977 on 2010-02-26
Marshamallow's suggestion got this:

Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  bandwidthd*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing bandwidthd (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bandwidthd
E: Sub-process /usr/bin/dpkg returned an error code (1)
tomba@tomba-desktop:~$ 

Bandwidthd is still in update manager. Still can't install anything!

---

### Post by tomba1977 on 2010-02-26
Carlee....

Sorry...I didn't know typo meant to look at your original suggestion. I saw it had changed.

I put it into terminal. It worked. I can now install progs again!

Well done and a big thank you.

:P

---

