---
title: "[SOLVED] Could not download all repository indexes"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by MooseMagnet on 2008-12-19
Ubuntu Feisty. Dell Laptop.

Tried to install via Add/Remove and also via Synaptic this morning, but get this message.

"Could not download all the repository indexes."

I've un-commented most everything in the sources.list file, but still no go.

Changed mirror, and then back, but no go.

---

### Post by Titan8990 on 2008-12-19
What happens if you do:


sudo apt-get update

---

### Post by donkyhotay on 2008-12-19
This problem is usually caused by a connection problem between you and the servers. Sometimes if you just try it again it works, otherwise change the servers you connect to.

---

### Post by MooseMagnet on 2008-12-19
I tried a couple of different servers. Same thing.

Here's the long result from sudo apt-get update

rich@rich-laptop:~$ sudo apt-get update
(lots of '404 file not found')


Password:
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [189B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages              
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [189B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [189B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Get:4 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [189B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [189B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US           
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                      
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources                         
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages                  
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages            
  404 Not Found [IP: 91.189.88.31 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US       
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge Release.gpg                                    
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge/main Translation-en_US                         
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages              
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages            
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources                   
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources             
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources               
  404 Not Found [IP: 91.189.88.31 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                          
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge/main Translation-en_US                         
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge Release                                        
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources             
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                      
  404 Not Found [IP: 91.189.88.31 80]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources                          
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge/main Packages                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
  404 Not Found
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge/main Packages                                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages             
Err [http://ftp.debian.org](http://ftp.debian.org) sarge/main Packages                                  
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages              
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                  
  404 Not Found
Err [http://ftp.debian.org](http://ftp.debian.org) sarge/main Packages                                  
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                         
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                              
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources                        
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                        
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Sources    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Sources
Fetched 6B in 3s (2B/s)                                  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ftp.debian.org/dists/sarge/main/binary-i386/Packages.gz](http://ftp.debian.org/dists/sarge/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.debian.org/dists/sarge/main/binary-i386/Packages.gz](http://ftp.debian.org/dists/sarge/main/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
rich@rich-laptop:~$

---

### Post by Titan8990 on 2008-12-19
You have repositories enabled for multiple versions of Ubuntu. This can cause some major problems. Disable all repositories that are not for your current version.

---

### Post by taurus on 2008-12-19
And if you are running feisty, keep in mind that it has expired so the repos probably have been moved.

---

### Post by MooseMagnet on 2008-12-19
I commented out everything BUT feisty, and saved the file.
But get the same results with sudo apt-get update

no change...

---

### Post by MooseMagnet on 2008-12-19
When I use System > Admin > Software Sources, I get this.

"Information About Available Software Is Out Of Date"

--then--

"Could not download all repository indexes"

--then this list--

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]

---

### Post by MooseMagnet on 2008-12-19
Oops. I didn't see that message about Feisty.

What shall I do? I don't want to go to Gutsy for fear of problems.

---

### Post by Michael.Godawski on 2008-12-19
Make a backup of your data and switch to Intrepid Ibex 8.10.

Radical but will solve your issue.

---

### Post by Titan8990 on 2008-12-19
Personally, I would go straight to Hardy, as it has been one of the more stable releases for Ubuntu.

I would also do it from a fresh install.

Backup your data and reformat.

---

### Post by ajgreeny on 2008-12-19
I agree with Titan8990 as Hardy is a LTS version and will have support on the desktop until 2011, and server till 2013.  It is the best version for me so far with few if any problems, though I can't yet speak for 8.10, as I've only just started looking at it.  LTS is worth a lot, though.

---

### Post by MooseMagnet on 2008-12-19
OK. I'll go to Hardy, then report back here.
Thanks.

---

### Post by Titan8990 on 2008-12-19
Good Luck!

---

### Post by theozzlives on 2008-12-19
> **MooseMagnet said:**
> Oops. I didn't see that message about Feisty.

What shall I do? I don't want to go to Gutsy for fear of problems.

I started with Gutzy, ain't nothin wrong with it, I just don't think you can still get it. You got a choice BTW 8.04 LTS, or Intrepid.

---

### Post by MooseMagnet on 2008-12-19
Hardy is terrible. Wacks out my touchpad, flat screen, and sound. Very frustrating that it's so difficult to set up ubuntu on a laptop, and that after several years, it is still very difficult. No progress from developers. I tried the latest, greatest also, but it doesn't work with this laptop either - the one with the logo that looks like a coffee stain.

I'm going back to 7.04 and starting over. It will take me tomorrow and probably part of Sunday to get it back to where it was. I backed up the data, but it's all the labor in configuration that is frustrating.

Very bummed out right now, and not happy with ubuntu at the moment.

Thanks for the help and suggestions.

---

### Post by abn91c on 2008-12-19
> **MooseMagnet said:**
> OK. I'll go to Hardy, then report back here.
Thanks.

before reinstalling use a wired connection with the laptop and try sudo apt-get update again

---

### Post by MooseMagnet on 2008-12-20
A bit too late for that.

Trying to install Hardy thoroughly messed up this laptop.

---

### Post by MooseMagnet on 2008-12-20
Especially the touchpad. 

Very frustrating.

---

### Post by k3lt01 on 2008-12-20
If you have a problem with the Hardy setup why don't you start a new thread asking for help with the current Hardy issues? 

Going back to Feisty isn't a solution because it has gone past End-Of-Life status, and you are fearful of Gutsy which isn't going to be supported for much longer anyway.

You could also check out the [Dell section]("http://ubuntuforums.org/forumdisplay.php?f=342") in this forum.

---

### Post by MooseMagnet on 2008-12-20
Allow me one more question.
I backed up what I need, and restored it.
/etc
/usr
/var
/rich

But the Firefox bookmarks are not here.

I've remembered all I need to do to restore the device functions on this laptop after installing a new distro.

But... Can you tell me where are my bookmarks? I must have restored that portion incorrectly.

Thanks

---

### Post by MooseMagnet on 2008-12-20
After briefly reading the Dell -> Hardy posts. The same problems exist as 2 years ago. Problems with mic, etc.

Obviously, no progress whatsoever from Ubuntu in solving these long-standing problems.

Disappointing.

Though not supported, Feisty is much more reliable at this time. I will do all I can to restore it, and use it.

Still can't get those dang bookmarks back. Hmmm.

---

### Post by theozzlives on 2008-12-20
> **MooseMagnet said:**
> After briefly reading the Dell -> Hardy posts. The same problems exist as 2 years ago. Problems with mic, etc.

Obviously, no progress whatsoever from Ubuntu in solving these long-standing problems.

Disappointing.

Though not supported, Feisty is much more reliable at this time. I will do all I can to restore it, and use it.

Still can't get those dang bookmarks back. Hmmm.

I never had much luck with Hardy, Intrepid works great with my Dell laptop.

---

### Post by MooseMagnet on 2008-12-20
OK. I'll go to Intrepid.

Can anyone tell me how to restore my bookmarks. I really do need help with these. I really need them.

Thank you

---

### Post by abn91c on 2008-12-20
> **MooseMagnet said:**
> OK. I'll go to Intrepid.

Can anyone tell me how to restore my bookmarks. I really do need help with these. I really need them.

Thank you
go into the firefox folders and look for a file named [COLOR="RoyalBlue"]**bookmarks.html**[/COLOR], copy that to as usb drive or something then import that to your new firefox

---

### Post by k3lt01 on 2008-12-20
> **abn91c said:**
> go into the firefox folders and look for a file named [COLOR="RoyalBlue"]**bookmarks.html**[/COLOR], copy that to as usb drive or something then import that to your new firefox You cannot import bookmarks.html into FF3.

Did you backup your /home folder? if you did your Bookmarks will be in a hidden folder in there, if not I am sorry to tell you your probably screwed.

Regarding the Dell section and your disappointment. Did you bother to start a new post? Did you ask any questions there? Just because something doesn't look to be fixed doesn't mean it isn't fixed. You really need to do a bit more footwork (in other words ask the appropriate questions in the appropriate places at the appropriate times) yourself.

---

### Post by MooseMagnet on 2008-12-20
No, I'm not screwed, the bookmarks work fine.
I have done the footwork. Everything I typed is accurate.
Same problems again and again. More people every day wrestling with the same problems.

---

### Post by ajgreeny on 2008-12-20
However, for future reference the FF3 bookmarks are now in a file called ~/.mozilla/firefox/**kdjhv**.default/places.sqlite.  The bookmarks.html file is now obsolete, and though you can use it as a manual import source for the bookmarks, the file is no longer updated as you change your bookmarks.

PS The **kdjhv** in bold above will be a different alphanumeric for your setup.

---

### Post by k3lt01 on 2008-12-20
> **MooseMagnet said:**
> No, I'm not screwed, the bookmarks work fine.Last time you posted you didn't have them.
> **MooseMagnet said:**
> I have done the footwork. Everything I typed is accurate.I haven't said its not accurate, what I am saying is that from what you have posted you haven't done anything to help yourself. I'm just trying to give you a few pointers and you talk about disappointment and fear of Gutsy
> **MooseMagnet said:**
> Same problems again and again. More people every day wrestling with the same problems.What problems? You haven't really said what your having trouble with. Apart from Bookmarks in FF3 and now the Microphone I haven't seen you actually mention anything concrete about problems with Hardy. Give us a numbered list and maybe we can work through it with you.

As for footwork I'm not sure that's entirely accurate either. You didn't know Feisty was no longer supported, your /etc/apt/sources.list file has references to Edgy as well as Feisty (and even Sarge from Debian) in it so in all likelyhood your system wasn't set up optimally anyway because of compatibility issues.

If you want to keep Feisty you should get rid of the Edgy and Sarge references. [Feisty is now kept here]("http://old-releases.ubuntu.com/") so you can update your /etc/apt/sources.lists to point to this repository.

---

### Post by MooseMagnet on 2009-01-30
Nobody wants to hear this, but Intrepid is terrible. I've used Dapper, Edgy, Feisty, and Intrepid. Feisty was fantastic, and I miss it so much. Intrepid is awful.

I've had to adjust the touchpad with all the versions of Ubuntu, and I know how to adjust it. The touchpad currently is set to  max sensitivity. When I tap inside a text box, it takes up to 65 seconds for the tap to register. I had been tapping several times, frustrated. But since discovered that one tap is enough, the problem is that something is causing this laptop to run so very slowly. Why so slow with Intrepid?

When typing, the cursor jumps around in the text box. I've adjusted the touchpad every way possible, but it still does it.

With Firefox, the screen turns gray and goes to sleep while it's loading a page. Why so slow with Intrepid?

With Totem, the screen turns gray and goes to sleep while loading the application. Why so slow with Intrepid?

Not a happy camper.

Dell Inspiron 1300 Laptop

---

### Post by k3lt01 on 2009-01-30
Start a new thread on these issues, or better still do a search and read around. You have already marked this as solved and you have to many new questions that don't relate at all to the original problem.

---

### Post by MooseMagnet on 2009-01-30
That's typical - unfortunately. Criticize the way I ask the question rather than attempting to solve any problems. I HAVE posted these problems elsewhere. But they are ignored there also.

---

### Post by k3lt01 on 2009-01-30
I do have a few tips for you but haven't seen the new thread/s. When I see them I will post there.

What is typical is your attitude, you have criticized the Ubuntu OS and when someone says to do something you take it to heart.

---

### Post by Revenged on 2009-01-30
> **k3lt01 said:**
> What is typical is your attitude, you have criticized the Ubuntu OS and when someone says to do something you take it to heart.

x2.

Chill man.

---

