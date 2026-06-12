---
title: "Requires installation of untrusted packages"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by RoRoRed on 2009-11-27
Hey out there in the void of the ether,

I want to install application using the ubuntu software centre;
but all i get is this error message:

Requires installation of untrusted packages
"The action would require the installation of packages from not authenticated sources."

can anyone explain in simple words (and commands) how to solve the issue?

thanks!

---

### Post by Excedio on 2009-11-27
Seems that you are not the only one with this problem.
 
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/475075](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/475075)

---

### Post by bodhi.zazen on 2009-11-27
[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

Basically, packages are signed with a GPG key and most likely that message is because you need to import a key.

We need more information, including the exact error message and the contents of /etc/apt/sources.list

---

### Post by RoRoRed on 2009-11-27
Now it works,

well  I checked the box for source code (in the ubuntu register)

thanks for your help & sorry to have wasted your time ^_^

---

### Post by stormsurge on 2009-12-11
I have the same problem... Can you make the solution simple? Sorry guys...  Thanks!

---

### Post by bodhi.zazen on 2009-12-11
> **stormsurge said:**
> I have the same problem... Can you make the solution simple? Sorry guys...  Thanks!

See the link I gave you. It works for the default repositories.

If you need more specific assistance you need to provide us with more details. What repository are you trying to add ? what error message are you getting ?

---

### Post by -=hazard=- on 2009-12-16
Same error here. Installing from Synaptic. Same error from Software Center. Repository Universe. I made some screens.

---

### Post by NoaHall on 2009-12-16
> **-=hazard=- said:**
> Same error here. Installing from Synaptic. Same error from Software Center. Repository Universe. I made some screens.

Can you post the output of ```
cat /etc/apt/sources.list
``` and then ```
gpg --list-keys
```  from the terminal?

---

### Post by -=hazard=- on 2009-12-16
```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.ynet.sk/ubuntu/ karmic main restricted universe
deb-src http://ubuntu.ynet.sk/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.ynet.sk/ubuntu/ karmic-updates main restricted universe
deb-src http://ubuntu.ynet.sk/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.ynet.sk/ubuntu/ karmic multiverse
deb-src http://ubuntu.ynet.sk/ubuntu/ karmic multiverse
deb http://ubuntu.ynet.sk/ubuntu/ karmic-updates multiverse
deb-src http://ubuntu.ynet.sk/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://pl.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://pl.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://ubuntu.ynet.sk/ubuntu/ karmic-security main restricted universe
deb-src http://ubuntu.ynet.sk/ubuntu/ karmic-security main restricted
deb http://ubuntu.ynet.sk/ubuntu/ karmic-security multiverse
deb-src http://ubuntu.ynet.sk/ubuntu/ karmic-security multiverse
deb http://packages.medibuntu.org/ karmic free non-free
```

I have only 1 key, that is not the VLC one. I have added only mediubuntu repository, the others are just default.

---

### Post by -=hazard=- on 2009-12-16
Ok, problem solved by changing the repository to the main one.

---

### Post by NoaHall on 2009-12-16
It might be a problem due to the servers you're using. Try going to System -> Admin -> Software Sources -> Select best server

---

### Post by -=hazard=- on 2009-12-16
> **NoaHall said:**
> It might be a problem due to the servers you're using. Try going to System -> Admin -> Software Sources -> Select best server

Yeah just did it. And they were already the best servers. Anyway now selected the main servers and works fine. Thanks though.

---

### Post by NoaHall on 2009-12-16
> **-=hazard=- said:**
> Yeah just did it. And they were already the best servers. Anyway now selected the main servers and works fine. Thanks though.

Ah, it's a server problem then. You could select the second best from the list, they might work.

---

### Post by -=hazard=- on 2009-12-16
> **NoaHall said:**
> Ah, it's a server problem then. You could select the second best from the list, they might work.

Yes did it, selected the main server and works fine :)

---

