---
title: "The following packages have unmet dependencies"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by adit on 2009-02-09
I don't remember exactly what I did with synaptic package manager last month.  I uninstalled some packages.
The problem now is there is no synaptic package manager in the Main menu.
```
~$ synaptic
bash: synaptic: command not found

```

```
$ sudo apt-get update
Hit http://in.archive.ubuntu.com gutsy Release.gpg
Ign http://in.archive.ubuntu.com gutsy/main Translation-en_IN
Ign http://in.archive.ubuntu.com gutsy/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com gutsy/universe Translation-en_IN
Hit http://in.archive.ubuntu.com gutsy Release
Hit http://in.archive.ubuntu.com gutsy/main Packages
Hit http://in.archive.ubuntu.com gutsy/restricted Packages
Hit http://in.archive.ubuntu.com gutsy/universe Packages
Reading package lists... Done

```

```
~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  synaptic: Depends: libapt-inst-libc6.6-6-1.1
            Depends: libapt-pkg-libc6.6-6-4.5
E: Broken packages

```

I want to install synaptic.  What should I do?

---

### Post by sydbat on 2009-02-09
Have you tried installing those missing items, then installing Synaptic?

---

### Post by handydan918 on 2009-02-09
You might try the following:

```
sudo apt-get install -f
```

If aptitude is installed, it often does a pretty good job of resolving these issues, or at least giving you a little more info about possible solutions. 

```
sudo aptitude install synaptic
```

---

### Post by adit on 2009-02-09
I tried the following

```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```
sudo aptitude install synaptic
sudo: aptitude: command not found

```

```
sudo apt-get install aptitude
The following packages have unmet dependencies:
aptitude: Depends: libapt-pkg-libc6.6-6-4.5
```

Packages providing libapt-pkg-libc6.6-6-4.5 (virtual package):
apt_0.7.6ubuntu14_i386.deb.  I downloaded and tried to install manually

```
sudo dpkg -i apt_0.7.6ubuntu14_i386.deb 
dpkg - warning: downgrading apt from 0.7.14ubuntu6 to 0.7.6ubuntu14.
(Reading database ... 100737 files and directories currently installed.)
Preparing to replace apt 0.7.14ubuntu6 (using apt_0.7.6ubuntu14_i386.deb) ...
Unpacking replacement apt ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing apt_0.7.6ubuntu14_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/locale/bg/LC_MESSAGES/apt.mo')
Errors were encountered while processing:
 apt_0.7.6ubuntu14_i386.deb


```

---

### Post by unutbu on 2009-02-09
libapt-inst-libc6.6-6-1.1 is a virtual package which is provided by apt-utils.
See [http://packages.ubuntu.com/gutsy/libapt-inst-libc6.6-6-1.1](http://packages.ubuntu.com/gutsy/libapt-inst-libc6.6-6-1.1)

libapt-pkg-libc6.6-6-4.5  is a virtual package which is provided by apt.
See [http://packages.ubuntu.com/gutsy/libapt-pkg-libc6.6-6-4.5](http://packages.ubuntu.com/gutsy/libapt-pkg-libc6.6-6-4.5)

So what is the output of:
```
sudo apt-get install --reinstall apt apt-utils
sudo apt-get install apt apt-utils

```
(If the first command works, the second command won't do anything)
If the above command(s) work, then try
```
sudo apt-get install synaptic
```

If they don't work, please post the output.

---

### Post by adit on 2009-02-09
```
sudo apt-get install --reinstall apt apt-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of apt is not possible, it cannot be downloaded.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
apt-utils: Depends: libapt-pkg-libc6.6-6-4.5
E: Broken packages

```

I remember last month, I installed apt (0.7.14ubuntu6) in my ubuntu gutsy.  That is actually an intrepid package.  I downloaded and installed that package manually.  Is this the cause of this problem?
The package for gutsy is apt (0.7.6ubuntu14)

---

### Post by Kellemora on 2009-02-10
Hi adit

It appears you just answered your own question!

You can't mix n match the repositories for different releases!

But don't feel bad, I did the same thing!
Downloaded something that was suggested and it was for the new release, not the stable LTS release.

Rather than try to fix the mess it made, it was faster and easier to reinstall the Distro from the CD.

Good Luck

TTUL
Gary

---

