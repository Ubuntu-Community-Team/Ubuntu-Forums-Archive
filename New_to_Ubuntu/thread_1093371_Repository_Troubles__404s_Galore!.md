---
title: "Repository Troubles:  404s Galore!"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by fidgetyacolyte on 2009-03-11
Hey, I just got one of the Dell Mini 9 laptops with Ubuntu on it, Hardy I believe, and I'm trying to get my Synaptic Package Manager working 100%.  I believe I've narrowed down my problem to my repository list.  As mentioned in another thread, I was trying to install ZSNES and it would never show up; someone just linked me to a deb package and that solved the ZSNES problem, but this repository problem seems slightly more important.

Anyways, here is some commands and output:

When I do:

sudo apt-get update

Here is the output:
```
Get:1 http://security.ubuntu.com hardy-security Release.gpg [189B]
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US        
Hit http://us.archive.ubuntu.com hardy Release.gpg                                
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US               
Hit http://archive.ubuntu.com hardy Release.gpg                                   
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US                  
Hit http://packages.medibuntu.org hardy Release.gpg                               
Ign http://packages.medibuntu.org hardy/free Translation-en_US                    
Ign http://security.ubuntu.com hardy-security/main Translation-en_US              
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US          
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US        
Get:2 http://security.ubuntu.com hardy-security Release [58.5kB]                  
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US                 
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                     
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US               
Get:3 http://us.archive.ubuntu.com hardy-updates Release.gpg [189B]               
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US       
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US             
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US         
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US       
Hit http://archive.ubuntu.com hardy Release                                       
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US                
Hit http://packages.medibuntu.org hardy Release                                   
Hit http://us.archive.ubuntu.com hardy Release                                    
Get:4 http://us.archive.ubuntu.com hardy-updates Release [58.5kB]                 
Ign http://archive.ubuntu.com hardy/multiverse Packages                           
Hit http://packages.medibuntu.org hardy/free Packages                             
Err http://archive.ubuntu.com hardy/multiverse Packages                           
  404 Not Found [IP: 91.189.88.31 80]
Hit http://packages.medibuntu.org hardy/non-free Packages                         
Ign http://security.ubuntu.com hardy-security/restricted Packages                 
Ign http://us.archive.ubuntu.com hardy/restricted Packages                        
Ign http://us.archive.ubuntu.com hardy/universe Packages                 
Ign http://us.archive.ubuntu.com hardy/main Packages                     
Ign http://us.archive.ubuntu.com hardy/multiverse Packages               
Ign http://security.ubuntu.com hardy-security/main Packages              
Ign http://security.ubuntu.com hardy-security/universe Packages          
Ign http://security.ubuntu.com hardy-security/multiverse Packages                 
Ign http://us.archive.ubuntu.com hardy-updates/restricted Packages                
Ign http://us.archive.ubuntu.com hardy-updates/main Packages                      
Ign http://us.archive.ubuntu.com hardy-updates/universe Packages                  
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Packages                
Err http://us.archive.ubuntu.com hardy/restricted Packages                        
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/universe Packages                          
  404 Not Found [IP: 91.189.88.40 80]
Err http://security.ubuntu.com hardy-security/restricted Packages                 
  404 Not Found
Err http://security.ubuntu.com hardy-security/main Packages                       
  404 Not Found
Err http://us.archive.ubuntu.com hardy/main Packages                              
  404 Not Found [IP: 91.189.88.40 80]
Err http://security.ubuntu.com hardy-security/universe Packages                   
  404 Not Found
Err http://us.archive.ubuntu.com hardy/multiverse Packages                        
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/restricted Packages                
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/main Packages             
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/universe Packages         
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/multiverse Packages       
  404 Not Found [IP: 91.189.88.40 80]
Err http://security.ubuntu.com hardy-security/multiverse Packages        
  404 Not Found
Hit http://dell-mini.archive.canonical.com hardy Release.gpg             
Ign http://dell-mini.archive.canonical.com hardy/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-updates Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-updates/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-security Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-security/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy Release
Hit http://dell-mini.archive.canonical.com hardy-updates Release
Hit http://dell-mini.archive.canonical.com hardy-security Release
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release
Hit http://dell-mini.archive.canonical.com hardy/main Packages                    
Hit http://dell-mini.archive.canonical.com hardy/universe Packages                
Hit http://dell-mini.archive.canonical.com hardy/multiverse Packages              
Hit http://dell-mini.archive.canonical.com hardy/restricted Packages              
Hit http://dell-mini.archive.canonical.com hardy/main Sources                     
Hit http://dell-mini.archive.canonical.com hardy/universe Sources                 
Hit http://dell-mini.archive.canonical.com hardy/multiverse Sources               
Hit http://dell-mini.archive.canonical.com hardy/restricted Sources               
Hit http://dell-mini.archive.canonical.com hardy-updates/main Packages            
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Packages        
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Packages      
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Packages      
Hit http://dell-mini.archive.canonical.com hardy-updates/main Sources             
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Sources         
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources       
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Sources       
Hit http://dell-mini.archive.canonical.com hardy-security/main Packages           
Hit http://dell-mini.archive.canonical.com hardy-security/universe Packages       
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Packages     
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Packages     
Hit http://dell-mini.archive.canonical.com hardy-security/main Sources            
Hit http://dell-mini.archive.canonical.com hardy-security/universe Sources        
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Sources      
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Sources      
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages       
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages   
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages 
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages 
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources        
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources    
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources  
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources  
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages          
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages      
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages    
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages    
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources           
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources       
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources     
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources     
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages       
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages   
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages 
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages 
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources        
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources    
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources  
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources  
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages          
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages      
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages    
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages    
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources           
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources       
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources     
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources     
Fetched 117kB in 7s (15.6kB/s)                                                    
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

When I tried to install zsnes:

sudo apt-get install zsnes

Here was my output:

```
sudo apt-get install zsnes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package zsnes

