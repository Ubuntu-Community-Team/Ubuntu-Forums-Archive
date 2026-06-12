---
title: "intallation of skype, flash player etc."
date: 2009-03-15
forum: New to Ubuntu
---

### Post by ni ni on 2009-03-15
Hello!

This is the most basic of questions :-(

But i think someone will help me because I only ever find kind patient people here!

When i double click on the skype or flash player installer i get:

"Only one software management tool is allowed to run at the same time"
please close the other application first e.g. Update Manager, aptitude, or Synaptic first.


How do i figure out wheich software management tool is open, and then how do i install my installer.

is it as simple as double clicking, and following the prompts??


Thank you soooo much x x x

---

### Post by humphreybc on 2009-03-15
It should be simple to install. Try rebooting your computer, wait about 30 seconds after you have logged in and then double click one of the files to see if it gives the same error. If it does then it means Synaptic is broken or trying to update in the background or something...

---

### Post by ni ni on 2009-03-15
thanks humphreybc.

yes I have restarted a couple of times.  I always get that message.

---

### Post by billgoldberg on 2009-03-15
On the top panel, there should be a icon if a package manager is working.

Now to anwser your question, I'll give you a terminal command.

Go to Applications -> Accessories -> Terminal and copy/paste this:


sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 skype



You will be prompted to enter your password, but you won't see what you type. Just type it blindly and press enter.

When it's done spitting out lines, everything will be installed and ready to use.

This will give you flash, skype, java, audio and video codecs and the dvd codecs.

Stuff everyone needs.

---

### Post by konqueror7 on 2009-03-15
ubuntu allows only to run one instance of a package manager, for example synaptic, dpkg, apt-get, or aptitude...so, what you might doing is double clicking them both at the same time...try to install them, one by one...close synaptic if its open or add/remove...;)

---

### Post by ni ni on 2009-03-15
Should i post the output?

niamh@niamh-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 skype
[sudo] password for niamh: 
--2009-03-15 11:29:54--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 230 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 230         --.-K/s   in 0s      

2009-03-15 11:29:54 (21.8 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [230/230]

OK
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_IE        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_IE  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_IE    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_IE  
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [197B]                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_IE             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_IE        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release             
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid Release.gpg                
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Translation-en_IE    
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Translation-en_IE
Get:2 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates Release.gpg [189B]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_IE
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11.7kB]       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages            
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid Release                         
Get:4 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates Release [51.2kB]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages [3518B]
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages [12.6kB]    
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Packages                
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Sources
Get:7 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Packages [307kB]
Get:8 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Packages [8097B]
Get:9 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Sources [97.7kB]
Get:10 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Sources [2474B]
Get:11 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Packages [75.1kB]
Get:12 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Sources [18.6kB]
Get:13 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Packages [10.9kB]
Get:14 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Sources [4118B]
Fetched 604kB in 2s (236kB/s)                       
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
niamh@niamh-laptop:~$ 


I don't know how to manually run dpkg!!

---

### Post by billgoldberg on 2009-03-15
> **ni ni said:**
> Should i post the output?

niamh@niamh-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 skype
[sudo] password for niamh: 
--2009-03-15 11:29:54--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 230 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 230         --.-K/s   in 0s      

2009-03-15 11:29:54 (21.8 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [230/230]

OK
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_IE        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_IE  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_IE    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_IE  
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [197B]                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_IE             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_IE        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release             
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid Release.gpg                
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Translation-en_IE    
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Translation-en_IE
Get:2 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates Release.gpg [189B]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_IE
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11.7kB]       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages            
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid Release                         
Get:4 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates Release [51.2kB]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages [3518B]
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages [12.6kB]    
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Packages                
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Sources
Get:7 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Packages [307kB]
Get:8 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Packages [8097B]
Get:9 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Sources [97.7kB]
Get:10 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Sources [2474B]
Get:11 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Packages [75.1kB]
Get:12 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Sources [18.6kB]
Get:13 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Packages [10.9kB]
Get:14 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Sources [4118B]
Fetched 604kB in 2s (236kB/s)                       
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
niamh@niamh-laptop:~$ 


I don't know how to manually run dpkg!!

In the terminal run this command:

```
sudo dpkg --configure -a
```


Then run the previous command again.

This error happens when you close a package manager while it's busy.

---

### Post by ni ni on 2009-03-15
I'm getting the same output (and it doesn't ask for my password this time)

> niamh@niamh-laptop:~$ sudo dpkg - -configure -a
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
niamh@niamh-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 skype
--2009-03-15 11:43:49--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 230 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 230         --.-K/s   in 0s      

