---
title: "Installed TweetDeck now I have a Broken package error"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by StutteringJohnSmith on 2011-02-06
Installed TweetDeck now I have a Broken package error:

---

### Post by robsoles on 2011-02-06
In case it hasn't been said: Welcome to UF.


You will have to be more specific about how the package manager is broken before anybody will be able to post anything all that brilliantly helpful to fix it for you ;)


Please copy and paste your terminal's response to```
sudo apt-get update
```(Sometimes package manager is broken in such a way that the error is indicated in output of this command...)

---

### Post by StutteringJohnSmith on 2011-02-06
sorry, i am new to this


Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_US              
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/mixxx/mixxx/ubuntu/](http://ppa.launchpad.net/mixxx/mixxx/ubuntu/) lucid/main Translation-en_US  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                               
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [761B]               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Fetched 2,305B in 1s (2,167B/s)
Reading package lists... Done
[john@sabrina2011:~] $

---

### Post by robsoles on 2011-02-07
OK, no errors reported.

Tempting to have you do any available updates```
sudo apt-get upgrade
```

What will probably cut to the chase a bit quicker though, will be if you say why you think your package manager is broken - please tell us what action you take that then reports any errors, or if no errors are reported then what is the failure you observe?

Screenshots of error message boxes attached to posts aren't against the rules - if you can't select text in a window to copy and paste here then screenshots are a workaround can save you notating and typing :)

---

### Post by techunit on 2011-02-07
> **robsoles said:**
> OK, no errors reported.

Tempting to have you do any available updates```
sudo apt-get upgrade
```

What will probably cut to the chase a bit quicker though, will be if you say why you think your package manager is broken - please tell us what action you take that then reports any errors, or if no errors are reported then what is the failure you observe?

Screenshots of error message boxes attached to posts aren't against the rules - if you can't select text in a window to copy and paste here then screenshots are a workaround can save you notating and typing :)
I remember having this same problem. I can't remember how I fixed it, but I think I actually tried upgrading my packages only to have Adobe Air Removed. The problem was solved but I didn't have tweetdeck anymore. I think if you add the Adobe Air PPA it might help. However It might have been the other way around and the PPA had been the possible solution and upgrading my packages was what solved it.

Any way food for thought. Good Luck hope this helps.

---

### Post by PACSFerret on 2011-02-08
Happened to me also - for a couple of AIR apps including TweetDeck.  Doing recommended "apt-get install -f" to fix package manager but first thing it does is uninstall the AIR app/package.

I fixed it by copying the app folder (/opt/TweetDeck tp /opt/TD in my case) before apt-get -f install, and then creating a new launcher for the new location ( /opt/TD/bin/TweetDeck with the icon at /opt/TD/share/icons/TweetDeck_128.png)

---

