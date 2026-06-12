---
title: "Connecting to wired and wireless networks"
date: 2015-01-16
forum: Networking &amp; Wireless
---

### Post by chris_h2 on 2015-01-16
I know there are similar threads, but I don't believe my requirements are quite the same.
I am developing an application for use in public venues. As part of the kit I provide a Ubuntu server and a wireless router. I (or rather the venue owners) don't want the public connecting to their WiFi, or routing to the internet through their broadband connection. The wireless router I provide will give the public access to a web site on my Ubuntu box only. I want my Ubuntu box to also connect to the venue's broadband so that I can administer it remotely.

To do this, my server needs to connect with a cable my router (no internet access) for venue customers and wirelessly to the private internet-connected router owned by the venue (for remote maintenance by me) on 2 completely separate networks.

So I have my server connected to my router via eth0 and configured in /etc/networks/interfaces to use a static ip suitable for my router and everything is fine - I can connect to the web site from another device and do my stuff. For testing, I am using my broadband router, so this also gets access to the internet.

I plugged in a WiFi dongle into the USB port and Ubuntu recognised it immediately and a WiFi symbol appeared in the top of the desktop. I opened that and it gave me a list of networks to connect to, so I connected to the same house broadband router. ifconfig showed that it had the static ip from the eth0 and a DHCP-assigned address from the wlan0. As soon as I did this, the server lost access to everything. I couldn't access internet any more or ping any other machine on my network. I also couldn't ping the server from any other machine using either address. When I then disconnected from the WiFi and even unplugged the wireless dongle I still couldn't do anything. I had to reboot the server to get back to where I started. Since both networks in my test environment are actually on the same network, with internet, I'm confused as to why all network traffic just ceased.

Incidentally, my Windows laptop when docked has both wired and wireless DHCP connections to the same router.

I suspect it's something to do with Network Manager - I was advised to turn it off to set up my static ip on eth0, so I was a bit surprised when I didn't have to manually configure the wlan0. I'm guessing I should also put this in /etc/network/interfaces too? But then how to configure the WPA2? It seems like this would be difficult to manage remotely - if the venue changed the SSID or passphrase then I would lose all remote access. I'm just a little confused why I can't just configure both interfaces easily in a simple GUI.

Sorry for my naivety - I'm not that well up on Ubuntu networking fundamentals.
Any help or advice would be much appreciated.
Thanks,
Chris

---

### Post by newbie-user on 2015-01-16
Without much knowledge of your setup, I'm guessing you have the gateway attribute set for eth0 in /etc/network/interfaces. Just remove that.

In my experience, Network Manager doesn't work right when used at the same time as /etc/network/interfaces. I'd recommend getting rid of Network Manager and the GUI all together if you're just running a web server. Here's some info on how to do wpa in /etc/network/interfaces: [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal]("http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal")

---

### Post by chris_h2 on 2015-01-19
Thanks, I'll try that

---

### Post by SeijiSensei on 2015-01-20
Make sure the eth0 and wifi connections are on two entirely distinct network subnets, like 192.168.50.0/24 and 192.168.51.0/24.  If you need to send traffic from one interface to the other, you'll need to enable IP forwarding in /etc/sysctl.conf by removing the "#" from the line "net.ipv4.ip_forward=1" and rebooting.  Without forwarding enabled, users on one network can see all its resources but not resources on the other network.  That might be what you want in this case.

I'd also avoid things like NetworkManager and configure static addresses on both interfaces in [/etc/network/interfaces]("https://help.ubuntu.com/14.04/serverguide/network-configuration.html#static-ip-addressing").

---

### Post by chris_h2 on 2015-01-23
There seems to be conflicting advice here on whether or not to use NetworkManager. I have been searching and found quite a few instances where people have said not to use it, but I have never seen any explanation of why.
For my system, I want the WiFi to use the venue's router. If they for some reason change the SSID or passphrase, then it would seem to be easier to talk them through using the GUI to re-enable the internet link, therefore enable me to do remote support than to talk them through editing a /etc/network/interfaces file. There is also the issue that I would need to get them to log onto the machine and give them sudo access in order to modify this file, so if it can be done through the NetworkManager I think that would seem preferable.
Unless someone more knowledgable than me knows different.....

---

