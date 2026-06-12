---
title: "[SOLVED] Packge problems installing samba"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by pd_mct on 2007-07-15
Hi,

I'm trying to setup SAMBA on 6.10 through the Shared Folders.
It pops up a dialog asking what services I want to install -  NFS or Samba.
I pick samba and get the following message:
"Could not apply changes! Fix broken packages first."

So I open Synaptic and try to install samba services and get the following error:
samba:
  Depends: samba-common (= 3.0.22-1ubuntu4) but 3.0.22-1ubuntu4.2 is to be installed

Synaptic says that 3.0.22-1ubunut4.2 is already installed and is listed as the latest.
(I also try via apt-get which did nothing)

Can any tell me how to fix this?

Thanks
Pter

---

### Post by Koybe on 2007-07-15
You can try :

```
sudo apt-get update
sudo apt-get -f install
```Then try again.

If it does not work, put the output of theses out there. ;-)

I hope this could help.

---

### Post by pd_mct on 2007-07-15
Sadly, that didn't help.

Here is the output from the cammands:

```
peter@astro:~$ sudo apt-get update 
Ign http://ubuntu.compiz.net edgy Release.gpg                                  
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Ign http://security.ubuntu.com edgy-security/main Translation-en_AU            
Get:2 http://archive.ubuntu.com edgy Release.gpg [191B]                        
Ign http://archive.ubuntu.com edgy/universe Translation-en_AU                  
Ign http://packages.freecontrib.org edgy Release.gpg                           
Ign http://packages.freecontrib.org edgy/free Translation-en_AU                
Ign http://packages.freecontrib.org edgy/non-free Translation-en_AU            
Ign http://blognux.free.fr unstable Release.gpg                                
Ign http://www.kiberpipa.org ./ Release.gpg                                    
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_AU      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_AU        
Ign http://security.ubuntu.com edgy-security/main Translation-en_AU            
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_AU      
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_AU      
Ign http://archive.ubuntu.com edgy/main Translation-en_AU                      
Ign http://archive.ubuntu.com edgy/restricted Translation-en_AU                
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_AU                
Get:3 http://archive.ubuntu.com edgy-updates Release.gpg [191B]                
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_AU          
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_AU              
Ign http://ubuntu.compiz.net edgy/main Translation-en_AU                       
Ign http://packages.freecontrib.org edgy Release                               
Hit http://security.ubuntu.com edgy-security Release                           
Ign http://www.kiberpipa.org ./ Translation-en_AU                              
Ign http://www.kiberpipa.org ./ Release.gpg                                    
Ign http://www.kiberpipa.org ./ Translation-en_AU                              
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_AU        
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_AU        
Hit http://archive.ubuntu.com edgy Release                                     
Hit http://archive.ubuntu.com edgy-updates Release                             
Ign http://packages.freecontrib.org edgy/free Packages                         
Ign http://blognux.free.fr unstable/main Translation-en_AU                     
Ign http://ubuntu.compiz.net edgy Release                                      
Get:4 http://security.ubuntu.com edgy-security/main Packages [90.5kB]          
99% [4 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com edgy-security/main Packages                     
  Sub-process bzip2 returned an error code (2)
Hit http://archive.ubuntu.com edgy/universe Packages                           
Hit http://archive.ubuntu.com edgy/main Packages                               
Hit http://archive.ubuntu.com edgy/restricted Packages                         
Ign http://www.kiberpipa.org ./ Release                                        
Ign http://packages.freecontrib.org edgy/non-free Packages                     
Err http://www.beerorkid.com edgy Release.gpg                                  
  The HTTP server sent an invalid reply header
Err http://www.beerorkid.com edgy/main Translation-en_AU                       
  Bad header line
Ign http://www.beerorkid.com edgy Release                                      
Ign http://www.beerorkid.com edgy/main Packages                                
Err http://www.beerorkid.com edgy/main Packages                                
  Bad header line
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Hit http://archive.ubuntu.com edgy/multiverse Packages                         
Hit http://archive.ubuntu.com edgy/universe Sources                            
Hit http://archive.ubuntu.com edgy/main Sources                                
Hit http://archive.ubuntu.com edgy/restricted Sources                          
Hit http://archive.ubuntu.com edgy/multiverse Sources                          
Ign http://ubuntu.compiz.net edgy/main Packages                                
Hit http://archive.ubuntu.com edgy-updates/universe Packages                   
Hit http://archive.ubuntu.com edgy-updates/main Packages                       
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages                 
Err http://packages.freecontrib.org edgy/free Packages                         
  404 Not Found
Ign http://www.kiberpipa.org ./ Release                                        
Ign http://blognux.free.fr unstable Release                                    
Hit http://security.ubuntu.com edgy-security/universe Packages                 
Get:5 http://security.ubuntu.com edgy-security/main Packages [90.5kB]          
Hit http://security.ubuntu.com edgy-security/multiverse Packages               
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Hit http://security.ubuntu.com edgy-security/universe Sources                  
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://security.ubuntu.com edgy-security/multiverse Sources                
99% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Connectibzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com edgy-security/main Packages                     
  Sub-process bzip2 returned an error code (2)
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Hit http://archive.ubuntu.com edgy-updates/restricted Packages                 
Err http://packages.freecontrib.org edgy/non-free Packages                     
  404 Not Found
Ign http://www.kiberpipa.org ./ Packages                                       
Err http://ubuntu.compiz.net edgy/main Packages                                
  302 Found [IP: 63.251.133.40 80]
Ign http://blognux.free.fr unstable/main Packages
Ign http://www.kiberpipa.org ./ Packages       
Hit http://blognux.free.fr unstable/main Packages
Err http://www.kiberpipa.org ./ Packages
  404 Not Found
Err http://www.kiberpipa.org ./ Packages
  404 Not Found
Fetched 5B in 6s (1B/s)                                                        
Failed to fetch http://www.beerorkid.com/compiz/dists/edgy/Release.gpg  The HTTP server sent an invalid reply header
Failed to fetch http://www.beerorkid.com/compiz/dists/edgy/main/i18n/Translation-en_AU.bz2  Bad header line
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://www.beerorkid.com/compiz/dists/edgy/main/binary-i386/Packages.gz  Bad header line
Failed to fetch http://ubuntu.compiz.net/dists/edgy/main/binary-i386/Packages.gz  302 Found [IP: 63.251.133.40 80]
Failed to fetch http://www.kiberpipa.org/~gandalf/ubuntu/edgy/mjpegtools/./Packages.gz  404 Not Found
Failed to fetch http://www.kiberpipa.org/~gandalf/ubuntu/edgy/cinelerra/pentium4/./Packages.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

peter@astro:~$ sudo apt-get -f install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu4) but 3.0.22-1ubuntu4.2 is to be installed
E: Broken packages
peter@astro:~$ 
```

Thanks
Pter

---

### Post by Koybe on 2007-07-15
Maybe you can try to remove it before :

```
sudo apt-get --purge remove samba-common
```

---

### Post by pd_mct on 2007-07-15
That fixed it -

I remember now why I didn't do that in the first place.
It says that removing samba-common will also remove ubuntu-desktop which kind of scared me.

It seems to have installed successfully now.

Thanks for your help.

cheers
Pter

---

### Post by Koybe on 2007-07-15
Nice.

ubuntu-desktop is a metapackage (a package that install many others), so if it removes it, I think you can actually reinstall it after your problem is solved.

Glad to help ;)

---

