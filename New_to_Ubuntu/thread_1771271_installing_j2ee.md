---
title: "installing j2ee"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-05-30
I want to install j2ee.
I downloaded .bin file 
and did 
sudo +x chmod *.bin

then
./j2eesdk-1_4_03-linux.bin
but I came up with this error:
./j2eesdk-1_4_03-linux.bin: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
How to get that file?
I also have to give my friends j2ee and they don't have internet access. What should I do??
I have installed netbeans. After installing j2ee, will it automatically support the j2ee libraries?? or is there something else to do?
Why isn't there a really simple way to install things like: setup.exe or setup.deb?

Another question:
For some .deb files I gave to friends, they say that some libraries were missing. How do I export libraries from my Ubuntu to theirs??

---

### Post by yeats on 2011-05-30
Try:

```
sudo apt-get install build-essential
```

(which installs a lot of useful tools for compiling software from source), then run the .bin script again.

---

### Post by RobikShrestha on 2011-05-30
Ran into another problem by doing as suggested:

robik@dhcppc0:~/Downloads/j2ee$ ./j2eesdk-1_4_03-linux.bin
./j2eesdk-1_4_03-linux.bin: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
robik@dhcppc0:~/Downloads/j2ee$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 100
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by yeats on 2011-05-30
Looks like your package manager is a bit borked.  Try doing:

```
sudo apt-get -f install
```

then 

```
sudo dpkg --configure -a
```

Post the output in CODE tags (by clicking the # when composing).

---

### Post by RobikShrestha on 2011-05-30
robik@dhcppc0:~$ sudo apt-get -f install
[sudo] password for robik: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
mysql stop/waiting
invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 100
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
          Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
robik@dhcppc0:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server




About j2ee, I installed it by downloading the required library. But I do not know how to setup the class path please help!
And will Netbeans automatically detect the new libraries of j2ee?

---

### Post by yeats on 2011-05-30
Okay, now try:

```
sudo apt-get purge mysql-server
sudo apt-get autoremove
sudo apt-get clean
```

If that doesn't cause an error, then do:

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install mysql-server build-essential
```

Then continue with the j2ee installation.

You will probably get better answers on the j2ee details in the programming section of the forums, FYI.

---

### Post by RobikShrestha on 2011-05-30
It caused an error:

robik@dhcppc0:~$ sudo apt-get purge mysql-server
[sudo] password for robik: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-server is not installed, so not removed
The following packages were automatically installed and are no longer required:
  mysql-server-5.1 mysql-server-core-5.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
mysql stop/waiting
invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 mysql-server-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
robik@dhcppc0:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mysql-server-5.1 mysql-server-core-5.1
0 upgraded, 0 newly installed, 2 to remove and 53 not upgraded.
1 not fully installed or removed.
After this operation, 25.5 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 192483 files and directories currently installed.)
Removing mysql-server-5.1 ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.
dpkg: error processing mysql-server-5.1 (--remove):
 subprocess installed pre-removal script returned error exit status 100
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Configuring mysql-server-5.1
----------------------------

While not mandatory, it is highly recommended that you set a password for the MySQL administrative "root" 
user.
[More] 


If this field is left blank, the password will not be changed.

New password for the MySQL "root" user: 


invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 100
Removing mysql-server-core-5.1 ...
Processing triggers for man-db ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Errors were encountered while processing:
 mysql-server-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
robik@dhcppc0:~$ sudo apt-get clean

---

### Post by jtarin on 2011-05-30
Your missing file is included and supplied by 

libstdc++2.10-glibc2.2
Which can be found:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)**_enter your own version name here_**/i386/libstdc++2.10-glibc2.2/download

---

### Post by RobikShrestha on 2011-05-30
Well thanks. I had already downloaded it.
I removed mysql via synaptic manager. Actually I have xampp for my mysql server and I do not require another mysql. I have asked about j2ee in programming section. Thanks for help. I would be grateful if u could also help in j2ee problem.

---

