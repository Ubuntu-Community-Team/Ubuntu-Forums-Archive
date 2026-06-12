---
title: "Network issue // no connection in apt-get"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by Oenologist on 2008-09-22
Yes. One more issue with my beloved University Network. 

From the very beginning the only working stuff were Firefox and Kadu (communicator). Unfortunately apt-get/synaptic and torrent software can't get connected.

I managed to work out Synaptic (entered proxy website in connection settings), but apt-get is still down:

> Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy/universe libmowgli1 0.6.0-1
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy-updates/universe libaudid3tag1 1.5.0-2ubuntu2~hardy1
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy/universe libcddb2 1.2.1-1
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy/main libneon27-gnutls 0.27.2-1
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy-updates/universe audacious-plugins 1.5.0-1ubuntu1.8.04.2
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy/universe libmcs1 0.4.1-2
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy-updates/universe libaudclient1 1.5.0-2ubuntu2~hardy1
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy-updates/universe audacious 1.5.0-2ubuntu2~hardy1
  Could not resolve ' wwwcache.aber.ac.uk'
Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/pool/universe/libm/libmowgli/libmowgli1_0.6.0-1_i386.deb](http://pl.archive.ubuntu.com/ubuntu/pool/universe/libm/libmowgli/libmowgli1_0.6.0-1_i386.deb)  Could not resolve ' wwwcache.aber.ac.uk'
Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/pool/universe/a/audacious/libaudid3tag1_1.5.0-2ubuntu2~hardy1_i386.deb](http://pl.archive.ubuntu.com/ubuntu/pool/universe/a/audacious/libaudid3tag1_1.5.0-2ubuntu2~hardy1_i386.deb)  Could not resolve ' wwwcache.aber.ac.uk'
Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/pool/universe/libc/libcddb/libcddb2_1.2.1-1_i386.deb](http://pl.archive.ubuntu.com/ubuntu/pool/universe/libc/libcddb/libcddb2_1.2.1-1_i386.deb)  Could not resolve ' wwwcache.aber.ac.uk'
Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/pool/main/n/neon27/libneon27-gnutls_0.27.2-1_i386.deb](http://pl.archive.ubuntu.com/ubuntu/pool/main/n/neon27/libneon27-gnutls_0.27.2-1_i386.deb)  Could not resolve ' wwwcache.aber.ac.uk'
Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/pool/universe/a/audacious-plugins/audacious-plugins_1.5.0-1ubuntu1.8.04.2_i386.deb](http://pl.archive.ubuntu.com/ubuntu/pool/universe/a/audacious-plugins/audacious-plugins_1.5.0-1ubuntu1.8.04.2_i386.deb)  Could not resolve ' wwwcache.aber.ac.uk'
Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/pool/universe/m/mcs/libmcs1_0.4.1-2_i386.deb](http://pl.archive.ubuntu.com/ubuntu/pool/universe/m/mcs/libmcs1_0.4.1-2_i386.deb)  Could not resolve ' wwwcache.aber.ac.uk'
Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/pool/universe/a/audacious/libaudclient1_1.5.0-2ubuntu2~hardy1_i386.deb](http://pl.archive.ubuntu.com/ubuntu/pool/universe/a/audacious/libaudclient1_1.5.0-2ubuntu2~hardy1_i386.deb)  Could not resolve ' wwwcache.aber.ac.uk'
Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/pool/universe/a/audacious/audacious_1.5.0-2ubuntu2~hardy1_i386.deb](http://pl.archive.ubuntu.com/ubuntu/pool/universe/a/audacious/audacious_1.5.0-2ubuntu2~hardy1_i386.deb)  Could not resolve ' wwwcache.aber.ac.uk'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


---

### Post by Bucky Ball on 2008-09-22
Check System->Admin->Software Sources and make sure you have things selected. In a terminal copy and paste this:
[B]
sudo apt-get update

[/B]Then try again. There's a message to try this last command at the end of your code. :)

---

### Post by Oenologist on 2008-09-22
I tried sudo apt-get update several times under various configs. Nothing.

Bear in mind that I'm trying to work out the connection for apt-get. It's rather not the sources fault. The system can't establish a connection. Synaptic works fine. Apt doesn't.

---

### Post by Bucky Ball on 2008-09-22
Got ya. This is the last line of the code you posted:

 > Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?so maybe --fix-missing ? What did you run to get the result of your code? Because it is saying it can't fetch archives or resolve the site it is trying to get that archive from. When you get nothing from sudo apt-get update, do you mean it just goes straight to a cursor again with no read out or do you mean you get the code you posted?

---

### Post by Oenologist on 2008-09-22
> **Bucky Ball said:**
> Got ya. This is the last line of the code you posted:

 so maybe --fix-missing ? What did you run to get the result of your code? Because it is saying it can't fetch archives or resolve the site it is trying to get that archive from. When you get nothing from sudo apt-get update, do you mean it just goes straight to a cursor again with no read out or do you mean you get the code you posted?

I think it was sudo apt-get install audacious. Whatever, here's the code:

> marcy@dell-desktop:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US        
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US  
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US    
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US  
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                          
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US            
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy Release.gpg
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy/main Translation-en_US
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy/restricted Translation-en_US
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy/universe Translation-en_US
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy/multiverse Translation-en_US
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy-updates Release.gpg
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy-updates/main Translation-en_US
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy-updates/universe Translation-en_US
  Could not resolve ' wwwcache.aber.ac.uk'
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
  Could not resolve ' wwwcache.aber.ac.uk'
Reading package lists... Done          
W: Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://pl.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://pl.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://pl.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://pl.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://pl.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://pl.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://pl.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://pl.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://pl.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://pl.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve ' wwwcache.aber.ac.uk'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve ' wwwcache.aber.ac.uk'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


---

### Post by Bucky Ball on 2008-09-22
Yep, I'd say there might be something wrong with the mirror you're using (wwwcache.aber.ac.uk) - is down or bad. Rather than a problem with apt-get. As you can see, it can't resolve the address (wwwcache.aber.ac.uk) for the archives you are requesting in the update so apt-get is attempting to do its job and indeed making a connection but the connection is being refused. As further proof of this, Synaptic is a way of running apt-get through a friendly GUI. Try one in the terminal just to make sure, maybe:

**sudo apt-get install gparted**

... if you haven't got a partition manager, or replace 'install' with 'remove' in the last command and then install it again if you have, just to make sure, or pick something from Synaptics and apt-get install it from a terminal, then remove.

In software sources, you could try changing the mirror you are attempting to download from (that server could be down) to 'Main'. Could you post the contents of:

**sudo /etc/apt/sources.list**

.. just to check. Also your machine type and version of Ubuntu. Incidentally, wwwcache.aber.ac.uk I'm guessing is a third party mirror site, which is why synaptics (using the repositories) is working and this archive site is not, perhaps. 

:)

