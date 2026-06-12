---
title: "wireless interface missing from network manager Intel
	

PRO/Wireless 4965 AG(N)"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by sheepfunk on 2008-01-06
While many others have posted on this topic, nothing from the forums has seemed to work for me, so please help if you have had any experience with this before. 

Essentially my wireless connection disappeared from the Network Manager a couple days a go after a reeboot. As Far as I know I was not doing any thing out of the ordinary at the time. 

What I know...

1. The Device is recognized

"lshw -C network" shows the wireless card

- PRO/Wireless 4965 AG or AGN Network Connection

2. The device is not being used as a netwok interface

-it doen't show up when I run "ifconfig" 


What I've tried... 

1. Mainly I've tried using windows drivers to install the card, until I realized there was a native linux driver for this wireless card, 

Now I'm not even sure if this is a driver issue.

2. I've reinstalled ubuntu (kinda drastic but this is a rough issue for me) when I reinstalled, the wireless interface did not autodetect, like it did the first time I installed

3. I've edited /etc/network/interfaces

I added:

auto wlan0
#iface wlan0 inet dhcp

but this didn't seem to do anything.


The long story short is that I really don't have any idea what is happening, and I'm just taking random suggestions at this point, so any help would be incredibly appreciated.

---

### Post by hebetude on 2008-02-02
for poops & giggles try

sudo ifconfig wlan0 up

It should at least show up in ifconfig then

---

### Post by zorkerz on 2008-03-22
hmm my 4965 just stopped working today in hardy.

What am i looking for in ifconfig? I see wlan0 but not the 4965 card name anywhere. 'sudo ifconfig wlan0 up' did not appear to change anything.

I see lots of wireless networks in nm-applet but when i try to connect it just spins on.

---

### Post by hebetude on 2008-03-22
restarting the applet helps me
sudo /etc/dbus-1/event.d/25NetworkManager restart

---

### Post by PetePhillips on 2008-05-01
edit 

  /etc/network/interfaces

and  make sure you comment out all lines which refer to interfaces you want nm-applet to manage for you.

Mine looks like this:


```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

#iface eth0 inet dhcp


#iface eth0 inet dhcp
#iface eth1 inet dhcp

#auto eth1

```

restart your networking and try again.

---

### Post by zorkerz on 2008-05-01
Thanks for that. I should have gotten back to this post. This was fixed for me at some point during hardy development.

---

