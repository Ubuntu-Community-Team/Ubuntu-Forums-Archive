---
title: "Wifi in Kubuntu"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by gitargr8 on 2006-11-07
Hello, I'm a bit of a noob and need some help getting the WiFi to work on an old Dell Inspiron 8200 with a Linksys WPC54G PCMCIA card. 

I'm trying to connect to an open network, I've set the ESSID, but whenever I run lshw I get *-network DISABLED. I'm pretty sure that the driver is working for it, it is listed when I run lsmod.

I don't have the driver version, since I have to run windows to get on the internet, but can provide it if necessary.

I read through the wiki article for wireless and it noted that there may be a key sequence to disable the wireless, but there isn't one on this laptop.

Any help would be greatly appriciated.

~Ryan

---

### Post by gitargr8 on 2006-11-08
'a-lo?

---

### Post by gitargr8 on 2006-11-10
Well, I got it fixed all by my lonesome. 

What I did was remove the driver for my wireless card that came with Kubuntu (bcm43xx I believe...)

```
lshw
```

Look for "*-network" and find the driver that is listed for the wifi card. In my case it was bcm43xx. I then stopped this driver:

```
sudo modprobe -r bcm43xx
```

Then I blacklisted the old driver by running

```

kdesu kate /etc/modprobe.d/blacklist &

```

and added

```

blacklist bcm43xx

```

to the end of the file.

Then I installed ndiswrapper and got the newest driver for my card. Installed the new driver, and verified it was installed:

```

sudo ndiswrapper -i driverfile.inf
ndiswrapper -l

```

Then I loaded the ndiswrapper module:

```
sudo modprobe ndiswrapper
```

And I wanted ndiswrapper to load on boot so I opened /etc/modules:

```
kdesu kate /etc/modules &
```

and added 

```
ndiswrapper
``` 

to the end of the file.

Well I hope that helps out anyone else who has the same problem. Thanks to everyone for not responding and forcing my lazy a$$ to do it myself. :-? 

~Ryan

---

### Post by Metaljaz on 2006-11-18
this thread will probably come in handy for me because i am gettin ready to install ubuntu on my dell i8200. i have the wpc11 v4 pcmcia card and may encounter the same problem.
will find out soon.

---

