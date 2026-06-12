---
title: "Updates won't download fully -- also through Synaptic Package Manager"
date: 2015-09-29
forum: Networking &amp; Wireless
---

### Post by Todd in Berlin on 2015-09-29
Hi,

Ubuntu 14.04 LTS
Intel® Core™ i7-4700HQ CPU @ 2.40GHz × 8 Gigs RAM
on a Asus N56-type laptop


I got the normal a few times a week notification for an Update and everything proceeds normally including authorization but then the installation completely stalls. The computer doesn't freeze, but at least some or most of the relevant files are not downloaded.

When I tried it through Synaptic Package Manager I had what seemed like the same problems. 

Following is the text that I appeared on my screen when I tried doing the Update with Synaptic. Hopefully this sheds light on the entire problem. Downloads of other things, streaming You Tube etc. work fine.

Thanks!


    
```
W: Failed to fetch[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.13.0-65-generic_3.13.0-65.105_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.13.0-65-generic_3.13.0-65.105_amd64.deb)
      
    
    
    W: Failed to fetch[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-3.13.0-65-generic_3.13.0-65.105_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-3.13.0-65-generic_3.13.0-65.105_amd64.deb)
      
    
    
    W: Failed to fetch[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_3.13.0.65.71_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_3.13.0.65.71_amd64.deb)
      
    
    
    W: Failed to fetch[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.13.0.65.71_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.13.0.65.71_amd64.deb)
      
    
    
    W: Failed to fetch[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-signed/linux-signed-image-3.13.0-65-generic_3.13.0-65.105_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-signed/linux-signed-image-3.13.0-65-generic_3.13.0-65.105_amd64.deb)
      
    
    
    W: Failed to fetch[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-signed-generic_3.13.0.65.71_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-signed-generic_3.13.0.65.71_amd64.deb)
      
    
    
    W: Failed to fetch[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-signed-image-generic_3.13.0.65.71_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-signed-image-generic_3.13.0.65.71_amd64.deb)
      
    
    
    W: Failed to fetch[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-65_3.13.0-65.105_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-65_3.13.0-65.105_all.deb)
      
    
    
    W: Failed to fetch[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-65-generic_3.13.0-65.105_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-65-generic_3.13.0-65.105_amd64.deb)
      
    
    
    W: Failed to fetch[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.13.0.65.71_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.13.0.65.71_amd64.deb)
```

---

### Post by dino99 on 2015-09-30
"failed to fetch" means that server had some issues at that time (nothing you can do here; except retrying or switching to an other mirror)

---

### Post by Todd in Berlin on 2015-09-30
Thanks. How do I switch to a different mirror?

I tried it again - see attachment - three days with the same problem....
[ATTACH=CONFIG]264757[/ATTACH]

---

### Post by Bashing-om on 2015-09-30
Todd in Berlin; Hello;

By 3 days the mirror should have sync'd up and be current. Lends credence to a system package management problem.
We get a better report of conditions from the command line.
Post pack the results - Between Code Tags - of terminal commands:
```

sudo apt update
sudo apt upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we look at the reported errors and then see what action is appropriate .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Todd in Berlin on 2015-09-30
[COLOR=#000000]Thanks!

In both instances below I let process of download start for longer than a minute, but no go.

```