---

### Post by Oenologist on 2008-09-23
> marcy@dell-desktop:~$ sudo apt-get install gparted
[sudo] password for marcy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  jfsutils ntfsprogs reiser4progs xfsprogs
The following NEW packages will be installed:
  gparted
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 348kB of archives.
After this operation, 2150kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  gparted
Install these packages without verification [y/N]? y
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy/main gparted 0.3.5-1ubuntu3
  Could not resolve ' wwwcache.aber.ac.uk'
Failed to fetch [http://pl.archive.ubuntu.com/ubuntu/pool/main/g/gparted/gparted_0.3.5-1ubuntu3_i386.deb](http://pl.archive.ubuntu.com/ubuntu/pool/main/g/gparted/gparted_0.3.5-1ubuntu3_i386.deb)  Could not resolve ' wwwcache.aber.ac.uk'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


As you can see, the same thing occurs. I use the same default, university proxy in Firefox (works fine) and in Synaptic. 

Here are the sources:

> deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) hardy main restricted
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras

It's definitely not the sources case, while the error occurs independently of sources contents. 

I wonder, whether there can be any other proxy address for the university network...

---

### Post by Bucky Ball on 2008-09-23
[quote=Oenologist]I wonder, whether there can be any other proxy address for the university network...[/quote]That is just what I was starting to think when I read your last post cos it sure is getting turned away somewhere. 

