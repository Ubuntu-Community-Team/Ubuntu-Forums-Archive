---
title: "Help for openjdk in Ubuntu 11.04"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by akashs.cse on 2011-06-18
i am a new user in ubuntu 11.04. before ubuntu 11.04 i used ubuntu 10.04. in ubuntu 10.04 i used sun jdk for java. when i install ubuntu 11.04 i also install sun jdk for java. but after some days i realized that when i install a new software ubuntu system want openjdk where i install sun jdk so i failled to install software. 
my question is which is best for java open jdk or sun jdk ? 
if open jdk is best for than how install openjdk remember that at this moment i use sun jdk so how i remove sun jdk and how many archive need to download  to install openjdk ? 
or if sun jdk is best for java then how i install software which want openjdk please help me ?

:confused::confused::confused:
sorry for a lot of question. And thanks in advance.

---

### Post by gandaran on 2011-06-18
sun-java maybe better but if you have some application that requires openjdk to work then just install both javas, only for the web browsers java plugin don't install the icedtea-plugin, keep only the sun-java6-plugin installed and you'll have a perfect working system.
find the openjdk-java packages in synatic package manager and mark for install.

---

### Post by akashs.cse on 2011-06-18
when i go in the synaptic package manager mark openjdk for install. then the synaptic manager show me a massage:
openjdk-6-jdk:
 Depends: openjdk-6-jre but it is not going to be installed
 Recommends: libxt-dev but it is not going to be installed

how i resolve this ?

---

### Post by gandaran on 2011-06-18
post the output of 
```
sudo apt-get update
```
try again installing after update

---

### Post by akashs.cse on 2011-06-20
sudo apt-get update
i try this process but i can't overcome my problem. please give me another process.

---

### Post by gandaran on 2011-06-20
> **akashs.cse said:**
> sudo apt-get update
i try this process but i can't overcome my problem. please give me another process.
please post the full output, we cant guess what is the problem! you have to provide some details or errors if you want quick help, and what ubuntu version are you running?

---

### Post by akashs.cse on 2011-06-20
Again when i try to install openjdk i get this message :
<code>
The following package have i=unresolved dependencies.
Make sure that all required repositories are added or enabled
in the preference. 
openjdk-6-jdk:
 Depends: openjdk-6-jre but it is not going to be installed
 Recommends: libxt-dev but it is not going to be installed
</code>

---

### Post by akashs.cse on 2011-06-23
Again when i try to install openjdk i get this message :

The following package have i=unresolved dependencies.
Make sure that all required repositories are added or enabled
in the preference.
openjdk-6-jdk:
Depends: openjdk-6-jre but it is not going to be installed
Recommends: libxt-dev but it is not going to be installed

---

### Post by gandaran on 2011-06-23
on post #4 I asked for the full *sudo apt-get update* output, it may reveal or not anything but it's worth looking into it.
also post the sources list
```
gedit /etc/apt/sources.list
```

---

