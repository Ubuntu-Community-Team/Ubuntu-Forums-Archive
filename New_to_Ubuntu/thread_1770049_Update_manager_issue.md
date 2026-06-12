---
title: "Update manager issue"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by Dockland on 2011-05-28
Hi all. 

I'm encountoring som problems with update manager. Getting error msg 

[IMG]http://i55.tinypic.com/ida9o2.jpg[/IMG]

And the text in the box:

```
W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/maintainer-package/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/maintainer-package/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://le-web.org/repository/dists/stable/main/binary-amd64/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Im not behind any FW and my internet connection is just fine. What can be wrong?

Best Regards Tim

---

### Post by dnairb on 2011-05-28
We need to see your sources lists, as it is very possible they are incorrect.

These are located at:

/etc/apt/sources.list - the main list
and any .list files listed in /etc/apt/sources.list.d

---

### Post by Dockland on 2011-05-28
Another error

"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

---

### Post by Dockland on 2011-05-28
> **dnairb said:**
> We need to see your sources lists, as it is very possible they are incorrect.

These are located at:

/etc/apt/sources.list - the main list
and any .list files listed in /etc/apt/sources.list.d


Ok. Heres my Source.list

```
deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty main restricted
deb-src http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty main restricted
deb http://le-web.org/repository stable main
## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty-updates main restricted
deb-src http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty universe
deb-src http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty universe
deb http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty-updates universe
deb-src http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty multiverse
deb-src http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty multiverse
deb http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty-updates multiverse
deb-src http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty-security main restricted
deb-src http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty-security main restricted
deb http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty-security universe
deb-src http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty-security universe
deb http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty-security multiverse
deb-src http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu natty main
# deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ natty-proposed restricted main multiverse universe
deb http://download.tuxfamily.org/glxdock/repository/ubuntu natty cairo-dock ## Cairo-Dock-Stable
```

---

### Post by drs305 on 2011-05-28
You can remove the first two messages (from the first post) by removing the CD from your repository list. If enabled, each time you try to update your sources it will look for the installation CD and complain if it doesn't find it. 

You can disable it via Synaptic, Settings, Repositories. It's in the first tab (Ubuntu Software) in the lower panel. You can check the other tabs as well to untick additional CD repository listings.

Added: There is currently no "http://www.le-web.org/repository/" available online. You can temporarily untick it, it's probably in the 'Other software' tab, or place a # symbol at the start of it's line in sources.list.

---

### Post by Dockland on 2011-05-28
And in Source.list.d a lot of list files, dont know what you need really. 

[IMG]http://i54.tinypic.com/n204ko.jpg[/IMG]

---

### Post by Miljet on 2011-05-28
The first two errors are because your system is looking for the cd-rom. You can correct that by going to System -> Administration -> Software Sources and removing the check beside cd-rom.

The rest of the errors are because you have entries in your /etc/apt/sources.list file that do not exist. You can edit the sources.list file by opening a terminal and entering
```
gksu gedit /etc/apt/sources.list
```
You will have to enter your login password, which will not show on the screen. Then simply place a hash (#) at the start of each line that is throwing errors. Then save the file and exit.

While you are still in the terminal, enter ```
sudo apt-get update
```

Then close the terminal and try running the Update Manager again.

---

### Post by Dockland on 2011-05-28
> **drs305 said:**
> You can remove the first two messages (from the first post) by removing the CD from your repository list. If enabled, each time you try to update your sources it will look for the installation CD and complain if it doesn't find it. 

You can disable it via Synaptic, Settings, Repositories. It's in the first tab (Ubuntu Software) in the lower panel. You can check the other tabs as well to untick additional CD repository listings.

Added: There is currently no "http://www.le-web.org/repository/" available online. You can temporarily untick it, it's probably in the 'Other software' tab, or place a # symbol at the start of it's line in sources.list.

Yes, I did that. But got error message 

"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

---

### Post by Dockland on 2011-05-28
I Did that, still same error

---

### Post by Dockland on 2011-05-28
When running sudo apt-update theres a lot of errors there aswell

```
Err http://le-web.org stable/main amd64 Packages                               
  404  Not Found
Ign http://le-web.org stable/main Translation-en_US
Ign http://le-web.org stable/main Translation-en   
Fetched 8,990 B in 22s (397 B/s)                   
W: Failed to fetch http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/maintainer-package/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/maintainer-package/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://le-web.org/repository/dists/stable/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by dnairb on 2011-05-28
In the first file, /etc/apt/sources.list, you need to remove:

```
deb http://le-web.org/repository stable main
```

