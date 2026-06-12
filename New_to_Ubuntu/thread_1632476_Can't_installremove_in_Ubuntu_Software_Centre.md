---
title: "Can't install/remove in Ubuntu Software Centre"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by demonboy on 2010-11-28
Hi,

I was attempting to install the add-on 'Option Globetrotter' to 'usb-modeswitch' but it hung half way through installation. This now appears to have corrupted my aptdaemon packet and I can no longer add or remove any software in USC.

I reported it as a bug but am unsure what happens next. What is the protocol for that? Also has anyone else had a similar problem with USC and is there a solution? The bug report is here:

[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/682167](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/682167)

Basically I can't get online until I install these add-ons so this is crippling me. If anyone can help I would be very grateful.

---

### Post by sikander3786 on 2010-11-28
Hi.

Reboot your PC first. Then go to Applications > Accessories > Terminal and post the output of these commands.

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by demonboy on 2010-11-28
sudo apt-get update
```

Hit http://archive.canonical.com maverick Release.gpg                         
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en      
Hit http://extras.ubuntu.com maverick Release.gpg                             
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en             
Hit http://ppa.launchpad.net maverick Release.gpg                             
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release.gpg                         
Hit http://packages.medibuntu.org maverick Release.gpg                        
Ign http://packages.medibuntu.org/ maverick/free Translation-en               
Ign http://packages.medibuntu.org/ maverick/free Translation-en_GB            
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en           
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_GB        
Hit http://security.ubuntu.com maverick-security Release.gpg                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en  
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_GB   
Hit http://archive.canonical.com maverick Release                             
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB          
Hit http://extras.ubuntu.com maverick Release                                 
Hit http://ppa.launchpad.net maverick Release.gpg                             
Ign http://ppa.launchpad.net/bilalakhtar/gimp/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/bilalakhtar/gimp/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg                             
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release                                 
Hit http://packages.medibuntu.org maverick Release                            
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Hit http://archive.canonical.com maverick/partner i386 Packages               
Hit http://extras.ubuntu.com maverick/main Sources                            
Hit http://security.ubuntu.com maverick-security Release                      
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en         
Hit http://packages.medibuntu.org maverick/free Sources                       
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB      
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en   
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en   
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en     
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB  
Hit http://gb.archive.ubuntu.com maverick-updates Release.gpg                 
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en 
Hit http://ppa.launchpad.net maverick Release                                 
Hit http://ppa.launchpad.net maverick Release                                 
Hit http://linux.dropbox.com maverick Release.gpg                             
Hit http://extras.ubuntu.com maverick/main i386 Packages                      
Hit http://security.ubuntu.com maverick-security/main Sources                 
Hit http://packages.medibuntu.org maverick/non-free Sources                   
Hit http://packages.medibuntu.org maverick/free i386 Packages                 
Hit http://packages.medibuntu.org maverick/non-free i386 Packages             
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://ppa.launchpad.net maverick/main Sources                  
Hit http://ppa.launchpad.net maverick/main i386 Packages                      
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en             
Hit http://security.ubuntu.com maverick-security/restricted Sources           
Hit http://security.ubuntu.com maverick-security/universe Sources             
Hit http://security.ubuntu.com maverick-security/multiverse Sources           
Hit http://security.ubuntu.com maverick-security/main i386 Packages           
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages     
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_GB          
Hit http://security.ubuntu.com maverick-security/universe i386 Packages       
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages     
Hit http://ppa.launchpad.net maverick/main Sources                  
Hit http://ppa.launchpad.net maverick/main i386 Packages            
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://linux.dropbox.com maverick Release 
Hit http://linux.dropbox.com maverick/main i386 Packages
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release
Hit http://gb.archive.ubuntu.com maverick-updates Release
Hit http://gb.archive.ubuntu.com maverick/main Sources
Hit http://gb.archive.ubuntu.com maverick/restricted Sources
Hit http://gb.archive.ubuntu.com maverick/universe Sources
Hit http://gb.archive.ubuntu.com maverick/multiverse Sources
Hit http://gb.archive.ubuntu.com maverick/main i386 Packages
Hit http://gb.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://gb.archive.ubuntu.com maverick/universe i386 Packages
Hit http://gb.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/main Sources
Hit http://gb.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-updates/universe Sources
Hit http://gb.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://gb.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Reading package lists... Done

[\code]

sudo apt-get upgrade

[code]
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following packages will be upgraded:
  comgt libutouch-grail1
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 16.7kB/56.7kB of archives.
After this operation, 188kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libutouch-grail1 i386 1.0.16-0ubuntu1 [16.7kB]
Fetched 16.7kB in 6s (2,711B/s)                                               
(Reading database ...
dpkg: warning: files list file for package `comgt' missing, assuming package has no files currently installed.
(Reading database ... 160201 files and directories currently installed.)
Preparing to replace comgt 0.32-2 (using .../archives/comgt_0.32-2_i386.deb) ...
Unpacking replacement comgt ...
Preparing to replace libutouch-grail1 1.0.15-0ubuntu1 (using .../libutouch-grail1_1.0.16-0ubuntu1_i386.deb) ...
Unpacking replacement libutouch-grail1 ...
Processing triggers for man-db ...
Setting up comgt (0.32-2) ...
Setting up libutouch-grail1 (1.0.16-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


```

sudo apt-get install -f

```

Reading package lists... Done
Building dependency tree      
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

sudo dpkg --configure -a

```

Reading package lists... Done
Building dependency tree      
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

OK, that appears to have fixed the aptdaemon problem. It seems the usb-modeswitch thing wasn't my connection problem though, so that's another issue to report on. Still, got the Ubuntu Software Centre up and running again. Thank you for that. I need to learn those Terminal prompts.

Cheers.

---

### Post by kirenpillay on 2011-06-09
Hi

Thanks, solved my issues:) :D

---

### Post by sunewbie on 2011-08-31
I am a newbie and have Ubuntu 10.04 LTS 3 inside virtualbox. 

I cannot install any software through software center, synaptic or through terminal. Soffware gets downloaded, but the installation fails.

here is the error.

```
nstallArchives() failed: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously deselected package bitstormlite.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 150952 files and directories currently installed.)
Unpacking bitstormlite (from .../bitstormlite_0.2q-1_i386.deb) ...
Processing triggers for man-db ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/usr/bin/mandb: can't set the locale; make sure $LC_* and $LANG are correct
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Rebuilding /usr/share/applications/desktop.en_IN.ISO8859-1.cache...
WARNING: System locale is invalid
Processing triggers for python-support ...
Setting up tex-common (2.06ubuntu0.1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Running mktexlsr. This may take some time... done.
No packages found matching texlive-base.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-binaries:
 texlive-binaries depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-binaries (--configure):
 dependency problems - leaving unconfigured
Setting up bitstormlite (0.2q-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 tex-common
 texlive-binaries
Setting up tex-common (2.06ubuntu0.1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Running mktexlsr. This may take some time... done.
No packages found matching texlive-base.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-binaries:
 texlive-binaries depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-binaries (--configure):
 dependency problems - leaving unconfigured

```

I tried 

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

and 

sudo dpkg --configure -a
sudo apt-get install -f

sudo apt-get install -f is also giving error

```
sujal@sujal-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up tex-common (2.06ubuntu0.1) ...
Running mktexlsr. This may take some time... done.
No packages found matching texlive-base.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-binaries:
 texlive-binaries depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-binaries (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 tex-common
 texlive-binaries
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have install XFCE and LXDE environments. Is this causing problems. I install only through gnome.

I also have 10.04 with KDE installed at home PC, dual boot with XP. Everything is working fine.

Please help me. How can this be fixed?

---

### Post by sunewbie on 2011-09-02
> **not found said:**
> Hi,

From Google it would seem there are issues installing tex-common (I don't think the problem is with the installers themselves).

Even Launchpad has a whole host of bugs files on issues installing it.

If you could try not to install it (remove it completely etc.) and just try and install something different then at least we can see if apt is working OK.


404

Hi 404,

Removing tex-common worked for me. 

```
sudo apt-get remove tex-common
```

I installed vlc from terminal and adobe air through software center.

Thanks for the help

*Thread: [http://ubuntuforums.org/showthread.php?p=11204825#post11204825](http://ubuntuforums.org/showthread.php?p=11204825#post11204825)*

---

