---
title: "No /sbn/udev found running: none killed."
date: 2009-10-10
forum: New to Ubuntu
---

### Post by appoi on 2009-10-10
hi guys i am using ubuntu 9.04 jaunty and i am newbie.... i have reloading problem can anyone help me with this.....................

*Reloding kernel even manager  No /sbn/udev found running: none killed.

invoke-rc.d: initdcript udev, action 'reload' failed.
dpkg: error processing fuse-utils (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problem prevent configuration of gvs-fuse:
gvs_fuse depends on fuse-utils; however:
package fuse--utils is not configure yet.
dpkg: error processing gvfs-fuse (--configure):
dependency problem - leaving unconfigureed
No apport report written because the error message indicates is following error from previous failure
                        error where encountered while processing:
fuse-utils
gvfs-fuse
:E Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by tarps87 on 2009-10-15
When do you see the error?

Looking at the output it is a installed package problem, try
```
sudo apt-get install -f
```
If this doesn't work then
```
sudo dpkg --configure -a
```

---

### Post by appoi on 2009-10-20
try ready still got error

dpkg: parse error, in file `/var/lib/dpkg/available' near line 2 package `indicator-messages':
 value for `status' field not allowed in this context

---

### Post by tarps87 on 2009-10-20
Try
```
sudo apt-get purge fuse-utils
```
It sounds like there was a problem when installing fuse, this should remove the package and then you can reinstall it.

---

### Post by appoi on 2009-10-20
root@gnetbook:/home/user# sudo apt-get purge fuse-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fuse-utils* gvfs-fuse* ntfs-3g* ntfsprogs*
0 upgraded, 0 newly installed, 4 to remove and 4 not upgraded.
After this operation, 1106kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 2 package `indicator-messages':
 value for `status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)

p/s: after update cannot install upgrade....

---

### Post by tarps87 on 2009-10-20
Ok, can you post the output of
```
ls -l /var/lib/dpkg/available/
```

---

### Post by appoi on 2009-10-20
sure!!

root@gnetbook:/home/user# ls -l /var/lib/dpkg/available/
ls: cannot access /var/lib/dpkg/available/: Not a directory

---

### Post by tarps87 on 2009-10-20
That does answer my question, I don't currently have a Ubuntu machine infront of me. The quick way maybe to move the file
```
sudo mv /var/lib/dpkg/available ~/
```
Now try to update or install something, if this doesn't work
```
sudo mv ~/available /var/lib/dpkg/
```
Now

```
sudo gedit /var/lib/dpkg/available
```
And post the contents, I will probably need to check this against mine later

---

### Post by appoi on 2009-10-20
just follow your instruction.... 

Could not open the file /var/lib/dpkg/available using the Unicode (UTF-8) character coding.
Please check that you are not trying to open a binary file.
Select a different character coding from the menu and try again.

when retry also the same message appear....

---

### Post by appoi on 2009-10-21
when try upgrade and install (any)packages it's showing same error....

dpkg: parse error, in file `/var/lib/dpkg/available' near line 2 package `indicator-messages':
 value for `status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)

gosh...

---

### Post by tarps87 on 2009-10-21
Did you try moving the file?
It appears to be corupt, if you move it, it should recreate it

---

### Post by appoi on 2009-10-21
sorry, i am newbie.. can u guide me recreate it....thanks

---

### Post by tarps87 on 2009-10-21
Did you try this?
sudo mv /var/lib/dpkg/available ~/

This moves the file, now running an update it should be recreated.

---

### Post by appoi on 2009-10-21
root@gnetbook:/home/user# sudo mv /var/lib/dpkg/available ~/
root@gnetbook:/home/user# sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Reading package lists... Done

then.. sudo apt-get upgrade

root@gnetbook:/home/user# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libsndfile1 python-zopeinterface tzdata tzdata-java
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1176kB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@gnetbook:/home/user# 

now can update but cannot upgrade...

---

### Post by tarps87 on 2009-10-21
In that case it would recreate the file.
{code]sudo echo "" > /var/lib/dpkg/available{/code]

This will create an empty file with a new line, now upgrade

---

### Post by appoi on 2009-10-21
helo friend it's working now...thanks... thanks for your help.

---

