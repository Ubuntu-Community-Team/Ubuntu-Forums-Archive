---
title: "how to add the PPA key"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by barnaclebill18 on 2009-09-11
Hello again,

I have been trying to add the PPA key and can not get to the web site shown in the video at  [http://blog.launchpad.net/ppa/adding...-key-to-ubuntu](http://blog.launchpad.net/ppa/adding...-key-to-ubuntu)

In the video it shows a button Personal Package Archive, I can't seem to get to that page.

When I put in the URL shown, it comes up a page without that button.

Are there other instructions beside that video, I guess I'm too dumb to follow the video?

---

### Post by sisco311 on 2009-09-11
Open a terminal (Applications -> Accessories -> Terminal)
and type:
```
sudo apt-get update
```

The command should throw a similar warning:
```
Reading package lists... Done
W: GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A**9D1A0061**
W: You may want to run apt-get update to correct these problems

```

type:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys **9D1A0061**
```
where **9D1A0061** are the last 8 digits from the public key mentioned in the warning.
and:
```
sudo apt-get update
```

[https://launchpad.net/+help/soyuz/ppa-sources-list.html]("https://launchpad.net/+help/soyuz/ppa-sources-list.html")

---

### Post by barnaclebill18 on 2009-09-11
Thanks, I did that and this came up. Is it installed?

bill@bill-laptop:~$ sudo apt-get update
[sudo] password for bill: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
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
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
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
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Reading package lists... Done
bill@bill-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9D1A0061
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 9D1A0061
gpg: requesting key 9D1A0061 from hkp server keyserver.ubuntu.com
gpg: key 9D1A0061: public key "Opera Software Archive Automatic Signing Key 2010 <packager@opera.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
bill@bill-laptop:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                 
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
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                     
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
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Reading package lists... Done
bill@bill-laptop:~$

---

### Post by sisco311 on 2009-09-11
First you have to add the sources.list enrties.

Go to System -> Administration -> Software Sources -> Third Party Software tab.

HTH

If you still have problems, please post a link to the ppa.

---

### Post by barnaclebill18 on 2009-09-11
I did that and it wants me to enter the complete APT line of the repository.

I do not know what that is.

Thanks

---

### Post by drs305 on 2009-09-11
Here is the link to the Ubuntu wiki on Repositories. It covers how to add repositories into sources.list. There is also a link on the page to the command line method of doing the same thing:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

Starting with Karmic, the command "add-apt-repository ppa:XXXXX" will automatically add a PPA repository named "XXXXX" into /etc/apt/sources.list.d/ and import the public key if one is required.

---

### Post by hal10000 on 2009-09-11
Here is a very fine sources.list generator (incl. adding keys): [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by barnaclebill18 on 2009-09-11
I am really getting lost now.

In the video it shows copy and pasting a key in a file that I should  copy from the website I could not get to in my original question, called do-core-public key then importing it to the authentication page in Software Suorces.

I do not know what to do.

---

### Post by drs305 on 2009-09-11
We'd like to help but the link in the original post is bad. We can't get to that page to see what you are trying to do.

Can you give us the name of the PPA you are trying to add?

---

### Post by barnaclebill18 on 2009-09-11
I thought I was adding a Launchpad key to Ubuntu, because of an error I got when getting an update. I think it is for Medibuntu.

---

### Post by sisco311 on 2009-09-11
> **barnaclebill18 said:**
> I thought I was adding a Launchpad key to Ubuntu, because of an error I got when getting an update. I think it is for Medibuntu.

```
sudo apt-get install medibuntu-keyring && sudo apt-get update
```
should solve the problem.

[uhelp]community/Medibuntu[/uhelp]

---

### Post by barnaclebill18 on 2009-09-11
Thanks Sisco, I entered that and a bunch of stuff came up and at the end  

u.org jaunty Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Reading package lists... Done
bill@bill-laptop:~$ 

Is it installed now?

---

### Post by drs305 on 2009-09-11
> **barnaclebill18 said:**
> Thanks Sisco, I entered that and a bunch of stuff came up and at the end  

u.org jaunty Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Reading package lists... Done
bill@bill-laptop:~$ 

Is it installed now?

Yes.  In linux, normally if you run a command and it finishes with "Done" or doesn't give you any error message the command ran successfully.

---

### Post by barnaclebill18 on 2009-09-11
Thanks

One last question.

On last post I was asked to mark it as SOLVED and I could not figure out how to do that.

I went to edit on the first post but there was no way to change the title or put the SOLVED flag on.

---

### Post by sisco311 on 2009-09-11
> **barnaclebill18 said:**
> Thanks

One last question.

On last post I was asked to mark it as SOLVED and I could not figure out how to do that.

I went to edit on the first post but there was no way to change the title or put the SOLVED flag on.

go to Thread Tools and select Mark this thread as solved.

for detailed instructions (and screen-shots) see the link in my signature.

---

### Post by Dave W. on 2009-09-12
Thanks for Posting this.  This was my exact problem and now it is solved!!

Dave

---

