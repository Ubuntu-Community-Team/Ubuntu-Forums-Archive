---
title: "IP Address Keeps Changing"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by skorpi0wn on 2007-06-12
Greetings

I'm running Ubuntu 7.04 Server Edition as a home-based file server.  I have the file /etc/network/interface setup as the following:

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1


Occasionally, I am not able to connect to the server from other machines in my house.  After checking out the ip addresses in my router, I noticed that the ip address of the linux box is getting changed.  (Most recently, it held 192.168.1.100 for about 3 weeks then tonight it changed to 192.168.1.7.)   I have to then login and run /etc/init.d/networking restart to get the ip address back to the static one I have set.

Has anyone else experienced a problem like this and is there a fix for it?

Any and all help is most appreciated.


Update:  I noticed this in syslog.  I wonder if dhclient is doing something?

Jun 12 22:32:33 steve dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Jun 12 22:32:33 steve dhclient: DHCPNAK from 192.168.1.1
Jun 12 22:32:33 steve dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jun 12 22:32:40 steve dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jun 12 22:32:41 steve dhclient: DHCPOFFER from 192.168.1.1
Jun 12 22:32:41 steve dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 12 22:32:43 steve dhclient: DHCPACK from 192.168.1.1
Jun 12 22:32:43 steve dhclient: bound to 192.168.1.7 -- renewal in 36438 seconds.

---

### Post by aberry5555 on 2007-06-13
Ok this might be a stupid question but in the network option under administration have you switched DHCP off?

<-- EDIT --> as a workaround, if you have turned it off and it's still doing it you could always fiddle with your router and have it prioritise your MAC address to the address you want, then turn DHCP back on in your settings, that way even though it's running off DHCP it will always be 192.168.1.100

---

### Post by skorpi0wn on 2007-06-13
> Ok this might be a stupid question but in the network option under administration have you switched DHCP off?

Actually, I don't think that I have.  How is this accomplished through the command-line?  I don't have any GUI tools installed.

---

### Post by ralyon on 2007-06-16
> **skorpi0wn said:**
> Occasionally, I am not able to connect to the server from other machines in my house.  After checking out the ip addresses in my router, I noticed that the ip address of the linux box is getting changed.  (Most recently, it held 192.168.1.100 for about 3 weeks then tonight it changed to 192.168.1.7.)   I have to then login and run /etc/init.d/networking restart to get the ip address back to the static one I have set.

Has anyone else experienced a problem like this and is there a fix for it?

I am having the exact same problem, although I am running the feisty x64 desktop edition. My setup that has worked fine for a year now was having the router assign the address to 192.168.1.6 based on mac address. However, 3 days ago I noticed that I couldn't connect to my server and upon checking the server its address had changed to .4.

A ifdown, ifup was able to fix it at first but it kept changing to something other than .6 so I set it to static in the network settings gui and several hours later iifconfig showed had again changed to a different address even though the setting still said it was static at .6.

The only change to my computer was an added netgear nic because my onboard nic was locking up on upnp client access. Other than that just the standard updates. I have a feeling this isn't hardware related because yesterday my mb died and I had to move everything into a different box so the only hardware that was moved was the hdds and the 2 tv tuner cards. Everything else is different.

Anyone have any suggestions or would like any additional info?

---

### Post by linux noooob on 2007-06-16
go to your router and set a static IP and everything should work fine (worked for me).

---

### Post by ralyon on 2007-06-16
> **linux noooob said:**
> go to your router and set a static IP and everything should work fine (worked for me).

Not sure what you are referring to  as the routers address has always been a static IP and as I said it was assigning an IP of 192.168.1.6 based on mac address and during the testing I had set it to static on the local machine. Could you be a little more specific?

---

### Post by nixfaced on 2007-06-16
> **ralyon said:**
> My setup that has worked fine for a year now was having the router assign the address to 192.168.1.6 based on mac address. 

The only change to my computer was an added netgear nic because my onboard nic was locking up on upnp client access. 

Anyone have any suggestions or would like any additional info?

Did you update your router settings to map 192.168.1.6 to your new netgear nic's mac address?

> **skorpi0wn said:**
> Actually, I don't think that I have.  How is this accomplished through the command-line?  I don't have any GUI tools installed.

sudo killall -TERM dhclient3 should do it for you.

---

### Post by ralyon on 2007-06-16
> **nixfaced said:**
> Did you update your router settings to map 192.168.1.6 to your new netgear nic's mac address?

Yes, when I connected the netgear nic I used the router to view connected devices and copied that mac address to the reserved address for 192.186.1.6. It would get that address at first and the clients could connect via that address, but then several hours later I would check and it had changed again.

---

### Post by ralyon on 2007-06-17
Well I couldn't stop playing with it. I tried setting everything manually in the interfaces file but I ended up locking up gnome with just the default background and some white screen that would pop up in the left top corner with no text on it. Additional fiddling didn't help and I could ping a web server(google) but couldn't get back to gnome. So I took out the install cd and wiped it clean. (My wife would have killed me if she wasn't able to play The Backyardigans for our son on monday.)

If you don't hear from me then the problem went away with the clean install. Otherwise I'll be back.

Thanks for everyones suggestions!

---

