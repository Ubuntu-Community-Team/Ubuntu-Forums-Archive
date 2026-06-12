---
title: "AWN applets"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Tuxdroid on 2011-01-31
Hi

I've been looking for threads about this but none found or none i understand :(
So I have the AWN installed with an ease :p but i want some more applets. 
i downloaded awn-extras-applets_0.4.0+bzr1372-0ubuntu3.debian.tar.gz but can't instal it.
Also The one i could install socket doesn't word, it just crashes :mad:

pls some advice, a way to install the tar.gz or a download link for PPA and a way to install this way

Greets 

Tuxdroid

---

### Post by nick_goodfate on 2011-01-31
Add [this ppa]("https://launchpad.net/~awn-testing/+archive/ppa") and install awn-extras-applets using your terminal. Don't forget the "sudo apt-get update" before installation...

---

### Post by Tuxdroid on 2011-01-31
I had the site in my bookmarks but somehow i never found the way to download the PPA :s
terminal, will be some study but i can manage only need the help with the download :s

---

### Post by davidmohammed on 2011-01-31
try the following

sudo add-apt-repository  ppa:awn-testing/ppa

sudo apt-get update

sudo apt-get install awn-applets-c-core-trunk awn-applets-c-extras-trunk awn-applets-common-trunk awn-applets-python-core-trunk awn-applets-python-extras-trunk

---

### Post by Tuxdroid on 2011-01-31
tom@tom-AMILO-PI-1536:~$ sudo add-apt-repository ppa:awn-testing/ppa
[sudo] password for tom: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv B0BE17C2A0C914F086B7B8327D2C7A23BF810CD5
gpg: requesting key BF810CD5 from hkp server keyserver.ubuntu.com
gpg: key BF810CD5: public key "Launchpad PPA for Awn Testing Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
tom@tom-AMILO-PI-1536:~$ sudo apt-get update
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Genegeerd [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en        
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg               
Genegeerd [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Genegeerd [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-nl
Genegeerd [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-nl        
Genegeerd [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                        
Genegeerd [http://ppa.launchpad.net/awn-core/ppa/ubuntu/](http://ppa.launchpad.net/awn-core/ppa/ubuntu/) maverick/main Translation-en
Genegeerd [http://ppa.launchpad.net/awn-core/ppa/ubuntu/](http://ppa.launchpad.net/awn-core/ppa/ubuntu/) maverick/main Translation-nl
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                              
Genegeerd [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Genegeerd [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-nl
Genegeerd [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Genegeerd [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-nl
Genegeerd [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Genegeerd [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-nl
Ophalen:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                 
Genegeerd [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/) maverick/main Translation-en
Genegeerd [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/) maverick/main Translation-nl
Genegeerd [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                            
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                   
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick Release.gpg                      
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick/main Translation-en    
Geraakt [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick/main Translation-nl      
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Geraakt [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-nl
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ophalen:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9753B]                    
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                         
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources              
Geraakt [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-nl
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Geraakt [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick/universe Translation-nl  
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick-updates Release.gpg              
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                   
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources        
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources          
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources        
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages        
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages  
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages    
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages  
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-nl
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Genegeerd [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Genegeerd [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-nl
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-nl
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Genegeerd [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-nl
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick Release
Ophalen:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [2258B]               
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick-updates Release                  
Ophalen:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [7423B]         
Genegeerd [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                       
Genegeerd [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick/main Sources                     
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick/restricted Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick/universe Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick/multiverse Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick/main i386 Packages
Fout [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources        
  404  Not Found
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick/restricted i386 Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick/universe i386 Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick/multiverse i386 Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick-updates/main Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick-updates/restricted Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick-updates/universe Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick-updates/multiverse Sources
Fout [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick-updates/main i386 Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick-updates/universe i386 Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
19,8kB opgehaald in 0s (35,7kB/s)
W: Ophalen van [http://ppa.launchpad.net/awn-core/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/awn-core/ppa/ubuntu/dists/maverick/main/source/Sources.gz) is mislukt  404  Not Found

W: Ophalen van [http://ppa.launchpad.net/awn-core/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/awn-core/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz) is mislukt  404  Not Found

E: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.
E: Kon vergrendeling /var/lib/dpkg/lock niet verkrijgen - open (11: Resource temporarily unavailable)
E: Kan de beheersmap (/var/lib/dpkg/) niet vergrendelen. Is deze in gebruik door een ander proces?
tom@tom-AMILO-PI-1536:~$ sudo apt-get install awn-applets-c-core-trunk awn-applets-c-extras-trunk awn-applets-common-trunk awn-applets-python-core-trunk awn-applets-python-extras-trunk
E: Kon vergrendeling /var/lib/dpkg/lock niet verkrijgen - open (11: Resource temporarily unavailable)
E: Kan de beheersmap (/var/lib/dpkg/) niet vergrendelen. Is deze in gebruik door een ander proces?


tried and failed :s

---

### Post by davidmohammed on 2011-01-31
please close down both update manager and synaptic manager - one/both of these are running.

---

### Post by Tuxdroid on 2011-01-31
indeed synaptic, srry, i though i would be less noob

---

### Post by Tuxdroid on 2011-01-31
ok everthing has been installed but nothing changed :s

---

### Post by davidmohammed on 2011-01-31
... you have rebooted haven't you?

---

### Post by davidmohammed on 2011-01-31
...

and you have installed version 0.4.1 of awn?

sudo apt-get install avant-window-navigator-trunk

---

### Post by Tuxdroid on 2011-01-31
idd 0.4.1 is installed, only have ubuntu for 3 days so normally everything is up to date :p

---

### Post by nick_goodfate on 2011-01-31
try "sudo apt-get upgrade" in terminal. This will upgrade any app you use to the latest version.

---

### Post by Frogs Hair on 2011-01-31
To use the Awn ppa you must purge the current version of Awn . see the instructions at the link.[http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html](http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html)

---

### Post by Tuxdroid on 2011-02-02
thx frogs hair, the manual helped a lot :p, solved

---

### Post by Frogs Hair on 2011-02-02
Your Welcome

Instructions are great when you can find them.

---

### Post by Tuxdroid on 2011-02-04
yeah idd, luckily all web-ip's are up, no more sites, till they start up the next :s

---