```

Any suggestions, or any other information needed?

Thanks for the help!

---

### Post by ubudog on 2009-03-11
Open a terminal and type dpkg --configure and reply what happens.

---

### Post by cariboo on 2009-03-11
Try a different server. Go to System-->Administration-->Software Sources, click the Download From Drop down and select Other. Next click Select Best Server, let it run, when it is finished clcik Choose Server. You will be prompted to reload the sources list, once it is down you should be able to install what you want.

Jim

---

### Post by fidgetyacolyte on 2009-03-11
Heres the output I get:

```
 dpkg --configure
dpkg: requested operation requires superuser privilege

 sudo dpkg --configure
[sudo] password for alex: 
dpkg: --configure needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

---

### Post by ubudog on 2009-03-11
Well I had the same problem and I did dpkg --configure and it gave me the same message as you got, but then I didn't get the error "please run dpkg --configure" anymore and everything worked fine. Mmm.

---

### Post by binbash on 2009-03-11
open synaptic manager and change the server.You will be fine

---

### Post by fidgetyacolyte on 2009-03-11
I have tried changing the server to Main Server, Server for United States, and [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu), and I had it select the best server, and it gave me the ubuntu.mit.edu server. They all give me the same following errors upon reload:

> The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

```
Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/hardy/main/binary-lpia/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```


I don't know why my laptop is being such a bother.  Maybe I should just reload and see if it happens again.  My father's laptop with ubuntu just came in the mail today.  I'll see if his has the same problem.

---

### Post by ubudog on 2009-03-11
Your father's probably won't have the same problem.  Do you have a working internet connection?

---

### Post by fidgetyacolyte on 2009-03-11
Yeah, I'm using this same computer to post on here currently.  Everything actually works beautifully except for this niggling little problem.

I recently just used someone elses proven sources list, and I get the same errors, saying it can't find the [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) packages.

What's funny is that I can hop on Firefox and get to the Package file at that location, no problem.  For some reason synaptic just cant do it.

---

### Post by mrearl on 2009-03-11
I had a similar problem a few weeks ago.  Changing servers made no difference and the errors were annoying.  My problem was solved when I went back to the default repositories for the Dell Mini 9 with one addition for wine.

