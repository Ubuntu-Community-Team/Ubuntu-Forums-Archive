---
title: "Installing sun java6 jre?"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by JaxM on 2010-06-09
I'm jumping through hoops to get this installed on my computer yet I have no way that I know to obtain this. I've gone to the software center numerous times, tried installing via the terminal with no luck, and I've even gone to the website to get the thing and I'm still having no clue what I'm doing. Help is greatly appreciated. I currently have OpenJDK Runtime Environment which I got from the software center.

---

### Post by Autodave on 2010-06-09
> **JaxM said:**
> I'm jumping through hoops to get this installed on my computer yet I have no way that I know to obtain this. I've gone to the software center numerous times, tried installing via the terminal with no luck, and I've even gone to the website to get the thing and I'm still having no clue what I'm doing. Help is greatly appreciated. I currently have OpenJDK Runtime Environment which I got from the software center.

Have you tried typing this into the terminal?

sudo apt-get install ubuntu-restricted-extras

If that doesn't work, then go to Synaptic Package Manager and type  jre  in for your search.  Make sure that  openjdk-****** is installed.

---

### Post by tom.swartz07 on 2010-06-09
In 10.04, Java was moved to the Partner repos.

Open a terminal and run

```
sudo add-apt-repository “deb http://archive.canonical.com/ lucid partner”
```
```
sudo apt-get update
```
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

Then youre all set!

---

### Post by JaxM on 2010-06-09
> **tom.swartz07 said:**
> In 10.04, Java was moved to the Partner repos.

Open a terminal and run

```
sudo add-apt-repository “deb http://archive.canonical.com/ lucid partner”
```
```
sudo apt-get update
```
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

Then youre all set!

I actually tried that approach but something wasn't working.I also went through the package manager but there was no sun-java6-jre that came up. I watched a YouTube video on installing it and it worked.  (love the power of youtube) [http://www.youtube.com/watch?v=QYcX6CzEico]("http://www.youtube.com/watch?v=QYcX6CzEico")

I swear I love using the Terminal since becoming an Ubuntu user :D  so Solved thanks to the video :P but greatly appreciative of the replies :)

---

### Post by Legendary_Bibo on 2010-06-09
> **JaxM said:**
> I actually tried that approach but something wasn't working.I also went through the package manager but there was no sun-java6-jre that came up. I watched a YouTube video on installing it and it worked.  (love the power of youtube) [http://www.youtube.com/watch?v=QYcX6CzEico](http://www.youtube.com/watch?v=QYcX6CzEico)

I swear I love using the Terminal since becoming an Ubuntu user :D  so Solved thanks to the video :P but greatly appreciative of the replies :)
Ah I've been trying to get java installed to get a coupon from the taco bell site, but this is what I get.
```

bibo@Bibo:~$  sudo apt-get update
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Get:1 http://packages.medibuntu.org lucid Release.gpg [197B]              
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US           
Hit http://us.archive.ubuntu.com lucid Release.gpg                        
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US     
Hit http://ppa.launchpad.net lucid Release.gpg                            
Ign http://ppa.launchpad.net/easystroke/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                     
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US       
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Get:2 http://packages.medibuntu.org lucid Release [6,854B]                
Hit http://us.archive.ubuntu.com lucid Release                            
Hit http://ppa.launchpad.net lucid Release.gpg                            
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                
Hit http://security.ubuntu.com lucid-security/main Packages               
Hit http://us.archive.ubuntu.com lucid-updates Release                    
Hit http://ppa.launchpad.net lucid Release                                
Hit http://security.ubuntu.com lucid-security/restricted Packages         
Hit http://security.ubuntu.com lucid-security/main Sources                
Hit http://security.ubuntu.com lucid-security/restricted Sources          
Hit http://security.ubuntu.com lucid-security/universe Packages           
Hit http://packages.medibuntu.org lucid/free Packages                     
Hit http://us.archive.ubuntu.com lucid/main Packages                      
Hit http://us.archive.ubuntu.com lucid/restricted Packages           
Hit http://us.archive.ubuntu.com lucid/main Sources                  
Hit http://us.archive.ubuntu.com lucid/restricted Sources            
Hit http://us.archive.ubuntu.com lucid/universe Packages             
Hit http://ppa.launchpad.net lucid/main Sources                           
Hit http://ppa.launchpad.net lucid/main Packages                          
Hit http://security.ubuntu.com lucid-security/universe Sources            
Hit http://security.ubuntu.com lucid-security/multiverse Packages         
Hit http://security.ubuntu.com lucid-security/multiverse Sources          
Hit http://us.archive.ubuntu.com lucid/universe Sources                   
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                
Hit http://us.archive.ubuntu.com lucid/multiverse Sources            
Hit http://us.archive.ubuntu.com lucid-updates/main Packages         
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages   
Hit http://us.archive.ubuntu.com lucid-updates/main Sources          
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources    
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://packages.medibuntu.org lucid/non-free Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Fetched 7,051B in 1s (5,065B/s)
Reading package lists... Done
bibo@Bibo:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bibo@Bibo:~$ sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
[color=red]E: Package sun-java6-jre has no installation candidate[/color]
bibo@Bibo:~$ 

```

---

