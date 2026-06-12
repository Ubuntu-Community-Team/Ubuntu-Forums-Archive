---
title: "NetGear WG111t problem"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by Caponetta on 2008-07-10
I followed everything in the tutorials here at Ubuntu Forums.

I boot up, run 

```
sudo modprobe ndiswrapper
```

I plug in my adapter and the Windows Wireless Drivers app says hardware is detected. But i dont get an option to connect via wireless.

Can someone help me?

Thanks in advance.

---

### Post by Caponetta on 2008-07-10
Bump!

This is a big problem.

---

### Post by CarlosNYB on 2008-07-21
> **Caponetta said:**
> I followed everything in the tutorials here at Ubuntu Forums.

I boot up, run 

```
sudo modprobe ndiswrapper
```

I plug in my adapter and the Windows Wireless Drivers app says hardware is detected. But i dont get an option to connect via wireless.

I don't know if this will help.

I tried downloading the ndiswrapper packages with dependent packages and installing them in the console, when I had Ubuntu Studio (Heron-based), but I wound up just starting fresh with a normal distribution of Hardy Heron, and then I used Synaptic with the Hardy Heron CD, to install the ndisgtk package with dependent packages.  When I did that, I found in the menus: SYSTEM >> ADMINISTRATION >> WINDOWS WIRELESS DRIVERS.  Then I was able to direct the Windows Wireless Drivers Applet to the "ndis5" folder.  This made a Wireless Network detector appear on the menu bar near the user login applet.  When my router is not set to WAP or WEP, it was detected when I went to SYSTEM >> ADMINISTRATION >> NETWORK and set the wireless network to 'roaming'.  I didn't mess with it after that, because it worked, I just have to plug the dongle in after starting Ubuntu and it's detected automatically, and I don't feel like fooling with WAP/WEP.  It didn't work after a few tries and when it worked without it, I was happy to have a working connection.

So anyhow, you may want to try installing the packages strait from the Hardy Heron installation CD.  Set Synaptic to use the CD in its respository >> third-party settings.

---

