---
title: "How apt-get works? Downloading some files 2x?"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by Kangarooo on 2010-07-20
heres output of dist-update
some are 2 times.
why?
```
Get:259 http://lv.archive.ubuntu.com/ubuntu/ maverick/main radeontool 1.6.1-1 [68,4kB]                                                       
Get:260 http://lv.archive.ubuntu.com/ubuntu/ maverick/main rtkit 0.8-0ubuntu1 [30,9kB]                                                       
Get:261 http://lv.archive.ubuntu.com/ubuntu/ maverick/main smbclient 2:3.5.4~dfsg-1ubuntu2 [13,8MB]                                          
Get:262 http://lv.archive.ubuntu.com/ubuntu/ maverick/main samba-common 2:3.5.4~dfsg-1ubuntu2 [395kB]                                        
Get:263 http://lv.archive.ubuntu.com/ubuntu/ maverick/main samba-common-bin 2:3.5.4~dfsg-1ubuntu2 [5*823kB]                                  
Get:264 http://lv.archive.ubuntu.com/ubuntu/ maverick/main sane-utils 1.0.21-2ubuntu2 [215kB]                                                
Get:265 http://lv.archive.ubuntu.com/ubuntu/ maverick/main sane-utils 1.0.21-2ubuntu2 [215kB]                                                
Get:266 http://lv.archive.ubuntu.com/ubuntu/ maverick/main software-center 2.1.5 [335kB]
Get:267 http://lv.archive.ubuntu.com/ubuntu/ maverick/main syslinux 2:4.01+dfsg-3ubuntu1 [87,9kB]                                            
Get:268 http://lv.archive.ubuntu.com/ubuntu/ maverick/main syslinux-common 2:4.01+dfsg-3ubuntu1 [1*120kB]                                    
Get:269 http://lv.archive.ubuntu.com/ubuntu/ maverick/main system-config-printer-common 1.2.3+20100713-0ubuntu1 [128kB]                      
Get:270 http://lv.archive.ubuntu.com/ubuntu/ maverick/main system-config-printer-common 1.2.3+20100713-0ubuntu1 [128kB]                      
Get:271 http://lv.archive.ubuntu.com/ubuntu/ maverick/main system-config-printer-gnome 1.2.3+20100713-0ubuntu1 [194kB]
Get:272 http://lv.archive.ubuntu.com/ubuntu/ maverick/main system-config-printer-udev 1.2.3+20100713-0ubuntu1 [16,5kB]
Get:273 http://lv.archive.ubuntu.com/ubuntu/ maverick/main transmission-gtk 2.00-1ubuntu1 [317kB]
Get:274 http://lv.archive.ubuntu.com/ubuntu/ maverick/main transmission-common 2.00-1ubuntu1 [189kB]
Get:275 http://lv.archive.ubuntu.com/ubuntu/ maverick/universe ufraw-batch 0.16-3 [290kB]                                                    
Get:276 http://lv.archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-radeon 1:6.13.1-1ubuntu1 [641kB]                               
Get:277 http://lv.archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-ati 1:6.13.1-1ubuntu1 [245kB]                                  
Get:278 http://lv.archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-vmware 1:11.0.1-2 [44,8kB]                                     
Get:279 http://lv.archive.ubuntu.com/ubuntu/ maverick/main xulrunner-1.9.2 1.9.2.7+build2+nobinonly-0ubuntu1 [9*376kB]                       
Get:280 http://lv.archive.ubuntu.com/ubuntu/ maverick/main yelp 2.30.1-0ubuntu1 [375kB]                                                      
Get:281 http://lv.archive.ubuntu.com/ubuntu/ maverick/main inputattach 20051019-12 [14,9kB]                                                  
Get:282 http://lv.archive.ubuntu.com/ubuntu/ maverick/main libdconf0 0.4.2-1 [30,6kB]                                                        
Get:283 http://lv.archive.ubuntu.com/ubuntu/ maverick/main libglu1-mesa 7.8.1-3ubuntu3 [189kB]                                               
Get:284 http://lv.archive.ubuntu.com/ubuntu/ maverick/main libspeechd2 0.7-5ubuntu1 [28,5kB]                        
```

---

### Post by lordbux on 2010-07-20
if you give ```
apt-get update
```

it will go to server and get the list of latest softwares available, so it can see if any newer versions are available and offer an update.

if you give ```
apt-get install <software name>
```
It will download that software and install it for you..

eg: ```
apt-get install firefox
```

ya and of course you have to use the ```
sudo 
```command  

eg:```
 sudo apt-get update
```

---

### Post by Paqman on 2010-07-20
No idea why it's downloading those twice. Try a different server and see if you get the same problem.

---