It looks like this:
```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
```

---

### Post by ubudog on 2009-03-11
Maybe try reinstalling synaptic.

---

### Post by fidgetyacolyte on 2009-03-11
Well, I went back to default sources list like you suggested, however, the problem with being able to find programs such as ZSNES still persists.  It tells me it cannot find that package.

Oh Dell, what have you done with your minis...

EDIT:  I just went back into Synaptic, and Re-checked the Canonical, Restricted, Multiverse, and Universe boxes, and I get the same error as before.  Its almost like my laptop isn't allowing Synaptic to access any Universe of Multiverse repositories:

Error:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by fidgetyacolyte on 2009-03-12
It seems like the problem lies in where synaptic is trying to fetch the update.

In the previous post, it cannot find the packages.gz because of the binary-lpia in the address.  ANyone know how I can circumvent this or somehow change the address it looks in?

---

### Post by ubudog on 2009-03-12
I don't think there is a package called zsnes in the repository.

---

### Post by fidgetyacolyte on 2009-03-12
I'm assuming it exists because the numerous websites I went to for help all said, "You can manually download it, but its much better to download it through Synaptic.  It is in multiverse."

---

### Post by ubudog on 2009-03-12
I searched for zsnes in synaptic and the results were visualboyadvance and visualboyadvance-gtk.  But there weren't any packages called zsnes.

---

### Post by boof1988 on 2009-03-12
> **ubudog said:**
> I don't think there is a package called zsnes in the repository.

I don't have any special repositories enabled.  Zsnes does appear to be in the repositories.  I didn't download or install... so I can't say whether the packages will download successfully or not.

```

*user*@*host*:~$ sudo apt-get -s install zsnes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libao2 libasound2 libdirectfb-1.0-0 libsdl1.2debian libsdl1.2debian-alsa
Suggested packages:
  libartsc0 libaudio2 libesd0 libesd-alsa0 libpulse0 libasound2-plugins
The following NEW packages will be installed:
  libao2 libasound2 libdirectfb-1.0-0 libsdl1.2debian libsdl1.2debian-alsa zsnes
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Inst libao2 (0.8.8-3 Ubuntu:8.04/hardy)
Inst libasound2 (1.0.15-3ubuntu4 Ubuntu:8.04/hardy)
Inst libdirectfb-1.0-0 (1.0.1-7ubuntu3 Ubuntu:8.04/hardy)
Inst libsdl1.2debian-alsa (1.2.13-1ubuntu1 Ubuntu:8.04/hardy)
Inst libsdl1.2debian (1.2.13-1ubuntu1 Ubuntu:8.04/hardy)
Inst zsnes (1.510-2ubuntu1 Ubuntu:8.04/hardy)
Conf libao2 (0.8.8-3 Ubuntu:8.04/hardy)
Conf libasound2 (1.0.15-3ubuntu4 Ubuntu:8.04/hardy)
Conf libdirectfb-1.0-0 (1.0.1-7ubuntu3 Ubuntu:8.04/hardy)
Conf libsdl1.2debian-alsa (1.2.13-1ubuntu1 Ubuntu:8.04/hardy)
Conf libsdl1.2debian (1.2.13-1ubuntu1 Ubuntu:8.04/hardy)
Conf zsnes (1.510-2ubuntu1 Ubuntu:8.04/hardy)
```

Edit:

I just downloaded the packages (without installing them).  Though I don't know if the OP will have that same luck.  I did have some problems yesterday with some of the downloads from the mirror for a Ubuntu-Minimal-Install.  Don't know why though.  Maybe there was/is a problem with the mirror?

