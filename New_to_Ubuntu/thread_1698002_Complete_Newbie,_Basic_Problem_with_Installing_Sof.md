---
title: "Complete Newbie, Basic Problem with Installing Software"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by 122lettie on 2011-03-01
Hi,

Having another go at Ubuntu after a bad experience last year. I've installed 10.10 on a new machine, but I'm still having the same basic problem. I can't install any software on it. 

When I try and install anything from the repository, it tells me it failed to download the repository information, and tells me to check my Internet connection. My Internet connection is fine, through ethernet. Could there be something blocking its attempts to get the files? Any advice anyone?

Thanks

---

### Post by matt_symes on 2011-03-01
Hi

Do you have any net connectivity ? Can you view web pages ? Can you ping google ?

```
ping -c 3 8.8.8.8
```

Can you ping your router ?

Are you connected via wireless or wired ? 

Have you tried a different mirror to get the software ?

Need more info really.

Kind regards

---

### Post by 122lettie on 2011-03-01
> **matt_symes said:**
> Hi

Do you have any net connectivity ? Can you view web pages ? Can you ping google ?

```
ping -c 3 8.8.8.8
```Can you ping your router ?

Are you connected via wireless or wired ? 

Have you tried a different mirror to get the software ?

Need more info really.

Kind regards

Yes, i have fine net connectivity. Wired connection. I've tried lots of different software in the repository from different sources.

When i put that code into a terminal I got 

Usage: ping [-LRUbdfnqrvVaAD] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface]
            [-M pmtudisc-hint] [-m mark] [-S sndbuf]
            [-T tstamp-options] [-Q tos] [hop1 ...] destination


Thanks for your answer :)

---

### Post by matt_symes on 2011-03-01
Hi

> When i put that code into a terminal I got 

Usage: ping [-LRUbdfnqrvVaAD] [-c count] [-i interval] [-w deadline]
[-p pattern] [-s packetsize] [-t ttl] [-I interface]
[-M pmtudisc-hint] [-m mark] [-S sndbuf]
[-T tstamp-options] [-Q tos] [hop1 ...] destination

Are you sure you typed it correctly. From my terminal

```
matthew@matthew-laptop:~$ ping -c 3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=51 time=28.0 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=51 time=29.3 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=50 time=26.2 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 26.290/27.911/29.371/1.277 ms
matthew@matthew-laptop:~$
``` 

That will check you can see the Google server.

So just to be sure you have fine internet connectivity and can view web pages.

Is update manager working ?
is synaptic package manager working ?
Is the software centre working ?

Open a terminal and type

```
sudo apt-get update
```

Post the results back here.

Kind regards

---

### Post by lfforman on 2011-03-01
Ok, where you are? I had something similar since i am in brasil and installed ubuntu in portuguese the mirror for software channels was directed to some local place here in brazil I changed it to the main canonical software channel and worked like a charm.

the ping command you should enter is 

"ping -c 4 8.8.8.8"

did you installed anything else?

LF

---

### Post by 122lettie on 2011-03-01
> **matt_symes said:**
> Hi



Are you sure you typed it correctly. From my terminal

```
matthew@matthew-laptop:~$ ping -c 3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=51 time=28.0 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=51 time=29.3 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=50 time=26.2 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 26.290/27.911/29.371/1.277 ms
matthew@matthew-laptop:~$
```That will check you can see the Google server.

So just to be sure you have fine internet connectivity and can view web pages.

Is update manager working ?
is synaptic package manager working ?
Is the software centre working ?

Open a terminal and type

```
sudo apt-get update
```Post the results back here.

Kind regards

Okay:

```
lettie@lettie-W5A:~$ ping -c 4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3024ms

```

Then ```
lettie@lettie-W5A:~$ sudo apt-get update
[sudo] password for lettie: 
Ign http://extras.ubuntu.com maverick Release.gpg                              
Ign http://archive.canonical.com maverick Release.gpg                          
Ign http://gb.archive.ubuntu.com maverick Release.gpg                          
Ign http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB           
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://extras.ubuntu.com maverick Release                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB 
Ign http://extras.ubuntu.com maverick/main Sources                             
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://extras.ubuntu.com maverick/main i386 Packages             
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB 
Ign http://extras.ubuntu.com maverick/main Sources                   
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Ign http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB   
Err http://extras.ubuntu.com maverick/main Sources                             
  409  Conflict
Ign http://security.ubuntu.com maverick-security Release             
Err http://extras.ubuntu.com maverick/main i386 Packages                       
  409  Conflict
Ign http://security.ubuntu.com maverick-security/main Sources/DiffIndex        
Ign http://gb.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://security.ubuntu.com maverick-security/restricted Sources/DiffIndex
Ign http://security.ubuntu.com maverick-security/universe Sources    
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://security.ubuntu.com maverick-security/multiverse Sources            
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_GB
Ign http://security.ubuntu.com maverick-security/main i386 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.canonical.com maverick Release                              
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
Ign http://archive.canonical.com maverick/partner Sources            
Ign http://security.ubuntu.com maverick-security/universe i386 Packages
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://archive.canonical.com maverick/partner i386 Packages      
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.canonical.com maverick/partner Sources            
Ign http://security.ubuntu.com maverick-security/main Sources
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Ign http://archive.canonical.com maverick/partner i386 Packages      
Ign http://security.ubuntu.com maverick-security/restricted Sources
Ign http://gb.archive.ubuntu.com maverick Release                    
Ign http://security.ubuntu.com maverick-security/universe Sources    
Err http://archive.canonical.com maverick/partner Sources
  409  Conflict
Ign http://gb.archive.ubuntu.com maverick-updates Release            
Ign http://security.ubuntu.com maverick-security/multiverse Sources  
Err http://archive.canonical.com maverick/partner i386 Packages      
  409  Conflict
Ign http://security.ubuntu.com maverick-security/main i386 Packages
Ign http://gb.archive.ubuntu.com maverick/main Sources                        
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages     
Ign http://gb.archive.ubuntu.com maverick/restricted Sources
Ign http://security.ubuntu.com maverick-security/universe i386 Packages
Ign http://gb.archive.ubuntu.com maverick/universe Sources
Ign http://gb.archive.ubuntu.com maverick/multiverse Sources
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com maverick/main i386 Packages
Ign http://security.ubuntu.com maverick-security/main Sources
Ign http://gb.archive.ubuntu.com maverick/restricted i386 Packages
Ign http://security.ubuntu.com maverick-security/restricted Sources
Ign http://gb.archive.ubuntu.com maverick/universe i386 Packages
Err http://security.ubuntu.com maverick-security/universe Sources
  409  Conflict [IP: 91.189.92.167 80]
Ign http://gb.archive.ubuntu.com maverick/multiverse i386 Packages
Err http://security.ubuntu.com maverick-security/multiverse Sources
  409  Conflict [IP: 91.189.92.167 80]
Ign http://security.ubuntu.com maverick-security/main i386 Packages
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages
Err http://security.ubuntu.com maverick-security/universe i386 Packages
  409  Conflict [IP: 91.189.92.166 80]
Err http://security.ubuntu.com maverick-security/multiverse i386 Packages
  409  Conflict [IP: 91.189.92.166 80]
Ign http://gb.archive.ubuntu.com maverick-updates/main Sources
Err http://security.ubuntu.com maverick-security/main Sources
  409  Conflict [IP: 91.189.92.166 80]
Ign http://gb.archive.ubuntu.com maverick-updates/restricted Sources          
Err http://security.ubuntu.com maverick-security/restricted Sources
  409  Conflict [IP: 91.189.92.166 80]
Err http://security.ubuntu.com maverick-security/main i386 Packages
  409  Conflict [IP: 91.189.92.166 80]
Ign http://gb.archive.ubuntu.com maverick-updates/universe Sources
Err http://security.ubuntu.com maverick-security/restricted i386 Packages
  409  Conflict [IP: 91.189.92.167 80]
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse Sources
Ign http://gb.archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com maverick/main Sources
Ign http://gb.archive.ubuntu.com maverick/restricted Sources
Ign http://gb.archive.ubuntu.com maverick/universe Sources
Ign http://gb.archive.ubuntu.com maverick/multiverse Sources
Ign http://gb.archive.ubuntu.com maverick/main i386 Packages
Ign http://gb.archive.ubuntu.com maverick/restricted i386 Packages
Ign http://gb.archive.ubuntu.com maverick/universe i386 Packages
Ign http://gb.archive.ubuntu.com maverick/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/main Sources
Ign http://gb.archive.ubuntu.com maverick-updates/restricted Sources
Ign http://gb.archive.ubuntu.com maverick-updates/universe Sources
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse Sources
Ign http://gb.archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Err http://gb.archive.ubuntu.com maverick/main Sources
  409  Conflict
Err http://gb.archive.ubuntu.com maverick/restricted Sources
  409  Conflict
Err http://gb.archive.ubuntu.com maverick/universe Sources
  409  Conflict
Err http://gb.archive.ubuntu.com maverick/multiverse Sources
  409  Conflict
Err http://gb.archive.ubuntu.com maverick/main i386 Packages
  409  Conflict
Err http://gb.archive.ubuntu.com maverick/restricted i386 Packages
  409  Conflict
Err http://gb.archive.ubuntu.com maverick/universe i386 Packages
  409  Conflict
Err http://gb.archive.ubuntu.com maverick/multiverse i386 Packages
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/main Sources
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/restricted Sources
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/universe Sources
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/multiverse Sources
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/main i386 Packages
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages
  409  Conflict
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  409  Conflict

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz  409  Conflict

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz  409  Conflict [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz  409  Conflict [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz  409  Conflict [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz  409  Conflict [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.167 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz  409  Conflict

E: Some index files failed to download, they have been ignored, or old ones used instead.
lettie@lettie-W5A:~$ 
```

