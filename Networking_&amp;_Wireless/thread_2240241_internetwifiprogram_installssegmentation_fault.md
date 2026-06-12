---
title: "internet/wifi/program installs/segmentation fault"
date: 2014-08-18
forum: Networking &amp; Wireless
---

### Post by terry22 on 2014-08-18
&#65279;I have just installed xubuntu 14 on a Dell 1300 series. I am totally new to ubuntu so am fumbling around trying to learn and understand. I'll start at the beginning as my fix for original problem may be causing what i have happening now. Hopefully someone can point me in the right direction. Thanks.
When I installed xubuntu I could access the internet via ethernet only. "enable WIFI" did not show on the network menu. After some research I found a solution that works. I downloaded b43 file and in terminal entered "sudo mv b43 /lib/firmware" then "sudo modprobe b43" and it then worked until I shut down computer.
I found a source that said to do the following:

```
$ sudo apt-get remove --purge bcmwl-kernel-source
$ sudo apt-get install linux-firmware-nonfree
$ sudo modprobe b43
$ sudo su
echo "b43" >> /etc/modules
```

I did that and I thought everything was working well until I tried to install gparted through the  ubuntu software centre. After 
entering my password gparted started installing but after a few moments the install froze and internet disconnected. I tried with wifi
and ethernet with the same result. If using WIFI, wifi would actually disappear off of the network menu.When I restart to get internet
back, ubuntu freezes on xubuntu screen and i have to force shutdown with power key.
My next move was to try to install via terminal with the following results:

```
barbie@barbie-ME051:~$ sudo apt-get install gparted
[sudo] password for barbie: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

[COLOR=#ff0000]**So, I now run the command:**[/COLOR]```

barbie@barbie-ME051:~$ sudo dpkg --configure -a
Setting up bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Removing old bcmwl-6.30.223.141+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.141+bdcom
Kernel:  3.13.0-34-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-34-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.......

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.30.223.141+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.30.223.141+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-34-generic
Building for architecture i686
Building initial module for 3.13.0-34-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-34-generic/updates/dkms/

depmod....

DKMS: install completed.
Segmentation fault
```

**[COLOR=#ff0000]At this point internet disconnects and WIFI disappears from network menu. I have to force ubuntu to shut down. I have tried installing other software with the same result...telling me to run "dpkg" etc....same reuslts. Somewhere I found the suggestion to run the command below which ends with the same "segmentation fault" and loss of internet.[/COLOR]**
  
```
barbie@barbie-ME051:~$ sudo apt-get update
[sudo] password for barbie: 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty InRelease
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports InRelease                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release.gpg
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports Release.gpg
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports Release             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en_CA       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en_CA   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Sources         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Sources   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Sources   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_CA           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main i386 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en_CA
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```
```
barbie@barbie-ME051:~$ sudo dpkg --configure -a
Setting up bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Removing old bcmwl-6.30.223.141+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.141+bdcom
Kernel:  3.13.0-34-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-34-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.......

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.30.223.141+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.30.223.141+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-34-generic
Building for architecture i686
Building initial module for 3.13.0-34-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-34-generic/updates/dkms/

depmod....

DKMS: install completed.
Segmentation fault
```

---

### Post by varunendra on 2014-08-19
Welcome to the forums terry22!

Firstly, if your card is supported by b43, you don't need to add it to /etc/modules. So remove that entry with the following command -
```
sudo sed -i '/b43/ d' /etc/modules
```
Next, purge the incorrect 'wl' module package -
```
sudo apt-get purge bcmwl-kernel-source
```
If it returns error and asks you to run 'sudo dpkg --configure -a', please do so after a reboot. Then repeat the command above. Any improvement or are we still stuck in the dpkg loop?

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by slickymaster on 2014-08-19
Moved to the **Networking & Wireless** sub-forum.

---

### Post by Elfy on 2014-08-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by terry22 on 2014-08-19
Thanks for your quick reply. "sudo sed -i '/b43/ d' /etc/modules" seemed to run ok. "sudo apt-get purge bcmwl-kernel-source" resulted in  the same request to run 'sudo dpkg --configure -a' which resulted in the failure as before.  The only change is that wifi is no longer listed on the network menu so I am back to no wifi. Thanks for the tip re code tag too. I still cannot install any programs. Same results....when in software centre the ethernet disconnects after maybe a minute after putting in password to install. Further suggestions?

---

### Post by terry22 on 2014-08-19
Attached (I think) is the text file output  from running the wireless script. I'm not sure if the 2 problems may be  related? As I am in VERY early learning stage. I will follow your suggestions so that I don't add to problems by messing with stuff.

---

### Post by varunendra on 2014-08-19
Please try -
```
sudo dpkg -P bcmwl-kernel-source
```
..and reboot.

Does it succeed to get rid of the offending package?

---

### Post by terry22 on 2014-08-19
THANKYOU varunendra. All is working now. I have wifi and can install programs. Being totally uneducated in these commands, would you be able to give me a short explanation of what I just did and what might have caused the problem?...something I did? I'm not even sure what the 'package' you refer to means. I have lots of reading and learning to do. From what I've seen so far, I love ubuntu...make this old laptop useable again. thankyou again.

---

### Post by varunendra on 2014-08-19
You're welcome! :)

I'm just a learner like you (those bean counts NEVER mean one is expert in anything) and will try to explain what I have understood so far -

The 'apt-get' command works at a higher level, and needs the package dependency tree to be all good and consistent to work properly.
The 'dpkg' command works at a more basic level and can deal with individual packages, regardless of possible inconsistencies in the package dependency tree.

The "dpkg -P bcmwl-kernel-source" command just 'purged' (means removed the package, as well as its configuration settings) the "bcmwl-kernel-source" package that was causing troubles (and that's what I called "offending package"). Once it got out of the system, the rest became consistent and working again.

I'm not sure about what might have caused the problem, but my best guess is that the 'b43' driver was loaded and had claimed the wireless card while you did the update. You must have either selected the "bcmwl-kernel-source" package manually, or it was installed prior to the update (following some guide/tutorial or by accepting the "Additional Drivers" offer). It is a software package that installs the alternative proprietary driver "wl" for the same wireless card that was already claimed by the native "b43" driver.

During installation, the package configuration routine tries to load the "wl" driver to make the wifi work, but the card was already in use by "b43" driver and that caused a conflict between "b43" and "wl" drivers, resulting in a system freeze (this is a common problem when both these drivers are loaded simultaneously for the same card). As such, the configuration stage did not reach its final stage, and you got stuck in a broken package dependency loop.

My earlier suggestion was based on the guess that the configuration of the "bcmwl-kernel-source" package should have blacklisted the "b43" driver to prevent it from loading and conflicting with "wl", and it was still loading only because you had also added it to /etc/modules, thus overriding the blacklist. I'm not sure what caused the "dpkg configure -a" failure even after removing that entry from /etc/modules (maybe you tried it without rebooting?). But the last command - "dpkg -P bcmwl-kernel-source" got rid of the offending package anyhow, and got you a stable, consistent system again.

Take-Home lesson - Don't even try the "wl" driver (package name - "bcmwl-kernel-source") again. The "Additional Drivers" program offers the same one, just don't accept its offer since the native "b43" is better for your card.

---

### Post by terry22 on 2014-08-19
thanks....lots of reading in my future i see

---

