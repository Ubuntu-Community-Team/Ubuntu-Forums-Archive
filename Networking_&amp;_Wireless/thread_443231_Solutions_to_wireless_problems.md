---
title: "Solutions to wireless problems?"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by Yoeri on 2007-05-14
I noticed there are a lot of problems with wireless networking in Feisty, at the moment approx. 44.9 percent of the users that filled in [this poll]("http://ubuntuforums.org/showthread.php?t=419905") can't get networking to work, me included.

Is there any chance that there will be an update for all those problems, looks like most of them are related to the use of network manager... my wireless adapter gets recognised but I can't connect to a network.

Do we really have to wait for Gutsy or will Feisty be updated? (i hope so)

---

### Post by misconfiguration on 2007-05-14
I'm not having a problem, my wifi card is using restricted drivers and I use the wifi manager, wireless is working flowlessly.

---

### Post by Jouke74 on 2007-05-14
^^ Of course, it would be even worse if no one has a working network manager....

In Edgy I installed Ndiswrapper from CD, Ndisgtk from universe net Edgy repositories, Windows 64 bit driver (which always has worked), gnome-network-manager. Then I did the configuration of Ndiswrapper with Ndisgtk. Next network manager could take over, notice all networks and had no problem connecting to any unsecure / WEP / WPA network.

In Feisty : Same stuff installed, new versions of network-manager, ndisgtk, ndiswrapper + same old driver. Bug. 1. :  Ndisgtk did not recognize any hardware present. The hardware was there with commandline ndiswrapper and did seem to work. Bug. 2. Network manager could detect all networks around, but could only connect to unsecured ones (WEP and WPA) failed. Wifiradar, same problem.

Reinstalled Feisty.

Deinstalled network manager. 

Reinstalled ndiswrapper only now compiled from source from ndiswrapper site.

Using administration > networks I manually configured my connection. Disabled the roaming. Used WEP HEX instead of WPA and there was my connection.

Some things definitively changed....

I think network manager (and  / or ndiswrapper) fails to pass certain basic things to certain the drivers, affecting all people using these.... resulting in no internet connection. This is quite a big group of people.

---

