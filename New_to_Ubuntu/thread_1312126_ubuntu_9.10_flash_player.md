---
title: "ubuntu 9.10 flash player"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by rct096 on 2009-11-02
hey i recently downloades ubuntu 9.10 and i have been trying to instal flash player to view sites like youtube.com or simply play flash games but when i try to download the ubuntu flash version it all runs very well until its installing it at a certain point it marks an error and it wont istall any one know how to fix this i really need flash player :(
 
plzz help

THx

---

### Post by Locke_99GS on 2009-11-02
Ok, so, what command are you issuing to install flash, and what errors are being reported?

```
sudo apt-get install ubuntu-restricted-extras
``` will generally bring in most everything you'll need, including Flash.

---

### Post by unamanic on 2009-11-02
What is the exact error do you get when you try to install it?  [U]
[/U]

---

### Post by NickJones on 2009-11-02
For me it worked out of the box. I only installed yesterday, so I don't think I had to install flash. It may already have been installed.

---

### Post by stchman on 2009-11-02
For 32 bit simply do the following:

```
sudo apt-get install flashplugin-nonfree
```

For 64 bit get the 64 bit flash plugin from:

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)

Install it in your ~/.mozilla/plugins folder.

---

### Post by chaimann on 2009-11-06
I've also had a problem with Flash. I tried the two suggestions above,  and in both cases, got this response:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
```It also has Synaptic mucked up, returning the following error before closing:

```
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

---

### Post by philinux on 2009-11-06
Use syanptic. find adobe-flashplugin and mark it for complete removel. Then reinstall it.

---

### Post by iw2z on 2009-11-07
hey i also have this same problem after u tried installing adobe-flashplugin



the problem is i can't use synaptic coz it it isn't installed, and i can't install anything AT ALL, i keep getting this error no matter what i try to install or remove:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.here r my details:
after the flash installation failed, and everything seemed broken becoz flash wasn't installed properly, i tried installing it again using this command:

