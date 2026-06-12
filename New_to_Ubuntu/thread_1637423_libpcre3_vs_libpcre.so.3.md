---
title: "libpcre3 vs libpcre.so.3"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by notquite on 2010-12-04
Hi folks,
I'm a Linux newbie and I'm trying to install an application that requires a couple of libraries that my hosted Ubuntu VPS server doesn't seem to have installed - one being /lib/libpcre.so.3 (another is libcurl.so.4).

I've tried to use symlink to libpcre3 and libcurl3, respectively, but checking with the command 'ldd <the app>' from the app's folder shows the libraries as not found. Maybe these libraries are not compatible?

The VPS has a Plesk control panel with Virtuozzo and I can't find libpcre.so.3 or libcurl.so.4 in the installed or available packages to install.

Any ideas?
Best,
Keith..

---

### Post by smo0th on 2010-12-04
what about 
sudo apt-get install libpcre3 libpcre3-dev libcurl4 libcurl4-dev
?

---

### Post by notquite on 2010-12-04
smo0th,
Thanks for the response and sorry - I see that my question was unclear.

The server has libpcre and libcurl3 installed. I've tried to use symlinks to these instead of the required libpcre.so.3 and libcurl.so.4 libraries without success. I was hoping these were package updates but it seems they are incompatible. 

Unfortunately, neither apt-get or my VPS Plesk/Virtunozzo package manager seem to have the required libraries available.

---

### Post by smo0th on 2010-12-04
probably your application needs the libraries for compiling, libpcre3 libpcre3-dev are different packages, are you sure you have installed the -dev versions?

---

### Post by notquite on 2010-12-05
The normal and -dev versions are installed but I can only symlink to one or the other. 

The real issue is that I can't find confirmation anywhere that these libraries libpcre3 and libcurl3 are Ubuntu-specific updates of libpcre.so.3 and libcurl.so.4 or something completely different.

Is there any Ubuntu resource that shows these mappings?

---

### Post by notquite on 2010-12-08
OK, having now learned that Linux has multiple library locations (newbie!), it turns out that I was looking in the wrong place: /lib/libpcre3 rather than /usr/lib/libpcre.so.3. So, a symlink solved the libpcre problem: ln -s /usr/lib/libpcre.so.3 libpcre.so.0

I also found /usr/lib/libcurl.so.3 but my app requires libcurl.so.4 and doesn't want to work with a symlink. I've added the Ubuntu Dapper-update repository to my apt-get source.list but the libcurl libraries stay as-is. 

The server is a hosted VPS, so I can't upgrade the Ubuntu version. So, I need to find what version upgrade of libcurl I need to get libcurl.so.4 - and how best to install this, along with any dependencies.

Is it safe to add a later distro's repository to my sources.list (in which case, how do I find which distro has the right libcurl library set) or should I install the latest version of curl from a [[COLOR="Blue"]download[/COLOR]]("http://curl.haxx.se/") and then work through all the dependencies manually?
Thanks,
Keith..

---

