---
title: "trouble with network interfaces (eth0 &amp; wlan0, two default routes)"
date: 2005-05-16
forum: Networking &amp; Wireless
---

### Post by pumuckel on 2005-05-16
hi.

/etc/network/interfaces:
```
auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth0

iface eth0 inet static
        address 172.16.16.10
        netmask 255.255.255.248
        network 172.16.16.8
        broadcast 172.16.16.15
        gateway 172.16.16.9
        dns-nameservers 172.16.16.9

auto wlan0
iface wlan0 inet static
        address 172.16.16.11
        netmask 255.255.255.248
        network 172.16.16.8
        broadcast 172.16.16.15
        gateway 172.16.16.9
        pre-up ifconfig wlan0 up
        up wpa_supplicant -wB -iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper
        post-down ifconfig wlan0 down
        post-down killall -q wpa_supplicant
```
-> two default routes after system boot
-> wireless lan works great after 'ifconfig eth0 down' 

what i need: a configuration that simply works!

- after system boot or wlan-button-event (on):
if my own wlan is available, i'd like to use it as default (with wpa, see above). the possibilty to join other wlans (e.g. with wep & dhcp) must be given by simply adding a few lines of configuration (see link below). eth0 should be active but not become default route.

- wlan-button-event (off):
wlan should be disabled and eth0 become default. unload ndiswrapper module to switch the status light off?

it would be great if you could provide a partial solution or any further help. i'd like to extend the ssidselect script from [http://www.ubuntulinux.org/wiki/WPAHowto](http://www.ubuntulinux.org/wiki/WPAHowto). 

a few additional questions:
- is there a way to detect very quickly if there's a dhcp-server present or not? (for eth0: yes -> use it, no -> use static ip like above)
- where should these scripts be placed? in interfaces? init.d? could this be integrated into hotplug? coldplug? (this is my first ubuntu install, but i am not new to linux)
- how to bind actions to the wlan-button of my notebook:
/var/log/messages:
```
May 16 22:36:08 localhost kernel: atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
May 16 22:36:08 localhost kernel: atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
```

a gui like wifi-radar or a working applet would be cool. but everything lacks wpa support.

thanks in advance.

---

