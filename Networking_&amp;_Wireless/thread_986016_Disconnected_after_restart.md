---
title: "Disconnected after restart"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by Nyod on 2008-11-18
first of all hi :)

I am a two-day user of Ubuntu and been pretty satisfied so far, but I have this problem. If I restart my computer (or if I come back from standby mode)
I'm getting disconnected from the wired.
Things I've tried : Removing cable and attaching it again
The only solution so far is to shut down completely the computer, wait for a few moments then turn it on again.

I'm using dsl connection with Ethernet cable. 

could you please help? thanks!

-nyod

---

### Post by Nyod on 2008-11-21
Anyone??????//

Please, I have to restart or shut down 20 times to get this to work
:(

---

### Post by Flexo87 on 2008-11-21
Hi!

Is your internet connection using DHCP? there's a file where the connection settings are written in order to be loaded at boot time, it's "/etc/networking/interfaces" check it! You can edit it manually (you may need root privileges to modify the content, type: sudo gedit /etc/networking/interfaces):

If you're using DHCP:

   auto lo
   iface lo inet loopback

   auto eth0
   iface eth0 inet dhcp

If you're using static IP assignment:

   auto lo
   iface lo inet loopback

   auto eth0
   iface eth0 inet static
   address 192.168.x.x
   netmask 255.255.255.0
   gateway 192.168.x.x

Change "eth0" with your device name, and in the last case put the correct IP for your machine and the gateway (router IP).
after editing the file restart the network with the following command:
 
     sudo /etc/init.d/networking restart

that's should be fine.

---

### Post by Nyod on 2008-11-21
yes I'm using DHCP...

ok after I did what you told me, it seems to work fine. I will let you know if there's a problem, thanks again!

-nyod

---

### Post by GAJAN on 2009-03-09
I also experience connection problems: usually on startup no connection is found, and I have to manually connect to the wired network, using the NetworkManager Applet (0.7.0). The checkmark next to the default connection (Auto eth0) is not activated at this time, and after clicking it takes quite some time before the connection is established.

But after editing my  "/etc/network/interfaces" by adding the lines suggested above 

[INDENT]auto eth0
iface eth0 inet dhcp
[/INDENT]

after restart no connection was found at all, and the network manager applet did not even show up....
Deleting the added lines re-enabled the network manager, but connecting to the wired network still requires a manual step.

Any ideas?

GAJAN

---