```
*user*@*host*:~$ sudo apt-get -d install zsnes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libao2 libasound2 libdirectfb-1.0-0 libsdl1.2debian libsdl1.2debian-alsa
Suggested packages:
  libartsc0 libaudio2 libesd0 libesd-alsa0 libpulse0 libasound2-plugins
The following NEW packages will be installed:
  libao2 libasound2 libdirectfb-1.0-0 libsdl1.2debian libsdl1.2debian-alsa zsnes
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 2158kB of archives.
After this operation, 7864kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hardy/main libao2 0.8.8-3 [26.2kB]
Get:2 http://us.archive.ubuntu.com hardy/main libasound2 1.0.15-3ubuntu4 [362kB]
Get:3 http://us.archive.ubuntu.com hardy/main libdirectfb-1.0-0 1.0.1-7ubuntu3 [642kB]
Get:4 http://us.archive.ubuntu.com hardy/main libsdl1.2debian-alsa 1.2.13-1ubuntu1 [207kB]
Get:5 http://us.archive.ubuntu.com hardy/main libsdl1.2debian 1.2.13-1ubuntu1 [20.8kB]
Get:6 http://us.archive.ubuntu.com hardy/universe zsnes 1.510-2ubuntu1 [900kB]
Fetched 2158kB in 9s (239kB/s)                                                                                                                                                                            
Download complete and in download only mode
```

---

### Post by ubudog on 2009-03-12
I searched for it in the repository and the results were: visualboyadvance and visualboyadvance-gtk.  There weren't any packages called zsnes in the repository though.

---

### Post by fidgetyacolyte on 2009-03-12
Well, for what its worth, visualboyadvance and visualboyadvance-gtk don't show up either.  All i get is vbaexpress, which is just a gui for visualboyadvance.

---

### Post by ubudog on 2009-03-12
hmm

---

### Post by boof1988 on 2009-03-12
> **fidgetyacolyte said:**
> Well, for what its worth, visualboyadvance and visualboyadvance-gtk don't show up either.  All i get is vbaexpress, which is just a gui for visualboyadvance.

It looks like (from [post #17](http://ubuntuforums.org/showpost.php?p=6882647&postcount=17)) zsnes is in *universe* and the rest of the packages (for my system) are in *main*.

I assume you have *main* and *universe* repositories enabled.  So I wonder if there is a problem with the mirrors.

---

### Post by fidgetyacolyte on 2009-03-12
Upon Googling, it seems like this is a problem native to the Dell Mini 9s, something about not being able to install i386 packages.  One person suggested upgrading Ubuntu to Intrepid instead of Hardy.  Does this sound like a good workaround?

---

### Post by egalvan on 2009-03-12
Running Hardy 8.04.2

This are my screen-shots of Synaptic
the first two show repo information
the third show **zsnes**:

---

### Post by ubudog on 2009-03-12
Check the third box on the first screenshot and see what happens.

---

### Post by boof1988 on 2009-03-12
> **fidgetyacolyte said:**
> Upon Googling, it seems like this is a problem native to the Dell Mini 9s, something about not being able to install i386 packages.  One person suggested upgrading Ubuntu to Intrepid instead of Hardy.  Does this sound like a good workaround?

I had the problem on a custom-build (intel mobo/CPU desktop non-Dell) machine.  So I don't think it is a problem (specifically) native to Dell mini 9s.

So I don't think you should have to upgrade to Intrepid until you know that upgrading (specifically) will fix your problem.  Hopefully someone else can give better information in this matter.

---

### Post by egalvan on 2009-03-12
> **ubudog said:**
> Check the third box on the first screenshot and see what happens.

If this was for me, then:

added the "sources" repo...
re-loaded repo's...
found **zsnes**...

The "Source Code" repo's are just that... the source code to the software.

What I am showing here is my setup, and that it shows the zsnes package that the OP is looking for...
some folks say it shows up in the repos, others say it doesn't.
My post is just a concrete example of Hardy 8.04.2 showing the package.
Perhaps there is information in the screen-shots that will help the OP or others fix the problem.
I have no clue other-wise. :)

ErnestG

---

### Post by ubudog on 2009-03-12
Yes I know that.  I thought you were the person having the problem.  I didn't look at your name.  Just forget about that post.

---

### Post by fidgetyacolyte on 2009-03-13
Looks like the repositories are designed for the Dell Mini so that they only list the binary-lpia optimized packages.

Supposedly, there aren't many packages I'm missing out on, and if there are, I will just have to manually go to one of the archives to get it.

Oh well, as long as I'm not missing the majority of my programs.

All in all, thanks for all the help!

---

