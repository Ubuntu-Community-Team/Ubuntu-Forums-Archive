---
title: "Something wrong with update?"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by lockalidiot on 2010-02-24
Hi again! Moments ago I decided to check for updates:
```
sudo apt-get update
```
What I got looked first normal, but then the bugger started to throw errors at me. (so to speak)

I'll post the whole output here.

```
here@me:~$ **sudo apt-get update**
Hit http://deb.opera.com stable Release.gpg
Ign http://deb.opera.com stable/non-free Translation-en_US
Ign http://download.skype.com stable Release.gpg                               
Hit http://deb.opera.com stable Release                                        
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Get:1 http://dl.google.com stable Release.gpg [189B]                           
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Ign http://download.skype.com stable/non-free Translation-en_US                
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://deb.opera.com stable/non-free Packages                              
Ign http://download.skype.com stable Release                                   
Get:2 http://archive.canonical.com karmic Release.gpg [189B]                   
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Ign http://deb.opera.com stable/non-free Packages                              
Get:3 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Get:4 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://deb.opera.com stable/non-free Packages                              
Ign http://download.skype.com stable/non-free Packages                         
Get:5 http://dl.google.com stable Release [2,540B]                             
Get:6 http://archive.canonical.com karmic Release [9,347B]                     
Hit http://ppa.launchpad.net karmic Release                                    
Ign http://download.skype.com stable/non-free Packages                         
Hit http://security.ubuntu.com karmic-security/main Packages                   
Get:7 http://dl.google.com stable/main Packages [871B]                         
**Err** http://download.skype.com stable/non-free Packages                         
  404  Not Found [IP: 130.117.72.42 80]
Get:8 http://ppa.launchpad.net karmic Release [65.9kB]                         
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Sources                    
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Get:9 http://archive.canonical.com karmic/partner Packages [2,260B]            
Get:10 http://ppa.launchpad.net karmic Release [66.0kB]                        
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://ppa.launchpad.net karmic Release                                    
Ign http://ppa.launchpad.net karmic Release                                    
Hit http://ppa.launchpad.net karmic/main Packages                              
Get:11 http://ppa.launchpad.net karmic/main Packages [4,130B]                
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Sources                             
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                              
**Err** http://fi.archive.ubuntu.com karmic Release.gpg                            
  **Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out**
Err http://fi.archive.ubuntu.com karmic/main Translation-en_US
  Unable to connect to fi.archive.ubuntu.com http:
Err http://fi.archive.ubuntu.com karmic/restricted Translation-en_US
  Unable to connect to fi.archive.ubuntu.com http:
Err http://fi.archive.ubuntu.com karmic/universe Translation-en_US
  Unable to connect to fi.archive.ubuntu.com http:
Err http://fi.archive.ubuntu.com karmic/multiverse Translation-en_US
  Unable to connect to fi.archive.ubuntu.com http:
Err http://fi.archive.ubuntu.com karmic-updates Release.gpg
  Unable to connect to fi.archive.ubuntu.com http:
Err http://fi.archive.ubuntu.com karmic-updates/main Translation-en_US
  Unable to connect to fi.archive.ubuntu.com http:
Err http://fi.archive.ubuntu.com karmic-updates/restricted Translation-en_US
  Unable to connect to fi.archive.ubuntu.com http:
Err http://fi.archive.ubuntu.com karmic-updates/universe Translation-en_US
  Unable to connect to fi.archive.ubuntu.com http:
Err http://fi.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
  Unable to connect to fi.archive.ubuntu.com http:
Fetched 86.1kB in 2min 0s (717B/s)                     
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1E5D5E8D66AE0775
W: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out

W: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2  Unable to connect to fi.archive.ubuntu.com http:

W: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2  Unable to connect to fi.archive.ubuntu.com http:

W: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2  Unable to connect to fi.archive.ubuntu.com http:

W: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2  Unable to connect to fi.archive.ubuntu.com http:

W: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Unable to connect to fi.archive.ubuntu.com http:

W: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2  Unable to connect to fi.archive.ubuntu.com http:

W: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2  Unable to connect to fi.archive.ubuntu.com http:

W: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2  Unable to connect to fi.archive.ubuntu.com http:

W: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2  Unable to connect to fi.archive.ubuntu.com http:

W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz  404  Not Found [IP: 130.117.72.42 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: Duplicate sources.list entry http://ppa.launchpad.net karmic/main Packages (/var/lib/apt/lists/ppa.launchpad.net_conkyhardcore_ppa_ubuntu_dists_karmic_main_binary-amd64_Packages)
me@here:~$
```

