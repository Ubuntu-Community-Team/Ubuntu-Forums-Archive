---
title: "Flash"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by v.mccann on 2009-11-16
Hi, 

I'm a complete novice at this, and I'm having some trouble with flash. Basically, it quit working. I've tried to reinstall it, but I get an error message saying the archive cannot be found. When I access some webpages, a message appears at the top of the firefox window saying that addition pluggings: adobe flash, swfdec swf and gnash need to be installed, but I get the same error message when I try to install them. Also, synaptic package manager doesn't open. 

I know that's probably not all the information needed to address the problem. If anyone has any ideas let me know what else you need to know. I upgraded to 9.1 a few weeks ago and haven't had any problems until now. 

Thanks.

---

### Post by garvinrick4 on 2009-11-16
sudo apt-get remove flashplugin-nonfree

sudo apt-get clean

sudo apt-get install flashplugin-nonfree

sudo apt-get update


Open a Terminal in Applications - accessories - terminal

type these commands one at a time and press enter- will ask for password press enter.

---

### Post by garvinrick4 on 2009-11-16
If you can get to Add and remove programs in 
Applications Install   ubuntu-restricted-extras   

It has quite a few packages you will need. If you have not installed already.

---

### Post by v.mccann on 2009-11-16
Thanks, 

when I typed sudo apt-get remove flashplugin-nonfree and entered my password, I got: "E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it."

---

### Post by v.mccann on 2009-11-16
I tried to install restricted extras. I got:

 "E:I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.:"

From terminal I got: 

"E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it."

---

### Post by garvinrick4 on 2009-11-16
sudo apt-get -f install




This code will attempt to fix broken packages.

When you can get to Software Sources. in Administation.

Go to ubuntu software tab.  To Download from: click on tab on right choose other.

Now pick out another mirror. Click select best server or pick one yourself. Do not know
what country you are in.

Now when you close it will reload new repositories.

Go to a Terminal Code:  sudo apt-get update

Now you have new mirror or server.

---

### Post by garvinrick4 on 2009-11-16
Once you get new repositories start over.

sudo apt-get remove flashplugin-nonfree

sudo apt-get clean

sudo apt-get install flashplugin-nonfree

sudo apt-get update

sudo apt-get install ubuntu-restricted-extras

sudo apt-get update


I do not know if you have the ubuntu-restricted-extras
you can actually just install them at the code:  sudo apt-get install flashplugin-nonfree

As long as you get them all. The ubuntu-restricted-extras include flashplayer
and a lot of codec's to play video's of all nature.

---

### Post by v.mccann on 2009-11-16
Thanks for all your help,

I'm still getting: 

"The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it."

I tried going through the process to change mirrors twice.

---

### Post by v.mccann on 2009-11-16
I tried to install restricted extras again. I got:

"E:I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.:"

---

### Post by garvinrick4 on 2009-11-16
Did it reload to new mirror.

sudo gedit /etc/apt/sources.list

If you know how to copy and paste do it in a Reply box so I can see what they are.

Oh there will be a text editor open called gedit with all your repositories in it. That is
what I need copy and pasted.

---

### Post by v.mccann on 2009-11-17
It looks like it's reloading from the new mirror, but some of the files say failed, rather than done. 

Heres the gedit: 

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse

---

### Post by sandy8925 on 2009-11-17
You're supposed to do sudo apt-get update before you install. There's a guide for this stuff at the Multimedia & Video forum.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

You can also install flash by downloading it from the adobe website. Just visit [www.adobe.com](www.adobe.com) and click on download flash player. Download the .deb for Ubuntu 8.04+ version. Dunno if it works for Karmic though.

---

### Post by v.mccann on 2009-11-17
Um, before I install what?

I tried to install from the adobe site. It says it can not open. The package might be corrupted or I do not have permission to open it.

---

### Post by 3rdalbum on 2009-11-17
It can't find the archive for flashplugin-installer... So download the package from [http://packages.ubuntu.com](http://packages.ubuntu.com) and put it into /var/cache/apt/archives.

For future reference, if a program starts playing up you should first remove its settings file - they are in a hidden directory in your home directory.

---

### Post by v.mccann on 2009-11-17
It says I don't have permission to move the file to that location.

---

### Post by garvinrick4 on 2009-11-17
I do not believe I saw this included in your list.
Go to software sources again. The Other Software tap.
MAKE SURE disabled on upgrade to karmic and disabled on to
upgrade to karmic free non-free are checked.

Okay hit ADD: Then copy and paste this line below into APT line:
Click add source.  Close it will add. The go to Terminal and do.
 Code:    sudo apt-get update



deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

Now clean and install will work this time. There is always a fix.
Let me no.

---

### Post by v.mccann on 2009-11-17
That did it. Thanks.

---

### Post by Dportner on 2009-12-01
kay so im getting this problem too.... and iv tried all the steps mentiond in this thread...but it still wont let me un install.

