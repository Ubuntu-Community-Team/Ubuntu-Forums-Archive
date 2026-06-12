---
title: "Wired works, but no wireless"
date: 2005-10-18
forum: Networking &amp; Wireless
---

### Post by hidamari no tami on 2005-10-18
I'm having an odd problem with my wireless connection on my laptop running Hoary. Basically, until about two weeks ago it worked fine. Unfortunately I've tried two different wireless cards (WG511 and WPC55AG) and neither will scan, let alone make a connection to my home network. Sometimes it will show a connection, but when I log into my router (or run ifconfig), I notice that I don't have an IP address leased.

When I borrowed a wired card though, it connected right away without any problems (just booted up and was ready to go). I've had a similar problem before though, and when a friend and I made an attempt to fix it (to no avail unfortunately), I ended up reinstalling Ubuntu after a reformat. 

Both of the times however, this problem has occured under Hoary. The first time, I ended up being unable to connect to wireless within two days of upgrading from Warty to Hoary, but this time it's after a few months so I'm not too sure if that's the problem. 

Thanks in advance for any help!

---

### Post by hidamari no tami on 2005-10-20
Also, the dmesg output has it that Yenta is loaded, but when uploading firmware I get the following:

eth0: resetting device...
eth0: uploading firmware...
eth0: firmware version: 1.0.4.3
eth0: firmware upload complete
eth0: interface reset complete
eth0: no IPv6 routers present
eth0: islpci_close ()
eth0: resetting device...
eth0: uploading firmware...
eth0: firmware version: 1.0.4.3
eth0: firmware upload complete
eth0: interface reset complete
eth0: no IPv6 routers present

The thing is, "IPv6 over IPv4 tunneling driver" shows up in dmesg also, so I think it's loading properly but I'm not sure. I hope someone can help. :)

---

### Post by hidamari no tami on 2005-10-23
Ok...I tried re-installing Ubuntu several times to no avail (tried Warty, Hoary, and Breezy). I still can't connect via wireless, though I did notice something interesting: it seems that I connected for a few seconds since I was on just long enough to lease an IP from my router, but as soon as I typed 'sudo iwconfig' to see if I was still connected, it read that I was not. Also, I am still unable to scan.

---

### Post by Stelmate on 2005-11-08
What drivers are you using? ndiswrapper?  also eth0 should be your RJ45 and wlan0 should be your wifi card in ubuntu.  

[QUOTE=hidamari no tami]Ok...I tried re-installing Ubuntu several times to no avail (tried Warty, Hoary, and Breezy). I still can't connect via wireless, though I did notice something interesting: it seems that I connected for a few seconds since I was on just long enough to lease an IP from my router, but as soon as I typed 'sudo iwconfig' to see if I was still connected, it read that I was not. Also, I am still unable to scan.[/QUOTE]

---

### Post by hidamari no tami on 2006-05-08
[QUOTE=Stelmate]What drivers are you using? ndiswrapper?  also eth0 should be your RJ45 and wlan0 should be your wifi card in ubuntu.[/QUOTE]

Sorry been a while since I checked this board, but I'm still having the same problem. I know that it *should* be under wlan0 as opposed to eth0, but for some reason it was alwasy eth0 (when the wireless was working for example). 
The wired works as eth0 as expected, and wlan0 is an unknown interface when I try to access it (says 'Device not found'). However, the green light on the card (Netgear WG511 - the silver ended one, not the black one) blinks as if it was trying to connect to a network.

Hope someone can help!

---

