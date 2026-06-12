---
title: "Setting up wireless in command line"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by Wofl on 2006-12-26
hey guys

now i got a great commandline system going. now i just need to get my wireless card installed.

i used this tutorian last time: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

but now i dont have a window manager installed, so no way to do the configuration in the network manager like last time.

how do i do this in the commands line?

---

### Post by c.dric on 2006-12-26
i'm guessing you mean step 7 ? 

```
7. Use the internet (you will have to open the System menu at the top of the screen, go to Administration, and then click Networking. Configure the interface eth1 or wlan0, and connect to your wifi network)
```

if so you should do the following : 

```
sudo nano /etc/network/interfaces
```

if your network uses dhcp add the following lines, replace eth1 by your interface name if needed : 

```
auto eth1
iface eth1 inet dhcp
wireless-essid <the name of your access point>
wireless-key <your wep key in hexadecimal>  # ignore this line if you don't use wep

```

if you use static ip, replace the ips with your settings : 

```
auto eth1
iface eth1 inet static
address 192.168.168.5
netmask 255.255.255.0
network 192.168.168.0
broadcast 192.168.168.255
gateway 192.168.168.230
dns-nameservers 192.168.168.230
wireless-essid <the name of your access point>
wireless-key <your wep key in hexadecimal>  # ignore this line if you don't use wep
```

then the following to launch the connection (you may have to restart first) :

```
sudo /etc/init.d/networking start
```

---

### Post by dbott67 on 2006-12-26
Some networking commands from the command line are:

Disable / Enable:
```
sudo ifdown eth0 && sudo ifup eth0
```
(replace eth0 with appropriate interface)

Restart Network:
```
sudo /etc/init.d/networking restart
```

List all recognized interfaces:
```
cat /etc/network/interfaces
```

List current status of all interfaces:
```
ifconfig -a
```

Scan for wireless networks:
```
iwlist scanning
```

Display Network Hardware:
```
sudo lshw -C network
```

Display current routing table:
```
route -n
```

-Dave

---

