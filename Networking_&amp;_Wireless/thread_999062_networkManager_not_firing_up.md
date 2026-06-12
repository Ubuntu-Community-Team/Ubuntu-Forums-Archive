---
title: "networkManager not firing up"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by br3athe on 2008-12-01
I have ubuntu 8.10 
I want to use NetworkManager as I cannot see anything GUI wise to scan for wireless networks and connect , I have been using ubuntu 8.10 with gnome desktop for about a month 
I have googled and NetworkManager is meant to ship with ubuntu , but I type sudo NetworkManager and there is not a command not found and it knows it is there as you can press TAB and it will autocomplete , but nothing happens , absolutely nothing 
There is a 'Network Settings' app which is what I get when I double click the network icon , but I am not able to scan for networks etc etc 
Can anyone tell me how to get NetworkManager working as this seems to be the app that will help me when out and about in the cafe world
thanks

---

### Post by m_duck on 2008-12-01
Try running```
nm-applet
```from a run box (by pressing alt F2). To make it persistent on each log in, goto System -> Preferences -> Sessions and add an entry similar to the attached picture. That is the default entry from the install of Intrepid (8.10).

---

### Post by br3athe on 2008-12-02
hi 
thanks for your reply but I am looking for a network manager app that has mobile broadband on one of its tabs the nm-applet is actually fireing up on startup , I was googling a few days ago and came across as screenshot of an app which looked a lot more substantial than nm-applet and like I say had a mobile broadband tab amongst others that nm-applet does not have  , I am pretty sure it was called network-manager , its not in my history and I cannot find it again doh....... 
basically it looked like exactly what I after to manage my connections 
do you know the app I am talking about by any chance ?
thanks

---

### Post by m_duck on 2008-12-02
Ah OK, I have never used mobile broadband so have never seen it, but having a look at my network manager now I have the tab. Are you running Intrepid (8.10)? I don't remember seeing it in Hardy, but in Intrepid, if you right click the network manager icon in the notification area, and goto "Edit Connections..." I have 5 tabs, the middle of which is "Mobile Broadband". For extra info, this is Network Manager version 0.7.0.

---

