---
title: "Actiontec EX560LKU external 56k USB/Serial modem working"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by Tuxtur on 2006-07-21
I have an ActionTec EX560LKU USB/Serial modem I got working without too much trouble so I thought I'd share my experience and save someone time. 

This modem has both USB and Serial connections. I can't use serial for other reasons so USB was my only real option. 

1. I went into Device Manager to see if modem is listed. it was as PL2303 

2. In Terminal I did "dmesg | grep USB" (note | is a character on the keyboard)

dmesg listed PL2303 as attatched to USB0

3. I used the menus System> Administration> Networking> Modem Connection> Properties> Modem> General type in your provider and account information.

Then in the Modem tab at the Modem Port field type in /dev/modem

4. In Terminal type "ln -sf /dev/ttyUSB0 /dev/modem"

Back to menu System>Administration>Networking>Modem Connection click on activate to dialout. Later click deactivate to disconnect.

Thats it, believe me it reads harder than it is.

I found since this modem is a real hardware modem that even using the USB connection I didn't need any drivers. There seems to be some confusion about this as I've seen posts of people talking about getting drivers for USB hardware modems, in this case I didn't find it necessary.

---

### Post by zxee on 2006-07-21
You were lucky. In my experiance alot of usb modems are soft or controllerless modems that require windows or linux drivers to work. A good resource for those who are unsure of the compatibility of their modems is [http://www.linmodems.org/](http://www.linmodems.org/)
I don't actually know if there is a hardware database at the ubuntu site. Your write up should be there if is there is-good job!

---

### Post by Kennny on 2006-10-27
Your solution works great -however - as soon as I disconnect all is wiped out and I have to go thru the rig-a-morole everytime I connect.  Did you find a solution for that?

BTW: I would never have thought of the substitution. Great thinking...

ken

---

### Post by age on 2006-10-28
> **Tuxtur said:**
> I have an ActionTec EX560LKU USB/Serial modem I got working without too much trouble so I thought I'd share my experience and save someone time. 

This modem has both USB and Serial connections. I can't use serial for other reasons so USB was my only real option. 

1. I went into Device Manager to see if modem is listed. it was as PL2303 

2. In Terminal I did "dmesg | grep USB" (note | is a character on the keyboard)

dmesg listed PL2303 as attatched to USB0

3. I used the menus System> Administration> Networking> Modem Connection> Properties> Modem> General type in your provider and account information.

Then in the Modem tab at the Modem Port field type in /dev/modem

4. In Terminal type "ln -sf /dev/ttyUSB0 /dev/modem"

Back to menu System>Administration>Networking>Modem Connection click on activate to dialout. Later click deactivate to disconnect.

Thats it, believe me it reads harder than it is.

I found since this modem is a real hardware modem that even using the USB connection I didn't need any drivers. There seems to be some confusion about this as I've seen posts of people talking about getting drivers for USB hardware modems, in this case I didn't find it necessary.

I'm running same modem but as serial and it works , but I cant find it in device manager other then I think pnp0501 under 15550a compatububke com port. I'm new to this and In modem network setup its assign devtty0. I want to use it as usb but I have like 7 other connections. should I be seeing modem in the device manager?
can I use usb 0 if I have other plugged in . is there away to check interference???

---

### Post by Raval on 2006-12-03
Hey thanks, I got this modem to dial up wit hyour info however, while the modem stays connected, I am still unable to browse any idea what could be the problem?

---

### Post by Raval on 2006-12-04
I am now able to browse however I too have to reset the connection everytime I boot up.

---

### Post by FuzzMaster on 2007-02-17
Sorry for the bump... I tried this technique, and it all goes well until the end, where my modem just... won't connect.  I see no activate button, and the little modem monitor panel thing won't let me activate.

Any ideas?  My device manager says it's the same device (PL2303) and at the same place (USB0) as the topic creators

---

### Post by Raval on 2007-02-17
You have to do it under admin- networking

---

### Post by fruitsofherwomb on 2007-04-30
Revival :KS 

basically, I got this modem for free from a friend since the one my pc came with always disconnects. First of all I got to show up on 7.04. But when I go to 'Dail' it makes weird as noises then just drops. 

Also, it refuses to be set in tone instead of pulse.

---

### Post by Raval on 2007-05-02
I just did an upgrade from dapper to edgy it was a clean install and this method no longer works. If I can't get this to work I'll rarely using Linux again.

---

