---
title: "hplip problems!"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by hellomoto on 2009-01-07
heya, I recently thought I resolved issues when running the automatic compiler for hplip. But I constantly get the following error whilst installing. 

```


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo aptitude install --assume-yes libcupsys2'
Please wait, this may take several minutes...
 

RUNNING POST-PACKAGE COMMANDS
-----------------------------


RE-CHECKING DEPENDENCIES
------------------------
error: A required dependency 'cups (cups - Common Unix Printing System)' is still missing.

```

Please advise me as to what to do?
I have used hplip many a time b4 and never had so many problems!

---

### Post by Captain_tux on 2009-01-07
I've used that automatic compiler twice without any problems. I'd re-run it **paying very careful attention to the instructions, help file(s), and any instructions it spits out**...

It's so easy, even a caveman can do it.

---

### Post by unutbu on 2009-01-07
Hi, I'm not sure I can help you, but on the off-chance that I can, please post
```

apt-cache depends hplip | awk '/Depends/{print $2}' | xargs apt-cache policy
lsb_release -a

```

This will give us an idea of what hplip-related packages you have installed on your system.

---

### Post by hellomoto on 2009-01-07
i know this is y it doesn't make any sense. Cups is installed and I have the latest version of hplip, gone through the installer correctly but I still get this error:

```

rror: A required dependency 'cups (cups - Common Unix Printing System)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.

```

---

### Post by hellomoto on 2009-01-07
many thanx for ur help:

```

mark@mark-desktop:~/Desktop$ apt-cache depends hplip | awk '/Depends/{print $2}' | xargs apt-cache policy
adduser:
  Installed: 3.105ubuntu1
  Candidate: 3.105ubuntu1
  Version table:
 *** 3.105ubuntu1 0
        500 http://mirror.ox.ac.uk hardy/main Packages
        100 /var/lib/dpkg/status
coreutils:
  Installed: 6.10-3ubuntu2
  Candidate: 6.10-3ubuntu2
  Version table:
 *** 6.10-3ubuntu2 0
        500 http://mirror.ox.ac.uk hardy/main Packages
        100 /var/lib/dpkg/status
cupsys:
  Installed: 1.3.7-1ubuntu3.2
  Candidate: 1.3.7-1ubuntu3.2
  Version table:
 *** 1.3.7-1ubuntu3.2 0
        500 http://mirror.ox.ac.uk hardy-updates/main Packages
        100 /var/lib/dpkg/status
     1.3.7-1ubuntu3.1 0
        500 http://mirror.ox.ac.uk hardy-security/main Packages
     1.3.7-1ubuntu3 0
        500 http://mirror.ox.ac.uk hardy/main Packages
hplip-data:
  Installed: (none)
  Candidate: 2.8.2-0ubuntu8.1
  Version table:
     2.8.2-0ubuntu8.1 0
        500 http://mirror.ox.ac.uk hardy-updates/main Packages
        500 http://mirror.ox.ac.uk hardy-security/main Packages
     2.8.2-0ubuntu8 0
        500 http://mirror.ox.ac.uk hardy/main Packages
hplip-data:
  Installed: (none)
  Candidate: 2.8.2-0ubuntu8.1
  Version table:
     2.8.2-0ubuntu8.1 0
        500 http://mirror.ox.ac.uk hardy-updates/main Packages
        500 http://mirror.ox.ac.uk hardy-security/main Packages
     2.8.2-0ubuntu8 0
        500 http://mirror.ox.ac.uk hardy/main Packages
libc6:
  Installed: 2.7-10ubuntu4
  Candidate: 2.7-10ubuntu4
  Version table:
 *** 2.7-10ubuntu4 0
        500 http://mirror.ox.ac.uk hardy-updates/main Packages
        100 /var/lib/dpkg/status
     2.7-10ubuntu3 0
        500 http://mirror.ox.ac.uk hardy/main Packages
libcupsys2:
  Installed: 1.3.7-1ubuntu3.2
  Candidate: 1.3.7-1ubuntu3.2
  Version table:
 *** 1.3.7-1ubuntu3.2 0
        500 http://mirror.ox.ac.uk hardy-updates/main Packages
        100 /var/lib/dpkg/status
     1.3.7-1ubuntu3.1 0
        500 http://mirror.ox.ac.uk hardy-security/main Packages
     1.3.7-1ubuntu3 0
        500 http://mirror.ox.ac.uk hardy/main Packages
libjpeg62:
  Installed: 6b-14
  Candidate: 6b-14
  Version table:
 *** 6b-14 0
        500 http://mirror.ox.ac.uk hardy/main Packages
        100 /var/lib/dpkg/status
libsane:
  Installed: 1.0.19-1ubuntu3
  Candidate: 1.0.19-1ubuntu3
  Version table:
 *** 1.0.19-1ubuntu3 0
        500 http://mirror.ox.ac.uk hardy/main Packages
        100 /var/lib/dpkg/status
libsnmp15:
  Installed: 5.4.1~dfsg-4ubuntu4.2
  Candidate: 5.4.1~dfsg-4ubuntu4.2
  Version table:
 *** 5.4.1~dfsg-4ubuntu4.2 0
        500 http://mirror.ox.ac.uk hardy-updates/main Packages
        500 http://mirror.ox.ac.uk hardy-security/main Packages
        100 /var/lib/dpkg/status
     5.4.1~dfsg-4ubuntu4 0
        500 http://mirror.ox.ac.uk hardy/main Packages
libssl0.9.8:
  Installed: 0.9.8g-4ubuntu3.3
  Candidate: 0.9.8g-4ubuntu3.3
  Version table:
 *** 0.9.8g-4ubuntu3.3 0
        500 http://mirror.ox.ac.uk hardy-updates/main Packages
        500 http://mirror.ox.ac.uk hardy-security/main Packages
        100 /var/lib/dpkg/status
     0.9.8g-4ubuntu3 0
        500 http://mirror.ox.ac.uk hardy/main Packages
libusb-0.1-4:
  Installed: 2:0.1.12-8
  Candidate: 2:0.1.12-8
  Version table:
 *** 2:0.1.12-8 0
        500 http://mirror.ox.ac.uk hardy/main Packages
        100 /var/lib/dpkg/status
lsb-base:
  Installed: 3.2-4ubuntu1
  Candidate: 3.2-4ubuntu1
  Version table:
 *** 3.2-4ubuntu1 0
        500 http://mirror.ox.ac.uk hardy/main Packages
        100 /var/lib/dpkg/status
python:
  Installed: 2.5.2-0ubuntu1
  Candidate: 2.5.2-0ubuntu1
  Version table:
 *** 2.5.2-0ubuntu1 0
        500 http://mirror.ox.ac.uk hardy/main Packages
        100 /var/lib/dpkg/status
python:
  Installed: 2.5.2-0ubuntu1
  Candidate: 2.5.2-0ubuntu1
  Version table:
 *** 2.5.2-0ubuntu1 0
        500 http://mirror.ox.ac.uk hardy/main Packages
        100 /var/lib/dpkg/status
python-imaging:
  Installed: 1.1.6-1ubuntu5
  Candidate: 1.1.6-1ubuntu5
  Version table:
 *** 1.1.6-1ubuntu5 0
        500 http://mirror.ox.ac.uk hardy/main Packages
        100 /var/lib/dpkg/status
python-support:
  Installed: 0.7.5ubuntu1
  Candidate: 0.7.5ubuntu1
  Version table:
 *** 0.7.5ubuntu1 0
        500 http://mirror.ox.ac.uk hardy/main Packages
        100 /var/lib/dpkg/status
python:
  Installed: 2.5.2-0ubuntu1
  Candidate: 2.5.2-0ubuntu1
  Version table:
 *** 2.5.2-0ubuntu1 0
        500 http://mirror.ox.ac.uk hardy/main Packages
        100 /var/lib/dpkg/status
mark@mark-desktop:~/Desktop$ lsb_release -a

```

