---
title: "hidden ssid problems - please help"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by qkmbr22 on 2007-12-01
hello

I got my wireless with WPA working on Gutsy last week. Now, however, I decided to hide my SSID, and I have some problems.

When I boot into Gutsy it tries to connect to a network that I temporarily created at some point but doesn't even exist anymore. If I deny the keyring password and the WPA password for the network it is requesting, it stops trying to connect to it. Then I can select "Connect to other wireless network" from nm-applet and connect to my network with the hidden SSID. However, if I don't deny those two password requests no matter what I do I cannot connect to my new network.

How can I make it stop trying to connect to my old network? Can I make it connect to the new network by default? And also, (this is a lesser problem) can I get rid of the keyring manager asking for the password every time at startup?

---

### Post by ayenack on 2007-12-01
Can you post the results of this command.

gksu gedit /etc/network/interfaces

This will open your network interfaces config file. You should comment out the WPA key in this file before you post it here.

---

### Post by qkmbr22 on 2007-12-01
it simply says

```
auto lo
iface lo inet loopback
```

---

### Post by ayenack on 2007-12-01
Are you using ndiswrapper for your wireless card?

---

### Post by qkmbr22 on 2007-12-01
yup

---

### Post by ayenack on 2007-12-01
OK I have zero experience with ndiswraper so I can't help you here. Sorry. You should post again saying that you're using ndiswrapper in the title you'll get someone with knowledge of it that'll help you out.

Good luck.

Edit: Try posting in the Network & Wireless section bound to be someone there that can help. ;)

---

### Post by kevdog on 2007-12-01
With a hidden essid, you cant rely on roaming mode anymore.  You need to either manually specify the network configuration in the /etc/network/interfaces file, or connect manually at the command line.

---

### Post by qkmbr22 on 2007-12-02
well I can only connect with roaming mode right now. To do that I have to click "Connect to other network" every time and enter my ssid and password. If i disable roaming i can't connect at all. Is there a way to make it connect automatically? My /etc/network/interfaces file is pretty empty (see above).

---

### Post by kevdog on 2007-12-02
Take a look at this post -- I will give you a skeleton of what you want to do:

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by phenest on 2007-12-30
I had this same problem, and I have the solution too.

The problem happens if you connect via the current ssid and then change the ssid on the router. Network Manager continues to try to connect to the old ssid. The answer is to open Configuration Editor and browse to system/networking/wireless/networks where you will see a list of ssid's. To get rid of the ones you don't want: highlight the ssid in the left pane, and in the right pane, right click each item and select 'Unset key'. Then exit the Configuration Editor. You may have to logout and login again, but this does solve the problem.

---

### Post by WhyWontThisWork on 2008-01-06
what config editor? I'm having the same problem and I've only put in my one SSID, which the only problem is when I hide the SSID....

---

