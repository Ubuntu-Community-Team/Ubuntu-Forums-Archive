---
title: "updates Fail installation fails 10.10"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by kindafunnylookin on 2010-11-05
Every day UPDATE MANAGER shows up with it's corrections and additions and whatever. They are never installed, after each attempt I get the message:
     [B]Package Installation Failed
       [/B]The installation or removal of a software package failed
      ```
installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 239462 files and directories currently installed.) 
Preparing to replace sysvinit-utils 2.87dsf-4ubuntu18 (using .../sysvinit-utils_2.87dsf-4ubuntu19_i386.deb) ... 
Unpacking replacement sysvinit-utils ... 
Preparing to replace sysv-rc 2.87dsf-4ubuntu18 (using .../sysv-rc_2.87dsf-4ubuntu19_all.deb) ... 
Unpacking replacement sysv-rc ... 
Preparing to replace initscripts 2.87dsf-4ubuntu18 (using .../initscripts_2.87dsf-4ubuntu19_i386.deb) ... 
Unpacking replacement initscripts ... 
Preparing to replace libcups2 1.4.4-6ubuntu2.1 (using .../libcups2_1.4.4-6ubuntu2.2_i386.deb) ... 
Unpacking replacement libcups2 ... 
Preparing to replace libcupscgi1 1.4.4-6ubuntu2.1 (using .../libcupscgi1_1.4.4-6ubuntu2.2_i386.deb) ... 
Unpacking replacement libcupscgi1 ... 
Preparing to replace libcupsdriver1 1.4.4-6ubuntu2.1 (using .../libcupsdriver1_1.4.4-6ubuntu2.2_i386.deb) ... 
Unpacking replacement libcupsdriver1 ... 
Preparing to replace libcupsimage2 1.4.4-6ubuntu2.1 (using .../libcupsimage2_1.4.4-6ubuntu2.2_i386.deb) ... 
Unpacking replacement libcupsimage2 ... 
Preparing to replace libcupsmime1 1.4.4-6ubuntu2.1 (using .../libcupsmime1_1.4.4-6ubuntu2.2_i386.deb) ... 
Unpacking replacement libcupsmime1 ... 
Preparing to replace libcupsppdc1 1.4.4-6ubuntu2.1 (using .../libcupsppdc1_1.4.4-6ubuntu2.2_i386.deb) ... 
Unpacking replacement libcupsppdc1 ... 
Preparing to replace cups-common 1.4.4-6ubuntu2.1 (using .../cups-common_1.4.4-6ubuntu2.2_all.deb) ... 
Unpacking replacement cups-common ... 
Preparing to replace cups-bsd 1.4.4-6ubuntu2.1 (using .../cups-bsd_1.4.4-6ubuntu2.2_i386.deb) ... 
Unpacking replacement cups-bsd ... 
Preparing to replace cups-client 1.4.4-6ubuntu2.1 (using .../cups-client_1.4.4-6ubuntu2.2_i386.deb) ... 
Unpacking replacement cups-client ... 
Preparing to replace cups-ppdc 1.4.4-6ubuntu2.1 (using .../cups-ppdc_1.4.4-6ubuntu2.2_i386.deb) ... 
Unpacking replacement cups-ppdc ... 
Preparing to replace cups 1.4.4-6ubuntu2.1 (using .../cups_1.4.4-6ubuntu2.2_i386.deb) ... 
cups stop/waiting 
Unpacking replacement cups ... 
Preparing to replace libfreetype6-dev 2.4.2-2 (using .../libfreetype6-dev_2.4.2-2ubuntu0.1_i386.deb) ... 
Unpacking replacement libfreetype6-dev ... 
Preparing to replace libfreetype6 2.4.2-2 (using .../libfreetype6_2.4.2-2ubuntu0.1_i386.deb) ... 
Unpacking replacement libfreetype6 ... 
Preparing to replace libpurple-bin 1:2.7.3-1ubuntu3 (using .../libpurple-bin_1%3a2.7.3-1ubuntu3.1_all.deb) ... 
Unpacking replacement libpurple-bin ... 
Preparing to replace libpurple0 1:2.7.3-1ubuntu3 (using .../libpurple0_1%3a2.7.3-1ubuntu3.1_i386.deb) ... 
Unpacking replacement libpurple0 ... 
Preparing to replace xserver-xorg-video-intel 2:2.12.0-1ubuntu5 (using .../xserver-xorg-video-intel_2%3a2.12.0-1ubuntu5.1_i386.deb) ... 
Unpacking replacement xserver-xorg-video-intel ... 
Processing triggers for man-db ... 
Processing triggers for ureadahead ... 
ureadahead will be reprofiled on next reboot 
Processing triggers for ufw ... 
Processing triggers for doc-base ... 
Processing 2 changed doc-base file(s)... 
Registering documents with scrollkeeper... 
Setting up postfix (2.7.1-1) ... 
 
Postfix configuration was not changed.  If you need to make changes, edit 
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration 
values, see postconf(1). 
 
After modifying main.cf, be sure to run '/etc/init.d/postfix reload'. 
 
Running newaliases 
newaliases: warning: valid_hostname: numeric hostname: 9 
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: 9 
dpkg: error processing postfix (--configure): 
 subprocess installed post-installation script returned error exit status 75 
No apport report written because MaxReports is reached already
Setting up sysvinit-utils (2.87dsf-4ubuntu19) ... 
Setting up sysv-rc (2.87dsf-4ubuntu19) ... 
Setting up initscripts (2.87dsf-4ubuntu19) ... 
Setting up libcups2 (1.4.4-6ubuntu2.2) ... 
Setting up libcupscgi1 (1.4.4-6ubuntu2.2) ... 
Setting up libcupsdriver1 (1.4.4-6ubuntu2.2) ... 
Setting up libcupsimage2 (1.4.4-6ubuntu2.2) ... 
Setting up libcupsmime1 (1.4.4-6ubuntu2.2) ... 
Setting up libcupsppdc1 (1.4.4-6ubuntu2.2) ... 
Setting up cups-common (1.4.4-6ubuntu2.2) ... 
Setting up cups-client (1.4.4-6ubuntu2.2) ... 
Setting up cups-bsd (1.4.4-6ubuntu2.2) ... 
Setting up cups-ppdc (1.4.4-6ubuntu2.2) ... 
Setting up cups (1.4.4-6ubuntu2.2) ... 
cups start/running, process 4687 
Setting up libfreetype6 (2.4.2-2ubuntu0.1) ... 
Setting up libfreetype6-dev (2.4.2-2ubuntu0.1) ... 
Setting up libpurple-bin (1:2.7.3-1ubuntu3.1) ... 
Setting up libpurple0 (1:2.7.3-1ubuntu3.1) ... 
Setting up xserver-xorg-video-intel (2:2.12.0-1ubuntu5.1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 postfix 
Setting up postfix (2.7.1-1) ... 
 
Postfix configuration was not changed.  If you need to make changes, edit 
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration 
values, see postconf(1). 
 
After modifying main.cf, be sure to run '/etc/init.d/postfix reload'. 
 
Running newaliases 
newaliases: warning: valid_hostname: numeric hostname: 9 
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: 9 
dpkg: error processing postfix (--configure): 
 subprocess installed post-installation script returned error exit status 75 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 

```any help greatly appreciated.

