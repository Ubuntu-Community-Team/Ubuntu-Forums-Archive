---
title: "Packages Kept Back"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by PPPilot on 2011-04-06
I am running Lucid and today when I did my upgrade I got this Message:

```
The following packages have been kept back:
  ffmpeg libavdevice52 libavfilter0 libavformat52 libpostproc51 libswscale0
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
```Why are these packages being held back?  I ran Synaptic and it reports no broken packages. I am at a loss.... Is there a way to clear this out or will it correct itself in time?

---

### Post by wolfen69 on 2011-04-06
It simply means there is no upgrade at the moment for those things. Nothing to worry about. All that matters is if they are working correctly.

---

### Post by rosencrantz on 2011-04-06
I assume you didn't hold them back manually (In that case [FONT="Courier New"]sudo apt-get install <packagename>[/FONT] should remove the lock).
You can check which versions are available:
[FONT="Courier New"]apt-cache policy <packagename>[/FONT]
Maybe newer versions are available in a different repository than the one you installed from and they aren't updated automatically.
You can probably resolve this with [FONT="Courier New"]sudo apt-get dist-upgrade[/FONT], but as wolfen69 said, as long as you don't run into conflicts or explicitly require a newer version, there is nothing to worry about.

---

### Post by tgm4883 on 2011-04-06
> **wolfen69 said:**
> It simply means there is no upgrade at the moment for those things. Nothing to worry about. All that matters is if they are working correctly.

If there were no upgrade available for those packages, then they wouldn't be listed. (If that were the case, there would be a lot more packages listed)

That usually means that 'apt-get upgrade' couldn't upgrade those packages because that would require that other packages be installed or removed (new dependencies or conflicts). 'apt-get upgrade' doesn't have permission to install or remove packages, for that you need to use 'apt-get dist-upgrade'

---

### Post by kracheck on 2011-04-06
Hi everyone,

I have the exact same issue. The command "sudo apt-get dist-upgrade" doesn't solve this. It returns :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  ffmpeg libavdevice52 libavfilter0 libavformat52 libpostproc51 libswscale0
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

Any other suggestions ?

---

### Post by kracheck on 2011-04-06
PPPilot...when you go into "System" "Administration" "Software Sources" "Other Software"...

is by any chance the entry 

"http://archive.canonical.com/ubuntu lucid partner (Source Code)" 

unchecked ?

It was in my case. I checked it, returned back to the console and typed sudo apt-get upgrade. It upgraded the involved packages and solved the 'kept back'.

---

### Post by tgm4883 on 2011-04-06
> **kracheck said:**
> PPPilot...when you go into "System" "Administration" "Software Sources" "Other Software"...

is by any chance the entry 

"http://archive.canonical.com/ubuntu lucid partner (Source Code)" 

unchecked ?

It was in my case. I checked it, returned back to the console and typed sudo apt-get upgrade. It upgraded the involved packages and solved the 'kept back'.

That wouldn't resolve the issue. Likely what did is that you did a recheck of available packages (apt-get update)

---

### Post by wolfen69 on 2011-04-06
> **tgm4883 said:**
> If there were no upgrade available for those packages, then they wouldn't be listed. (If that were the case, there would be a lot more packages listed)

That usually means that 'apt-get upgrade' couldn't upgrade those packages because that would require that other packages be installed or removed (new dependencies or conflicts). 'apt-get upgrade' doesn't have permission to install or remove packages, for that you need to use 'apt-get dist-upgrade'

Thanks for clarifying.

---

### Post by PPPilot on 2011-04-06
I gave this a try. Same answer...

```
john@john-desktop:~/Desktop$ sudo apt-get dist-upgrade
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  ffmpeg libavdevice52 libavfilter0 libavformat52 libpostproc51 libswscale0
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
```

---

### Post by PPPilot on 2011-04-06
I tried checking "ubuntu lucid partner"  line as suggested and it allowed the following: 

```
john@john-desktop:~/Desktop$ sudo apt-get upgrade
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  ffmpeg libavcodec-extra-52 libavcodec-unstripped-52 libavdevice52
  libavfilter0 libavformat52 libavutil-extra-49 libpostproc51 libswscale0
  x11-xserver-utils
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,834kB of archives.
After this operation, 24.6kB of additional disk space will be used.
Do you want to continue [Y/n]? y
```Note that it now upgraded 4 additional packages and upgraded a total of 10 packages which cleared the "Kept Back". Very strange...... Sounds like a bug?????

---

### Post by twall on 2011-11-18
Check /etc/apt/preferences.  That file may hold additional settings indicating how an update will affect a given package or packages.

I had one machine that stubbornly refused to recognize a package as installed or upgradable (although I could force an update via aptitude and scrolling to the new version).  Turned out there was an entry in /etc/apt/preferences for the package, indicating an obsolete version.

---

