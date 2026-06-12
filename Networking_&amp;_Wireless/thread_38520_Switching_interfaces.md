---
title: "Switching interfaces"
date: 2005-05-31
forum: Networking &amp; Wireless
---

### Post by Strife on 2005-05-31
I have a laptop, and so I have two network interfaces (wireless and wired). But let's say I want to switch from one to the other because, say, I'm not getting a wireless signal.

The problem is, even though I have an IP address and my wireless adapter is disabled, it still tries to use it as the interface connecting to the internet. If I try to connect to anything, it immediately tells me the server cannot be found.

Is there a way to correct this without restarting?

---

### Post by MechR on 2005-06-01
In your system tray you should have an icon for your 'net connection (it looks like two monitors).  Click on it, and in the popup window use the dropdown arrow to change interfaces (or type in the interface name yourself).

If that doesn't work, open the window again and click on Configure, and deactivate the interface(s) you don't want to use.

---

### Post by Strife on 2005-06-01
That icon simply shows you the status of connections. As far as I know, this is all it does. Therefore, changing which one's status I see shouldn't do anything

Besides, I already have BOTH interfaces have their own icon so I can see both statuses at the same time.

Even if I enable one and disable the other, I can't seem to switch it to be able to use the other one.

---

### Post by Strife on 2005-06-02
There has GOT to be an easier way to switch which interface to use as the one to use without restarting....

sudo /etc/init.d/networking restart perhaps?

---

### Post by cwaldbieser on 2005-06-04
What does your routing table look like when the wireless adapter is disabled?  Is your route to the Internet trying to use the dead interface?
```

$ route
```

will show you.

---

### Post by Strife on 2005-06-04
route may be able to show me what it's using (I'm assuming it was trying eth1 still), but how can I change what it actually USES as opposed to just SHOWING me what it uses?

---

### Post by cwaldbieser on 2005-06-05
Well, you can do it via the command line using the route command in all its gory glory (see man route).  Or you could go to:

+ System -> Administration -> Networking
+ Enter Password when prompted
+ Network Settings Dialog
+ Default gateway device at the bottom should be changed to the active interface.

With a little ingenuity, you could probably cobble together a shell script that does the switcheroo for you and put a shortcut to it on your desktop.

---

### Post by Strife on 2005-06-05
I gave the GUI method a try (I have tried many times before, actually), but it did not work. After pressing OK, it just sat there thinking for a while, and when it was finally finished, I could no longer connect to ANYTHING. It wouldn't even try to use the wireless interface.

---

### Post by cwaldbieser on 2005-06-05
Well, the thing to try would be to route add a new default route that specifies your second interface.  Without knowing what your normal routes look like, I can't plug in the numbers for you, but when you are using the wireless, you probably have a rule or rules like this:

+ If the destination address of the IP packets I am sending is on the Internet, send the packets to my wireless router which has address xxx.xxx.xxx.xxx using device wlan0.

When your wireless interface is deactivated, naturally, those routes are invalid, so they go away.  You just need to put in a new route that says something like:

+ If the destination IP address of the IP packets I am sending is on the Internet, send the packets to the router/dsl modem/whatever with IP address xxx.xxx.xxx.xxx using device eth0.

The man pages on the route command explain the particulars.  I can't tell you what addresses or devices need to be used without more information about your particular setup.  But you don't need to restart.

I am surprised that the GUI doesn't work as expected.  You might want to file a bug about it.  Including output from your ifconfig and route commands both before and after you tried changing the setting via the GUI would probably help whoever was trying to troubleshoot the problem.

---

