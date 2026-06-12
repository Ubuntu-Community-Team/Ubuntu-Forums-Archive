---
title: "Wireless Network Menubar Panel Icon"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by dlfuller on 2009-03-07
I have a basic 8.10 installation on a Compaq R3000 laptop.  Networking worked out of the box with the Broadcom B43 wireless driver.  Included was a network icon in the menubar panel that displayed a circular pattern when connecting and then five bars for signal strength after connection.

During housekeeping of the menubar panel I deleted what seemed to be a separator and lost this original network icon.  I did add the Network Monitor to the menubar panel and it is different than the original.  The value of the original was in always displaying the five bars.  Network Monitor requires a click to access the signal strength.

Where can I locate the original icon?

---

### Post by terry_gardener on 2009-03-07
this thread might off interest to you. 

[http://ubuntuforums.org/showthread.php?t=878000](http://ubuntuforums.org/showthread.php?t=878000)

---

### Post by dlfuller on 2009-03-08
Thanks.  It kinda helps.

Network Manager is checked in the System>Preferences>Sessions>Startup Programs tab.  Its command is: nm-applet --sm-disable.

The documentation <https://help.ubuntu.com/community/NetworkManager0.7> for nm-applet isn't much help.  The menubar remains with an icon of two computers, one below to the other.  Not the five bar signal strength icon of the original applet.  Plus I now also seem to have lost the ability that existed before to optionally choose a wired network connection.

---

### Post by bailbath on 2009-03-08
[http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/)

this is what you mean

but I think you deleted the notification area. Right click the top panel and then add to panel then add notification area.
Ian

---

### Post by dlfuller on 2009-03-08
That's it!  But nothing like it is listed in the Add to Panel dialog.

My Synaptic Package Manager does show network manager 0.7 installed but right click About on the icon shows "gnome-netstatus-applet 2.12.2".

---

### Post by bailbath on 2009-03-09
It needs the notification area plugin ticked to show up re-tick 'notification area' in 'add to panel' and it should show up then.
Ian

---

### Post by dlfuller on 2009-03-09
Ian--

Thanks.  Before I didn't get what the "notification area" was.

As you expected, finding Notification Area in the plugins and adding it back returned the icon for NetworkManager Applet 0.7.0.  And immediately, an "updates available" icon also appeared in the notification area and an "ah ha" moment for me in getting the concept of the notification area.

Deleting what I thought was a visual separator in the menubar had been all too easy.  That was for the Notification Area plugin.

Thanks again for your help.

--Don

---

### Post by bailbath on 2009-03-09
> **dlfuller said:**
> Ian--


Deleting what I thought was a visual separator in the menubar had been all too easy.  That was for the Notification Area plugin.

Thanks again for your help.

--Don

It's the easy things that sometimes get forgot in answers and the hard way that is sometimes suggested/used instead! Thanks for your thanks but your question and process to solution will help others so thanks to you too.
Ian

---

### Post by David Ostrom on 2009-03-14
Thank you! I had the same problem deleting what I thought was a separator, who would have thought it was the "Notification Area plugin". I added it back and now all my icons appear. Great post!

---

