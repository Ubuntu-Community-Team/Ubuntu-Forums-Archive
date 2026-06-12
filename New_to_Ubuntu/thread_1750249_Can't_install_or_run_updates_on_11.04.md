---
title: "Can't install or run updates on 11.04"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by jiggajoe506 on 2011-05-05
I installed a bunch of package and ended up getting a message that says serious problem, if you see this again contact developers with this bug.
```
E:Type 'launchpad.net/tiheum/equinox/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/tiheum-equinox-natty.list
```

When going to update manager it also has an error message that looks like this...

---

### Post by ~Plue on 2011-05-05
Could you post the output of the following from a terminal?
```
[FONT=monospace]cat [/FONT]/etc/apt/sources.list.d/tiheum-equinox-natty.list
```

---

### Post by jiggajoe506 on 2011-05-05
i got the following 

```
deb http://ppa.launchpad.net/tiheum/equinox/ubuntu natty main #Faenza icon theme
launchpad.net/tiheum/equinox/ubuntu natty main
```

---

### Post by ~Plue on 2011-05-05
Run *gksu gedit /etc/apt/sources.list.d/tiheum-equinox-natty.list *to open the file as root and remove the 2nd line*. *Then run* sudo apt-get update *to refresh the software index.

---

### Post by jiggajoe506 on 2011-05-05
Still didn't work this is what a i got....

```
joey@joey-Aspire-5551:~$ sudo apt-get update
Ign http://download.skype.com stable InRelease
Ign http://linux.dropbox.com maverick InRelease                                
Ign http://download.skype.com stable Release.gpg                               
Ign http://security.ubuntu.com natty-security InRelease                        
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://download.skype.com stable Release                                   
Hit http://linux.dropbox.com maverick Release.gpg                              
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Ign http://download.skype.com stable/non-free i386 Packages/DiffIndex          
Hit http://linux.dropbox.com maverick Release                                  
Hit http://security.ubuntu.com natty-security Release.gpg                      
Ign http://download.skype.com stable/non-free TranslationIndex                 
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://download.skype.com stable/non-free i386 Packages                    
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://linux.dropbox.com maverick/main i386 Packages                       
Hit http://security.ubuntu.com natty-security Release                          
Hit http://extras.ubuntu.com natty Release                                     
Ign http://linux.dropbox.com maverick/main TranslationIndex                    
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                     
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://packages.medibuntu.org natty InRelease                              
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Hit http://us.archive.ubuntu.com natty Release                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release                                     
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/main i386 Packages               
Hit http://security.ubuntu.com natty-security/restricted i386 Packages         
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://us.archive.ubuntu.com natty-updates Release                         
Ign http://download.skype.com stable/non-free Translation-en_US                
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Ign http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Ign http://download.skype.com stable/non-free Translation-en                   
Hit http://security.ubuntu.com natty-security/universe i386 Packages           
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages         
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://packages.medibuntu.org natty/free Sources                           
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/main i386 Packages                      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                
Hit http://us.archive.ubuntu.com natty/universe i386 Packages                  
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages                
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://us.archive.ubuntu.com natty-updates/main Sources                    
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources              
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                
Hit http://packages.medibuntu.org natty/non-free Sources                       
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages              
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages        
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages          
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages        
Ign http://linux.dropbox.com maverick/main Translation-en_US                   
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Ign http://linux.dropbox.com maverick/main Translation-en                      
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Hit http://packages.medibuntu.org natty/free i386 Packages                     
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://packages.medibuntu.org natty/non-free i386 Packages                 
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://packages.medibuntu.org natty/free TranslationIndex                  
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US     
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en               
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://us.archive.ubuntu.com natty/universe Translation-en                 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en   
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Err http://ppa.launchpad.net natty/main Sources                                
  404  Not Found
Err http://ppa.launchpad.net natty/main i386 Packages                          
  404  Not Found
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
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en    
Ign http://ppa.launchpad.net natty/main Translation-en_US 
Ign http://ppa.launchpad.net natty/main Translation-en    
Ign http://packages.medibuntu.org natty/free Translation-en_US
Ign http://packages.medibuntu.org natty/free Translation-en
Ign http://packages.medibuntu.org natty/non-free Translation-en_US
Ign http://packages.medibuntu.org natty/non-free Translation-en
W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Did i delete the right thing also this is what it looked like after deleting....

---

### Post by ~Plue on 2011-05-05
> **jiggajoe506 said:**
> 
Did i delete the right thing also this is what it looked like after deleting....
Yes you did. That is another ppa [and from the looks of it]("https://launchpad.net/%7Eteam-xbmc/+archive/ppa"), they do not yet provide packages for natty. You could remove it by running *sudo rm /etc/apt/sources.list.d/team-xbmc** or from the software sources dialog in synaptic. //(Don't forget to run *apt-get update*)

---

### Post by jiggajoe506 on 2011-05-05
> **~Plue said:**
> Yes you did. That is another ppa [and from the looks of it]("https://launchpad.net/%7Eteam-xbmc/+archive/ppa"), they do not yet provide packages for natty. You could remove it by running *sudo rm /etc/apt/sources.list.d/team-xbmc** or from the software sources dialog in synaptic. //(Don't forget to run *apt-get update*)

It tried but it said no such directory found.... I really do suck at this

---

### Post by el_koraco on 2011-05-05
Software Center - Edit, Edit sources, find the PPA and disable it. Run the update and you're done.

---

### Post by ~Plue on 2011-05-05
> **jiggajoe506 said:**
> It tried but it said no such directory found.... I really do suck at this
You missed the asterisk (*), Its used as a wildcard to remove any file beginning with that name. (And always preface a command with *sudo *to run something as root)

If you're uncomfortable with the command line, use the synaptic package manager from the System > Administration menu (search the applications list for it if you're using the new unity interface). The repositories settings should be available from one of the menus.
edit: Or the software center as said in the previous post^

---

### Post by jiggajoe506 on 2011-05-05
problem solved it is updating now. Thanks for all the help guys!

---

