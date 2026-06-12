---
title: "Saving wireless settings"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by meng on 2006-11-24
Here's the issue: Edgy installed on my Dell laptop, everything works great until I changed my wireless network's WEP key a couple days ago. Now every time I boot the laptop, I have to manually change the WEP key from the old one to the new one. Furthermore, the GUI configuration program (System > Admin > Networking) doesn't seem to make any changes! I have to drop to the command line and "sudo iwconfig eth1 key ..." and "sudo dhclient eth1" to make the changes and re-establish my internet connection.

So who knows what's going on here? Is there some configuration file that's read at startup that I have to edit?

---

### Post by wieman01 on 2006-11-24
Give this one a try & post the contents:
> sudo gedit /etc/network/interfaces

---

### Post by meng on 2006-11-24
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid [essidname]
        wireless-key1 [oldkey]
        wireless-key [newkey]


So, should I just replace the last two lines with:
wireless-key1 [newkey]
???

---

### Post by wieman01 on 2006-11-24
Are you using "ndiswrapper" by chance? Try to replace the contents of the files with this:
> auto lo
iface lo inet loopback

[COLOR="Blue"]auto eth1[/COLOR]
iface eth1 inet dhcp
wireless-mode managed
wireless-essid [COLOR="Red"]your_essid[/COLOR]
wireless-key1 [COLOR="Red"]your_current_key[/COLOR]
Then restart the network & post the output:
> sudo /etc/init.d/networking restart
If this does not do the job, replace the **"wireless-key1"** line with **"wireless-key"** and try again.

---

### Post by meng on 2006-11-24
I used wireless-key1 and it worked out.

---

### Post by wieman01 on 2006-11-24
Just one question: Do you use "ndiswrapper" for your wireless adapter?

---

### Post by borobudur on 2006-11-25
Hi guys, can I ask you something to this topic?

Is it possible to have two settings in the /etc/network/interfaces file for the same interface like 

```
iface eth0.0 ...
iface eth0.1 ...

```

It's quite annoying to change the setting all the time on my laptop. I saw something [here]("http://www.freewrt.org/trac/wiki/Documentation/Howto/Network") but it didn't work with me.

---

### Post by wieman01 on 2006-11-25
In Ubuntu? Not that I am aware of. If you need to switch regularly, I recommend graphical tools such as Wifi-Radar or NetworkManager.

---

### Post by meng on 2006-11-25
> **wieman01 said:**
> Just one question: Do you use "ndiswrapper" for your wireless adapter?
No, my Dell Trumobile 1150 worked out of the box with both Dapper and Edgy.

---

