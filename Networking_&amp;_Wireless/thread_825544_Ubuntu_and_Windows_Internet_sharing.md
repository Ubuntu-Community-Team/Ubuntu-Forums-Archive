---
title: "Ubuntu and Windows Internet sharing"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by dinotaz on 2008-06-11
HI

I have Ubuntu 8.04 installed on my PC and want to share my internet connection with two other window's PC on the network.

1. My PC has the router connected via usb.
2. I connect to the network via my network card.
3. The network hub is on one of the other Windows PC.
4. Ubuntu Can see the other computers on the network and they see me.

I remember i used to create a network bridge on my windows PC, so that the other computers could use my adsl connection. I have tried everything that i know (which is not much) and cannot find a way to set this up in Ubuntu.

Please help before the kids kill me.

---

### Post by MeURi on 2008-06-11
Avoid being killed by the kids while you look at [thread=132515]this thread[/thread] :-)

To tell the truth, I don't understand properly your setup: if you have a router, why don't you connect all the PCs to it? Or you meant your Ubuntu box is connected to the modem? Because I know only about modem-routers which have 4 ethernet ports :-)

Anyway, you should bridge your eth# interface to some pppo*, and I'm not sure if the link I provided suits your needs...

Hope it helps, at least a bit

---

### Post by dinotaz on 2008-06-11
Hi

The network cabling is setup this way and there is no adsl line where the hub is so that is why i have this setup.
Thanks

---

### Post by superprash2003 on 2008-06-11
you need to setup ICS in ubuntu [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

### Post by dinotaz on 2008-06-11
Hi

Thanks for the reply, but is there not a app that i can use to set this up for me, im not to good a typing and using the terminal, more scared that i mess up.

---

### Post by rickyjones on 2008-06-11
> **dinotaz said:**
> Hi

Thanks for the reply, but is there not a app that i can use to set this up for me, im not to good a typing and using the terminal, more scared that i mess up.

What kind of internet service do you have that has you connecting via USB? I know my first cable modem had both USB and CAT5 connections, but that is still an odd way to go.

The easiest way to go would be to get your modem connected to an actual router and let that handle it. It might save many hours of frustration.

Just my advice.

Thanks,
Richard

---

### Post by superprash2003 on 2008-06-11
you could try firestarter

---

### Post by dinotaz on 2008-06-11
Thanks guys, for all the help, all is up and runing.

Long live ubuntu !!!!!!!

---

