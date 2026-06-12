---
title: "setting up wireless"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by SpikeyMike on 2007-02-10
Hi

I have just installed Ubuntu on my laptop, I already have it on my main pc with a wired connection and it works fine but I don't know how to configure a wireless connection.  I have a broadcom wireless adaptor. I think this is recognised ok as it shows up when I go to Networking and I can configure it as DHCP or static.  Do I need to install some other software so I can see my wireless network?

Any help appreciated

Spikey

---

### Post by jan247 on 2007-02-10
You don't need any additional software on this one, and it's not pretty hard to configure from where you are. But it is tedious to do so for every wireless network you visit. So, skipping configuration instructions, I suggest you use some wifi tool instead. The one I'm using is the NetworkManager Applet, which you install by typing the following over the command line:

```

sudo apt-get install network-manager-gnome

```

To save you the trouble, sometimes network-manager-gnome doesn't detect your wifi device. Head over to /etc/network/interfaces and remove any lines with traces of wlan and eth1 (since in my case, eth0 is wired, eth1 is wireless). If you do so, simply reboot the system, and it'll work fine.

---

### Post by SpikeyMike on 2007-02-11
Hi, thanks for your reply, I did what you said to install the network manager and it seemed to install ok but how do I use the network manager? Is it possible for me to open it and see the wireless networks available in my area so I can select to connect to mine?  also i'm not sure what you meant in the last part about removing any traces of lines with wlan and eth1,  below is a copy of my /etc/network/interfaces file, after installing the network manager I rebooted but I still cannot connect to my wireless network.

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet static
address 192.168.1.19
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid TheStudio
wireless-key s:mypass001

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp

auto eth1

auto eth0

---

