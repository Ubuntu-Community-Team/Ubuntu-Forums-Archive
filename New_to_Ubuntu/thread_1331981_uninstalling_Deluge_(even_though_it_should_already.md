---
title: "uninstalling Deluge (even though it should already be...)"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by christopher.newell on 2009-11-19
I'm trying to either get Deluge working properly again, or uninstall it so I can try something else without worrying about conflicts.  I've been unable to get on any of the Deluge websites lately, otherwise, I'd post there.  I currently have Deluge 1.2 rc3.
  When I try to download a torrent, Deluge will no longer open by default.  If Deluge is open, it will monitor the Desktop folder, but it won't start Deluge with a new torrent.  I'm using Firefox, and I've tried finding Deluge from the preferences, but I can't find the right file.  I also tried to simply input the command 'deluge' since that works in the terminal.  No love.
  Also, I can't check to make sure the ports are properly forwarded.
  My biggest beef lately is the fact that if I have an active torrent, only the active torrent(s) will upload.  If I have another torrent that should be seeding, it does nothing while another torrent is downloading.  I can only seed after all downloading has ended.  (I did try to find an answer to that in the Deluge forums, but none of the suggested solutions worked.)
  If I can get those things working again, I'll be perfectly happy with Deluge.

  So, on to my attempt to uninstall.  I've tried using Synaptic Package Manager to completely remove it--marking every component I could find with "Completely Remove."  When I reinstalled, all of my settings were still there.  I uninstalled again last night, only to find it still works.  In the Ubuntu forums, I found someone else having problems, so I tried those uninstall suggestions.  Here's what I get in my terminal:

> username@Ubuntu-PC:~$ sudo dpkg --remove --force-remove-reinstreq deluge
dpkg: warning: ignoring request to remove deluge which isn't installed.
username@Ubuntu-PC:~$ sudo dpkg --remove --force-remove-reinstreq deluge-torrent
dpkg: warning: ignoring request to remove deluge-torrent which isn't installed.
usernamer@Ubuntu-PC:~$ sudo apt-get purge deluge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package deluge is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
username@Ubuntu-PC:~$ sudo apt-get purge deluge-torrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package deluge-torrent is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
username@Ubuntu-PC:~$ which deluge
/usr/local/bin/deluge
username@Ubuntu-PC:~$ 
  If I enter "deluge" in the terminal, it runs--with all my settings still intact!  I'm baffled.

---

### Post by 3rdalbum on 2009-11-19
Removing a program does not remove its settings (for a number of reasons),

Program settings are in a hidden folder in your home directory. Try looking in ~/.deluge or ~/.local or ~/.config, in your home directory.

---

### Post by diesch on 2009-11-19
Files in */usr/local/* are most likely not installed by a package but manually, so you have to manually uninstall them, too.

---

### Post by GrandpaLeaman on 2009-11-19
Rather than completely remove the RC3, go to Synaptic Package Manager and go to the "Package" menu and select "Force Version" and select the version in the repositories, which I believe should be 1.1.9.

---

### Post by christopher.newell on 2009-11-19
How do I manually uninstall? Is it simply a matter of deleting files?

---

### Post by diesch on 2009-11-19
> **christopher.newell said:**
> How do I manually uninstall? Is it simply a matter of deleting files?

Most likely yes. How did you install Deluge?

---

### Post by christopher.newell on 2009-11-19
I had downloaded a tarball from the Deluge site and used the commands in the readme file.

Without starting a separate sub-discussion, I wanted to ask about configuration files not being uninstalled. Synaptic Package Manager specifically differentiates "Complete Removal" as including config files. Are they full of crap, or did 3rdalbum just misread that part of my first post?

---

### Post by diesch on 2009-11-19
> **christopher.newell said:**
> I had downloaded a tarball from the Deluge site and used the commands in the readme file.


With some luck running
```
sudo make uninstall
```
in the directory where you run "make install" does the job. Otherwise you have to find and remove Deluge's files in /usr/local/ manually.

> **christopher.newell said:**
> 
Without starting a separate sub-discussion, I wanted to ask about configuration files not being uninstalled. Synaptic Package Manager specifically differentiates "Complete Removal" as including config files. Are they full of crap, or did 3rdalbum just misread that part of my first post?

The package manager never touches anything in your $HOME so all the config files there will stay. 

Global config files aren't removed by default as they may contain valuable information from changes made by you or other packages. You need to do a "Complete Removal" to remove them.

---

### Post by 3rdalbum on 2009-11-19
System-wide cinfiguration files are removed, but not per-user preferences.

---

### Post by GrandpaLeaman on 2009-11-20
It looks like you are not the only one having this problem with Deluge 1.2 RC3. Check out this thread...
 
[http://ubuntuforums.org/showthread.php?t=1332434](http://ubuntuforums.org/showthread.php?t=1332434)

---

### Post by christopher.newell on 2009-11-20
Once I get rid of 1.2, I think I'll go back to 1.1.9.  At least if I'm installing from the repos, I won't have the same problem uninstalling... I was thinking of trying kTorrent as a replacement.  Any comments or alternate suggestions?  (Didn't like Vuze in Linux--it tries to be too many things and wasn't very stable on my system.)

Thanks for the clarification 3rdalbum.  I didn't realize the differentiation between configuration and preferences, I guess.

---

### Post by rideburton56 on 2009-11-20
IMO, Ktorrent is a lesser program to deluge.  It uses more resources, and I personally consistently get lower speeds even with ports fowarded, DHT enabled, etc.

As far as deluge goes, I strongly suggest sticking with the repo version.  First of all, I always thought that if you manually install a program, then the package manager doesn't bother with it anyway (which is why apt + synaptic are unaware of it even existing).  Every time I try to stay on the bleeding edge of a program, it ends up being a headache.

---

### Post by camaron1 on 2009-11-20
> **christopher.newell said:**
> Once I get rid of 1.2, I think I'll go back to 1.1.9.  At least if I'm installing from the repos, I won't have the same problem uninstalling... I was thinking of trying kTorrent as a replacement.  Any comments or alternate suggestions?  (Didn't like Vuze in Linux--it tries to be too many things and wasn't very stable on my system.)

Thanks for the clarification 3rdalbum.  I didn't realize the differentiation between configuration and preferences, I guess.

Ktorrent is very good too, but it is true that uses more resources (on a Gnome desktop anyway).

---

### Post by christopher.newell on 2009-11-20
Well, I'm happy to say I'm back up and running again. Thanks for the help in getting rid of 1.2!  That'll be the last time I install out of the repos.  Before trying kTorrent, I wanted to make sure I really tried to save Deluge on my system.  Once I had everything uninstalled (deleted), I disabled the ppa for Deluge, and installed 1.1.9 via the Ubuntu Software Centre.  All my settings were gone from my rigorous deleting, so I restored what I wanted.  I don't often have torrents running, so I couldn't check the seeding problems, but I still couldn't start a torrent from Firefox.  So, after some further googling, I came across a bug report for someone who had a problem after upgrading, but couldn't reproduce the bug on a fresh install... I did upgrade, but was that when the problems start?  Can't hurt to try, I thought.  I can now start a torrent from Firefox!  So, for anyone combing the forums for the same fix to their problem, here's the advice I followed:
> Can you add the following to /etc/apparmor.d/usr.bin.firefox-3.5:
  /usr/bin/deluge Ux,
  /usr/bin/mkfifo Ux,

Then reload the profile with:
```
sudo apparmor_parser -r /etc/apparmor.d/usr.bin.firefox-3.5
```
Hopefully the seed problem is gone too.  I don't download much, so it'll be a while before I need that.

---

