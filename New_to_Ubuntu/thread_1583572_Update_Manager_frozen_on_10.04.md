---
title: "Update Manager frozen on 10.04"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by Asteria on 2010-09-28
So every time I try to use Update Manager, it freezes. I've tried using the terminal commands to update, but it always kicks back a few things, saying it can't update them. What should I try to help get my Update Manager working again? Layman's terms, please, I'm new to Linux.

---

### Post by JohnHeikkila on 2010-09-28
You should try Synaptic.
System-->Administration-->Synaptic Package Manager.

---

### Post by Soul-Sing on 2010-09-28
> but it always kicks back a few things, saying it can't update them
what is the exact errormessage?

---

### Post by Asteria on 2010-09-28
What should I do in Synaptic?

When I use sudo apt-get update in terminal, I get:

sudo: unable to resolve host World Domination
Get:1 [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release.gpg [197B]
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) lucid/non-free Translation-en_US
Get:2 [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release [3,445B]                    
Ign [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release                               
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid/non-free Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/rawtherapee/ppa/ubuntu/](http://ppa.launchpad.net/rawtherapee/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/unbuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/unbuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [44.7kB]              
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                          
  404  Not Found
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [314kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [3,240B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [122kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [1,443B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [121kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [48.6kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [3,773B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [1,739B]
Fetched 661kB in 3s (189kB/s)
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: Failed to fetch [http://ppa.launchpad.net/unbuntu-wine/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/unbuntu-wine/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by JohnHeikkila on 2010-09-28
If you ask me, you should remove the links from the Software Sources (System-->Administration-->Software Sources) that get a 404.

With the key error, do this:
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 54422A4B98AB5139
```
then:
```
gpg --export --armor 54422A4B98AB5139 | sudo apt-key add -
```

---

### Post by Asteria on 2010-10-02
So, nothing under 'Administration' will even open. I never get an error, it just says it's loading and then nothing happens. Have I completely ruined my system?

---

### Post by Asteria on 2010-10-05
Anyone have any ideas? Help!

---

### Post by NightwishFan on 2010-10-05
If it never opens perhaps you are typing the password wrong (though perhaps not). Check the caps lock. Also run this in a terminal to see if there are any errors:
```
gksu /usr/bin/software-properties-gtk
```

You can manually edit the sources by running:
```
sudo nano /etc/apt/sources.list
```

Be careful what you edit in there. Perhaps just remove the offending lines that give a 404.

---

### Post by Asteria on 2010-10-06
Okay, so I can't do anything in synaptic or software sources and update manager just freezes. My whole computer also seems significantly slower and everything, too. I've tried to run those codes and stuff in terminal, but nothing seems to be working. Do you think I have a virus or something?

---

### Post by NightwishFan on 2010-10-06
No, something you did using root powers messed something up. I do not have time to help at the moment though, I will check back later.

---

### Post by Bulletproofmask on 2010-10-07
I don't know what could have caused that, but if you post your command line history maybe someone here will see something.

---

### Post by Asteria on 2010-10-07
Where can I find my command line history?

---

### Post by Bulletproofmask on 2010-10-07
> **Asteria said:**
> Where can I find my command line history?

Just type

```
history > clhistory
```This puts your command line history into a file called clhistory which is created in the directory you are currently working in.  Open this file with any text editor(such as gedit) and you can copy and paste it here.  If this problem is occurring because of something you did in the terminal, hopefully someone here will be able to spot it.

---

### Post by Soul-Sing on 2010-10-07
i thought [COLOR="Red"].bash_history[/COLOR] in your home map

/home ctrl+h===> hidden folders

---

### Post by corcomp84 on 2010-10-07
try getting a current live CD from Ubuntu and try updating using that. disconnect from the internet and update with just the cd.. It sounds like you added another universe and its not working right, (can you get into software sources?) then if that doesn't work reboot the computer and at the grub loading stage use a different version normally there is more than one, dont use the recovery one though.. I remember having the same problem I think it was because I updated from 9.10 to 10.04 using the internet not a live CD which is always a bad idea..

---

### Post by Bulletproofmask on 2010-10-07
> **leoquant said:**
> i thought [COLOR=Red].bash_history[/COLOR] in your home map

/home ctrl+h===> hidden folders

So I guess that's where it pulls your history from, never noticed it before.

---

### Post by drs305 on 2010-10-07
In Post #4, the code starts off with:
> 
[COLOR="Red"]sudo: unable to resolve host World Domination[/COLOR]
Get:1 [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release.gpg [197B]
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) lucid/non-free Translation-en_US
 

Do you still have the use of "sudo"? If so, open /etc/hosts for editing and post the results to see where "world domination" is coming from.
```
gksu gedit /etc/hosts
```

---

