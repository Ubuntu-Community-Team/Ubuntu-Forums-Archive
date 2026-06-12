---
title: "Using the VPN connection of the University of Amsterdam"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by cantillon on 2011-03-07
In case there are other ubuntu users at the University of Amsterdam trying to figure out how to use the VPN connection, here's a short how-to. I did it with Ubuntu 10.10, but should work with other versions and linux distributions:

[COLOR="Blue"]**1. Install network-manager-vpnc and network-manager-vpnc-gnome:**[/COLOR]

Open a terminal (Applications > Accessories > Terminal)

In the terminal type:

[INDENT]sudo apt-get install network-manager-vpnc network-manager-vpnc-gnome[/INDENT]

Enter your password when prompted and accept the installation.

You can also install this packages using Synaptic (System > Administration > Synaptic Package Manager)

[COLOR="Blue"]**2. Configure VPN connection:**[/COLOR]

Click on the network-manager icon in the system tray (top right corner of the screen).

In the drop-down menu, select VPN Connections > Configure VPN

Click on the VPN tab, and then click &#8220;Add&#8221; button to add a new VPN connection.

Fill in the following information:

[INDENT]Connection name: UvAvpn (or whatever name you want to give it)

Gateway: vpn.uva.nl

Group name: ipsec

User password: **your UvA password** (select &#8220;Saved&#8221; in the field next to the password)

Group password: ipsec (select &#8220;Saved&#8221; in the field next to the password)

Username: **the numbers of your UvAnetID** (only the numbers, without @uva.nl)

Encription method: Safe

Transversal NAT: Cisco UDP[/INDENT]

Substitute the text in **bold letters** with your own information

**[COLOR="Blue"]3. Restart network-manager[/COLOR]**

Open a terminal (Applications > Accessories > Terminal)

In the terminal type:

[INDENT]sudo service network-manager restart[/INDENT]

Enter your password when prompted

[COLOR="Blue"]**4. Connect to VPN**[/COLOR]

Click on the network-manager icon in the system tray (top right corner of the screen).

In the drop-down menu, select VPN Connections > UvAvpn (or whatever name you give to the VPN connection you just created).

You can find out more on how to use the UvA services with linux on this blog: [http://linuxatuva.wordpress.com]("http://linuxatuva.wordpress.com")

---

