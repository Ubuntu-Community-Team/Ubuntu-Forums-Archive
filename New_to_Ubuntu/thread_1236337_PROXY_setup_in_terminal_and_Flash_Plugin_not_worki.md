---
title: "PROXY setup in terminal and Flash Plugin not working"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by humphreybc on 2009-08-10
SOLVED: See last post

I'm getting pretty tired of this stuff. So I'm a uni student and I do all my internet updating etc at our university library, where a proxy needs to be configured. 

I have it configured under System > Network Proxy, and have clicked apply system wide. Why-oh-why does "apply system wide" NOT APPLY IT SYSTEM WIDE?!?!?!?!?!?!!

I also have it under Synaptic > Preferences > Network.

I also have a file /etc/apt/apt.conf with the following in it:

```

ACQUIRE { 
http::proxy "http://username:password@student.otago.ac.nz:3128/" 
}

```

I ALSO have it set up in Firefox.

These are the programs that work with the proxy:

Firefox
Synaptic Package Manager
Add/Remove Programs
Update Manager

This is the program that doesn't:

TERMINAL!!!!!

When I try sudo apt-get update in terminal I get the following:

```

Ign http://packages.medibuntu.org jaunty Release.gpg
Ign http://nz.archive.ubuntu.com jaunty Release.gpg                            
Ign http://archive.canonical.com jaunty Release.gpg                            
Ign http://packages.medibuntu.org jaunty/free Translation-en_NZ                
Ign http://nz.archive.ubuntu.com jaunty/main Translation-en_NZ                 
Ign http://archive.canonical.com jaunty/partner Translation-en_NZ              
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_NZ            
Ign http://nz.archive.ubuntu.com jaunty/restricted Translation-en_NZ           
Ign http://archive.canonical.com jaunty Release                                
Ign http://packages.medibuntu.org jaunty Release                               
Ign http://nz.archive.ubuntu.com jaunty/universe Translation-en_NZ             
Ign http://archive.canonical.com jaunty/partner Packages                       
Ign http://packages.medibuntu.org jaunty/free Packages                         
Ign http://nz.archive.ubuntu.com jaunty/multiverse Translation-en_NZ           
Ign http://archive.canonical.com jaunty/partner Packages                       
Ign http://packages.medibuntu.org jaunty/non-free Packages                     
Ign http://nz.archive.ubuntu.com jaunty-updates Release.gpg                    
Err http://archive.canonical.com jaunty/partner Packages                       
  407 Proxy Authentication Required
Ign http://packages.medibuntu.org jaunty/free Packages                         
Ign http://nz.archive.ubuntu.com jaunty-updates/main Translation-en_NZ         
Ign http://packages.medibuntu.org jaunty/non-free Packages                     
Ign http://nz.archive.ubuntu.com jaunty-updates/restricted Translation-en_NZ   
Err http://packages.medibuntu.org jaunty/free Packages                         
  407 Proxy Authentication Required
Ign http://nz.archive.ubuntu.com jaunty-updates/universe Translation-en_NZ     
Err http://packages.medibuntu.org jaunty/non-free Packages                     
  407 Proxy Authentication Required
Ign http://nz.archive.ubuntu.com jaunty-updates/multiverse Translation-en_NZ   
Ign http://nz.archive.ubuntu.com intrepid-backports Release.gpg
Ign http://nz.archive.ubuntu.com intrepid-backports/main Translation-en_NZ
Ign http://nz.archive.ubuntu.com intrepid-backports/restricted Translation-en_NZ
Ign http://nz.archive.ubuntu.com intrepid-backports/universe Translation-en_NZ
Ign http://nz.archive.ubuntu.com intrepid-backports/multiverse Translation-en_NZ
Ign http://nz.archive.ubuntu.com jaunty-security Release.gpg
Ign http://nz.archive.ubuntu.com jaunty-security/main Translation-en_NZ
Ign http://nz.archive.ubuntu.com jaunty-security/restricted Translation-en_NZ
Ign http://nz.archive.ubuntu.com jaunty-security/universe Translation-en_NZ
Ign http://nz.archive.ubuntu.com jaunty-security/multiverse Translation-en_NZ
Ign http://nz.archive.ubuntu.com jaunty-backports Release.gpg
Ign http://nz.archive.ubuntu.com jaunty-backports/restricted Translation-en_NZ
Ign http://nz.archive.ubuntu.com jaunty-backports/main Translation-en_NZ
Ign http://nz.archive.ubuntu.com jaunty-backports/multiverse Translation-en_NZ
Ign http://nz.archive.ubuntu.com jaunty-backports/universe Translation-en_NZ
Ign http://nz.archive.ubuntu.com jaunty Release
Ign http://nz.archive.ubuntu.com jaunty-updates Release
Ign http://nz.archive.ubuntu.com intrepid-backports Release
Ign http://nz.archive.ubuntu.com jaunty-security Release
Ign http://nz.archive.ubuntu.com jaunty-backports Release
Ign http://nz.archive.ubuntu.com jaunty/main Packages
Ign http://nz.archive.ubuntu.com jaunty/restricted Packages
Ign http://nz.archive.ubuntu.com jaunty/main Sources
Ign http://nz.archive.ubuntu.com jaunty/restricted Sources
Ign http://nz.archive.ubuntu.com jaunty/universe Packages
Ign http://nz.archive.ubuntu.com jaunty/universe Sources
Ign http://nz.archive.ubuntu.com jaunty/multiverse Packages
Ign http://nz.archive.ubuntu.com jaunty/multiverse Sources
Ign http://nz.archive.ubuntu.com jaunty-updates/main Packages
Ign http://nz.archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://nz.archive.ubuntu.com jaunty-updates/main Sources
Ign http://nz.archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://nz.archive.ubuntu.com jaunty-updates/universe Packages
Ign http://nz.archive.ubuntu.com jaunty-updates/universe Sources
Ign http://nz.archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://nz.archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://nz.archive.ubuntu.com intrepid-backports/main Packages
Ign http://nz.archive.ubuntu.com intrepid-backports/restricted Packages
Ign http://nz.archive.ubuntu.com intrepid-backports/universe Packages
Ign http://nz.archive.ubuntu.com intrepid-backports/multiverse Packages
Ign http://nz.archive.ubuntu.com jaunty-security/main Packages
Ign http://nz.archive.ubuntu.com jaunty-security/restricted Packages
Ign http://nz.archive.ubuntu.com jaunty-security/main Sources
Ign http://nz.archive.ubuntu.com jaunty-security/restricted Sources
Ign http://nz.archive.ubuntu.com jaunty-security/universe Packages
Ign http://nz.archive.ubuntu.com jaunty-security/universe Sources
Ign http://nz.archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://nz.archive.ubuntu.com jaunty-security/multiverse Sources
Ign http://nz.archive.ubuntu.com jaunty-backports/restricted Packages
Ign http://nz.archive.ubuntu.com jaunty-backports/main Packages
Ign http://nz.archive.ubuntu.com jaunty-backports/multiverse Packages
Ign http://nz.archive.ubuntu.com jaunty-backports/universe Packages
Ign http://nz.archive.ubuntu.com jaunty/main Packages        
Ign http://nz.archive.ubuntu.com jaunty/restricted Packages  
Ign http://nz.archive.ubuntu.com jaunty/main Sources         
Ign http://nz.archive.ubuntu.com jaunty/restricted Sources   
Ign http://nz.archive.ubuntu.com jaunty/universe Packages    
Ign http://nz.archive.ubuntu.com jaunty/universe Sources     
Ign http://nz.archive.ubuntu.com jaunty/multiverse Packages  
Ign http://nz.archive.ubuntu.com jaunty/multiverse Sources   
Ign http://nz.archive.ubuntu.com jaunty-updates/main Packages
Ign http://nz.archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://nz.archive.ubuntu.com jaunty-updates/main Sources 
Ign http://nz.archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://nz.archive.ubuntu.com jaunty-updates/universe Packages
Ign http://nz.archive.ubuntu.com jaunty-updates/universe Sources
Ign http://nz.archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://nz.archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://nz.archive.ubuntu.com intrepid-backports/main Packages
Ign http://nz.archive.ubuntu.com intrepid-backports/restricted Packages
Ign http://nz.archive.ubuntu.com intrepid-backports/universe Packages
Ign http://nz.archive.ubuntu.com intrepid-backports/multiverse Packages
Ign http://nz.archive.ubuntu.com jaunty-security/main Packages
Ign http://nz.archive.ubuntu.com jaunty-security/restricted Packages
Ign http://nz.archive.ubuntu.com jaunty-security/main Sources
Ign http://nz.archive.ubuntu.com jaunty-security/restricted Sources
Ign http://nz.archive.ubuntu.com jaunty-security/universe Packages
Ign http://nz.archive.ubuntu.com jaunty-security/universe Sources
Ign http://nz.archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://nz.archive.ubuntu.com jaunty-security/multiverse Sources
Ign http://nz.archive.ubuntu.com jaunty-backports/restricted Packages
Ign http://nz.archive.ubuntu.com jaunty-backports/main Packages
Ign http://nz.archive.ubuntu.com jaunty-backports/multiverse Packages
Ign http://nz.archive.ubuntu.com jaunty-backports/universe Packages
Err http://nz.archive.ubuntu.com jaunty/main Packages        
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty/restricted Packages  
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty/main Sources         
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty/restricted Sources   
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty/universe Packages    
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty/universe Sources     
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty/multiverse Packages  
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty/multiverse Sources   
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-updates/main Packages
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-updates/restricted Packages
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-updates/main Sources 
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-updates/restricted Sources
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-updates/universe Packages
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-updates/universe Sources
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-updates/multiverse Packages
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-updates/multiverse Sources
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com intrepid-backports/main Packages
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com intrepid-backports/restricted Packages
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com intrepid-backports/universe Packages
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com intrepid-backports/multiverse Packages
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-security/main Packages
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-security/restricted Packages
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-security/main Sources
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-security/restricted Sources
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-security/universe Packages
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-security/universe Sources
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-security/multiverse Packages
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-security/multiverse Sources
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-backports/restricted Packages
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-backports/main Packages
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-backports/multiverse Packages
  407 Proxy Authentication Required
Err http://nz.archive.ubuntu.com jaunty-backports/universe Packages
  407 Proxy Authentication Required
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty/partner/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://packages.medibuntu.org/dists/jaunty/free/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://packages.medibuntu.org/dists/jaunty/non-free/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-amd64/Packages  407 Proxy Authentication Required

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-amd64/Packages  407 Proxy Authentication Required

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Now, this is particularly annoying at the moment because I just did an update today and then went to YouTube, and, surprisingly it gave me a flash plugin error. So I go to download it off Adobe, the .deb package, and it tells me it's the wrong architecture... i386 and I am running AMD64. So I have a look on the internet and try to re-install flashplugin-installer, first using Synaptic which seems to go fine. Then using Terminal and I get an error. I tried to use Add/Remove Programs and check the "Adobe Flash Plugin 10" box but it says in the description: 

"Adobe Flash Plugin 10 cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.
Adobe Flash Plugin 10 is available in the third party software channel 'jaunty-partner'. To install it, please click on the checkbox to activate the software channel."

I think that Terminal is trying to install the adobe-flashplugin but it's not working due to my proxy dilemma.

HELP!!!

---

### Post by stumbleUpon on 2009-08-10
Edit your .bashrc file (located in your home directory) and add the following lines

http_proxy=http://username:password@student.otago.ac.nz:3128/
ftp_proxy=http://username:password@student.otago.ac.nz:3128/

In the same terminal do

source ~/.bashrc

then try using apt-get

---

### Post by humphreybc on 2009-08-12
Okay I've done that, and this is what I get:

```

