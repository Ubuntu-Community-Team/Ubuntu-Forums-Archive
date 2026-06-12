---
title: "[SOLVED] Networking and Downloading Packages Problem"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by CorvusViridis on 2008-08-14
Hi everyone,
I asked for help about this in the beginner forum a day ago ([http://ubuntuforums.org/showthread.php?t=888781](http://ubuntuforums.org/showthread.php?t=888781)), but it seems to me mine is a none standard problem. I'll try to explain, I'm sorry if I forget to mention something important, I'm really new to this:

It started with me not being able to connect to my school's wifi, I've got a BCM4318, this seems to be a standard problem, but the standard solutions don't seem to work, so the problem has to be somewhere else.

When I check the Administration -> Hardware Drivers box for my wireless driver, it tells me the system needs a restart; a restart doesn't change anything, though.

Apparently I'm having trouble downloading and installing (via the wired connection I'm using to write this post) any packages at all. For instance, trying to install the flashplayer:

```
klp@KLP-Cassiopeia:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
```

Trying to update the package installer:
```
klp@KLP-Cassiopeia:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for klp: 
Get:1 http://mirror.csclub.uwaterloo.ca hardy Release.gpg [191B]
Get:2 http://mirror.csclub.uwaterloo.ca hardy/main Translation-en_US
99% [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.71)]bzip2: (stdin) is not a bzip2 file.
Ign http://mirror.csclub.uwaterloo.ca hardy/main Translation-en_US
Get:3 http://mirror.csclub.uwaterloo.ca hardy/restricted Translation-en_US
52% [3 Translation-en_US bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (12bzip2: (stdin) is not a bzip2 file.
Ign http://mirror.csclub.uwaterloo.ca hardy/restricted Translation-en_US       
Get:4 http://mirror.csclub.uwaterloo.ca hardy/universe Translation-en_US       
36% [4 Translation-en_US bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (12bzip2: (stdin) is not a bzip2 file.
Ign http://mirror.csclub.uwaterloo.ca hardy/universe Translation-en_US         
Get:5 http://mirror.csclub.uwaterloo.ca hardy/multiverse Translation-en_US     
27% [5 Translation-en_US bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (12bzip2: (stdin) is not a bzip2 file.
Ign http://mirror.csclub.uwaterloo.ca hardy/multiverse Translation-en_US       
Get:6 http://mirror.csclub.uwaterloo.ca hardy-updates Release.gpg [189B]       
Get:7 http://mirror.csclub.uwaterloo.ca hardy-updates Release.gpg [189B]       
Get:8 http://mirror.csclub.uwaterloo.ca hardy-updates Release.gpg [189B]       
Get:9 http://mirror.csclub.uwaterloo.ca hardy-updates Release.gpg [189B]       
Get:10 http://mirror.csclub.uwaterloo.ca hardy-updates Release.gpg [189B]      
Get:11 http://mirror.csclub.uwaterloo.ca hardy-updates/main Translation-en_US  
23% [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.71)]    30B/s 3min16sbzip2: (stdin) is not a bzip2 file.
Ign http://mirror.csclub.uwaterloo.ca hardy-updates/main Translation-en_US     
Get:12 http://mirror.csclub.uwaterloo.ca hardy-updates/restricted Translation-en_US
20% [12 Translation-en_US bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (1bzip2: (stdin) is not a bzip2 file.
Ign http://mirror.csclub.uwaterloo.ca hardy-updates/restricted Translation-en_US
Get:13 http://mirror.csclub.uwaterloo.ca hardy-updates/universe Translation-en_US
19% [13 Translation-en_US bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (1bzip2: (stdin) is not a bzip2 file.
Ign http://mirror.csclub.uwaterloo.ca hardy-updates/universe Translation-en_US 
Get:14 http://mirror.csclub.uwaterloo.ca hardy-updates/multiverse Translation-en_US
17% [14 Translation-en_US bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (1bzip2: (stdin) is not a bzip2 file.
Ign http://mirror.csclub.uwaterloo.ca hardy-updates/multiverse Translation-en_US
Get:15 http://mirror.csclub.uwaterloo.ca hardy-security Release.gpg [189B]     
Get:16 http://mirror.csclub.uwaterloo.ca hardy-security Release.gpg [189B]     
Get:17 http://mirror.csclub.uwaterloo.ca hardy-security Release.gpg [189B]     
Get:18 http://mirror.csclub.uwaterloo.ca hardy-security/main Translation-en_US 
14% [18 Translation-en_US bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (1bzip2: (stdin) is not a bzip2 file.
Ign http://mirror.csclub.uwaterloo.ca hardy-security/main Translation-en_US    
Get:19 http://mirror.csclub.uwaterloo.ca hardy-security/restricted Translation-en_US
12% [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.71)]    31B/s 7min24sbzip2: (stdin) is not a bzip2 file.
Ign http://mirror.csclub.uwaterloo.ca hardy-security/restricted Translation-en_US
Get:20 http://mirror.csclub.uwaterloo.ca hardy-security/universe Translation-en_US
13% [20 Translation-en_US bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (1bzip2: (stdin) is not a bzip2 file.
Ign http://mirror.csclub.uwaterloo.ca hardy-security/universe Translation-en_US
Get:21 http://mirror.csclub.uwaterloo.ca hardy-security/multiverse Translation-en_US
12% [21 Translation-en_US bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (1bzip2: (stdin) is not a bzip2 file.
Ign http://mirror.csclub.uwaterloo.ca hardy-security/multiverse Translation-en_US
Get:22 http://mirror.csclub.uwaterloo.ca hardy Release [65.9kB]                
Ign http://mirror.csclub.uwaterloo.ca hardy Release                            
Get:23 http://mirror.csclub.uwaterloo.ca hardy-updates Release [58.5kB]        
Ign http://mirror.csclub.uwaterloo.ca hardy-updates Release                    
Get:24 http://mirror.csclub.uwaterloo.ca hardy-security Release [58.5kB]       
Ign http://mirror.csclub.uwaterloo.ca hardy-security Release                   
Get:25 http://mirror.csclub.uwaterloo.ca hardy/main Sources                    
90% [25 Sources bzip2 0] [Waiting for headers]                      28.6kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy/main Sources                       
  Sub-process bzip2 returned an error code (2)
Get:26 http://mirror.csclub.uwaterloo.ca hardy/restricted Sources              
90% [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.71)]      28.6kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy/restricted Sources                 
  Sub-process bzip2 returned an error code (2)
Get:27 http://mirror.csclub.uwaterloo.ca hardy/main Packages                   
90% [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.71)]      28.6kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy/main Packages                      
  Sub-process bzip2 returned an error code (2)
Get:28 http://mirror.csclub.uwaterloo.ca hardy/restricted Packages             
91% [28 Packages bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy/restricted Packages                
  Sub-process bzip2 returned an error code (2)
Get:29 http://mirror.csclub.uwaterloo.ca hardy/multiverse Sources              
91% [29 Sources bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy/multiverse Sources                 
  Sub-process bzip2 returned an error code (2)
Get:30 http://mirror.csclub.uwaterloo.ca hardy/universe Sources                
91% [30 Sources bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy/universe Sources                   
  Sub-process bzip2 returned an error code (2)
Get:31 http://mirror.csclub.uwaterloo.ca hardy/universe Packages               
91% [31 Packages bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy/universe Packages                  
  Sub-process bzip2 returned an error code (2)
Get:32 http://mirror.csclub.uwaterloo.ca hardy/multiverse Packages             
91% [32 Packages bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy/multiverse Packages                
  Sub-process bzip2 returned an error code (2)
Get:33 http://mirror.csclub.uwaterloo.ca hardy-updates/main Packages           
91% [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.71)]       962B/s 19sbzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-updates/main Packages              
  Sub-process bzip2 returned an error code (2)
Get:34 http://mirror.csclub.uwaterloo.ca hardy-updates/restricted Packages     
91% [34 Packages bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-updates/restricted Packages        
  Sub-process bzip2 returned an error code (2)
Get:35 http://mirror.csclub.uwaterloo.ca hardy-updates/restricted Sources      
91% [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.71)]       526B/s 35sbzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-updates/restricted Sources         
  Sub-process bzip2 returned an error code (2)
Get:36 http://mirror.csclub.uwaterloo.ca hardy-updates/main Sources            
91% [36 Sources bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-updates/main Sources               
  Sub-process bzip2 returned an error code (2)
Get:37 http://mirror.csclub.uwaterloo.ca hardy-updates/multiverse Sources      
91% [37 Sources bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-updates/multiverse Sources         
  Sub-process bzip2 returned an error code (2)
Get:38 http://mirror.csclub.uwaterloo.ca hardy-updates/universe Sources        
91% [38 Sources bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-updates/universe Sources           
  Sub-process bzip2 returned an error code (2)
Get:39 http://mirror.csclub.uwaterloo.ca hardy-updates/universe Packages       
91% [39 Packages bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-updates/universe Packages          
  Sub-process bzip2 returned an error code (2)
Get:40 http://mirror.csclub.uwaterloo.ca hardy-updates/multiverse Packages     
91% [40 Packages bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-updates/multiverse Packages        
  Sub-process bzip2 returned an error code (2)
Get:41 http://mirror.csclub.uwaterloo.ca hardy-security/main Packages          
91% [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.71)]       920B/s 20sbzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-security/main Packages             
  Sub-process bzip2 returned an error code (2)
Get:42 http://mirror.csclub.uwaterloo.ca hardy-security/restricted Packages    
91% [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.71)]       920B/s 20sbzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-security/restricted Packages       
  Sub-process bzip2 returned an error code (2)
Get:43 http://mirror.csclub.uwaterloo.ca hardy-security/restricted Sources     
91% [43 Sources bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-security/restricted Sources        
  Sub-process bzip2 returned an error code (2)
Get:44 http://mirror.csclub.uwaterloo.ca hardy-security/main Sources           
91% [44 Sources bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-security/main Sources              
  Sub-process bzip2 returned an error code (2)
Get:45 http://mirror.csclub.uwaterloo.ca hardy-security/multiverse Sources     
91% [45 Sources bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-security/multiverse Sources        
  Sub-process bzip2 returned an error code (2)
Get:46 http://mirror.csclub.uwaterloo.ca hardy-security/universe Sources       
92% [46 Sources bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134.bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-security/universe Sources          
  Sub-process bzip2 returned an error code (2)
Get:47 http://mirror.csclub.uwaterloo.ca hardy-security/universe Packages      
92% [47 Packages bzip2 0] [Connecting to mirror.csclub.uwaterloo.ca (129.97.134bzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-security/universe Packages         
  Sub-process bzip2 returned an error code (2)
Get:48 http://mirror.csclub.uwaterloo.ca hardy-security/multiverse Packages    
92% [48 Packages bzip2 0]                                           1236B/s 15sbzip2: (stdin) is not a bzip2 file.
Err http://mirror.csclub.uwaterloo.ca hardy-security/multiverse Packages       
  Sub-process bzip2 returned an error code (2)
Fetched 55.4kB in 1min8s (805B/s)                                              
W: GPG error: http://mirror.csclub.uwaterloo.ca hardy Release: The following signatures were invalid: NODATA 2
W: GPG error: http://mirror.csclub.uwaterloo.ca hardy-updates Release: The following signatures were invalid: NODATA 2
W: GPG error: http://mirror.csclub.uwaterloo.ca hardy-security Release: The following signatures were invalid: NODATA 2
W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/main/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/restricted/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/main/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/restricted/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/multiverse/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/universe/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/universe/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/multiverse/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/main/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/restricted/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/main/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/multiverse/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/universe/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/universe/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/multiverse/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/main/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/restricted/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/restricted/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/main/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/multiverse/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/universe/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/multiverse/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
klp@KLP-Cassiopeia:~$ 
```

(Sorry this is so long, I just can't tell what's important and what isn't.)

Can anyone make sense of this? I've tried switching download servers, but that doesn't help. I feel like I'm missing something obvious :(

---

### Post by SpaceTeddy on 2008-08-14
this looks like bzip2 is missing... maybe you want to go to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/"), download the bzip2 package manually and reinstall it...

just a guess... really... otherwise, no idea :(

---

### Post by CorvusViridis on 2008-08-14
Thanks, I tried it. It doesn't seem to be it, though. It was already installed, so I reinstalled it, but

```
sudo apt-get update && sudo apt-get upgrade
```

still gets me same error message.

---

### Post by SpaceTeddy on 2008-08-14
yeah - if i had bothered scrolling left i would have seen that too (i have the code box - it cuts off stuff.
Anyways - can you open this url :

> [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/main/binary-i386/Packages.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/main/binary-i386/Packages.bz2) with your browser ? do you have any proxies for apt installed (don't ask me where they are configured). This looks like the download of the files fails. The most likely reason for that is that you get a "file not found" back instead of the expected packet lists. 
Also, what happens if you try a different mirror ?

i am doing heavy guessing here...

---

### Post by CorvusViridis on 2008-08-14
My school's internet filter isn't allowing .bz2-files (Nicht zulaessige Dateinamenerweiterung: .bz2). I'm going to have to go and talk to them in person. I'll tell when I've tried. Thanks so far...

---

### Post by CorvusViridis on 2008-08-14
And this was exactly the problem: DansGuardian doesn't allow .bz2 files. However, the error messages didn't say why they couldn't be downloaded, so only after to open the url you told me to try did I realize there was a problem with the firewall. I got it solved by asking it-support to free access to one of the download mirrors, and now it works. Apparently, I can also change the sources.list to ftp instead of http ([http://ubuntuforums.org/showthread.php?t=9944&highlight=gzip+bzip2+error](http://ubuntuforums.org/showthread.php?t=9944&highlight=gzip+bzip2+error)). This works for now, though!

Thank you!

---

