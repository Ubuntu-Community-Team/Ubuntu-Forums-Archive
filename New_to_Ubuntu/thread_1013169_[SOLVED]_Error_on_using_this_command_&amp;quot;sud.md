---
title: "[SOLVED] Error on using this command: &amp;quot;sudo apt-get update&amp;quot;"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by looi76 on 2008-12-16
Hi everyone, Just now I have installed Ubuntu 8.10 64-bit on my laptop. I wanted to update the apt (Advanced Packaging Tool) and got this error when I enterend this command "sudo apt-get update" in the terminal:

```
looi76@looi76-laptop:~$ sudo apt-get update
Hit http://security.ubuntu.com intrepid-security Release.gpg
Hit http://bh.archive.ubuntu.com intrepid Release.gpg                          
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US        
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US 
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://bh.archive.ubuntu.com intrepid/main Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com intrepid-security Release
Ign http://bh.archive.ubuntu.com intrepid/restricted Translation-en_US
Get:1 http://security.ubuntu.com intrepid-security/main Packages [36.3kB]   
Hit http://security.ubuntu.com intrepid-security/restricted Packages        
Ign http://bh.archive.ubuntu.com intrepid/universe Translation-en_US        
Ign http://bh.archive.ubuntu.com intrepid/multiverse Translation-en_US      
Get:2 http://bh.archive.ubuntu.com intrepid-updates Release.gpg [189B]
Ign http://bh.archive.ubuntu.com intrepid-updates/main Translation-en_US
Get:3 http://security.ubuntu.com intrepid-security/main Sources [11.7kB]
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Ign http://bh.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://bh.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://bh.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://bh.archive.ubuntu.com intrepid Release
Get:4 http://bh.archive.ubuntu.com intrepid-updates Release [51.2kB]          
Err http://bh.archive.ubuntu.com intrepid-updates Release                     
  
Hit http://bh.archive.ubuntu.com intrepid/main Packages
Hit http://bh.archive.ubuntu.com intrepid/restricted Packages
Hit http://bh.archive.ubuntu.com intrepid/main Sources                        
Hit http://security.ubuntu.com intrepid-security/universe Packages            
Hit http://security.ubuntu.com intrepid-security/universe Sources           
Hit http://security.ubuntu.com intrepid-security/multiverse Packages        
Hit http://bh.archive.ubuntu.com intrepid/restricted Sources                
Hit http://bh.archive.ubuntu.com intrepid/universe Packages                    
Hit http://bh.archive.ubuntu.com intrepid/universe Sources                     
Hit http://bh.archive.ubuntu.com intrepid/multiverse Packages                  
Hit http://bh.archive.ubuntu.com intrepid/multiverse Sources                   
Hit http://security.ubuntu.com intrepid-security/multiverse Sources            
Fetched 192B in 8s (22B/s)                                                     
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://bh.archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://bh.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
looi76@looi76-laptop:~$ 
```

What is the problem?

---

### Post by jerome1232 on 2008-12-16
I would try and switch servers, goto System -> Administration -> Software Sources, drop the 'download from:' box and select other, now tell it to find a good server or just choose another one.

---

### Post by Michael.Godawski on 2008-12-16
Try to switch the server to the main server, and run sudo apt-get update again.
System > Administration > Software Sources > Download from

---

### Post by hfranco on 2008-12-16
Have you ran?

```
sudo apt-get update
```

---

### Post by donkyhotay on 2008-12-16
Synaptic was unable verify that one of the repository servers were legitimate. Specifically the hash files and key's didn't match. This is most commonly caused by a transmission error between the ubuntu repositories and synaptic. I would just try updating synaptic again.

---

### Post by looi76 on 2008-12-16
I have change the server but I still think there is something wrong! check out what I got:

```
looi76@looi76-laptop:~$ sudo apt-get update
[sudo] password for looi76: 
Hit http://us.archive.ubuntu.com intrepid Release.gpg
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-security Release.gpg
Ign http://us.archive.ubuntu.com intrepid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release
Hit http://us.archive.ubuntu.com intrepid-updates Release                    
Hit http://us.archive.ubuntu.com intrepid-security Release                   
Get:1 http://us.archive.ubuntu.com intrepid/main Packages [1254kB]           
Get:2 http://us.archive.ubuntu.com intrepid/restricted Packages [8420B]        
Get:3 http://us.archive.ubuntu.com intrepid/main Sources [505kB]               
Get:4 http://us.archive.ubuntu.com intrepid/restricted Sources [3113B]         
Get:5 http://us.archive.ubuntu.com intrepid/universe Packages [4516kB]         
Get:6 http://us.archive.ubuntu.com intrepid/universe Sources [1981kB]          
Get:7 http://us.archive.ubuntu.com intrepid/multiverse Packages [192kB]        
Get:8 http://us.archive.ubuntu.com intrepid/multiverse Sources [95.8kB]        
Get:9 http://us.archive.ubuntu.com intrepid-updates/main Packages [254kB]      
Get:10 http://us.archive.ubuntu.com intrepid-updates/restricted Packages [3852B]
Get:11 http://us.archive.ubuntu.com intrepid-updates/main Sources [79.3kB]     
Get:12 http://us.archive.ubuntu.com intrepid-updates/restricted Sources [1169B]
Get:13 http://us.archive.ubuntu.com intrepid-updates/universe Packages [29.2kB]
Get:14 http://us.archive.ubuntu.com intrepid-updates/universe Sources [5727B]  
Get:15 http://us.archive.ubuntu.com intrepid-updates/multiverse Packages [1922B]
Get:16 http://us.archive.ubuntu.com intrepid-updates/multiverse Sources [14B]  
Get:17 http://us.archive.ubuntu.com intrepid-security/main Packages [36.3kB]   
Get:18 http://us.archive.ubuntu.com intrepid-security/restricted Packages [1805B]
Get:19 http://us.archive.ubuntu.com intrepid-security/main Sources [11.7kB]    
Get:20 http://us.archive.ubuntu.com intrepid-security/restricted Sources [571B]
Get:21 http://us.archive.ubuntu.com intrepid-security/universe Packages [13.8kB]
Get:22 http://us.archive.ubuntu.com intrepid-security/universe Sources [1617B] 
Get:23 http://us.archive.ubuntu.com intrepid-security/multiverse Packages [14B]
Get:24 http://us.archive.ubuntu.com intrepid-security/multiverse Sources [14B] 
Fetched 8850kB in 6min26s (22.9kB/s)                                           
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
looi76@looi76-laptop:~$ 
```

---

### Post by Michael.Godawski on 2008-12-16
see here:


[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/282270](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/282270)
[/LIST]

switching the source should finally solve this out.

---

### Post by looi76 on 2008-12-16
How can I switch the source?

---

### Post by Kareeser on 2008-12-16
You did once already. Give the command a try again.

---

### Post by uos on 2009-03-06
> **jerome1232 said:**
> I would try and switch servers, goto System -> Administration -> Software Sources, drop the 'download from:' box and select other, now tell it to find a good server or just choose another one.


thank you very much as this help me from a big headache
(apt-key net-update , apt-get update, ..., etc)

it was just easy as just changed the server to US MAIN SERVER.....

my thanks to you ... :P

---

### Post by uos on 2009-03-06
> **jerome1232 said:**
> I would try and switch servers, goto System -> Administration -> Software Sources, drop the 'download from:' box and select other, now tell it to find a good server or just choose another one.


thank you very much as this help me from a big headache
(apt-key net-update , apt-get update, ..., etc)

it was just easy as just changed the server to US MAIN SERVER.....

my thanks to you ... :P

---