---

### Post by LowSky on 2010-11-05
Run these two command form terminal, copy and paste them for the correct effect.

```
sudo dpkg-configure --a
```

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoremove
```

---

### Post by kindafunnylookin on 2010-11-05
> **LowSky said:**
> Run these two command form terminal, copy and paste them for the correct effect.

```
sudo dpkg-configure --a
``````
sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoremove
```


no luck -- this is what I get
```
sudo dpkg-configure --asudo dpkg-configure --a
peter@9:~$ sudo dpkg-configure --a
sudo: dpkg-configure: command not found
peter@9:~$ 
peter@9:~$ sudo dpkg-configure --a
sudo: dpkg-configure: command not found
peter@9:~$ 
peter@9:~$ sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoremove
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Hit http://us.archive.ubuntu.com maverick Release.gpg               
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://archive.canonical.com/ maverick/partner Translation-en              
Ign http://archive.canonical.com/ maverick/partner Translation-en_US           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Hit http://extras.ubuntu.com maverick Release                        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Hit http://archive.canonical.com maverick Release
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Hit http://extras.ubuntu.com maverick/main i386 Packages             
Hit http://archive.canonical.com maverick/partner i386 Packages      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://us.archive.ubuntu.com maverick-proposed Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en_US
Hit http://security.ubuntu.com maverick-security/main Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-backports Release.gpg
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release
Hit http://us.archive.ubuntu.com maverick-updates Release
Hit http://us.archive.ubuntu.com maverick-proposed Release
Hit http://us.archive.ubuntu.com maverick-backports Release
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/main Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-proposed/restricted Sources
Hit http://us.archive.ubuntu.com maverick-proposed/main Sources
Hit http://us.archive.ubuntu.com maverick-proposed/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-proposed/universe Sources
Hit http://us.archive.ubuntu.com maverick-proposed/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-proposed/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-proposed/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-proposed/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-backports/restricted Sources
Hit http://us.archive.ubuntu.com maverick-backports/main Sources
Hit http://us.archive.ubuntu.com maverick-backports/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-backports/universe Sources
Hit http://us.archive.ubuntu.com maverick-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-backports/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-backports/universe i386 Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up postfix (2.7.1-1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: numeric hostname: 9
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: 9
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
peter@9:~$ 


```

---

### Post by HectorG on 2011-01-07
Same issue here...

---

### Post by HectorG on 2011-01-08
Fixed mine by doing the following...

sudo dpkg --configure -a
sudo apt-get install -f

uninstall akirad repository (not sure why this fixed it yet)

Try your update now

---

