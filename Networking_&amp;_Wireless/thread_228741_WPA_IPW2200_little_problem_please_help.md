---
title: "WPA IPW2200 little problem please help"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by freaks on 2006-08-03
hello,
I installed wpa_supplicant in my toshiba computer. All is ok but i can't access network and internet
this is my interface file . I am automaticaly connected at startup all is ok but no ping

anybody know the solution ?

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.80
netmask 255.255.255.0
gateway 192.168.1.254

auto eth1
iface eth1 inet static
address 192.168.1.81
netmask 255.255.255.0
gateway 192.168.1.254
pre-up /etc/init.d/wpasupplicant start
wireless-mode Managed
wireless-essid myssid
wireless-key 675105c2c2ba59f5ea4eb49d34fa83a3a7093ffa95c8d83525506c066fd69c73
pre-down /etc/init.d/wpasupplicant stop

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
```

---

### Post by opbzil on 2006-08-03
How are you?

I managed to get Dapper drake on my laptop to work perfectly. It also has a intel 2200BG card and I am using it along with WPA security.

There where several things that needed to be done. After doing a basic install. I ran easyubuntu (not reaslly necessary but nice to do) and then did a full update. This took a while but it updates wpasupplicant among many other things! Then you need to update the firmware of the cards. You can get it from [http://ipw2200.sourceforge.net/firmware.php]("http://ipw2200.sourceforge.net/firmware.php")

You will need to extact it and copy the files over to **/lib/firmware/** you will have to overwrite the ones there. Finally install NetworkManager (it works with our cards!)this great little tool lets you easily set your security.

hoping this helps you.

---

### Post by freaks on 2006-08-03
ok i downloaded firmware v3.0 an updated the /lib/firmware/2.6.15-26-686 folder and overwrited the existing file after a reboot nothing changed ... must i update the driver too ?

---

