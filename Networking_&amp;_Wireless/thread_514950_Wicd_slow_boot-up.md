---
title: "Wicd slow boot-up"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by hnaamyilkemku on 2007-08-01
I've configured the session manager to start /opt/wicd/tray.py during boot-up. It takes an annoying amount of time to start, though--on the order of a minute after everything else in Gnome has finished loading. Does it just take that long to identify local wireless networks (there are 5+ here at work)? Could the slow start have something to do with wicd attempting to start a connection with my home network when I'm at work? In case it makes a difference, I'll note that I've configured my computer to accept a static ip when I'm at home. Thanks as always for any help!

---

### Post by imdano on 2007-08-01
If wicd can't find your wireless network when it runs iwlist scan it won't try to connect to it, so I don't think that's your problem, especially if you aren't using dhcp.  Do you have your home network set to autoconnect?  If you do uncheck it and see if the start up is any quicker.  Also, what version of wicd are you using?

---

### Post by hnaamyilkemku on 2007-08-01
I appreciate your response. I'm running version 1.3.1, and I can't check whether my home connection is on auto-connect b/c my home network doesn't show up in wicd (because I'm not at home). If you know how I can check w/o wicd showing the network, I will and I'll get back to you.

It seems that the problem is with /opt/wicd/tray.py; the tray icon never loads after boot-up, but I can run wicd manually and connect to the network, after which the tray icon pops up. There is a gray space on the panel where the icon would normally sit before I make the connection by hand.

---

### Post by walkerk on 2007-08-01
That's not normal. I don't have any issues with wicd.. the tray.py daemon loads up immediately and finds my AP..

I'm using 1.3.1 as well.. like said above wicd only provides a gui for the iwlist, dhclient, & ifup/down commands..

---

### Post by imdano on 2007-08-01
Are you using GNOME?

You can check if your home network is set to autoconnect by opening /opt/wicd/data/wireless-settings.conf, finding your network's profile and checking if "automatic" is set to True.

---

### Post by Rustafur on 2007-08-02
> **hnaamyilkemku said:**
> It seems that the problem is with /opt/wicd/tray.py; the tray icon never loads after boot-up, but I can run wicd manually and connect to the network, after which the tray icon pops up. There is a gray space on the panel where the icon would normally sit before I make the connection by hand.

I am having the exact same problem, to the letter. Same version of WiCD, same exact problem. So the "autoconnect" needs to be disabled in */opt/wicd/data/wireless-settings.conf* ? That's going to suck if I have to turn off autoconnect to get WiCD to actually boot up and run. But it will be better than having to go fire up WiCD every time I boot up.

---

### Post by imdano on 2007-08-02
Were any of you folks with slow boot problems using an earlier version of wicd without this problem?

---

### Post by Rustafur on 2007-08-02
> **imdano said:**
> Were any of you folks with slow boot problems using an earlier version of wicd without this problem?

I didn't have an earlier version installed, I've only used 1.3.1.

On a side note, my ubuntu machine at home must have heard me talking about it at work earlier today. When I booted up the laptop, the WiCD icon appeared immediately after the battery power indicator and volume control in the top taskbar. WiCD didn't automatically connect to the router, but at least it's starting up on boot-up. I never changed anything it's just started to "behave" by itself.

---

### Post by imdano on 2007-08-02
I think it might be because of the way I wrote the autoconnect portion of the daemon.  I was using a while loop in there that wasn't ending until the connection process was completed, and I think that was making the daemon unresponsive to calls from dbus (which the tray uses to communicate with the daemon).  So the tray tries to call some function in the daemon to get information about the connection status in order to decide what image/tooltip to display, but the daemon doesn't respond because still running the autoconnect function.  Normally you don't notice it because the tray already has an image/tooltip loaded, but if the connection is taking a while or fails dbus sometimes crashes, and at startup the tray doesn't have an image/tooltip loaded so it looks like the tray isn't working.  At least that's my theory.

I have a potential fix up on our SVN that has improved speeds for a few people.  I'll definitely try to have it sorted for the next release.

---

### Post by Rustafur on 2007-08-03
That's great news imdano! You're assessment of the problem sounds spot on. For me, there's always been a space in the taskbar, after boot-up, where the WiCD icon would go, but there would just be a blank space that would later be occupied by the WiCD icon once I started WiCD via the Applications menu. I didn't get a chance last night to try disabling auto-connect, to see if that solved the "slow boot-up issue." But after reading your post I'm sure it would fix it. I'll be sure to try tonight after work.

---

