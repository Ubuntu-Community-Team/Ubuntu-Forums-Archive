---
title: "Update Error Question"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by barnaclebill18 on 2009-09-10
Hello.

This evening I received an update to Jaunty and this message came up after the Update Manager finished.

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
 

What does this mean and is it important?

Thanks

---

### Post by Cheezespread on 2009-09-11
GPG - stands for Gnu PG - or GNU Privacy Guard. It is a sort of encyption/digital signing that is applied over the updates so as to authenticate where the updates are from. Similar to the digital signatures used in emails.The keys used in this process can be of the form *.gpg or *.asc. The updates you are trying to install are tied to a Public key 2EBC26B60C5A2783. 

Can you please try this and update us back with the results:

This should add the Medibuntu to your sources.list.
```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

This should add the **GPG** keys
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Please correct me if i am wrong.

---

### Post by barnaclebill18 on 2009-09-11
Well, I entered the above and this came up.

bill@bill-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
[sudo] password for bill: 
--2009-09-11 00:32:16--  [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 280 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 280         --.-K/s   in 0s      

2009-09-11 00:32:17 (21.7 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [280/280]

bill@bill-laptop:~$

---

### Post by Cheezespread on 2009-09-11
That adds medibuntu to the sources list. Could you run the second code in terminal as well.

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

This should install the GPG keys needed. Let us know if the same works.

---

### Post by Partyboi2 on 2009-09-11
Since you have orginally already added the repo, you only needed to add the key[FONT=monospace]
[/FONT]```
sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by natravis on 2009-09-11
You need to also run the second command that he listed. Then run updates again.

Edit: I like how in 30 seconds 3 people responded with the same info.

---

### Post by barnaclebill18 on 2009-09-11
When I entered the second command, this came up, I put a y there.

bill@bill-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
[sudo] password for bill: 
--2009-09-11 00:32:16--  [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 280 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 280         --.-K/s   in 0s      

2009-09-11 00:32:17 (21.7 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [280/280]

bill@bill-laptop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US            
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources             
Fetched 198B in 11s (17B/s)                                                    
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Install these packages without verification [y/N]? y
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free medibuntu-keyring 2008.04.20 [3448B]
Fetched 3448B in 1s (2880B/s)                           
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 153541 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release               
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 198B in 1s (117B/s)
Reading package lists... Done

---

### Post by Cheezespread on 2009-09-11
As this portion says :
> Install these packages without verification [y/N]? y
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free medibuntu-keyring 2008.04.20 [3448B]
Fetched 3448B in 1s (2880B/s) 
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 153541 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

The keyring has been added and the sources have been updated. COuld you try the updates from the update-manager now?. Let us know if you have any more trouble . ( I suppose you shouldn't)

Please correct me if i am wrong.

---

### Post by barnaclebill18 on 2009-09-11
I ran the Update Manager and it said I was up to date and no error messages came up, so I would guess it is fixed.

Thanks.

---

### Post by Cheezespread on 2009-09-11
You are welcome :) . Please edit the first post's title and mark as SOLVED .Thanks

---

### Post by barnaclebill18 on 2009-09-11
I tried to edit the first post, but it does not change in in the title.

---

### Post by MelDJ on 2009-09-11
there is a video here on how to add the pub key. hope it helps:
[http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

---

### Post by Partyboi2 on 2009-09-11
> **barnaclebill18 said:**
> I tried to edit the first post, but it does not change in in the title.
You don't need to edit the title and mark it as solve. To mark a thread solved on the top right select "Thread Tools" and choose "Mark this thread solved" and its all done :)

---

