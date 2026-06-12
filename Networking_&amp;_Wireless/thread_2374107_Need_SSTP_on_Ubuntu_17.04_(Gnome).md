---
title: "Need SSTP on Ubuntu 17.04 (Gnome)"
date: 2017-10-12
forum: Networking &amp; Wireless
---

### Post by thehallofshields on 2017-10-12
Hey guys,

I'm using Ubuntu 17.04 with Gnome and absolutely have to get SSTP setup on my Laptop for work, or it's back to Windows for me.
I've followed a couple of guides that had me install PPA's for sstp-client and the sstp NetworkManager plugin, but they failed to install.

Does anyone know of a good solution for this?

---

### Post by praseodym on 2017-10-13
Found this

[http://sstp-client.sourceforge.net/](http://sstp-client.sourceforge.net/)

Follow the steps there for compiling. Additionally, 17.04 has a network manager bug:

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by thehallofshields on 2017-10-16
Well. I compiled and went through the steps on sourceforge.

I only get this output:
[B]
user@localhost:~$ sudo pon sstp-test 
Plugin sstp-pppd-plugin.so loaded.[/B]

Once I do that, it seems to be able to ping servers via hostname, but not IP.

---

### Post by praseodym on 2017-10-16
Did you configure via network-manager? Adding the routes, etc.?

---

### Post by thehallofshields on 2017-10-20
I installed network-manager-sstp and sstp-client, and also ran the bug-fix above, but I still don't see SSTP connection as an option in my Network Manager GUI.

---

### Post by thehallofshields on 2017-10-20
> **praseodym said:**
> Did you configure via network-manager? Adding the routes, etc.?

No this was using the `pon` command as described on the sstp-client page.

I don't see the SSTP option showing up in network-manager.

---

### Post by thehallofshields on 2017-11-01
It looks like my issue comes down to not knowing how to integrate the network-manager-sstp package. 
I've installed the network-manager-sstp package as described here: [https://github.com/enaess/network-manager-sstp,]("https://github.com/enaess/network-manager-sstp") but I don't see any SSTP option in the Gnome Network Manager or nmtui. 

f someone could help me with this I'd be super appreciative.

[IMG]http://i66.tinypic.com/2m4ros0.jpg[/IMG]

---

### Post by praseodym on 2017-11-01
Lets try

```
sudo apt-get update
sudo apt-get install --reinstall network-manager-openvpn network-manager-openvpn-gnome network-manager-pptp network-manager-pptp-gnome network-manager-vpnc network-manager-vpnc-gnome network-manager-openconnect network-manager-openconnect-gnome network-manager-sstp sstp-client
```
Reboot

---

### Post by thehallofshields on 2017-11-02
Well that got me a couple more options. But I still don't see SSTP.

[IMG]http://i68.tinypic.com/2149pbn.jpg[/IMG]

---

### Post by thehallofshields on 2017-11-02
Just to be sure, after reboot, I re-ran the command and it completed without errors.

> sudo apt-get install --reinstall \
network-manager-openvpn network-manager-openvpn-gnome \
network-manager-pptp network-manager-pptp-gnome \ 
network-manager-vpnc network-manager-vpnc-gnome \
network-manager-openconnect network-manager-openconnect-gnome \
network-manager-sstp sstp-client

---

### Post by thehallofshields on 2017-11-02
It looks like all of the VPN options are stored in /etc/NetworkManager/VPN

> user@computer:/etc/NetworkManager/VPN$ ls -1
nm-openconnect-service.name
nm-openvpn-service.name
nm-pptp-service.name
**nm-sstp-service.name**
nm-vpnc-service.name


SSTP is in there, but doesn't appear as an option in the Network Manager GUI (Gnome and Unity)

---

### Post by thehallofshields on 2017-11-02
Alright guys, I think I'm close!

Just missing: **/usr/lib/NetworkManager/libnm-vpn-plugin-sstp.so**

[IMG]http://i65.tinypic.com/k1s3me.jpg[/IMG]

---

### Post by praseodym on 2017-11-05
Found something:

```
sudo apt-get install network-manager-l2tp-gnome
```

---

### Post by thehallofshields on 2017-11-06
> **praseodym said:**
> Found something:

```
sudo apt-get install network-manager-l2tp-gnome
```

Package not found. Any tips?

> E: Unable to locate package network-manager-l2tp-gnome

---

### Post by praseodym on 2017-11-06
[https://packages.ubuntu.com/artful/network-manager-l2tp-gnome](https://packages.ubuntu.com/artful/network-manager-l2tp-gnome)

---

### Post by thehallofshields on 2017-11-27
I got the network-manager-l2tp-gnome 			 		package installed. Added an option for L2TP but still no option for SSTP.

Still stuck at this error: **/usr/lib/NetworkManager/libnm-vpn-plugin-sstp.so not found!**

---

### Post by thehallofshields on 2017-12-08
I think I'm very close. Can anyone recommend other places to get support on this?

---

