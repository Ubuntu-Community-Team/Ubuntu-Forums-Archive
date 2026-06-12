---
title: "Upgrade from 9.04 to 9.10 removed NBR"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by GaretJax on 2010-08-24
I had installed 9.04 Netbook Remix on my Dell Mini 9 a year or so ago.  The Update Manager kept reminding me that there was a new version out, so I finally decided to upgrade tonight.

I knew that the upgrade would only bring my system to 9.10 which is now preceded 10.04, but I didn't mind behind a little behind.

When I chose to upgrade, I did it through the Update Manager's  "upgrade" button.  It was painless and took about two hours.  :popcorn:  During the upgrade, I was concerned that the new version might not contain the Netbook Remix.


Well now that my Mini 9 is running 9.10 I believe my concerns were correct because I can't find the "switch window mode" under any of the menus.

Is there a way to add the NBR after the fact without reinstalling the OS?

---

### Post by quixote on 2010-08-25
Yikes.  It shouldn't change your installation type!  I've never heard of that happening before.  Any chance that the useful feature you liked just got removed?  I mean, are you sure it's still actually a part of UNR?  (Sometimes it seems like the Ubuntu devs try to figure out ways of breaking things that were fine before they "fixed" them.)

To answer your question: I'm not aware of after-the-fact ways of installing UNR, but that doesn't mean there aren't any.  It's just a version of gnome, and if you knew which packages to install, you'd get the new "skin".  Like installing kubuntu alongside ubuntu, for instance.

---

### Post by DavidOfLondon on 2010-08-25
Sadly, the issue of not being able to rollback or re-instate older software post-upgrade is very, very common with Linux OS users.

Some packages just aren't maintained any more, some were never updated...

It annoyed me intensely to find that several tab window effects aren't supported in Ubuntu 10.04, for example.

If you have any script knowledge it's possible to modify virtually everything. Consider Mr Google on editing the scripts used - even advanced users copy and paste script.

Sorry this isn't more specific an answer but with a free OS the truth is that things move very quickly and often packages just get left behind.

---

### Post by GaretJax on 2010-08-26
So.  Is there a UNR for 9.10 or 10.04?

---

### Post by quixote on 2010-08-27
Yes, of course.  This is the link to [download UNR 10.04]("http://www.ubuntu.com/netbook").  That would be a new install, which means you'd lose any packages you installed yourself and, unless your /home partition is separate, all your configurations. (You could back up your current home, and then copy it back after installation to avoid that.)  There's a page of instructions about [upgrading]("http://www.ubuntu.com/netbook/get-ubuntu/upgrade").  I wonder if maybe you ran into trouble because you pushed a button for a "regular" ubuntu upgrade.  The UNR upgrade seems to be quite separate.

---

### Post by LowSky on 2010-08-27
its this easy if it isn't installed

open a terminal and type:

```
sudo apt-get install ubuntu-netbook-remix
```

---

### Post by cariboo on 2010-08-27
Before trying to install anything, look at sessions in the lower panel of the login screen to see if you have the gnome-desktop session selected, instead of the netbook.

---

### Post by quixote on 2010-08-27
> look at sessions in the lower panel of the login screen to see if you have the gnome-desktop session selected, instead of the netbook
Good point!  Why didn't I think of that?  :rolleyes:

---

### Post by GaretJax on 2010-08-30
> **cariboo907 said:**
> Before trying to install anything, look at sessions in the lower panel of the login screen to see if you have the gnome-desktop session selected, instead of the netbook.

Good tip.  In the sessions window I have Failsafe Gnome, Gnome, and xterm.  So I figure that UNR isn't one of them.

> **LowSky said:**
> its this easy if it isn't installed

open a terminal and type:

```
sudo apt-get install ubuntu-netbook-remix
```

I will be trying this next and I will post my adventures to follow :KS

---

### Post by GaretJax on 2010-08-30
> **LowSky said:**
> its this easy if it isn't installed

open a terminal and type:

```
sudo apt-get install ubuntu-netbook-remix
```

