---
title: "problems updating....."
date: 2011-03-19
forum: New to Ubuntu
---

### Post by shaun6mc on 2011-03-19
[HTML]
shaun@shaun-bobdole007:~$ sudo apt-get update
[sudo] password for shaun: 
Get:1 http://us.archive.ubuntu.com maverick Release.gpg [198B]                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-security Release.gpg             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                          
Hit http://us.archive.ubuntu.com maverick-updates Release                  
Hit http://us.archive.ubuntu.com maverick-security Release                 
Hit http://us.archive.ubuntu.com maverick/main Sources                         
Hit http://us.archive.ubuntu.com maverick/restricted Sources                   
Hit http://us.archive.ubuntu.com maverick/multiverse Sources               
Hit http://us.archive.ubuntu.com maverick/universe Sources                 
Hit http://us.archive.ubuntu.com maverick/main amd64 Packages                  
Hit http://us.archive.ubuntu.com maverick/restricted amd64 Packages            
Hit http://us.archive.ubuntu.com maverick/universe amd64 Packages              
Hit http://us.archive.ubuntu.com maverick/multiverse amd64 Packages            
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources           
Hit http://us.archive.ubuntu.com maverick-updates/main Sources                 
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources           
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://us.archive.ubuntu.com maverick-updates/main amd64 Packages      
Hit http://us.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe amd64 Packages  
Hit http://us.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com maverick-security/restricted Sources      
Hit http://us.archive.ubuntu.com maverick-security/main Sources            
Hit http://us.archive.ubuntu.com maverick-security/multiverse Sources      
Hit http://us.archive.ubuntu.com maverick-security/universe Sources            
Hit http://us.archive.ubuntu.com maverick-security/main amd64 Packages         
Hit http://us.archive.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com maverick-security/universe amd64 Packages     
Hit http://us.archive.ubuntu.com maverick-security/multiverse amd64 Packages   
Err http://extras.ubuntu.com maverick Release.gpg                          
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://extras.ubuntu.com maverick/main Sources/DiffIndex                   
Ign http://extras.ubuntu.com maverick/main amd64 Packages/DiffIndex            
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://extras.ubuntu.com maverick/main amd64 Packages                      
Err http://archive.canonical.com maverick Release.gpg                          
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US
Hit http://archive.canonical.com maverick Release
Ign http://archive.canonical.com maverick/partner Sources/DiffIndex
Ign http://archive.canonical.com maverick/partner amd64 Packages/DiffIndex
Hit http://archive.canonical.com maverick/partner Sources
Hit http://archive.canonical.com maverick/partner amd64 Packages
Fetched 198B in 16s (12B/s)
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
[/HTML]

This is the output of sudo apt-get update.

[LIST]
[*]ubuntu 10.10
[*]server for United States
[*]most boxes checked in Software Sources
[/LIST]

I didn't start having issues until I tried to remove wine1.2.2 and reinstall :/

---

### Post by shaun6mc on 2011-03-19
[HTML]
shaun@shaun-bobdole007:~$ sudo apt-get update
[sudo] password for shaun: 
Get:1 http://us.archive.ubuntu.com maverick Release.gpg [198B]                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-security Release.gpg             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                          
Hit http://us.archive.ubuntu.com maverick-updates Release                  
Hit http://us.archive.ubuntu.com maverick-security Release                 
Hit http://us.archive.ubuntu.com maverick/main Sources                         
Hit http://us.archive.ubuntu.com maverick/restricted Sources                   
Hit http://us.archive.ubuntu.com maverick/multiverse Sources               
Hit http://us.archive.ubuntu.com maverick/universe Sources                 
Hit http://us.archive.ubuntu.com maverick/main amd64 Packages                  
Hit http://us.archive.ubuntu.com maverick/restricted amd64 Packages            
Hit http://us.archive.ubuntu.com maverick/universe amd64 Packages              
Hit http://us.archive.ubuntu.com maverick/multiverse amd64 Packages            
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources           
Hit http://us.archive.ubuntu.com maverick-updates/main Sources                 
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources           
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://us.archive.ubuntu.com maverick-updates/main amd64 Packages      
Hit http://us.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe amd64 Packages  
Hit http://us.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com maverick-security/restricted Sources      
Hit http://us.archive.ubuntu.com maverick-security/main Sources            
Hit http://us.archive.ubuntu.com maverick-security/multiverse Sources      
Hit http://us.archive.ubuntu.com maverick-security/universe Sources            
Hit http://us.archive.ubuntu.com maverick-security/main amd64 Packages         
Hit http://us.archive.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com maverick-security/universe amd64 Packages     
Hit http://us.archive.ubuntu.com maverick-security/multiverse amd64 Packages   
Err http://extras.ubuntu.com maverick Release.gpg                          
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://extras.ubuntu.com maverick/main Sources/DiffIndex                   
Ign http://extras.ubuntu.com maverick/main amd64 Packages/DiffIndex            
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://extras.ubuntu.com maverick/main amd64 Packages                      
Err http://archive.canonical.com maverick Release.gpg                          
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US
Hit http://archive.canonical.com maverick Release
Ign http://archive.canonical.com maverick/partner Sources/DiffIndex
Ign http://archive.canonical.com maverick/partner amd64 Packages/DiffIndex
Hit http://archive.canonical.com maverick/partner Sources
Hit http://archive.canonical.com maverick/partner amd64 Packages
Fetched 198B in 16s (12B/s)
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
[/HTML]

This is the output of sudo apt-get update.

[LIST]
[*]ubuntu 10.10
[*]server for United States
[*]most boxes checked in Software Sources
[/LIST]

I didn't start having issues until I tried to remove wine1.2.2 and reinstall   :/

---

### Post by howefield on 2011-03-19
Thread merged.

---

