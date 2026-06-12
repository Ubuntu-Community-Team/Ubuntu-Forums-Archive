---
title: "Can't Install Firefox Build"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2010-05-13
I just upgraded my sister's Ubuntu to 10.04.

I have sucessfully updated its OpenOffice, but now I am having some problems installing Ubuntuzilla with Firefox build. I have tried numerous times to no avail. Here is what I see:```
autumang@autumang:~$ echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null 
autumang@autumang:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpg: key C1289A29: public key "Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
autumang@autumang:~$ sudo apt-get update
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg           
Hit http://archive.canonical.com lucid Release.gpg                   
Hit http://security.ubuntu.com lucid-security Release                
Hit http://us.archive.ubuntu.com lucid Release                                 
Hit http://archive.canonical.com lucid Release                                 
Hit http://us.archive.ubuntu.com lucid-updates Release                         
Get:1 http://downloads.sourceforge.net all Release.gpg [197B]                  
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://us.archive.ubuntu.com lucid/restricted Packages                     
Hit http://us.archive.ubuntu.com lucid/main Sources                            
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources                     
Hit http://us.archive.ubuntu.com lucid/restricted Sources                      
Hit http://us.archive.ubuntu.com lucid/universe Packages                       
Hit http://us.archive.ubuntu.com lucid/universe Sources                        
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://us.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://archive.canonical.com lucid/partner Sources                         
Hit http://us.archive.ubuntu.com lucid-updates/main Packages                   
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages   
Hit http://us.archive.ubuntu.com lucid-updates/main Sources          
Hit http://security.ubuntu.com lucid-security/restricted Sources     
Hit http://security.ubuntu.com lucid-security/universe Packages      
Hit http://security.ubuntu.com lucid-security/universe Sources       
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Hit http://security.ubuntu.com lucid-security/multiverse Sources     
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources    
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages      
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources       
Get:2 http://downloads.sourceforge.net all Release [961B]               
Ign http://downloads.sourceforge.net all/main Packages
Ign http://downloads.sourceforge.net all/main Packages
Get:3 http://downloads.sourceforge.net all/main Packages [853B]      
Fetched 2011B in 4s (497B/s)                                         
Reading package lists... Done
autumang@autumang:~$ sudo apt-get install firefox-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-mozilla-build is already the newest version.
The following packages were automatically installed and are no longer required:
  libcolamd2.7.1 lp-solve firefox-3.5-branding libgraphite3 xfonts-mathml
  libneon27-gnutls
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/10.9MB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 
dpkg: warning: files list file for package `firefox-mozilla-build' missing, assuming package has no files currently installed.
(Reading database ... 206478 files and directories currently installed.)
Preparing to replace firefox-mozilla-build 3.6.3-0ubuntu1 (using .../firefox-mozilla-build_3.6.3-0ubuntu1_i386.deb) ...
Unpacking replacement firefox-mozilla-build ...
dpkg: error processing /var/cache/apt/archives/firefox-mozilla-build_3.6.3-0ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/bin/firefox', which is also in package firefox 0:3.6.3+nobinonly-0ubuntu4
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.C.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/firefox-mozilla-build_3.6.3-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
autumang@autumang:~$
```

And, sure enough, checking Applications>Internet shows that (instead of having "Firefox Web Brouser" and the Firefox Build), I do not have the Firefox build to update Firefox with. What can I do to fix this?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by blazemore on 2010-05-13
If you're on a 64-bit system, UbuntuZilla supposidly doesn't work.
If you're on a 32-bit system, running this uber-command will probably sort you out :-)

```
sudo apt-get update; sudo apt-get upgrade -y --force-yes; sudo dpkg -i --force-all /var/cache/apt/archives/firefox-mozilla-build_3.6.3-0ubuntu1_i386.deb; sudo apt-get -f install
```

---

### Post by RedStarYellowSun on 2010-05-13
Thanks!

---

