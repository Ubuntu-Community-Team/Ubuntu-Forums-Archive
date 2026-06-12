---
title: "Problem Install/Removing With apt-get"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by Chrissd on 2010-01-01
Hey all,

Today I've been playing about with a few different things, such as ZoneMinder and a FTP server.

Now I can't remove vsftpd, and can't install anything. Below is what happens when I do. Any help gratefully received.

```

sudo apt-get remove vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  apache2: Depends: apache2-mpm-worker (>= 2.2.12-1ubuntu2.1) but it is not going to be installed or
                    apache2-mpm-prefork (>= 2.2.12-1ubuntu2.1) but it is not going to be installed or
                    apache2-mpm-event (>= 2.2.12-1ubuntu2.1) but it is not going to be installed or
                    apache2-mpm-itk (>= 2.2.12-1ubuntu2.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

``` 

```
 
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  python-crypto empathy-doc telepathy-salut libempathy-gtk28 python-telepathy
  libsnack2-alsa libloudmouth1-0 telepathy-haze amsn-data telepathy-gabble
  tcl8.5 tk8.5 libempathy-gtk-common telepathy-butterfly python-papyon tcl-tls
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-worker
The following packages will be REMOVED
  vsftpd
The following NEW packages will be installed
  apache2-mpm-worker
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2,314B of archives.
After this operation, 406kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 194826 files and directories currently installed.)
Removing vsftpd ...
dpkg: error processing vsftpd (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` 


Thanks in advance.

---

### Post by tom.swartz07 on 2010-01-01
> **Chrissd said:**
> Hey all,

Today I've been playing about with a few different things, such as ZoneMinder and a FTP server.

Now I can't remove vsftpd, and can't install anything. Below is what happens when I do. Any help gratefully received.

```

sudo apt-get remove vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  apache2: Depends: apache2-mpm-worker (>= 2.2.12-1ubuntu2.1) but it is not going to be installed or
                    apache2-mpm-prefork (>= 2.2.12-1ubuntu2.1) but it is not going to be installed or
                    apache2-mpm-event (>= 2.2.12-1ubuntu2.1) but it is not going to be installed or
                    apache2-mpm-itk (>= 2.2.12-1ubuntu2.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

``` 

```
 
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  python-crypto empathy-doc telepathy-salut libempathy-gtk28 python-telepathy
  libsnack2-alsa libloudmouth1-0 telepathy-haze amsn-data telepathy-gabble
  tcl8.5 tk8.5 libempathy-gtk-common telepathy-butterfly python-papyon tcl-tls
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-worker
The following packages will be REMOVED
  vsftpd
The following NEW packages will be installed
  apache2-mpm-worker
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2,314B of archives.
After this operation, 406kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 194826 files and directories currently installed.)
Removing vsftpd ...
dpkg: error processing vsftpd (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` 


Thanks in advance.

I may be wrong, but it appears that there are some unmet upgrades that you have. Could you try running ```
sudo apt-get update && sudo apt-get upgrade
```

See if that clears your problem.

---

### Post by Chrissd on 2010-01-01
Similar sort of thing returned. Apologies for the big list of text returned, not sure what's relevant and what's not.

