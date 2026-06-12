---
title: "network stopped working"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by monkman on 2008-06-22
everything worked fine until i tried, without luck, to get wireless network working with wpa (worked without encryption). 
i thought i were clever saving a network-profile, before beginning to mess around. but it didn't help.

lenovo 3000 n200 bgg notebook
broadcom netlink bcm5906m
ubuntu 8.04 32bit

when i try a local ping(to gateway), it says: network is unreachable
#sudo /etc/init.d/networking restart, doesn't help either

the settings seem to be okay, eth0 should have the korrekt ip number, gateway is fine, dns is fine.

everything works fine in vista(dualboot)

eth0: 192.168.37.70
gw: 192.168.37.65
dns: gw
subnetmask: 255.255.255.224
broadcast 192.168.37.95

any suggestions? thx!

---

### Post by chili555 on 2008-06-22
> broadcom netlink bcm5906mI believe this is a wired ethernet card. Your wireless is, I think, Intel 3945ABG. The interface eth0 would be correct for wired ethernet, however your wireless is likely wlan0. I would try connecting with DHCP first, before you try static, because you know you connected if you got an IP address.

It's not clear if you are asking for help with wired or wireless.

---

### Post by monkman on 2008-06-22
sorry, it's about the wired connection, wlan is turned off with the switch on the notebook...

---

### Post by chili555 on 2008-06-22
The Broadcom uses the module *tg3* which is loaded. I suggest you change your settings back to DHCP and see if it connects. If not, let's troubleshoot with the command:```
sudo dhclient eth0
```If you require a static address, let's fix that once we have reliably connected.

PS- I hate your netmask; I think it should be 255.255.255.0.

---

### Post by monkman on 2008-06-23
my netmask is okay ;)

i try that later after work, thanx! but i have my doubts whether my router (linksys wrt54g v5.0) has the possibility to make dhcp in the ip range i use. maybe i switch back to 192.168.0.0 or something like that. but that wouldn't look "nerdy" though ;)

---

### Post by ujwols on 2008-06-23
Yes, You should be able to define the dhcp ip range for your router. As shown in the attached screen shot you can define the starting ip address under DHCP server configuration and you can also define the no of connection that is available for that router.

---

### Post by monkman on 2008-06-23
Starting IP Adress: 192.168.0.X. the 0 seems to be static, in my case i have an 37 at this place. but this is not the problem here ;)

my network doesn't work, as i said before i'll try this later after work, thx!

---

### Post by monkman on 2008-06-26
it works now, switched to dhcp and back, can't explain for myself, but it's okay now...

---

