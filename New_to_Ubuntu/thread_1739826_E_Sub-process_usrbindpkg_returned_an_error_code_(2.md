---
title: "E: Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by mustafa ibrahim on 2011-04-26
oot@Mustafa-sr1:/home/mustafa# apt-get remove squid3
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
squid3
0 upgraded, 0 newly installed, 1 to remove and 96 not upgraded.
1 not fully installed or removed.
After this operation, 3,609kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 69462 files and directories currently installed.)
Removing squid3 ...
invoke-rc.d: unknown initscript, /etc/init.d/squid3 not found.
dpkg: error processing squid3 (--remove):
subprocess installed pre-removal script returned error exit status 100
update-rc.d: /etc/init.d/squid3: file does not exist
dpkg: error while cleaning up:
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
squid3
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Mustafa-sr1:/home/mustafa# apt-get purge squid3
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
squid3*
0 upgraded, 0 newly installed, 1 to remove and 96 not upgraded.
1 not fully installed or removed.
After this operation, 3,609kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 69462 files and directories currently installed.)
Removing squid3 ...
invoke-rc.d: unknown initscript, /etc/init.d/squid3 not found.
dpkg: error processing squid3 (--purge):
subprocess installed pre-removal script returned error exit status 100
update-rc.d: /etc/init.d/squid3: file does not exist
dpkg: error while cleaning up:
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
squid3
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Mustafa-sr1:/home/mustafa# rm -R /pathtofolder
rm: cannot remove `/pathtofolder': No such file or directory
root@Mustafa-sr1:/home/mustafa# rm- R/etc/squid
No command 'rm-' found, did you mean:
Command 'rmt' from package 'tar' (main)
Command 'rmt' from package 'dump' (universe)
Command 'rmf' from package 'nmh' (universe)
Command 'rmf' from package 'mailutils-mh' (universe)
Command 'rme' from package 'pvm-examples' (universe)
Command 'rmm' from package 'nmh' (universe)
Command 'rmm' from package 'mailutils-mh' (universe)
Command 'rm' from package 'coreutils' (main)
Command 'rm' from package 'safe-rm' (universe)
rm-: command not found
root@Mustafa-sr1:/home/mustafa# apt-get -R /pathtofolder
E: Command line option 'R' [from -R] is not known.
root@Mustafa-sr1:/home/mustafa# aptitude install squid3
The following partially installed packages will be configured:
squid3
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 96 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up squid3 (3.1.6-1.1ubuntu1.1) ...
/var/lib/dpkg/info/squid3.postinst: 70: cannot open /etc/squid3/squid.conf: No s uch file
dpkg: error processing squid3 (--configure):
subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
squid3
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:

root@Mustafa-sr1:/home/mustafa# /var/mustafa/dpkg/info
bash: /var/mustafa/dpkg/info: No such file or directory
root@Mustafa-sr1:/home/mustafa# rm -rf squid*
root@Mustafa-sr1:/home/mustafa# rm -rf squid*
root@Mustafa-sr1:/home/mustafa# rm -rf squid*
root@Mustafa-sr1:/home/mustafa# apt-get install squid
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
squid-common
Suggested packages:
squid-cgi logcheck-database resolvconf
The following NEW packages will be installed:
squid squid-common
0 upgraded, 2 newly installed, 0 to remove and 96 not upgraded.
1 not fully installed or removed.
Need to get 0B/1,119kB of archives.
After this operation, 2,572kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: unrecoverable fatal error, aborting:
statoverride file contains empty line
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@Mustafa-sr1:/home/mustafa#

---

### Post by mustafa ibrahim on 2011-04-26
hello all 
really i am new and it is a big problem for me please i need help

thanks to all

---

### Post by mustafa ibrahim on 2011-04-26
i still need help please i am in a big problem

---

### Post by TeoBigusGeekus on 2011-04-26
Since apt complaints about the /etc/init.d/squid3 missing, create it and try again:
```
sudo touch /etc/init.d/squid3
```
Then
```
sudo apt-get install --reinstall squid3
```

---

### Post by mustafa ibrahim on 2011-04-26
root@Mustafa-sr1:/home/mustafa# touch /etc/init.d/squid3
root@Mustafa-sr1:/home/mustafa# apt-get install --reinstall squid3
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 96 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up squid3 (3.1.6-1.1ubuntu1.1) ...
/var/lib/dpkg/info/squid3.postinst: 70: cannot open /etc/squid3/squid.conf: No s                                                                             uch file
dpkg: error processing squid3 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 squid3
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Mustafa-sr1:/home/mustafa#

---

### Post by mustafa ibrahim on 2011-04-26
so what i do?


root@Mustafa-sr1:/home/mustafa# dpkg dpkg --configure -a
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by TeoBigusGeekus on 2011-04-26
Create the other file as well
```
sudo touch /etc/squid3/squid.conf
```
and again
```
sudo apt-get install --reinstall squid3
```

---

### Post by mustafa ibrahim on 2011-04-26
dpkg dpkg --configure -a
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
root@Mustafa-sr1:/home/mustafa# touch /etc/squid3/squid/conf
touch: cannot touch `/etc/squid3/squid/conf': No such file or directory
root@Mustafa-sr1:/home/mustafa# apt-get install --reinstall squid3
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ntfs-3g : PreDepends: fuse-utils but it is not going to be installed
 ntfsprogs : Depends: fuse-utils (> 2.5.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@Mustafa-sr1:/home/mustafa# [http://ubuntuforums.org/showthread.php?p=10724144#post10724144](http://ubuntuforums.org/showthread.php?p=10724144#post10724144)

---

### Post by TeoBigusGeekus on 2011-04-26
> **mustafa ibrahim said:**
> 
root@Mustafa-sr1:/home/mustafa# touch /etc/squid3/squid/conf
touch: cannot touch `/etc/squid3/squid/conf': No such file or directory


This should have been
```
#touch /etc/squid3/squid.conf
```

Then do what apt advises you to do
```
#apt-get -f install
```

Finally try reinstalling squid3 again
```
#apt-get --reinstall squid3
```

---

### Post by jtarin on 2011-04-26
Try this command as a "normal user"....not root. ```
sudo apt-get remove squid3
```

---

### Post by mustafa ibrahim on 2011-04-26
sorry 
what i have to do


root@Mustafa-sr1:/home/mustafa# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  fuse-utils libfuse2 mount
Suggested packages:
  nfs-common
The following NEW packages will be installed:
  fuse-utils
The following packages will be upgraded:
  libfuse2 mount
2 upgraded, 1 newly installed, 0 to remove and 94 not upgraded.
1 not fully installed or removed.
Need to get 336kB of archives.
After this operation, 164kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main mount i386 2.17                                                                             .2-0ubuntu1.10.10.2 [174kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main libfuse2 i386 2                                                                             .8.4-1ubuntu1.3 [141kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main fuse-utils i386                                                                              2.8.4-1ubuntu1.3 [21.6kB]
Fetched 336kB in 5s (56.3kB/s)
dpkg: parse error, in file '/var/lib/dpkg/status' near line 12213 package 'fuse-                                                                             utils':
 duplicate value for `Package' field
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@Mustafa-sr1:/home/mustafa# apt-get --reinstall squid3
E: Invalid operation squid3
root@Mustafa-sr1:/home/mustafa# apt-get --reinstall squid3
E: Invalid operation squid3
root@Mustafa-sr1:/home/mustafa#

---

### Post by TeoBigusGeekus on 2011-04-26
Your cache seems corrupted. Do
```
sudo dpkg --clear-avail && sudo apt-get update
```
and then 
```
sudo apt-get -f install
```

---

### Post by cyjambo on 2011-11-28
> **TeoBigusGeekus said:**
> Your cache seems corrupted. Do
```
sudo dpkg --clear-avail && sudo apt-get update
```and then 
```
sudo apt-get -f install
```

Perfect, thanks for the solution! This was also my problem!!! :)

---

