---
title: "Help with Nautilus"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by lsk3993 on 2010-06-10
Hi,
I need some help because I'm not sure what I've done. I think I've broken Nautilus :P

Here's what happened: I found out about Nautilus Elementary which seemed to be a good upgrade for the current Nautilus. Using this website: [http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html](http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html)
I used this code to install Nautilus
```

sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
sudo apt-get update && sudo apt-get upgrade
nautilus -q #restarts nautilus

```After the lines in terminal about the sources and everything I get:
> The following packages will be upgraded:
  libnautilus-extension1 nautilus nautilus-data
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,004kB of archives.
After this operation, 209kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
I'm guessing that means it didn't work and now Nautilus looks like this for me:
[IMG]http://imgur.com/La8Lv.png[/IMG]
(Note the arrow thing is now broken)

So basically I want to know how to fix this and/or the correct way of installing Nautilus Elementary

Thanks in advance :)

---

### Post by Peter09 on 2010-06-10
Where did the Abort line come from, did you get nothing inbetween, have you tried it again to see if it works?

---

### Post by lsk3993 on 2010-06-10
> **Peter09 said:**
> Where did the Abort line come from, did you get nothing inbetween, have you tried it again to see if it works?
I did try it again, it gave me the same thing, and here's exactly what happened:
> Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg                  
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) lucid/main Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) lucid/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libnautilus-extension1 nautilus nautilus-data
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,004kB of archives.
After this operation, 209kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.


---

### Post by Peter09 on 2010-06-10
Sanity Check, try a Captial 'Y' when you answer the Y/n question.

---

### Post by lsk3993 on 2010-06-10
> **Peter09 said:**
> Sanity Check, try a Captial 'Y' when you answer the Y/n question.
Still does the same thing, not gonna post the whole thing again though:
```
After this operation, 209kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
```

---

### Post by inameiname on 2010-06-10
This happens sometimes when you run a string of commands in the terminal. Try to separate them:

sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa 

...then when it's done...

sudo apt-get update && sudo apt-get upgrade

...and finally...

nautilus -q #restarts nautilus

Then open up nautilus and it should work just fine.


OR since you've already added the nautilus-elementary repo already, just open up Update Manager and update it that way.

---

### Post by lsk3993 on 2010-06-10
> **inameiname said:**
> This happens sometimes when you run a string of commands in the terminal. Try to separate them:

sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa 

...then when it's done...

sudo apt-get update && sudo apt-get upgrade

...and finally...

nautilus -q #restarts nautilus

Then open up nautilus and it should work just fine.
Ah thanks, that fixed it :)

---

### Post by inameiname on 2010-06-10
Cool. Enjoy nautilus-elementary. It rocks. I've used it for months now. I'll never go back.

PS....Be sure to also get that breadcrumbs hack also mentioned on WebUpd8, which will give you the pretty breadcrumb look for all themes.

---