I can browse and view webpages, I'm on it just now. I can't install any updates or software

Thank you for your help.

---

### Post by matt_symes on 2011-03-01
Hi

That's quite odd. I think a look at you sources file might be useful. Please post the output of

```
cat /etc/apt/sources.list
```

Also i am concerned you could not ping 8.8.8.8. Try this instead and post the output back here.

```
ping -c 3 gb.archive.ubuntu.com
```

I take it you are based in the UK ?

Kind regards

---

### Post by powertower on 2011-03-01
I have this problem at work behind our proxy. Are you behind a proxy? If you know your proxy address the syntax to resolve the problem is "export http_proxy=proxyaddress:proxyport

---

### Post by 122lettie on 2011-03-02
> **matt_symes said:**
> Hi

That's quite odd. I think a look at you sources file might be useful. Please post the output of

```
cat /etc/apt/sources.list
```Also i am concerned you could not ping 8.8.8.8. Try this instead and post the output back here.

```
ping -c 3 gb.archive.ubuntu.com
```I take it you are based in the UK ?

Kind regards

Okay...

```
lettie@lettie-W5A:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

```

And

```
lettie@lettie-W5A:~$ ping -c 3 gb.archive.ubuntu.com
PING gb.archive.ubuntu.com (194.169.254.10) 56(84) bytes of data.

--- gb.archive.ubuntu.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms

lettie@lettie-W5A:~$ 

```

Yeah, UK. Thank you so much for taking the time to look at this!

---

### Post by 122lettie on 2011-03-02
> **powertower said:**
> I have this problem at work behind our proxy. Are you behind a proxy? If you know your proxy address the syntax to resolve the problem is "export http_proxy=proxyaddress:proxyport

Hi, yes I think I am behind a proxy, as I'm on a university residence internet system. My automatic proxy configuration URL is `[http://wwwcache.lancs.ac.uk](http://wwwcache.lancs.ac.uk)'

When I put it into the syntax you gave me, I got back `[http://wwwcache.lancs.ac.uk](http://wwwcache.lancs.ac.uk)' not a "valid identifier." Could you give me the exact syntax with that cache.lancs thing in it?

Thank you  :)

---

### Post by houseworkshy on 2011-03-02
You could try System>Administration>Software sources  and then click on the "download from..." which is on the first tab, choose other and let the system scan for the best server.  If you are using a laptop does the machine work elsewhere than the Uni?

---

### Post by matt_symes on 2011-03-02
Hi

Well your sources.list file looks fine so i would also suggest it's a proxy issue.

Here are 2 tutorials about how to set the proxy for apt-get in Ubuntu/Debian when behind a proxy.

[http://www.unixmen.com/linux-tutorials/939-configure-apt-get-to-work-behind-a-proxy-in-ubuntu-lucid-](http://www.unixmen.com/linux-tutorials/939-configure-apt-get-to-work-behind-a-proxy-in-ubuntu-lucid-)

[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

Have a read through. Any questions then post back.

What browser are you using and have you set proxy settings for that ?

Kind regards

---

### Post by 122lettie on 2011-03-02
This is the error message I get when I try to download anything from the repository

```
W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  409  Conflict
, W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  409  Conflict
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz  409  Conflict [IP: 91.189.92.167 80]
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz  409  Conflict [IP: 91.189.92.167 80]
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.166 80]
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.166 80]
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz  409  Conflict [IP: 91.189.92.166 80]
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz  409  Conflict [IP: 91.189.92.166 80]
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.166 80]
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  409  Conflict
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.167 80]
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz  409  Conflict
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz  409  Conflict
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz  409  Conflict
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  409  Conflict
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  409  Conflict
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  409  Conflict
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  409  Conflict
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz  409  Conflict
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz  409  Conflict
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz  409  Conflict
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz  409  Conflict
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz  409  Conflict
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz  409  Conflict
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz  409  Conflict
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz  409  Conflict
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by 122lettie on 2011-03-02
> **matt_symes said:**
> Hi

Well your sources.list file looks fine so i would also suggest it's a proxy issue.

Here are 2 tutorials about how to set the proxy for apt-get in Ubuntu/Debian when behind a proxy.

