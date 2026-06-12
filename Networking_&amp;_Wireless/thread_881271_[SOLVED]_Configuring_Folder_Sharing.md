---
title: "[SOLVED] Configuring Folder Sharing"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by [TCK] on 2008-08-05
Using Kubuntu 8.04 KDE4 Remix on a fresh install, I've been trying to get folder sharing working and failing miserably.  Viewing other folder shares works, but I'm having trouble sharing my own folders.  after getting to the share tab in the folder properties and clicking on "Configure File Sharing..." I'm given a pop-up box, Title bar: "Error - KdeSudo" Dialog: "Command not found!".  After looking around these forums and a good Google search I've installed samba but that hasn't seemed to change much, and the little advice I've found seems rather complicated.  

If any more information is required of me I'm able to give it, though bear in mind that I'm a Kubuntu newbie (short of a brief spell a few years ago), my only real prior knowledge of Linux is Xandros on the EEEpc.

---

### Post by Linux Lurker on 2008-08-07
First point - I do NOT know what I'm doing.

But, I thought I'd post what I discovered while experiencing this same problem.

I have a Kubuntu 4 installation over the top of my KDE3.  Despite not using the KDE4, I have been using that version of Dolphin for file browsing.
On the off chance this was causing the error, I opened up the KDE3 version of Dolphin and right clicked properties to access the file sharing tab.
I haven't configured my stuff yet.  But I'm happy to report that accessing it this way opens up the "configure file sharing" dialog box the way it's supposed to.

Hope that helps.

---

### Post by [TCK] on 2008-08-07
Thanks, I installed d3lphin and tried configuring file sharing.  No error message came up but not much else came up either.  However, I opened d3lphin with the terminal, which reported the following message:

```
kcmshell (kdelibs): WARNING: Could not find module 'fileshare'.
```

I tried opening up Dolphin (KDE4) with the terminal open to see if any hidden messages came up for that.  After clicking the "command not found" dialog box, the terminal reported:

```
QSocketNotifier: Invalid socket 23 and type 'Read', disabling...
```

A google of the latter error message proved fruitless, but googling the former message led me to [this thread on the Gentoo forums]("http://forums.gentoo.org/viewtopic-t-397161-view-next.html?sid=355513e46ab06b3db2f86d1cd93350bb"), which encouraged me to install the KDE3 version of kdenetwork-filesharing, which worked with d3lphin to configure file sharing.

So in a roundabout way you helped to solve the problem, because I would naturally not checked the terminal for error messages.  The lesson to be learned: always check the terminal for extra clues.  Ideally I would like this to work with Dolphin/kdenetwork-filesharing-kde4, but this is a perfectly acceptable workaround :)

---

### Post by dando80 on 2009-02-12
Hi guys,

I found that in my case the "command not found" when choosing "Configure File  Sharing" was because dolphin / konqueror call kdesu for 

"kcmshell4 fileshare"

I found this works without sudo but does not allow changes. It fails when run using sudo. I haven't found fix yet but workaround is to run the following:-

"sudo /usr/lib/kde4/bin/kcmshell4 fileshare"

Dan

---

### Post by mugginz on 2009-04-20
When kcmshell4 won't run the fileshare module, I've found it's usually related to an unupdated system config cache and can be fixed by running the following command.

```
sudo rm -R /var/tmp/kdecache-root
```

This should allow the following command to execute successfully.

```
kdesudo kcmshell4 fileshare
```

There's a bit more info about it here.

[http://mugginix.com/articles/2009/Apr/19/Broken-File-Sharing/]("http://mugginix.com/articles/2009/Apr/19/Broken-File-Sharing/")

---

### Post by exsencon on 2009-10-14
Thanks mugginz,I've been trying for two days getting file sharing to work in Kubuntu 9.04.Your solution works like a charm!
It is so easy in Ubuntu and for some reason Kubuntu is always more difficult at least with my system

---

### Post by john newbuntu on 2009-12-04
Install kdenetwork-filesharing to resolve this problem.

---

### Post by naught101 on 2011-03-27
> **john newbuntu said:**
> Install kdenetwork-filesharing to resolve this problem.
Thanks john, that worked for me!

---

### Post by karl0s on 2011-04-09
> **john newbuntu said:**
> Install kdenetwork-filesharing to resolve this problem.

Thank you very much! After several years of manual samba configuring I almost give up trying to find a solution for this problem but this really works! Thanks again!

---

