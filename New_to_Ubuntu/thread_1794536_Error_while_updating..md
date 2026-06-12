---
title: "Error while updating."
date: 2011-07-01
forum: New to Ubuntu
---

### Post by Vege 4wd on 2011-07-01
Hi I was trying to update via apt-get and I got the following error.

```
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/58.3kB of archives.
After this operation, 319kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 248876 files and directories currently installed.)
Preparing to replace ubufox 0.9-0ubuntu1~mfs~lucid1 (using .../ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb) ...
Unpacking replacement ubufox ...
dpkg: error processing /var/cache/apt/archives/ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb (--unpack):
 trying to overwrite '/etc/xul-ext/ubufox.js', which is also in package xul-ext-ubufox 0:0.9-0ubuntu1~mfs~lucid1
Errors were encountered while processing:
 /var/cache/apt/archives/ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
aaron@aaron-laptop:~$ 

```

It appears that two packages have the same code.
Is there anyway to fix the problem?  Thanks in advance.

---

### Post by scatteredstones on 2011-07-01
I found a thread that appears to relate to your situation. Perhaps this will help.
[http://ubuntuforums.org/showthread.php?t=1789097](http://ubuntuforums.org/showthread.php?t=1789097)

---

### Post by sikander3786 on 2011-07-01
Please take look here, specifically the text under "Update 6/23/2011" at this page.

[http://ubuntu4beginners.blogspot.com/2011/06/firefox-5-stable-arrives-in-official.html](http://ubuntu4beginners.blogspot.com/2011/06/firefox-5-stable-arrives-in-official.html)

---

### Post by raja.genupula on 2011-07-01
try this 

```
sudo rm -rf /var/lib/apt/list/*

```

and then do update

---

### Post by Vege 4wd on 2011-07-01
Thank you the link gave me this script.

```
sudo apt-get purge xul-ext-ubufox
```

After running it I was able update without any conflicts.:biggrin::biggrin:

---