[http://www.unixmen.com/linux-tutorials/939-configure-apt-get-to-work-behind-a-proxy-in-ubuntu-lucid-](http://www.unixmen.com/linux-tutorials/939-configure-apt-get-to-work-behind-a-proxy-in-ubuntu-lucid-)

[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

Have a read through. Any questions then post back.

What browser are you using and have you set proxy settings for that ?

Kind regards

Thank you.

I added ```
export HTTP_PROXY=http://wwwcache.lancs.ac.uk.net:8080/

export FTP_PROXY=http://wwwcache.lancs.ac.uk.net:8080/
```

at the bottom of 
**/etc/bash.bashrc**
Does that seem right? I don't have a username/password for it, and I didn't know the port but the first tutorial said it would probably be 8080.

I still get the same error message from the software respository, but I'll restart and see what happens.

Thanks for your help.

---

### Post by 122lettie on 2011-03-02
> **houseworkshy said:**
> You could try System>Administration>Software sources  and then click on the "download from..." which is on the first tab, choose other and let the system scan for the best server.  If you are using a laptop does the machine work elsewhere than the Uni?

Hi, I don't have Software Sources option in my System>Administration menu.

I haven't been able to try it anywhere else, just with this ethernet connection.

Thanks

---

### Post by houseworkshy on 2011-03-02
That is strange.  Try System>Administration>Synaptic Package Manager  Then click on settings at the top, On the box which pops up the the first tab should be Ubuntu software ( it opens on that tab anyway ).  There is a drop down menu next to &#8220;Download from&#8221;, click the down arrow and choose &#8220;other&#8221;.  Another window will pop up click &#8220;select best server&#8221; and your system should start scanning for it.  Then choose server to use it.  You will be asked to reload the list and that may be it.

The software sources menu item really should be there.  It's worth looking at System>Preferances>main menu.  If you want an item to show put a tick next to it, if not don't.

Also be sure that you are in the admin' account, for obvious reasons guests can't install.

---

### Post by 122lettie on 2011-03-02
> **houseworkshy said:**
> That is strange.  Try System>Administration>Synaptic Package Manager  Then click on settings at the top, On the box which pops up the the first tab should be Ubuntu software ( it opens on that tab anyway ).  There is a drop down menu next to “Download from”, click the down arrow and choose “other”.  Another window will pop up click “select best server” and your system should start scanning for it.  Then choose server to use it.  You will be asked to reload the list and that may be it.

The software sources menu item really should be there.  It's worth looking at System>Preferances>main menu.  If you want an item to show put a tick next to it, if not don't.

When I press Select Best Server, I get

 No suitable download server was found. Check your internet connection. But my internet connection is fine, I'm browsing on it right now! I don't understand.

Thanks for your help anyway

---

### Post by houseworkshy on 2011-03-02
How about the software firewall?  In Ubuntu this is ufw, generally it is not turned on and the when it is the default will certainly allow updates etc.  It could have been messed up somehow.  So you could open a terminal and try "sudo ufw status" It will ask for your password.  Unless you have turned it on it probably won't be ( I would actually, with "sudo ufw default deny" then "sudo ufw enable" ).

---

### Post by houseworkshy on 2011-03-02
It could be that your admin at uni has blocked it at the router/network level and you need to talk to them.  Or try connecting from elsewhere and all is well.

As you can browse and are new to the system there are some useful links here 
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

I found the pocket guide very helpful in getting started.

This is another very good start and another freebie

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

### Post by 122lettie on 2011-03-02
> **houseworkshy said:**
> How about the software firewall?  In Ubuntu this is ufw, generally it is not turned on and the when it is the default will certainly allow updates etc.  It could have been messed up somehow.  So you could open a terminal and try "sudo ufw status" It will ask for your password.  Unless you have turned it on it probably won't be ( I would actually, with "sudo ufw default deny" then "sudo ufw enable" ).

Okay, I've done ```
lettie@lettie-W5A:~$ 
lettie@lettie-W5A:~$ sudo ufw status
[sudo] password for lettie: 
Status: inactive
lettie@lettie-W5A:~$ sudo ufw default deny
Default incoming policy changed to 'deny'
(be sure to update your rules accordingly)
lettie@lettie-W5A:~$ sudo ufw enable
Firewall is active and enabled on system startup
lettie@lettie-W5A:~$ 

```

Still can't download software, but I'll restart and see if works. My uni admin are ridiculously unhelpful :(

Thanks

---

### Post by 122lettie on 2011-03-02
Still failing to download repository information :(

---

### Post by matt_symes on 2011-03-02
Hi

Open a terminal and type

```
sudo iptables -F
```

to flush any rules you may have.

Try port 80; the http port in your .bashrc file.

```
export HTTP_PROXY=http://wwwcache.lancs.ac.uk.net:80
export FTP_PROXY=http://wwwcache.lancs.ac.uk.net:80
```

I think they might have closed most of the ports. As you can browse hopefully port 80 should be open.

Reload your .bashrc file (it needs both dots separated by a space)

```
. .bashrc
```

then

```
sudo apt-get update
sudo apt-get upgrade
```

Kind regards

---

### Post by 122lettie on 2011-03-03
> **matt_symes said:**
> Hi

Open a terminal and type

```
sudo iptables -F
```to flush any rules you may have.

Try port 80; the http port in your .bashrc file.

```
export HTTP_PROXY=http://wwwcache.lancs.ac.uk.net:80
export FTP_PROXY=http://wwwcache.lancs.ac.uk.net:80
```I think they might have closed most of the ports. As you can browse hopefully port 80 should be open.

Reload your .bashrc file (it needs both dots separated by a space)

```
. .bashrc
```then

```
sudo apt-get update
sudo apt-get upgrade
```Kind regards

Thanks for your help.

I did ```
sudo iptables -F
```

That stopped my internet working, so I couldn't load any webpages. I restarted, and I was able to load webpages again. Then I did

```
lettie@lettie-W5A:~$ sudo gedit /etc/bash.bashrc
[sudo] password for lettie: 
Sorry, try again.
[sudo] password for lettie: 
lettie@lettie-W5A:~$ . .bashrc
lettie@lettie-W5A:~$ sudo apt-get update
Ign http://archive.canonical.com maverick Release.gpg                          
Ign http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://gb.archive.ubuntu.com maverick Release.gpg                          
Ign http://extras.ubuntu.com maverick Release.gpg
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_GB    
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://extras.ubuntu.com maverick Release                                  
Ign http://archive.canonical.com maverick Release                              
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB 
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
Ign http://extras.ubuntu.com maverick/main Sources                             
Ign http://archive.canonical.com maverick/partner Sources                      
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://archive.canonical.com maverick/partner i386 Packages                
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB 
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://archive.canonical.com maverick/partner Sources                      
Ign http://extras.ubuntu.com maverick/main Sources
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.canonical.com maverick/partner i386 Packages                
Ign http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB   
Err http://archive.canonical.com maverick/partner Sources                      
  409  Conflict
Err http://extras.ubuntu.com maverick/main Sources                             
  409  Conflict
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com maverick-updates Release.gpg                  
Err http://archive.canonical.com maverick/partner i386 Packages                
  409  Conflict
Err http://extras.ubuntu.com maverick/main i386 Packages                       
  409  Conflict
Ign http://security.ubuntu.com maverick-security Release             
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://security.ubuntu.com maverick-security/main Sources/DiffIndex       
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://security.ubuntu.com maverick-security/restricted Sources/DiffIndex 
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://security.ubuntu.com maverick-security/universe Sources
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
Ign http://security.ubuntu.com maverick-security/multiverse Sources           
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://security.ubuntu.com maverick-security/main i386 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://security.ubuntu.com maverick-security/universe i386 Packages
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages     
Ign http://gb.archive.ubuntu.com maverick Release
Ign http://gb.archive.ubuntu.com maverick-updates Release
Ign http://security.ubuntu.com maverick-security/main Sources
Ign http://security.ubuntu.com maverick-security/restricted Sources           
Ign http://gb.archive.ubuntu.com maverick/main Sources
Ign http://security.ubuntu.com maverick-security/universe Sources             
Ign http://gb.archive.ubuntu.com maverick/restricted Sources
Ign http://security.ubuntu.com maverick-security/multiverse Sources           
Ign http://gb.archive.ubuntu.com maverick/universe Sources                    
Ign http://security.ubuntu.com maverick-security/main i386 Packages           
Ign http://gb.archive.ubuntu.com maverick/multiverse Sources                  
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages
Ign http://gb.archive.ubuntu.com maverick/main i386 Packages                  
Ign http://security.ubuntu.com maverick-security/universe i386 Packages       
Ign http://gb.archive.ubuntu.com maverick/restricted i386 Packages
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages     
Ign http://gb.archive.ubuntu.com maverick/universe i386 Packages
Ign http://security.ubuntu.com maverick-security/main Sources                 
Ign http://gb.archive.ubuntu.com maverick/multiverse i386 Packages            
Ign http://security.ubuntu.com maverick-security/restricted Sources
Ign http://gb.archive.ubuntu.com maverick-updates/main Sources
Err http://security.ubuntu.com maverick-security/universe Sources
  409  Conflict [IP: 91.189.92.166 80]
Ign http://gb.archive.ubuntu.com maverick-updates/restricted Sources
Err http://security.ubuntu.com maverick-security/multiverse Sources           
  409  Conflict [IP: 91.189.92.166 80]
Ign http://gb.archive.ubuntu.com maverick-updates/universe Sources            
Ign http://security.ubuntu.com maverick-security/main i386 Packages           
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse Sources          
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/main i386 Packages
Err http://security.ubuntu.com maverick-security/universe i386 Packages       
  409  Conflict [IP: 91.189.92.167 80]
Ign http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages    
Err http://security.ubuntu.com maverick-security/multiverse i386 Packages     
  409  Conflict [IP: 91.189.92.167 80]
Ign http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages      
Err http://security.ubuntu.com maverick-security/main Sources
  409  Conflict [IP: 91.189.92.167 80]
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages    
Err http://security.ubuntu.com maverick-security/restricted Sources           
  409  Conflict [IP: 91.189.92.167 80]
Ign http://gb.archive.ubuntu.com maverick/main Sources
Err http://security.ubuntu.com maverick-security/main i386 Packages
  409  Conflict [IP: 91.189.92.167 80]
Ign http://gb.archive.ubuntu.com maverick/restricted Sources 
Err http://security.ubuntu.com maverick-security/restricted i386 Packages
  409  Conflict [IP: 91.189.92.166 80]
Ign http://gb.archive.ubuntu.com maverick/universe Sources
Ign http://gb.archive.ubuntu.com maverick/multiverse Sources
Ign http://gb.archive.ubuntu.com maverick/main i386 Packages
Ign http://gb.archive.ubuntu.com maverick/restricted i386 Packages
Ign http://gb.archive.ubuntu.com maverick/universe i386 Packages
Ign http://gb.archive.ubuntu.com maverick/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/main Sources
Ign http://gb.archive.ubuntu.com maverick-updates/restricted Sources
Ign http://gb.archive.ubuntu.com maverick-updates/universe Sources
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse Sources
Ign http://gb.archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Err http://gb.archive.ubuntu.com maverick/main Sources  
  409  Conflict
Err http://gb.archive.ubuntu.com maverick/restricted Sources
  409  Conflict
Err http://gb.archive.ubuntu.com maverick/universe Sources
  409  Conflict
Err http://gb.archive.ubuntu.com maverick/multiverse Sources
  409  Conflict
Err http://gb.archive.ubuntu.com maverick/main i386 Packages
  409  Conflict
Err http://gb.archive.ubuntu.com maverick/restricted i386 Packages
  409  Conflict
Err http://gb.archive.ubuntu.com maverick/universe i386 Packages
  409  Conflict
Err http://gb.archive.ubuntu.com maverick/multiverse i386 Packages
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/main Sources
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/restricted Sources
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/universe Sources
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/multiverse Sources
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/main i386 Packages
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages
  409  Conflict
Err http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages
  409  Conflict
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz  409  Conflict

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  409  Conflict

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz  409  Conflict [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz  409  Conflict [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz  409  Conflict [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz  409  Conflict [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.166 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz  409  Conflict

E: Some index files failed to download, they have been ignored, or old ones used instead.
lettie@lettie-W5A:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lettie@lettie-W5A:~$ 

```

And got a load of errors. I really don't understand this! I tried changing my proxy settings to no proxy, but that stopped me from loading webpages. 

I just can't get a connection to any of the software sources.

Thanks

---

### Post by matt_symes on 2011-03-03
Hi

> I tried changing my proxy settings to no proxy, but that stopped me from loading webpages.   

Yes it's the proxy that's causing the problem i think. 

Flushing iptables in this situation was not a good suggestion. My bad. It was late.

I will do some research for you.

Do you know if your proxy requires authentication with your user name and password ?

Kind regards

---

### Post by matt_symes on 2011-03-03
Hi

Alright. Lets try a different approach. You can set the http proxy in .gconf settings under system.

Open a terminal and type (copy and paste if you want)

```
gconftool-2 --type bool -s /system/http_proxy/use_http_proxy true
gconftool-2 --type string -s /system/http_proxy/host http://wwwcache.lancs.ac.uk.net
sudo apt-get update

```

if that does not work type this line.

```
gconftool-2 --type int -s /system/http_proxy/port 80
sudo apt-get update
```

to reset the above values if they don't work type

```
gconftool-2 --recursive-unset /system/http_proxy
```

Is authentication required for the proxy ?

Kind regards

---

### Post by 122lettie on 2011-03-03
> **matt_symes said:**
> Hi

Alright. Lets try a different approach. You can set the http proxy in .gconf settings under system.

Open a terminal and type (copy and paste if you want)

```
gconftool-2 --type bool -s /system/http_proxy/use_http_proxy true
gconftool-2 --type string -s /system/http_proxy/host http://wwwcache.lancs.ac.uk.net
sudo apt-get update

```if that does not work type this line.

```
gconftool-2 --type int -s /system/http_proxy/port 80
sudo apt-get update
```to reset the above values if they don't work type

```
gconftool-2 --recursive-unset /system/http_proxy
```Is authentication required for the proxy ?

Kind regards

Thank you so much for all the time you've spent on this!

I installed Linux Mint Julia today, and I get exactly the same problem with the repository on that. The proxy doesn't need any authentication - I don't have a username/password.

I don't suppose you would happen to know the relevant commands for Linux (asking a lot here, I know!). If not, I won't have time tonight, but I'll wipe it and put Ubuntu back tomorrow to try those ones.

Thanks

---

### Post by matt_symes on 2011-03-03
Hi

> I don't suppose you would happen to know the relevant commands for Linux (asking a lot here, I know!). If not, I won't have time tonight, but I'll wipe it and put Ubuntu back tomorrow to try those ones.

If you mean for Linux Mint, it should be the same gconftool-2 commands i gave you for Ubuntu entered into a terminal (I think. I don't use Mint).

It would seem the IT staff there are useless when it comes to support (but maybe i judge them too quickly).

Do you ever get the feeling you are banging your head against a brick wall ? :P . Still let's not give up yet eh ?

Kind regards

---

### Post by col48 on 2011-03-03
Nothing to contribute, except that this current thread on 'General Help' seems to be about the same basic issue - no solution there, yet, either.


[http://ubuntuforums.org/showthread.php?t=1428035](http://ubuntuforums.org/showthread.php?t=1428035)

---

### Post by houseworkshy on 2011-03-03
I've searched google on this one focusing on Error 409 and found rather a lot.

I know this may not be directly relevant as I've never heard of an ISP thinking this way about Ubuntu updates but the info from the link below may point the way to an area of useful enquiry.

[http://www.checkupdown.com/status/E409.html](http://www.checkupdown.com/status/E409.html)

It could be that this problem can only be solved at the system network admin level as that is what sits between you and the ISP.  Also "man netstat" in the terminal could give some ideas about diagnostics.  Networking is something I know practically nothing about yet so don't be put off by the link ;- this is possably a spurious post.
 
Just ideas and at least the bump may call in the troops.

I searched again with +error +409 +synaptic +network and found more relevant results.  I don't have time to comb through them all now but have posted a sample one below, unsolved but another idea.

[http://askubuntu.com/questions/5949/network-proxy-is-not-applied](http://askubuntu.com/questions/5949/network-proxy-is-not-applied)

I may just be fogging here, if so sorry.

---

### Post by 122lettie on 2011-03-03
> **houseworkshy said:**
> I've searched google on this one focusing on Error 409 and found rather a lot.

I know this may not be directly relevant as I've never heard of an ISP thinking this way about Ubuntu updates but the info from the link below may point the way to an area of useful enquiry.

[http://www.checkupdown.com/status/E409.html](http://www.checkupdown.com/status/E409.html)

It could be that this problem can only be solved at the system network admin level as that is what sits between you and the ISP.  Also "man netstat" in the terminal could give some ideas about diagnostics.  Networking is something I know practically nothing about yet so don't be put off by the link ;- this is possably a spurious post.
 
Just ideas and at least the bump may call in the troops.

I searched again with +error +409 +synaptic +network and found more relevant results.  I don't have time to comb through them all now but have posted a sample one below, you'll recognise the source :)

[http://askubuntu.com/questions/5949/network-proxy-is-not-applied](http://askubuntu.com/questions/5949/network-proxy-is-not-applied)

My problem is way too over my head for me to solve :( I did man netstat ```
   Active AX.25 sockets
       (this needs to be done by somebody who knows it)

NOTES
       Starting with Linux release 2.2 netstat -i does not show interface sta&#8208;
       tistics for alias interfaces. To get per alias interface  counters  you
       need to setup explicit rules using the ipchains(8) command.

FILES
       /etc/services -- The services translation file

       /proc  --  Mount  point  for the proc filesystem, which gives access to
       kernel status information via the following files.

       /proc/net/dev -- device information

       /proc/net/raw -- raw socket information

       /proc/net/tcp -- TCP socket information

       /proc/net/udp -- UDP socket information

       /proc/net/igmp -- IGMP multicast information
 Manual page netstat(8) line 289/356 87%

```

Thanks for your help

---

### Post by 122lettie on 2011-03-03
> **matt_symes said:**
> Hi

Alright. Lets try a different approach. You can set the http proxy in .gconf settings under system.

Open a terminal and type (copy and paste if you want)

```
gconftool-2 --type bool -s /system/http_proxy/use_http_proxy true
gconftool-2 --type string -s /system/http_proxy/host http://wwwcache.lancs.ac.uk.net
sudo apt-get update

```if that does not work type this line.

```
gconftool-2 --type int -s /system/http_proxy/port 80
sudo apt-get update
```to reset the above values if they don't work type

```
gconftool-2 --recursive-unset /system/http_proxy
```Is authentication required for the proxy ?

Kind regards

I did ```
lettie@lettie-W5A ~ $ gconftool-2 --type bool -s /system/http_proxy/use_http_proxy true
lettie@lettie-W5A ~ $ 
lettie@lettie-W5A ~ $ gconftool-2 --type string -s /system/http_proxy/host http://wwwcache.lancs.ac.uk.net
lettie@lettie-W5A ~ $ sudo apt-get update
Ign file: binary/ Release.gpg
Ign file:/usr/share/local-repository/ binary/ Translation-en                   
Ign file:/usr/share/local-repository/ binary/ Translation-en_GB                
Ign file: binary/ Release                                                      
Ign file: binary/ Packages                                                     
Ign file: binary/ Packages                                                     
Ign http://archive.canonical.com maverick Release.gpg                          
Ign http://packages.medibuntu.org maverick Release.gpg                         
Ign http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://archive.ubuntu.com maverick Release.gpg                             
Ign http://packages.linuxmint.com julia Release.gpg                            
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://packages.medibuntu.org/ maverick/free Translation-en                
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en             
Ign http://packages.linuxmint.com/ julia/import Translation-en                 
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_GB    
Ign http://packages.medibuntu.org/ maverick/free Translation-en_GB             
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB          
Ign http://packages.linuxmint.com/ julia/import Translation-en_GB              
Ign http://archive.canonical.com maverick Release                              
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en       
Ign http://packages.linuxmint.com/ julia/main Translation-en                   
Ign http://packages.linuxmint.com/ julia/main Translation-en_GB                
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
Ign http://archive.canonical.com maverick/partner i386 Packages/DiffIndex      
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_GB         
Ign http://packages.linuxmint.com/ julia/upstream Translation-en               
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.canonical.com maverick/partner i386 Packages                
Ign http://packages.medibuntu.org maverick Release
Ign http://packages.linuxmint.com/ julia/upstream Translation-en_GB            
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://archive.canonical.com maverick/partner i386 Packages                
Ign http://packages.medibuntu.org maverick/free i386 Packages/DiffIndex
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en         
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Err http://archive.canonical.com maverick/partner i386 Packages                
  409  Conflict
Ign http://packages.linuxmint.com julia Release                                
Ign http://packages.medibuntu.org maverick/non-free i386 Packages/DiffIndex    
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Ign http://packages.linuxmint.com julia/main i386 Packages/DiffIndex           
Ign http://packages.medibuntu.org maverick/free i386 Packages                  
Ign http://archive.ubuntu.com maverick-updates Release.gpg                     
Ign http://packages.linuxmint.com julia/upstream i386 Packages/DiffIndex       
Ign http://packages.medibuntu.org maverick/non-free i386 Packages              
Ign http://security.ubuntu.com maverick-security Release                       
Ign http://packages.linuxmint.com julia/import i386 Packages/DiffIndex         
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en     
Ign http://packages.medibuntu.org maverick/free i386 Packages                  
Ign http://security.ubuntu.com maverick-security/main i386 Packages/DiffIndex  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB  
Ign http://packages.linuxmint.com julia/main i386 Packages                     
Ign http://packages.medibuntu.org maverick/non-free i386 Packages    
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://packages.linuxmint.com julia/upstream i386 Packages                 
Err http://packages.medibuntu.org maverick/free i386 Packages        
  409  Conflict
Ign http://security.ubuntu.com maverick-security/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
Ign http://packages.linuxmint.com julia/import i386 Packages                   
Err http://packages.medibuntu.org maverick/non-free i386 Packages    
  409  Conflict
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://packages.linuxmint.com julia/main i386 Packages           
Ign http://security.ubuntu.com maverick-security/main i386 Packages            
Ign http://packages.linuxmint.com julia/upstream i386 Packages                 
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://packages.linuxmint.com julia/import i386 Packages                   
Ign http://security.ubuntu.com maverick-security/universe i386 Packages        
Err http://packages.linuxmint.com julia/main i386 Packages                     
  409  Conflict
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://archive.ubuntu.com maverick Release                       
Err http://packages.linuxmint.com julia/upstream i386 Packages                 
  409  Conflict
Ign http://security.ubuntu.com maverick-security/main i386 Packages            
Ign http://archive.ubuntu.com maverick-updates Release                         
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages
Err http://packages.linuxmint.com julia/import i386 Packages
  409  Conflict
Ign http://archive.ubuntu.com maverick/main i386 Packages/DiffIndex
Ign http://security.ubuntu.com maverick-security/universe i386 Packages       
Ign http://archive.ubuntu.com maverick/restricted i386 Packages/DiffIndex     
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://archive.ubuntu.com maverick/universe i386 Packages/DiffIndex
Err http://security.ubuntu.com maverick-security/main i386 Packages           
  409  Conflict [IP: 91.189.92.167 80]
Ign http://archive.ubuntu.com maverick/multiverse i386 Packages/DiffIndex     
Err http://security.ubuntu.com maverick-security/restricted i386 Packages
  409  Conflict [IP: 91.189.92.166 80]
Err http://security.ubuntu.com maverick-security/universe i386 Packages
  409  Conflict [IP: 91.189.92.166 80]
Ign http://archive.ubuntu.com maverick-updates/main i386 Packages/DiffIndex
Err http://security.ubuntu.com maverick-security/multiverse i386 Packages     
  409  Conflict [IP: 91.189.92.166 80]
Ign http://archive.ubuntu.com maverick-updates/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick/main i386 Packages
Ign http://archive.ubuntu.com maverick/restricted i386 Packages
Ign http://archive.ubuntu.com maverick/universe i386 Packages
Ign http://archive.ubuntu.com maverick/multiverse i386 Packages
Ign http://archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Ign http://archive.ubuntu.com maverick/main i386 Packages
Ign http://archive.ubuntu.com maverick/restricted i386 Packages
Ign http://archive.ubuntu.com maverick/universe i386 Packages
Ign http://archive.ubuntu.com maverick/multiverse i386 Packages
Ign http://archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Err http://archive.ubuntu.com maverick/main i386 Packages
  409  Conflict [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com maverick/restricted i386 Packages
  409  Conflict [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com maverick/universe i386 Packages
  409  Conflict [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com maverick/multiverse i386 Packages
  409  Conflict [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com maverick-updates/main i386 Packages
  409  Conflict [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com maverick-updates/restricted i386 Packages
  409  Conflict [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com maverick-updates/universe i386 Packages
  409  Conflict [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
  409  Conflict [IP: 91.189.88.46 80]
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://packages.medibuntu.org/dists/maverick/free/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://packages.medibuntu.org/dists/maverick/non-free/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://packages.linuxmint.com/dists/julia/main/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://packages.linuxmint.com/dists/julia/upstream/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://packages.linuxmint.com/dists/julia/import/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.166 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  409  Conflict [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  409  Conflict [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  409  Conflict [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz  409  Conflict [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz  409  Conflict [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz  409  Conflict [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz  409  Conflict [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
lettie@lettie-W5A ~ $ gconftool-2 --type int -s /system/http_proxy/port 8080
lettie@lettie-W5A ~ $ sudo apt-get update
Ign file: binary/ Release.gpg
Ign file:/usr/share/local-repository/ binary/ Translation-en                   
Ign file:/usr/share/local-repository/ binary/ Translation-en_GB                
Ign file: binary/ Release                                                      
Ign file: binary/ Packages                                                     
Ign file: binary/ Packages                                                     
Ign http://packages.linuxmint.com julia Release.gpg                            
Ign http://archive.ubuntu.com maverick Release.gpg                             
Ign http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://packages.medibuntu.org maverick Release.gpg                         
Ign http://archive.canonical.com maverick Release.gpg                          
Ign http://packages.medibuntu.org/ maverick/free Translation-en                
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en             
Ign http://packages.linuxmint.com/ julia/import Translation-en                 
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://packages.linuxmint.com/ julia/import Translation-en_GB              
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_GB    
Ign http://packages.medibuntu.org/ maverick/free Translation-en_GB             
Ign http://packages.linuxmint.com/ julia/main Translation-en                   
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Ign http://archive.canonical.com maverick Release                              
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_GB         
Ign http://packages.linuxmint.com/ julia/main Translation-en_GB                
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
Ign http://archive.canonical.com maverick/partner i386 Packages/DiffIndex      
Ign http://packages.linuxmint.com/ julia/upstream Translation-en               
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://packages.medibuntu.org maverick Release                   
Ign http://packages.linuxmint.com/ julia/upstream Translation-en_GB            
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://archive.canonical.com maverick/partner i386 Packages                
Ign http://packages.medibuntu.org maverick/free i386 Packages/DiffIndex        
Ign http://packages.linuxmint.com julia Release                                
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en         
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.canonical.com maverick/partner i386 Packages                
Ign http://packages.medibuntu.org maverick/non-free i386 Packages/DiffIndex    
Ign http://packages.linuxmint.com julia/main i386 Packages/DiffIndex           
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Err http://archive.canonical.com maverick/partner i386 Packages                
  409  Conflict
Ign http://packages.medibuntu.org maverick/free i386 Packages                  
Ign http://packages.linuxmint.com julia/upstream i386 Packages/DiffIndex       
Ign http://archive.ubuntu.com maverick-updates Release.gpg                     
Ign http://security.ubuntu.com maverick-security Release             
Ign http://packages.medibuntu.org maverick/non-free i386 Packages    
Ign http://packages.linuxmint.com julia/import i386 Packages/DiffIndex         
Ign http://security.ubuntu.com maverick-security/main i386 Packages/DiffIndex  
Ign http://packages.medibuntu.org maverick/free i386 Packages        
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB  
Ign http://packages.linuxmint.com julia/main i386 Packages                     
Ign http://packages.medibuntu.org maverick/non-free i386 Packages    
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://packages.linuxmint.com julia/upstream i386 Packages                 
Ign http://security.ubuntu.com maverick-security/universe i386 Packages/DiffIndex
Err http://packages.medibuntu.org maverick/free i386 Packages                  
  409  Conflict
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
Ign http://packages.linuxmint.com julia/import i386 Packages                   
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages/DiffIndex
Err http://packages.medibuntu.org maverick/non-free i386 Packages    
  409  Conflict
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://packages.linuxmint.com julia/main i386 Packages                     
Ign http://security.ubuntu.com maverick-security/main i386 Packages            
Ign http://packages.linuxmint.com julia/upstream i386 Packages                 
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://packages.linuxmint.com julia/import i386 Packages         
Ign http://security.ubuntu.com maverick-security/universe i386 Packages
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Err http://packages.linuxmint.com julia/main i386 Packages           
  409  Conflict
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://archive.ubuntu.com maverick Release                       
Err http://packages.linuxmint.com julia/upstream i386 Packages                 
  409  Conflict
Ign http://security.ubuntu.com maverick-security/main i386 Packages            
Err http://packages.linuxmint.com julia/import i386 Packages                   
  409  Conflict
Ign http://archive.ubuntu.com maverick-updates Release               
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages
Ign http://security.ubuntu.com maverick-security/universe i386 Packages
Ign http://archive.ubuntu.com maverick/main i386 Packages/DiffIndex
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://archive.ubuntu.com maverick/restricted i386 Packages/DiffIndex     
Err http://security.ubuntu.com maverick-security/main i386 Packages           
  409  Conflict [IP: 91.189.92.167 80]
Ign http://archive.ubuntu.com maverick/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick/multiverse i386 Packages/DiffIndex
Err http://security.ubuntu.com maverick-security/restricted i386 Packages
  409  Conflict [IP: 91.189.92.166 80]
Err http://security.ubuntu.com maverick-security/universe i386 Packages
  409  Conflict [IP: 91.189.92.166 80]
Ign http://archive.ubuntu.com maverick-updates/main i386 Packages/DiffIndex
Err http://security.ubuntu.com maverick-security/multiverse i386 Packages
  409  Conflict [IP: 91.189.92.166 80]
Ign http://archive.ubuntu.com maverick-updates/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick/main i386 Packages
Ign http://archive.ubuntu.com maverick/restricted i386 Packages
Ign http://archive.ubuntu.com maverick/universe i386 Packages
Ign http://archive.ubuntu.com maverick/multiverse i386 Packages
Ign http://archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Ign http://archive.ubuntu.com maverick/main i386 Packages
Ign http://archive.ubuntu.com maverick/restricted i386 Packages
Ign http://archive.ubuntu.com maverick/universe i386 Packages
Ign http://archive.ubuntu.com maverick/multiverse i386 Packages
Ign http://archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Err http://archive.ubuntu.com maverick/main i386 Packages
  409  Conflict [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com maverick/restricted i386 Packages
  409  Conflict [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com maverick/universe i386 Packages
  409  Conflict [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com maverick/multiverse i386 Packages
  409  Conflict [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com maverick-updates/main i386 Packages
  409  Conflict [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com maverick-updates/restricted i386 Packages
  409  Conflict [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com maverick-updates/universe i386 Packages
  409  Conflict [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
  409  Conflict [IP: 91.189.88.46 80]
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://packages.medibuntu.org/dists/maverick/free/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://packages.medibuntu.org/dists/maverick/non-free/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://packages.linuxmint.com/dists/julia/main/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://packages.linuxmint.com/dists/julia/upstream/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://packages.linuxmint.com/dists/julia/import/binary-i386/Packages.gz  409  Conflict

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.166 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  409  Conflict [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  409  Conflict [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  409  Conflict [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  409  Conflict [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz  409  Conflict [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz  409  Conflict [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz  409  Conflict [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz  409  Conflict [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
lettie@lettie-W5A ~ $ 

``` 

More errors...

Very much head + brick wall! And also I'm completely new to this, so I'm very stuck. Thank you :)

---

### Post by houseworkshy on 2011-03-03
Ah I'm on Ubuntu 10.04.1 lts, didn't remember that you are using mint at the moment, getting vauge sorry.  Actually haven't tried 10.10 yet as I prefer to stick with the long term support versions. I can understand the morter on the forehead effect,  not exactly beginner level.  When you swap back to Ubuntu "man netstat" simply brings up the manual page for the netstat command.  I was thinking that you could use it to glean some network information.  man is a useful command and, as a none expert ( sorry ), one of the ones I use most, typed in front of any command it tells you about it.  Actually it would work in a live cd session too.

I wish I could be more helpful.  By your proxy I'm guessing that you are a student with work to do.  There is a way of installing programs which is still open to you; .deb files.  These can be downloaded and then run, a bit like win.exe's.  One needs to be sure of the source though.

Safer would be to use a linux called Puppy which loads to ram, after which the boot medium can be ejected, and can have things installed to it.  One would have to do this on every session of course or have a collection of .pup's ( very like debs)  Also has a cd burner in it's software.  In the unlikely event that your installation cd is imperfect Puppy could get you out of the hole. It also has a differant style package manager so would provide a useful cross check which if it failed too would suggest to this not-quite-beginner that your unhelpful network admin may have to be forced to help.  It is amazing for it's size but definately fairly bare bones compaired to a full monty such as mint or Ubuntu.

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")

The thought being that you may need to get things done ( assignments for example ) which depend on software you haven't been able to put into Ubuntu while this is being worked out. 

When I was last at college there was a block on downloading....can you download?  Or is that the problem, updates are also downloads. I can imagine a college admin thinking "can't let the blighters do piracy etc so block all downloading p2p etc, now got to let windows updates through of course .. so malware next... anti virus yes....antispy ware yes ....firewall yes.  Good.   Where's that list of essential applications the Heads of department gave me?  Ah yes here it is... "Word, Acrobat, email, browser yep blah, blah, blah all the usual....ok done.....Oh so we're allowing social networking again are we...Well they're the bosses  , their funeral ..ok.......good to go.... done. What's this.... student request eh     'Ubuntu'?        How dare ..?    Oh it's a linux is it?  ....Doesn't sound like it........Nope....   still remember the last time we had a big virus hit.....and it was only the linux machines which stayed up.......What does that tell you eh?... I know what it tells me....hackers......not having any of that.            Next well...time for a pint or three I think"

 Could be.

---

### Post by 122lettie on 2011-03-04
> **houseworkshy said:**
> Ah I'm on Ubuntu 10.04.1 lts, didn't remember that you are using mint at the moment, getting vauge sorry.  Actually haven't tried 10.10 yet as I prefer to stick with the long term support versions. I can understand the morter on the forehead effect,  not exactly beginner level.  When you swap back to Ubuntu "man netstat" simply brings up the manual page for the netstat command.  I was thinking that you could use it to glean some network information.  man is a useful command and, as a none expert ( sorry ), one of the ones I use most, typed in front of any command it tells you about it.  Actually it would work in a live cd session too.

I wish I could be more helpful.  By your proxy I'm guessing that you are a student with work to do.  There is a way of installing programs which is still open to you; .deb files.  These can be downloaded and then run, a bit like win.exe's.  One needs to be sure of the source though.

Safer would be to use a linux called Puppy which loads to ram, after which the boot medium can be ejected, and can have things installed to it.  One would have to do this on every session of course or have a collection of .pup's ( very like debs)  Also has a cd burner in it's software.  In the unlikely event that your installation cd is imperfect Puppy could get you out of the hole. It also has a differant style package manager so would provide a useful cross check which if it failed too would suggest to this not-quite-beginner that your unhelpful network admin may have to be forced to help.  It is amazing for it's size but definately fairly bare bones compaired to a full monty such as mint or Ubuntu.

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

The thought being that you may need to get things done ( assignments for example ) which depend on software you haven't been able to put into Ubuntu while this is being worked out. 

When I was last at college there was a block on downloading....can you download?  Or is that the problem, updates are also downloads. I can imagine a college admin thinking "can't let the blighters do piracy etc so block all downloading p2p etc, now got to let windows updates through of course .. so malware next... anti virus yes....antispy ware yes ....firewall yes.  Good.   Where's that list of essential applications the Heads of department gave me?  Ah yes here it is... "Word, Acrobat, email, browser yep blah, blah, blah all the usual....ok done.....Oh so we're allowing social networking again are we...Well they're the bosses  , their funeral ..ok.......good to go.... done. What's this.... student request eh     'Ubuntu'?        How dare ..?    Oh it's a linux is it?  ....Doesn't sound like it........Nope....   still remember the last time we had a big virus hit.....and it was only the linux machines which stayed up.......What does that tell you eh?... I know what it tells me....hackers......not having any of that.            Next well...time for a pint or three I think"

 Could be.

I tried installing a .deb file off the Skype website, which opened in Packgage Installer, but "could not download all required files; please check your internet connection or installation medium."

There's not block on downloading at all. We have a 30GB quota. I'm not a Linux user by choice. I had a bit of a **** up with Windows. It's not exactly been the best introduction for me :(

I found this [http://wwww.ubuntuforums.org/showthread.php?t=1277234](http://wwww.ubuntuforums.org/showthread.php?t=1277234) which I think is my problem, and a couple of people resolved it. Can anyone here give me some nice simple step-by-step instructions to do what they described? Thanks

I'm going to email the university computing society and see if I can find anyone on campus running Linux....

---

### Post by houseworkshy on 2011-03-04
Sorry about the last para, was far too sleepy to be posting anywhere.  No one thinks like that anymore, feel embarassed about that bit now, wrong tone too.
Currently looking for some distro that has skype pre-installed.  

There is another way of installing called apt:url, this opens a package manager from a browser page.  Some think this method is potentially dangerous, including me. To my knowlage, the risk is still only a potential one so the following para is not relevent yet, even so as I am suggesting using this method here goes. 

The risk being that the apt:url askes for a password, as it should for an admin action, which gives the sudo command fifteen minets of grace period.  So if one then clicks on another one an install takes place without asking, *and* one is in the browser.  Clicking around during the fifteen minuets could some day be bad practive.  So, as the command initialted will complete even if the grace period has run out it, it may be a good idea to open a terminl and enter "sudo -k".   This terminates sudo privalages and restores the "being alerted and asked for password state".   

The chances of it working are slight, still package management based, but may be worth a go.  The online documentation for Ubuntu has some scattered through it so you could try one from this trusted source as test, and if it worked then try one for skype. 

[https://help.ubuntu.com/10.10](https://help.ubuntu.com/10.10)

There are some alternatives to skype which are compatable with its protocols.

There is an apt:url link for skype here.

[http://appnr.com](http://appnr.com)

---

### Post by col48 on 2011-03-05
If you know all you would need to install, can you find a friend off-campus who would let you use their broadband connection for a few hours?  This way you need not trouble the IT establishment at all.

---

### Post by 122lettie on 2011-03-05
> **houseworkshy said:**
> Sorry about the last para, was far too sleepy to be posting anywhere.  No one thinks like that anymore, feel embarassed about that bit now, wrong tone too.
Currently looking for some distro that has skype pre-installed.  

There is another way of installing called apt:url, this opens a package manager from a browser page.  Some think this method is potentially dangerous, including me. To my knowlage, the risk is still only a potential one so the following para is not relevent yet, even so as I am suggesting using this method here goes. 

The risk being that the apt:url askes for a password, as it should for an admin action, which gives the sudo command fifteen minets of grace period.  So if one then clicks on another one an install takes place without asking, *and* one is in the browser.  Clicking around during the fifteen minuets could some day be bad practive.  So, as the command initialted will complete even if the grace period has run out it, it may be a good idea to open a terminl and enter "sudo -k".   This terminates sudo privalages and restores the "being alerted and asked for password state".   

The chances of it working are slight, still package management based, but may be worth a go.  The online documentation for Ubuntu has some scattered through it so you could try one from this trusted source as test, and if it worked then try one for skype. 

[https://help.ubuntu.com/10.10](https://help.ubuntu.com/10.10)

There are some alternatives to skype which are compatable with its protocols.

There is an apt:url link for skype here.

[http://appnr.com](http://appnr.com)

I tried installing from [http://appnr.com/](http://appnr.com/) but it still fails to fetch the package information.

I don't know actually know anyone in town I'd feel comfortable asking :(

---

### Post by houseworkshy on 2011-03-05
Some internet caf[FONT=Liberation Serif, serif]é's may allow it, which would cost.  Museums usually have internet access too.  It would probably be cheaper to ring around first rather than hauling the pc around.   You could also put a note on the SU notice board explaining the problem and asking if you could borrow the connection of someone in digs rather than halls, might even have pleasant social side effects.[/FONT]
 

 [FONT=Liberation Serif, serif]You also have on the distro a messaging client, it may be able to access your Skype account.  I use pidgin which is why I'm not sure about it.  I think it's gwibber or something like that on 10.10.    It should certainly be able to go through google talk, aim, yahoo etc.  Could be a stop gap measure.[/FONT]
 

 [FONT=Liberation Serif, serif]I have a few friends who are offline.  Have used several methods, .deb files which are varied, some want a data version  to go in first after which the app can go in, some work in one and some just won't go unless one is online.  Skype seems to be in the later category.  Aptoncd is a nice way for when you are at home, can put all the bits one has installed onto a cd and use it like a repository at some future date.  I'd recommend using it in the vacations but not much use now.[/FONT]
 

 [FONT=Liberation Serif, serif]Until this is sorted out the way to go may be with puppy linux, this is the one I mentioned earlier which  can boot into ram.  The reason being that the files which one installs into can be simply downloaded and the installation is local.  One of my friends found that that was the only way he could get cinelerra onto his machine, couldn't find a non-techy way with offline Ubuntu.  So he now runs a live cd session with puppy, takes out the boot media when it has loaded and then puts in a cd which is full of .pets, effectively his repository.  I think that this may be the easiest way to run skype for you.  Puppy can also live on a flash stick.[/FONT]
 [FONT=Liberation Serif, serif]
[http://www.puppylinuxfaq.org/content/19/123/en/skype-pet.html](http://www.puppylinuxfaq.org/content/19/123/en/skype-pet.html) [/FONT] 
 

 [[FONT=Liberation Serif, serif]http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm[/FONT]]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")
 

 [FONT=Liberation Serif, serif]There was also a project to put repository files on a cd for offline Ubuntu but I can't find it, it may have fizzled.  It's not the best distro for offline machines.  I know you are not offline only effectively offline as far Ubuntu package managers are concearned.  There are some souped up versions of Ubuntu though, I'm sure that one has skype on it but so far I haven't found it, I'll let you know if I do.
[/FONT]

---

### Post by matt_symes on 2011-03-07
Ji

@122lettie. Did you manage to get it working ?

Kind regards

---

### Post by 122lettie on 2011-03-07
> **matt_symes said:**
> Ji

@122lettie. Did you manage to get it working ?

Kind regards

I didn't. But I emailed the computing society president and he said I could come to their next meeting on Wednesday and someone would have a look at it.

@houseworksky Thanks for your help, but I think I'm just going to leave it until someone more capable than me has a look at it.

---

### Post by matt_symes on 2011-03-07
Hi

There is something else to try.

```
sudo nano /etc/apt/apt.conf
```

and add this line

```
http::Proxy "http://wwwcache.lancs.ac.uk.net:**8080**"
```

or

```
Acquire::http::Proxy "http://wwwcache.lancs.ac.uk.net:**8080**"
```

Press Ctrl + o to save the file and ctrl + x to exit.

Then try 

```
sudo apt-get update
```

You can also try changing the port to 80. Highlighted in bold.

Kind regards

---

### Post by houseworkshy on 2011-03-07
Ok Lettie that's probably the wisest, unless studying operating systems is what you are at Uni' to do, it's all taking too long and studies come first, and socialisation second.  

Linux is actually easier than windows though it probably doesn't feel like when as a novice there's a problem and all one can do about it is enter never seen before commands in the terminal.  Usually everything simply works through the grapic user interphase, is very straight forward and one can worry about learning what's under the bonnet at leisure when you feel like it as all the applications simply work and you can just get on with things.  Please don't let a couple of bad experiances put you off, usually far less troublesome than other platforms.

If it turns out that the Ubuntu mirrors are simply blocked the extra weight of the computer society may help convince your network admin'.  Linux is probably the best system for students, many free applications, many editions geared to science, media, the theology of most major religions, design, engineering.  Anyone studying almost anything can set up a system geared to their feild of study and mostly for free.  Most things can save and open in the standard formats of other operating systems so that's no argument either.  Not quite so good for games as windows but getting there.  I would be very suprised if it was just blocked.  Excellent free resource.

When someone in the know gets to look at it please could you post back  and say what it is.  There is something unusual about that network  setup, downloading and the browser do work yet updating via port 80 is  blocked.  The information could get someone else out of the same hole,  I've a feeling there are going to be a lot more suffering from this one.


Good luck with the studies and have fun too, it is part of it.

---

### Post by 122lettie on 2011-03-14
Turns out I put an extra .net in the proxy address in the apt-get file thing...

All that was needed was to change the bash.rc and apt-get files, and change the proxy settings in Synaptic.

Thanks everyone for the help

---

### Post by houseworkshy on 2011-04-04
So you solved it, well done. Enjoy :)

---

