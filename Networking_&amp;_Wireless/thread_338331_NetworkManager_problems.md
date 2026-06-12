---
title: "NetworkManager problems"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by timkoop on 2007-01-14
Hi all.

I'm trying to get WPA working, like a lot of people I suppose, but please don't bother reproducing the instructions here.  I've found a pile already.  I'm currently trying to follow the instructions posted on this page:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

This page says to use the NetworkManager, which I would like to because I like GUIs.  However, I've installed and reinstalled and uninstalled so many things already that I don't have the NetworkManager applet in the panel (system tray) there anymore (I'm using Ubuntu 6.10).  However, Synaptic tells me that network-manager (0.6.3-2ubuntu6) is installed already, but when I go to "Add to Panel...", Network Manager is nowhere to be found.  I can find Network Monitor, but that's not the same thing.

Any advice on how I can get Network Manager back?  Thanks a lot!

---

### Post by kilps on 2007-01-14
Network Manager needs to be started as an individual program

So press Alt and F2 and run **nm-applet**, if it doesn't show up then add the notification area to the panel ...

Hope that helps ...

---

### Post by timkoop on 2007-01-14
Thanks kilps.

For those of you who might have the same problem, this is what I did...

I ran that command and it did nothing as far as I could tell.  So I went to try to add it to the panel again, but still couldn't find it in the list of stuff to add.  But then I saw something not called "Network Manager" but "Notification Area".  I recognized that as from your post so I added it, and viola!  There it is!  Thanks!

So then I found that I had three of them running so I "kill"'ed off two of them.

---

