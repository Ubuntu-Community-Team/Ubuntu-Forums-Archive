---
title: "checking for updates: Ign... and Hit..."
date: 2011-05-09
forum: New to Ubuntu
---

### Post by werty2010 on 2011-05-09
is there something wrong here?
what is Ing and Hit and why are there?

i ran "sudo apt-get update" and it gave me:

```
Ign http://archive.canonical.com natty InRelease
Ign http://extras.ubuntu.com natty InRelease                        
Ign http://archive.ubuntu.com natty InRelease                        
Ign http://archive.ubuntu.com natty-updates InRelease                
Ign http://archive.ubuntu.com natty-security InRelease               
Hit http://archive.canonical.com natty Release.gpg                   
Hit http://extras.ubuntu.com natty Release.gpg                       
Ign http://dl.google.com stable InRelease                            
Hit http://archive.ubuntu.com natty Release.gpg                      
Hit http://archive.canonical.com natty Release                       
Hit http://extras.ubuntu.com natty Release     
Hit http://archive.ubuntu.com natty-updates Release.gpg               
Hit http://archive.canonical.com natty/partner amd64 Packages        
Hit http://extras.ubuntu.com natty/main Sources                      
Hit http://archive.ubuntu.com natty-security Release.gpg             
Get:1 http://dl.google.com stable Release.gpg [197 B]                
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://extras.ubuntu.com natty/main amd64 Packages               
Ign http://extras.ubuntu.com natty/main TranslationIndex             
Hit http://archive.ubuntu.com natty Release                          
Get:2 http://dl.google.com stable Release [1,338 B]                            
Hit http://archive.ubuntu.com natty-updates Release                            
Hit http://archive.ubuntu.com natty-security Release                           
Hit http://archive.ubuntu.com natty/main Sources                               
Hit http://archive.ubuntu.com natty/restricted Sources                         
Hit http://archive.ubuntu.com natty/universe Sources                 
Hit http://archive.ubuntu.com natty/multiverse Sources                         
Hit http://archive.ubuntu.com natty/main amd64 Packages                        
Get:3 http://dl.google.com stable/main amd64 Packages [471 B]        
Hit http://archive.ubuntu.com natty/restricted amd64 Packages                  
Hit http://archive.ubuntu.com natty/universe amd64 Packages                    
Hit http://archive.ubuntu.com natty/multiverse amd64 Packages        
Ign http://archive.ubuntu.com natty/main TranslationIndex            
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex                
Ign http://archive.ubuntu.com natty/restricted TranslationIndex      
Ign http://archive.ubuntu.com natty/universe TranslationIndex        
Hit http://archive.ubuntu.com natty-updates/main Sources             
Hit http://archive.ubuntu.com natty-updates/restricted Sources       
Hit http://archive.ubuntu.com natty-updates/universe Sources         
Hit http://archive.ubuntu.com natty-updates/multiverse Sources       
Hit http://archive.ubuntu.com natty-updates/main amd64 Packages      
Hit http://archive.ubuntu.com natty-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com natty-updates/universe amd64 Packages  
Hit http://archive.ubuntu.com natty-updates/multiverse amd64 Packages
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex    
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex          
Hit http://archive.ubuntu.com natty-security/main Sources            
Hit http://archive.ubuntu.com natty-security/restricted Sources      
Hit http://archive.ubuntu.com natty-security/universe Sources        
Hit http://archive.ubuntu.com natty-security/multiverse Sources      
Hit http://archive.ubuntu.com natty-security/main amd64 Packages     
Hit http://archive.ubuntu.com natty-security/restricted amd64 Packages
Hit http://archive.ubuntu.com natty-security/universe amd64 Packages 
Hit http://archive.ubuntu.com natty-security/multiverse amd64 Packages
Ign http://archive.ubuntu.com natty-security/main TranslationIndex   
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://archive.canonical.com natty/partner Translation-en_US     
Ign http://extras.ubuntu.com natty/main Translation-en_US            
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex
Ign http://archive.canonical.com natty/partner Translation-en        
Ign http://extras.ubuntu.com natty/main Translation-en               
Ign http://archive.ubuntu.com natty/main Translation-en_US           
Ign http://archive.ubuntu.com natty/main Translation-en
Ign http://archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty/multiverse Translation-en
Ign http://archive.ubuntu.com natty/restricted Translation-en_US
Ign http://archive.ubuntu.com natty/restricted Translation-en
Ign http://archive.ubuntu.com natty/universe Translation-en_US
Ign http://archive.ubuntu.com natty/universe Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://archive.ubuntu.com natty-updates/main Translation-en
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com natty-updates/universe Translation-en
Ign http://archive.ubuntu.com natty-security/main Translation-en_US
Ign http://archive.ubuntu.com natty-security/main Translation-en
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-security/restricted Translation-en
Ign http://archive.ubuntu.com natty-security/universe Translation-en_US
Ign http://archive.ubuntu.com natty-security/universe Translation-en
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Fetched 2,006 B in 8s (237 B/s)                                                
Reading package lists... Done

```

is there something wrong here?
what is Ing and Hit and why are there?

---

### Post by compmodder26 on 2011-05-09
No need to worry.  The way the the update command works is it will check each repository for updated packages.  When there are no changes to the repository it will say Ign, meaning it will ignore that repository and not download an updated package list.  When there are updated packages in a repository, it will say Hit, meaning that it has found updated packages and will update the package list for the repository.

---

### Post by werty2010 on 2011-05-09
thank you for your good and quick response

---

