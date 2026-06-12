---
title: "Installing OpenKinect (Libfreenect) on natty narwhal 11.04"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by greenblob on 2011-07-17
The libfreenect package doesn't seem to be available in any graphical installer, so I've resorted to using the terminal to install it.
       I'm getting lots of errors while attempting to install.
I think the errors have primarily derived from an incorrect PPA for installation, probably because it's outdated. The PPA is "ppa:arne-alamut/freenect", which was taken from ***[COLOR="Blue"][their launchpad website]("https://launchpad.net/~arne-alamut/+archive/freenect")[/COLOR]***.

If anyone has a working PPA, or any knowledge relevant to the subject, I'd appreciate it very much, thanks in advance. :D

**_My Command Window When Installing:_**
```
**luke@luke:~$ sudo add-apt-repository ppa:arne-alamut/freenect**
[sudo] password for luke: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 2EBE82D1B759F33B878955C38C51891484AEB4FF
gpg: requesting key 84AEB4FF from hkp server keyserver.ubuntu.com
gpg: key 84AEB4FF: "Launchpad PPA for Arne" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
**luke@luke:~$ sudo apt-get update**
Ign http://gb.archive.ubuntu.com natty InRelease
Hit http://gb.archive.ubuntu.com natty Release.gpg                             
Hit http://repository.spotify.com stable InRelease                             
Hit http://gb.archive.ubuntu.com natty Release                                 
Ign http://archive.canonical.com natty InRelease                               
Ign http://archive.canonical.com lucid InRelease                               
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://archive.canonical.com natty Release.gpg                             
Ign http://security.ubuntu.com natty-security InRelease                        
Hit http://extras.ubuntu.com natty Release.gpg                                 
Ign http://ppa.launchpad.net natty Release.gpg                                 
Hit http://archive.canonical.com lucid Release.gpg                             
Hit http://gb.archive.ubuntu.com natty/main Sources                            
Hit http://security.ubuntu.com natty-security Release.gpg                      
Hit http://extras.ubuntu.com natty Release                                     
Ign http://ppa.launchpad.net natty Release                                     
Hit http://archive.canonical.com natty Release                                 
Hit http://gb.archive.ubuntu.com natty/restricted Sources                      
Hit http://gb.archive.ubuntu.com natty/universe Sources                        
Hit http://gb.archive.ubuntu.com natty/multiverse Sources                      
Hit http://gb.archive.ubuntu.com natty/main i386 Packages                      
Hit http://gb.archive.ubuntu.com natty/restricted i386 Packages                
Hit http://security.ubuntu.com natty-security Release                          
Hit http://archive.canonical.com lucid Release                                 
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://gb.archive.ubuntu.com natty/universe i386 Packages                  
Hit http://gb.archive.ubuntu.com natty/multiverse i386 Packages                
Ign http://gb.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://gb.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://gb.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Ign http://gb.archive.ubuntu.com natty/universe TranslationIndex               
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://gb.archive.ubuntu.com natty/main Translation-en_GB                  
Hit http://gb.archive.ubuntu.com natty/multiverse Translation-en_GB            
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/main i386 Packages               
Hit http://security.ubuntu.com natty-security/restricted i386 Packages         
Hit http://archive.canonical.com lucid/partner Sources                         
Hit http://archive.canonical.com lucid/partner i386 Packages                   
Hit http://gb.archive.ubuntu.com natty/restricted Translation-en_GB            
Hit http://security.ubuntu.com natty-security/universe i386 Packages           
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages         
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://archive.canonical.com lucid/partner TranslationIndex                
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Hit http://gb.archive.ubuntu.com natty/universe Translation-en_GB              
Err http://ppa.launchpad.net natty/main Sources                                
  404  Not Found
Ign http://extras.ubuntu.com natty/main Translation-en_GB                      
Err http://ppa.launchpad.net natty/main i386 Packages                          
  404  Not Found
Ign http://archive.canonical.com natty/partner Translation-en_GB               
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://gb.archive.ubuntu.com natty/main Translation-en                     
Ign http://ppa.launchpad.net natty/main Translation-en_GB            
Ign http://gb.archive.ubuntu.com natty/multiverse Translation-en     
Ign http://ppa.launchpad.net natty/main Translation-en               
Ign http://archive.canonical.com lucid/partner Translation-en_GB     
Ign http://security.ubuntu.com natty-security/main Translation-en_GB 
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://gb.archive.ubuntu.com natty/restricted Translation-en
Ign http://gb.archive.ubuntu.com natty/universe Translation-en
Ign http://archive.canonical.com lucid/partner Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_GB
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_GB
Ign http://security.ubuntu.com natty-security/universe Translation-en

[COLOR="Red"]W: Failed to fetch http://ppa.launchpad.net/arne-alamut/freenect/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/arne-alamut/freenect/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found[/COLOR]

E: Some index files failed to download. They have been ignored, or old ones used instead.
[B]luke@luke:~$ sudo apt-get install freenect
[/B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package freenect
**luke@luke:~$ **

```

---

### Post by anonymousphrase on 2011-07-26
There are currently no packages created for the current version of Ubuntu (Natty Narwhal).  That's what generates the two error messages at the end of the **sudo apt-get update**.

So then when you go to install freenect, the command is unable to find the proper packages (they don't exist) and fails.

The solution is to perform an [[COLOR="Blue"]Ubuntu Manual Install[/COLOR]]("http://openkinect.org/wiki/Getting_Started#Ubuntu_Manual_Install") as detailed on the getting started page.

Then since you are sure to be feeling really reved up by that experience, you can generate your own Natty Narwhal packages, post them on Launchpad, and thus make the world a better place of FOSS software.

---

### Post by greenblob on 2011-10-26
> **anonymousphrase said:**
> There are currently no packages created for the current version of Ubuntu (Natty Narwhal).  That's what generates the two error messages at the end of the **sudo apt-get update**.

So then when you go to install freenect, the command is unable to find the proper packages (they don't exist) and fails.

The solution is to perform an [[COLOR="Blue"]Ubuntu Manual Install[/COLOR]]("http://openkinect.org/wiki/Getting_Started#Ubuntu_Manual_Install") as detailed on the getting started page.

Then since you are sure to be feeling really reved up by that experience, you can generate your own Natty Narwhal packages, post them on Launchpad, and thus make the world a better place of FOSS software.

Thanks ver much,
that was helpfull :KS

Luke

---

