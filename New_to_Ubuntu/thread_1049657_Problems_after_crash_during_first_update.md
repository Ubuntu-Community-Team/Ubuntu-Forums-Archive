---
title: "Problems after crash during first update"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Camillus on 2009-01-24
I installed Ubuntu 8.04 on to my laptop from a live CD yesterday and initially everything worked well. 

I then ran an update and during that process the system stopped working (specifically during the f-spot update). There was no response to either the keyboard or the mouse and after 15 minutes of no movement I powered the system off. When I rebooted Ubuntu loaded but was clearly different in appearence (the help icon and shutdown button had both changed) and none of the programs would load. 

I rebooted into diagnostic(?) mode and when offered the choice to repair damaged packages I took it. Yhis restored the appearence of the system and programs will now load. However I have now lost my wireless connection.

The system appears to recognise that I have a wireless adapter but for some reason will not let me use it. When I select "Network" from the GUI I get a message saying that "The configuration could not be loaded - you are not allowed to access the configuration system."

I am using an Acer Apsire 7004 with an Atheros AR5005G network adapter.

The installation is a dual boot with Vista. While I am not particularly wedded to Windows I would like to keep it if a reinstallation of Ubuntu is the best solution to the problem.

Thanks

---

### Post by Michael.Godawski on 2009-01-25
hi,

it is never good to interrupt the update process... but when the system froze you had not much choice left.

Let's check first if the packages are intact .Run please these commands in terminal.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo dpkg --configure -a   
```

---

### Post by Camillus on 2009-01-25
> **Michael.Godawski said:**
> hi,

it is never good to interrupt the update process... but when the system froze you had not much choice left.

Let's check first if the packages are intact .Run please these commands in terminal.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo dpkg --configure -a   
```

Thanks for the reply. I ran the commands you gave and the results are below:

```
charles@charles-laptop:~$ sudo apt-get update
[sudo] password for charles: 
Err http://gb.archive.ubuntu.com hardy Release.gpg
  Could not resolve ‘gb.archive.ubuntu.com’
Err http://gb.archive.ubuntu.com hardy/main Translation-en_GB
  Could not resolve ‘gb.archive.ubuntu.com’
Err http://gb.archive.ubuntu.com hardy/restricted Translation-en_GB
  Could not resolve ‘gb.archive.ubuntu.com’
Err http://gb.archive.ubuntu.com hardy/universe Translation-en_GB
  Could not resolve ‘gb.archive.ubuntu.com’
Err http://gb.archive.ubuntu.com hardy/multiverse Translation-en_GB
  Could not resolve ‘gb.archive.ubuntu.com’
Err http://gb.archive.ubuntu.com hardy-updates Release.gpg
  Could not resolve ‘gb.archive.ubuntu.com’
Err http://gb.archive.ubuntu.com hardy-updates/main Translation-en_GB
  Could not resolve ‘gb.archive.ubuntu.com’
Err http://gb.archive.ubuntu.com hardy-updates/restricted Translation-en_GB
  Could not resolve ‘gb.archive.ubuntu.com’
Err http://gb.archive.ubuntu.com hardy-updates/universe Translation-en_GB
  Could not resolve ‘gb.archive.ubuntu.com’
Err http://gb.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
  Could not resolve ‘gb.archive.ubuntu.com’
Err http://security.ubuntu.com hardy-security Release.gpg
  Could not resolve ‘security.ubuntu.com’
Err http://security.ubuntu.com hardy-security/main Translation-en_GB
  Could not resolve ‘security.ubuntu.com’
Err http://security.ubuntu.com hardy-security/restricted Translation-en_GB
  Could not resolve ‘security.ubuntu.com’
Err http://security.ubuntu.com hardy-security/universe Translation-en_GB
  Could not resolve ‘security.ubuntu.com’
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_GB
  Could not resolve ‘security.ubuntu.com’
Reading package lists... Done
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_GB.bz2  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not resolve ‘security.ubuntu.com’

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_GB.bz2  Could not resolve ‘security.ubuntu.com’

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘security.ubuntu.com’

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘security.ubuntu.com’

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘security.ubuntu.com’

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```

```

charles@charles-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up dbus (1.1.20-1ubuntu3.2) ...
The user `messagebus' already exists. Exiting.
 * Reloading system message bus config...                                [ OK ] 

Setting up avahi-daemon (0.6.22-2ubuntu4.1) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ] 

Setting up dbus-x11 (1.1.20-1ubuntu3.2) ...
Setting up evolution (2.22.3.1-0ubuntu1) ...

Setting up evolution-exchange (2.22.3-0ubuntu2) ...

Setting up evolution-plugins (2.22.3.1-0ubuntu1) ...
Setting up f-spot (0.4.3.1-0ubuntu1) ...

Setting up hal (0.5.11~rc2-1ubuntu8.2) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting Hardware abstraction layer hald                                     /usr/sbin/hald already running.
                                                                         [ OK ]

Setting up tracker (0.6.6-0ubuntu3.8.04.1) ...

Setting up libdeskbar-tracker (0.6.6-0ubuntu3.8.04.1) ...

Setting up network-manager (0.6.6-0ubuntu5.8.04.1) ...
 * Reloading system message bus config...                                [ OK ] 
 * Restarting network connection manager NetworkManager                  [ OK ] 
 * Restarting network events dispatcher NetworkManagerDispatcher         [ OK ] 

Setting up policykit-gnome (0.7-2ubuntu1.1) ...
Setting up rhythmbox (0.11.5-0ubuntu8) ...

Setting up tracker-search-tool (0.6.6-0ubuntu3.8.04.1) ...

Setting up update-notifier (0.70.10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

```

charles@charles-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

```
charles@charles-laptop:~$ sudo dpkg --configure -a
```

produced no output.

After everything had run the system restarted and now detects the network.

Is there anything else I need to do. Naturally I'm a little wary of updates at the moment.

---

### Post by callan79 on 2009-01-25
> **Camillus said:**
> Thanks for the reply. I ran the commands you gave and the results are below:

Is there anything else I need to do. Naturally I'm a little wary of updates at the moment.



Hello,

Updates should be fine, they just make a right mess if they are interrupted (computer locks, power failure, etc).

So now you're back up and running, just do :

```

sudo apt-get update
sudo apt-get upgrade

```

and you should be fine :)

Cheers
Callan

---

