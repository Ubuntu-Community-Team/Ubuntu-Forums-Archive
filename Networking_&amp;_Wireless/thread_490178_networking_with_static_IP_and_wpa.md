---
title: "networking with static IP and wpa"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by finite9 on 2007-07-02
I use network-manager for two laptops which works great on both, but now I want to use one laptop as a server, and network manager doesnt work too well then, becuase you need to log in to enter the pam password to start the connection.

So I have fallen back to good ol networking with /etc/network/interfaces.

I have a wireless bcm43xx card (working fine with network-manager and acer_acpi) connecting to a router using wpa.

I set up interfaces like this:

```
auto eth1
iface eth1 inet dhcp
pre-up /etc/network/wireless-up
pre-up wpa_supplicant -Bw -ieth1 -c/etc/wpa_supplicant.conf -Dwext -w
post-down killall -q wpa_supplicant
post-down /etc/network/wireless-down
```

and wpa_supplicant.conf like this:

```
wpa_passphrase MySID MyPassword | sudo tee -a /etc/wpa_supplicant.conf
```

and /etc/default/wpasupplicant like this (but not sure if this is needed):

```
ENABLED=1
OPTIONS="-ieth1 -c/etc/wpa_supplicant.conf -Dwext -w"

```

My pre-up and post-down scripts look like this:

```
modprobe bcm43xx
modprobe acer_acpi
sudo chmod 777 /proc/acpi/acer/wireless
sudo echo &#8220;enabled: 1&#8221; > /proc/acpi/acer/wireless
sudo iwconfig eth1 ap any
sudo iwconfig eth1 rate 36M

```

```
echo &#8220;enabled: 0&#8221; > /proc/acpi/acer/wireless
modprobe -r acer_acpi
modprobe -r bcm43xx
```

This works great:  I log into the server and I can connect to the internet and browse just fine, and doing "sudo /etc/init.d/networking restart" works like a charm, so I suspect it will work well without logging in.

However...I cannot see the other laptop on the network, and the other laptop cannot see this server.  If I use networkmanager for the servers network connection, then I can see each laptop perfectly OK, and ssh and VNC into the server.

What am i doing wrong?

I really want to use a static IP for the wireless eth1 adapter, so I changed /etc/network/interfaces so it looks like this:

```
auto eth1
iface eth1 inet static
address=192.168.1.111
netmask=255.255.255.0
pre-up /etc/network/wireless-up
pre-up wpa_supplicant -Bw -ieth1 -c/etc/wpa_supplicant.conf -Dwext -w
post-down killall -q wpa_supplicant
post-down /etc/network/wireless-down
```

but this will not connect to my router at all....is it because wpa_supplicant handles the connection to the router and not interfaces file??  When I use this config, iwconfig does report that the specified IP address is being used, and iwlist/iwconfig dont show any errors as far as I can see.

---

### Post by finite9 on 2007-07-17
bump!!

seriously, does noone know??  Maybe I pratlled on too much, so here it is in short:

I now use static IP for my server, and connection works, but I cannot see the server from a wireless laptop.  I can see the server from laptop if I use Gnome and NetworkManager on the server to manage the connection, but not if I use /etc/network/interfaces to manage the connection

I cannot ping the static IP of the server even though it's on the same subnet: 192.168.1.x

-------------------

Just had a thought...I have never tried to access a ethernet connected PC from a wireles connected PC via the router.  Could it be that the router does not allow this???  I *had* a Linksys WRT54GX v2 router (i fried it 3 days ago and new one is on the way--note to self: never connect an AC power supply to a DC unit).  If this is the case, and it was configurable I will need to look at the settings of the new router (Linksys WAG534N I think).

---

