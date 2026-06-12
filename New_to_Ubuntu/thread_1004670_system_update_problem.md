---
title: "system update problem"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by andrew222 on 2008-12-07
Hello,

Thank you for reading this post.

Just this morning I started receiving an error icon (orange, triangular, with exclamation mark in middle).  When I put the cursor over it i got this message that scripted below the icon:

[COLOR="Red"]**"The update information is outdated.  This may be caused by network problems or by a repository that is no longer available.  Please update manually by clicking on this icon and then selecting 'check for updates' and check if some of the listed repositories fail."[/COLOR]**


After I clicked the icon and checked for updates, I got this error message; this is a paste of exact message from the GUI box...

[B][COLOR="Red"]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.[/COLOR][/B]


The only actions done in the past that have could have triggered was going to a site that was titled"20 things to do after installing Ubuntu" and another site titled"50 ways to speed up the boot process in Ubuntu".


Any suggestions / advice are more than welcome.

---

### Post by taurus on 2008-12-07
What happens when you run these commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```
Remember to close Update-Manager first before you run those two commands.

---

### Post by andrew222 on 2008-12-07
Hello Taurus,

Thank you for your reply...
I tried the two commands and here is the exact output received.....



[I][COLOR="SlateGray"]andrew@andrew-desktop:~$ sudo apt-get update
[sudo] password for andrew: 
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release.gpg
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release  
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages
Err cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-en_US        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US                  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Translation-en_US   
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Sources
W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
andrew@andrew-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andrew@andrew-desktop:~$ 

[/COLOR][/I]

---

### Post by lovelyvik293 on 2008-12-07
I think you have to use the 
```
apt-cdrom add
``` 
to add the cdrom.
And then use the
```

apt-get update

```
again.

---

### Post by Michael.Godawski on 2008-12-07
I would comment out the hardy heron entries... You are on Intrepid, aren't you? Why bothering wilh old repositories. 
Just comment out the hardy entries with a # in front of the line and save the file.
Open the sources.list with:
```

gksudo gedit /etc/apt/sources.list
```Then once again

```
sudo apt-get udpate
sudo apt-get upgrade
```

---

### Post by andrew222 on 2008-12-07
Hello Taurus,


I just went to 'Administration > Software Sources > Third Party Software and removed the check mark denoting "Cdrom with Ubuntu 8.04 'Hardy Heron'"..

Seeing such references to such an item in the terminal output prompted me to act and do so,  I do not see the error icon anymore...

---

### Post by andrew222 on 2008-12-07
Hello,

Thank you for your replies.



**lovelyvik293:** I will be sure to remember those commands for future use, thank you so much...


**Michael.Godawski:**  That is what I had in mind regarding my previous post, but I did not know about this one.  I shall do this as well to be on the safe side...



Thanks again...

---

