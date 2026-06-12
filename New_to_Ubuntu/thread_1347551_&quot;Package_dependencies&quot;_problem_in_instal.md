---
title: "&quot;Package dependencies&quot; problem in installing borh DeVeDe and mandvd ,"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by medya on 2009-12-06
I am trying to install a software to convert my AVI movies to DVD movie ,
and when I try to install borh DeVeDe and mandvd
i get the same error from synaptic :
Package dependencies cannot be resolved

then I try to install the packages which synaptic cant install then I get more problems.... 
like synaptic says "mandvd:  Depends: dvd-slideshow but it is not going to be installed"

why is that and what to do ?

---

### Post by oldos2er on 2009-12-06
Check System, Administration, Software Sources; make sure you have all repositories enabled.

---

### Post by medya on 2009-12-06
I have enabaled all of them.

---

### Post by medya on 2009-12-06
no idea? are u ppl albe to install mandvd ? or it just me

---

### Post by oldos2er on 2009-12-06
Try ```
sudo apt-get update && sudo apt-get install devede mandvd
```

If it fails, please post the terminal output here.

---

### Post by medya on 2009-12-06
here is the terminal output  :
> 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  devede: Depends: libavcodec-extra-52 but it is not going to be installed
          Depends: libavformat-extra-52 but it is not going to be installed
          Depends: libpostproc-extra-51 but it is not going to be installed
          Depends: libswscale-extra-0 but it is not going to be installed
  mandvd: Depends: dvd-slideshow but it is not going to be installed
E: Broken packages


---

### Post by medya on 2009-12-06
oldos2er , are you able to intall mandvd yourself ? maybe it is a ubuntu 9.10 problem .

---

### Post by oldos2er on 2009-12-06
Double-check that you have the multiverse repository enabled, that's where libavcodec and libavformat (and probably the other libs as well) are. You may want to try a different server also.

---

### Post by medya on 2009-12-06
I dobuled checked  I have mulitiunvierse, 
I even changed the server of synaptic from Iran to Mainsever , did it again and still I get error see :
> 
sudo apt-get update && sudo apt-get install  mandvd
[sudo] password for karmakurdan: 
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US                    
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release.gpg                              
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Translation-en_US                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US                
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) karmic Release.gpg                             
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) karmic/main Translation-en_US                  
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US              
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg [189B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_US      
Get:2 [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release [1,723B]                       
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                               
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) karmic Release                                 
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg [189B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) karmic/main Packages                           
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release [44.1kB]                
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages                            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources                      
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) karmic/main Sources                            
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages                         
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release [44.1kB]
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) karmic/main Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages [1,353kB]
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) karmic/main Sources  
Hit [http://linux.getdropbox.com](http://linux.getdropbox.com) karmic/main Packages                           
Hit [http://linux.getdropbox.com](http://linux.getdropbox.com) karmic/main Sources                            
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages [7,971B]            
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources [116kB]              
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources [2,795kB]              
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages [5,133kB]            
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages [190kB]                       
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages [104kB]                     
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages [14B]                 
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources [14B]                  
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources [30.8kB]                     
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources [1,223B]               
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources [13.8kB]                 
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages [61.3kB]                
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages [1,616B]              
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages [28.5kB]                   
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages [14B]                
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources [14B]                 
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources [7,625B]                    
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources [14B]                 
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources [793B]                  
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages [8,762B]               
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages [14B]                
Fetched 9,942kB in 3min 51s (43.0kB/s)                                                    
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mandvd: Depends: dvd-slideshow but it is not going to be installed
E: Broken packages


---

### Post by medya on 2009-12-06
u didnt answer my question, are you yourself able to install mandvd ?

---

### Post by oldos2er on 2009-12-06
Yes, I've had it installed for awhile. You've got an awful lot of "Ign"ores in there, which could possibly be part of the problem.

 You can run **sudo apt-get install -f** to fix your broken packages.

---

### Post by medya on 2009-12-06
I did that too see :
> **karmakurdan@KarmaKurdan:~$ sudo apt-get install -f**
[sudo] password for karmakurdan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavutil-unstripped-49 libsvga1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
**karmakurdan@KarmaKurdan:~$ sudo apt-get autoremove**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libavutil-unstripped-49 libsvga1
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 758kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 228358 files and directories currently installed.)
Removing libavutil-unstripped-49 ...
Removing libsvga1 ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
**karmakurdan@KarmaKurdan:~$ sudo apt-get install  mandvd**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mandvd: Depends: mencoder but it is not going to be installed
          Depends: mplayer but it is not going to be installed or
                   mplayer-nogui but it is not going to be installed
E: Broken packages

---

### Post by mc4man on 2009-12-06
Why don't you try using synaptic to see what's up.

First go into System -> Admin -> Software Sources -> Third Party and for the moment disable any ppa's. Then click close and reload ( you can leave medibuntu if shown, disable any others

Then open synaptic, if it shows any broken packages then click on the 'custom filters', then 'broken' and see what they are (if any)

If there are any broken either remove or go edit -> fix broken..'

To install devede and mandvd you need mplayer-nogui, mencoder, and libavcodec-extra-52

So search out ffmpeg and 2 ways to  approach

Either try to mark for install the ffmpeg libs to the extra versions, starting by scrolling to bottom (libswscale-extra-0) and working your way up to libavcodec-extra-52
Then click apply and after they're installed try devede

Or 
search ffmpeg and mark all the ffmpeg libs for removal and apply (you'll lose some players and plugins, no matter, just re-install after

After removing all ffmpeg libs then again install devede, mandvd and whatever else was removed.

This will take care of the gstreamer plugins that may have been removed and or never installed

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse


```

---

### Post by medya on 2009-12-07
> Or
search ffmpeg and mark all the ffmpeg libs for removal and apply (you'll lose some players and plugins, no matter, just re-install after


thank you so much that worked ! how did u guess that it would solve the problem .thanks again.

---

### Post by oldos2er on 2009-12-07
> **mc4man said:**
> To install devede and mandvd you need mplayer-nogui, mencoder, and libavcodec-extra-52

 mc4man, I don't understand why apt wouldn't grab these dependencies when first given the command 'sudo apt-get install devede'? Can you explain? Thanks.

---

### Post by mc4man on 2009-12-07
> why apt wouldn't grab these dependencies when first given the command..

It normally should, the only thing that was happening for some was it was removing a ppa mplayer to install devede and then removing devede when mplayer was re-installed ( since fixed in regards to that ppa

While unrelated here does point out that some ppa's can interfere with installing devede or libavcodec and the Op has some enabled that aren't clear as to what they're providing.

The other thing that seems to happen is in some upgrades from jaunty to karmic, libavcodec-extra-52 won't install, maybe from still having the unstripped version installed, or again from upgrading with a ppa or ppa packages installed.

Seems very inconsistent and somewhat nonsense

That's why I think if one gets jammed up this way and can't find what's blocking,  that removing all and then installing devede, ect. should resolve because then mplayer-nogui, mencoder and libavcode-extra-52 should install, being deps of devede

edit:
just as an example of the mplayer/devede deal and how one can go around in circles till it's finally resolved is here 
[http://ubuntuforums.org/showthread.php?t=1290522](http://ubuntuforums.org/showthread.php?t=1290522)

---

### Post by oldos2er on 2009-12-08
Thank you.

---

