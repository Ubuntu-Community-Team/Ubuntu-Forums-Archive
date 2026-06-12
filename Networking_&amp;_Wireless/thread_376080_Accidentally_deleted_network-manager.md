---
title: "Accidentally deleted network-manager ??"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by floke on 2007-03-04
Have been playing around with my panels in Feisty and accidentally removed the applet for network-manager (at least I think that this was the applet - the one that lists the networks you can connect to etc.). Anyway, the question is: how do I get it back? This sounds stupid (and probably is) but I can't see it in my 'add to panel' list of applets (I have network-monitor, but it doesn't do the same, drop down list, job). I try launching 'nm-applet' from a terminal but nothing happens. There's nothin corresponding to this either in my menu lists.

Aaaaaaagh....

Any help?

---

### Post by FurryNemesis on 2007-03-04
Try Network-monitor in add-to-panel. I think it's the same thing.

---

### Post by floke on 2007-03-04
No, it appears they're different. Network-manager allows you to choose from a range of networks that it detects (and is made by red hat and novell - I checked on another pc!). Network monitor just monitors a given connection (and is made by sun).

Thanks anyway though.

---

### Post by spd106 on 2007-03-04
I'm not quite sure how you managed to achieved this since it's in the notification area, rather than as a taskbar applet, just like gaim and beryl-manager.

I suggest that you open the System -> Pref -> Sessions capplet and see if Network Manager is enabled under the Startup Programs tab.

---

### Post by floke on 2007-03-04
Ha! Well I haven't actually deleted it - its still running fine etc. and still listed as a startup prog. But I've removed it from the panel and would like to get it back on rather than the clunky network monitor applet. 

It's no biggy, but an irritant that I stupidly removed it.

---

### Post by spd106 on 2007-03-04
Do you have a notification area? I tried removing mine, then adding it back. The update-notifier and battery status applets re-appeared, but nm-applet didn't so I had to restart gnome.

---

### Post by floke on 2007-03-04
Spd106 - you're a fargin' genuis!
All sorted, thankyou very much.

---

### Post by xdevnull on 2007-03-04
Perhaps along that same note - does anyone know how to restart networkmanager?  Every once in a while when I come out of hibernate it doesn't detect my network cards or at some point gets fubar.  I know how to restart network (sudo /etc/init.d/networking restart) - but I don't know if there is something similar to get NetworkManager restarted as well - hopefully to kind of reset it?  I looked on the site and didn't see and documentation...

Thanks

---

### Post by spd106 on 2007-03-05
There may be a cleaner way, but I usually do ```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```
There is also a script for 26NetworkManagerDispatcher, though I'm sure what effect restarting this has, I usually do it anyway.

---

### Post by xdevnull on 2007-03-05
Thanks - I'll give it a try

---

### Post by Ek0nomik on 2007-03-05
Thanks spd106.  That notification area did the trick.  :)

---

### Post by cjnucette on 2007-04-10
Just add a notification area to the panel, it's under utilities

---

