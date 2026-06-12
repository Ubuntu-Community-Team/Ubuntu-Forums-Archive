---
title: "Trying to get &quot;stdio.h&quot;"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by grandsatrap on 2009-01-01
Hi, I am trying to compile a C program in Ubuntu, but I can't find stdio.h.  There is nothing like this in /usr/include

Someone online said that I should do "sudo apt-get install build-essential"
This now hangs, saying that I have to insert my server CDROM
"Media change: please insert the disc labeled  'Ubuntu-Server 7.04 ..."  I don't have this CDROM (maybe I lost it) and I don't know how to make another one. I tried burning the ISO image to CD, but apparently the ISO image is not what apt-get wants.

So, then I found a posting saying run "sudo vi /etc/apt/sources.list" and comment out the CDROM line.
I did this and now get these errors:

> WARNING: The following packages cannot be authenticated!
  libc6-dev libstdc++6-4.1-dev g++-4.1 g++ dpkg-dev build-essential
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libc6-dev 2.5-0ubuntu14
 404 Not Found [IP: 91.189.88.46 80]
...
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
...


Also, now when I try and change sources-list to access the CDROM it still won't.

So, I'm totally stuck. I don't know why it says that these packages cannot be authenticated. I also don't know why it can't find them.

(Feel free to move this to the correct forum. Thanks)

---

### Post by taurus on 2009-01-01
Double bad news for you.  First, feisty has expired and the repos have been moved.

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

Second, build-essential is on the CD so if you want to install it, best to get the alternate CD and install the build-essential package from there.

[http://old-releases.ubuntu.com/releases/feisty/](http://old-releases.ubuntu.com/releases/feisty/)

---

### Post by mcduck on 2009-01-01
The download doesn't work because the servers for Feisty (Ubuntu 7.04) have already been shut down. The support for that version ended in October 2008.

I suggest getting a more up-to-date version of Ubuntu, if possible. Otherwise download the alternate-CD or server-CD for your version and use that to install the build-essentials package.

---