[/COLOR]todd@Dukla:~$ sudo apt update
[sudo] password for todd: 
Ign http://apt.spideroak.com release InRelease
Hit http://apt.spideroak.com release Release.gpg                               
Ign http://APT.spideroak.com release InRelease                                 
Hit http://apt.spideroak.com release Release                                   
Hit http://APT.spideroak.com release Release.gpg                               
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://APT.spideroak.com release Release                                   
Hit http://apt.spideroak.com release/restricted amd64 Packages                 
Ign http://repos.cloudme.com ./ InRelease                                      
Hit http://APT.spideroak.com release/restricted amd64 Packages                 
Hit http://apt.spideroak.com release/restricted i386 Packages                  
Hit http://APT.spideroak.com release/restricted i386 Packages                  
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://repos.cloudme.com ./ Release.gpg                                    
Get:1 https://download.01.org trusty InRelease                                 
Ign https://download.01.org trusty InRelease                                   
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://repos.cloudme.com ./ Release                                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:2 https://download.01.org trusty/main amd64 Packages/DiffIndex             
Ign https://download.01.org trusty/main amd64 Packages/DiffIndex               
Ign http://repos.cloudme.com ./ Packages/DiffIndex                             
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://apt.spideroak.com release/restricted Translation-en_US              
Ign http://APT.spideroak.com release/restricted Translation-en_US              
Ign http://apt.spideroak.com release/restricted Translation-en                 
Ign http://APT.spideroak.com release/restricted Translation-en                 
Ign https://download.01.org trusty/main i386 Packages/DiffIndex                
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://repos.cloudme.com ./ Packages                                       
Ign http://repos.cloudme.com ./ Translation-en_US                              
Ign http://repos.cloudme.com ./ Translation-en                                 
Hit https://download.01.org trusty/main amd64 Packages                         
Hit https://download.01.org trusty/main i386 Packages                          
Get:3 https://download.01.org trusty/main Translation-en_US                    
Ign https://download.01.org trusty/main Translation-en_US                      
Ign https://download.01.org trusty/main Translation-en                         
Ign http://dl.google.com stable InRelease                                      
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://extras.ubuntu.com trusty/main Sources                               
Ign http://dl.google.com stable/main Translation-en                            
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
100% [Connecting to us.archive.ubuntu.com (2001:67c:1562::15)] [Connecting to s
[COLOR=#000000]
```

... and I get Process Kill it? Message when I close Terminal....

+

[/COLOR][COLOR=#000000]```
[/COLOR]
todd@Dukla:~$ sudo apt upgrade
[sudo] password for todd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  fonts-dejavu fonts-sil-gentium fonts-sil-gentium-basic kde-l10n-engb
  libgnome-keyring0:i386 libllvm3.4:i386 libqt4-gui
  libreoffice-report-builder-bin linux-image-3.13.0-32-generic
  linux-image-3.13.0-36-generic linux-image-extra-3.13.0-32-generic
  linux-image-extra-3.13.0-36-generic linux-signed-image-3.13.0-36-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-3.13.0-65 linux-headers-3.13.0-65-generic
  linux-image-3.13.0-65-generic linux-image-extra-3.13.0-65-generic
  linux-signed-image-3.13.0-65-generic
The following packages will be upgraded:
  dkms libcgmanager0 libcgmanager0:i386 linux-generic linux-headers-generic
  linux-image-generic linux-signed-generic linux-signed-image-generic
8 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 61.7 MB of archives.
After this operation, 271 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
0% [Connecting to us.archive.ubuntu.com (2001:67c:1562::13)] [Connecting to sec
[COLOR=#000000]
```[/COLOR]



[COLOR=#000000]

[/COLOR]

---

### Post by Bashing-om on 2015-09-30
Todd in Berlin; Yuk !

That appears to be a proxy issue, Where your proxy is blocking the connection.
I have no experience in such an arrangement and thus can not advise further.
We will let the NetWorking peeps handle this one if/when this thread comes to their attention.

[INDENT][INDENT]some things I just do not know
[/INDENT][/INDENT]

---

### Post by Todd in Berlin on 2015-09-30
Thanks, Bashing-om!

---

### Post by Bashing-om on 2015-09-30
Todd in Berlin; Hey;

As said, I do not know. But, I will stay tuned to enhance my own knowledge base,

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Todd in Berlin on 2015-10-02
No one is seeing this thread -- can you recommend a better place on UbuntuForums to make this query? thanks.

---

### Post by Bashing-om on 2015-10-02
Todd in Berlin; Well;

As I do not have a solution; You might ping a moderator and have this thread moved to the 'networking' forum.
May get a dedicated audience in that sub-forum.

Best I am able to offer
[INDENT][INDENT][INDENT]If I knew better
[INDENT][INDENT][INDENT]I would do better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Todd in Berlin on 2015-10-03
I am trying this with a new thread...

I am not able to download updates to 14.04. I get "faled to fetch" notifications and then it was suggested I run suda apt update and sudo apt upgrade into Terminal. My results were as follows, and respectively:

[FONT=Verdana]```

[/FONT]todd@Dukla:~$ sudo apt update
[sudo] password for todd: 
Ign http://apt.spideroak.com release InRelease
Hit http://apt.spideroak.com release Release.gpg                               
Ign http://APT.spideroak.com release InRelease                                 
Hit http://apt.spideroak.com release Release                                   
Hit http://APT.spideroak.com release Release.gpg                               
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://APT.spideroak.com release Release                                   
Hit http://apt.spideroak.com release/restricted amd64 Packages                 
Ign http://repos.cloudme.com ./ InRelease                                      
Hit http://APT.spideroak.com release/restricted amd64 Packages                 
Hit http://apt.spideroak.com release/restricted i386 Packages                  
Hit http://APT.spideroak.com release/restricted i386 Packages                  
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://repos.cloudme.com ./ Release.gpg                                    
Get:1 https://download.01.org trusty InRelease                                 
Ign https://download.01.org trusty InRelease                                   
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://repos.cloudme.com ./ Release                                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:2 https://download.01.org trusty/main amd64 Packages/DiffIndex             
Ign https://download.01.org trusty/main amd64 Packages/DiffIndex               
Ign http://repos.cloudme.com ./ Packages/DiffIndex                             
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://apt.spideroak.com release/restricted Translation-en_US           
Ign http://APT.spideroak.com release/restricted Translation-en_US              
Ign http://apt.spideroak.com release/restricted Translation-en                 
Ign http://APT.spideroak.com release/restricted Translation-en                 
Ign https://download.01.org trusty/main i386 Packages/DiffIndex                
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://repos.cloudme.com ./ Packages                                       
Ign http://repos.cloudme.com ./ Translation-en_US                              
Ign http://repos.cloudme.com ./ Translation-en                                 
Hit https://download.01.org trusty/main amd64 Packages                         
Hit https://download.01.org trusty/main i386 Packages                          
Get:3 https://download.01.org trusty/main Translation-en_US                    
Ign https://download.01.org trusty/main Translation-en_US                      
Ign https://download.01.org trusty/main Translation-en                         
Ign http://dl.google.com stable InRelease                                      
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://extras.ubuntu.com trusty/main Sources                               
Ign http://dl.google.com stable/main Translation-en                            
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
100% [Connecting to us.archive.ubuntu.com (2001:67c:1562::15)] [Connecting to s

```



```

todd@Dukla:~$ sudo apt upgrade
[sudo] password for todd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  fonts-dejavu fonts-sil-gentium fonts-sil-gentium-basic kde-l10n-engb
  libgnome-keyring0:i386 libllvm3.4:i386 libqt4-gui
  libreoffice-report-builder-bin linux-image-3.13.0-32-generic
  linux-image-3.13.0-36-generic linux-image-extra-3.13.0-32-generic
  linux-image-extra-3.13.0-36-generic linux-signed-image-3.13.0-36-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-3.13.0-65 linux-headers-3.13.0-65-generic
  linux-image-3.13.0-65-generic linux-image-extra-3.13.0-65-generic
  linux-signed-image-3.13.0-65-generic
The following packages will be upgraded:
  dkms libcgmanager0 libcgmanager0:i386 linux-generic linux-headers-generic
  linux-image-generic linux-signed-generic linux-signed-image-generic
8 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 61.7 MB of archives.
After this operation, 271 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
0% [Connecting to us.archive.ubuntu.com (2001:67c:1562::13)] [Connecting to sec 
```

---

### Post by howefield on 2015-10-03
Duplicate threads merged and also moved to the "*Networking & Wireless*" forum for better support.

---

### Post by Todd in Berlin on 2015-10-03
Thanks!

---

