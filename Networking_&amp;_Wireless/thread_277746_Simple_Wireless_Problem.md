---
title: "Simple Wireless Problem?"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by ART_Adventures on 2006-10-15
I am new to Ubuntu, and I'm not a skilled Linux user. But, I have now setup my wireless card (Netgear: WG511v2). I have two wireless connections, both use WEP. Both work on wired connections, and I have access to the router settings for each one.

The problem: When it comes to wireless, I can only connect to one connection, but not the other.

Can anybody help me? What kind of settings can I check on the router that might affect how this works?

Thanks.

---

### Post by wieman01 on 2006-10-15
The file that controls your network connections is this one"
> sudo gedit /etc/network/interfaces
You can post the contents so that we can help.

---

### Post by ART_Adventures on 2006-10-15
Thanks for the reply. Here is the file.

```

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


iface wlan0 inet dhcp
wireless-essid MY_SSID
wireless-key MY_KEY


auto wlan0

```

As I mentioned, it can connect to one wireless router, but not the other.

Thanks.

---

### Post by wieman01 on 2006-10-15
Ok, basically [COLOR="Red"]MY_SSID[/COLOR] stands for your network's ESSID, [COLOR="Red"]MY_KEY[/COLOR] for your **WEP** password, you have figure that out I guess.

So in principle all you need to do is replace both password & ESSID so that it matches with either one of the networks. Have you tried that?

If this does not work, please check the router settings & confirm that both are set to WEP and have a password. 

You don't want to connect to both router at a time, right?

---

### Post by wieman01 on 2006-10-15
And also check that both routers have **[COLOR="Red"]DHCP[/COLOR]** enabled. That done try to reconnect this way:
> sudo /etc/init.d/networking restart
And post the ouput please for each connection.

---

