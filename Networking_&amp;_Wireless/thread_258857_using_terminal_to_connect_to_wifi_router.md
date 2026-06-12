---
title: "using terminal to connect to wifi router"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by SVwanders on 2006-09-16
I am visiting a friend and installed suse 10.1 in and old machine of hers. I know this is not suse forum! But I run Ubuntu at home and this forum runs circles around all the others I have tried to use. 
Anyway, she got a rt2500 wireless card that I finally got to work. I can run iwlist ra0 scan and it picks up the network. I have tried using KNetworkManager without ANY luck. It would lock up at 28%. What are the commands I need  to know to connect to the wireless router through the Konsole terminal? What information do I need to supply so that I can get her machine connected to the web.

Thank you, Tim Maddux

---

### Post by Velox Letum on 2006-09-16
```
man iwconfig
```

Generally I do the following commands

```
iwconfig wlan0 mode managed channel 6 key open <yourwepkeyhereifany> essid MyNet
iwconfig wlan0 ap DE:CA:FF:C0:FF:EE
dhclient wlan0
```

*examples

---

### Post by SVwanders on 2006-09-16
That GOT IT! This forum ROCKS. 

I did have to change dhclient ra0 instead of wlan0 
I guess I need to look up the difference. I wasn't able to get the iwconfig wlan0 ap DE:CA:FF:CO:FF:EE command and arguments to work. I suppose they would also have to be changed to ra0 instead of wla0. I will do some research on this.

Thank you again for your help! I have been working on this for days and loving it.

Tim

---

### Post by Velox Letum on 2006-09-16
Well, the interface was my own, the the DE:CA:FF:C0:FF:EE was just an example AP MAC address. You generally don't need to use that, but I do because I'm sometimes in areas with Ad-hoc networks and I want to connect to a certain AP.

---

### Post by towsonu2003 on 2006-09-16
> **SVwanders said:**
> 
I did have to change dhclient ra0 instead of wlan0 
I guess I need to look up the difference. I wasn't able to get the iwconfig wlan0 ap DE:CA:FF:CO:FF:EE command and arguments to work. I suppose they would also have to be changed to ra0 instead of wla0. I will do some research on this.

ra0 instead of wlan0: The name of your wireless card is different. I believe it changes with what driver is used and which chipset is the network card ( = interface). You can look up the names of your network cards with ```
ifconfig -a
``` and you can check which card / interface is wireless by ```
iwconfig
```

MAC address: each network device has a MAC address unique to it (although it can be spoofed). you can check the MAC address of your ap (access point) by doing: 
```
$ iwlist ra0 scan
eth1      Scan completed :
          Cell 01 - Address: **xx:xx:xx:xx:xx:xx**
                    ESSID:"name"
                    [censored]
```The part in bold is the MAC address of the access point called "name". Sometimes there are more than one access points with the same name in your area (like linksys, which is the default name of linksys routers). when that's the case and you know the MAC address of your own access point, you specify it with ```
#iwconfig ra0 ap xx:xx:xx:....
```

---

