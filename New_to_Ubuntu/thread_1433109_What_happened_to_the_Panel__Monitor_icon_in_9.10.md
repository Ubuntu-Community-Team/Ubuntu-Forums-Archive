---
title: "What happened to the Panel  Monitor icon in 9.10????"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by suomalainen on 2010-03-18
Ubunteros,

I just upgraded from 8.04LTS to 9.10.

In 8.04LTS the panel contained a monitor icon. When clicked upon the monitor icon would provide services like information on wired broadband connection or allow connectivity to the Internet via a wireless connection like 802.11G. In short it described your network connection.

Now that I have upgraded to 9.10 it appears the icon may have changed as seen in the attached picture. In this case, I'm referring to the first icon found to the left.

When I installed 9.10 for the first time this icon was always present. However, When I configured my wireless card and entered its password this "monitor icon" changed to an additional loud speaker icon and I wasn't able to select the type of network connection I wanted.

To get around this, I went to system > Preferences > Network Connections and changed the password to the card. Then rebooted. Once I did this the second loud speaker icon in Panel disappeared and the new icon representing connectivity to the network appeared. Again, this icon is seen in the attached picture and is the first icon to the left.

It seems to me that 9.10 is a little buggy. Regardless, does anyone know why my Monitor icon disappeared after I had configured my access to the wireless network???

Thank You!

---

### Post by eronisko on 2010-03-18
I might have missed it, but did you attach the mentioned files?

---

### Post by suomalainen on 2010-03-18
Here You go and thanks!

---

### Post by plucky on 2010-03-18
Alt+F2 ```
nm-applet &
``` and see if it appears.

Good Luck

---

### Post by tom.swartz07 on 2010-03-18
> **suomalainen said:**
> Ubunteros,

I just upgraded from 8.04LTS to 9.10.

In 8.04LTS the panel contained a monitor icon. When clicked upon the monitor icon would provide services like information on wired broadband connection or allow connectivity to the Internet via a wireless connection like 802.11G. In short it described your network connection.

Now that I have upgraded to 9.10 it appears the icon may have changed as seen in the attached picture. In this case, I'm referring to the first icon found to the left.

When I installed 9.10 for the first time this icon was always present. However, When I configured my wireless card and entered its password this "monitor icon" changed to an additional loud speaker icon and I wasn't able to select the type of network connection I wanted.

To get around this, I went to system > Preferences > Network Connections and changed the password to the card. Then rebooted. Once I did this the second loud speaker icon in Panel disappeared and the new icon representing connectivity to the network appeared. Again, this icon is seen in the attached picture and is the first icon to the left.

It seems to me that 9.10 is a little buggy. Regardless, does anyone know why my Monitor icon disappeared after I had configured my access to the wireless network???

Thank You!

Im not quite sure of the problem. The icon there, the two plugs connected, -- what Im assuming you refer to as the 'monitor icon'-- is called the network manager applet. Its the same one as in 8.04, it just has a different icon image. Clicking on this icon still brings up network connection choices. As you were describing, you could right-click on it and configure the networks.

You could add the network applet yourself - right click on the panel and add the applet

---