> sudo dpkg -i install_flash_player_10_linux.debthis gives me the following error:
> Selecting previously deselected package adobe-flashplugin.
(Reading database ... 87770 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.32.18-1 (using install_flash_player_10_linux.deb) ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing install_flash_player_10_linux.deb (--install):
 subprocess new pre-removal script returned error exit status 2
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 install_flash_player_10_linux.deb
so i tried removing it using this command:
> sudo apt-get remove adobe-flashpluginbut i get this error:
> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
so i tried this command:
> sudo aptitude remove adobe-flashpluginbut also got an error:
> Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages will be REMOVED:
  adobe-flashplugin
0 packages upgraded, 0 newly installed, 1 to remove and 24 not upgraded.
Need to get 0B of archives. After unpacking 10.4MB will be freed.
Writing extended state information... Done
dpkg: error processing adobe-flashplugin (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
so i tried this:
> sudo dpkg -r adobe-flashplugingot this error:
> dpkg: error processing adobe-flashplugin (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 adobe-flashplugin
so i tried forcing it:
> sudo dpkg -r --force-remove-reinstreq adobe-flashpluginbut still it wouldn't work:
> dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 87769 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashpluginnow as i said this is preventing the installation of anything else so this is really a show stopper, but i don't wanna go back to 9.04 (that's another 700MB to downoad), so guys what to do? help plz!

---

### Post by 3rdalbum on 2009-11-07
Get the adobe-flashplugin package from [http://packages.ubuntu.com](http://packages.ubuntu.com) (the same as what's in the repositories) and then put it into /var/cache/apt/archives. You should be able to reinstall it now using:'

```
sudo apt-get install --reinstall adobe-flashplugin
```

---

### Post by dodo7254 on 2009-11-07
having exact same problem!
btw, i couldn't figure out how to get the package from that website (i'm a **real** beginner)

---

### Post by paul_in_london on 2009-11-07
The [COLOR="Red"]adobe-flashplugin[/COLOR] package is apparently now deprecated in favour of [COLOR="Red"]flashplugin-nonfree[/COLOR]. 

Try uninstalling [COLOR="Red"]adobe-flashplugin[/COLOR] and then installing [COLOR="Red"]flashplugin-nonfree[/COLOR].

If you see the following error message when you try to install a package using **apt-get**, **aptitude** or **synaptic**:

```
E: The package **<package name>** needs to be reinstalled, but I can’t find an archive for it.
```

try the following command to remove it (taking [COLOR="Red"]adobe-flashplugin[/COLOR] as the example):

```
dpkg --remove --force-remove-reinstreq [COLOR="Red"]adobe-flashplugin[/COLOR]
``` or if the first command doesn't work:

```
sudo dpkg --purge --force-remove-reinstreq **--force-hold** [COLOR="Red"]adobe-flashplugin[/COLOR]
```

Then run:

```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install flashplugin-nonfree
```

Flash should then work.

In Karmic you can install [COLOR="Red"]flashplugin-installer[/COLOR] and [COLOR="Red"]flashplugin-nonfree[/COLOR] is described as a "transitional package that can safely be removed after you installed flashplugin-installer", so if [COLOR="Red"]flashplugin-installer[/COLOR] is available it might be better to use that.

---

### Post by vood on 2009-11-07
im having an issue with flash, when i first got ubuntu 9.04 64 bit i had an issue with flash. when i tried to watch videos with hulu the video would close after a few mins. i was about to fix this by installing 'flashplugin-installer'. since i upgraded to 9.10 ive been having issues again. this time when i open firefox and go to a site like hulu or youtube the buttons do not work. ive tried re-installing and the 'flashplugin-installer' since I'm running 64 bit the nonfree plugin will not do me any good. 

ive also tried installing 'libflashplayer.so' in '/usr/lib/mozilla/plugins/' but still no luck the problem is still there. 

i don't know what to do i am still new to using Ubuntu and i just don't know how to fix this by myself.

---

### Post by dodo7254 on 2009-11-08
on the first command its giving me :
>  requested operation requires superuser privilege
what do i do?

---

### Post by sandyd on 2009-11-08
> **vood said:**
> im having an issue with flash, when i first got ubuntu 9.04 64 bit i had an issue with flash. when i tried to watch videos with hulu the video would close after a few mins. i was about to fix this by installing 'flashplugin-installer'. since i upgraded to 9.10 ive been having issues again. this time when i open firefox and go to a site like hulu or youtube the buttons do not work. ive tried re-installing and the 'flashplugin-installer' since I'm running 64 bit the nonfree plugin will not do me any good. 

ive also tried installing 'libflashplayer.so' in '/usr/lib/mozilla/plugins/' but still no luck the problem is still there. 

i don't know what to do i am still new to using Ubuntu and i just don't know how to fix this by myself.
try```

sudo apt-get remove flashplugin-installer flashplugin-nonfree gnash swfdec
wget -c http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xvfz libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so
rm libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

oh, and the plugins still beta. might have some issues.

---

### Post by vood on 2009-11-08
i tried this and everything seems to be exactly the same. i can watch flash videos if the have an auto start function. however, i can not click anything, the weird thing is the button animation works. 

any other suggestions?
> **carlee said:**
> try```

sudo apt-get remove flashplugin-installer flashplugin-nonfree gnash swfdec
wget -c http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xvfz libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so
rm libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```oh, and the plugins still beta. might have some issues.

---

### Post by ricardopresto on 2009-11-08
> **dodo7254 said:**
> on the first command its giving me :

what do i do?

just preface the command with 'sudo'

---

### Post by bschoenbaechler on 2009-11-09
I am having the same problem and tried all the above steps as well...help!

---

### Post by bails on 2009-11-09
> **iw2z said:**
> hey i also have this same problem after u tried installing adobe-flashplugin



the problem is i can't use synaptic coz it it isn't installed, and i can't install anything AT ALL, i keep getting this error no matter what i try to install or remove:

here r my details:
after the flash installation failed, and everything seemed broken becoz flash wasn't installed properly, i tried installing it again using this command:

this gives me the following error:

so i tried removing it using this command:
but i get this error:
so i tried this command:
but also got an error:
so i tried this:
got this error:
so i tried forcing it:
but still it wouldn't work:
now as i said this is preventing the installation of anything else so this is really a show stopper, but i don't wanna go back to 9.04 (that's another 700MB to downoad), so guys what to do? help plz!
thank you for doing all that work for this... saving me a bit of time.... i hope someone finds an answer soon.

---

### Post by emacs on 2009-11-09
I too had similar problem.  I installed a fresh copy of 64-bit 9.10 onto my son's HP laptop, and found out that he could not watch some youtube videos.
I made the mistake of downloading debian package from adobe.com and attempting to install it.  I should have known better.

I don't know the implementation of dpkg/apt-get/etc. too well, but the following allowed me to remove adobe-flashplugin package:

sudo rm -f /var/lib/dpkg/info/adobe-flashplugin.*

I figured that a pre or post install script was failing which is the reason for the inability to remove the pacakge.  That is why i looked for and found these files.
Normally you should not do things like this to bypass the programs that you are supposed to use and mess with the internal files.  However none of other alternatives worked.  So use this method with caution!

---

### Post by bails on 2009-11-10
to Paul in london this is what happened when i tried what you said
> 
~$ sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin

dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 148436 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin

> ~$ sudo dpkg --purge --force-remove-reinstreq --force-hold adobe-flashplugin
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 148436 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin

> ~$ sudo aptitude update

Writing extended state information... Done
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg               
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                           
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Sources
Reading package lists... Done  

> ~$ sudo aptitude upgrade

W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages have been kept back:
  adobe-flashplugin 
The following packages will be REMOVED:
  firefox-3.0-dev{u} firefox-3.5-dev{u} libnspr4-dev{u} libnss3-dev{u} 
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common cups-ppdc cupsddk libcups2 
  libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 
12 packages upgraded, 0 newly installed, 4 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 3,183kB will be freed.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

> ~$ sudo aptitude install flashplugin-nonfree

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  flashplugin-installer{a} flashplugin-nonfree 
The following packages will be REMOVED:
  firefox-3.0-dev{u} firefox-3.5-dev{u} libnspr4-dev{u} libnss3-dev{u} 
0 packages upgraded, 2 newly installed, 4 to remove and 13 not upgraded.
Need to get 0B of archives. After unpacking 2,957kB will be freed.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

so for me at least this unfortunatly didn't fix the problem... any one have any other suggestions?

---

### Post by mac9416 on 2009-11-11
This here has worked for quite a few people...

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

Hope that helps!

---

### Post by leandromartinez98 on 2009-11-11
Why not install ubuntu-restricted-extras directly?

---

### Post by MarceloMats on 2009-11-11
Thanks mac9416, that worked perfect for me, solve the problem!!

---

### Post by dodo7254 on 2009-11-13
seems to have worked brill'! thanks a lot mac!

---

### Post by andrewandrew on 2009-11-13
I have experienced the same problem as you guys - I will give the above a try when I get home tonight.
 
I had the same problem when I tried to install Picas for Linux.

---

### Post by philinux on 2009-11-13
For 64 bit flash the following is what I do on every machine I use from a clean install. If you've installed 32 bit flash on a 64 bit machine then remove all other instances using synaptic.

Hope this helps.
1. get the plug in from adobe. [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) and save to Desktop.

2. Right click the archive and choose extract here.

3. Open the extracted folder and copy the file libflashplayer.so to ~/.mozilla/plugins
You will have to first create the plugins folder.

4. restart firefox

---

### Post by clem11388 on 2009-11-13
I fixed my problem by first trying everything tht  "iw2z" did and one of them worked for me. here is everything he tried so first start there. 

Quoting iw2z:
hey i also have this same problem after u tried installing adobe-flashplugin



the problem is i can't use synaptic coz it it isn't installed, and i can't install anything AT ALL, i keep getting this error no matter what i try to install or remove:

 	Quote:
 	 	 		 			 				Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it. 			 		 	 	 
here r my details:
after the flash installation failed, and everything seemed broken becoz flash wasn't installed properly, i tried installing it again using this command:

 	Quote:
 	 	 		 			 				sudo dpkg -i install_flash_player_10_linux.deb 			 		 	 	 
this gives me the following error:
 	Quote:
 	 	 		 			 				Selecting previously deselected package adobe-flashplugin.
(Reading database ... 87770 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.32.18-1 (using install_flash_player_10_linux.deb) ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing install_flash_player_10_linux.deb (--install):
 subprocess new pre-removal script returned error exit status 2
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 install_flash_player_10_linux.deb 			 		 	 	 
so i tried removing it using this command:
 	Quote:
 	 	 		 			 				sudo apt-get remove adobe-flashplugin 			 		 	 	 
but i get this error:
 	Quote:
 	 	 		 			 				Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it. 			 		 	 	 
so i tried this command:
 	Quote:
 	 	 		 			 				sudo aptitude remove adobe-flashplugin 			 		 	 	 
but also got an error:
 	Quote:
 	 	 		 			 				Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages will be REMOVED:
  adobe-flashplugin
0 packages upgraded, 0 newly installed, 1 to remove and 24 not upgraded.
Need to get 0B of archives. After unpacking 10.4MB will be freed.
Writing extended state information... Done
dpkg: error processing adobe-flashplugin (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done 			 		 	 	 
so i tried this:
 	Quote:
 	 	 		 			 				sudo dpkg -r adobe-flashplugin 			 		 	 	 
got this error:
 	Quote:
 	 	 		 			 				dpkg: error processing adobe-flashplugin (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 adobe-flashplugin 			 		 	 	 
so i tried forcing it:
 	Quote:
 	 	 		 			 				sudo dpkg -r --force-remove-reinstreq adobe-flashplugin 			 		 	 	 
but still it wouldn't work:
 	Quote:
 	 	 		 			 				dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 87769 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin 			 		 	 	 
now as i said this is preventing the installation of anything else so this is really a show stopper, but i don't wanna go back to 9.04 (that's another 700MB to downoad), so guys what to do? help plz!:::: End quote

All though these things didnt work for him, one of them worked for me despite the fact the the terminal and many other programs were giving me the exact same error messages so i believe it is strictly a case by case basis along with some just playing around to find what might work. after one of those seems to work i started FireFox then went to the top and clicked the tools menu and then went down the menu and seen the options called ""Manage Content Plug-ins"" this caught my eyes so i thought i would play with it. then i seen that there were many things labeled something about flash player or shock flash or something along those lines. the i clicked on them one by one and seen there was a drop down menu for each of them ((some were being difficult and only showing the drop down menu for a split second so you might have to be very quick with your mouse)) then clicked search in that menu. it came up with some things about installing so i just went along with it and did the same for all the the items labeled anythings about adobe or flash. after tht nothing i was able to install programs again and now i can watch youtube so i am assuming the problem is resolve but you will have to do your own trial and error along the way because iv only been using Linux for a week :P if i have a returning problem i will check back  and thanks for all the help guys i couldnt have done it with out these forums you all are awsome!!!

P.S. sorry for typing so much lol i just have learned that the more descriptive an explanation is the better it is for the person who reads it :)

---

### Post by presence1960 on 2009-11-13
> **NickJones said:**
> For me it worked out of the box. I only installed yesterday, so I don't think I had to install flash. It may already have been installed.

**_Flash is not installed out of the box in Ubuntu!_**

---

### Post by gwm on 2009-11-17
I had a similar problem. It turned out to be that I was missing the adobe repository in my sources.list file. Here is where I got the fix. **[http://ubuntuforums.org/showthread.php?t=1328128](http://ubuntuforums.org/showthread.php?t=1328128)**

---

### Post by EdGy28376 on 2009-11-18
Thank you Philinux- Your solution worked for me. However with Firefox 3.5 the directory you want to place the plugin is is found in /opt/firefox/plugins. You will need to have root priviledges to do copy the plugin over.

---

### Post by arnab_das on 2009-11-18
isnt it better to install ubuntu-restircted-extras package as it already has flash in it?

---

### Post by tance_bt on 2009-11-24
And i can't install flash player on my new ununtu 9.10. I het this error "Error: Dependency is not satisfiable: libnss3-dev".:sad::frown:

---

### Post by Plasma2k on 2009-12-04
Hi All,  > **tance_bt said:**
> And i can't install flash player on my new ununtu 9.10. I het this error &quot;Error: Dependency is not satisfiable: libnss3-dev&quot;.:sad::frown:

  I'm having exactly the same error when trying to install the flash player from adobe (package for ubuntu). Strange thing is that when starting the Live-CD the flash player package installation works perfectly without problems.  I found somewhere that it's a question of permissions, so I tried to rise permissions and indeed it started installing additional packages (I guess libnss3-dev + further dependencies), but then installation crashes.  After this the situation is that both package managers crash when trying to run them (one crashes immediately, the other says the cache is corrupt).  As I'm an absolute newbie I guess I wanted to reinstall ubuntu, but now during installation it shows me a crash report (!!).  Is there any (further) specific reason why the installation of the adobe flash player works with the LiveCD while it doesn't with ubuntu 9.10 installed? I wanted to try ubuntu as a replacement for Win, but at the moment it's not making my life easier... :(   Thanks for any help.  Plasma2k

---

### Post by muralinux on 2009-12-08
Hello All,
I faced the same problem after installing Ubuntu-9.10 today. Now I have the solution as follows :

1. Open System > Administration> Software Sources from the menu at the top
2. Click on Other Software and check the two options which are repositories .
This enables adobe flash player .
3. Open synaptic and search for adobe flash player and install it in the usual manner, it works. 

Muralinux

---

### Post by xrotaryguy on 2009-12-12
> **philinux said:**
> For 64 bit flash the following is what I do on every machine I use from a clean install. If you've installed 32 bit flash on a 64 bit machine then remove all other instances using synaptic.

Hope this helps.
1. get the plug in from adobe. [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) and save to Desktop.

2. Right click the archive and choose extract here.

3. Open the extracted folder and copy the file libflashplayer.so to ~/.mozilla/plugins
You will have to first create the plugins folder.

4. restart firefox
I did this and it worked. The flash player doesn't really work all that well tough. Flash games don't seem to work at all.

---

### Post by gordontytler on 2009-12-13
This also worked for me with a recently installed 9.10

> **muralinux said:**
> Hello All,
I faced the same problem after installing Ubuntu-9.10 today. Now I have the solution as follows :

1. Open System > Administration> Software Sources from the menu at the top
2. Click on Other Software and check the two options which are repositories .
This enables adobe flash player .
3. Open synaptic and search for adobe flash player and install it in the usual manner, it works. 

Muralinux

---

### Post by slakkie on 2009-12-13
Google Ubuntu flash upgrade and one of the first hits is the page you are looking for:

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

and otherwise, my own blog: [http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/](http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/)

---

### Post by rocketero on 2010-01-02
> **3rdalbum said:**
> Get the adobe-flashplugin package from [http://packages.ubuntu.com](http://packages.ubuntu.com) (the same as what's in the repositories) and then put it into /var/cache/apt/archives. You should be able to reinstall it now using:'

```
sudo apt-get install --reinstall adobe-flashplugin
```

this suggestion fixed temporarily the issue with not sound in pandora, but just like for 5 minutes, after that I lost sound again.

---

### Post by CeilingCrash on 2010-01-10
Having a similar problem, thought I'd share the solution I found.   Upgraded to 9.10, tried to install adobe flash player from adobe site (directed there from youtube, big mistake it seems.)  After that my upgrade manager kept complaining flash package was in a badly inconsistent state, and nothing could clean it (including 'Repair broken packages' in Synaptic/Edit.

I found this which worked (apologies to original author.) : 

sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree

This finally removed the bad package.  Then from Synaptic I loaded adobe-flashplugin and all was well.

---

### Post by carsonrose on 2010-01-12
> **gordontytler said:**
> This also worked for me with a recently installed 9.10


worked like a charm!!

Thanks:popcorn:

---

### Post by fractaltrip on 2010-02-10
Ok, first post of my life. I had a hard time since I'm a real beginner but I think this could save hazzle to others like me that don't know much. If this was useful, please thank, I'd love to have some first Replies. 

1 Download Flash Player from Adobe [http://get.adobe.com/es/flashplayer/](http://get.adobe.com/es/flashplayer/)    (select tar.gz for Linux)

2 Open a console. Go to the directory where was downloaded 
~$ cd /home/(YOUR USER)/Downloads

3 Copy the file into the correct directory, my file was "flash_player_10_linux.tar.gz"
~$ sudo cp install_flash_player_10_linux.tar.gz /usr/lib/mozilla/plugins/

4 Go to the file's new location
~$ cd /usr/lib/mozilla/plugins/

5 Unzip 
~$ sudo gunzip install_flash_player_10_linux.tar.gz

Restart Firefox and watch!

Thanks,

fractaltrip from Mexico!

---

### Post by mac9416 on 2010-02-10
Hey, fractaltrip,

Welcome to UbuntuForums, and congrats on your first post!

I have not tried following your instructions, but I would like to offer a suggestion. I think new users will find it easier to use 'cd ~/Downloads' than 'cd /home/(YOUR USER)/Downloads'. Both will have the same effect.

Besides that, it looks great, and hopefully others will find your instructions useful!

---

### Post by R0manus on 2010-02-18
> **mac9416 said:**
> this here has worked for quite a few people...

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # installs flashplayer the easy way
```hope that helps!

worked!!!!:p:p

---

### Post by Kryzzalid on 2010-02-18
Hi, I don't have any problem with abode flash player except for myspace. I can't listen to the music because the player doesn't even show up. I have tried most of those proposed solutions but it still the same or it crashes the windows as soon as the player is trying to load. I'm using Xubuntu 9.10 x86-64 and firefox 3.5.8. Any ideas?

---

### Post by 4ugeistr on 2010-02-18
> **mac9416 said:**
> 

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```



Worked like a charm!
Thanks a lot!

---

### Post by Kryzzalid on 2010-02-22
I found the solution to the problem:) I went to medibuntu.org and download/install w64codecs. And now myspace and other websites work great!

---

### Post by d3j452 on 2010-03-06
I've tried everything on all the pages in this thread and I still can't get
[http://www.uclick.com/client/sea/hida](http://www.uclick.com/client/sea/hida)
to display the game. So I can't play it.  :confused:
The system says that Flashplayer plugin *IS* installed

Does anyone have any luck getting this to display??


tnx, Dave

---

### Post by Liam1995 on 2010-04-18
> **rct096 said:**
> hey i recently downloades ubuntu 9.10 and i have been trying to instal flash player to view sites like youtube.com or simply play flash games but when i try to download the ubuntu flash version it all runs very well until its installing it at a certain point it marks an error and it wont istall any one know how to fix this i really need flash player :(
 
plzz help

THx
flash installs fine and works on me, but whenever i want to pause a video, the video stops straight away as normal but the audio carries on for like 1 second after.. can anyone help with this?

---

### Post by PinchedNerve on 2010-04-19
Never mind, I figured it out.....

---

