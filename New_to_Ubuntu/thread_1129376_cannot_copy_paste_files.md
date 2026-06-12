---
title: "cannot copy paste files"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by the_kop on 2009-04-18
This is what I get when i try to update.

hmw@han-laptop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg
Hit [http://apt.wicd.net](http://apt.wicd.net) lenny Release.gpg                                      
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lenny Release.gpg                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB [27.0kB]   
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_GB            
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_GB        
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper Release.gpg                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_GB  
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_GB    
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper/main Translation-en_GB     
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB [27.0kB]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_GB  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper/dupdate Translation-en_GB  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Ign [http://apt.wicd.net](http://apt.wicd.net) lenny/extras Translation-en_GB                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://apt.wicd.net](http://apt.wicd.net) lenny Release                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources            
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper/french Translation-en_GB   
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB [27.0kB]   
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu Release.gpg                
Ign [http://apt.wicd.net](http://apt.wicd.net) lenny/extras Packages                                  
Hit [http://apt.wicd.net](http://apt.wicd.net) lenny/extras Packages                                  
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB [27.0kB]   
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB [27.0kB]   
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB [27.0kB]   
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB [27.0kB]   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB         
99% [7 Translation-en_GB bzip2 0] [Connecting to gb.archive.ubuntu.com (194.169
bzip2: Data integrity error when decompressing.                                
        Input file = (stdin), output file = (stdout)                           

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.     

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.            

Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources
Ign [http://download.virtualbox.org](http://download.virtualbox.org) lenny/non-free Translation-en_GB
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lenny Release
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lenny/non-free Packages
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/main Translation-en_GB
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/dupdate Translation-en_GB
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/french Translation-en_GB
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper Release
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu Release
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper/main Packages
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper/dupdate Packages
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper/french Packages
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/main Packages
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/dupdate Packages
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/french Packages
Hit [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper/main Packages
Hit [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper/dupdate Packages
Hit [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper/french Packages
Hit [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/main Packages
Hit [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/dupdate Packages
Hit [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/french Packages
Fetched 269B in 5s (49B/s)
Reading package lists... Done

I suspect that the problem is in the line about bzip2recover. Any help would be greatly appreciated.

---

### Post by llamabr on 2009-04-18
What does this have to do with copy pasting files?

Try taking that line out of your sources.list and run it again.  You have a massively big sources.list.

---

### Post by the_kop on 2009-04-18
I have unchecked all the third party softwares. run update again and same problem. If it is not the case, then I just want to fix that copy and paste problem which is really annoying.

I can see copy and cut but when I selected those, paste was still greyed out.

---

### Post by sgosnell on 2009-04-18
What copy and paste problem?  I still don't understand your problem.  There is no copying, cutting, or pasting going on with updating.

---

### Post by the_kop on 2009-04-18
My problem was with copy, pasting files and folders. Those commands do not work. I posted the list on update just in case.

---

### Post by sgosnell on 2009-04-18
How are you trying to do this?  Terminal or file manager?  What files in what folders?  You can't access folders owned by root unless you have root access, via sudo or starting the file manager with gksudo.  You haven't given nearly enough information about your problem.

---

### Post by the_kop on 2009-04-18
Just normal copy, paste in ordinary folders in GUI(right click, copy-paste, but paste is greyed out) not in terminal and not the folders in root.

---

### Post by sgosnell on 2009-04-18
The only folders you own as a user are in your home folder and below.  You own none of the system folders, thus you can't write to any of them unless you have root privileges, through sudo.

---

### Post by the_kop on 2009-04-18
Folders in my /home/... only. not in system folders such as those in root as you have mentioned. But still, I should still be able to at least click paste but it was greyed out.

---

### Post by sgosnell on 2009-04-18
I have no idea, then, unless your home folder has become read-only.  Have you checked the permissions on those folders?

---

### Post by the_kop on 2009-04-18
the permissions are all right(readable and writeable). Can you please have a look at the error on the update maybe?

---

### Post by sgosnell on 2009-04-18
That has nothing to do with it.  You've downloaded a corrupt file, apparently.  That won't affect your ability to write to your home folder.  It's just coincidence.

---

### Post by Toshubu on 2009-04-18
...No idea...Have you tried simply re-booting?..(I'm also inclined to believe that the updates problem has nothing to do with the copy/paste functions.)

---

### Post by halitech on 2009-04-18
I agree with the others on the update failure has nothing to do with being able to copy/paste anything.

where are you trying to paste a file/folder? (ie, exact location)

is the folder a mounted drive in your home folder? (ie, thumbdrive?)

---

### Post by llamabr on 2009-04-19
It looks like you have two distinct issues, but which you think are the same.

Copy/paste.  If you're having trouble pasting files into your home directory, you messed up permissions.  Navigate to /home, and do a:

```
ls -l
```

The other: you have a bad line in your sources.list.  Post it and we'll find it.

---