as the address [http://le-web.org/repository](http://le-web.org/repository) does not exist (I have checked)

You also need to remove the following files from /etc/apt/sources.list.d/

```
elegant-gnome-ppa-natty.list
elegant-gnome-ppa-natty.list.save
```

as the elegant-gnome ppa has no entries for natty (only Lucid and Maverick: [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/))

```
maintainer-package-ppa-natty.list
maintainer-package-ppa-natty.list.save
```

as these do not exist at all for any version of Ubuntu ([http://ppa.launchpad.net/maintainer-package/ppa](http://ppa.launchpad.net/maintainer-package/ppa)). (Again, I have checked)

---

### Post by drs305 on 2011-05-28
Edit: *dnairb* did a nice job of explaining things as I was writing this. His post should cover your problems.


I hadn't given you the complete list of errors so you would still continue to get the message as long as one or more listings failed.

It appears from the message that you will also have to disable the maintainer-package and elegant-gnome ppa listings - at least until they come online. Basically you deselect any repositories which are giving you errors.

It's possible the servers are just offline. Since these aren't Ubuntu official repositories, how reliable they are I don't know. Normally if you really need to update things it's best just to disable the malfunctioning ones temporarily and then try to enable them again later.

You are also getting a 'lock' message. This is most likely due to running Synaptic or Software Center while trying to run apt-get from the command line.

---

### Post by Dockland on 2011-05-29
Thank You all. Dont know how to edit those files but i'll give it a try. 
I havent got any update for my 11.04 in nine days, is this ok?

---

### Post by Dockland on 2011-05-29
I can not edit my source.list file. Cant delete or add anything. Not in the Source.list.d folder either. Cant remove anything.

---

### Post by drs305 on 2011-05-29
> **Dockland said:**
> I can not edit my source.list file. Cant delete or add anything. Not in the Source.list.d folder either. Cant remove anything.
You may find it easier to just untick the entries in Synaptic, but if you want to manually edit the files you have to do it as root.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bad
gksu gedit /etc/apt/sources.list 
```
If an entry doesn't appear in sources.list, it may be in a separate file located in the /etc/apt/sources.list.d folder

---

### Post by dnairb on 2011-05-29
OK. you need to have sudo privileges to edit and remove these files.
For the sources.list file, in terminal run:

```
gksudo gedit /etc/apt/sources.list
```

Enter your password in the authentication box, delete the line

```
deb http://le-web.org/repository stable main
```

and save.

You can open a terminal by pressing the <CTRL><ALT><T> keys at the same time.

To delete the unwanted files, again in terminal, run:

```
sudo rm /etc/apt/sources.list.d/elegant-gnome* /etc/apt/sources.list.d/maintainer-package*
```

and enter your password (the password is not displayed when you type - this is normal)

---

### Post by Dockland on 2011-05-29
Thank You. Can I uncheck every line in this picture?

[IMG]http://i54.tinypic.com/2niskub.jpg[/IMG]

---

### Post by dnairb on 2011-05-29
Uncheck the two **maintainer-package** lines and the two **elegant-gnome** lines

---

### Post by Dockland on 2011-05-29
> **dnairb said:**
> Uncheck the two **maintainer-package** lines and the two **elegant-gnome** lines

Thank You. Did that. Got error message:

```
W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty/main/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty/multiverse/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty/restricted/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty/universe/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty-updates/main/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty-updates/restricted/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty-updates/universe/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty-security/main/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty-security/multiverse/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty-security/restricted/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty-security/universe/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty-proposed/main/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty-proposed/multiverse/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty-proposed/restricted/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, W:Failed to fetch http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/dists/natty-proposed/universe/i18n/Translation-en  Unable to connect to ftp.sunet.se:http:
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

"Check your internet connection."

---

### Post by dnairb on 2011-05-29
OK. So now the only errors relate to the server from which Synaptic is attempting to download the package information.
If you have an internet connection, you have 2 options:

1. Wait. The server may come back online soon.

2. Change the server in Synaptic-->Settings-->Repositories-->Ubuntu Software tab--> "Download from: " and choose another server.

---

### Post by Dockland on 2011-05-29
> **dnairb said:**
> OK. So now the only errors relate to the server from which Synaptic is attempting to download the package information.
If you have an internet connection, you have 2 options:

1. Wait. The server may come back online soon.

2. Change the server in Synaptic-->Settings-->Repositories-->Ubuntu Software tab--> "Download from: " and choose another server.


Yes., IT works! Thank You. 

But still no updates, for nine days now. Can that be correct?

---

### Post by dnairb on 2011-05-29
> **Dockland said:**
> Yes., IT works! Thank You. 

You're welcome.

> **Dockland said:**
> But still no updates, for nine days now. Can that be correct?

Could well be right. Don't worry, updates will come as and when needed.

---