2009-03-15 11:43:52 (20.7 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [230/230]

OK
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid Release.gpg
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Translation-en_IE               
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Translation-en_IE         
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Translation-en_IE           
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Translation-en_IE         
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Translation-en_IE       
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Translation-en_IE 
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Translation-en_IE   
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_IE
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid Release                    
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates Release            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_IE
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_IE
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_IE
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_IE
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Packages       
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_IE
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_IE
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
niamh@niamh-laptop:~$ 

---

### Post by ni ni on 2009-03-15
konqueror7, it's not the double clicking as i tried it with right clicking too, to make sure that wasn't the problem.

---

### Post by Berserker v7 on 2009-03-15
First of all, its `dpkg --configure -a`, not `dpkg - -configure -a`...

I believe your problem is that update-manager is running in the background... automatic updates are on by default in ubuntu... so, first issue the command `pkill update-manager` and then try the install command given by billgoldberg... hope this helps...

---

### Post by ni ni on 2009-03-15
after the command pkill update-manager  nothing happens.  :-(

---

### Post by Berserker v7 on 2009-03-15
after pkill, when you give the install commands, what's the output?

---

### Post by ni ni on 2009-03-15
This output:
```
root@niamh-laptop:/home/niamh# pkill update-manager
root@niamh-laptop:/home/niamh# sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 skype
--2009-03-15 17:22:37--  http://www.medibuntu.org/sources.list.d/intrepid.list
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 230 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 230         --.-K/s   in 0s      

2009-03-15 17:22:37 (15.1 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [230/230]

OK
Hit http://ie.archive.ubuntu.com intrepid Release.gpg
Ign http://ie.archive.ubuntu.com intrepid/main Translation-en_IE    
Hit http://security.ubuntu.com intrepid-security Release.gpg         
Ign http://security.ubuntu.com intrepid-security/main Translation-en_IE
Ign http://ie.archive.ubuntu.com intrepid/restricted Translation-en_IE
Ign http://ie.archive.ubuntu.com intrepid/universe Translation-en_IE 
Ign http://ie.archive.ubuntu.com intrepid/multiverse Translation-en_IE
Get:1 http://ie.archive.ubuntu.com intrepid-updates Release.gpg [189B]
Ign http://ie.archive.ubuntu.com intrepid-updates/main Translation-en_IE
Ign http://ie.archive.ubuntu.com intrepid-updates/restricted Translation-en_IE
Ign http://ie.archive.ubuntu.com intrepid-updates/universe Translation-en_IE
Ign http://ie.archive.ubuntu.com intrepid-updates/multiverse Translation-en_IE
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_IE
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_IE
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_IE
Get:2 http://packages.medibuntu.org intrepid Release.gpg [197B]
Ign http://packages.medibuntu.org intrepid/free Translation-en_IE    
Hit http://ie.archive.ubuntu.com intrepid Release                    
Hit http://ie.archive.ubuntu.com intrepid-updates Release            
Hit http://security.ubuntu.com intrepid-security Release             
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_IE
Hit http://packages.medibuntu.org intrepid Release                   
Hit http://ie.archive.ubuntu.com intrepid/main Packages
Hit http://ie.archive.ubuntu.com intrepid/restricted Packages       
Hit http://ie.archive.ubuntu.com intrepid/main Sources               
Hit http://ie.archive.ubuntu.com intrepid/restricted Sources         
Hit http://ie.archive.ubuntu.com intrepid/universe Packages          
Hit http://ie.archive.ubuntu.com intrepid/universe Sources           
Hit http://security.ubuntu.com intrepid-security/main Packages       
Hit http://ie.archive.ubuntu.com intrepid/multiverse Packages        
Hit http://ie.archive.ubuntu.com intrepid/multiverse Sources
Hit http://ie.archive.ubuntu.com intrepid-updates/main Packages
Hit http://ie.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://ie.archive.ubuntu.com intrepid-updates/main Sources
Hit http://ie.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://packages.medibuntu.org intrepid/free Packages
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://ie.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://ie.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://ie.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://ie.archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://packages.medibuntu.org intrepid/non-free Packages
Fetched 386B in 0s (697B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
root@niamh-laptop:/home/niamh# 
```

---

### Post by Berserker v7 on 2009-03-15
ok copy/paste the following commands in order....

1.    pkill update-manager
2.    sudo dpkg --configure -a
             #note that there is no space in --configure
3.    sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 skype

---

### Post by ni ni on 2009-03-15
i ran those commands.

it now says i have Broken Dependencies.
[IMG]http://www.facebook.com/photo.php?pid=1612205&l=efbb77d153&id=600738588[/IMG]

---

### Post by ni ni on 2009-03-15
oh, i attached an image of my error message but it isn't showing.

it's here [http://www.facebook.com/photo.php?pid=1612205&l=efbb77d153&id=600738588](http://www.facebook.com/photo.php?pid=1612205&l=efbb77d153&id=600738588)

---

### Post by ni ni on 2009-03-15
I can't get my firefox plugins either: I get the following

 [http://www.facebook.com/photo.php?pid=1612321&l=8d4e600483&id=600738588](http://www.facebook.com/photo.php?pid=1612321&l=8d4e600483&id=600738588)


(sorry about the facebook but it's the only way i can seem to link my images)

---

### Post by Berserker v7 on 2009-03-15
I beleive, issuing the command "sudo apt-get install -f", as shown in one of the images you posted show, should solve all your problems. it will resolve all the broken dependencies. you might use the "pkill update-manager" command if you get the "unable to lock..." error...

---

### Post by ni ni on 2009-03-15
I get :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
niamh@niamh-laptop:~$

---

### Post by konqueror7 on 2009-03-15
in the terminal, type:
```
sudo dpkg --configure -a
```

(be sure to close any running installation managers;))

---