benjamin@benjamin-laptop:~$ sudo apt-get update
Err http://nz.archive.ubuntu.com jaunty Release.gpg
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty/main Translation-en_NZ                 
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty/restricted Translation-en_NZ           
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty/universe Translation-en_NZ             
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty/multiverse Translation-en_NZ           
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty-updates Release.gpg                    
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty-updates/main Translation-en_NZ         
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty-updates/restricted Translation-en_NZ   
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty-updates/universe Translation-en_NZ     
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty-updates/multiverse Translation-en_NZ   
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com intrepid-backports Release.gpg                
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com intrepid-backports/main Translation-en_NZ     
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com intrepid-backports/restricted Translation-en_NZ
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com intrepid-backports/universe Translation-en_NZ 
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com intrepid-backports/multiverse Translation-en_NZ
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty-security Release.gpg                   
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty-security/main Translation-en_NZ        
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty-security/restricted Translation-en_NZ  
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty-security/universe Translation-en_NZ    
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty-security/multiverse Translation-en_NZ  
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty-backports Release.gpg                  
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty-backports/restricted Translation-en_NZ 
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty-backports/main Translation-en_NZ       
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty-backports/multiverse Translation-en_NZ 
  Could not resolve 'student.otago.ac.nz'
