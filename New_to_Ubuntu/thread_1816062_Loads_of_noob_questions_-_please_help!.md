---
title: "Loads of noob questions - please help!"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by adamhum3 on 2011-08-01
So, I've not long had Ubuntu 11.04 installed, but it's frustrating the hell out of me.

The main problems I've been getting seem to be with broken packages. Whenever I try installing a program like VLC, or Deluge it errors me saying > This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.Or if I do it in the terminal, it gives me other errors saying certain packages have unmet dependencies.

So the majority of programs I'd like to install, won't install, and I've tried updating, upgrading, autocleaning, etc. etc. and none of it seems to be working, I would like to just get rid of all of these problems and maybe just start fresh - unless there's another, better option available?


Also I'm experiencing a jumping cursor a lot in Ubuntu, bare in mind I am using a trackpad, any ideas what is causing it?



Thanks in advance,

Adam.

---

### Post by goldshirt9 on 2011-08-01
you need to post your machines spec's ,that will help a lot.:)
was it  a fresh install or upgrade.???

---

### Post by IWantFroyo on 2011-08-01
Does this help? ```
sudo apt-get update
```

---

### Post by snowpine on 2011-08-01
If your system is fully updated and you are installing apps from the official repositories using the Ubuntu Software Center (or the appropriate terminal commands) then you should **never** have a dependency issue.

If you have modified your software sources then yes, it is possible to experience dependency problems. Posting the exact error messages is a good first step to getting help on these forums. :)

---

### Post by Rex Bouwense on 2011-08-01
Welcome to the forums.  Sorry about your problems but let me ask if everything works on your computer using 11.04.  Several people have had some problems (other than downloading and installing programs).  How did you try to install these programs?  Did you use the Ubuntu Software Center or Synaptic Package Manager?  It helps us if tell us exactly what you did and the exact results.  Then we don't have to guess.  Have you sought a response by searching the forums.
Sit back and have some :popcorn:.

---

### Post by adamhum3 on 2011-08-01
> **goldshirt9 said:**
> you need to post your machines spec's ,that will help a lot.:)
was it  a fresh install or upgrade.???

Oops.

Acer Aspire 7730
4GB RAM
148GB HDD
Intel Core 2 Duo

Fresh install :)

> **IWantFroyo said:**
> Does this help? ```
sudo apt-get update
```

Tried it :\

---

### Post by sanderd17 on 2011-08-01
> **adamhum3 said:**
> 



Tried it :\

Can you post the output? reading the output can be very helpful.

---

### Post by adamhum3 on 2011-08-01
This is what I get when trying to install VLC through the terminal:
> adam@ubuntu:~$ sudo apt-get install vlc
[sudo] password for adam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 vlc : Depends: vlc-nox (= 1.1.9-1ubuntu1) but it is not going to be installed
       Depends: libavcodec52 (>= 4:0.6-1~) but it is not installable or
                libavcodec-extra-52 (>= 4:0.6-1~) but it is not going to be installed
       Depends: libqtcore4 (>= 4:4.7.0~beta1) but it is not installable
       Depends: libqtgui4 (>= 4:4.5.3) but it is not installable
       Depends: libva-x11-1 but it is not installable
       Depends: libva1 but it is not installable
       Depends: libxcb-keysyms1 (>= 0.3.6) but it is not installable
       Depends: libxcb-xv0 (>= 1.2) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 1.1.9-1ubuntu1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1.1.9-1ubuntu1) but it is not going to be installed
E: Broken packages

This is what I get installing if the software centre:
> The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 1.1.9-1ubuntu1) but 1.1.9-1ubuntu1 is to be installed
     Depends: libaa1 (>= 1.4p5) but 1.4p5-38build1 is to be installed
     Depends: libavcodec-extra-52 (>= 4:0.6-1~) but 4:0.6.2-1ubuntu2+medibuntu1 is to be installed
     Depends: libavutil-extra-50 (>= 4:0.6-1~) but 4:0.6.2-1ubuntu2+medibuntu1 is to be installed
     Depends: libc6 (>= 2.8) but 2.13-0ubuntu13 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.4-1ubuntu2.1 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed
     Depends: libqtcore4 (>= 4:4.7.0~beta1) but it is not going to be installed
     Depends: libqtgui4 (>= 4:4.5.3) but it is not going to be installed
     Depends: libsdl-image1.2 (>= 1.2.10) but 1.2.10-2ubuntu1 is to be installed
     Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.14-6.1ubuntu3 is to be installed
     Depends: libstdc++6 (>= 4.5) but 4.5.2-8ubuntu4 is to be installed
     Depends: libva-x11-1 but it is not going to be installed
     Depends: libva1 but it is not going to be installed
     Depends: libxcb-keysyms1 (>= 0.3.6) but it is not going to be installed
     Depends: libxcb-xv0 (>= 1.2) but 1.1-1ubuntu1 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed

