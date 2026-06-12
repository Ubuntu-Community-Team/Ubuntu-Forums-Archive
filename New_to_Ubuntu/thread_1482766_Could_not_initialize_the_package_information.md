---
title: "Could not initialize the package information"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by grey1 on 2010-05-13
ubuntu 10.04
I have a problem in terminal, when trying to fix a problem here I get this line 

E: Type 'echo' is not known on line 1 in source list /etc/apt/sources.list.d/ddebs.list


Also get this message in update manager:

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'echo' is not known on line 1 in source list /etc/apt/sources.list.d/ddebs.list, E:The list of sources could not be read.'

Is there anything I can do to fix the problem ?

---

### Post by Sealbhach on 2010-05-13
Looks like you added a PPA from the command line. Open up that file with this command:

```
gksu gedit /etc/apt/sources.list.d/ddebs.list
```

and remove the word "echo" which is probably at the beginning of the line.

.

---

### Post by grey1 on 2010-05-13
ok "echo" was there and have removed it.

---

### Post by Sealbhach on 2010-05-13
Right, so you need to save and close the file and then run 

```
sudo apt-get update

```
to make sure the change takes effect.

.

---

### Post by grey1 on 2010-05-14
I get:

E: Type 'sudo' is not known on line 5 in source list /etc/apt/sources.list.d/ddebs.list

---

### Post by Sealbhach on 2010-05-14
> **grey1 said:**
> I get:

E: Type 'sudo' is not known on line 5 in source list /etc/apt/sources.list.d/ddebs.list

Ok, can you open up that file again, and copy and paste everything that's in it to here?

Thanks.

.

---

### Post by grey1 on 2010-05-14
> **Sealbhach said:**
> Ok, can you open up that file again, and copy and paste everything that's in it to here?

Thanks.

.

deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release -cs)-updates main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release -cs)-security main restricted universe multiverse

deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release -cs)-proposed main restricted universe multiverse"
sudo tee -a /etc/apt/sources.list.d/ddebs.list

---

### Post by Sealbhach on 2010-05-14
> **grey1 said:**
> deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release -cs)-updates main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release -cs)-security main restricted universe multiverse

deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release -cs)-proposed main restricted universe multiverse"
[COLOR=Red]sudo tee -a /etc/apt/sources.list.d/ddebs.list[/COLOR]

See the part in Red? Delete that, then save and close, then run 

```
sudo apt-get update
```

.

---

### Post by grey1 on 2010-05-14
> **Sealbhach said:**
> See the part in Red? Delete that, then save and close, then run 

```
sudo apt-get update
```

.



Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release Release.gpg                          
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]          
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [189B]       
Ign [http://ddebs.ubuntu.com/](http://ddebs.ubuntu.com/) $(lsb_release/-cs)-updates Translation-en_US 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://ddebs.ubuntu.com/](http://ddebs.ubuntu.com/) $(lsb_release/main Translation-en_US
Ign [http://ddebs.ubuntu.com/](http://ddebs.ubuntu.com/) $(lsb_release/restricted Translation-en_US        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://ddebs.ubuntu.com/](http://ddebs.ubuntu.com/) $(lsb_release/universe Translation-en_US          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://ddebs.ubuntu.com/](http://ddebs.ubuntu.com/) $(lsb_release/multiverse Translation-en_US        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [189B]            
Ign [http://ddebs.ubuntu.com/](http://ddebs.ubuntu.com/) $(lsb_release/-cs)-security Translation-en_US     
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [32.5kB]               
Ign [http://ddebs.ubuntu.com/](http://ddebs.ubuntu.com/) $(lsb_release/-cs)-proposed Translation-en_US     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release Release                              
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [5,309B]         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/-cs)-updates Packages                
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]      
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/main Packages                        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [2,164B]          
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/restricted Packages                  
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]                      
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]       
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/universe Packages                    
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [1,216B]    
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [38.5kB]             
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/multiverse Packages            
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [780B]       
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/-cs)-security Packages               
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [14B]     
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/-cs)-proposed Packages               
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [14B]      
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/-cs)-updates Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/main Packages                        
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/restricted Packages                  
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages [6,208B]         
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/universe Packages                    
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/multiverse Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/-cs)-security Packages               
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources [3,775B]          
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/-cs)-proposed Packages               
Err [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/-cs)-updates Packages                
  404  Not Found