Err http://nz.archive.ubuntu.com jaunty-backports/universe Translation-en_NZ   
  Could not resolve 'student.otago.ac.nz'
Err http://archive.canonical.com jaunty Release.gpg                            
  Could not resolve 'student.otago.ac.nz'
Err http://archive.canonical.com jaunty/partner Translation-en_NZ              
  Could not resolve 'student.otago.ac.nz'
Err http://download.virtualbox.org jaunty Release.gpg                          
  Could not resolve 'student.otago.ac.nz'
Err http://download.virtualbox.org jaunty/non-free Translation-en_NZ           
  Could not resolve 'student.otago.ac.nz'
Err http://ppa.launchpad.net jaunty Release.gpg                                
  Could not resolve 'student.otago.ac.nz'
Err http://ppa.launchpad.net jaunty/main Translation-en_NZ                
  Could not resolve 'student.otago.ac.nz'
Err http://packages.medibuntu.org jaunty Release.gpg                      
  Could not resolve 'student.otago.ac.nz'
Err http://packages.medibuntu.org jaunty/free Translation-en_NZ           
  Could not resolve 'student.otago.ac.nz'
Err http://packages.medibuntu.org jaunty/non-free Translation-en_NZ       
  Could not resolve 'student.otago.ac.nz'
Reading package lists... Done                                             
W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-backports/Release.gpg  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release.gpg  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/jaunty/Release.gpg  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/jaunty/main/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/jaunty/Release.gpg  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/jaunty/non-free/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://packages.medibuntu.org/dists/jaunty/Release.gpg  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://packages.medibuntu.org/dists/jaunty/free/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Failed to fetch http://packages.medibuntu.org/dists/jaunty/non-free/i18n/Translation-en_NZ.bz2  Could not resolve 'student.otago.ac.nz'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

Seems the main error here is "Could not resolve student.otago.ac.nz"

---

### Post by humphreybc on 2009-08-12
Don't worry, fixed it. The actual proxy address was "proxy.student.otago.ac.nz" and not "student.otago.ac.nz"

Sorry!

---

### Post by lacis_alfredo on 2012-03-12
Should the ftp_proxy not be:

```
ftp_proxy=**http**://username.....
```
but instead, should it be this?
```
ftp_proxy=**ftp**://username.....
```

[Aussie Alf]("http://www.alfredo4570.net")

---

### Post by overdrank on 2012-03-12
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