Anyone knows what is this. Should I be worried or in panic? 

Thanks guys and girls!

---

### Post by Zeptinune on 2010-02-24
To be honest even though I'm a noob friend. : D I tend to get the exact same thing from the us updates sever. Some things tend to not download at all so they are skipped, either when I update from the terminal or when I update from the manager.

I read in a wiki a week ago that it's usually due to the files being locked or being in use, and I was told to do a restart close all the things you need after startup and then update because less things are running.

---

### Post by slakkie on 2010-02-24
Perhaps the mirror is down/busy?
Try another mirror and see what happens.

---

### Post by lockalidiot on 2010-02-24
Did that, updated via Update Manager this time, got this error message:
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1E5D5E8D66AE0775
W: Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic/Release.gpg](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic/Release.gpg)  Could not connect to [www.nic.funet.fi:80](www.nic.funet.fi:80) (193.166.3.3), connection timed out

W: Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic/main/i18n/Translation-en_US.bz2](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic/main/i18n/Translation-en_US.bz2)  Unable to connect to [www.nic.funet.fi](www.nic.funet.fi) http:

W: Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Unable to connect to [www.nic.funet.fi](www.nic.funet.fi) http:

W: Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic/universe/i18n/Translation-en_US.bz2](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic/universe/i18n/Translation-en_US.bz2)  Unable to connect to [www.nic.funet.fi](www.nic.funet.fi) http:

W: Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to [www.nic.funet.fi](www.nic.funet.fi) http:

W: Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-updates/Release.gpg](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-updates/Release.gpg)  Unable to connect to [www.nic.funet.fi](www.nic.funet.fi) http:

W: Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to [www.nic.funet.fi](www.nic.funet.fi) http:

W: Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to [www.nic.funet.fi](www.nic.funet.fi) http:

W: Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to [www.nic.funet.fi](www.nic.funet.fi) http:

W: Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to [www.nic.funet.fi](www.nic.funet.fi) http:

W: Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-security/Release.gpg](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-security/Release.gpg)  Unable to connect to [www.nic.funet.fi](www.nic.funet.fi) http:

W: Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Unable to connect to [www.nic.funet.fi](www.nic.funet.fi) http:

W: Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to [www.nic.funet.fi](www.nic.funet.fi) http:

W: Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to [www.nic.funet.fi](www.nic.funet.fi) http:

