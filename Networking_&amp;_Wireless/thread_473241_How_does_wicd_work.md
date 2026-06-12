---
title: "How does wicd work"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-06-13
Using wicd on kubuntu fiesty.  Im trying to figure out how this thing actually works.  I started the guy from command line however the gui is buggy. I hit a button, nothing happens.  I restart, hit a button, a blank about window is shown.  As far as configuring for wpa, forget about it.  I double click on the network name, nothing, I hit connect, I see all the advanced options greyed out, and it tries to connect.  I push cancel button, nothing happens.

Can you configure this manually???
Im really disappointed.

---

### Post by kevdog on 2007-06-13
OK progress I think

I found the wireless-settings.conf file under /opt/wicd/data

Im trying to use WPA-PSK.

How do I configure this file to specify the options?

---

### Post by compwiz18 on 2007-06-16
Check manager-settings.conf in /opt/wicd/data and see if the wireless interface is set correctly - sometimes the GUI has problems if it isn't.

---

