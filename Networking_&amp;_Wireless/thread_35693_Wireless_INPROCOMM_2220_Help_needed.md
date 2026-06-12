---
title: "Wireless INPROCOMM 2220 Help needed"
date: 2005-05-19
forum: Networking &amp; Wireless
---

### Post by ssck on 2005-05-19
From the posts in the forum, i find that there are many ubuntu users who need help with wireless connectivity thru their laptops.i am one of them.after i finally managed to get ubuntu to recognize the wireless card, it is now lighted up.however, to get it connected to the access point is another matter.can some ubuntu experts help us newbies out ????

for my home use, the access point does not have wep.with dhcp on, i get no offers when i do a scan.when i fix the ip address, and gateway with the essid name, i get a destination host not found when i ping the gateway.

what seems to be a problem ???? something so simple in winxp is so complicated here.i really like this distro and i am sure many others do to.but if my wireless doesn't work, it really serves no purpose.i don't want to move back to winxp.

again, can some experts help us out ????

---

### Post by f.prisson on 2005-05-20
If I understand your post right, you still have to configure you wireless settings (exactly as with windows). If you use Gnome, go to System -> Settings (I'm not sure about the english name, I use it in german) -> network. Without WEP you only have to  configure your essid.

---

### Post by ssck on 2005-05-20
[QUOTE=f.prisson]If I understand your post right, you still have to configure you wireless settings (exactly as with windows). If you use Gnome, go to System -> Settings (I'm not sure about the english name, I use it in german) -> network. Without WEP you only have to  configure your essid.[/QUOTE]

Hi Prisson,

Thanks for looking at this problem.

These are my settings in the interfaces file :

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
address 192.168.2.10
netmask 255.255.255.0
gateway 192.168.2.1


iface wlan0 inet static
wireless_keymode open
wireless_mode managed
#wireless_nick REPLACE WITH YOUR HOST NAME
address 192.168.2.239
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 202.188.0.133
wireless-essid Hex3
wireless-key open

auto wlan0


auto eth0


Is it because the settings are wrong ?? maybe that is the reason why i keep on getting 'destination host unreachable' ??? anything i should change ?

i even tried with or without dhcp but it still doesn't work.

what else should i do ?

thanks.

---

### Post by f.prisson on 2005-05-21
Please post your /etc/resolv.conf```
sudo gedit /etc/resolv.conf
``` Are you able to ping your router with the IP? Please let me also see the output of ```
iwconfig wlan0
``` Your settings in /etc/network/interfaces look good.

---

### Post by ssck on 2005-05-21
hi prisson,

thanks for your help.i disabled the eth0 and enabled wlan0.rebooted the laptop and now it is working perfectly.

i am really not sure what is the reason.possibly due to the driver.

appreciate your help.

---

