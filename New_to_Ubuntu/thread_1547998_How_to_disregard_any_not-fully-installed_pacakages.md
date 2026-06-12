---
title: "How to disregard any not-fully-installed pacakages?"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by outleradam on 2010-08-07
I just went through a long, long, long process of getting my LIRC to work on kernel 2.6.35 and neither the SVN version of LIRC nor the apt-get version will fully install.  However, together, I can get them to work.  The drivers are supplied by the apt-get package and the rest is supplied by the SVN compiled source.   I'm just left with the inability to use apt-get now.   


```
root@xbmc-live:/# sudo apt-get install x11vnc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
x11vnc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up lirc (0.8.6-0ubuntu4.1) ...
invoke-rc.d: unknown initscript, /etc/init.d/udev not found.
dpkg: error processing lirc (--configure):
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 lirc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'm sure theres some sort of dpkg command to make the package manager disregard any previous installs which have occurred recently or are failing out..  Everything is in proper order except I cannot use apt-get

How can I get this error message to go away when I use apt-get install?

---

### Post by corrytonapple on 2010-08-07
I don't know if you should be in root terminal if you are going to act as root by putting "Sudo". Try it in the normal terminal. To remove partially installed packages, type in the regular terminal:
```

sudo apt-get autoclean

```
Hopefully it works.

---

### Post by outleradam on 2010-08-07
If it were that simple it would have been done a long time ago.  This is way outside the standard box with compiling partially from source and partially from apt-get.  

here's the problem... I had a package which was installed improperly, but it was working as desired with augmented help from another process.   So the database was reporting that there was a problem, when in fact there was no problem.  It was installed improperly from a broken package on my system and I corrected that by using svn source.   

After that, the database required maintenance.  The database is located in /var/lib/dpkg/status.  This file was reporting that I had a 1/2 configured package.

So to correct that:
```
gedit /var/lib/dpkg/status
```
then search and find the package in question.  In my case it was lirc.  So I searched and found lirc and it said:
```
Package: lirc
Status: install ok half-configured
```
so I changed that to:
```
 Package: lirc
Status: install ok installed
```

---

### Post by corrytonapple on 2010-08-07
You do know your Ubuntu. Ok here's a guide that might help: [Link]("http://ubuntuforums.org/showthread.php?t=140920")
Now go to Ubuntu Software Center. Type Ubuntu Tweak and download it. Launch it and go to Package Cleaner. Clean up those old, half installed, broken, packages.
How is this thread solved?

---

### Post by outleradam on 2010-08-10
Because that's what I was trying to do.

```

 Package: lirc
Status: install ok installed
```  Now that the problem is patched over, I can wait for the devs to release a working version where LIRC compiles.    The problem is that the old package wont work on the new kernel, and the SVN package drivers don't work on the newest kernel.  So, I got the package installed partially and augmented it with the SVN.  Then tricked apt into thinking everything was fine by adding the line above.

I'm running kernel 2.6.35-020635-generic.  Ubuntu is distributing 2.6.32-24-generic.

---

