---
title: "Unable to update"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-08-02
Hi Folks,

I'm running 11.04 and starting about two days ago I noticed that the update manager always says it was updated one hour ago.

Just now I tried sudo apt-get install update and got this:

```


sudo apt-get install update
[sudo] password for grouchygaijin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Unable to locate package update**

```

Any idea on how I can fix this?

---

### Post by 3rdalbum on 2011-08-02
```
sudo apt-get update
```

You need to install the updates to get the displayed time to change. It's a bug.

---

### Post by GrouchyGaijin on 2011-08-02
> **3rdalbum said:**
> ```
sudo apt-get update
```

You need to install the updates to get the displayed time to change. It's a bug.
Thanks

When I run 

```
 sudo apt-get update
```

I now get

```

$ sudo apt-get update
[sudo] password for grouchygaijin: 
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://dl.google.com stable Release [1,347 B]                            
Ign http://ftp.sunet.se natty InRelease                                        
Ign http://ftp.sunet.se natty-updates InRelease                                
Ign http://ftp.sunet.se natty-security InRelease                               
Hit http://ftp.sunet.se natty Release.gpg                                      
Hit http://ftp.sunet.se natty-updates Release.gpg                              
Hit http://ftp.sunet.se natty-security Release.gpg                             
Hit http://ftp.sunet.se natty Release                                          
Hit http://ftp.sunet.se natty-updates Release                                  
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://archive.canonical.com natty InRelease                               
Hit http://ftp.sunet.se natty-security Release                                 
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://packages.medibuntu.org natty InRelease                              
Get:3 http://dl.google.com stable/main i386 Packages [767 B]                   
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://extras.ubuntu.com natty Release.gpg                                 
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ftp.sunet.se natty/main Sources                                     
Hit http://ftp.sunet.se natty/restricted Sources                               
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ftp.sunet.se natty/universe Sources                                 
Hit http://archive.canonical.com natty Release                                 
Hit http://extras.ubuntu.com natty Release                                     
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ftp.sunet.se natty/multiverse Sources                               
Hit http://ftp.sunet.se natty/main i386 Packages                               
Hit http://ftp.sunet.se natty/restricted i386 Packages                         
Hit http://ftp.sunet.se natty/universe i386 Packages                           
Hit http://ftp.sunet.se natty/multiverse i386 Packages                         
Ign http://ftp.sunet.se natty/main TranslationIndex                            
Ign http://ftp.sunet.se natty/multiverse TranslationIndex                      
Ign http://ftp.sunet.se natty/restricted TranslationIndex                      
Ign http://ftp.sunet.se natty/universe TranslationIndex                        
Hit http://ftp.sunet.se natty-updates/main Sources                             
Hit http://ftp.sunet.se natty-updates/restricted Sources                       
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ftp.sunet.se natty-updates/universe Sources                         
Hit http://ftp.sunet.se natty-updates/multiverse Sources                       
Hit http://ftp.sunet.se natty-updates/main i386 Packages                       
Hit http://ftp.sunet.se natty-updates/restricted i386 Packages                 
Hit http://ftp.sunet.se natty-updates/universe i386 Packages                   
Hit http://ftp.sunet.se natty-updates/multiverse i386 Packages                 
Ign http://ftp.sunet.se natty-updates/main TranslationIndex                    
Ign http://ftp.sunet.se natty-updates/multiverse TranslationIndex              
Ign http://ftp.sunet.se natty-updates/restricted TranslationIndex              
Ign http://ftp.sunet.se natty-updates/universe TranslationIndex                
Hit http://ftp.sunet.se natty-security/main Sources                            
Hit http://ftp.sunet.se natty-security/restricted Sources                      
Hit http://ftp.sunet.se natty-security/universe Sources                        
Hit http://ftp.sunet.se natty-security/multiverse Sources                      
Hit http://ftp.sunet.se natty-security/main i386 Packages                      
Hit http://ftp.sunet.se natty-security/restricted i386 Packages                
Hit http://archive.canonical.com natty/partner i386 Packages                   
Hit http://ftp.sunet.se natty-security/universe i386 Packages                  
Hit http://ftp.sunet.se natty-security/multiverse i386 Packages                
Ign http://ftp.sunet.se natty-security/main TranslationIndex                   
Ign http://ftp.sunet.se natty-security/multiverse TranslationIndex             
Ign http://ftp.sunet.se natty-security/restricted TranslationIndex             
Ign http://ftp.sunet.se natty-security/universe TranslationIndex               
Hit http://packages.medibuntu.org natty/free i386 Packages                     
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://packages.medibuntu.org natty/non-free i386 Packages                 
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Ign http://www.geekconnection.org karmic/ InRelease                            
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://ftp.sunet.se natty/main Translation-en_US                           
Ign http://ftp.sunet.se natty/main Translation-en                              
Ign http://ftp.sunet.se natty/multiverse Translation-en_US                     
Ign http://ftp.sunet.se natty/multiverse Translation-en                        
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://ftp.sunet.se natty/restricted Translation-en_US                     
Ign http://ftp.sunet.se natty/restricted Translation-en                        
Ign http://ftp.sunet.se natty/universe Translation-en_US                       
Ign http://ftp.sunet.se natty/universe Translation-en                          
Ign http://packages.medibuntu.org natty/free TranslationIndex                  
Ign http://ftp.sunet.se natty-updates/main Translation-en_US                   
Ign http://ftp.sunet.se natty-updates/main Translation-en                      
Ign http://ftp.sunet.se natty-updates/multiverse Translation-en_US             
Ign http://ftp.sunet.se natty-updates/multiverse Translation-en                
Ign http://dl.google.com stable/main Translation-en                            
Ign http://ftp.sunet.se natty-updates/restricted Translation-en_US             
Ign http://ftp.sunet.se natty-updates/restricted Translation-en                
Ign http://ftp.sunet.se natty-updates/universe Translation-en_US               
Ign http://ftp.sunet.se natty-updates/universe Translation-en                  
Ign http://ftp.sunet.se natty-security/main Translation-en_US                  
Ign http://ftp.sunet.se natty-security/main Translation-en                     
Ign http://ftp.sunet.se natty-security/multiverse Translation-en_US            
Ign http://ftp.sunet.se natty-security/multiverse Translation-en               
Ign http://ftp.sunet.se natty-security/restricted Translation-en_US            
Ign http://ftp.sunet.se natty-security/restricted Translation-en               
Ign http://ftp.sunet.se natty-security/universe Translation-en_US              
Ign http://ftp.sunet.se natty-security/universe Translation-en                 
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Ign http://www.geekconnection.org karmic/ Release.gpg                          
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign https://private-ppa.launchpad.net natty InRelease                          
Ign http://www.geekconnection.org karmic/ Release                              
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://www.geekconnection.org karmic/ Packages/DiffIndex                   
Ign http://linux.dropbox.com natty InRelease                                   
Hit https://private-ppa.launchpad.net natty Release.gpg                        
Hit https://private-ppa.launchpad.net natty Release                  
Hit http://linux.dropbox.com natty Release.gpg                                 
Hit https://private-ppa.launchpad.net natty/main i386 Packages                 
Ign https://private-ppa.launchpad.net natty/main TranslationIndex              
Hit http://linux.dropbox.com natty Release                                     
Hit http://linux.dropbox.com natty/main i386 Packages                          
Ign http://linux.dropbox.com natty/main TranslationIndex                       
Ign http://packages.medibuntu.org natty/free Translation-en_US                 
Ign http://packages.medibuntu.org natty/free Translation-en                    
Ign http://packages.medibuntu.org natty/non-free Translation-en_US             
Hit http://www.geekconnection.org karmic/ Packages                             
Ign http://packages.medibuntu.org natty/non-free Translation-en                
Ign http://www.geekconnection.org karmic/ Translation-en_US          
Ign http://www.geekconnection.org karmic/ Translation-en
Ign http://linux.dropbox.com natty/main Translation-en_US
Ign http://linux.dropbox.com natty/main Translation-en
Ign https://private-ppa.launchpad.net natty/main Translation-en_US
Ign https://private-ppa.launchpad.net natty/main Translation-en
Fetched 2,312 B in 6s (380 B/s)                                                
Reading package lists... Done

```

