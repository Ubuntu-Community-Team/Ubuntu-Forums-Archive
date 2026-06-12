---
title: "Network Manager at start up"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by miseljt on 2007-01-23
Hey all, this is my first post on the forum and I'm very new to Ubuntu. Thus far, I'm very impressed with the amount of help I've already received from different threads. I've been looking through the Network Manager posts to see if this problem has been addressed and I haven't found any to my knowledge.

I'm using the network manager you get through apt-get. It's installed properly and is working. The problem comes up whenever I shut my laptop down and then restart it later. In my day to day routine I'll be on one of three networks, which isn't a problem. When I restart my computer, the network manager doesn't start back up, I have to go through and restart the manager.

When I restart it I:

sudo killall NetworkManager
sudo /etc/init.d/networking restart
sudo NetworkManager

Once I cycle through all of those, the Network Manager is available again.

Specs: Edgy, Intel PW2200.

Is there a script I could write to cycle that for me whenever I reboot or anything like that? Thanks in advance.

---

### Post by coffeecat on 2007-01-23
I assume you are using the Gnome desktop. If so, have you got the network-manager-gnome applet installed? If not you can install it via Synaptic. If it is already installed, check System > Preferences > Sessions. Select the Startup Programs tab and make sure this code:

```
nm-applet --sm-disable
```is in the Command field. Then the network manager applet should start every time you boot up. One irritation about it - it demands a keyring password (not the encryption password) each time before it will connect. You choose this password when you first use it.

I use network manager on my laptop (both Dapper and Edgy on different partitions) with Intel ipw2200 and it works fine and starts up on each bootup.

---

### Post by miseljt on 2007-01-23
Thanks a lot. Yeah, sorry I didn't include my desktop type. I'm assuming you mean between Gnome and KDE. I had that code in the Sessions tab, and when I restarted to test it, this was the first time it asked me for my keyring password before everything finished logging in. Thanks again!

---

### Post by Azakus on 2007-01-24
You can get rid of that keyring necessity if you install keyring-manager and delete the keyring password.

---

### Post by Floppyjoe on 2007-01-24
> **Azakus said:**
> You can get rid of that keyring necessity if you install keyring-manager and delete the keyring password.

I can't delete the session key using gnome-keyring-manager for some reason. I keep getting a cannot connect to keyring daemon error.

---