This is what I get after running apt-get update:
> adam@ubuntu:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy InRelease                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy InRelease                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe amd64 Packages          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free amd64 Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe TranslationIndex        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main amd64 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe amd64 Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse amd64 Packages                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main TranslationIndex                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe TranslationIndex                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main amd64 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted amd64 Packages          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free TranslationIndex                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main TranslationIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted TranslationIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe amd64 Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe TranslationIndex                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_GB                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_GB               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_GB               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_GB                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en_GB                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free amd64 Packages          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free amd64 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_GB            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_GB                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free TranslationIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en
Reading package lists... Done


---

### Post by 3rdalbum on 2011-08-01
Oh my.

You're running Ubuntu 11.04 ("Natty") and you have software sources listed there for Ubuntu 8.04 ("Hardy") in addition to what should be there.

Go into Software Center and then Edit > Software Sources... Under the Other Software tab, remove anything that has a reference to "hardy". When you close the window, it will ask you if you want to reload the package list - do this. Then your software should install properly.

In future, make sure you only add repositories that are for your version of Ubuntu. Using repositories for older or newer versions is a recipe for trouble.

---

### Post by sanderd17 on 2011-08-01
How did you get those hardy release repositories in it?

You should remove those repositories as a start and do the update again.

You can remove them via the software center and go to software sources.

EDIT: I was to slow :D

---

### Post by snowpine on 2011-08-01
Ubuntu 8.04 "Hardy Heron" has reached its "end of life" and is no longer supported.

Your system is a mix of Hardy and Natty 11.04 packages. I'm not surprised it is broken and I don't know how to fix it. 

I recommend a fresh reinstall of 11.04. Good luck! :)

---

### Post by adamhum3 on 2011-08-01
Hahaha, I did mention I'm new to this! I'll give it a try and let you know, thanks a lot for the quick responses really appreciate that. Anyone know what i can do about this jumping cursor?

---

### Post by sanderd17 on 2011-08-01
> **adamhum3 said:**
> Anyone know what i can do about this jumping cursor?

First begin with having the right packages. So we know with what we are dealing. There are serveral apps that let you configure the sensitivity of the mouse, but you won't be able to install them now.

---

### Post by 3rdalbum on 2011-08-01
It hasn't bothered me enough to mention it before, but I get a jumping cursor as well. It only jumps when I move over a certain spot on the trackpad; it might be something to do with the scrolling function of the trackpad. Turning off the scroll area function in the Mouse/Trackpad panel might help (or turning it to "two finger scroll" instead). I can't give precise instructions for this because my netbook is running the development version of Ubuntu, not 11.04.

---

### Post by adamhum3 on 2011-08-01
> **3rdalbum said:**
> Oh my.

You're running Ubuntu 11.04 ("Natty") and you have software sources listed there for Ubuntu 8.04 ("Hardy") in addition to what should be there.

Go into Software Center and then Edit > Software Sources... Under the Other Software tab, remove anything that has a reference to "hardy". When you close the window, it will ask you if you want to reload the package list - do this. Then your software should install properly.

In future, make sure you only add repositories that are for your version of Ubuntu. Using repositories for older or newer versions is a recipe for trouble.

I tried this, however it didn't ask me to reload the package list. I'm still getting the error, which is:

> adam@ubuntu:~$ sudo apt-get autoclean
[sudo] password for adam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
adam@ubuntu:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 vlc : Depends: vlc-nox (= 1.1.9-1ubuntu1) but it is not going to be installed
       Depends: libavcodec52 (>= 4:0.6-1~) but it is not installable or
                libavcodec-extra-52 (>= 4:0.6-1~) but it is not going to be installed
       Depends: libqtcore4 (>= 4:4.7.0~beta1) but it is not installable
       Depends: libqtgui4 (>= 4:4.5.3) but it is not installable
       Depends: libva-x11-1 but it is not installable
       Depends: libva1 but it is not installable
       Depends: libxcb-keysyms1 (>= 0.3.6) but it is not installable
       Depends: libxcb-xv0 (>= 1.2) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 1.1.9-1ubuntu1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1.1.9-1ubuntu1) but it is not going to be installed
E: Broken packages


---

### Post by OldBoy44 on 2011-08-01
> **snowpine said:**
> Ubuntu 8.04 "Hardy Heron" has reached its "end of life" and is no longer supported.

Your system is a mix of Hardy and Natty 11.04 packages. I'm not surprised it is broken and I don't know how to fix it. 

I recommend a fresh reinstall of 11.04. Good luck! :)

This may best solution! :)

---

### Post by madjr on 2011-08-01
fresh install and all those problems will be gone ! :)

note: backup (copy) your important files first to somewhere safe before reinstall.

oh and try not to use development releases unless you are a developer or beta tester :)

---

### Post by adamhum3 on 2011-08-01
Cheers guys. Just quickly, what's the easiest way to reinstall? I used wubi beforehand...

---

### Post by sanderd17 on 2011-08-01
If you used wubi, you can delete Ubuntu with the windows add/remove software utility. Afterwards you install Ubuntu again via any method.

You can do it via Wubi again (but do remember that wubi doesn't give all the advantages of Linux to you) or you can boot a live CD/USB and follow the installation wizard.

---

