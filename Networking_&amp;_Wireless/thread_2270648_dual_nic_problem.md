---
title: "dual nic problem"
date: 2015-03-24
forum: Networking &amp; Wireless
---

### Post by lievenco on 2015-03-24
Hello

I have a question about a dual nic (eth0 & wlan0) problem.

I am creating a script to test my internet connection with a ping test and a download test.
the wifi and cable are connected on the same router.
So they are in the same ip range/subnet
But when my cable is plugged in i can't ping to the internet trough my wifi.
I can ping my default gw of the router trough wifi
i only can ping trough my cable connection.
when I unplug my cable, I can ping/download trough my wifi

I considered to enable/disable the specific connection ( ifconfig wlan0/eth0 up/down) and then run the script.
But is there an other way to do this simple, when both connections are up?

[U][B]example:
[/B][/U]eth0 ip = 192.168.0.2
wlan0 ip = 192.168.0.3
default gw = 192.168.0.1
subnet = 255.255.255.0

[U][B]does work
[/B][/U]ping -I eth0 8.8.8.8
wget --bind-address=192.168.0.2 [http://www.test.com/500mbexample](http://www.test.com/500mbexample)
[U][B]
doesn't work[/B][/U]
ping -I wlan0 8.8.8.8
wget --bind-address=192.168.0.3 [http://www.test.com/500mbexample](http://www.test.com/500mbexample)

_**route -n information**_
herentals@herentals-Latitude-E5540:~/Bureaublad$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan2

---

### Post by SeijiSensei on 2015-03-24
Having both interfaces on the same network subnet is a recipe for problems.  If you disable one interface or the other, do you have the same problems?

Also there's really no value to connecting both interfaces to the same subnet.  You won't see any performance improvements unless you use "[bonding]("https://help.ubuntu.com/community/UbuntuBonding")."

---

### Post by lievenco on 2015-03-24
if I disable/enable 1 of the 2 interfaces, there's no problem.

the script is for troubleshooting a internet connection of a ISP.
I have to check if the speed trough cable/wifi is OK and upload the result to a database.
if the wifi speed is not OK, it will also upload RSSI an PHY rate at that moment.

So i'm not trying to bond the 2 interfaces, just for troubleshooting a cable/wifi connection :p

---

### Post by SeijiSensei on 2015-03-24
Then you'll have to do them one at a time.

---

