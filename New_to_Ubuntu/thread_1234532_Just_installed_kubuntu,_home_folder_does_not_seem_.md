---
title: "Just installed kubuntu, home folder does not seem to be home partition"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by barbedsaber on 2009-08-08
Ok, so I just installed kubuntu 9.04 because I was sick of GNOME
During the install, I decided to use a proper home partition.
From the live usb, I deleted everything on my old install/home partition (except the home folder) and moved everything from that folder, out of that folder.
When I opened that partition, I saw all the files from my home folder, along with things like my music folder, etc.
During the kde install, I specified that I wanted that partition to NOT be formated, and to be used as an ext4 home partition/folder
Now that the install has finished, when I click home on the desktop, I get a blank home folder (with empty folders for music and such)
when I manually go to /home I see my files.

```
harry@Toaster:~$ ls
Desktop    Music     Public                     Templates
Documents  Pictures  screen-configurations.xml  Videos   
harry@Toaster:~$ cd /home                                
harry@Toaster:/home$ ls                                  
26-06-09_1236.jpg                                        
2965809295_36ec284d56_o.jpg                              
30-04-09_1242.jpg                                        
381kenya3.swf                                            
7100.0.090421-1700_x86fre_client_en-us_retail_ultimate-grc1culfrer_en_dvd.iso.dlm                                                                               
Alex's Pong Game                                                                
Alex's Pong Game.zip                                                            
all my crap                                                                     
anime stuff                                                                     
anti drm                                                                        
backup                                                                          
bornpost.pdf                                                                    
cake.zip                                                                        
Chatlog.txt                                                                     
contens of thumbdrive                                                           
davidmeshow                                                                     
demote again again                                                              
Desktop                                                                         
Documents                                                                       
Downloads                                                                       
## The rest of my files are there as well, but you don't need to see all of them :)

```

Is there any way I can fix this so when I click home on the desktop, it will be the right place where all my stuff is?
thanks for you're help, am new to this whole KDE thing.

---

### Post by bigbrovar on 2009-08-08
hmm i cant quite get what the problem is .. i sent you a msg on twitter?

---

### Post by bigbrovar on 2009-08-08
must be a problem during installation, did you remember to use the same user name as the last install, anyway why not just mv the files from /home to /home/username ? you might have to use sudo for that probably start dolphin as root and move the files to your /home/username then open konsole and do

sudo chown -R yourusername /home/userusername

---

### Post by barbedsaber on 2009-08-08
lol, taht was obvious, doing it now, and it seems to be working
thanks man.

---

### Post by mapes12 on 2009-08-08
If the installer set /home on the same partition as "/" then the system may think that /home is still there and not the other partition you are mv files to. This HowTo may be a permanent fix: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

