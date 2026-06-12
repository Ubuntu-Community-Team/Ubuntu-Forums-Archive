---
title: "Update Manager Error (partial upgrade)"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by Alien260 on 2009-05-07
Hello, 

Im running Ubuntu 8.10, this evening i turned on my machine and i get an error saying that 'Run a partial upgrade, to install as many updates as possible' (this is in a pop-up window)

When i press 'Partial Upgrade' it fails and says:

[HTML]Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later[/HTML]

Any help would be really appreciated. 

Regards
[COLOR="Lime"]alien[/COLOR]

---

### Post by taurus on 2009-05-07
What are the outputs of these two commands, remember to shut down the update manager first?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by danebramaged on 2009-05-07
I am running 9.04 after upgrading from 8.10 and I saw the the same thing today.  :confused:     9.04 is misbehaving on my system (starting with the upgrade itself) but that was over a week ago.  

So anyway, I just went for it.  I was hoping there would be some bug fixes for me but, sadly, no.  At least it hasn't made matters worse.

Sorry, but that's all I know.

---

### Post by Therion on 2009-05-07
It's happened to me before.  Wait a day or two and try again; most likely it will resolve itself.  

Like the message says, "This is most likely a transient problem, please try again later..."

---

### Post by danebramaged on 2009-05-07
The results are:  Lengthy!

isaac@Monolith:~$ **sudo apt-get update**
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty Release.gpg
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty/main Translation-en_US              
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty/restricted Translation-en_US        
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty/universe Translation-en_US          
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty/multiverse Translation-en_US        
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-updates Release.gpg                 
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-updates/main Translation-en_US
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-updates/restricted Translation-en_US
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-updates/universe Translation-en_US
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-updates/multiverse Translation-en_US
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-security Release.gpg      
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-security/main Translation-en_US
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-security/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                  
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US    
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-en_US
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-security/universe Translation-en_US
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-security/multiverse Translation-en_US
Get:2 [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-backports Release.gpg [189B]
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-backports/restricted Translation-en_US
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-backports/main Translation-en_US
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-backports/multiverse Translation-en_US
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-backports/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                      
Get:3 [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-proposed Release.gpg [189B]
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-proposed/restricted Translation-en_US
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-proposed/main Translation-en_US
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-proposed/multiverse Translation-en_US
Ign [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-proposed/universe Translation-en_US
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty Release                   
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-updates Release           
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-security Release          
Get:4 [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-backports Release [49.6kB]        
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release [51.2kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Get:6 [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-proposed Release [49.6kB]         
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty/main Packages                       
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty/restricted Packages
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty/main Sources      
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty/restricted Sources
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty/universe Packages                 
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty/universe Sources
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty/multiverse Packages
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty/multiverse Sources
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-updates/main Packages
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-updates/restricted Packages
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-updates/main Sources
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-updates/restricted Sources
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-updates/universe Packages
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-updates/universe Sources
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-updates/multiverse Packages
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-updates/multiverse Sources
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-security/main Packages
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-security/restricted Packages
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-security/main Sources
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-security/restricted Sources
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-security/universe Packages
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-security/universe Sources
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-security/multiverse Packages
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-security/multiverse Sources
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-backports/restricted Packages
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-backports/main Packages
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-backports/multiverse Packages
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages [112kB]
Get:8 [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-backports/universe Packages [1256B]
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-proposed/restricted Packages  
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-proposed/main Packages        
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-proposed/multiverse Packages
Hit [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) jaunty-proposed/universe Packages
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages [14B]   
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages [110kB]  
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages [13.9kB]
Fetched 389kB in 14s (26.9kB/s)                                                
Reading package lists... Done
isaac@Monolith:~$** sudo apt-get dist-upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by taurus on 2009-05-07
Are you still running Intrepid?  I don't see intrepid from the output; instead, I see a bunch of jaunty and hardy(???).

```
lsb_release -a
cat /etc/apt/sources.list
```

---

### Post by danebramaged on 2009-05-07
Alien260 is on 8.10.

I started out with Hardy, upgraded to intrepid, had no problems.  Upgraded to 9.04 and have some unresolved issues.

I was hoping this update would fix them, but no.

---

### Post by Alien260 on 2009-05-07
> **taurus said:**
> What are the outputs of these two commands, remember to shut down the update manager first?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get dist-upgrade
```


After running 

```
sudo apt-get dist-upgrade
```

it updated my system. at the moment im not getting any errors when i open the update manager (UI) .. tho there are no more updates for the system at the moment. 

Thanks for your help taurus

Cheers
[COLOR="Lime"]alien[/COLOR]

---

### Post by taurus on 2009-05-07
You should consider editing your /etc/apt/sources.list and either remove those hardy repos or at least put a # in front of them to comment them out.  It's not a good idea to mix releases in /etc/apt/sources.list because bad things could happen and would happen.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by chellrose on 2009-05-07
I got that random popup window regarding a partial upgrade, too.  In my case, I told it to upgrade what it could (don't remember the buttons any more), and it would start downloading things, then the box would just vanish.  It doesn't seem to have done any upgrades, though.

I have only jaunty repos in my /etc/apt/sources.list file.  What I don't understand is: why would I need to do apt-get dist-upgrade?  I just upgraded the distro to Jaunty last week.

Sorry for being so clueless. :D

---

### Post by gabitzu4224 on 2009-05-30
> I got that random popup window regarding a partial upgrade, too. In my case, I told it to upgrade what it could (don't remember the buttons any more), and it would start downloading things, then the box would just vanish. It doesn't seem to have done any upgrades, though.

I have only jaunty repos in my /etc/apt/sources.list file. What I don't understand is: why would I need to do apt-get dist-upgrade? I just upgraded the distro to Jaunty last week.

Sorry for being so clueless. 


I had the same problem. But I eventually fixed it, thanks to Google.
I apparently had some broken packages in need of fixing.
You have to go to the Synaptic Package Manager, go to the Edit menu and hit Fix Broken Packages, and then apply. After that the update manager went on smoothly.

---

