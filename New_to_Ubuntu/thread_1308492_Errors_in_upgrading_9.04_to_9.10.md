---
title: "Errors in upgrading 9.04 to 9.10"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by zaivala on 2009-10-31
I just finished upgrading... almost...

Using Upgrade Manager in Ibis, I upgraded to Koala... but xulrunner would not install.  Everything else appears to be installed.  I was informed that I did not have a complete installation, and that my system may not boot properly.  I was asked to report the problem, and clicked on the icon to do so... a minute later, I was informed that my download was not a genuine Ubuntu installation and therefore could not be reported.

The system did, after some fancy keywork, reboot.  But without Firefox, so I couldn't get online to report it (fortunately I also have a Windoze machine).  I attempted to upgrade my installation, and was told that I did not have a complete installation and so could only do a partial install.  While doing that, I booted my WIndoze machine and am using it to type this message.

My machine is a Gateway E6100, 2.6 GHz HT single core, which has been running 9.04 for several months without an issue.

Update: The 'update' that Ubuntu did removed xulrunner 1.9.  I assume in installed something else.  I haven't tried my sound yet (something others have said they had problems with), but everything seems to work... including Firefox, although the icon in my taskbar is still a red-circle-with-a-slash.

Update 2: Sound is not working, and while Firefox works it still has the red-slash-and-circle icon in the taskbar.

---

### Post by kansasnoob on 2009-10-31
You said:

> Using Upgrade Manager in Ibis, I upgraded to Koala

Assuming you were running Intrepid Ibex you shouldn't have been able to upgrade directly to Karmic Koala. You would have to go Intrepid > Jaunty > Karmic.

What output is displayed in terminal if you run the command:

```
cat /etc/issue
```

Also run this command **[COLOR="Red"]but do NOT click on y (yes), just copy & paste the results here[/COLOR]**:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by zaivala on 2009-10-31
I did misspeak, I had already upgraded to Jackalope, although I had to do a fresh install.  For this I apologize.  Nonetheless, I still have no sound.  I will go run the things you suggested and report back.

---

### Post by zaivala on 2009-10-31
> **kansasnoob said:**
> You said:



Assuming you were running Intrepid Ibex you shouldn't have been able to upgrade directly to Karmic Koala. You would have to go Intrepid > Jaunty > Karmic.

What output is displayed in terminal if you run the command:

```
cat /etc/issue
```

Also run this command **[COLOR="Red"]but do NOT click on y (yes), just copy & paste the results here[/COLOR]**:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

To the first, I received "Ubuntu 9.10 /n/l"

---

### Post by zaivala on 2009-10-31
To the second...

zaivala@zaivala-desktop:~$ sudo apt-get update && sudo apt-get dist-upgrade
[sudo] password for zaivala: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by kansasnoob on 2009-10-31
If you right click the sound icon is mute ticked? If so untick it.

Does the Firefox icon have a red circle & slash thru it?

---

### Post by zaivala on 2009-10-31
> **kansasnoob said:**
> If you right click the sound icon is mute ticked? If so untick it.

Does the Firefox icon have a red circle & slash thru it?

OK, the sound icon did not show up on my taskbar at all (or whatever Linuxers call it), so I checked the System - Preferences, and found the Output Volume was a tad low.  Now the sound is working... but I don't believe that was all that was wrong, although some of it could have been a short circuit between the chair and the keyboard.

No, there is no Firefox icon.  There is an icon featuring a grey box with a red circle and slash through it where the Firefox icon SHOULD be, and clicking on that causes Firefox to run.

---

### Post by rburkartjo on 2009-10-31
zai i had a similar problem with the ff icon. i just deleted the desktop messed up icon and went to app/internet/ high lighted the ff icon right clicked and then selected add this launcher to desktop

---

### Post by zaivala on 2009-10-31
Worked great, thanks rburkartjo

---