---

### Post by unutbu on 2009-01-07
There is a package called 'cups' which is a required dependency for hplip version 2.8.7-0ubuntu6 (for Intrepid). This package [is not listed]("http://packages.ubuntu.com/hardy/hplip") as a dependency for hplip 2.8.2-0ubuntu8.1 (for Hardy). 
Since the automatic compiler is complaining about the 'cups' package being missing, I wonder if somehow you have the version mismatch between the automatic compiler and the rest of your system.

What exactly is the command that you run to produce this error:

```
rror: A required dependency 'cups (cups - Common Unix Printing System)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.
```

---

### Post by hellomoto on 2009-01-07
I just run the automatic installer:

```

sh hplip-2.8.12.run

```

I thought I had cups installed.
I can't see a package just named "cups" in synaptic

---

### Post by unutbu on 2009-01-07
I might be wrong about the cups dependency problem. According to this page:
[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html), hplip-2.8.12.tar.gz
works with every Ubuntu version from Hoary 5.04 to Intrepid 8.10.

On the other hand, the instructions on that page do not mention 
```

sh hplip-2.8.12.run
```

because they use the tar.gz file instead of the .run file.
Perhaps try the tar.gz method described on that page?

---

### Post by hellomoto on 2009-01-07
yeh the .run file is for the automatic installer script. 
the . tar is for the manual install method - i am going to just try this now. I will let u know how i get on. Many thanks for your help so far.

---

### Post by hellomoto on 2009-01-07
I have got it to install! However Hplip can't find a driver for my printer:

Its a Deskjet D2560

---

### Post by unutbu on 2009-01-07
Did you try clicking on the hplip-install file (as gwad44 describes: [http://ubuntuforums.org/showthread.php?t=903662](http://ubuntuforums.org/showthread.php?t=903662)) or did you try setting up the printer using hp-setup: [http://hplipopensource.com/hplip-web/install/manual/hp_setup.html?](http://hplipopensource.com/hplip-web/install/manual/hp_setup.html?)

---

### Post by hellomoto on 2009-01-08
ok i finally sorted the problem and reinstalled hplip with the automatic installer. 

For some reason I have a problem with cups and have to restart it but when I do my printer shows up and works perfectly (got the test page to prove it)

So if you get the error I have please try running:

```

sudo /etc/init.d/cupsys restart

```

---