### Post by NoaHall on 2009-12-16
> **-=hazard=- said:**
> Yes did it, selected the main server and works fine :)

I know :) But what I'm saying, you could select another server than the main server, and the one you had problems with, and it should be okay :)

---

### Post by -=hazard=- on 2009-12-16
> **NoaHall said:**
> I know :) But what I'm saying, you could select another server than the main server, and the one you had problems with, and it should be okay :)

Yes I know :P But main server is cool too. I have no big differences in speed between best server and the main one, though I prefer german servers.

---

### Post by Krealle on 2009-12-17
> **stormsurge said:**
> I have the same problem... Can you make the solution simple? Sorry guys...  Thanks!
Go to system>Administration>Software sources>Uncheck Multiverse Worked for me ;)

---

### Post by philinux on 2009-12-17
> **Krealle said:**
> Go to system>Administration>Software sources>Uncheck Multiverse Worked for me ;)

Not a good idea. Lots of important packages reside in multiverse including java and ubuntu-restricted-extras to name two.

---

### Post by -=hazard=- on 2009-12-20
> **philinux said:**
> Not a good idea. Lots of important packages reside in multiverse including java and ubuntu-restricted-extras to name two.

True. He might try as I did, by selecting the main server, might be some server aren't updated and this cause the problem.

---

### Post by linx-fan on 2010-02-12
I was getting this error, after a regular update. googled the forums and changed the Download from to Main server in "Syste->Administration-Software Sources".

Now I I am able to install the software from Ubuntu software center.:KS

---

### Post by Hado on 2010-02-21
[SIZE=2]I had precisely the same error.  And switching to the main server made the proper fix.
Thanks guys![/SIZE]

---

### Post by anugrahbasketball on 2010-05-16
I'm also facing problem while installing programs through "Ubuntu Software Center" it gives me the message: "requires installation  of untrusted packages" 

