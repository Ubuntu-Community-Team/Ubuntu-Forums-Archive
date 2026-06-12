---
title: "Trouble removing squid package"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by mustafa ibrahim on 2011-04-24
hey hello i am new here and new in linux please i need help



 apt-get purge squid squid-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package squid-common is not installed, so not removed
The following packages will be REMOVED:
  squid*
0 upgraded, 0 newly installed, 1 to remove and 95 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 69467 files and directories currently installed.)
Removing squid ...
Purging configuration files for squid ...
Purging logfiles ..
Removing the config-file ..
Remove the proxy cache in /var/spool/squid yourself!
dpkg: warning: while removing squid, directory '/var/spool/squid' not empty so n                                                                             ot removed.
dpkg: warning: while removing squid, directory '/etc/squid' not empty so not rem                                                                             oved.
Setting up squid3 (3.1.6-1.1ubuntu1.1) ...
/var/lib/dpkg/info/squid3.postinst: 70: cannot open /etc/squid3/squid.conf: No s                                                                             uch file
dpkg: error processing squid3 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 squid3
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Mustafa-sr1:/home/mustafa#
 

so what i have to do

---

### Post by pdwerryhouse on 2011-04-24
Try this before removing it:

```
touch /etc/squid3/squid.conf
```

---

### Post by mustafa ibrahim on 2011-04-25
root@Mustafa-sr1:/home/mustafa# apt-get purge squid squid-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package squid is not installed, so not removed
Package squid-common is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 95 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up squid3 (3.1.6-1.1ubuntu1.1) ...
/var/lib/dpkg/info/squid3.postinst: 70: cannot open /etc/squid3/squid.conf: No such file
dpkg: error processing squid3 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 squid3
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Mustafa-sr1:/home/mustafa# touch /etc/squid3/squid.conf
touch: cannot touch `/etc/squid3/squid.conf': No such file or directory

---

### Post by mustafa ibrahim on 2011-04-25
root@Mustafa-sr1:/home/mustafa# /etc/squid rm -f -R /var/spool/squid
bash: /etc/squid: is a directory

---

### Post by pdwerryhouse on 2011-04-25
Oops, I've been misreading the errors.

squid and squid-common *are* removed ...

The errors are coming from the squid3 package.

Are you trying to install or remove squid3?

---

### Post by collisionystm on 2011-04-25
> **mustafa ibrahim said:**
> hey hello i am new here and new in linux please i need help



 apt-get purge squid squid-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package squid-common is not installed, so not removed
The following packages will be REMOVED:
  squid*
0 upgraded, 0 newly installed, 1 to remove and 95 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 69467 files and directories currently installed.)
Removing squid ...
Purging configuration files for squid ...
Purging logfiles ..
Removing the config-file ..
Remove the proxy cache in /var/spool/squid yourself!
dpkg: warning: while removing squid, directory '/var/spool/squid' not empty so n                                                                             ot removed.
dpkg: warning: while removing squid, directory '/etc/squid' not empty so not rem                                                                             oved.
Setting up squid3 (3.1.6-1.1ubuntu1.1) ...
/var/lib/dpkg/info/squid3.postinst: 70: cannot open /etc/squid3/squid.conf: No s                                                                             uch file
dpkg: error processing squid3 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 squid3
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Mustafa-sr1:/home/mustafa#
 

so what i have to do

Very common. You will see this sort of error alot. Squid was kind enough to keep the config files encase you wanted to reinstall later. To remove them do

```

sudo rm -R /pathtofolder

```

I.e.

Sudo rm- R /etc/squid

---

### Post by wallander_kurt on 2011-04-26
Hi, I hope you have received solution by now.

But If not, you need to remove every reference to squid3 

for me the error message contained this,

0 packages upgraded, 0 newly installed, 2 to remove and 43 not upgraded.
Need to get 0B of archives. After unpacking 6873kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 92501 files and directories currently installed.)
Removing squid3 ...
invoke-rc.d: unknown initscript, /etc/init.d/squid3 not found.
dpkg: error processing squid3 (--remove):
 subprocess pre-removal script returned error exit status 100
update-rc.d: /etc/init.d/squid3: file does not exist
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing squid3-common ...
Errors were encountered while processing:
 squid3
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
root@inbu-labsquid:/var/lib/dpkg/info# aptitude install squid3
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been automatically kept back:
  apache2-utils apparmor apparmor-profiles clamav clamav-base exim4 exim4-base exim4-config exim4-daemon-light libaprutil1 libavcodec1d libavutil1d libc6-dev libpango1.0-0
  libpango1.0-common libtiff4 linux-libc-dev openssh-client openssh-server samba-common vmware-open-vm-tools-kmod-2.6.24-16-generic x11-xserver-utils
The following NEW packages will be automatically installed:
  squid3-common
The following packages have been kept back:
  anteater bsdutils clamav-freshclam dansguardian dhcp3-client dhcp3-common libc6 libc6-i686 libdbus-1-3 libldap-2.4-2 linux-image-virtual mount openssl samba smbclient ssh
  tzdata util-linux util-linux-locales vmware-open-vm-tools-common vsftpd
The following NEW packages will be installed:
  squid3-common
The following partially installed packages will be configured:
  squid3
0 packages upgraded, 1 newly installed, 0 to remove and 43 not upgraded.
Need to get 0B/207kB of archives. After unpacking 4461kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Selecting previously deselected package squid3-common.
(Reading database ... 91436 files and directories currently installed.)
Unpacking squid3-common (from .../squid3-common_3.0.STABLE1-1ubuntu1_all.deb) ...
Setting up squid3-common (3.0.STABLE1-1ubuntu1) ...
Setting up squid3 (3.0.STABLE1-1ubuntu1) ...
/var/lib/dpkg/info/squid3.postinst: 70: cannot open /etc/squid3/squid.conf: No such file
/var/lib/dpkg/info/squid3.postinst: 70: cannot open /etc/squid3/squid.conf: No such file
/var/lib/dpkg/info/squid3.postinst: 70: cannot open /etc/squid3/squid.conf: No such file
Creating Squid HTTP proxy 3.0 spool directory structure
FATAL: Unable to open configuration file: /etc/squid3/squid.conf: (2) No such file or directory,


I removed any squid* from 

/var/lib/dpkg/info/

/var/lib/dpkg/info# rm -rf squid*

then again tried installing squid3 

It worked. 

Hope this helps

---

### Post by mustafa ibrahim on 2011-04-26
root@Mustafa-sr1:/home/mustafa# apt-get remove squid3
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
root@Mustafa-sr1:/home/mustafa#  aptitude install squid3
The following partially installed packages will be configured:
  squid3
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 96 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up squid3 (3.1.6-1.1ubuntu1.1) ...
/var/lib/dpkg/info/squid3.postinst: 70: cannot open /etc/squid3/squid.conf: No s                                                                             uch file
dpkg: error processing squid3 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 squid3
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

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
hey really sorry i am new in linux 
i need help 

thanks all

---

### Post by wallander_kurt on 2011-05-17
/var/lib/dpkg/info/

 is a directory
 
First,
 
cd /var/lib/dpkg/info/
 
then
 
rm -rf squid*
 
Hope this helps
 
Regards

---

### Post by mrzero on 2011-05-29
Thank you wallander_kurt this worked for me here is what i do
cd /var/lib/dpkg/info/
 
then
 
rm -rf squid*
then
sudo apt-get clean all
sudo apt-get update
sudo apt-get update
sudo apt-get upgrade

"sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up squid3 (3.1.11-1) ...
"
Done....

that's all thanks again everybody:D

---

