---
title: "Cinelerra Install Help"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by Vicki17 on 2009-08-30
Hi, I'm new to Ubuntu and I'm trying to install Cinelerra for video editing. I've endlessly searched the forums trying to find a solution for my problem. I have 8.10 installed right now. I used to have 9.04 ubuntu installed but I thought my cinelerra related install issues might be due to the newer verision so i switched. i've tried to figure out the heroinewarrior.com verison but so far i've had no luck. I used the instructions at  [http://cvs.cinelerra.org/getting_cinelerra.php](http://cvs.cinelerra.org/getting_cinelerra.php). i put in ```
echo deb http://akirad.cinelerra.org akirad-intrepid main | sudo tee  /etc/apt/sources.list.d/akirad.list && wget -q  http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add - &&  sudo apt-get update
``` then after it says its all good i enter ```
sudo apt-get install cinelerra
``` then i recieve ```
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://giss.tv ./ Release.gpg                                              
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://us.archive.ubuntu.com hardy-backports Release.gpg                   
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US        
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US  
Hit http://archive.canonical.com hardy Release                                 
Hit http://us.archive.ubuntu.com hardy-updates Release                         
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com hardy-security Release                          
Ign http://giss.tv ./ Release                                                  
Hit http://us.archive.ubuntu.com hardy Release                                 
Hit http://us.archive.ubuntu.com hardy-backports Release                       
Hit http://archive.canonical.com hardy/partner Packages                        
Get:1 http://repository.akirad.net akirad-hardy Release.gpg [197B]             
Ign http://repository.akirad.net akirad-hardy/main Translation-en_US           
Hit http://security.ubuntu.com hardy-security/main Packages                    
Ign http://giss.tv ./ Sources                                                  
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages               
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources                
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages             
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources              
Hit http://archive.canonical.com hardy/partner Sources                         
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://security.ubuntu.com hardy-security/universe Packages                
Get:2 http://repository.akirad.net akirad-hardy Release [3530B]                
Hit http://us.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://us.archive.ubuntu.com hardy/multiverse Sources                      
Hit http://giss.tv ./ Sources                                                  
Hit http://us.archive.ubuntu.com hardy-backports/main Packages                 
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages 
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages   
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages 
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-backports/main Sources
Hit http://us.archive.ubuntu.com hardy-backports/restricted Sources
Hit http://us.archive.ubuntu.com hardy-backports/universe Sources
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Sources
Get:3 http://repository.akirad.net akirad-hardy/main Packages [18.7kB]
Fetched 22.4kB in 0s (29.5kB/s)
Reading package lists... Done
vkallsen@vkallsen-computer:~$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: cinelerracv but it is not going to be installed or
                      cinelerrahv but it is not installable
E: Broken packages

```:confused: I just need a simple solution to the broken packages problem. i'd prefer the community version but at this point if anyone can get some version of it installed, that would be fantastic. its okay if it will only work for the ubuntu 8.10 but if i could switched back to 9.04 that would be so very much appreciated. thank you!

---

### Post by nhasian on 2009-08-30
after you added akirad.cinelerra.org to the repository, did you do:

```
sudo apt-get update
```

---

### Post by zvacet on 2009-08-31
You are saying that you have Intrepid installed but your sources list is for Hardy.Edit your sources list 

```
gksudo gedit /etc/apt/sources.list
```

and replace hardy with intrepid in all lines.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

Now you try to install.If you get broken packages error 

```
sudo apt-get -f install
```

---

### Post by sfwasabi on 2009-09-08
THANK YOU THANK YOU THANK YOU!!!

It never occurred to me that when I upgraded Ubuntu that it didn't rewrite the sources.list. All my sources said "Jaunty". When I renamed them to "Intrepid" it did the installation with no problems.

Thank you!

---

