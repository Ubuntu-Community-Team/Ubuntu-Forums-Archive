---
title: "Synaptic/software center not downloading!!"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by eklikeroomys on 2011-05-20
Please help, I am unable to install any packages using either Synaptic or Software Center. Yes, I am connected to the internet. I am able to select an application or package, but once I click on install, Software Center says Downloading, but the progress bar remains at 0kb. Similarly, in Synaptic, when I click on apply, it only says queued, and remains there. 

This makes me think that I may have some package or application stuck in a queue somewhere, but I dont know how to fix it. 

sudo apt-get install also wont work, it just keeps trying but never actually downloads anything. My internet connection is fine, I am able to access the repositories with my browser. I am even able to download the package list in Synaptic.

---

### Post by philinux on 2011-05-20
> **eklikeroomys said:**
> Please help, I am unable to install any packages using either Synaptic or Software Center. Yes, I am connected to the internet. I am able to select an application or package, but once I click on install, Software Center says Downloading, but the progress bar remains at 0kb. Similarly, in Synaptic, when I click on apply, it only says queued, and remains there. 

This makes me think that I may have some package or application stuck in a queue somewhere, but I dont know how to fix it. 

sudo apt-get install also wont work, it just keeps trying but never actually downloads anything. My internet connection is fine, I am able to access the repositories with my browser. I am even able to download the package list in Synaptic.

Close SC and synaptic.
Open a terminal. And report back any errors from this command. Use copy and paste.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by eklikeroomys on 2011-05-23
> **philinux said:**
> Close SC and synaptic.
Open a terminal. And report back any errors from this command. Use copy and paste.

```
sudo apt-get update && sudo apt-get upgrade
```

Halo philinux,

Thank you for your reply, I ran the command in the terminal but I did not receive any errors. The following is the output that I got: 

chris@chris-PC:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for chris: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg               
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_ZA
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_ZA
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en    
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_ZA 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_ZA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_ZA 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_ZA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_ZA
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Fetched 72B in 2s (27B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  skype
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.6MB of archives.
After this operation, 489kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner skype i386 2.2.0.25-1maverick1 [23.6MB]
Fetched 23.6MB in 58s (405kB/s)                                                
(Reading database ... 121338 files and directories currently installed.)
Preparing to replace skype 2.2.0.25-1 (using .../skype_2.2.0.25-1maverick1_i386.deb) ...
Unpacking replacement skype ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_ZA.utf8.cache...
Processing triggers for python-support ...
Setting up skype (2.2.0.25-1maverick1) ...

I tried installing tkgate from SC but its still not downloading...

---

### Post by Wolfenberg on 2011-05-23
Try: sudo apt-get install tkgate

---

### Post by eklikeroomys on 2011-05-23
> **Wolfenberg said:**
> Try: sudo apt-get install tkgate

I tried this, but it has the same effect, it just keeps trying to download, but nothing happens until I use Ctrl+C to quit the operation:


sudo apt-get install tkgate
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  tk8.4 tkgate-data tkgate-doc
The following NEW packages will be installed:
  tk8.4 tkgate tkgate-data tkgate-doc
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,438kB of archives.
After this operation, 7,971kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main tk8.4 i386 8.4.19-4 [1,023kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main tk8.4 i386 8.4.19-4 [1,023kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main tk8.4 i386 8.4.19-4 [1,023kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main tk8.4 i386 8.4.19-4 [1,023kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main tk8.4 i386 8.4.19-4 [1,023kB]
0% [5 tk8.4 0B/1,023kB 0%]^C
chris@chris-PC:~$

---

