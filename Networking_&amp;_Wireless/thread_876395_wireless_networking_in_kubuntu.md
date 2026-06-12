---
title: "wireless networking in kubuntu"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by GameboyHippo on 2008-07-31
If I start up ubuntu in gnome, my laptop connects to my wireless network without any problems.  If I start up in KDE 4.1, I don't get wireless access (except if I have been in gnome previously)  How do I get my laptop to autoconnect to my wireless network if I start up in KDE 4.1?

---

### Post by mailkarthi on 2008-07-31
I am facing the same problem. If login to gnome first and then to KDE my wireless works. But when I login to KDE directly  wireless is disabled. It is not even detecting my wireless hardware.

---

### Post by mailkarthi on 2008-08-02
For me, this turned to be just an UI problem. I was always clicking (left click) on the network manager and it keeps showing me a window with all buttons disabled. Then I right clicked on it today by mistake, to my surprise it showed me all the wireless network available and then I was able to select the one I wanted and able to connect it with out any problem

---

### Post by dodle on 2008-08-02
> **GameboyHippo said:**
> If I start up ubuntu in gnome, my laptop connects to my wireless network without any problems.  If I start up in KDE 4.1, I don't get wireless access (except if I have been in gnome previously)  How do I get my laptop to autoconnect to my wireless network if I start up in KDE 4.1?

It sounds like you may not have the Kde network manager installed.```
sudo apt-get install knetworkmanager knetworkconf network-manager-kde
```

Hope that works for you.

---

### Post by GameboyHippo on 2008-08-03
Okay, here is what I did to fix it.  I went to Computer -> System Settings -> Advance -> Autostart -> Add Program.  I then added nm-applet.  I made sure that the status was "enabled".  I then logged out and logged in and it works just like gnome now!

---