wont let me install or reinstall flash.
wont let me install ubuntu restricted extras.
keep gettin the saammmeee message..E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

---

### Post by sandyd on 2009-12-01
> **Dportner said:**
> kay so im getting this problem too.... and iv tried all the steps mentiond in this thread...but it still wont let me un install.

wont let me install or reinstall flash.
wont let me install ubuntu restricted extras.
keep gettin the saammmeee message..E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
i am the queen of posting bugs ;)
[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/412944](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/412944)

```

sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin //to make sure its really gone.
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
tar xvfz install_flash_player_10_linux.tar.gz
sudo mv *.so /usr/lib/firefox/plugins/
rm install_flash_player_10_linux.tar.gz

```

---

### Post by Dportner on 2009-12-01
got this:

dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 198895 files and directories currently installed.)
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

:S

---

### Post by sandyd on 2009-12-01
> **Dportner said:**
> got this:

dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 198895 files and directories currently installed.)
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

:S
fixed. the first line was actually a test (sorry, i got a bit too curious......)

---

### Post by Dportner on 2009-12-01
this is what i got:

dylan@dylan-laptop:~$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
rm: cannot remove `/var/lib/dpkg/info/adobe-flashplugin.prerm': No such file or directory
dylan@dylan-laptop:~$ wget -c [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
--2009-12-01 21:44:02--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
Resolving fpdownload.macromedia.com... 96.7.202.70
Connecting to fpdownload.macromedia.com|96.7.202.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4044751 (3.9M) [application/x-gzip]
Saving to: `install_flash_player_10_linux.tar.gz'

100%[======================================>] 4,044,751    419K/s   in 8.0s    

2009-12-01 21:44:10 (493 KB/s) - `install_flash_player_10_linux.tar.gz' saved [4044751/4044751]

dylan@dylan-laptop:~$ tar xvfz install_flash_player_10_linux.tar.gz
libflashplayer.so
dylan@dylan-laptop:~$ sudo mv *.so /usr/lib/firefox/plugins/
dylan@dylan-laptop:~$ rm install_flash_player_10_linux.tar.gz


but i dont think it did anything.... it still says the same things

---

### Post by sandyd on 2009-12-01
> **Dportner said:**
> this is what i got:

dylan@dylan-laptop:~$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
rm: cannot remove `/var/lib/dpkg/info/adobe-flashplugin.prerm': No such file or directory
dylan@dylan-laptop:~$ wget -c [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
--2009-12-01 21:44:02--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
Resolving fpdownload.macromedia.com... 96.7.202.70
Connecting to fpdownload.macromedia.com|96.7.202.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4044751 (3.9M) [application/x-gzip]
Saving to: `install_flash_player_10_linux.tar.gz'

100%[======================================>] 4,044,751    419K/s   in 8.0s    

2009-12-01 21:44:10 (493 KB/s) - `install_flash_player_10_linux.tar.gz' saved [4044751/4044751]

dylan@dylan-laptop:~$ tar xvfz install_flash_player_10_linux.tar.gz
libflashplayer.so
dylan@dylan-laptop:~$ sudo mv *.so /usr/lib/firefox/plugins/
dylan@dylan-laptop:~$ rm install_flash_player_10_linux.tar.gz


but i dont think it did anything.... it still says the same things
doesn't matter now. im sure your flash works.
and although im pretty sure it works (those were actually the manual flash installation steps)
ill spare you the pain of performing a manual flash upgrade when 10.1 is out......
```

sudo echo "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner" >> /etc/apt/sources.list
sudo apt-get update
sudo apt-get clean
sudo rm /usr/lib/firefox/plugins/libflash*so
sudo apt-get install flashplugin-installer
```

---

### Post by Dportner on 2009-12-01
sooo il never be able to start package manager ever again? :S

cuz it doesnt let me do that....
when i try to launch it i get

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by sandyd on 2009-12-01
> **Dportner said:**
> sooo il never be able to start package manager ever again? :S

cuz it doesnt let me do that....
when i try to launch it i get

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

sudo rm /var/lib/dpkg/info/adobe-flashplugin*
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin

```

---

### Post by Dportner on 2009-12-01
ugh... this is so frustratin :( nothing is working...

i get this
dylan@dylan-laptop:~$ sudo echo "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner" >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
dylan@dylan-laptop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic Release.gpg
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/multiverse Packages
Reading package lists... Done
dylan@dylan-laptop:~$ sudo apt-get clean
dylan@dylan-laptop:~$ sudo rm /usr/lib/firefox/plugins/libflash*so
dylan@dylan-laptop:~$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.



still get the exact same thing at the end... "E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it."

---

### Post by Dportner on 2009-12-01
thank you omg!!!!!!
:]
this work:
sudo rm /var/lib/dpkg/info/adobe-flashplugin*
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin

---

### Post by sandyd on 2009-12-01
finally!
adobe is REALLY getting on my nerves now.
they apparently did something wrong with the package they provide.......

---

