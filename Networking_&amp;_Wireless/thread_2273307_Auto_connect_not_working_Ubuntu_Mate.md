---
title: "Auto connect not working Ubuntu Mate"
date: 2015-04-12
forum: Networking &amp; Wireless
---

### Post by Krillo on 2015-04-12
Hi all

I had a look in the [SIZE=1]"Official Flavours Support[/SIZE] Forum" but didn't find any appropriate subforum, so I'll post here again...

I re-installed, removed xubuntu and went with ubuntu mate which seems really nice :)

I'm having a couple of problems

1) Auto connect is not working, I have to choose wifi every reboot.
2) Software updater gets alot of errors trying to connect to repos (usually seems to hang during "checking for updates")
3) It boots one of like 3 times.
4) Because I can't download updates, I can't dim the screen (can't install xbacklight)

Thanks, and sorry for the not so detailed problem descriptions.

```
user@laptop:~$ sudo apt-get update
[sudo] password for user: 
Ign http://ftp.lysator.liu.se utopic InRelease                                 
Ign http://ftp.lysator.liu.se utopic-updates InRelease                         
Ign http://ftp.lysator.liu.se utopic-security InRelease                        
Ign http://archive.canonical.com utopic InRelease
Hit http://ftp.lysator.liu.se utopic Release.gpg
Get:1 http://ftp.lysator.liu.se utopic-updates Release.gpg [933 B]
Get:2 http://ftp.lysator.liu.se utopic-security Release.gpg [933 B]            
Hit http://archive.canonical.com utopic Release.gpg                            
Hit http://archive.canonical.com utopic Release                                
Hit http://ftp.lysator.liu.se utopic Release                                   
Get:3 http://ftp.lysator.liu.se utopic-updates Release [63,5 kB]               
Hit http://downloads.sourceforge.net all InRelease                         
Get:4 http://ftp.lysator.liu.se utopic-security Release [63,5 kB]              
Hit http://archive.canonical.com utopic/partner Sources                        
Hit http://archive.canonical.com utopic/partner amd64 Packages                 
Hit http://archive.canonical.com utopic/partner i386 Packages                  
Get:5 http://downloads.sourceforge.net all/main amd64 Packages [855 B]         
Ign http://archive.canonical.com utopic/partner Translation-en                 
Get:6 http://ftp.lysator.liu.se utopic/main amd64 Packages [1 331 kB]          
Get:7 http://downloads.sourceforge.net all/main i386 Packages [969 B]
Get:8 http://ftp.lysator.liu.se utopic/restricted amd64 Packages [12,2 kB]     
Get:9 http://ftp.lysator.liu.se utopic/universe amd64 Packages [6 175 kB]      
Ign http://downloads.sourceforge.net all/main Translation-en_US                
Ign http://downloads.sourceforge.net all/main Translation-en                   
Get:10 http://ftp.lysator.liu.se utopic-updates/restricted amd64 Packages [8 496 B]
Get:11 http://ftp.lysator.liu.se utopic-updates/universe amd64 Packages [90,8 kB]
Get:12 http://ftp.lysator.liu.se utopic-updates/multiverse amd64 Packages [4 139 B]
Get:13 http://ftp.lysator.liu.se utopic-updates/main i386 Packages [245 kB]
Get:14 http://ftp.lysator.liu.se utopic-updates/restricted i386 Packages [8 438 B]
Get:15 http://ftp.lysator.liu.se utopic-updates/universe i386 Packages [90,7 kB]
Get:16 http://ftp.lysator.liu.se utopic-updates/multiverse i386 Packages [4 325 B]
Get:17 http://ftp.lysator.liu.se utopic-updates/main Translation-en [114 kB]
Get:18 http://ftp.lysator.liu.se utopic-updates/multiverse Translation-en [1 943 B]
Get:19 http://ftp.lysator.liu.se utopic-security/main i386 Packages [215 kB]    
Get:20 http://ftp.lysator.liu.se utopic-security/restricted i386 Packages [14,1 kB]
Get:21 http://ftp.lysator.liu.se utopic-security/universe i386 Packages [77,5 kB]
Get:22 http://ftp.lysator.liu.se utopic-security/multiverse i386 Packages [4 102 B]
Err http://ftp.lysator.liu.se utopic/multiverse amd64 Packages
  Bad header line [IP: 130.236.254.50 80]
Err http://ftp.lysator.liu.se utopic/main i386 Packages
  Bad header line [IP: 130.236.254.50 80]
Err http://ftp.lysator.liu.se utopic/restricted i386 Packages
  Bad header line [IP: 130.236.254.50 80]
Err http://ftp.lysator.liu.se utopic/universe i386 Packages
  Bad header line [IP: 130.236.254.50 80]
Hit http://ftp.lysator.liu.se utopic/main Translation-en
Hit http://ftp.lysator.liu.se utopic/multiverse Translation-en
Hit http://ftp.lysator.liu.se utopic/restricted Translation-en
Hit http://ftp.lysator.liu.se utopic/universe Translation-en
Err http://ftp.lysator.liu.se utopic-updates/main amd64 Packages
  404  Not Found [IP: 130.236.254.50 80]
Get:23 http://ftp.lysator.liu.se utopic-updates/restricted Translation-en [1 797 B]
Hit http://ftp.lysator.liu.se utopic-updates/universe Translation-en
Err http://ftp.lysator.liu.se utopic-security/main amd64 Packages
  404  Not Found [IP: 130.236.254.50 80]
Err http://ftp.lysator.liu.se utopic-security/restricted amd64 Packages        
  404  Not Found [IP: 130.236.254.50 80]
Err http://ftp.lysator.liu.se utopic-security/universe amd64 Packages          
  404  Not Found [IP: 130.236.254.50 80]
Err http://ftp.lysator.liu.se utopic-security/multiverse amd64 Packages        
  404  Not Found [IP: 130.236.254.50 80]
Hit http://ftp.lysator.liu.se utopic-security/main Translation-en              
Hit http://ftp.lysator.liu.se utopic-security/multiverse Translation-en        
Hit http://ftp.lysator.liu.se utopic-security/restricted Translation-en        
Hit http://ftp.lysator.liu.se utopic-security/universe Translation-en          
Err http://ftp.lysator.liu.se utopic/multiverse i386 Packages                  
  404  Not Found [IP: 130.236.254.50 80]
Fetched 2 351 kB in 8min 8s (4 814 B/s)                                        
W: Failed to fetch http://ftp.lysator.liu.se/ubuntu/dists/utopic/multiverse/binary-amd64/Packages  Bad header line [IP: 130.236.254.50 80]

W: Failed to fetch http://ftp.lysator.liu.se/ubuntu/dists/utopic/main/binary-i386/Packages  Bad header line [IP: 130.236.254.50 80]

W: Failed to fetch http://ftp.lysator.liu.se/ubuntu/dists/utopic/restricted/binary-i386/Packages  Bad header line [IP: 130.236.254.50 80]

W: Failed to fetch http://ftp.lysator.liu.se/ubuntu/dists/utopic/universe/binary-i386/Packages  Bad header line [IP: 130.236.254.50 80]

W: Failed to fetch http://ftp.lysator.liu.se/ubuntu/dists/utopic/multiverse/binary-i386/Packages  404  Not Found [IP: 130.236.254.50 80]

W: Failed to fetch http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/binary-i386/Packages  Hash Sum mismatch

W: Failed to fetch http://ftp.lysator.liu.se/ubuntu/dists/utopic-updates/main/binary-amd64/Packages  404  Not Found [IP: 130.236.254.50 80]

W: Failed to fetch http://ftp.lysator.liu.se/ubuntu/dists/utopic-security/main/binary-amd64/Packages  404  Not Found [IP: 130.236.254.50 80]

W: Failed to fetch http://ftp.lysator.liu.se/ubuntu/dists/utopic-security/restricted/binary-amd64/Packages  404  Not Found [IP: 130.236.254.50 80]

W: Failed to fetch http://ftp.lysator.liu.se/ubuntu/dists/utopic-security/universe/binary-amd64/Packages  404  Not Found [IP: 130.236.254.50 80]

W: Failed to fetch http://ftp.lysator.liu.se/ubuntu/dists/utopic-security/multiverse/binary-amd64/Packages  404  Not Found [IP: 130.236.254.50 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
user@laptop:~$ 


```

---

### Post by Vladlenin5000 on 2015-04-12
What is that ftp.lysatot. ... repository and what is it doing there? It doesn't work so you better start by removing it and reloading the sources.

---

### Post by Krillo on 2015-04-12
FYI:
[ftp://ftp.lysator.liu.se/](ftp://ftp.lysator.liu.se/)
[www.liu.se]("http://www.liu.se")

This server was suggested when using the Download from > Other > Select best server.
It wasn't best :D

Strangely enough, I get different suggestions every time.

---

### Post by Krillo on 2015-04-12
> **Krillo said:**
> 
4) Because I can't download updates, I can't dim the screen (can't install xbacklight)


This point solved by updating server. Still funny a non working server is suggested :-k

---

