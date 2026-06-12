---
title: "Weird wireless issue"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by alienseer23 on 2006-08-14
I use a Linksys wireless, I have it working fine with Dapper Drake, it was a pain, but I finally figgured it out. But, every time I reload X, I have no network usage at all untill I click on the properties, and the configure tabs for this connection...then it magically works. I do not have to adjust anything, just click to configure it, and it turn on right there.
How do I get this to just simply work???

Thanks....AS23

---

### Post by mjziegle on 2006-08-14
You have a few options here.  

Two questions...

1.  Are you using network manager?
2.  Post you /etc/network/interfaces file

-mjziegle


> **alienseer23 said:**
> I use a Linksys wireless, I have it working fine with Dapper Drake, it was a pain, but I finally figgured it out. But, every time I reload X, I have no network usage at all untill I click on the properties, and the configure tabs for this connection...then it magically works. I do not have to adjust anything, just click to configure it, and it turn on right there.
How do I get this to just simply work???

Thanks....AS23

---

### Post by alienseer23 on 2006-08-14
No, I am not using a manager program, and here is the file you asked for



auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.17
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid XXX
wireless-key XXX

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0



I XXX 'ed out the ssid and key.


thanks :)

---

### Post by mjziegle on 2006-08-16
How many network devices do you have in this computer?  It looks like you have 3 wired and 2 wireless connections.  It seems to me that your static eth0 take precedence over your ath0 or wlan0 (wireless) which is why you have to manually start every time.

I would suggest using network manager which will consolidate your connections and use the best one.  To install 

sudo apt-get install network-manager-gnome

Then change your /etc/network/interfaces to

auto lo
iface lo inet loopback

Reboot and configure from the new nm-applet icon in the tray.  You'll have to setup a keyring password.  Another plus with network manager is that you can use WPA pretty easily vs. the WEP which you have now.



> **alienseer23 said:**
> No, I am not using a manager program, and here is the file you asked for



auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.17
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid XXX
wireless-key XXX

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0



I XXX 'ed out the ssid and key.


thanks :)

---

### Post by Kodiak3000 on 2006-08-16
Can I piggyback on this thread?  I'm trying to configure a Linksys WMP54G on my Ubuntu box to run off our WAG54G gateway.  I've followed all the tutorials I could (the ones that made sense to me, anyway), and I've got the thing being recognised and I can activate it, but I still can't connect. 

I think the problem is that I don't know how to configure the gateway to allow this machine to access it.  Sounds stupid, because I got it to work on my Windoze box, and I do't have any problem getting in to the gateway's admin...

Any thoughts?

Thanks

Update - I installed Network Manager - very cool! - but I still can't connect to the wireless network.  Wired network works fine - always has - but still no wireless...

---

### Post by alienseer23 on 2006-08-18
Thank You! That worked like a charm! A minor pain in the butt now gone, isn't that what life is all about?

UPDATE: Ok, It was going well for a moment using your fix. But, I need to know about static ip with network manager? I really need that. So, I also tried this on my second ubuntu machine, and it really did not want to work. It just kept asking for the key over and over again, that is when I looked to notice that network manager had the very wrong ip for this machine (a static for another comp in the home, which is outside the ip range of my dhcp server, very odd). So, I set back this and the other ubuntu to a static under gnomes own network tools, and it worked to get them back online. Any ideas? I think I just need to set static ip's for both of them thru this new network manager, but how? i didn't see that anywhere.

---

