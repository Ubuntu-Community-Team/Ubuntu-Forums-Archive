---
title: "network manager and breezy"
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by vtec on 2005-10-17
What is the status of network manager in breezy. I installed it last night on my laptop but then was unable to figure out what to do next. I could not find any applets or programs from the install. Is breezy's current network manager usable??

---

### Post by emendelson on 2005-10-17
Network manager is wonderful, but it would be nice if someone explained how to use it. Here goes. 

Install it from the repositories. 

Use System-->Preferences-->Sessions, go to the Startup Programs tab, and add this:

```
nm-applet
```

Give it an Order of 10 or 20 (so it starts soon after you log in)

Log out and log in again.

Right-click on the OLD network monitor applet (the one with two screens overlapping). Choose Remove from panel. (You can always put it back with Add to Panel, but it interferes with nm-applet.)

If you're using a wired connection, all should be well. If you want to switch to wireless, disconnect the cable. Click on the Network Manager applet, choose your wireless network. The applet will prompt you to create a password for the default keyring; choose something short and easy to type, because you may need to type it often. Follow the prompts to setup your connection. It should work perfectly. 

Now plug the ethernet cable back in, and watch the connection change back to wired. Amazing, isn't it? Better than anything in Windows.

---

### Post by vtec on 2005-10-17
Thanks i think that is what i needed to know. I'll try it as soon as i'm home. Last night i installed somthing called "network manager" but not the applet you mentioned.

---

### Post by emendelson on 2005-10-17
When you installed "network manager" you actually DID install nm-applet. That's the confusing part. No one ever bothers to say how to start the thing. But "network manager" (or "network-manager" or "NetworkManager") works when you run "nm-applet". So you already have nm-applet installed. All you need to do is run it.

---

### Post by MetalMusicAddict on 2005-10-17
[Heres]("http://www.ubuntuforums.org/showthread.php?t=77461") the problem Im having with it. Any help?

---

### Post by vtec on 2005-10-17
I got nm-applet to start up, and the icon show up. However when i click on it it could not find any wireless networks, and then disapperared. This happened a few times taking a restart to get it to come back. After a few restarts it stops showing up all together. It never did work. I'm back to using gtkwifi now which isn't to bad but not as good as i hear NM can be. Is there anything else that needs to be set up for it to work??

---

### Post by netdance on 2005-10-17
OK, I give up.

I followed the instructions above - I downloaded network-manager from the repository, and added nm-applet at the startup.  I deleted the default app.

I logged out and logged back in.  I see nothing.

I reboot.  I see nothing.

What should I be seeing?  And any idea why I'm not seeing it?

---

### Post by vtec on 2005-10-17
Thats kinda what my problem was/is. When i did see somthing i saw an icon saying my ethernet cable was unplugged.

---

### Post by vtec on 2005-10-18
Well i got it working. I had a few updates that i didn't do. Once i did the update network manager was amoung them and now works great.:p

---

### Post by netdance on 2005-10-20
Interesting - since the update, Network Manager has started clobbering the /etc/resolv.conf symlink which seems to be required for other stuff.  Since I wasn't using it anyway, I uninstalled it.  Wierd.

Unless I hear popular acclaim, I'm going to assume this part of Ubuntu is... less functional than the rest.

Wish  I had the skills to get it going, but apparently I don't...

---

### Post by blackpaw on 2005-10-20
thank you, it works like a charm!

now if only someone could build in support for wpa (or wpa-supplicant) into this applet, I would be one happy ubuntu laptop user :D


cheers

---

### Post by sav2005 on 2005-10-20
If only I could get this to work with WEP-TLS certificates :-(

---

### Post by landotter on 2005-10-20
[IMG]http://static.flickr.com/27/54470842_93048e050c_o.jpg[/IMG]

Got it working here too, but certain websites became unavailable. :wacko: Didn't remove the old net-monitor applet--which may have done strange things.

Great simple app. :up:

---

### Post by johneboy on 2005-10-23
Thanks emendelson!  Your how-to worked a treat on My Acer 163x laptop with an INPROCOMM IPN 2220 card and ndiswrapper!

---

### Post by Anthem on 2005-10-27
Ok, help me here.

I got nm-applet up and running, I logged onto my WEP network, and I got the keyring established.  I still have two problems.

First, NetworkManager can't find my wired connection.  I'm plugged in, but it shows no wired network available.

Second, my wireless network is SLOW through networkmanager.

Any tips?

---

### Post by bonifacio on 2005-10-27
Two issues:
1.  Network manager could not see hidden ESSID.  I tried adding it manually but couldn't establish connection.

2.  When my laptop suspend to RAM.  NM is not restarting itself.  The applet is gone from the tray.

---

### Post by Anthem on 2005-10-27
Does anyone know how to change the NetworkManager password?

Actually I just want to get rid of the password.

---

### Post by landotter on 2005-10-28
[quote=Anthem]Does anyone know how to change the NetworkManager password?

Actually I just want to get rid of the password.[/quote]

It didn't need a password when I restarted, it just ran as a service. I made sure to add "nm-applet" to my system/preferences/sessions/startup programs list. I gave it an order number of 40 which seems to work fine. 

Hope that helps. :D I'm on a desktop so don't get too fancy with wireless. I only have two networks that I can connect to.

---

### Post by emendelson on 2005-10-28
It's the default keyring password. Install something called something like keyring manager from Synaptic.

---

### Post by Anthem on 2005-10-28
Cool, I'll try.

Two more questions:
1.  Does anyone else have problems w/ NetworkManager significantly adding to book time?
2.  The NetworkManager site says the latest news was the last release... in May.  That's not something that screams "active development" to me.  Can I assume that development's moving forward somewhere else?  EDIT:  Browsed CVS and there are changes from this week.  So I guess it is moving forward.

---

### Post by MrStu on 2005-11-03
If anyone can help me regarding network manager I'd be most grateful. All info is this thread: [http://ubuntuforums.org/showthread.php?t=81251](http://ubuntuforums.org/showthread.php?t=81251)

---

