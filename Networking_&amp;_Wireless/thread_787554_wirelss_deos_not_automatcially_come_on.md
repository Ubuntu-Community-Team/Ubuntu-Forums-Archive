---
title: "wirelss deos not automatcially come on"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by nanjil on 2008-05-09
hardy 8.04

when the machine turns on the wireless does not become automatically become active. I have to physically log in the machine. how can i make the wireless come on as part of the boot up?

I had similar problem a year ago in fiesty, which was solved by simple modification to /etc/network/interfaces file. but that solution does not work in hardy. actually if i change the interface file , the wireless connection completely goes off

---

### Post by amohanty on 2008-05-09
Hardy uses NetworkManager which is directed by the network applet in the gnome panel. By default that is what is used. Since only nm-applet (the panel applet) can talk to NetworkManager (you can chat with it via dbus-send - however the dbus api is not very well documented), and the panel applet will only start when gnome-panel starts - which in turn will only start when you login you dont really have that much of a choice.

However, if the interfaces files specifies the wireless interface then NetworkManager will ignore it. So you might have to munge with your /etc/network/interfaces again.

HTH
AM

PS:

post the output of:
sudo ifconfig -a

and the contents of your non-working /etc/network/interfaces file.

---

### Post by nanjil on 2008-05-09
when i travel i log onto my machine. so if the network is tied to the gnome panel , then if the power goes down, the machine has to be now both started and somebody has to log in before the network can come on!!

ok here are the outputs

/etc/network/iinterfaces

auto lo
iface lo inet loopback



ifconfig -a 


thanx

---

### Post by amohanty on 2008-05-10
man that's 3 network interfaces!! Unfortunately I don't know which one you were connected to the network with, but assuming that that was the wireless one, try adding the following to your /etc/network/interfaces file by doing:

sudo gedit /etc/network/interfaces

The in the file put the following:

auto ath0
iface ath0 inet dhcp
wireless-mode managed
wireless-essid your_access_point_ssid
wireless-key your_access_point_key

This also assumes you are using basic WEP hex key encryption. If you are using WPA/WPA2 this changes and you need to use wpa_supplicant.

HTH
AM

---

### Post by amohanty on 2008-05-10
man that's 3 network interfaces!! Unfortunately I don't know which one you were connected to the network with, but assuming that that was the wireless one, try adding the following to your /etc/network/interfaces file by doing:

sudo gedit /etc/network/interfaces

The in the file put the following:

auto ath0
iface ath0 inet dhcp
wireless-mode managed
wireless-essid your_access_point_ssid
wireless-key your_access_point_key

This also assumes you are using basic WEP hex key encryption. If you are using WPA/WPA2 this changes and you need to use wpa_supplicant.

HTH
AM

---

### Post by nanjil on 2008-05-12
no luck ; the /etc/net/work/inteface has any lines in hardy. if i add those lines immediately my wireless stops working

---

### Post by nanjil on 2008-05-12
I am actually connected only through the wireless network throuhg the dlink card.

---

### Post by amohanty on 2008-05-15
> **nanjil said:**
> no luck ; the /etc/net/work/inteface has any lines in hardy. if i add those lines immediately my wireless stops working

I am not sure what you mean by the first sentence.
Yes it will stop working because NetworkManager only handles interfaces that are in roaming mode. By specifying them in the file, you changed that. 

To start it simply do the following in a terminal:
sudo ifdown ath0 && sudo ifup ath0

You will not have to do it everytime because the next time you boot it will automatically connect even before you login. However keep in mind that after a sleep/hibernate it may not reconnect by itself.

AM

---

### Post by btermeli on 2008-05-15
Hi,

I have a similar problem, I can see my wireless networks but it doesnt established automatically. Everytime I have to choose the network and type the pass.

Can u recommend something about that?

---

### Post by amohanty on 2008-05-15
try wicd - in my experience it has performed way better than networkmanager.

AM

---