Hmm.  Well it it seemed to go well.  It said it has 1 new package to install and installed it.  It went surprisingly fast.  I think it only downloaded 64k.  After the installation I could not find a way to activate it.  I logged off to look at the session options.  Nothing is different from my previous post.  And I can't find 'switched window mode' under preferences or administration.  I look around the rest of the menus, no sign of UNR.  Oh and I did all this after a reboot.  I retyped your install command and it says it is already installed.

So not sure what else to do at this point.

---

### Post by quixote on 2010-08-30
Remix is small, but it's not that small.  Something went wrong with the download.  I think you want to either get rid of or fix the broken version currently installed, rather than install again on top of it, and I'm not sure of the best way to do that.  Trying the following is harmless, but may not work if the UNR install is very broken:```
sudo apt-get remove ubuntu-netbook-remix
```Then try the installation again.

Added: you may want to select ubuntu-netbook-remix within synaptic.  There shouldn't be a difference to using command line apt-get, but who knows.  Then you don't have to worry about making typos, and maybe it'll be more careful about getting all dependencies. ??

---

### Post by GaretJax on 2010-08-31
Well I would have to say the experience was the same as before, but this time I am posting the terminal in case you eye can see something that I am not seeing.

> garet@Tatooine:~$ sudo apt-get remove ubuntu-netbook-remix
[sudo] password for garet: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  binutils-static
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ubuntu-netbook-remix
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 61.4kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 141261 files and directories currently installed.)
Removing ubuntu-netbook-remix ...

garet@Tatooine:~$ sudo apt-get install ubuntu-netbook-remix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  binutils-static
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  ubuntu-netbook-remix
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/32.2kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Selecting previously deselected package ubuntu-netbook-remix.
(Reading database ... 141259 files and directories currently installed.)
Unpacking ubuntu-netbook-remix (from .../ubuntu-netbook-remix_1.171_i386.deb) ...
Setting up ubuntu-netbook-remix (1.171) ...
garet@Tatooine:~$

---

### Post by quixote on 2010-08-31
It's not showing the full path to the ubuntu-netbook-remix_1.171_i386.deb it's using, so I can't go check what that really is, but when I searched on that file name, I find links to "meta" directories and, indeed, that file is all of 31.5K.  Whatever that is, it's not the upgrade itself.  I think it's probably the front end that's supposed to get the upgrade started, but for some reason it isn't doing its job.

I tried to find a direct link to a repository that looked like it might be useful, but all I find are directories that have the full Netbook Remix for installation, e.g. [http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.iso](http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.iso), and I doubt those will be useful for upgrading.

My guess about what's happening is that the default location that you reach with the "sudo apt-get install ubuntu-netbook-remix" command isn't working on your system.  Possibly if we could find another location, or fix whatever is stopping your system from proceeding, it would work, but I don't know how to do that. :(

Just as a for instance: if the meta file is pointing to a torrent for upgrading, but torrents are firewalled on your system, it would fail right at the beginning.  I don't think that's what's going on (it would say if it was a torrent), but it might be some weirdness along those lines. ??

---

### Post by GaretJax on 2010-08-31
Before I upgraded I was wondering if that upgrade button would actually upgrade me in line with the UNR version or if it would simply put 9.10 vanilla on my system.  I am thinking that it did just that.  But cautious as always, I backed up my documents before upgrading.

Should I try to autoremove the binutils-static?  Or should I just upgrade to 10.04 and try this again?

---

### Post by GaretJax on 2010-09-03
Well I am not sure what broke, so I just chose to upgrade to 10.04 through the same "upgrade" button on the Update Manager.  During the upgrade process it told me that ubuntu-netbook-remix was no longer supported and would have to be removed.  I had nothing to lose so I went with it.  After the upgrade was complete, my machine booted into 10.04 UNR.

Go figure! :popcorn:

---

### Post by quixote on 2010-09-03
Man.  Talk about a classic :confused: UI!  Glad to hear you conquered!

---

