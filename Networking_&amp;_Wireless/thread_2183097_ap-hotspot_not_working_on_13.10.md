---
title: "ap-hotspot not working on 13.10"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by Ertai87 on 2013-10-23
Hi all!  I just upgraded from 13.04 to 13.10, and I'm having trouble with ap-hotspot.  Under 13.04 everything worked fine, and I used it all the time, but something broke under 13.10.  At first, I started it and tried connecting to it, but the connection just hung, and none of my devices could get on.  So I tried reinstalling it and adding the PPA.  The installation seemed to go fine.  So I started up the hotspot again (it kept my settings somehow), but again, couldn't connect.  So I tried running the configure command to try to refresh the settings, and now it won't start at all; it hangs on "Starting Wireless Hotspot" and never gets to the "Active" stage.

How can I fix this?  Has anyone else had a similar problem?  Thanks.

---

### Post by Ertai87 on 2013-11-03
This post is about a week old already; wondering if anyone else is having a similar problem, if the devs are working on it, if there are any workarounds, etc.

---

### Post by Ertai87 on 2013-11-10
Bump?

Also, perhaps the following is useful information (if anyone other than me is even checking this thread):

```
$ sudo ap-hotspot start
Starting Wireless Hotspot...
$ sudo ap-hotspot start
Another process is already running
$ sudo ap-hotspot stop
Stopping Wireless Hotspot...
mon.wlan0: ERROR while getting interface flags: No such device
```

(username, hostname, and PWD snipped)

---

### Post by sbnwl on 2013-11-14
Remove and purge the ppa. Also remove any other customised configurations.
Ubuntu 13.04 and earlier releases require the installation of ap-hotspot script and some cumbersome configuration with ap-hotspot and dnsmasq.
You might neet to reconfigure the ap-hotspot by running this command in the terminal:

sudo ap-hotspot configure

If you could not follow that procedure correctly then here is a simple guide to follow:
[http://ubuntuforums.org/showthread.php?t=2165035](http://ubuntuforums.org/showthread.php?t=2165035)

Just follow the guide. I recently upgraded from Ubuntu 13.04 to Ubuntu 13.10, which broke/removed the ap-hotspot script and other configurations. Just followed the guide once again (It's me) on upgraded Ubuntu system and **the ap-hotspot started working again!**

**The network manager in default Kubuntu 13.10 installation has inbuilt support for AccessPoint mode. **
Just go to "Edit Connections" , then "Add" a "WiFi(Shared)" connection, select "WiFi tab, mode = AccessPoint", select "WiFi-Security tab, Security = WPA & WPA2 Personal and give any password" and save the connection. That is all, you should be done!

---

### Post by Ertai87 on 2013-11-14
Hm.  I guess all I needed to do was reinstall the PPA...or something...?  I have no idea, but it seems to work again.  Alrighty then.

---

### Post by sbnwl on 2013-11-27
Then you should mark the thread as "SOLVED" ! Use the thread tools for that.

---

### Post by Adfc on 2014-02-10
Hi!
I have just followed what you wrote in this thread, but I cannot have my hotspot working. It runs but my device (smartphone with Android 4.4.2) cannot connect to the wi-fi network: it does not see it.
I have the same problem if I activate the Wireless Hotspot in Network setting, but also if I activate ap-hotspot (as described in the linked guide).
Have you other suggestions?

---

