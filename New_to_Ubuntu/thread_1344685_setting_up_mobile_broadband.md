---
title: "setting up mobile broadband"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by tyrant monkey on 2009-12-03
I am currently very new to ubuntu and was having a tough time setting up my mobile broadband device. I have a 3G/HSDPA USB device that is detected by ubuntu when I plug it in. My problem is that on the list of countries one has to select as the first step to setting things  the country I live in, Namibia is not listed.
 
Is there a way of setting up my 3G dongle if I am unable to select the country I live in?
 
cheers

---

### Post by anaconda on 2009-12-03
of course it is possible.

The list of countries and operators are there (in networkmanager) just for using settings that are already in the   networkmanagers setup files..

If I was you I would try to connect first with wvdial, which sadly doesn't come with ubuntu 9.04 or 9.10.. It used to come with previous versions of ubuntu. But if you have a new ubuntu you can install wvdial  (and gnome-ppp to it if you can get the machine online any other way..

---

### Post by 3rdalbum on 2009-12-03
Yep, just right-click on the Network Manager, choose Edit Connections... click the Mobile Broadband tab and click New, then add in the settings manually. You'll probably need the modem initialisation string to be set to *99#, with username and password probably set to "a".

Your APN will change depending on your carrier, so I don't know what you'd need to use for that; but most of the other options should be fine at their defaults.

---

