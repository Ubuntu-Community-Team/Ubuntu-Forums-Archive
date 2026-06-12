---
title: "cannot get online!"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by geomcewan on 2008-12-16
My first computer is running win 2K and has a Linksys WRT54g router which works perfectly. My second computer is running Ubuntu and has an Asus wireless card installed, although I dont know if Ubuntu has detected this. How do I set this up properly - I have went into network settings and on the wireless tab put in the relevant mac address and ssid, although I dont know what to put in the bssid box. Any help gratefully appreciated.

---

### Post by shifty_powers on 2008-12-16
what version of ubuntu are you using?

and what happens when you put

```
sudo iwlist scan
```

into a terminal?

---

### Post by geomcewan on 2008-12-16
I get the messages
lo
eth0
pan0
Interface doesn't support scanning

---

### Post by wolfen69 on 2008-12-16
do
```
lspci
``` and post output here

---

### Post by geomcewan on 2008-12-16
Afraid I cant copy the output (no floppy) but there is a large list of things like AMD K8, nvidia and the like but no mention of Asus or anything wireless. If its a specific output I'm only too happy to reply.

---

### Post by geomcewan on 2008-12-16
I can ping the second computer Ok at 127.0.0.1 with 4 packets sent and recieved. Dont know if this clarifies anything..........

---

### Post by Michael.Godawski on 2008-12-16
hey geomcewan, 
can you check via the terminal commands:

```
sudo lshw -C network
iwconfig
```if the drivers for the wlan are active; here is my output as an example, just to know what to look at:

```
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:04:0e:c4:f2:63
       capabilities: ethernet physical wireless
       configuration:** broadcast=yes driver=ndiswrapper+fwlan driverversion=1.53+AVM GmbH,12/28/2006,2.0.6.1 ip=192.168.178.23 link=yes multicast=yes wireless=IEEE **802.11g
```

---

