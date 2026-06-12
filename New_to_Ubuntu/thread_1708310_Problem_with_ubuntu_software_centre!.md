---
title: "Problem with ubuntu software centre!"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by vnpifhf on 2011-03-16
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

Don't know what this means and need to install some programs, help!

---

### Post by Vi3tHoneyX on 2011-03-16
> **jahangir99 said:**
> Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
**SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.**

Don't know what this means and need to install some programs, help!

What happens if you open a terminal and run? ```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by vnpifhf on 2011-03-16
jamila@jahangir-Aspire-M1610:~$ sudo apt-get install ttf-mscorefonts-installer
[sudo] password for jamila: 
jamila is not in the sudoers file.  This incident will be reported.
jamila@jahangir-Aspire-M1610:~$ 



:/

---

### Post by matt_symes on 2011-03-16
Hi

If the above post does not fix your issue, download and install the deb file manually.

```
sudo dpkg -i ...
```

[http://packages.ubuntu.com/lucid/ttf-mscorefonts-installer](http://packages.ubuntu.com/lucid/ttf-mscorefonts-installer)

Kind regards

---

### Post by Joshun on 2011-03-16
You must be using an account that hasn't been given root privileges (i.e a non-admin account). You need to login with an account that is set with these privileges - the first user account you set up when you installed Ubuntu should do this. Login to that account and try:
```
sudo apt-get update
``````
sudo apt-get apt-get install ttf-mscorefonts-installer
``````
sudo apt-get --reinstall install aptdaemon
```If you want to make your normal account have sudo privilges, you can change the settings on the 'admin' account (System>Administration>Users and Groups), click change under account type, tick Administration and click OK, then close it.

---

### Post by Joshun on 2011-03-16
You must be using an account that hasn't been given root privileges (i.e a non-admin account). You need to login with an account that is set with these privileges - the first user account you set up when you installed Ubuntu should do this. Login to that account and try:
```
sudo apt-get update
``````
sudo apt-get apt-get install ttf-mscorefonts-installer
``````
sudo apt-get --reinstall install aptdaemon
```If you want to make your normal account have sudo privilges, you can change the settings on the 'admin' account (System>Administration>Users and Groups), click change under account type, tick Administration and click OK, then close it.

EDIT: Sorry for the duplicate post, broadband went off.

---

### Post by vnpifhf on 2011-03-16
Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; TrueType core fonts for the Web EULA                                        
 &#9474;                                                                             
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                           
 &#9474;                                                                             
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement         
 &#9474; ("EULA") is a legal agreement between you (either an individual or a        
 &#9474; single entity) and Microsoft Corporation for the Microsoft software         
 &#9474; accompanying this EULA, which includes computer software and may include    
 &#9474; associated media, printed materials, and "on-line" or electronic            
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your        
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be      
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of        
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                            
 &#9474;                                                                             
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                               
Its giving me this blue screen but what does it mean and there are no options?

sudo apt-get --reinstall install aptdaemon

---

### Post by matt_symes on 2011-03-16
Hi

> Its giving me this blue screen but what does it mean and there are no options?

Hit the tab key and then enter to get past that screen.

Kind regards

---

### Post by vnpifhf on 2011-03-16
All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
Setting up python-aptdaemon (0.31+bzr506-0ubuntu6.1) ...
Processing triggers for python-central ...
Setting up python-aptdaemon-gtk (0.31+bzr506-0ubuntu6.1) ...
Setting up aptdaemon (0.31+bzr506-0ubuntu6.1) ...
Processing triggers for python-central ...
jamila@jahangir-Aspire-M1610:~$ 

 All is working, thanks for getting this sorted all of you! :KS
Jay :D

---

