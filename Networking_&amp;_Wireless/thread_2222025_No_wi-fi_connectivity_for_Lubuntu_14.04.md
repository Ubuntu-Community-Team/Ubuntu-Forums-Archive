---
title: "No wi-fi connectivity for Lubuntu 14.04"
date: 2014-05-04
forum: Networking &amp; Wireless
---

### Post by History Teacher on 2014-05-04
I just updated a Lenovo G470 laptop to Lubuntu 14.04.  However, it is not recognizing my wi-fi modem.  The modem, which is working fine, is not showing up under network connections.

Any suggestions on how to resolve this?

Thanks!

---

### Post by DogMatix on 2014-05-04
Is the network manager icon showing with the indicator applets next to the clock in the lxpanel?

If it isn't try opening a terminal and typing:

```
nm-applet
```

The network manager applet icon should then appear and left-clicking on it will reveal a list of available networks.

This is an issue I've experienced with fresh installs of Lubuntu 14.04 and on an upgrade I performed the network manager applet no longer auto started.

---

### Post by History Teacher on 2014-05-04
Thanks.  That code launched the applet perfectly.  However, it is still not recognizing the wi-fi.  The message is "no network connection" and the wi-fi modem does not show up in the network connections box.

---

### Post by DogMatix on 2014-05-04
Have you tried right clicking on the applet icon and checking 'Enable Wi-fi' ?

---

### Post by geral-k on 2014-05-04
Click on the Network Manager applet.&#8194;Then click on Edit. You may need to configure your ESSID, password etc. After entering all the data needed, close the Edit window. You may then need to disable wifi and then enable it.

---

### Post by History Teacher on 2014-05-10
The Network Manager applet does seem to recognize my modem.  The little lock sympol shows up on the left of the signal status bars.  Wi Fi is enabled.  I'm guessing it has something to do with my password? 

I get stuck when I try to add the connection.  I enter the modem name, select wi fi from the drop down menu, and I get to the editing Wi Fi box.  Under the Wi Fi tab boxes for SSID, Mode, BSSID, Device MAC address, Cloned MAC address, and MTU.

I'm not sure what to do at this point.  I'm still pretty much a newbie.

Thanks for all your help!

---

### Post by geral-k on 2014-05-15
Hello, sorry for my late answer. So in case you are still facing the same problem:

1. The little lock on the left of the signal status bar means your WiFi network is protected by password. You obviously do need to know both the password and the encryption system used (WEP or WPA). You also need to know the name (SSID) of your WiFi network (SSID). Normally, if you click on the signal status icon, the drop-down menu will list the nearby networks available. From your description, I gather you have been able to enter the edit menu.

2. Using the Edit menu: Under the "General" tab, check the first two squares (automatic connection and permission for all users to connect); leave the third square (VPN) unchecked.

3. Go to the Wi-Fi tab. Type the name of your WI Fi net into the SSID field. Let  the mode be "infrastructure" (the default). The BSSID parameter is optional, so you may leave it blank, unless you want to lock your connection to this particular access point. Let the device MAC address be the one Network Manager chose for you; in the unlikely event your router does not accept this MAC address, you will have to use a cloned one (next field), but normally you should leave this field blank. Finally, let MTU be "automatic" (the default).

4. Go to the "Security" tab. Choose your encryption system (most routers use WPA-WPA2 personal) and type in your password.

5. Go to the "IPV4 Settings" tab. "Method" should be set to "Automatic" by default. If your router allocates dynamic addresses (IPs) to the computers linked to it, that is, if it uses DHCP, then you're ready; and this is the most common case. However, if your network uses static addresses like mine does, you will have to type in the IPV4 or IPV6 parameters.

6. Click on the "Save" button. You may have to disconnect and then reconnect, using the drop down menu. A warning should appear, telling you your computer has been connected to the WiFi net.
 
Let us know whether this has worked for you. Best wishes.

---

