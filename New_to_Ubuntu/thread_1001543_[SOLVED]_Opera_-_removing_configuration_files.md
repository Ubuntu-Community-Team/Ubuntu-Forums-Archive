---
title: "[SOLVED] Opera - removing configuration files?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by heyup on 2008-12-04
I installed Opera 9.5 and decided to try Opera 9.27 (which I have used on Windows XP). I removed Opera 9.5 using Synaptic (opting for complete removal), then installed Opera 9.27, but the configuration files do not appear to have been removed. The skins I downloaded on Opera 9.5 remain on Opera 9.27.

How do I get rid of the configuration files?

I have tried commands
 
sudo dpkg --remove opera
sudo dpkg --purge opera

Reinstalled Opera and tried commands

sudo apt-get remove opera
sudo apt-get purge opera

But to no avail. Also Ubuntu does not appear to have removed Opera at all - just puts it away in a cache somewhere. When I try to download Opera after unistall, it finds Opera from some cache rather than does a new download.

How can I clear this cache.

I'm new to Ubuntu. Using 8.04 Hardy.

Edit. Meant Opera 9.62 not Opera 9.5

---

### Post by nakama85 on 2008-12-04
> **heyup said:**
> I installed Opera 9.5 and decided to try Opera 9.27 (which I have used on Windows XP). I removed Opera 9.5 using Synaptic (opting for complete removal), then installed Opera 9.27, but the configuration files do not appear to have been removed. The skins I downloaded on Opera 9.5 remain on Opera 9.27.

How do I get rid of the configuration files?

I have tried commands
 
sudo dpkg --remove opera
sudo dpkg --purge opera

Reinstalled Opera and tried commands

sudo apt-get remove opera
sudo apt-get purge opera

But to no avail. Also Ubuntu does not appear to have removed Opera at all - just puts it away in a cache somewhere. When I try to download Opera after unistall, it finds Opera from some cache rather than does a new download.

How can I clear this cache.

I'm new to Ubuntu. Using 8.04 Hardy.

Have you tried removing Opera through synaptic package manager.

I think other than that you would need to locate the config files and remove them through terminal using the remove command.

many people will hesitate to tell you how to remove with the remove command (as well as myself) and you should be weary of any such commands because if done wrong you could mess up your whole system.

---

### Post by Dj Melik on 2008-12-04
```
sudo apt-get autoclean
```

Its not configuration files, its just .deb archive files. Autoclean should clean them.

---

### Post by Michael.Godawski on 2008-12-04
When you go to Synaptics and right-click on a installed application, then go to properties and then installed files, you get a list with the directories of all files belonging to the installation. 
Check there if there are some config files, and post their names here.

---

### Post by gandaran on 2008-12-04
> **heyup said:**
> I installed Opera 9.5 and decided to try Opera 9.27 (which I have used on Windows XP). I removed Opera 9.5 using Synaptic (opting for complete removal), then installed Opera 9.27, but the configuration files do not appear to have been removed. The skins I downloaded on Opera 9.5 remain on Opera 9.27.

How do I get rid of the configuration files?

I have tried commands
 
sudo dpkg --remove opera
sudo dpkg --purge opera

Reinstalled Opera and tried commands

sudo apt-get remove opera
sudo apt-get purge opera

But to no avail. Also Ubuntu does not appear to have removed Opera at all - just puts it away in a cache somewhere. When I try to download Opera after unistall, it finds Opera from some cache rather than does a new download.

How can I clear this cache.

I'm new to Ubuntu. Using 8.04 Hardy.

configuration files on your home 'user' folder you have to delete them, they don't uninstall like files on root file system, also if you make any change to any root configuration file (like puting skins in opera root folders) these files or folders get left behind when you uninstall opera, only solution is to delete them
and it's best you use synaptic to remove opera, select complete removal and hit apply

---

### Post by heyup on 2008-12-04
Thanks. I did remove Opera 9.62 with Synaptic Package Manager.

The list of files in Synaptic are files in root, most in /usr and a couple in /etc but not the configuration files I was looking for.

I'll have a go with the autoclean command.

gandaran. You are right. I had a look in /home/opera and there are files that were not removed - they are the configuration files such as skins, styles etc.

I didn't realise I had to remove these files manually.

Thanks to all for your help.

---

