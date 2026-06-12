---
title: "file access problems"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by Unguidedone on 2011-06-27
so i did this :

**[SIZE=4]_Screening your system_[/SIZE]**

There is a package, tiger, which will screen your system for potential  security holes. While not complete it may be an excellent place to start  (tiger does not check your firewall for example).

For an overview of tiger see [man tiger]("http://www.penguin-soft.com/penguin/man/8/tiger.html") , scroll to the bottom and you will see a listing and brief description of the tests performed (modules).

Install by any means, *tiger john chkrootkit*
     Code:
     sudo apt-get install tiger john chkrootkit 
Run tiger from the command line with :
     Code:
     sudo tiger -H 
The -H flag will produce a very nice HTML document.

The command tigexp can be used to explain the results.

     Quote:
                                                 $ /usr/sbin/tigexp pass014w

The listed login ID is disabled in some manner ('*' in passwd field, etc),
but the login shell for the login ID is a valid shell (from /etc/shells
or the system equivalent).  A valid shell can potentially enable the
login ID to continue to be used.  The login shell should be changed to
something that doesn't exist, or to something like /bin/false.                                 
Tiger should give you some ideas on things to research. As always  there can be false positives so take care not to either panic or blindly  make system changes without understanding what you are doing and how to  undo your changes (ie make backups of system files before you edit  them).

got this read out from terminal :

julio@julio-ThinkCentre-M52:~$ sudo apt-get install tiger john chkrootkit
[sudo] password for julio: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  diff john-data
The following NEW packages will be installed:
  chkrootkit diff john john-data tiger
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1,865kB of archives.
After this operation, 5,923kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe diff all 1:3.0-1 [6,532B]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main chkrootkit i386 0.49-4 [309kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main john-data all 1.7.3.1-1 [649kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main john i386 1.7.3.1-1 [291kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe tiger i386 1:3.2.2-11ubuntu1 [610kB]
Fetched 1,865kB in 6s (269kB/s)                                                
Preconfiguring packages ...
Selecting previously deselected package diff.
(Reading database ... 196195 files and directories currently installed.)
Unpacking diff (from .../diff_1%3a3.0-1_all.deb) ...
Selecting previously deselected package chkrootkit.
Unpacking chkrootkit (from .../chkrootkit_0.49-4_i386.deb) ...
Selecting previously deselected package john-data.
Unpacking john-data (from .../john-data_1.7.3.1-1_all.deb) ...
Selecting previously deselected package john.
Unpacking john (from .../john_1.7.3.1-1_i386.deb) ...
Selecting previously deselected package tiger.
Unpacking tiger (from .../tiger_1%3a3.2.2-11ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up prelude-lml (1.0.0-1) ...
Starting Prelude LML: prelude-lmlinvoke-rc.d: initscript prelude-lml, action "start" failed.
dpkg: error processing prelude-lml (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up diff (1:3.0-1) ...
Setting up chkrootkit (0.49-4) ...
Setting up john-data (1.7.3.1-1) ...
Setting up john (1.7.3.1-1) ...
Setting up tiger (1:3.2.2-11ubuntu1) ...

Creating config file /etc/tiger/tigerrc with new version
Errors were encountered while processing:
 prelude-lml
E: Sub-process /usr/bin/dpkg returned an error code (1)
julio@julio-ThinkCentre-M52:~$ sudo tiger -H
Tiger UN*X security checking system
   Developed by Texas A&M University, 1994
   Updated by the Advanced Research Corporation, 1999-2002
   Further updated by Javier Fernandez-Sanguino, 2001-2007
   Covered by the GNU General Public License (GPL)

Configuring...
 
Will try to check using config for 'i686' running Linux 2.6.35-28-generic...
--CONFIG-- [con005c] Using configuration files for Linux 2.6.35-28-generic. Using
           configuration files for generic Linux 2.
Tiger security scripts *** 3.2.2, 2007.08.28.00.00 ***
Output Mode is HTML
21:49> Beginning security report for julio-ThinkCentre-M52.
21:49> Starting file systems scans in background...
21:49> Checking password files...
21:49> Checking group files...
21:49> Checking user accounts...
21:50> Checking .rhosts files...
21:50> Checking .netrc files...
21:50> Checking ttytab, securetty, and login configuration files...
21:50> Checking PATH settings...
21:50> Checking anonymous ftp setup...
21:50> Checking mail aliases...
21:50> Checking cron entries...
21:50> Checking 'services' configuration...
21:51> Checking NFS export entries...
21:51> Checking permissions and ownership of system files...
--CONFIG-- [con010c] Filesystem 'devtmpfs' used by 'none' is not recognised as a valid filesystem
21:51> Checking for indications of break-in...
--CONFIG-- [con010c] Filesystem 'devtmpfs' used by 'none' is not recognised as a valid filesystem
21:51> Performing rootkit checks...
21:51> Performing system specific checks...
/bin/grep: /etc/inittab: No such file or directory
22:15> Performing root directory checks...
22:15> Checking for secure backup devices...
22:15> Checking for the presence of log files...
22:15> Checking for the setting of user's umask...
22:15> Checking for listening processes...
22:15> Checking SSHD's configuration...
22:15> Checking the printers control file...
22:15> Checking ftpusers configuration...
22:15> Checking NTP configuration...
22:15> Waiting for filesystems scans to complete...
22:15> Filesystems scans completed...
22:15> Performing check of embedded pathnames...
22:17> Security report completed for julio-ThinkCentre-M52.
Security report is in `/var/log/tiger/security.report.julio-ThinkCentre-M52.110626-21:49.html'.
julio@julio-ThinkCentre-M52:~$ 


after when that was all done and good i went to check the file in :
/var/log/tiger/security.report.julio-ThinkCentre-M52.110626-21:49.html'.

and got this message:

[IMG]http://i913.photobucket.com/albums/ac340/Happy_Mask_Salesman/ohnooooooooooooooooooooooo.png[/IMG]

---

### Post by jtarin on 2011-06-27
Use an application that can view an .html file...I have chosen Firefox as an example and used "gksudo" because I need to be root opening an application that uses a GUI in Gnome.```
gksudo firefox /var/log/tiger/security.report.julio-ThinkCentre-M52.110626-21:49.html
```

---

