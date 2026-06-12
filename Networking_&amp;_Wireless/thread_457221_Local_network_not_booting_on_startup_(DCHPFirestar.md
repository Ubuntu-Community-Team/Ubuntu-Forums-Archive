---
title: "Local network not booting on startup (DCHP/Firestarter)"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by jeremy12 on 2007-05-28
Ok, so i have DCHP and Firestart setup and everything works perfectly, HOWEVER when i reboot the system i can ping google.com/ubuntu.com from the server but the local network cannot ping the server/get past it untill i login to my command line go into gnome and open firestarters GUI then it all works fine, when i attempt to run the firstarter start command "sudo firestarter -start -start-hidden" i receive the error
"(firestarter:7015): Gtk-WARNING **: cannot open display:" i know this is error is 99% most likely a firestarter bug, i encourage you to try and see if you get the error as well and if so go to [http://bugzilla.gnome.org/show_bug.cgi?id=441506](http://bugzilla.gnome.org/show_bug.cgi?id=441506) and comment that it exsists for you as well, however any ideas on why the localnetwork is not booting untill i open the firestarter GUI, would this be a firestarter issue or DHCP not starting till firestarter GUI does


eth0 - Internet connection
eth1 - goes to a switch and on tot he rest of my network

My dchpd.conf
```
ddns-update-style interim;
ignore client-updates;

subnet 192.168.0.0 netmask 255.255.255.0 {
	option routers 192.168.0.1;
	option subnet-mask 255.255.255.0;
	option domain-name-servers 68.87.77.130, 68.87.72.130;
	option ip-forwarding off;
	range dynamic-bootp 192.168.0.100 192.168.0.200;
	default-lease-time 21600;
	max-lease-time 43200;
}
```

My /etc/network/interfaces
```
auto lo
iface lo inet lookpack

iface eth0 inet dhcp

auto eth0

iface eth1 inet static
address 192.168.0.1
network 182.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255

auto eth1
```

---

### Post by wishmechaos on 2007-06-05
Have you enabled "Enable DHCP for the local network" in firestarter config? If so, beware that firestarter starts the DHCP server by itself. I had to disable the dhcpd service in init.d for it to work.

I also had to do a weird workaround since firestarter executes dhcpd instead of dhcpd3, so I made a symlink.

hope it helps.

---

