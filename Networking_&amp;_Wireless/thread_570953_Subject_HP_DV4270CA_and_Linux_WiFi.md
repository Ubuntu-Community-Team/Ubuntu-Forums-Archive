---
title: "Subject: HP DV4270CA and Linux WiFi"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by jphebert on 2007-10-08
G'day all,

I installed Ubuntu onto my trusty DV4270CA (Centrino) and all is fine but for WiFi.. I can't find the way to enable / turn on the wireless card.  Not bad for a newbie to Ubuntu! (XP power user looking for alternatives :))

I have a button that I usually press to activate the wireless card  but under Linux and it's not collaborating. Should I install another driver than the one that comes with 7.04 or something else?

Any words of wisdom on the HP DV4000 series laptops?  This unit runs the Intel 2200BG card.

Thanks!!!

---

### Post by Lambert on 2007-10-09
> **jphebert said:**
> G'day all,

I installed Ubuntu onto my trusty DV4270CA (Centrino) and all is fine but for WiFi.. I can't find the way to enable / turn on the wireless card.  Not bad for a newbie to Ubuntu! (XP power user looking for alternatives :))

I have a button that I usually press to activate the wireless card  but under Linux and it's not collaborating. Should I install another driver than the one that comes with 7.04 or something else?

Any words of wisdom on the HP DV4000 series laptops?  This unit runs the Intel 2200BG card.

Thanks!!!

Open a terminal and type this command

```

sudo echo 0 > /sys/bus/pci/drivers/ipw2200/*/rf_kill

```

The wiki page on this laptop says that key works so not sure what is happening for you.
[https://wiki.ubuntu.com/LaptopTestingTeam/HPDV4000?highlight=%28dv4000%29](https://wiki.ubuntu.com/LaptopTestingTeam/HPDV4000?highlight=%28dv4000%29)

---

### Post by roscomca on 2007-10-19
I am not sure if this will help but I have an HP NX8220 laptop with a button to turn wireless on and off. It was doing nothing until I found in another thread to enter the following command to tell the driver that the "kill switch" is set to on. PS my laptop doesn't have a hardware slider switch.

```
 sudo modproble fsam7400 radio=1
```

Now the on/off button does indeed turn the radio on and off!

I did the following to make the change permanent:

```
 sudo echo options fsam7400 radio=1 >> /etc/modprob.d/options 
```

Hope this helps, it took me ages to get the WiFi working.

---