wwwcache.aber.ac.uk

Just dawned on me that this address is probably your University (of Aberdeen?) server refusing your request. Not really my area to comment, but like you say, another proxy setting or port could be the go. Maybe a different port number, static ip?

_** Update:*_

[http://www.cyberciti.biz/faq/linux-aptget-warning-following-packages-cannot-authenticated/](http://www.cyberciti.biz/faq/linux-aptget-warning-following-packages-cannot-authenticated/)

That might be of help. They suggest:

**sudo apt-key update**

... to update keyring.

_*Update 2*_: That might not be the main problem though as I've discovered you should still be able to download with 'y' after the warning.

**_*Update 3*_**: Okay, I have a feeling there might be a couple of issues - one with the keyring authentication and this:

[http://ubuntuforums.org/showthread.php?t=876616](http://ubuntuforums.org/showthread.php?t=876616)

The last post on page one gives workaround for your issue that might just work for you. There must be a better way though. :)

* Update: I mentioned this a few posts ago; did you try going to System->Admin->Software Sources and changing the '**download from**' location from the one you're using? Try another and see if there's a difference.

---

### Post by Oenologist on 2008-09-23
The change of location didnt' work. I've turned to direct connection instead of proxy. The result is:

> marcy@dell-desktop:~$ sudo apt-get update
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)
Err [http://apt.wicd.net](http://apt.wicd.net) hardy Release.gpg                                      
  Could not connect to apt.wicd.net:80 (208.113.186.14). - connect (111 Connection refused)
Err [http://apt.wicd.net](http://apt.wicd.net) hardy/extras Translation-en_US                         
  Could not connect to apt.wicd.net:80 (208.113.186.14). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)
Err [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
  Could not connect to download.skype.com:80 (204.9.165.83). - connect (111 Connection refused) [IP: 204.9.165.83 80]
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
  Could not connect to dl.google.com:80 (66.249.93.91). - connect (111 Connection refused) [IP: 66.249.93.91 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_US                
  Could not connect to download.skype.com:80 (204.9.165.83). - connect (111 Connection refused) [IP: 204.9.165.83 80]
Err [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                     
  Could not connect to dl.google.com:80 (66.249.93.91). - connect (111 Connection refused) [IP: 66.249.93.91 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                     
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/Release.gpg](http://wine.budgetdedicated.com/apt/dists/hardy/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg](http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg)  Could not connect to download.skype.com:80 (204.9.165.83). - connect (111 Connection refused) [IP: 204.9.165.83 80]

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/i18n/Translation-en_US.bz2](http://download.skype.com/linux/repos/debian/dists/stable/non-free/i18n/Translation-en_US.bz2)  Could not connect to download.skype.com:80 (204.9.165.83). - connect (111 Connection refused) [IP: 204.9.165.83 80]

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release.gpg](http://dl.google.com/linux/deb/dists/stable/Release.gpg)  Could not connect to dl.google.com:80 (66.249.93.91). - connect (111 Connection refused) [IP: 66.249.93.91 80]

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/non-free/i18n/Translation-en_US.bz2](http://dl.google.com/linux/deb/dists/stable/non-free/i18n/Translation-en_US.bz2)  Could not connect to dl.google.com:80 (66.249.93.91). - connect (111 Connection refused) [IP: 66.249.93.91 80]

W: Failed to fetch [http://apt.wicd.net/dists/hardy/Release.gpg](http://apt.wicd.net/dists/hardy/Release.gpg)  Could not connect to apt.wicd.net:80 (208.113.186.14). - connect (111 Connection refused)

W: Failed to fetch [http://apt.wicd.net/dists/hardy/extras/i18n/Translation-en_US.bz2](http://apt.wicd.net/dists/hardy/extras/i18n/Translation-en_US.bz2)  Could not connect to apt.wicd.net:80 (208.113.186.14). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


I think the keyrings are the minor problem here...They key is the connection, something, somewhere. A switch, a port, an IP?

---

### Post by Bucky Ball on 2008-09-23
> **Oenologist said:**
> I think the keyrings are the minor problem here...They key is the connection, something, somewhere. A switch, a port, an IP?

Totally agree, it looks like maybe something to do with port 80 perhaps. But that is a public port - open to all. You say you are going through the Uni server? Perhaps uni server not liking the port. Tried two different servers so not that.

I'm just about out of ideas for the moment but will think about it some more and get back to you if I discover anything. Let us know if you come up with anything. :(

---

### Post by pedro_orange on 2008-09-23
I've only skim read this thread, so apologies if you've done what I'm about to suggest:

First I'd try and ping the servers you're trying to resolve to, to see if you can actually reach them.

Secondly, some corporate networks actually block apt. My work one does and I have to use the direct ADSL link to get it working.

Thirdly: Maybe this thread will help: [http://ubuntuforums.org/archive/index.php/t-67958.html](http://ubuntuforums.org/archive/index.php/t-67958.html)

---

### Post by Bucky Ball on 2008-09-23
> **pedro_orange said:**
> ... some corporate networks actually block apt. 

That would explain a lot and something I was thinking about in broader terms before. I thought they might block certain known mirror or sites or servers, but they just block the command so users aren't downloading through their servers (and using space). The plot thickens but that could very well be the cause ... :-k Good lead ...

---

### Post by Oenologist on 2008-09-23
I wonder whether this problem is in any way associated with the torrent problem (also no connection, all ports closed). I'm thinking about any other application that seems to have problems with connection...

Firefox works, kadu works, Synaptic works...
Haven't tried Evolution, Skype...

Both torrent clients (Transmission and qtorrent) fail to work. 

More information about my connection is here: [http://ubuntuforums.org/showthread.php?t=926591](http://ubuntuforums.org/showthread.php?t=926591)

We've fixed the problem from that topic, though. 

Firefox needs proxy, as well as Synaptic. Kadu seems to work without it.

---

### Post by Bucky Ball on 2008-09-23
From the post you mention:

```
$cd /etc/network
$vi interfaces 
$comment auto etho <# auto etho>
```Did you change /etc/network/interfaces file to this? Post this file:

**nano /etc/network/interfaces**

If you copied and pasted it, OP has used letter 'o' instead of the number '0'. That could cause some probs I guess.

---

### Post by Oenologist on 2008-09-25
The file has the following content:

> #BEGIN

auto eth0
iface eth0 inet dhcp
wpa-driver wired
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

auto lo
iface lo inet loopback

#END


---

### Post by jmar71n on 2008-09-27
I'm at Aberystwyth also, as there is a proxy on http connections i use ftp in the sources.list so i get the latest updates, as ftp connections don't go via proxy (wwwcache.aber.ac.uk).

That may solve your problem, but in one of your original posts it says "unable to resolve wwwcache.aber.ac.uk". That suggests to me your DNS settings are incorrect, but you say other applications work... Strange.

Anyway...

Have a look at [Central Systems Info]("http://www.inf.aber.ac.uk/ns3/systems/servers/?showpageemail")

A list of archive mirrors [here]("https://launchpad.net/ubuntu/+archivemirrors")

---

### Post by Oenologist on 2009-01-02
I entered some proxy stuff into bash file - everything works fine now!

---

### Post by rudigarude on 2009-01-20
Hi,

Can you give details how you fixed this, what did you enter into the bash file?

Martin

---

### Post by Oenologist on 2009-01-25
> **rudigarude said:**
> Hi,

Can you give details how you fixed this, what did you enter into the bash file?

Martin

Sure.

http_proxy="http://your.proxy.server:8080/"

Just in the very end of the file. Although I see that in 8.10 it's easier - just apply the proxy settings throughout the whole system in System/Preferences/Network Proxy

---