W: Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to [www.nic.funet.fi](www.nic.funet.fi) http:

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404  Not Found [IP: 78.141.179.2 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by slakkie on 2010-02-24
What happens when you use archive.ubuntu.com?

---

### Post by lockalidiot on 2010-02-24
First it freezes in the middle of the process for a long time.( see screenshot.png)
Then I get an error message.(see attachment2.png)
With this text:
```
GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1E5D5E8D66AE0775Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Connection failed [IP: 91.189.88.40 80]
Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz  404  Not Found [IP: 130.117.72.43 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by slakkie on 2010-02-24
Remove the skype entry from /etc/apt/sources.list or /etc/apt/sources.list.d/somefile.list

And for the key error do the following:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1E5D5E8D66AE0775

instead of using keyserver.ubuntu.com you can also use wwwkeys.eu.pgp.net

And try again.

---

### Post by _Kurt on 2010-02-24
Err.. looks like the servers are messed up :confused:

Fetched 30.1kB in 23min 20s (22B/s)
Reading package lists... Done

I have never been able complete my updates today:-({|=:-({|=:-({|=

---

### Post by philinux on 2010-02-24
> **_Kurt said:**
> Err.. looks like the servers are messed up :confused:

Fetched 30.1kB in 23min 20s (22B/s)
Reading package lists... Done

I have never been able complete my updates today:-({|=:-({|=:-({|=

Yep I had to switch from main to the uk server.

---

### Post by tom3393 on 2010-02-24
I've got the same problem... Something is broken somewhere !

---

### Post by lockalidiot on 2010-02-24
> **slakkie said:**
> Remove the skype entry from /etc/apt/sources.list or /etc/apt/sources.list.d/somefile.list

And for the key error do the following:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1E5D5E8D66AE0775

instead of using keyserver.ubuntu.com you can also use wwwkeys.eu.pgp.net

And try again.

Done, See attachment... Frozen there still.



EDIT: no errors this time. Just took awfully long.
```
Fetched 4,097B in 4min 32s (15B/s)
Reading package lists... Done
```

---

### Post by routermods on 2010-02-24
I am also having issues. 2 fresh installs both wont update. I tried the key thing and won't work.

---

### Post by lockalidiot on 2010-02-24
My stuff seems to work.. though it is still awfully slow.

---

### Post by _Kurt on 2010-02-25
Ahh, a new morning and i think the severs are awake today :D

Fetched 772kB in 9s (77.6kB/s)                                                                       
Reading package lists... Done

Now i am able to do my updates without any hassle :P

---

### Post by manickaselvam on 2010-02-26
> **philinux said:**
> Yep I had to switch from main to the uk server.
Hi Guys... Try this way... 

Systems > Administration > Software Sources > > 

Select Download From: Down button > Select Other > Click "Select Best Server" 

It will run for 3-5 minutes to ping all the ubuntu servers through out the world and select the best one for you. Then "Choose the Server".

Now you will be able to update your machine perfectly. It worked for me. Try this out.

Manick

---

### Post by manickaselvam on 2010-02-26
> **tom3393 said:**
> I've got the same problem... Something is broken somewhere !
Hi Guys... Try this way... 

Systems > Administration > Software Sources > > 

Select Download From: Down button > Select Other > Click "Select Best Server" 

It will run for 3-5 minutes to ping all the ubuntu servers through out the world and select the best one for you. Then "Choose the Server".

Now you will be able to update your machine perfectly. It worked for me. Try this out.

Manick

---

### Post by manickaselvam on 2010-02-26
Hi Guys... Try this way... 

Systems > Administration > Software Sources > > 

Select Download From: Down button > Select Other > Click "Select Best Server" 

It will run for 3-5 minutes to ping all the ubuntu servers through out the world and select the best one for you. Then "Choose the Server".

Now you will be able to update your machine perfectly. It worked for me. Try this out.

Manick

---

### Post by afrodeity on 2010-03-01
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
  404  Not Found

---

### Post by baraka607 on 2010-10-14
am having the same problem and till now no lucky to solve it... please help

 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1E5D5E8D66AE0775

---

### Post by sdibaja on 2010-10-14
I was having this issue but manually installed the keys as described in post #7

< sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys _____ >

I think it is fixed!  

Thanks all:KS

---

### Post by baraka607 on 2010-10-14
> **slakkie said:**
> Remove the skype entry from /etc/apt/sources.list or /etc/apt/sources.list.d/somefile.list

And for the key error do the following:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1E5D5E8D66AE0775

instead of using keyserver.ubuntu.com you can also use wwwkeys.eu.pgp.net

And try again.

Ha ha ha ha' thank you man you have just do the magic and the problem is gone now. Yo the man!One:)

---

### Post by baraka607 on 2010-10-15
> **lockalidiot said:**
> First it freezes in the middle of the process for a long time.( see screenshot.png)
Then I get an error message.(see attachment2.png)
With this text:
```
GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1E5D5E8D66AE0775Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Connection failed [IP: 91.189.88.40 80]
Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz  404  Not Found [IP: 130.117.72.43 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```

hey buddy this command line works for me you should try this if you still got problem:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1E5D5E8D66AE0775

---

