---
title: "Configuring the Linksys WMP54G and WEP"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by Dorsai on 2007-04-28
Thought I would share my install of the Linksys WMP54G PCI wireless NIC on Feisty.

1.) Download Wicd here - 

[http://compwiz18.ig3.net/wicd/wb/](http://compwiz18.ig3.net/wicd/wb/)

2.) Print the Wicd FAQ about "Do I have to remove ubuntu-desktop to install wicd?". You'll have to follow the steps about uninstalling Network-Manager before proceeding.

3.) Once you have Network-Manager uninstalled and Wicd installed go ahead and follow the FAQ about "Is there a tray icon? ". This will give you an icon in the system tray that you will be able to right click on to adjust connection properties.

4.)If you installed Feisty with the NIC already in your computer you should be able to go into System/Preferences/Hardware Information and verify that your hardware was detected and is installed on the PCI bus. 

5.)Now you have to adjust the network file to change some settings. Open a terminal and type:
sudo gedit /etc/network/interfaces

6.)Once the file is opened make a back up copy and then edit it to look like this; of course use your actual essid and key -

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ra1
iface ra1 inet dhcp
wireless-essid YOUR ESSID
wireless-key YOUR WEP KEY

Make sure you delete all of the other lines from the file. 

7.)Save the file and restart the network interface by typing - 
sudo /etc/init.d/networking restart

You should see your NIC talking to your router at this point as it trys to acquire a DHCP connection. If successful you'll see a release/renewal notice.

---

### Post by PartyTaco on 2007-05-11
I cannot find that FAQ page or the "do I have to uninstall ubuntu-dekstop to install wicd?" page either. If Someone could tell me how to uninstall network manager I would be very happy!

---

### Post by JeevesBond on 2007-05-24
> **PartyTaco said:**
> I cannot find that FAQ page or the "do I have to uninstall ubuntu-dekstop to install wicd?" page either. If Someone could tell me how to uninstall network manager I would be very happy!

The FAQ seems to have disappeared from their site. Uninstalling network-manager is as simple as typing:

```
sudo apt-get remove network-manager
```

Or you can go into your package manager, then search and remove it from there. wicd will not install unless you remove the network-manager, after doing that it worked for me.

---

### Post by doctorzizmore on 2007-05-29
you kick some serious *** Dorsai.  Worked like a charm.  Thanks

---

### Post by doctorzizmore on 2007-05-29
Actually this worked fine until I restarted my computer.  Now I can't get it to work again!!! wicd comes up on startup and says that I have a good connection only Firefox won't load any pages.  What's going on?  Thanks.

---

### Post by ikkubus on 2008-06-26
this doesn't work on me :(

---

