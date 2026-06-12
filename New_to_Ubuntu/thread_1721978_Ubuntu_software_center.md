---
title: "Ubuntu software center"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by hemoali on 2011-04-05
Why when I click on Ubuntu software center no thing appears  no any window opens anyone know the cause 
second videos I watching on youtube doesn't appear in the tmp folder why??

---

### Post by Dutch70 on 2011-04-05
> **hemoali said:**
> Why when I click on Ubuntu software center no thing appears  no any window opens anyone know the cause 
second videos I watching on youtube doesn't appear in the tmp folder why??

1. No idea, can you give any more info on the situation?

2. I believe they've changed that around, they don't show up in the tmp folder anymore, and I'm not sure where they're at. Maybe Mozilla or Firefox Cache.

---

### Post by oldos2er on 2011-04-05
> **hemoali said:**
> Why when I click on Ubuntu software center no thing appears  no any window opens anyone know the cause

Can you open a terminal (Applications, Accessories, Terminal), run the following command and post the output here? ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by hemoali on 2011-04-06
Still Not Working

---

### Post by donkyhotay on 2011-04-06
> **hemoali said:**
> Still Not Working

As requested by oldos2er open up terminal and copy/paste
```

sudo apt-get update && sudo apt-get upgrade

```
there, press enter, then post the results here. This will give us more information for us to try and identify why the software center is not working.

---

### Post by oldos2er on 2011-04-06
> **hemoali said:**
> Still Not Working

We have no idea what's not working. [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by hemoali on 2011-04-07
Ok Look I find a solution 
sudo software-center
when i wrote it in terminal the ubuntu software center opened nut when i click on its button in the applications menu no thing appears 
So I think the problem in menu not in the center

---

### Post by Paddy Landau on 2011-04-07
@hemoali, the problem is *not* in the menu, because Ubuntu Software Centre does not require sudo or gksu.

You have twice been asked what to do ([post #3]("http://ubuntuforums.org/showthread.php?p=10641020#post10641020") and [post #5]("http://ubuntuforums.org/showthread.php?p=10645133#post10645133")). Do as they ask, and then we can help you further.

Otherwise, you are wasting our time.

---

### Post by hemoali on 2011-04-07
this what I have After I did what you said

> Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Get:1 [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release.gpg [197B]                 
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick Release                              
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) karmic/non-free Translation-en
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) karmic/non-free Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates Release                      
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/main Sources                         
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/restricted Sources                   
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/universe Sources           
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/multiverse Sources         
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/main i386 Packages                   
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/restricted i386 Packages             
Get:2 [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release [5,436B]                   
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release                              
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/universe i386 Packages               
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/multiverse i386 Packages   
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/main Sources       
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/restricted Sources 
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/universe Sources   
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/multiverse Sources 
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/main i386 Packages 
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free i386 Packages/DiffIndex     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/s-lagui/ppa/ubuntu/](http://ppa.launchpad.net/s-lagui/ppa/ubuntu/) maverick/main Translation-en  
Ign [http://ppa.launchpad.net/s-lagui/ppa/ubuntu/](http://ppa.launchpad.net/s-lagui/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/shutter/ppa/ubuntu/](http://ppa.launchpad.net/shutter/ppa/ubuntu/) maverick/main Translation-en  
Ign [http://ppa.launchpad.net/shutter/ppa/ubuntu/](http://ppa.launchpad.net/shutter/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Fetched 198B in 9s (22B/s)                                                     
Reading package lists... Done
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  cups evolution-plugins linux-generic linux-headers-generic
  linux-image-generic
The following packages will be upgraded:
  x11-xserver-utils
1 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 170kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/main x11-xserver-utils i386 7.5+2ubuntu1.1 [170kB]
Fetched 170kB in 1s (115kB/s)             
(Reading database ... 160489 files and directories currently installed.)
Preparing to replace x11-xserver-utils 7.5+2ubuntu1 (using .../x11-xserver-utils_7.5+2ubuntu1.1_i386.deb) ...
Unpacking replacement x11-xserver-utils ...
Processing triggers for man-db ...
Setting up x11-xserver-utils (7.5+2ubuntu1.1) ...
hemo@Ibrahim:~$ 


---

### Post by oldos2er on 2011-04-07
"W: GPG error: [http://download.virtualbox.org]("http://download.virtualbox.org/") karmic"

You need to remove that repository from your sources.list.

---

### Post by hemoali on 2011-04-07
Ho please I'm just began use ubuntu for 3 months only

---

### Post by oldos2er on 2011-04-07
Run ```
gksu gedit /etc/apt/sources.list
``` in a terminal. When you are done, run ```
sudo apt-get update
``` [COLOR=Red]If there are still errors, please copy and paste them in full here[/COLOR].

---

### Post by hemoali on 2011-04-07
Ok it opened sourcelist  file what i should remove

---

### Post by oldos2er on 2011-04-07
[http://download.virtualbox.org]("http://download.virtualbox.org/") karmic

---

### Post by hemoali on 2011-04-07
you mean that
> deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free
yes???

---

### Post by hemoali on 2011-04-07
no thing happened such as before

---

### Post by oldos2er on 2011-04-07
You removed the line "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free", and ran **sudo apt-get update** ?

---

### Post by hemoali on 2011-04-07
I did but no results
and this is the output
> Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                   
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en   
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                    
Ign [http://ppa.launchpad.net/s-lagui/ppa/ubuntu/](http://ppa.launchpad.net/s-lagui/ppa/ubuntu/) maverick/main Translation-en  
Ign [http://ppa.launchpad.net/s-lagui/ppa/ubuntu/](http://ppa.launchpad.net/s-lagui/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
Ign [http://ppa.launchpad.net/shutter/ppa/ubuntu/](http://ppa.launchpad.net/shutter/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/shutter/ppa/ubuntu/](http://ppa.launchpad.net/shutter/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick Release                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates Release                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/main Sources               
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/restricted Sources
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/universe Sources
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Reading package lists... Done
hemo@Ibrahim:~$ 


---

### Post by hemoali on 2011-04-07
see this video
[http://www.youtube.com/watch?v=tReYzvype-4](http://www.youtube.com/watch?v=tReYzvype-4)

---

### Post by linux.alucard on 2011-05-05
isn't working at login :(

---

### Post by Paddy Landau on 2011-05-05
@hemoali:

Did you get it working yet?

If not, please run the following in a terminal:
```
sudo apt-get update && sudo apt-get upgrade
```Post the results here please.

---

