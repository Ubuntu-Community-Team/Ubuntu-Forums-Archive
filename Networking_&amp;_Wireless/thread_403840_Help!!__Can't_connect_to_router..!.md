---
title: "Help!!  Can't connect to router..!?"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by ponx on 2007-04-07
Hi,

I have a laptop and a desktop, on both of which I have just installed 7.04.

Both machines load the rt73usb driver and both can scan and detect my router.

However, neither will connect to it, even with all the security turned off..!?

I really have no idea why, so any ideas would be greatly appreciated...

ponx

---

### Post by pixeldotz on 2007-04-07
a few things that can help us that i'm sure you can provide.

what model of router are you using? reason i ask is because certain routers assign their ip's differently. in linksys' case 192.168.100.1  or 1.1 is usually what it's set to.

the bottom of your router should say this.

-what is the ip and gateway set to on your ethernet adapter?
the gateway for your ethernet adapter should be set to whatever the ip is of your router. same goes for the dns setting. gateway and dns should be set to the routers ip.

if all this matches, then try pinging your router.
 - start up a terminal and enter.
```

ping 192.168.0.1

```

where '192.168.0.1' is whatever your routers ip is. if the pc sees the router correctly you'll get a 'reply' from the device.

post that info and anything else you think is relevant. i'll check the thread later tonight.

---

### Post by ponx on 2007-04-07
It's a Linksys router but running DD-WRT v23.  Anyway, I don't think the router is the problem since I have had the same dongle connecting fine with Gentoo (albeit with a self-built rt73 driver).

I think the rt73usb driver itself may be the issue...  Not sure what else I can say...

ponx

---

### Post by ponx on 2007-04-08
At last..!!!  I have solved the problem - I may not have much hair left, but at least I can connect now...

Ok, my USB wifi stick is something called an ADD-ON ADD-GWU180v3 (some cheapo make that I discovered uses one of the ever-prevalent RaLink chipsets).

Anyhow, when Ubuntu runs after a fresh install it has loaded the rt73usb driver.  As it happens, this driver did everything except talk to the router.  Maybe it works with other cards, I don't know, but it didn't work with mine.

Therefore, after much research I carried out ther following:

1)  Removed the rt73usb driver and built the latest rt73 driver from CVS.  The how-to I follwed is here -> [COLOR="Blue"][http://wiki.ubuntu-it.org/RalinkRT73]("http://wiki.ubuntu-it.org/RalinkRT73")[/COLOR].    Ok, it's in Italian, but you can still follow the commands.  (The only additional thing that isn't in there is that before compiling the driver you have to do a 'lsusb' to get the hardware number for the device and add it to the relevant area in rtmp_def.h

2)  With the new driver it is now time to remove Network Manager from the installation.  This is because, apparently, Ubuntu's Network Manager is not compatible with RaLink drivers..!?!?  The thread I used was for rt61, but still worked for mine -> [COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=392415&highlight=wireless+rt61]("http://ubuntuforums.org/showthread.php?t=392415&highlight=wireless+rt61")[/COLOR] 

And that was it really, after configuring /etc/network/interfaces and rebooting, my wireless connection now runs flawlessly...!!

Only one other thing...  No with NetworkManager disabled I no longer have the little network icon showing in the top panel.  Does anyone know of any other little apps that can go there instead to at least show I am connected..??

Cheers.

ponx

---

### Post by crosscountry on 2007-04-08
> **ponx said:**
> Only one other thing...  No with NetworkManager disabled I no longer have the little network icon showing in the top panel.  Does anyone know of any other little apps that can go there instead to at least show I am connected..??

Cheers.

ponx
Network-Manager comes with its own 'nm-applet'. I think there is still another network icon you can add. Right-click on the panel and choose 'Add to the panel ....' or something like this. In the system/hardware section you will find a network status applet. (if not, maybe you first have to install gnome-netstatus-applet or gnome-nettool)

---

### Post by ponx on 2007-04-08
Found it.  Thanks, exactly what I was looking for...

ponx

---

### Post by pixeldotz on 2007-04-08
network-manager is the one i use for my laptop, it's awesome.

also, what version is your router?

reason i ask is because i have a v5 linksys with dd-wrt v23 and i think it sucks so bad.

i also have a buffalo whr with tomato firmware and it's the best alt-firmware i've ever seen. my friend uses it on his v2 linksys router.

i know it's off topic but i thought i'd toss that up there :)

---