### Post by akashs.cse on 2011-06-28
I am extremely sorry for my stupid fault. here is the output of the [COLOR=Blue]_*sudo apt-get update*_[/COLOR]:
```

akash@akash:~$ sudo apt-get update
[sudo] password for shayla: 
Ign http://security.ubuntu.com natty-security InRelease                                          
Ign http://bd.archive.ubuntu.com natty InRelease                                                 
Ign http://bd.archive.ubuntu.com natty-updates InRelease                                         
Ign http://extras.ubuntu.com natty InRelease                                                     
Ign http://ppa.launchpad.net natty InRelease                                               
Hit http://security.ubuntu.com natty-security Release.gpg                                        
Ign http://ppa.launchpad.net natty InRelease                                                     
Hit http://security.ubuntu.com natty-security Release                                            
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]                                    
Ign http://archive.canonical.com natty InRelease                                                 
Hit http://extras.ubuntu.com natty Release                                                       
Hit http://ppa.launchpad.net natty Release.gpg                                                   
Hit http://extras.ubuntu.com natty/main Sources                                                  
Hit http://security.ubuntu.com natty-security/main Sources                                       
Hit http://ppa.launchpad.net natty Release.gpg                                             
Hit http://extras.ubuntu.com natty/main i386 Packages                                            
Hit http://security.ubuntu.com natty-security/restricted Sources                                 
Hit http://ppa.launchpad.net natty Release                                                       
Ign http://extras.ubuntu.com natty/main TranslationIndex                                         
Hit http://security.ubuntu.com natty-security/universe Sources                                   
Hit http://security.ubuntu.com natty-security/multiverse Sources                                 
Hit http://security.ubuntu.com natty-security/main i386 Packages                                 
Hit http://security.ubuntu.com natty-security/restricted i386 Packages                           
Hit http://security.ubuntu.com natty-security/universe i386 Packages                             
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages                           
Ign http://security.ubuntu.com natty-security/main TranslationIndex                              
Hit http://ppa.launchpad.net natty Release                                                       
Hit http://ppa.launchpad.net natty/main Sources                                                  
Hit http://ppa.launchpad.net natty/main i386 Packages                                            
Ign http://ppa.launchpad.net natty/main TranslationIndex                                   
Hit http://bd.archive.ubuntu.com natty Release.gpg                                               
Hit http://bd.archive.ubuntu.com natty-updates Release.gpg                                       
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex                        
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex                  
Ign http://security.ubuntu.com natty-security/universe TranslationIndex                    
Hit http://bd.archive.ubuntu.com natty Release                                                   
Hit http://bd.archive.ubuntu.com natty-updates Release                                           
Hit http://ppa.launchpad.net natty/main Sources                                                  
Hit http://ppa.launchpad.net natty/main i386 Packages                                            
Ign http://ppa.launchpad.net natty/main TranslationIndex                                   
Hit http://bd.archive.ubuntu.com natty/main Sources                                              
Hit http://bd.archive.ubuntu.com natty/restricted Sources                                        
Hit http://bd.archive.ubuntu.com natty/universe Sources                                          
Hit http://bd.archive.ubuntu.com natty/multiverse Sources                                  
Hit http://bd.archive.ubuntu.com natty/main i386 Packages                                  
Hit http://bd.archive.ubuntu.com natty/restricted i386 Packages                            
Hit http://bd.archive.ubuntu.com natty/universe i386 Packages                                    
Hit http://bd.archive.ubuntu.com natty/multiverse i386 Packages                                  
Ign http://bd.archive.ubuntu.com natty/main TranslationIndex                               
Hit http://archive.canonical.com natty Release.gpg                                               
Ign http://bd.archive.ubuntu.com natty/multiverse TranslationIndex                               
Ign http://bd.archive.ubuntu.com natty/restricted TranslationIndex                               
Ign http://bd.archive.ubuntu.com natty/universe TranslationIndex                                 
Hit http://archive.canonical.com natty Release                                                   
Hit http://archive.canonical.com natty/partner i386 Packages                                     
Hit http://bd.archive.ubuntu.com natty-updates/main Sources                                      
Hit http://bd.archive.ubuntu.com natty-updates/restricted Sources                                
Hit http://bd.archive.ubuntu.com natty-updates/universe Sources                            
Hit http://bd.archive.ubuntu.com natty-updates/multiverse Sources                                
Hit http://bd.archive.ubuntu.com natty-updates/main i386 Packages                                
Hit http://bd.archive.ubuntu.com natty-updates/restricted i386 Packages                          
Hit http://bd.archive.ubuntu.com natty-updates/universe i386 Packages                            
Hit http://bd.archive.ubuntu.com natty-updates/multiverse i386 Packages                          
Ign http://bd.archive.ubuntu.com natty-updates/main TranslationIndex                             
Ign http://bd.archive.ubuntu.com natty-updates/multiverse TranslationIndex                       
Ign http://archive.canonical.com natty/partner TranslationIndex                                  
Ign http://bd.archive.ubuntu.com natty-updates/restricted TranslationIndex                       
Ign http://bd.archive.ubuntu.com natty-updates/universe TranslationIndex                         
Ign http://security.ubuntu.com natty-security/main Translation-en_US                             
Ign http://security.ubuntu.com natty-security/main Translation-en                                
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US                 
Ign http://extras.ubuntu.com natty/main Translation-en_US                                        
Ign http://security.ubuntu.com natty-security/multiverse Translation-en                          
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US                 
Ign http://security.ubuntu.com natty-security/restricted Translation-en                    
Ign http://security.ubuntu.com natty-security/universe Translation-en_US                         
Ign http://security.ubuntu.com natty-security/universe Translation-en                            
Ign http://ppa.launchpad.net natty/main Translation-en_US                                        
Ign http://ppa.launchpad.net natty/main Translation-en                                     
Ign http://ppa.launchpad.net natty/main Translation-en_US                                  
Ign http://extras.ubuntu.com natty/main Translation-en                                     
Ign http://ppa.launchpad.net natty/main Translation-en                                     
Ign http://bd.archive.ubuntu.com natty/main Translation-en_US        
Ign http://bd.archive.ubuntu.com natty/main Translation-en
Ign http://bd.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://bd.archive.ubuntu.com natty/multiverse Translation-en
Ign http://bd.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://bd.archive.ubuntu.com natty/restricted Translation-en
Ign http://bd.archive.ubuntu.com natty/universe Translation-en_US
Ign http://bd.archive.ubuntu.com natty/universe Translation-en
Ign http://bd.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://bd.archive.ubuntu.com natty-updates/main Translation-en
Ign http://bd.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://bd.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://bd.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://bd.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://bd.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://bd.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://archive.canonical.com natty/partner Translation-en_US
Ign http://archive.canonical.com natty/partner Translation-en
Fetched 72 B in 2min 6s (1 B/s)
Reading package lists... Done
akash@akash:~$ 

```

---

