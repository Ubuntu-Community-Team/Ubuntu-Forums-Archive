---
title: "Roaming mode (or, how to find open networks)"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by CocheseUGA on 2007-05-15
Got Feisty Fawn working and wireless at home, of course because I knew my SSID, etc. When I want to connect to a network I don't know the name of, etc, how do I do that?

I read something about iwconfig, but don't know the correct commands or how to connect to any network it displays, mostly because I'm not sure what I'm looking for. Any help would be appreciated.

Also, if there is any GUI-based program that lists available networks, a point in the right direction to that would help as well. Thanks.

---

### Post by NilsE on 2007-05-15
Network-Manager-Gnome package is the answer to your question.  It will show you which routers are within range and let you connect to one.

It should already be installed so just right click on a panel and do an "add to panel" and select "Notification Area"

If that does not make it show up make sure nm-applet is running and if it is not put it in the System/Preferences/Session start up panel. Call it whatever you want but the command is nm-applet

You may need to edit the /etc/network/interfaces file if you have configured any devices manually. Just leave these 2 lines. (back it up first). You can comment out the others with a # 

auto lo
iface lo inet loopback

---

### Post by CocheseUGA on 2007-05-15
Sorry, but that didn't help me as far as I know.

I tried to add to panel, Notification, but it didn't add anything. I also tried searching for anything else, but no luck. I already have Network Monitor installed in a panel, but that doesn't do anything for me that I haven't already tried.

I am also really new to this, so a lot of the time when you tell me to do something I don't know how. Thanks for being patient.

---

### Post by NilsE on 2007-05-15
> **CocheseUGA said:**
> Sorry, but that didn't help me as far as I know.

I tried to add to panel, Notification, but it didn't add anything. I also tried searching for anything else, but no luck. I already have Network Monitor installed in a panel, but that doesn't do anything for me that I haven't already tried.

I am also really new to this, so a lot of the time when you tell me to do something I don't know how. Thanks for being patient.
I think you need to re-read my comment.  I did not say "Network Monitor" I said "Network-Manager-Gnome".  Two very different functions one monitors the other manages.

Go into Synaptic and search on it and see if it is installed.  Should be.  Then do the follow-up on the nm-applet and notification area that I suggested.

---

### Post by CocheseUGA on 2007-05-15
> **NilsE said:**
> I think you need to re-read my comment.  I did not say "Network Monitor" I said "Network-Manager-Gnome".  Two very different functions one monitors the other manages.

Go into Synaptic and search on it and see if it is installed.  Should be.  Then do the follow-up on the nm-applet and notification area that I suggested.

I know that's not what you said, that's all that I can find. I don't see Synaptic either, but I'll look again after I reboot.

---

### Post by NilsE on 2007-05-15
Synaptic is the package manager under the System pulldown.  That is where you will do most of your package/product/utility installs.  If the manager is installed the box on the left will be colored green.  If not you click on it and take the mark for installation option.

---

### Post by CocheseUGA on 2007-05-15
OK, did everything that you said (to the best of my ability). Found the Synaptec package and it's installed. nm-applet is running. Dragged 'notification area' to panel, and...nothing.

I installed KwifiManager, and that meets my needs. I am concerned though I couldn't get what you said to work, though.

---

