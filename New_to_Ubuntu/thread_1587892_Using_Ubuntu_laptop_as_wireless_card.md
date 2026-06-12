---
title: "Using Ubuntu laptop as wireless card"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by random turnip on 2010-10-04
Basically i have a desktop in an office that isn't connected to my house thus is too far away from my wireless router to connect with an ethernet cable.  It's an old desktop and doesn't have wireless and i don't have a wireless USB card thing to use.  I want to download a couple of programs on it.

My plan, if this is at all possible, is to take my laptop with Ubuntu on out there, connected to the internet, and use an ethernet cable to connect my laptop to the desktop and use the laptop's wireless connection to the internet on the desktop?
Is that possible.

I found a couple of pages on Google, but they confused me and i was a little unsure what they meant and they were quite old.

---

### Post by Naitsirhc Hsem on 2010-10-04
It's possible. I think in lucid lynx and above you can connect to the wifi and plug your laptop into the desktop via ethernet and it will automatically connect. if not, I can do some more digging.

---

### Post by HermanAB on 2010-10-04
Yes, you can do that, but there are a few things to bear in mind:
[LIST]
[*]To connect the laptop to the desktop, you either need a cross-over ethernet cable, or you need a switch and two cables.
[*]On the Linux laptop, you got to enable IP forwarding.
[*]On the Linux laptop, you should either run a DHCP server and let it bind to the ethernet port, or you need to assign the ip addresses, netmasks and gateways manually on both machines.
[/LIST]

---

### Post by random turnip on 2010-10-04
> **HermanAB said:**
> Yes, you can do that, but there are a few things to bear in mind:
[LIST]
[*]To connect the laptop to the desktop, you either need a cross-over ethernet cable, or you need a switch and two cables.
[*]On the Linux laptop, you got to enable IP forwarding.
[*]On the Linux laptop, you should either run a DHCP server and let it bind to the ethernet port, or you need to assign the ip addresses, netmasks and gateways manually on both machines.
[/LIST]

I have a standard ethernet cable (the type you can just put in a computer one end and router the other end) where the plugs on each end are the same, is this good enough?

For the second 2 points, i've just looked at a few tuts on IP forwarding.  Looks like it might be easier to just temporarily bring the computer into the house while i download what i need, lol.

---

### Post by cap10Ibraim on 2010-10-04
> **HermanAB said:**
> Yes, you can do that, but there are a few things to bear in mind:
[LIST]
[*]On the Linux laptop, you should either run a DHCP server and let it bind to the ethernet port, or you need to assign the ip addresses, netmasks and gateways manually on both machines.
[/LIST]
but I already get my IP automatically from a DHCP server , should I dig in my modem/router , use them as static then choose the IP of the Desktop so that they'll be in the same network ?

---

### Post by HermanAB on 2010-10-04
If you set up a bridge between the WiFi and Ethernet ports, then you will have a single network, but instead of installing dhcpd you then have to install the bridge tools - Six of one and half a dozen of the other...

This is what you have to do:
Cut the head off the cable at one end.  Swap the orange and green pairs and crimp on a new RJ45.  Now tie a knot in the cable to make it clear that this is a special cable.

On Laptop:
echo 1 > /proc/sys/net/ipv4/ip_forward
ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up

Install vsftpd, ssh-server or NFS and share a folder.

On Desktop:
ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up
route add eth0 default gw 192.168.1.1

Use Nautilus or gftp to access the shared folder on the laptop.

---

### Post by Kevdunleavy on 2010-10-04
I do this at home all the time.

I use Karmic but I'd say its the same for Lucid. Not so sure about versions older than Karmic though.

Anyway here's what I do...

[LIST=1][*]Connect laptop to internet[*]Right click on the network icon in the system tray (top right)[*]Go to "Edit Connections"[*]Go to the wired tab and edit the entry (Mine is "Auto eth0")[*]Go to the IPv4 settings tab[*]Select "Shared to other computers" as the method[*]Click Apply and then click close
[/LIST]

Then insert the ethernet cable from your desktop computer. Connect to the wired network in the laptop by right clicking the network icon (in the system tray) and clicking the "Wired Network" option.

I'm pretty sure thats all I do. Hope it works for you :)

---

### Post by random turnip on 2010-10-20
> **Kevdunleavy said:**
> I do this at home all the time.

I use Karmic but I'd say its the same for Lucid. Not so sure about versions older than Karmic though.

Anyway here's what I do...

[LIST=1][*]Connect laptop to internet[*]Right click on the network icon in the system tray (top right)[*]Go to "Edit Connections"[*]Go to the wired tab and edit the entry (Mine is "Auto eth0")[*]Go to the IPv4 settings tab[*]Select "Shared to other computers" as the method[*]Click Apply and then click close
[/LIST]

Then insert the ethernet cable from your desktop computer. Connect to the wired network in the laptop by right clicking the network icon (in the system tray) and clicking the "Wired Network" option.

I'm pretty sure thats all I do. Hope it works for you :)

I will try this soon, thanks very much.

If it's going to be much trouble i think i'll just leave it, but something like this is fine.

---