What are all the IGNs for?
Does this mean that my system is actually up to date?
Why would the update manager consistently show that the last update check was an hour ago even though it has been more than one hour since I checked.  It's been like this for at least two days.

---

### Post by plucky on 2011-08-02
> What are all the IGNs for?

It just means there are no updates for those packages.

> Does this mean that my system is actually up to date?

No,all you have done is download the package list files.You need to run ```
sudo apt-get upgrade
``` to install the new packages.


> Hit [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages

That means there is a **Karmic** repository in your Software Sources,which is not a good idea to mix repositories between different versions.You can use the Software Sources Gui to disable it.

Good Luck

---

### Post by vkbidve on 2011-08-02
When you start your synaptic update manager, let it check for the updates and let it say that its all updated. Then click on the 'Check' button and provide your password. Now it will actually 'check' for updates and will show you the list if there are really any.

---

### Post by GrouchyGaijin on 2011-08-02
Thanks Guys,

I just checked the update manager and it said that I had last checked 3 hours ago.  So it looks like that is working again.

I did the update then upgrade from the terminal and it looks like there are no updates.

I also removed the Karmac repository from the list.

---

### Post by JYx70 on 2011-08-02
Hi guys,
I've been having the same problem for a couple of days now... can't get update manager to get past "check for updates", it just returns: failed to download repository information... check internet connection.
I don't have a problem with my internet connection.
I did do the apt-get update/upgrade which returned 0 updates and 0 upgrades.
So, how do I repair the update manager? Backup and reinstall?

---

### Post by GrouchyGaijin on 2011-08-02
> **JYx70 said:**
> Hi guys,
I've been having the same problem for a couple of days now... can't get update manager to get past "check for updates", it just returns: failed to download repository information... check internet connection.
I don't have a problem with my internet connection.
I did do the apt-get update/upgrade which returned 0 updates and 0 upgrades.
So, how do I repair the update manager? Backup and reinstall?

WOW I thought it was just me.

---

