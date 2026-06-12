---
title: "Accidentaly overwrote /bin/bash"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by Shindogo on 2010-07-18
Yeah. Whoops. My /bin/bash file is gone now, and using synaptic to try and reinstall bash gives me a series of errors:

```
Need to get 0B/646kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 161529 files and directories currently installed.)
Preparing to replace bash 4.1-2ubuntu3 (using .../bash_4.1-2ubuntu3_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: No such file or directory
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new pre-removal script: No such file or directory
dpkg: error processing /var/cache/apt/archives/bash_4.1-2ubuntu3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: No such file or directory
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bash_4.1-2ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So, anyone able to help me here?

---

### Post by bodhi.zazen on 2010-07-18
Try

```
sudo touch /bin/bash
sudo apt-get install --reinstall bash
```

---

### Post by Shindogo on 2010-07-18
Didn't work - same errors. My /bin/bash file is completely gone, I deleted the file that overwrote it.

---

### Post by Telengard C64 on 2010-07-18
This probably won't work, but maybe if you create a simlink to /bin/dash it might be enough for you to get bash from the repo.

Hmm, also maybe you could extract bash from the install CD. That might have a better chance of success.

Just a couple of

---

### Post by potat on 2010-07-18
What happens if you just replace /bin/bash? I attached my copy, gzipped. 
Get someone else to confirm the md5sum so you know it's not malicious code.
Gunzip the file and run "md5sum bash" to get the checksum.

Hope this helps.

EDIT: You can find this on the install CD or another Linux machine, of course.
Also, to use this you will have to give it execute permissions (chmod 755 bash) and set owner to root (sudo chown root:root bash) before copying it to /bin/bash.
Good luck!

---

### Post by new__buntu on 2010-07-18
I just md5sum'd it and got the following checksum: 8fe61c37f53f0af5d3bf988536b16182
It's the same as the one returned when I md5sum'd the bash file on my comp.

---

### Post by Shindogo on 2010-07-18
Using the bash file uploaded by potat (don't have the cd) worked, thanks very much :D

---

### Post by deniro on 2011-08-02
Hi
can somebody upload  ubuntu 10.04 64-bit  /bin/bash file for me.
I need to replace my /bin/bash as it seems to be corrupted.
thx
deniro--

---

### Post by 3rdalbum on 2011-08-02
This is from [http://packages.ubuntu.com;](http://packages.ubuntu.com;) I've extracted /bin/bash from the package, and then gzipped it because the forum software here requires it.

64-bit Lucid bash in gzip format.

---

### Post by deniro on 2011-08-02
Thx. Greatly appreciated. 
see my response in the other post.
deniro--

---