```

sudo apt-get update && sudo apt-get upgrade
Hit http://packages.medibuntu.org karmic Release.gpg
Ign http://packages.medibuntu.org karmic/free Translation-en_GB                
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_GB          
Ign http://packages.medibuntu.org karmic/non-free Translation-en_GB  
Hit http://gb.archive.ubuntu.com karmic Release.gpg                  
Get: 1 http://gb.archive.ubuntu.com karmic/main Translation-en_GB [63.7kB]
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_GB    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_GB      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_GB    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://packages.medibuntu.org karmic Release                               
Get: 2 http://gb.archive.ubuntu.com karmic/restricted Translation-en_GB [3,402B]
Get: 3 http://gb.archive.ubuntu.com karmic/universe Translation-en_GB [33.2kB] 
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://packages.medibuntu.org karmic/free Packages                         
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/main Sources                    
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Get: 4 http://gb.archive.ubuntu.com karmic/multiverse Translation-en_GB [43.8kB]
Hit http://gb.archive.ubuntu.com karmic-updates Release.gpg            
Ign http://gb.archive.ubuntu.com karmic-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com karmic-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com karmic Release
Hit http://gb.archive.ubuntu.com karmic-updates Release                     
Hit http://gb.archive.ubuntu.com karmic/main Packages                       
Hit http://gb.archive.ubuntu.com karmic/restricted Packages
Hit http://gb.archive.ubuntu.com karmic/restricted Sources
Hit http://gb.archive.ubuntu.com karmic/main Sources
Hit http://gb.archive.ubuntu.com karmic/multiverse Sources
Hit http://gb.archive.ubuntu.com karmic/universe Sources
Hit http://gb.archive.ubuntu.com karmic/universe Packages
Hit http://gb.archive.ubuntu.com karmic/multiverse Packages
Hit http://gb.archive.ubuntu.com karmic-updates/main Packages
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://gb.archive.ubuntu.com karmic-updates/main Sources
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://gb.archive.ubuntu.com karmic-updates/universe Sources
Hit http://gb.archive.ubuntu.com karmic-updates/universe Packages
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Packages
Fetched 144kB in 1s (103kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  apache2: Depends: apache2-mpm-worker (>= 2.2.12-1ubuntu2.1) but it is not installed or
                    apache2-mpm-prefork (>= 2.2.12-1ubuntu2.1) but it is not installed or
                    apache2-mpm-event (>= 2.2.12-1ubuntu2.1) but it is not installed or
                    apache2-mpm-itk (>= 2.2.12-1ubuntu2.1) but it is not installed
E: Unmet dependencies. Try using -f.

```

---

### Post by aust77 on 2010-01-01
Hm...I don't want to be questioning your common sense, but have you tried the apt-get -f install as recommended by the terminal?

Not too familiar with these kinds of things, but I figured I'd help out by pointing that out.

You might also want to use apt-get autoremove to get rid of unwanted packages that *MAY* be causing this.

---

### Post by Magnesium on 2010-01-01
> **aust77 said:**
> Hm...I don't want to be questioning your common sense, but have you tried the apt-get -f install as recommended by the terminal?

> **Chrissd said:**
> ...Below is what happens when I do...

```

sudo apt-get remove vsftpd
...
``` 

```
sudo apt-get -f install
...
``` 


I think the answer to your question aust77 is "yes" :P

Mg

---

### Post by Magnesium on 2010-01-01
Here's a similar bug in Launchpad for installing...same error though, but unfortunately not solution: [https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/484004](https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/484004)

Maybe you could try running ```
sudo dpkg --configure -a
```

Mg

---

### Post by Chrissd on 2010-01-01
Hi,
Tried that, it didn't return anything, but tried removing and -f instal etc, no joy, same.

Really baffled. :(

---

### Post by spiderbatdad on 2010-01-01
It looks like it is trying to install apache2. Try removing apache2, or look at /var/cache/apt/archives/lock delete the lock file. You could also try opening synaptic and running fix broken packages under the edit menu.

---

### Post by Chrissd on 2010-01-02
Hi, before all this, Apache2 was installed and working, although it won't start now because it's lacking that file.

Tried going into synaptic but it returns the same error as in command line.

Should I just delete the file /var/cache/apt/archives/lock?

---

### Post by Chrissd on 2010-01-02
Tried removing Apache2 here's the result:

```

sudo apt-get remove apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-crypto empathy-doc apache2-utils telepathy-salut
  libaprutil1-dbd-sqlite3 apache2.2-bin libapr1 libempathy-gtk28
  python-telepathy libaprutil1-ldap libsnack2-alsa libloudmouth1-0
  telepathy-haze apache2.2-common amsn-data telepathy-gabble tcl8.5 tk8.5
  libempathy-gtk-common telepathy-butterfly python-papyon libaprutil1 tcl-tls
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  apache2 vsftpd
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 516kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 194826 files and directories currently installed.)
Removing vsftpd ...
dpkg: error processing vsftpd (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing apache2 ...
Processing triggers for ureadahead ...
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by spiderbatdad on 2010-01-02
Did you try running ```
sudo apt-get autoremove && sudo apt-get install -f
```
Did you try deleting lock file?

---

