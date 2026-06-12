---
title: "problems with synaptic"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by anfelvas on 2011-08-31
Hi everyone,

I have been trying to execute synaptic in order to working on mysql. However, every time I write 

sudo apt-get update

I only get a large list of things, among which I have the message:

(-5 - No address associated with hostname)

Someone can help me?

---

### Post by anfelvas on 2011-08-31
Hi everyone,

I have been trying to execute synaptic in order to working on mysql. However, every time I write 

sudo apt-get update

I only get a large list of things, among which I have the message:

(-5 - No address associated with hostname)

Someone can help me?

---

### Post by Enigmapond on 2011-08-31
ok 1. Using the terminal is not using synaptic...that's only a GUI for what you are doing in the terminal.

2. Can you please post the output here with the "long line" of things...these "things" are important in diagnosing the problem.

Also list the output of :

```
cat /etc/apt/sources.list
```

---

### Post by TeoBigusGeekus on 2011-08-31
Can you please post us the whole output of the command?

---

### Post by anfelvas on 2011-08-31
OK

sudo apt-get update
Ign file: binary/ InRelease
Ign file: binary/ Release.gpg                                                                                       
Ign file: binary/ Release                                                                                           
Ign file: binary/ Translation-es_CO                                                                                                                                    
Ign file: binary/ Translation-es                                                                                                                                       
Ign file: binary/ Translation-en                                                                                                                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                                                                                                          
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) katya InRelease                                                                                                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                                                                                                                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                                                                                                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease                                                                                                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                                                                                                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                                                                                                                  
Err [http://packages.linuxmint.com](http://packages.linuxmint.com) katya Release.gpg                                                                                                                    
  Algo raro pasó al resolver «packages.linuxmint.com:http» (-5 - No address associated with hostname)
Err [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                                                                                                                     
  Algo raro pasó al resolver «archive.canonical.com:http» (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                                                                                                              
  Algo raro pasó al resolver «security.ubuntu.com:http» (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                                                                                 
  Algo raro pasó al resolver «extras.ubuntu.com:http» (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) natty Release.gpg                                                                                            
  Algo raro pasó al resolver «packages.medibuntu.org:http» (-5 - No address associated with hostname)
Ign [http://archive.canonical.com](http://archive.canonical.com) natty Release                                                                                                                         
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) katya Release                                                                                                                        
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg                                                                                                                        
  Algo raro pasó al resolver «archive.ubuntu.com:http» (-5 - No address associated with hostname)
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty Release                                                                                                                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                                                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                                                                                                                  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg                                                                                                                
  Algo raro pasó al resolver «archive.ubuntu.com:http» (-5 - No address associated with hostname)
49% [Conectando a packages.linuxmint.com] [Conectando a archive.ubuntu.com] [Conectando a security.ubuntu.com] [Conectando a archive.canonical.com] [Conectando a extra^


Now, the output of    cat /etc/apt/sources.list  is:

deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) katya main upstream import
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty partner
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free

#deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) natty-getdeb apps
#deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) natty-getdeb games

---

### Post by snip3r8 on 2011-08-31
> **anfelvas said:**
> Hi everyone,

I have been trying to execute synaptic in order to working on mysql. However, every time I write 

sudo apt-get update

I only get a large list of things, among which I have the message:

(-5 - No address associated with hostname)

Someone can help me?

synaptic is gui based,why are you typing in apt commands?

---

### Post by aura7 on 2011-08-31
Try opening synaptic from System->Administration->Synaptic Package Manager

Then you can mark all upgrades and apply to download.

---

### Post by overdrank on 2011-08-31
Hi and welcome, please do not create multiple threads on the same issue. Threads merged :)

---

