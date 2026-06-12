---
title: "[SOLVED] ipv6 (i think) isues: unable to connect to repo"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by M0phead on 2008-05-18
This is my seccond thread about what appears to be a continuously changing problem (or just a whole host of problems).
I orriginaly posted about browsing death ([http://ubuntuforums.org/showthread.php?t=796430&highlight=browsing+death](http://ubuntuforums.org/showthread.php?t=796430&highlight=browsing+death))
when firefox was experiencing some isues wherby it could not connect to web pages unless i typed in an ip adress instead of a web adress.
This was fixed by turning off ipv6 in firefox which is now working perfectly.
i then tried to update sympatic, which took some time so i decided to cancel.
i asked if there was any way of turning off ipv6 for entire computer and was refered to this thread: [http://ubuntuforums.org/showthread.php?t=87798&page=14](http://ubuntuforums.org/showthread.php?t=87798&page=14)
I followed both of the methods decribed in posts 131 and 133.
i then tried to up date again, leaving it for about an hour.
it failed (i think) and returned this:

ben@ben-desktop:~$ sudo apt-get update
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg
Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg
Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB
Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_GB
Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_GB
Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_GB
Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_GB
Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg
Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_GB
Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB
Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB
Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB
Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg
Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_GB
Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_GB
Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_GB
Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_GB
Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...sy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...sy/Release.gpg) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...es/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...es/Release.gpg) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...ts/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...ts/Release.gpg) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/...tion-en_GB.bz2) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.canonical.com/ubuntu/...sy/Release.gpg](http://archive.canonical.com/ubuntu/...sy/Release.gpg) Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.canonical.com/ubuntu/...tion-en_GB.bz2](http://archive.canonical.com/ubuntu/...tion-en_GB.bz2) Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/di...ty/Release.gpg](http://security.ubuntu.com/ubuntu/di...ty/Release.gpg) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/di...tion-en_GB.bz2](http://security.ubuntu.com/ubuntu/di...tion-en_GB.bz2) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/di...tion-en_GB.bz2](http://security.ubuntu.com/ubuntu/di...tion-en_GB.bz2) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/di...tion-en_GB.bz2](http://security.ubuntu.com/ubuntu/di...tion-en_GB.bz2) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/di...tion-en_GB.bz2](http://security.ubuntu.com/ubuntu/di...tion-en_GB.bz2) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

:confused::confused::confused::confused::confused::confused::confused:

---

### Post by M0phead on 2008-05-18
Has anyone seen something like this before?

---

### Post by The Cog on 2008-05-18
No. But the (1.0.0.0) puzzles me. Can you try the command
**ping us.archive.ubuntu.com**
and see what address it says it is pinging? It looks as though perhaps DNS is returning an address of 1.0.0.0 for that name, which I don't believe to be correct. Don't worry if the ping succeeds or not. Just make sure the IP address resolves OK.

---

### Post by M0phead on 2008-05-18
i get this:
ben@ben-desktop:~$ ping us.archive.ubuntu.com
PING us.archive.ubuntu.com (91.189.88.31) 56(84) bytes of data.
64 bytes from us.archive.ubuntu.com (91.189.88.31): icmp_seq=1 ttl=54 time=24.0 ms
64 bytes from us.archive.ubuntu.com (91.189.88.31): icmp_seq=2 ttl=54 time=20.3 ms
64 bytes from us.archive.ubuntu.com (91.189.88.31): icmp_seq=3 ttl=54 time=23.3 ms
64 bytes from us.archive.ubuntu.com (91.189.88.31): icmp_seq=4 ttl=54 time=21.6 ms
64 bytes from us.archive.ubuntu.com (91.189.88.31): icmp_seq=5 ttl=54 time=23.1 ms

---

### Post by M0phead on 2008-05-18
i just tried sudo apt-get update again and i think it may have worked...
it returned this after about 1 minute:
[B]Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Get: 1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                   
Get: 2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_GB [21.3kB]      
Get: 3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB               
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]            
Get: 5 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release [65.9kB]                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB     
Get: 6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_GB [2395B] 
Get: 7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_GB [4405B]   
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release [51.2kB]              
Get: 9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_GB [8133B] 
Get: 10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_GB          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB    
Get: 11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [191B]        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_GB        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_GB  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_GB    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_GB  
Get: 12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release [65.9kB]                    
Get: 13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release [58.5kB]            
Get: 14 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages [94.9kB]       
Get: 15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release [44.0kB]
Get: 16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages [1075kB]              
Get: 17 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages [14B]    
Get: 18 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources [17.9kB]        
Get: 19 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources [14B]     
Get: 20 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages [64.3kB]  
Get: 21 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources [9352B]     
Get: 22 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages [2880B]  
Get: 23 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources [812B]    
Get: 24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages [7664B]         
Get: 25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources [306kB]                
Get: 26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources [2120B]          
Get: 27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages [4065kB]          
Get: 28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources [1226kB]           
Get: 29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages [158kB]         
Get: 30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources [56.8kB]         
Get: 31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages [264kB]       
Get: 32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages [4263B] 
Get: 33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources [72.8kB]       
Get: 34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources [937B]   
Get: 35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages [88.6kB]  
Get: 36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources [14.4kB]   
Get: 37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages [9936B] 
Get: 38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources [1881B]  
Get: 39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages [30.2kB]    
Get: 40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages [14B] 
Get: 41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages [106kB] 
Get: 42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages [16.7kB]
Get: 43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Sources [9183B]      
Get: 44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Sources [14B]  
Get: 45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Sources [25.7kB] 
Get: 46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Sources [3665B]
Fetched 8058kB in 1m7s (119kB/s)                                               
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release](http://archive.canonical.com/ubuntu/dists/gutsy/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.[/B]

Does that mean it is now working?
if so, why?
i havent changed anything...

---

### Post by dmizer on 2008-05-18
step one: disable ipv6 according to the following link:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)

step two: you'll probably experince much better browsing if you use openDNS servers according to this link:
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

i suspect you're having problems steming from a flaky router.  the above two fixes should help you to get around even if the router's dns and ip stack is flaky.

---

