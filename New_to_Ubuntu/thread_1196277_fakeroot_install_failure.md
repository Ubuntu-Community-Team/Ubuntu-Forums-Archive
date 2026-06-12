---
title: "fakeroot install failure :/"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by Cesaar on 2009-06-24
I was trying to install fakeroot as this is necessary for running virtualbox but I get the following error(s):

```
cesar@cesar-laptop:~$ sudo apt-get install fakeroot
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following NEW packages will be installed:
  fakeroot
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 114kB of archives.
After this operation, 455kB of additional disk space will be used.
Err http://ppa.launchpad.net jaunty/main fakeroot 1.12.4ubuntu1~ucd2~jaunty
  404 Not Found
Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/f/fakeroot/fakeroot_1.12.4ubuntu1~ucd2~jaunty_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

I tried --fix-missing with apt-get but same errors followed. It is also weird that is downloading from chromium-daily.. I'm not sure if that's right. can somebody get me some pointers please?:confused:

---

### Post by keplerspeed on 2009-06-24
Why are installing it manually? Just download the appropriate virtualbox .deb from here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

then double click on it and install! It will handle all dependencies!

It is usually much easier to let the package manager handle dependencies, there is no need to do it yourself unless you need an older package.

---

### Post by Cesaar on 2009-06-29
> **keplerspeed said:**
> Why are installing it manually? Just download the appropriate virtualbox .deb from here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

then double click on it and install! It will handle all dependencies!

It is usually much easier to let the package manager handle dependencies, there is no need to do it yourself unless you need an older package.

Thanks keplerspeed. I was able to install virtualbox by downloading the .deb file as you said.
Initially I was trying to download virtualbox from Add/Remove Applications, but regardless of how many times I tried, it wouldn't install the fakeroot dependency. So then I tried doing it from Terminal using **sudo apt-get install VirtualBox** but again, the fakeroot dependency would not be 'fetched'. Then that's when I decided to do **sudo apt-get install fakeroot** but it continued to fail. That was weird, but I'm glad I have VirtualBox back. :)

---

