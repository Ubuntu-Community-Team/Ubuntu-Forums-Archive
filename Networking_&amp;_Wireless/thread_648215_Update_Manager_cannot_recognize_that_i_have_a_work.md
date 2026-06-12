---
title: "Update Manager cannot recognize that i have a working WiFi connection"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by tsio on 2007-12-23
[B]Hello to every one!

   I' m not very familiar with Ubuntu and generally with Linux. I' m experienced of a problem with Update Manager, Add/Remove and Synaptic Packet Manager.

   Although I have a working WiFi connection (Ndiswrapper / Netgear WG311), and I can surf in the internet normally with no problems at all, I can' t update nothing because these programs don' t recognize that I have a working WiFi connection.

<< Add/Remove program response in checking the desire application >>
   
   The list of applications is not available
   Click on 'Reload' to load it. To reload the list you need a working internet connection. 

<< Update Manager program response in checking for updates >>

   Nothing / It says that my system is up-to-date!!!

<< Synaptic Packet Manager program response in checking for installation >>

   It asks me to put in to the drive the Ubuntu Installation CD, witch means that it can' t
   see the working internet connection!!!

If anybody can help to resolve this problem please let me know!!

Thanks a lot !!!


[/B]

---

### Post by tsio on 2007-12-23
Before I came upon this problem I was setting up the wireless connection, following some
instructions in the WifiDocs/Driver/Ndiswrapper. **page:[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#autostart](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#autostart)**

After the successful installation of the wireless card, I made the settings in section 3.7.1 for automatically loading at start-up, which probably I shouldn' t do.

I open again the specific file: **[COLOR="Blue"]gksudo gedit /etc/modules[/COLOR]** and I erase the word I added in the end ("ndiswrapper").

The problem is solved but know when I open then PC I must manually reload the module:
[COLOR="Blue"]**sudo modprobe ndiswrapper**[/COLOR]  so to connect to the internet with the WiFi card.

---

### Post by ubu-wan on 2007-12-23
Hi,

I am just starting with Ubuntu also, but I did come across these issues so maybe I can help!
The first one is simple although I am not on my Ubuntu PC at the moment so is from my (poor) memory. All you need to do is tell the package manager to use the online updates as a source. You will see down the left side a list of sources; this will include your CD and also something like *local*. You will find somewhere in the preferences for the package manager the options to add the server as a source and also which updates to download or inform you of automatically.

The second issue I also had (guessing you have Broadcom like me). You were correct in adding *ndiswrapper* to the /etc/modules file. But you said you then removed it; did it cause you a problem? If so maybe you hadn't properly removed and blacklisted the native driver? As long as this is properly done you should have no problem. Adding ndiswrapper to /etc/modules got mine working on startup so you should try that again.


HTH


ubu-wan

:guitar:

---

