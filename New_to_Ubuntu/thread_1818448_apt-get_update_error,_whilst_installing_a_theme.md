---
title: "apt-get update error, whilst installing a theme"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by adamhum3 on 2011-08-04
So I've been installing a few themes, and adding repositories whilst doing so, I'm guessing that's what's causing the problem. Here's what comes up when I use apt-get update:

```
adam@Adam-PC:~$ sudo apt-get update
Ign http://security.ubuntu.com natty-security InRelease
Hit http://security.ubuntu.com natty-security Release.gpg                      
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://security.ubuntu.com natty-security Release                          
Ign http://archive.canonical.com natty InRelease                               
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://gb.archive.ubuntu.com natty InRelease                               
Ign http://gb.archive.ubuntu.com natty-updates InRelease                       
Ign http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://extras.ubuntu.com natty InRelease                                   
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://gb.archive.ubuntu.com natty Release.gpg                             
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                       
Hit http://archive.canonical.com natty Release                                 
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://ppa.launchpad.net natty Release                           
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/main amd64 Packages              
Hit http://security.ubuntu.com natty-security/restricted amd64 Packages        
Hit http://gb.archive.ubuntu.com natty-updates Release.gpg                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://extras.ubuntu.com natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://security.ubuntu.com natty-security/universe amd64 Packages          
Hit http://security.ubuntu.com natty-security/multiverse amd64 Packages        
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Hit http://archive.canonical.com natty/partner amd64 Packages                  
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Hit http://gb.archive.ubuntu.com natty Release                                 
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://extras.ubuntu.com natty/main Sources                                
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://gb.archive.ubuntu.com natty-updates Release                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Hit http://extras.ubuntu.com natty/main amd64 Packages                         
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://gb.archive.ubuntu.com natty/main Sources                            
Hit http://gb.archive.ubuntu.com natty/restricted Sources                      
Hit http://gb.archive.ubuntu.com natty/universe Sources                        
Hit http://gb.archive.ubuntu.com natty/multiverse Sources                      
Hit http://gb.archive.ubuntu.com natty/main amd64 Packages                     
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://gb.archive.ubuntu.com natty/restricted amd64 Packages               
Hit http://gb.archive.ubuntu.com natty/universe amd64 Packages                 
Hit http://gb.archive.ubuntu.com natty/multiverse amd64 Packages               
Ign http://gb.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://gb.archive.ubuntu.com natty/multiverse TranslationIndex             
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://gb.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://gb.archive.ubuntu.com natty/universe TranslationIndex               
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://gb.archive.ubuntu.com natty-updates/main Sources                    
Hit http://gb.archive.ubuntu.com natty-updates/restricted Sources              
Hit http://gb.archive.ubuntu.com natty-updates/universe Sources                
Hit http://gb.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://gb.archive.ubuntu.com natty-updates/main amd64 Packages             
Hit http://gb.archive.ubuntu.com natty-updates/restricted amd64 Packages       
Hit http://gb.archive.ubuntu.com natty-updates/universe amd64 Packages         
Hit http://gb.archive.ubuntu.com natty-updates/multiverse amd64 Packages       
Ign http://gb.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://gb.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://gb.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://gb.archive.ubuntu.com natty-updates/universe TranslationIndex       
Hit http://gb.archive.ubuntu.com natty/main Translation-en_GB                  
Hit http://gb.archive.ubuntu.com natty/multiverse Translation-en_GB            
Hit http://gb.archive.ubuntu.com natty/restricted Translation-en_GB            
Hit http://gb.archive.ubuntu.com natty/universe Translation-en_GB              
Ign http://security.ubuntu.com natty-security/main Translation-en_GB           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://archive.canonical.com natty/partner Translation-en_GB               
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_GB     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_GB     
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Ign http://security.ubuntu.com natty-security/universe Translation-en_GB       
Ign http://archive.canonical.com natty/partner Translation-en                  
Err http://ppa.launchpad.net natty/main Sources                                
  404  Not Found
Err http://ppa.launchpad.net natty/main amd64 Packages                         
  404  Not Found
Ign http://extras.ubuntu.com natty/main Translation-en_GB                      
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Ign http://extras.ubuntu.com natty/main Translation-en               
Ign http://ppa.launchpad.net natty/main Translation-en_GB            
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_GB
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://gb.archive.ubuntu.com natty/main Translation-en
Ign http://gb.archive.ubuntu.com natty/multiverse Translation-en
Ign http://gb.archive.ubuntu.com natty/restricted Translation-en
Ign http://gb.archive.ubuntu.com natty/universe Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-updates/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_GB
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_GB
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/restricted Translation-en_GB
Ign http://ppa.launchpad.net natty/main Translation-en_GB
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-updates/universe Translation-en
W: Failed to fetch http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Here's the theme I'm trying to install: [http://danrabbit.deviantart.com/art/elementary-gtk-theme-83104033?q=gallery%3Adanrabbit%2F3751876&qo=2](http://danrabbit.deviantart.com/art/elementary-gtk-theme-83104033?q=gallery%3Adanrabbit%2F3751876&qo=2)

[http://danrabbit.deviantart.com/gallery/3751876#/d1y30vn](http://danrabbit.deviantart.com/gallery/3751876#/d1y30vn)

The files didn't actually come with any 'tar.gz' files in them, could someone also give me a hand installing?

Thanks in advance,


Adam :)

---

### Post by jtarin on 2011-08-04
Edit your sources list and change ```
 http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/natty/main/binary-amd64/
```
to
```
http://ppa.launchpad.net/elementaryart/unstable-upstream/ubuntu/dists/natty/main/binary-amd64/
```
then run 
```
sudo apt-get update
```it should be listed in Synaptic then ready to download.

---

### Post by adamhum3 on 2011-08-04
Whenever I open sources.list it comes up blank?

I'm typing sudo gedit etc/apt/sources.list

Comes up with a blank text editor...

**Nevermind. Missed the / before etc.**

However I can't actually find ```
http://ppa.launchpad.net/elementaryart/ubuntu/dists/natty/main/binary-amd64/
``` in the sources list.

---

### Post by jtarin on 2011-08-04
Use the Synaptics software manager. ```
gksudo synaptics
```
In the menu you will find a listing for repositories. Remove the old one insert the new.

---

### Post by adamhum3 on 2011-08-04
I can't see anything in there that's the same as that one. There are some similar, however I'm not sure which one to remove, and even when I go to add a new one, add source is greyed out?

---

### Post by jtarin on 2011-08-04
> **adamhum3 said:**
> I can't see anything in there that's the same as that one. There are some similar, however I'm not sure which one to remove, and even when I go to add a new one, add source is greyed out?Remove all the ones marked elementary and then in a terminal issue the command ```
sudo add-apt-repository ppa:elementaryart/elementarydesktop
```Your system will now fetch the PPA's key. This enables your Ubuntu system to verify that the packages in the PPA have not been interfered with since they were built. 

Now, as a one-off, you should tell your system to pull down the latest list of software from each archive it knows about, including the PPA you just added:

```
sudo apt-get update
```

Now you're ready to start installing software from the PPA! Use Synaptic. Be warned that all packages might not be available for your version 11.04, as it's the newest version and not all developers have submitted updated packages to the ppa.

---

### Post by adamhum3 on 2011-08-04
Fantastic! Thanks a lot for the help jtarin :D

---

### Post by jtarin on 2011-08-04
> **adamhum3 said:**
> Fantastic! Thanks a lot for the help jtarin :D
Great!!! 
Now if you would mark the thread as solved using the "thread tools" at the top of the page. It will help others when they search for this problem.

---

