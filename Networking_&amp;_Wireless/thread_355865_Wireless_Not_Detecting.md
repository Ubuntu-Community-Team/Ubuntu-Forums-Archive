---
title: "Wireless Not Detecting"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by jbraum on 2007-02-07
My wireless card is on automatically being detected.  I can manually config the wireless network and it works fine.  Any suggestions

I'm using a Belkin wireless card.

Thanks

---

### Post by chili555 on 2007-02-07
I suggest you explain what your problem is that you would like us to help you with.> it works fine doesn't sound like a problem.

What exact model of Belkin card is it? Please tell us what _doesn't_ work.

---

### Post by jbraum on 2007-02-07
I have one wireless connection at home and one a work.  Each time I boot with the card = Belkin Wireless G, I have to go into the network settings and set the card up for each connection.  It's not automatically detecting my card when I boot up.

I can go in and configure the card each time I connect but that's a pain .

Hopefully this helps.

---

### Post by gradedcheese on 2007-02-08
If you don't mind, can you tell us what steps you have to do when you boot up like this?  That would help me suggest what to do.  For example, what commands do you run, or what do you click on?

---

### Post by chili555 on 2007-02-08
I suggest you look into wifi-radar. [http://packages.ubuntu.com/edgy/net/wifi-radar](http://packages.ubuntu.com/edgy/net/wifi-radar)
> It enables you to scan for available networks and create profiles for your preferred networks. At boot time, running Wi-Fi Radar will automatically scan for an available preferred network and connect to it.

---

### Post by jbraum on 2007-02-08
> **gradedcheese said:**
> If you don't mind, can you tell us what steps you have to do when you boot up like this?  That would help me suggest what to do.  For example, what commands do you run, or what do you click on?

Once I login to the computer I have to go to sys>admin>networking>wireless connection and configure the ssid and network password anytime I am trying to connect to a new connection.

Example - Last night I setup my wireless connection with all of the above parameters.  This morning I login to the computer and the wireless automatically connected - good.  Shutdown, packed the computer up and took it to work with me.  Boot up at work and my wire card did not come on.  I had to do the above configuration (with a different ssid and password) to get the card to work at work.  Come home and I have to do the same at home.  Hope this a helpful.

---

### Post by gradedcheese on 2007-02-09
Ah, ok.  This is one of those things that wasn't handled very gracefully by the Networking tool, and Network Manager handles it much better (and will soon replace it).  Though currently it can only do DHCP (no static IPs).  I am not sure if its available for 5.10, but it might be.  

Hopefully I am not telling you to do something stupid (ie: there might be an easier way) but... the Networking tool just writes settings to /etc/network/interfaces (take a look and you'll see your SSID, key, etc).  The Networking tool also has 'locations' (home, work, etc) for which you're supposed to be able to configure different settings.  So you can try that and see if it works: at work, switch to the 'work' location, and so on.  If not, you can just have two (or more) copies of differently-configured /etc/network/interfaces and have a script allow you to swap them as needed :)  The latter is certainly not the solution you're looking for.

WiFi radar (as recommended by chilli555) is another tool that you might try, it's sort of like Network Manager and a lot more user friendly than the default Networking app.  It can also to 'locations'.

---

### Post by jbraum on 2007-02-10
This is whats in my etc/network/inferface

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






iface ra0 inet dhcp
wireless-essid Lily
wireless-key xxxxxxxxxx

auto ra0

I imagine I need to make changes to auto ra0 as that might be the reason I'm not getting auto detection of my card??? Don't know for sure.

---

