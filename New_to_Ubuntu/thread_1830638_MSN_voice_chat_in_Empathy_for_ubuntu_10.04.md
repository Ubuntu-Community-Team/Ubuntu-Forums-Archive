---
title: "MSN voice chat in Empathy for ubuntu 10.04"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by xgtyca on 2011-08-22
Hi,
My Empathy does not support MSN voice chat in Ubuntu 10.04 although I updated it
I have 11.04 on another machine and empathy there looks different and works perfectly, but for this machine I dont want to put 11.04 as it is very old and slow machine
any Ideas:confused::confused:


Thanks  :popcorn:

---

### Post by gandaran on 2011-08-22
> **xgtyca said:**
> Hi,
My Empathy does not support MSN voice chat in Ubuntu 10.04 although I updated it
I have 11.04 on another machine and empathy there looks different and works perfectly, but for this machine I dont want to put 11.04 as it is very old and slow machine
any Ideas:confused::confused:


Thanks  :popcorn:
did you install the empathy and libpurple updates on 10.04?  you need the updates as microsoft changed some protocols so the older versions don't work.

---

### Post by xgtyca on 2011-08-22
How to do the update???

---

### Post by gandaran on 2011-08-22
> **xgtyca said:**
> How to do the update???
the usual ubuntu updates, haven't you installed them?

---

### Post by xgtyca on 2011-08-22
I get this failure when trying to check for updates

(GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A445E8CCD1A0D2FBFailed to fetch [http://deb.torproject.org/torproject.org/dists/maverick/main/binary-i386/Packages.gz](http://deb.torproject.org/torproject.org/dists/maverick/main/binary-i386/Packages.gz)  403  Forbidden [IP: 194.8.197.22 80]
Some index files failed to download, they have been ignored, or old ones used instead.)

I am not sure if this the reason or it not related to our issue
Please help me as I am a beginner

---

### Post by gandaran on 2011-08-22
every time you add an extra repository you also have to add the signing key, try runnig this commands
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A445E8CCD1A0D2FB
```
then 
```
sudo apt-get update
```

---

### Post by xgtyca on 2011-08-22
This is what happen


```
marwan@marwan-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
marwan@marwan-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A445E8CCD1A0D2FB
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys A445E8CCD1A0D2FB
gpg: requesting key D1A0D2FB from hkp server keyserver.ubuntu.com
gpg: key D1A0D2FB: "Launchpad PPA for Ubuntu Muslim Edition Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
marwan@marwan-laptop:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg                            
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid Release.gpg                                   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Get:2 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [8,215B]                      
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ppa.launchpad.net/sabily.team/ppa/ubuntu/](http://ppa.launchpad.net/sabily.team/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US            
Ign [http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/](http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/) lucid/main Translation-en_US
Ign [http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/](http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/) lucid/restricted Translation-en_US
Ign [http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/](http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/) lucid/universe Translation-en_US
Ign [http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/](http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/) lucid/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-updates Release.gpg                           
Ign [http://ppa.launchpad.net/romance990033/ppa/ubuntu/](http://ppa.launchpad.net/romance990033/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                                
Ign [http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/](http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/) lucid-updates/main Translation-en_US
Ign [http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/](http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/) lucid-updates/restricted Translation-en_US
Ign [http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/](http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/) lucid-updates/universe Translation-en_US
Ign [http://ppa.launchpad.net/telepathy/ppa/ubuntu/](http://ppa.launchpad.net/telepathy/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_US          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Ign [http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/](http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/) lucid-updates/multiverse Translation-en_US
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-security Release.gpg                          
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/](http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/) lucid-security/main Translation-en_US
Ign [http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/](http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/) lucid-security/restricted Translation-en_US
Ign [http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/](http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/) lucid-security/universe Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                      
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US              
Ign [http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/](http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/) lucid-security/multiverse Translation-en_US
Ign [http://deb.torproject.org](http://deb.torproject.org) maverick Release.gpg                   
Ign [http://deb.torproject.org/torproject.org/](http://deb.torproject.org/torproject.org/) maverick/main Translation-en_US
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid Release                             
Ign [http://deb.torproject.org](http://deb.torproject.org) maverick Release                                 
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                             
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-updates Release                               
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-security Release                              
Ign [http://deb.torproject.org](http://deb.torproject.org) maverick/main Packages                           
Get:5 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1,010B]                   
Ign [http://deb.torproject.org](http://deb.torproject.org) maverick/main Packages                           
Err [http://deb.torproject.org](http://deb.torproject.org) maverick/main Packages                           
  403  Forbidden [IP: 78.46.17.118 80]
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid/main Packages                       
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid/restricted Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid/main Sources                                  
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid/restricted Sources                            
Get:6 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,082B]                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid/universe Packages                             
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid/universe Sources                              
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid/multiverse Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid/multiverse Sources                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-updates/main Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                           
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-updates/restricted Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-updates/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-updates/restricted Sources                    
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-updates/universe Packages                     
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-updates/universe Sources                      
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-updates/multiverse Packages                   
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-updates/multiverse Sources                    
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-security/main Packages                        
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-security/restricted Packages                  
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-security/main Sources                         
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-security/restricted Sources                   
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-security/universe Packages                    
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-security/universe Sources                     
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-security/multiverse Packages                  
Hit [http://www-ftp.lip6.fr](http://www-ftp.lip6.fr) lucid-security/multiverse Sources                   
Fetched 5,024B in 15s (328B/s)                                                 
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://deb.torproject.org/torproject.org/dists/maverick/main/binary-i386/Packages.gz](http://deb.torproject.org/torproject.org/dists/maverick/main/binary-i386/Packages.gz)  403  Forbidden [IP: 78.46.17.118 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
marwan@marwan-laptop:~$
```

---

### Post by gandaran on 2011-08-22
well then if it didn't work and you need to update then just disable or remove the same broken repositories in software sources, if you want them back then next time try following the instructions on how to add the repository correctly with the signing key.
open synaptic package manager » go to menu bar » settings » repositories » other/third party software tab and remove the repositories or just disable them, run the update command.

---

### Post by xgtyca on 2011-08-22
> **gandaran said:**
> well then if it didn't work and you need to update then just disable or remove the same broken repositories in software sources, if you want them back then next time try following the instructions on how to add the repository correctly with the signing key.
open synaptic package manager » go to menu bar » settings » repositories » other/third party software tab and remove the repositories or just disable them, run the update command.


[COLOR=Blue]Done, now the update problem is gone and my ubuntu is up to date but still empathy not supporting voice chat in MSN account[/COLOR]

---

### Post by gandaran on 2011-08-22
okay lets see if this helps, I'm not using 10.04 but I think there's an update for libpurple for 10.04 like there is for 11.04 from getdeb repository
[add this repository]("http://www.getdeb.net/updates/Ubuntu/10.04/") (and don't forget the signing key) then run update command and check if any libpurple updates are available.
also I'm not sure if the older emphaty versions works with the new libpurple library's but try anyway.
install pidgin if empathy still won't connect, pidgin and empathy use the same lipurple libraries.

---

### Post by gandaran on 2011-08-22
also found this
[http://www.techdrivein.com/2010/06/install-latest-empathy-in-ubuntu-from.html](http://www.techdrivein.com/2010/06/install-latest-empathy-in-ubuntu-from.html)

---

### Post by xgtyca on 2011-08-22
> **gandaran said:**
> okay lets see if this helps, I'm not using 10.04 but I think there's an update for libpurple for 10.04 like there is for 11.04 from getdeb repository
[add this repository]("http://www.getdeb.net/updates/Ubuntu/10.04/") (and don't forget the signing key) then run update command and check if any libpurple updates are available.
also I'm not sure if the older emphaty versions works with the new libpurple library's but try anyway.
install pidgin if empathy still won't connect, pidgin and empathy use the same lipurple libraries.


Can you please explain to me how to do that step by step:confused:
i am a fresh beginner:(
I know that i tok a lot of your time but please help me:D

Thanks:popcorn:

---

### Post by gandaran on 2011-08-22
> **xgtyca said:**
> Can you please explain to me how to do that step by step:confused:
i am a fresh beginner:(
I know that i tok a lot of your time but please help me:D

Thanks:popcorn:
open the 'Click here to learn how to install applications from GetDeb' then download the getdeb.deb package and click the package to install or follow the manually install instruction for adding the repository to software sources and the signing key.

---