Err [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/main Packages                        
  404  Not Found
Err [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/restricted Packages                  
  404  Not Found
Err [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/universe Packages                    
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Err [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/multiverse Packages                  
  404  Not Found
Err [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/-cs)-security Packages               
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Err [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release/-cs)-proposed Packages              
  404  Not Found
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages [180kB]         
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources [119kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [150kB]        
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [2,102B] 
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [59.5kB]        
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [737B]    
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [21.2kB]   
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [4,868B]    
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [632B]   
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [14B]     
Fetched 685kB in 57s (12.0kB/s)                                                
W: Failed to fetch http://ddebs.ubuntu.com/dists/$(lsb_release/-cs)-updates/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ddebs.ubuntu.com/dists/$(lsb_release/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ddebs.ubuntu.com/dists/$(lsb_release/restricted/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ddebs.ubuntu.com/dists/$(lsb_release/universe/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ddebs.ubuntu.com/dists/$(lsb_release/multiverse/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ddebs.ubuntu.com/dists/$(lsb_release/-cs)-security/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ddebs.ubuntu.com/dists/$(lsb_release/-cs)-proposed/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by grey1 on 2010-05-14
I think it is fixed (I hope).
Thank you Sealbhach

---

### Post by Sealbhach on 2010-05-14
> **grey1 said:**
> deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release -cs)-updates main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release -cs)-security main restricted universe multiverse

deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release -cs)-proposed main restricted universe multiverse"


Ok, the part "$(lsb_release -cs)" is supposed to be replaced with the name lucid, or intrepid or hardy or karmic or whichever release you are using.

So I would suggest changing "$(lsb_release -cs)" to "lucid" if you're using Lucid. Did you use a how-to to add this file to your sources? If so, could you provide a link to it?

.

---

### Post by grey1 on 2010-05-14
> 
Did you use a how-to to add this file to your sources? If so, could you provide a link to it?

.

Using ubuntu 10.04 lts that down loaded as upgrade in update manager. Been having a problem with lock-up all the time after an update a week later from update manager. Was told it was FireFox, so tryed three other browsers, had same problem. then told it was java. I don't remember where or what for a link. all I can remember is rebooting the computer every 10 to 15 minutes and trying to fix it to get rid of the lockup. I am wearing out my on-off button to reboot.

---

### Post by Sealbhach on 2010-05-14
Right, still a problem. Please could you do:

```
cat /etc/apt/sources.list
```

and copy and paste the result here.

.

---

### Post by grey1 on 2010-05-14
> **Sealbhach said:**
> Right, still a problem. Please could you do:

```
cat /etc/apt/sources.list
```

and copy and paste the result here.

.



# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

---

### Post by Sealbhach on 2010-05-14
That all appears fine, I don't see anything obviously wrong with it, maybe someone can spot something.

What is the error message you get now?

.

---

### Post by grey1 on 2010-05-14
> **Sealbhach said:**
> That all appears fine, I don't see anything obviously wrong with it, maybe someone can spot something.

What is the error message you get now?

.

Don't get any error messages now, but still locks up a lot "freeze-up". Any way, I have to shut down with off on switch to get out of a lock-up situation. Happened twice today on this site as well as many others. Funny, when it locks up, some times the screen has vertical lines with what look like dominos on the left side.

Guess problem still is lock-up, now that the problem of "*Could not initialize the package information*" seems solved ?

---

### Post by Sealbhach on 2010-05-14
Right, well there's a bunch of other people experiencing random freezeups, it would be a good idea to follow that thread: [http://ubuntuforums.org/showthread.php?p=9299944](http://ubuntuforums.org/showthread.php?p=9299944)

Now, rather than mash the power button, please try to shut down using this method, which is kinder to your computer:

**Holding down Alt and SysRq (which is the Print Screen key) while slowly  typing REISUB**

From here:  [http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

There could be any number of reasons why you're experiencing lockups, I think if you follow that other thread there, you might get some better ideas of what to try and what to do.

.

---

### Post by grey1 on 2010-05-14
[B]A big thanks for helping me solve the "*Could not initialize the package information*" problem, that had me worried. 
Will follow:  [http://ubuntuforums.org/showthread.php?p=9299944](http://ubuntuforums.org/showthread.php?p=9299944)  
to see if anything there helps.

Thanks again Sealbhach[/B]

---

### Post by grey1 on 2010-05-15
Have had two lockups since last, and find that

**Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB**

does not work.

---

### Post by Sealbhach on 2010-05-15
OK, then maybe this method will do it

press Ctrl+Alt+F1, login and run the command

```
sudo shutdown -r now
```

or if that doesn't work

```
sudo halt
```

.

---

### Post by grey1 on 2010-05-15
> **Sealbhach said:**
> OK, then maybe this method will do it

press Ctrl+Alt+F1, login and run the command

```
sudo shutdown -r now
```

or if that doesn't work

```
sudo halt
```

.

Wish it would work, no luck :confused:
Only seems to work before a lockup happens
but not after a lockup.

---

### Post by philinux on 2010-05-15
How about Alt+SysRq+k

Have a look in /var/log/messages see if any errors are being reported. What app are you using when it freezes.

Open a terminal and keep **top** running see if anything is maxing out the cpu.

---

### Post by grey1 on 2010-05-15
"Alt+SysRq+k"  
Does not work

"Have a look in /var/log/messages see if any errors are being reported"  
Can't get into this, shows error 

"see if anything is maxing out the cpu"
cpu is not maxing out, spikes, but no steady max use. 
Locked up at 30%, 25%, and 10%. No pattern there.

---

### Post by grey1 on 2010-05-28
Looks as if it mite be the wireless 
in the laptop that causes the lockup.
For now guess the other problem is 
repaired

---

