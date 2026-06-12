---
title: "Wireless Network Stopped Working"
date: 2013-09-16
forum: Networking &amp; Wireless
---

### Post by ooboontwo on 2013-09-16
Hello everyone,

I am playing around with Ubuntu Server (no desktop environment) 12.04.3 LTS.

I set everything up and HAD a working wirless network connection.

I then ran

```
sudo shutdown now -r
```

And when the system came back up it hung on something like "configuring network interface / connection." I have never been able to connect again.

I am somewhat new to terminal-only stuff, but I tried messing around with "ifconfig" "iwconfig" etc.

I tried:

```
sudo iwconfig wlan0 essid "MYIDHERE" key s:MYPASSHERE
```

The terminal took it and the changes were reflected in iwconfig but I still have no internet connection.

How can I go about troubleshooting this thing?

I have "links" installed for web browsing and it is not connecting, nor can I "ping" anything.

I am wanting to learn how to work in the terminal and do not have Gnome or KDE installed, so please let me know how to proceed.

I tried googling an answer but I'm not sure exactly what to follow. I have seen mention of "dhclient." What is it and how does it work? Also, I tried:

```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

Just trying to reset the network adapter, similar to "ipconfig /release /renew" in Windows command line.

Thanks in advance for the help!

Blessings,
Cody

---

### Post by carl4926 on 2013-09-16
A server running on wireless? Is very odd IMO.
I usually install a minimal UI, even on a server, it's just easier.

---

### Post by Hadaka on 2013-09-16
Hi ..after you did...
```
sudo shutdown now
```
to restart do.
```
**sudo /etc/init.d/networking restart**

```

now..depending on what changes you have made..you can configure your network with..
```
sudo gedit /etc/netowrk/interfaces
```
make any corrections...additions ..save ...close then 
do a restart..
```
**sudo /etc/init.d/networking restart**

```
hope that helps.

---

### Post by ooboontwo on 2013-09-16
```
**sudo /etc/init.d/networking restart
```**

Thank you! This fixed it!

Shouldn't this automatically run every time I start the server though? Why did networking stop, and how can I make sure it automatically initializes each boot?

Also, I realize it is strange to have a server running on wireless. I am not using this server as a server. I'm just playing around with Ubuntu server because I want to learn it better.

Thanks again!

---

### Post by Hadaka on 2013-09-16
Hi, more than likely,since you are NOT using the desktop server,
the network starts on boot. you can see if it's running by entering..
```
sudo service networking status
```
you may also want to make a change in..
```
cat /etc/NetworkManager/NetworkManager.conf
```
```
sudo gedit /etc/NetworkManager/NetworkManager.conf
```
*Change managed=false ~ to ~ **managed=true**
My server is also wireless,never a problem,but i use the desktop
server and configure my static ip  with the IPv4 settings. 
Have fun playing!
Please mark this thread solved.
thanks.

---

### Post by ooboontwo on 2013-09-16
> **Hadaka said:**
> Hi, more than likely,since you are NOT using the desktop server,
the network starts on boot. you can see if it's running by entering..
```
sudo service networking status
```
you may also want to make a change in..
```
cat /etc/NetworkManager/NetworkManager.conf
```
```
sudo gedit /etc/NetworkManager/NetworkManager.conf
```
*Change managed=false ~ to ~ **managed=true**
My server is also wireless,never a problem,but i use the desktop
server and configure my static ip  with the IPv4 settings. 
Have fun playing!
Please mark this thread solved.
thanks.

Perfect. Thank you for the info!

---

