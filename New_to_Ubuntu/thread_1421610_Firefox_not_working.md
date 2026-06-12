---
title: "Firefox not working"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by idom on 2010-03-04
Hi 

I am using ubuntu 8.0.4 LTS version in my toshiba laptop and it was working all fine. One day I was updating my softward throught update manager and before update was over I shutdown my computer.

And after that firefox is not working. I thought that something would have gone wrong while updating firefox so I did 
apt-get remove firefox. 
And it was able to remove firefox properly. 

after that if I do apt-get install firefox
it says 

eading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 firefox: Depends: libasound2 (> 1.0.18) but 1.0.15-3ubuntu4 is to be installed
          Depends: libdbus-glib-1-2 (>= 0.78) but 0.74-2 is to be installed
          Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is to
be installed
E: Broken packages

I did 
dom-laptop:~> sudo apt-get install libasound2
Reading package lists... Done
Building dependency tree
Reading state information... Done
libasound2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

The same message is given out even with the other two packages.

Help is greatly appreciated.

idom

---

### Post by heatblazer on 2010-03-04
Sorry to disappoint you with my reply... but I gave up FF 2 months ago and completely replaced it with Google-Chrome! It`s way better, faster, multithreaded and much more flexible.... just abandon FF and use Chrome!

---

### Post by wojox on 2010-03-04
What does this do:

```
sudo apt-get dist-upgrade
```

---

### Post by bodhi.zazen on 2010-03-04
Try:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by idom on 2010-03-05
> **bodhi.zazen said:**
> Try:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Sorry guys for late reply. Your help is really appreciated. 
After the command I tried sudo apt-get install firefox and still gave the same error as my first pots. I rebooted and still the same. 



Output of your suggestions is pasted below. 

idom-laptop:~> sudo apt-get update
> [sudo] password for idom:
> Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release.gpg [189B]
> Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Translation-gu
> Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Translation-gu
> Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Translation-gu
> Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]
> Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-gu
> Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
> Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-gu
> Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]
> Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-gu
> Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Translation-gu
> Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release.gpg [189B]
> Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Translation-gu
> Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Translation-gu
> Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Translation-gu
> Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Translation-gu
> Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-gu
> Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-gu
> Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-gu
> Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
> Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-gu
> Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release [65.9kB]
> Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
> Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
> Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-gu
> Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]
> Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
> Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
> Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
> Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
> Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
>   404 Not Found [IP: 91.189.88.46 80]
> Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
>   404 Not Found [IP: 91.189.88.46 80]
> Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
>   404 Not Found [IP: 91.189.88.46 80]
> Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release [58.5kB]
> Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]
> Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
> Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
>   404 Not Found [IP: 91.189.88.46 80]
> Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [210kB]
> Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
> Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
> Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages [11.3kB]
> Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources [3314B]
> Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
> Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
> Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Packages [1178kB]
> Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
> [10.6kB]
> Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [35.7kB]
> Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [943B]
> Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [109kB]
> Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [17.3kB]
> Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
> [12.3kB]
> Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [1122B]
> Get:21 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Packages [6986B]
> Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Sources [338kB]
> Get:23 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Sources [1488B]
> Get:24 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Packages [4293kB]
> Get:25 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Packages [4293kB]
> Get:26 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Sources [1323kB]
> Get:27 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Packages [179kB]
> Get:28 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Sources [60.9kB]
> Get:29 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Packages [490kB]
> Get:30 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Packages
> [10.6kB]
> Get:31 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Sources [122kB]
> Get:32 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Sources [943B]
> Get:33 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Packages [232kB]
> Get:34 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Sources [47.5kB]
> Get:35 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Packages
> [29.3kB]
> Get:36 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Sources
> [5229B]
> Fetched 8988kB in 8min13s (18.2kB/s)
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following
> signatures couldn't be verified because the public key is not
> available: NO_PUBKEY EF4186FE247510BE
> W: Failed to fetch
> [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)
>  404 Not Found [IP: 91.189.88.46 80]
>
> W: Failed to fetch
> [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz)
>  404 Not Found [IP: 91.189.88.46 80]
>
> W: Failed to fetch
> [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz)
>  404 Not Found [IP: 91.189.88.46 80]
>
> W: Failed to fetch
> [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz)
>  404 Not Found [IP: 91.189.88.46 80]
>
> E: Some index files failed to download, they have been ignored, or old
> ones used instead.
>
idom-laptop:~> sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
 firefox-gnome-support
The following packages will be upgraded:
 cupsys cupsys-bsd cupsys-client cupsys-common
firefox-3.0-gnome-support libcupsimage2 libcupsys2
7 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 3437kB of archives.
After this operation, 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
 firefox-3.0-gnome-support
Install these packages without verification [y/N]? y
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main cupsys-common
1.3.7-1ubuntu3.8 [1144kB]
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main firefox-3.0-gnome-support
3.6.2~hg20100302r33648+nobinonly-0ubuntu1~umd1~jaunty [77.3kB]
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main libcupsys2
1.3.7-1ubuntu3.8 [175kB]
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main libcupsimage2
1.3.7-1ubuntu3.8 [49.9kB]
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main cupsys
1.3.7-1ubuntu3.8 [1865kB]
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main cupsys-bsd
1.3.7-1ubuntu3.8 [37.0kB]
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main cupsys-client
1.3.7-1ubuntu3.8 [88.5kB]
Fetched 3437kB in 2min33s (22.4kB/s)
Preconfiguring packages ...
(Reading database ... 139522 files and directories currently installed.)
Preparing to replace cupsys-common 1.3.7-1ubuntu3.6 (using
.../cupsys-common_1.3.7-1ubuntu3.8_all.deb) ...
Unpacking replacement cupsys-common ...
Preparing to replace libcupsys2 1.3.7-1ubuntu3.6 (using
.../libcupsys2_1.3.7-1ubuntu3.8_i386.deb) ...
Unpacking replacement libcupsys2 ...
Preparing to replace libcupsimage2 1.3.7-1ubuntu3.6 (using
.../libcupsimage2_1.3.7-1ubuntu3.8_i386.deb) ...
Unpacking replacement libcupsimage2 ...
Preparing to replace cupsys 1.3.7-1ubuntu3.6 (using
.../cupsys_1.3.7-1ubuntu3.8_i386.deb) ...
 * Stopping Common Unix Printing System: cupsd
                                              [ OK ]
Unpacking replacement cupsys ...
Preparing to replace cupsys-bsd 1.3.7-1ubuntu3.6 (using
.../cupsys-bsd_1.3.7-1ubuntu3.8_i386.deb) ...
Unpacking replacement cupsys-bsd ...
Preparing to replace cupsys-client 1.3.7-1ubuntu3.6 (using
.../cupsys-client_1.3.7-1ubuntu3.8_i386.deb) ...
Unpacking replacement cupsys-client ...
Preparing to replace firefox-3.0-gnome-support
3.6.2~hg20100226r33622+nobinonly-0ubuntu1~umd1~jaunty (using
.../firefox-3.0-gnome-support_3.6.2~hg20100302r33648+nobinonly-0ubuntu1~umd1~jaunty_all.deb)
...
Unpacking replacement firefox-3.0-gnome-support ...
Setting up cupsys-common (1.3.7-1ubuntu3.8) ...
Setting up libcupsys2 (1.3.7-1ubuntu3.8) ...

Setting up libcupsimage2 (1.3.7-1ubuntu3.8) ...

Setting up cupsys (1.3.7-1ubuntu3.8) ...
Reloading AppArmor profiles : done.
 * Starting Common Unix Printing System: cupsd
                                              [ OK ]

Setting up cupsys-client (1.3.7-1ubuntu3.8) ...

Setting up cupsys-bsd (1.3.7-1ubuntu3.8) ...

Setting up firefox-3.0-gnome-support
(3.6.2~hg20100302r33648+nobinonly-0ubuntu1~umd1~jaunty) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
idom-laptop:~>

---

### Post by bodhi.zazen on 2010-03-05
Not sure what error message you are referring to exactly.

Your sources appear to be a ream mess, you have multiple distros listed in there, that can often cause breakage, unless you be using pinning.

What version of Ubuntu are you using ?

I suggest you remove all other distros.

Unless you know what you are doing you should not be using hardy , edgy, and jaunty in your sources.

---

### Post by idom on 2010-03-05
> **bodhi.zazen said:**
> Not sure what error message you are referring to exactly.

Your sources appear to be a ream mess, you have multiple distros listed in there, that can often cause breakage, unless you be using pinning.

What version of Ubuntu are you using ?

I suggest you remove all other distros.

Unless you know what you are doing you should not be using hardy , edgy, and jaunty in your sources.
I am using 8.04 LTS hardy heron version
so should I run the same commands after removing jaunty and edgy.

I think I wanted to install empathy so  I added higher versions 
idom

---

### Post by idom on 2010-03-05
> **idom said:**
> I am using 8.04 LTS hardy heron version
so should I run the same commands after removing jaunty and edgy.

I think I wanted to install empathy so  I added higher versions 
idom
Hi bodhi.zazen

I am referring to error while doing 
sudo apt-get install firefox 

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
firefox: Depends: libasound2 (> 1.0.1 but 1.0.15-3ubuntu4 is to be installed
Depends: libdbus-glib-1-2 (>= 0.7 but 0.74-2 is to be installed
Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is to
be installed
E: Broken packages

This is stil the same. 

I have removed edgy and jaunty from sources.list and I am rerunning 
sudo apt-get update 
sudo apt-get dist-upgrade

will let you know once it is done
do yo have any other suggestions ? 

idom

---

### Post by idom on 2010-03-05
> **idom said:**
> Hi bodhi.zazen

I am referring to error while doing 
sudo apt-get install firefox 

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
firefox: Depends: libasound2 (> 1.0.1 but 1.0.15-3ubuntu4 is to be installed
Depends: libdbus-glib-1-2 (>= 0.7 but 0.74-2 is to be installed
Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is to
be installed
E: Broken packages

This is stil the same. 

I have removed edgy and jaunty from sources.list and I am rerunning 
sudo apt-get update 
sudo apt-get dist-upgrade

will let you know once it is done
do yo have any other suggestions ? 

idom

I ran 
sudo apt-get update 
sudo apt-get dist-upgrade

sudo apt-get install firefox

and now firefox 3.0 is up and running 

Thanks for your help. 

Now I will try to upgrade firefox to 3.6 version

idom

---

