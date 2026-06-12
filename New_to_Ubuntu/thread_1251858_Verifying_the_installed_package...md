---
title: "Verifying the installed package.."
date: 2009-08-28
forum: New to Ubuntu
---

### Post by karthick87 on 2009-08-28
I am not sure whether i have installed perl or not,how to veify it?

---

### Post by dk06 on 2009-08-28
> **getyourkarthick said:**
> I am not sure whether i have installed perl or not,how to veify it?
Check your logs...Your install/software log should show all the info you need to verify it installed correctly

---

### Post by karthick87 on 2009-08-28
How to view the logs?

---

### Post by MelDJ on 2009-08-28
cant v just go to synaptic and check? correct me if i am wrong

---

### Post by Partyboi2 on 2009-08-28
System>Admin>Synaptic>File>History will allow you to check what packages have been installed.

---

### Post by scorp123 on 2009-08-28
> **getyourkarthick said:**
> I am not sure whether i have installed perl or not,how to veify it? 
```
dpkg -l *perl*
```

If any package in that list has the status "ii" then it is installed. And of course: You can combine this with "grep" so all other statuses are filtered out:

```
dpkg -l *perl* | grep ii
```

If I do that here I get a loooong list, but the most important entries would be these:

```
...
...
ii  perl          5.10.0-19ubuntu1.1      Larry Wall's Practical Extraction and Report Language
ii  perl-base     5.10.0-19ubuntu1.1      minimal Perl system
ii  perl-modules  5.10.0-19ubuntu1.1      Core Perl modules
...
...
```

So output like the one above would strongly suggest that Perl 5.10 is installed and unless some disaster happened the files, binaries, libraries and what not should be installed and working.

A quickie check if the "perl" binary would be OK to accept commands is to ask it about its version:  **perl -version**

```
> perl -version

This is perl, v5.10.0 built for i486-linux-gnu-thread-multi

Copyright 1987-2007, Larry Wall

Perl may be copied only under the terms of either the Artistic License or the
GNU General Public License, which may be found in the Perl 5 source kit.

Complete documentation for Perl, including FAQ lists, should be found on
this system using "man perl" or "perldoc perl".  If you have access to the
Internet, point your browser at http://www.perl.org/, the Perl Home Page.
```

---

### Post by dk06 on 2009-08-28
[LEFT]                     [B][SIZE=1]to view logs:[/SIZE]
[/B]Click on System menu > Choose Administration > System Log:

**tail -f /var/log/messages**

> 

[B][SIZE=2][COLOR=Red]http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/[/COLOR][/SIZE]
[/B]

**View log files in Ubuntu Linux**

                 
                  [[IMG]http://figs.cyberciti.biz/3rdparty/ubuntu-logo.jpg[/IMG]]("http://www.cyberciti.biz/faq/category/ubuntu-linux/")
 **[COLOR=#ff0000]Q[/COLOR]**. Can you explain me log files in Ubuntu Linux and how do I view logs?
 **[COLOR=#009900]A[/COLOR]. **All logs are stored in /var/log directory under Ubuntu (and other Linux distro).
 **Linux Log files and usage**

 => **/var/log/messages** : General log messages
 => **/var/log/boot** : System boot log
 => **/var/log/debug** : Debugging log messages
 => **/var/log/auth.log** : User login and authentication logs
 => **/var/log/daemon.log** : Running services such as squid, ntpd and others log message to this file
 => **/var/log/dmesg** : Linux kernel  ring buffer log
 => **/var/log/dpkg.log** : All binary package log includes package installation and other information
 => **/var/log/faillog** : User failed login log file
 => **/var/log/kern.log** : Kernel log file
 => **/var/log/lpr.log** : Printer log file
 => **/var/log/mail.*** : All mail server message log files
 => **/var/log/mysql.*** : MySQL server log file
 => **/var/log/user.log** : All userlevel logs
 => **/var/log/xorg.0.log** : X.org log file
 => **/var/log/apache2/*** : Apache web server log files directory
 => **/var/log/lighttpd/*** : Lighttpd web server log files directory
 => **/var/log/fsck/*** : fsck command log
 => **/var/log/apport.log** : Application crash report / log file
[/LEFT]

---

### Post by hal10000 on 2009-08-28
In almost every linux disrtibution perl is installed by default.
Verify it by typing [COLOR="Red"]perl -v[/COLOR] in a terminal window.
The output should be like this:
> This is perl, v5.10.0 built for x86_64-linux-gnu-thread-multi

Copyright 1987-2007, Larry Wall

Perl may be copied only under the terms of either the Artistic License or the
GNU General Public License, which may be found in the Perl 5 source kit.

Complete documentation for Perl, including FAQ lists, should be found on
this system using "man perl" or "perldoc perl".  If you have access to the
Internet, point your browser at [http://www.perl.org/](http://www.perl.org/), the Perl Home Page.
With Synaptic (or another package manager) you can list (and install/remove) any available packages.

---

### Post by credobyte on 2009-08-28
```
dainis@ubuntu:~$ **sudo aptitude show perl**
[sudo] password for dainis: 
Package: perl
**State: installed**
Automatically installed: no
Version: 5.10.0-19ubuntu1.1
Priority: standard
Section: perl
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 14.0M
Depends: perl-base (= 5.10.0-19ubuntu1.1), perl-modules (>= 5.10.0-19ubuntu1.1),
         libc6 (>= 2.4), libdb4.6, libgdbm3
Recommends: netbase
Suggests: perl-doc, libterm-readline-gnu-perl | libterm-readline-perl-perl
Conflicts: libdigest-md5-perl (< 3.07-1), libdigest-sha-perl (< 5.45-1),
           libmime-base64-perl (< 3.07-1), libstorable-perl (< 2.15-1),
           libtime-hires-perl (< 1.86-1), libtime-piece-perl (< 1.12-1),
           perl-doc (< 5.10.0-1)
Replaces: libarchive-tar-perl (<= 1.38-2), libdigest-md5-perl,
          libdigest-sha-perl, libmime-base64-perl, libmodule-corelist-perl (<
          2.14-2), libstorable-perl, libtime-hires-perl, libtime-piece-perl,
          perl-base (< 5.8.8-1), perl-doc (< 5.8.0-1), perl-modules (< 5.8.1-1)
Provides: data-dumper, libdigest-md5-perl, libdigest-sha-perl,
          libmime-base64-perl, libstorable-perl, libtime-hires-perl,
          libtime-piece-perl, perl5
Description: Larry Wall's Practical Extraction and Report Language
 An interpreted scripting language, known among some as "Unix's Swiss Army
 Chainsaw". 
 
 Perl is optimised for scanning arbitrary text files and system administration.
 It has built-in extended regular expression matching and replacement, a
 data-flow mechanism to improve security with setuid scripts and is extensible
 via modules that can interface to C libraries.
```

---