and when i run "sudo apt-get update" it gives me the following message: (the error message is at the bottom.)

Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
  
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Get:3 [http://repository.cairo-dock.org](http://repository.cairo-dock.org) karmic Release.gpg [1,026B]             
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Get:4 [http://repository.cairo-dock.org](http://repository.cairo-dock.org) karmic/cairo-dock Translation-en_US [1,026B]
99% [Connecting to in.archive.ubuntu.com (111.91.91.37)]bzip2: (stdin) is not a bzip2 file.
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) karmic/cairo-dock Translation-en_US       
Get:5 [http://repository.cairo-dock.org](http://repository.cairo-dock.org) karmic Release [1,026B]                 
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) karmic Release                            
Get:6 [http://repository.cairo-dock.org](http://repository.cairo-dock.org) karmic/cairo-dock Packages [1,026B]    
98% [6 Packages bzip2 0] [Connecting to in.archive.ubuntu.com (111.91.91.37)]bzip2: (stdin) is not a bzip2 file.
Err [http://repository.cairo-dock.org](http://repository.cairo-dock.org) karmic/cairo-dock Packages              
  Sub-process /bin/bzip2 returned an error code (2)
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release.gpg [189B]                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Translation-en_US
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release [65.9kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Sources
Fetched 4,602B in 2min 0s (38B/s)
Reading package lists... Done
[COLOR=Red]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5

W: GPG error: [http://repository.cairo-dock.org](http://repository.cairo-dock.org) karmic Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/karmic/Release](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/karmic/Release)  

W: Failed to fetch [http://repository.cairo-dock.org/ubuntu/dists/karmic/cairo-dock/binary-i386/Packages.bz2](http://repository.cairo-dock.org/ubuntu/dists/karmic/cairo-dock/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR]

Your help will be highly appreciated.

Thanks in anticipation.


> **bodhi.zazen said:**
> See the link I gave you. It works for the default repositories.

If you need more specific assistance you need to provide us with more details. What repository are you trying to add ? what error message are you getting ?

---

### Post by bodhi.zazen on 2010-05-16
You will need to add the keys to those repositories manually.

[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%27s%20keys%20to%20your%20system](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%27s%20keys%20to%20your%20system)

[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

[http://www.glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en](http://www.glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en)

---

### Post by anugrahbasketball on 2010-05-19
> **bodhi.zazen said:**
> You will need to add the keys to those repositories manually.

[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%27s%20keys%20to%20your%20system](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%27s%20keys%20to%20your%20system)

[https://launchpad.net/~awn-testing/+archive/ppa]("https://launchpad.net/%7Eawn-testing/+archive/ppa")

[http://www.glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en](http://www.glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en)



Sir,

Thank you for helping me out.

the links you posted and all the information in there was new to me. so i didn't know really what to do. but I followed as much as I can and hopefully have fixed it all.

here's the information I get now when I run *"sudo apt-get update*" in the terminal:
Is that OK. I guess nothing wrong now, its just problem on the server, they no more have the pages, which is my computer shows 404 error.


Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Translation-en_US                 
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Translation-en_US 
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Translation-en_US             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages       
  404  Not Found
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Sources
W: Failed to fetch [http://ppa.launchpad.net/anugrah-hp/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/anugrah-hp/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/anugrah/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/anugrah/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by bodhi.zazen on 2010-05-19
You seem to be using a lot of ppa ....

What ppa is that ? You need to go to the ppa and confirm you have the correct line in /etc/apt/sources.list

See the links I already gave you and the project home / ppa page.

If your sources.list is correct, you will need to file a bug report with the project so they can fix their repo (ppa).

---

### Post by asuastrophysics on 2010-06-03
Grrrrr WTF???

I get this message no matter what I try to install. From OpenOffice to Gnome Tetris. Nothing installs at all, even if it's in the main repository.

I don't know how to go about getting every single PPA key needed. All I did was install (supported) updates from update-manager and now nothing will install.

So thanks a lot for another great update. I think I'm just going to remove update-manager and never update anything ever again. All it does is just break stuff.  

](*,)](*,)](*,)](*,)
lol why can't anything ever be simple?

---

### Post by coolman98 on 2010-09-28
fix worked for me in maverick

---

### Post by fabiocunha on 2010-10-03
II cannot install anything. Always giving me some sort of error. Not even the update manager works. Please help

---

### Post by bodhi.zazen on 2010-10-03
> **fabiocunha said:**
> II cannot install anything. Always giving me some sort of error. Not even the update manager works. Please help

Can you run apt-get update from a terminal and post the error message ?

---

### Post by fabiocunha on 2010-10-04
fabio@aglinux:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory
fabio@aglinux:~$

---

### Post by oldos2er on 2010-10-04
Use sudo: ```
sudo apt-get update
```

---

### Post by fabiocunha on 2010-10-05
> **bodhi.zazen said:**
> Can you run apt-get update from a terminal and post the error message ?


this is the result

fabio@aglinux:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory
fabio@aglinux:~$

---

### Post by fabiocunha on 2010-10-05
> **oldos2er said:**
> Use sudo: ```
sudo apt-get update
```
I've tried that. it doesn't work.

---

### Post by tarps87 on 2010-10-05
> **fabiocunha said:**
> I've tried that. it doesn't work.

What is the error message when using sudo?

---

### Post by fabiocunha on 2010-10-05
> **tarps87 said:**
> What is the error message when using sudo?

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: NODATA 2

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release: The following signatures were invalid: NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed Release: The following signatures were invalid: NODATA 2
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
fabio@aglinux:~$

---

### Post by oldos2er on 2010-10-05
lucid-proposed key: [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/Release.gpg)

lucid-security key: [http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)

You might try running **sudo apt-key update**; if that doesn't work use the links above to add the keys manually.

---

### Post by fabiocunha on 2010-10-06
> **oldos2er said:**
> lucid-proposed key: [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/Release.gpg)

lucid-security key: [http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)

You might try running **sudo apt-key update**; if that doesn't work use the links above to add the keys manually.

Thanks. But how do I install manually if I have to do it that way?

---

### Post by bodhi.zazen on 2010-10-06
> **fabiocunha said:**
> Thanks. But how do I install manually if I have to do it that way?

See this section :

[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

---

### Post by fabiocunha on 2010-10-06
> **oldos2er said:**
> lucid-proposed key: [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/Release.gpg)

lucid-security key: [http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)

You might try running **sudo apt-key update**; if that doesn't work use the links above to add the keys manually.
I've done it all, and when I try to update to 10.10 the following appears:
fabio@aglinux:~$ update-manager -d
extracting 'maverick.tar.gz'
authenticate 'maverick.tar.gz' against 'maverick.tar.gz.gpg' 
tar: Removing leading `/' from member namesWARNING: Failed to read mirror file
fabio@aglinux:~$

---

### Post by bodhi.zazen on 2010-10-06
> **fabiocunha said:**
> I've done it all, and when I try to update to 10.10 the following appears:
fabio@aglinux:~$ update-manager -d
extracting 'maverick.tar.gz'
authenticate 'maverick.tar.gz' against 'maverick.tar.gz.gpg' 
tar: Removing leading `/' from member namesWARNING: Failed to read mirror file
fabio@aglinux:~$

That error message should be reported on Launchpad against update-manager, but is likely to be resolved by the developers (soon ... )

---

### Post by goustaroubunta on 2010-10-16
I have the same problem on Maverick. On my first update [libv4l thing].
Switched from the Greek to the main server and still the same error =/

when i activated updates from untrusted packages i had the error: 
> "W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: &#927;&#953; &#960;&#945;&#961;&#945;&#954;&#940;&#964;&#969; &#965;&#960;&#959;&#947;&#961;&#945;&#966;&#941;&#962; &#948;&#949;&#957; &#942;&#964;&#945;&#957; &#948;&#965;&#957;&#945;&#964;&#972;&#957; &#957;&#945; &#949;&#960;&#945;&#955;&#951;&#952;&#949;&#965;&#964;&#959;&#973;&#957; &#949;&#960;&#949;&#953;&#948;&#942; &#948;&#949;&#957; &#942;&#964;&#945;&#957; &#948;&#953;&#945;&#952;&#941;&#963;&#953;&#956;&#959; &#964;&#959; &#948;&#951;&#956;&#972;&#963;&#953;&#959; &#954;&#955;&#949;&#953;&#948;&#943;: NO_PUBKEY F86C6AC1C3FFB4AA"

---

### Post by fabiocunha on 2010-10-16
> **goustaroubunta said:**
> I have the same problem on Maverick. On my first update [libv4l thing].
Switched from the Greek to the main server and still the same error =/

when i activated updates from untrusted packages i had the error:

What I did (after several attempts in trying to fix it) was to do a clean install of it. Now it works fine.

---

### Post by goustaroubunta on 2010-10-16
> **fabiocunha said:**
> What I did (after several attempts in trying to fix it) was to do a clean install of it. Now it works fine.

hm thanx for the tip but i have done so many fixes for my webcam, my sound recording etc that i don't want to reinstall ubuntu. if i wanted reinstallations i'd get windows.

edit: the problem somehow vanished and the update installed =/

---

### Post by andresv on 2010-10-17
same problem here with 10.10 Maverick ubuntu --- anyone knows how to fix this (quite annoying) problem?

---

### Post by bodhi.zazen on 2010-10-17
> **andresv said:**
> same problem here with 10.10 Maverick ubuntu --- anyone knows how to fix this (quite annoying) problem?

See this sticky :

[http://ubuntuforums.org/showthread.php?t=1588889](http://ubuntuforums.org/showthread.php?t=1588889)

---

### Post by Linye on 2010-10-19
Had this problem trying to install something from the main repos and changing from the Puerto Rico servers to the Main server solved this. At least for now.

---

### Post by psychok7 on 2010-10-19
> **Linye said:**
> Had this problem trying to install something from the main repos and changing from the Puerto Rico servers to the Main server solved this. At least for now.

yup changing the server also worked for me

---

### Post by Jimbotronics on 2010-10-20
From reading through this thread, there seems to be several different issues going on.  When I got the "installation of untrusted packages" message, I was trying to update Google Chrome and Sun Java run-times via the update app.  For me, the solution was simple:

[COLOR="Blue"]Applications -> Ubuntu Software Center -> Edit -> Software Sources -> Updates tab -> and then check the box in front of "unsupported updates."[/COLOR]

Then everything went fine, although Sun's server speed may remind old-timers of the joys of 300 baud modems.

---

### Post by kezyka on 2010-11-03
> **Jimbotronics said:**
> From reading through this thread, there seems to be several different issues going on.  When I got the "installation of untrusted packages" message, I was trying to update Google Chrome and Sun Java run-times via the update app.  For me, the solution was simple:

[COLOR="Blue"]Applications -> Ubuntu Software Center -> Edit -> Software Sources -> Updates tab -> and then check the box in front of "unsupported updates."[/COLOR]

Then everything went fine, although Sun's server speed may remind old-timers of the joys of 300 baud modems.

<3 you!

---

### Post by bigmorron on 2010-11-15
Well I have this entire post and tried everything but I am at a loss. This is a new computer setup and I have not messed much with linux since redhat came out. Ubuntu seems to have everything i am looking for but I am stuck with the same error as the rest and I have no clue what to do next. Ubuntu software center will not install any aps at all and I thought they were on the disk. Same error in Synaptic Package Manager and update manager. Any help would be greatly appreciated thanks
 Should have mentioned I have a fresh install of Ubuntu 10.10

---

### Post by bigmorron on 2010-11-17
Guess I will try reinstall

---

### Post by sakusa on 2010-11-23
> **-=hazard=- said:**
> Ok, problem solved by changing the repository to the main one.

Sorry but that doesn't work for me. Have been reporting this problem to launchpad but got no response:(
As a result my two Ubuntu 10.10 computers haven't been updated for a couple of weeks now

---

### Post by tajiknomi on 2010-11-26
[SIZE=2]See my own Thread,which i had posted a month ago,and it is Solved :p


   [/SIZE][http://ubuntuforums.org/showthread.php?t=1610903](http://ubuntuforums.org/showthread.php?t=1610903)

---

### Post by sakusa on 2010-11-29
I'm on Ubuntu 10.10, and my Update Manager keeps prompting me to install updates, but the install fails due to "Requires installation of untrusted packages : The action would require the installation of packages from not authenticated sources."

Details: alsa-utils apparmor apparmor-utils apport-hooks-medibuntu aptdaemon compiz compiz-core compiz-gnome compiz-plugins cups cups-bsd cups-client cups-common cups-ppdc cupsddk empathy empathy-common evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins firefox firefox-branding firefox-gnome-support gcalctool gdb gimp gimp-data gnome-keyring gnome-settings-daemon gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber gwibber-service hal-cups-utils hpijs hplip hplip-cups hplip-data humanity-icon-theme icedtea-6-jre-cacao icedtea6-plugin indicator-sound initscripts libapparmor-perl libapparmor1 libasound2 libavcodec-extra-52 libavcodec-unstripped-52 libavutil-extra-50 libc-bin libc-dev-bin libc6 libc6-dev libcairo2 libcamel1.2-14 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdecoration0 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13 libedataserverui1.2-8 libegroupwise1.2-13 libevolution libfreetype6 libgcr0 libgdata-google1.2-1 libgdata1.2-1 libgimp2.0 libgp11-0 libgvfscommon0 libhpmud0 libldap-2.4-2 libnautilus-extension1 libpam-gnome-keyring libplymouth2 libpst4 libpurple-bin libpurple0 libsane-hpaio libssl0.9.8 libutouch-grail1 libvpx0 libxml2 libxml2-utils light-themes linux-generic linux-headers-2.6.35-23 linux-headers-2.6.35-23-generic linux-headers-generic linux-image-2.6.35-23-generic linux-image-generic linux-libc-dev mplayer nautilus nautilus-data nautilus-sendto-empathy nautilus-share openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openssl pidgin pidgin-data plymouth plymouth-label plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text plymouth-x11 python-aptdaemon python-aptdaemon-gtk python-cupshelpers python-libxml2 rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins simple-scan system-config-printer-common system-config-printer-gnome system-config-printer-udev sysv-rc sysvinit-utils thunderbird tzdata tzdata-java ubufox ubuntu-sso-client vino xserver-xorg-video-intel xul-ext-ubufox xulrunner-1.9.2

Here are the contents of /etc/apt/sources.list:
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/google-chrome.list.distUpgrade
/etc/apt/sources.list.d/google-chrome.list.save
/etc/apt/sources.list.d/jaunty-partner.list
/etc/apt/sources.list.d/jaunty-partner.list.distUpgrade
/etc/apt/sources.list.d/jaunty-partner.list.save
/etc/apt/sources.list.d/medibuntu.list
/etc/apt/sources.list.d/medibuntu.list.save

My Update Manager settings are:
Ubuntu software: 
Canonical-supported open source software (Main)
Community-maintained Open source software (universe)
Download from Main server
Other software:
Independent third party developers repository provided by third party software developers
Medibuntu -Ubuntu 10.10 Maverick Meerkat
[http://dl.google.com/linux/chrome/deb/stable](http://dl.google.com/linux/chrome/deb/stable) main
Canonical partners - software packaged by Canonical for their partners
Updates:
Important security updates (maverick-security)
Recommended updates (maverick-updates)
Automatic updates- check for updates daily
Install security updates without confirmation
Release upgrade: Normal releases

Trusted software providers: 
Ubuntu archive automatic signing key
Ubuntu CD image automatic signing key
Google Inc. Linux package signing key
Ubuntu Extras archive automatic signing key
Medibuntu packaging team

Statistics: Submit statistical information

My two Ubuntu systems are now several weeks out of date, more or less since I upgraded to Ubuntu 10.10
Could you please help?
Thanks

---

### Post by sakusa on 2010-11-29
(sorry I posted this reply to the wrong thread)

---

### Post by sakusa on 2010-11-29
> **bodhi.zazen said:**
> [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

Basically, packages are signed with a GPG key and most likely that message is because you need to import a key.

We need more information, including the exact error message and the contents of /etc/apt/sources.list
=====================================
    I'm on Ubuntu 10.10, and my Update Manager keeps prompting me to install updates, but the install fails due to "Requires installation of untrusted packages : The action would require the installation of packages from not authenticated sources."

Details: alsa-utils apparmor apparmor-utils apport-hooks-medibuntu aptdaemon compiz compiz-core compiz-gnome compiz-plugins cups cups-bsd cups-client cups-common cups-ppdc cupsddk empathy empathy-common evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins firefox firefox-branding firefox-gnome-support gcalctool gdb gimp gimp-data gnome-keyring gnome-settings-daemon gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber gwibber-service hal-cups-utils hpijs hplip hplip-cups hplip-data humanity-icon-theme icedtea-6-jre-cacao icedtea6-plugin indicator-sound initscripts libapparmor-perl libapparmor1 libasound2 libavcodec-extra-52 libavcodec-unstripped-52 libavutil-extra-50 libc-bin libc-dev-bin libc6 libc6-dev libcairo2 libcamel1.2-14 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdecoration0 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13 libedataserverui1.2-8 libegroupwise1.2-13 libevolution libfreetype6 libgcr0 libgdata-google1.2-1 libgdata1.2-1 libgimp2.0 libgp11-0 libgvfscommon0 libhpmud0 libldap-2.4-2 libnautilus-extension1 libpam-gnome-keyring libplymouth2 libpst4 libpurple-bin libpurple0 libsane-hpaio libssl0.9.8 libutouch-grail1 libvpx0 libxml2 libxml2-utils light-themes linux-generic linux-headers-2.6.35-23 linux-headers-2.6.35-23-generic linux-headers-generic linux-image-2.6.35-23-generic linux-image-generic linux-libc-dev mplayer nautilus nautilus-data nautilus-sendto-empathy nautilus-share openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openssl pidgin pidgin-data plymouth plymouth-label plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text plymouth-x11 python-aptdaemon python-aptdaemon-gtk python-cupshelpers python-libxml2 rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins simple-scan system-config-printer-common system-config-printer-gnome system-config-printer-udev sysv-rc sysvinit-utils thunderbird tzdata tzdata-java ubufox ubuntu-sso-client vino xserver-xorg-video-intel xul-ext-ubufox xulrunner-1.9.2

Here are the contents of /etc/apt/sources.list:
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/google-chrome.list.distUpgrade
/etc/apt/sources.list.d/google-chrome.list.save
/etc/apt/sources.list.d/jaunty-partner.list
/etc/apt/sources.list.d/jaunty-partner.list.distUpgrade
/etc/apt/sources.list.d/jaunty-partner.list.save
/etc/apt/sources.list.d/medibuntu.list
/etc/apt/sources.list.d/medibuntu.list.save

My Update Manager settings are:
Ubuntu software: 
Canonical-supported open source software (Main)
Community-maintained Open source software (universe)
Download from Main server
Other software:
Independent third party developers repository provided by third party software developers
Medibuntu -Ubuntu 10.10 Maverick Meerkat
[http://dl.google.com/linux/chrome/deb/stable](http://dl.google.com/linux/chrome/deb/stable) main
Canonical partners - software packaged by Canonical for their partners
Updates:
Important security updates (maverick-security)
Recommended updates (maverick-updates)
Automatic updates- check for updates daily
Install security updates without confirmation
Release upgrade: Normal releases

Trusted software providers: 
Ubuntu archive automatic signing key
Ubuntu CD image automatic signing key
Google Inc. Linux package signing key
Ubuntu Extras archive automatic signing key
Medibuntu packaging team

Statistics: Submit statistical information

My two Ubuntu systems are now several weeks out of date, more or less since I upgraded to Ubuntu 10.10
Could you please help?
Thanks

---

### Post by F.Soroush on 2010-11-29
hi everybody
I've a problem with my maveric on my laptop in updating:
"Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.
apport-hooks-medibuntu mplayer"


and do not understand how to solve it.
please help me!

---

### Post by PaulWhipp on 2010-12-15
I had exactly this problem on my netbook following upgrading from 10.04 to 10.10. I use the main repository.

I tried Synaptic (System | Administration | Synaptic Package Manager) for the upgrades rather than the Update Manager and it worked fine upgrading from both the main repository and from medibuntu.

Looks like a glitch in the 10.10 upgrade.

So if you get this problem - try synaptic and if it still fails try switching the source before messing around with the keys.

---

### Post by sakusa on 2010-12-23
> **PaulWhipp said:**
> I had exactly this problem on my netbook following upgrading from 10.04 to 10.10. I use the main repository.

I tried Synaptic (System | Administration | Synaptic Package Manager) for the upgrades rather than the Update Manager and it worked fine upgrading from both the main repository and from medibuntu.

Looks like a glitch in the 10.10 upgrade.

So if you get this problem - try synaptic and if it still fails try switching the source before messing around with the keys.
=============================
Thanks Paul. one of my many mistakes was to assume latest Ubuntu versions are sufficiently debugged to at least ensure auto updates would be reasonably trouble free.  I've just managed to download and install 10.04 LTS on one of my laptops. Shall try out your approach too - nothing else has worked so far.

---

### Post by PaulWhipp on 2010-12-23
The LTS versions have always proved sound for me. I recommend sticking with them unless you have a reason to want to use the six monthly updates.

I like to run the latest updates on my netbook so I can see what is coming up - Thanks to Ubuntu One and some basic scripting to add the few extra packages I need I can easily rebuild my netbook whenever I need to.

---

### Post by sxe4ever on 2011-01-08
> **F.Soroush said:**
> "Requires installation of untrusted packages. The action would require the installation of packages from not authenticated sources. 
apport-hooks-medibuntu mplayer"

and do not understand how to solve it.
please help me!

I was having this same issue on my desktop using version 11.04 with my regular software updates through software manager. I ended up using Synaptic as listed below and it worked fine for me. All you have to do is click on "Mark All Upgrades" and then "Apply" once you launch it. After running Synaptic and checking the Update Manager again, it had installed all of the updates.

> **PaulWhipp said:**
> I had exactly this problem on my netbook following upgrading from 10.04 to 10.10. I use the main repository.

I tried Synaptic (System | Administration | Synaptic Package Manager) for the upgrades rather than the Update Manager and it worked fine upgrading from both the main repository and from medibuntu.

Looks like a glitch in the 10.10 upgrade.

So if you get this problem - try synaptic and if it still fails try switching the source before messing around with the keys.

---

### Post by anur.bhargav on 2011-02-02
> **-=hazard=- said:**
> Ok, problem solved by changing the repository to the main one.

Thank You !! I had the same problem...:popcorn:

---

### Post by dalekirkwood on 2011-02-06
Just to let you all know, I had the same problem when installing GIMP image editor. selecting main server worked a treat .

---

### Post by sakusa on 2011-02-09
> **dalekirkwood said:**
> Just to let you all know, I had the same problem when installing GIMP image editor. selecting main server worked a treat .

Sorry, but that hasn't worked for me. Have tried three different repository sources, including the main server :(

---

### Post by ktat on 2011-03-15
> **RoRoRed said:**
> Now it works,

well  I checked the box for source code (in the ubuntu register)

thanks for your help & sorry to have wasted your time ^_^

Funny - I had the same problem, although my "source" box had a line through it so I unchecked it and viola, problem fixed!!

---

### Post by BoogeyOfTheMan on 2011-06-29
I have been having this problem about once a month or so, mainly from the Opera repo. It seems that the only fix I have found is to re-add the key. I also just got that error for Getdeb repo, but havent messed with that one yet.

---

### Post by miz0ooo0 on 2011-07-10
i found the simplest solution ,i tried it and worked smoothly 
by typing (sudo apt-get update) in terminal then try to install any software ,it will work

---

### Post by brucewagner on 2011-07-14
This solved this problem for me:

I just clicked Update Manager --> Settings...

Then on "Other Software" tab, I also checkmarked "Source Code" one that had not been on...

I then clicked Close...   And did an Update again.

It worked.

Apparently, something was expecting/requiring some source code to be updated... and since Source Code was defaulted to "off".... It wasn't finding it.

Or, at least, that's my guess.

Anyway, it apparently fixed the problem.

---

### Post by theodorekon on 2011-11-27
I had the same problem with some updates from the medibuntu repository. None of the solutions mentioned involving the settings of the update manager worked for me. I found this command in order to add the medibuntu repositories:

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && 
sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

After doing that the problem was solved for me. I noticed that a new key has been added to the trusted software providers so I guess that's what was causing the problem.

---

### Post by yoosofan on 2012-04-08
I had this problem too. This problem was easily solved by running the following command in terminal.
sudo apt-get upgrade
Confirmation is needed to install unauthenticated updates( simply enter y whenever it asks you any y/n question.).
I hope that this method does not cause any unwanted side effects.

---

### Post by oldos2er on 2012-04-08
Let's let sleeping dogs lie. Closed.

---

