---
title: "Update problem"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by Garthhh on 2010-11-27
My up dates aren't finishing, since I tried to install ipython yesterday [for exaile]
marked error

---

### Post by Garthhh on 2010-11-27
this is from trying to update
marked Error2

---

### Post by karthick87 on 2010-11-27
Try 

```
sudo apt-get update
```

---

### Post by Garthhh on 2010-11-27
> **karthick87 said:**
> Try 

```
sudo apt-get update
```

I just ran that on a terminal
it looked like it checked all the repositories I'm using


Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/) lucid/main Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,338B]                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [613B]                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release                       
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources              
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages
Fetched 2,140B in 2s (1,031B/s)
Reading package lists... Done

I ran update manager again same result
same with ipython

---

### Post by Penguin=) on 2010-11-27
Ok, try checking the repositories for iPython.

You said it checked the repositories and by the looks of it, i think it found it in your repositories, so i would go into Synaptic and search iPython.


Get back to me on how it went.:p

---

### Post by Garthhh on 2010-11-27
> **Penguin=) said:**
> Ok, try checking the repositories for iPython.

You said it checked the repositories and by the looks of it, i think it found it in your repositories, so i would go into Synaptic and search iPython.


Get back to me on how it went.:p

Both updating [update manager] or installing ipython through synaptic give the same error
linux-headers-2.6.32-25 generic & so forth

---

### Post by karthick87 on 2010-11-27
@Garthhh Always post your results in [CODE] tag.So that it will be easy for an user to answer your question.

---

### Post by Garthhh on 2010-11-27
which part?

---

### Post by karthick87 on 2010-11-27
> **Garthhh said:**
> which part?

post [#4]("http://ubuntuforums.org/showpost.php?p=10169989&postcount=4")

---

### Post by Garthhh on 2010-11-27
> **Garthhh said:**
> I just ran that on a terminal
it looked like it checked all the repositories I'm using


```
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/) lucid/main Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,338B]                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [613B]                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release                       
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources              
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages
Fetched 2,140B in 2s (1,031B/s)
Reading package lists... Done
```

I ran update manager again same result
same with ipython

more like that?

---

### Post by Garthhh on 2010-11-28
after some more testing
I get this error

Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `linux-headers-2.6.32-25-generic': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

I actually get this error, if I try to add anything on synaptic, or update or install any thing from software center

If I look up the 2 packages with similar titles in synaptic & try to reinstall, synaptic turns gray & crashes

---

### Post by Garthhh on 2010-11-28
I was going to file a bug, but decided to ask a question on launch pad  [https://answers.launchpad.net/ubuntu/+source/update-manager/+question/135770](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/135770)
which leads to [http://ubuntuforums.org/showthread.php?t=1232143](http://ubuntuforums.org/showthread.php?t=1232143)
the last post seems very similar, but I don't quite follow which file I should edit?
[last post] makes the most sense, when I go to where the offending files are [usr/share/doc/linux-headers-2.6.32-25-generic],  they are dated october, while linux-headers-2.6.32-26-generic are dated wednesday

---

### Post by Garthhh on 2010-11-30
Launch Pad [thanks Sam], got me there
the `problem was with dpkg, the headers was a symptom.
Here is a step by step:
#1
Backup the file (rename it with whatever ending you like)e.g.:
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-broken

#2
Open the file and find the line regarding: linux-headers-2.6.32-25-generic
gksudo gedit /var/lib/dpkg/status

Remove only the lines concerning this package.
## You can search gedit by ctrl+F and insert the text in the popup window.
## Don't forget to leave one empty line between the other two packages left above and below.

## Before edit example
## Content of lines incl. linux-headers-2.6.32-25-generic between two other packages.
[http://paste.ubuntu.com/538121/](http://paste.ubuntu.com/538121/)

## After removal example
[http://paste.ubuntu.com/538124/](http://paste.ubuntu.com/538124/)

#3
Save the edited file.
Close all package management GUIs e.g. Synaptic, Software Center... while working in the terminal.
In case one of them outputs an error post it here.

sudo dpkg --configure -a
sudo apt-get -f install

In case reinstall the package:
sudo apt-get install linux-headers-2.6.32-25-generic 
__.____._

---

