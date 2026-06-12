---
title: "Installing a C compiler"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by lwilde on 2010-06-09
I've just installed Browser-Appliance 1.0.0 VMPlayer on a Windows system. This is my first experience with Linux.

I would like to install a C compiler.

When I type this in a Terminal window:

```
 
sudo apt-get install build-essential

```after entering a password, I get these errors:

```
 
Err http://us.archive.ubuntu.com breezy/main binutils 2.16.1-2ubuntu6
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com breezy/main linux-kernel-headers 2.6.11.2-0ubuntu13
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com breezy/main libc6-dev 2.3.5-1ubuntu12
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com breezy/main gcc-4.0 4.0.1-4ubuntu9
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com breezy/main gcc 4:4.0.1-3
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com breezy/main libstdc++6-4.0-dev 4.0.1-4ubuntu9
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com breezy/main g++-4.0 4.0.1-4ubuntu9
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com breezy/main g++ 4:4.0.1-3
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com breezy/main make 3.80-9
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com breezy/main dpkg-dev 1.13.10ubuntu4
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1-2ubuntu6_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.3.5-1ubuntu12_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/gcc-4.0_4.0.1-4ubuntu9_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/gcc_4.0.1-3_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/g++-4.0_4.0.1-4ubuntu9_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.0.1-3_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/make/make_3.80-9_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.10ubuntu4_all.deb  404 Not Found [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```When I type:
```
 
apt-get update

```I get:
```
 
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```I welcome advice!

---

### Post by bodhi.zazen on 2010-06-09
My guess is that your network connection is not properly configured. What network options did you use when you started the guest with VMPlayer ?

The error with "apt-get update" is because you did not say please

```
sudo apt-get update
```

---

### Post by lwilde on 2010-06-09
I don't know the answer offhand but will look into it, thanks for the suggestion.

---

### Post by eriktheblu on 2010-06-09
> Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) **breezy**/main binutils 2.16.1-2ubuntu6
Does that mean what I think it means?

---

### Post by ibuclaw on 2010-06-09
> **eriktheblu said:**
> Does that mean what I think it means?
It sure does. :)


lwilde, Ubuntu 5.10 is no longer supported officially, but the repositories are still available - just under a difference subdomain.

If you change:
```
http://us.archive.ubuntu.com
```
for
```
old-releases.ubuntu.com
```
In your /etc/apt/sources.list file, then all should download + install OK.

If you aren't in favour of manually editing all lines, this *might* do the job for you.
```
sudo sed -i 's/us.archive/old-releases/g' /etc/apt/sources.list
```

Regards
Iain

---

### Post by -kg- on 2010-06-09
> **eriktheblu said:**
> Does that mean what I think it means?

That was my thought when I read the errors, myself.

Did you install Ubuntu Lucid Lynx, or did you get an old Breezy installation disk from somewhere and install it from that?  Breezy is no longer supported, and the repos from that distro are no longer carried.

---

### Post by -kg- on 2010-06-09
+1, ibuclaw

What concerned me, however, is the OP's statement:

> This is my first experience with Linux.

This tells me that either he installed the wrong version, or got an old computer with that version still on it.

I'm thinking it might be a good idea to either install a more recent version or upgrade to a supported version, if he's just getting started.

But that's just me.

---

### Post by lwilde on 2010-06-09
I downloaded the OS from here:

[http://www.vmware.com/appliances/directory/80](http://www.vmware.com/appliances/directory/80)

I didn't notice how old it was. I will start over with something else. Thanks to all who responded.

---

### Post by eriktheblu on 2010-06-09
You might try this one [http://www.vmware.com/appliances/directory/542303]("http://www.vmware.com/appliances/directory/542303").

I don't use VMware myself, so I can't give great advice. 10.04 is the latest and recommended release of Ubuntu.

---

