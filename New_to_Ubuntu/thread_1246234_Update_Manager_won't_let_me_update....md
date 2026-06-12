---
title: "Update Manager won't let me update..."
date: 2009-08-21
forum: New to Ubuntu
---

### Post by TCWriter on 2009-08-21
This is likely a wholly embarrassingly simple question, but a while ago I installed the UbuntuOne client. Shortly thereafter, every time the Update Manager runs it shows an UbuntuOne update in its list of updates, but won't let me click the check box.

The same is true of the Brasero software; an update appears in the list, but I can't click the check box and update it. 

How can I get my UbuntuOne and Brasero packages updated (or at least off the list)?

---

### Post by linux6994 on 2009-08-21
How about going in to the terminal shell and doing update via apt

sudo apt-get update
sudo apt-get upgrade

---

### Post by TCWriter on 2009-08-21
> **linux6994 said:**
> How about going in to the terminal shell and doing update via apt

sudo apt-get update
sudo apt-get upgrade

Not so good. Running the update command returns a long list of stuff (pasted at bottom of post to save space).

Running the Upgrade command returns:

[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  brasero ubuntuone-client
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.[/INDENT]

They're still there, and still grayed out. I can live with them being there, but I'm concerned that I'm not getting the latest version of UbuntuOne's client.



******
Update command output:

Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg                         
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_US              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Reading package lists... Done

---

### Post by tarps87 on 2009-08-21
It is possible that both UbuntuOne and Brasero have an updated version in the repo but some of thier dependicyies are not.
E.g
Say Brasero 2.4 depends apon CD Reader 2.6 but the latest version in the Ubuntu repos is CD Reader 2.5 it will not be able to update.

This should short its self out.

```
sudo apt-get -V upgrade
```
Should show more detail

---

### Post by TCWriter on 2009-08-21
> **tarps87 said:**
> It is possible that both UbuntuOne and Brasero have an updated version in the repo but some of thier dependicyies are not.
E.g
Say Brasero 2.4 depends apon CD Reader 2.6 but the latest version in the Ubuntu repos is CD Reader 2.5 it will not be able to update.

This should short its self out.

```
sudo apt-get -V upgrade
```
Should show more detail

This is what I get:

[INDENT]The following packages have been kept back:
   brasero (0.8.2-0ubuntu1 => 2.26.1-0ubuntu1)
   ubuntuone-client (0.90.2.1+r55-0ubuntu1~ppa1~jaunty => 0.92.0+r163-0ubuntu1~ppa1~jaunty)[/INDENT]

The Brasero package has been in the list for quite a while, and the UbuntuOne upgrade has been there for a couple weeks, so it doesn't appear to be sorting itself out. 

I wonder if an uninstall/reinstall wouldn't help.

---

### Post by Cheesemill on 2009-08-21
What does
```
sudo apt-get install brasero ubuntuone-client

```give you as output?

---

### Post by TCWriter on 2009-08-21
> **Cheesemill said:**
> What does
```
sudo apt-get install brasero ubuntuone-client

```give you as output?

Ahh, that did it. All seems well for now:

[INDENT]
tc@tc-desktop:~$ sudo apt-get install brasero ubuntuone-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++5 python-nautilus
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libbrasero-media0 python-ubuntuone-client python-ubuntuone-storageprotocol
Suggested packages:
  gstreamer0.10-fluendo-mp3 vcdimager
The following packages will be REMOVED:
  nautilus-cd-burner ubuntuone-storage-protocol
The following NEW packages will be installed:
  libbrasero-media0 python-ubuntuone-client python-ubuntuone-storageprotocol
The following packages will be upgraded:
  brasero ubuntuone-client
2 upgraded, 3 newly installed, 2 to remove and 0 not upgraded.
Need to get 1978kB of archives.
After this operation, 573kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libbrasero-media0 2.26.1-0ubuntu1 [212kB]
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main ubuntuone-client 0.92.0+r163-0ubuntu1~ppa1~jaunty [37.1kB]
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main python-ubuntuone-storageprotocol 0.92.0+r63-0ubuntu1~ppa1~jaunty [41.6kB]
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main python-ubuntuone-client 0.92.0+r163-0ubuntu1~ppa1~jaunty [114kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main brasero 2.26.1-0ubuntu1 [1574kB]
Fetched 1978kB in 12s (152kB/s)                                                        
(Reading database ... 199578 files and directories currently installed.)
Removing nautilus-cd-burner ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 199532 files and directories currently installed.)
Preparing to replace ubuntuone-client 0.90.2.1+r55-0ubuntu1~ppa1~jaunty (using .../ubuntuone-client_0.92.0+r163-0ubuntu1~ppa1~jaunty_all.deb) ...
Unpacking replacement ubuntuone-client ...
dpkg: warning - unable to delete old directory `/etc/xdg/ubuntuone/oauth_registration.d': Directory not empty
dpkg: warning - unable to delete old directory `/etc/xdg/ubuntuone': Directory not empty
Processing triggers for man-db ...
(Reading database ... 199431 files and directories currently installed.)
Removing ubuntuone-storage-protocol ...
Selecting previously deselected package python-ubuntuone-storageprotocol.
(Reading database ... 199408 files and directories currently installed.)
Unpacking python-ubuntuone-storageprotocol (from .../python-ubuntuone-storageprotocol_0.92.0+r63-0ubuntu1~ppa1~jaunty_all.deb) ...
Selecting previously deselected package python-ubuntuone-client.
Unpacking python-ubuntuone-client (from .../python-ubuntuone-client_0.92.0+r163-0ubuntu1~ppa1~jaunty_all.deb) ...
Selecting previously deselected package libbrasero-media0.
Unpacking libbrasero-media0 (from .../libbrasero-media0_2.26.1-0ubuntu1_amd64.deb) ...
Replacing files in old package brasero ...
Preparing to replace brasero 0.8.2-0ubuntu1 (using .../brasero_2.26.1-0ubuntu1_amd64.deb) ...
Unpacking replacement brasero ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Setting up python-ubuntuone-storageprotocol (0.92.0+r63-0ubuntu1~ppa1~jaunty) ...

Setting up python-ubuntuone-client (0.92.0+r163-0ubuntu1~ppa1~jaunty) ...
Installing new version of config file /etc/xdg/ubuntuone/syncdaemon.conf ...

Setting up ubuntuone-client (0.92.0+r163-0ubuntu1~ppa1~jaunty) ...
Setting up libbrasero-media0 (2.26.1-0ubuntu1) ...

Setting up brasero (2.26.1-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
[/INDENT]

---

### Post by TCWriter on 2009-08-21
Thanks for everyone's help. I'll try the get/install command should this happen again, though I'm certainly open to any suggestions as to how to avoid this kind of thing.

TC

---

