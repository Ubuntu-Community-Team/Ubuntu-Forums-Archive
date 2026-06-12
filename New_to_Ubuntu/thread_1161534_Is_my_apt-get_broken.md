---
title: "Is my apt-get broken?"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by spillin_dylan on 2009-05-16
Hello, everyone.

I'm having some problems when trying to update my Ubuntu 8.10.

I have the 'Update Notification' icon telling me there are (currently) 30 updates available.  Telling it to start results in nothing spectacular, it goes through it's normal process, but when it gets to "Reading state information", it stops.  

The CLI method is no better, but at least I'm getting some kind of feedback from it:
```

spillin@Laptop:~$ sudo apt-get update
Hit http://apt.wicd.net intrepid Release.gpg
Ign http://apt.wicd.net intrepid/extras Translation-en_CA                                                
Hit http://apt.wicd.net intrepid Release                                                                 
Ign http://apt.wicd.net intrepid/extras Packages                                                                              
Hit http://apt.wicd.net intrepid/extras Packages                                                          
Hit http://cafelinux.org tinwoodman Release.gpg                                                           
Hit http://archive.ubuntu.com intrepid Release.gpg                                                        
Ign http://archive.ubuntu.com intrepid/main Translation-en_CA
Hit http://archive.canonical.com intrepid Release.gpg                
Ign http://archive.canonical.com intrepid/partner Translation-en_CA  
Ign http://cafelinux.org tinwoodman/main Translation-en_CA
Get:1 http://archive.ubuntu.com intrepid/restricted Translation-en_CA [3750B]
Ign http://archive.ubuntu.com intrepid/universe Translation-en_CA                                       
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_CA     
Hit http://archive.ubuntu.com intrepid-updates Release.gpg              
Get:2 http://archive.ubuntu.com intrepid-updates/main Translation-en_CA [2731B]
Hit http://archive.canonical.com intrepid Release                       
Hit http://cafelinux.org tinwoodman Release                                                                  
Get:3 http://archive.ubuntu.com intrepid-updates/restricted Translation-en_CA [3750B]                 
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_CA                                
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_CA
Hit http://archive.ubuntu.com intrepid-security Release.gpg             
Ign http://archive.ubuntu.com intrepid-security/main Translation-en_CA  
Ign http://archive.ubuntu.com intrepid-security/restricted Translation-en_CA
Ign http://archive.canonical.com intrepid/partner Packages              
Ign http://archive.ubuntu.com intrepid-security/universe Translation-en_CA
Ign http://archive.ubuntu.com intrepid-security/multiverse Translation-en_CA
Hit http://archive.ubuntu.com intrepid Release 
Ign http://cafelinux.org tinwoodman/main Packages                    
Hit http://archive.ubuntu.com intrepid-updates Release               
Hit http://archive.ubuntu.com intrepid-security Release                                                            
Ign http://archive.canonical.com intrepid/partner Sources                                                          
Hit http://archive.ubuntu.com intrepid/main Packages                                          
Hit http://archive.ubuntu.com intrepid/restricted Packages                                                                             
Hit http://archive.ubuntu.com intrepid/restricted Sources                                                                              
Hit http://cafelinux.org tinwoodman/main Packages                                                                                      
Hit http://archive.canonical.com intrepid/partner Packages                                                                             
Hit http://archive.ubuntu.com intrepid/main Sources                                                                                    
Hit http://archive.ubuntu.com intrepid/multiverse Sources                                                                              
Hit http://archive.ubuntu.com intrepid/universe Sources                                                                                
Hit http://archive.ubuntu.com intrepid/universe Packages                                                                               
Hit http://archive.ubuntu.com intrepid/multiverse Packages                                                                             
Hit http://archive.canonical.com intrepid/partner Sources                                                                              
Hit http://archive.ubuntu.com intrepid-updates/main Packages                                                                           
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages                                                                     
Hit http://archive.ubuntu.com intrepid-updates/restricted Sources                                                                      
Hit http://archive.ubuntu.com intrepid-updates/main Sources                                                                            
Hit http://archive.ubuntu.com intrepid-updates/multiverse Sources                                                                      
Hit http://archive.ubuntu.com intrepid-updates/universe Sources                                                                        
Hit http://archive.ubuntu.com intrepid-updates/universe Packages                                                                       
Hit http://archive.ubuntu.com intrepid-updates/multiverse Packages                                                                     
Hit http://archive.ubuntu.com intrepid-security/main Packages                                                                          
Hit http://archive.ubuntu.com intrepid-security/restricted Packages                                                                    
Hit http://archive.ubuntu.com intrepid-security/restricted Sources                                                                     
Hit http://archive.ubuntu.com intrepid-security/main Sources                                                                           
Hit http://archive.ubuntu.com intrepid-security/multiverse Sources                                                                     
Hit http://archive.ubuntu.com intrepid-security/universe Sources                                                                       
Hit http://archive.ubuntu.com intrepid-security/universe Packages                                                                      
Hit http://archive.ubuntu.com intrepid-security/multiverse Packages                                                                    
Fetched 10.2kB in 6s (1526B/s)                                                                                                         
Reading package lists... Done

```

Any thoughts on what's happening here, and why I can't update?

---

### Post by taurus on 2009-05-16
Now run this command and see what happens.

```
sudo apt-get upgrade
```

---

### Post by spillin_dylan on 2009-05-16
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  adobe-flashplugin apparmor apparmor-utils apport apport-gtk apport-qt e17-svn firefox firefox-3.0 firefox-3.0-branding
  firefox-3.0-gnome-support firefox-gnome-support gnome-system-tools libapparmor-perl libapparmor1 libmodplug0c2 libpango1.0-0
  libpango1.0-common libpango1.0-dev libwmf0.2-7 linux-generic linux-headers-generic linux-image-generic linux-libc-dev
  linux-restricted-modules-common linux-restricted-modules-generic python-apport python-problem-report xulrunner-1.9
  xulrunner-1.9-gnome-support
30 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.2MB of archives.
After this operation, 139kB of additional disk space will be used.
Do you want to continue [Y/n]? ^C

```

So, maybe I started the upgrade and it didn't finish? I hit yes BTW, so I'll let you know what happens once it downloads all the packages.  I'm assuming 9.04 will happen instead of 8.10

---

### Post by spillin_dylan on 2009-05-16
Well that looks like it worked perfectly!  The output is waa-aa-a-aay too long to post the whole thing, but it looks like that updated all 30 packages, and I'm still in Intrepid, so that's cool!  All I have to do now is restart FireFox, and then "Bob's your uncle!"

Thanks, taurus!

---

