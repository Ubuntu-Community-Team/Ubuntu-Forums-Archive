---
title: "Acer Aspire 3050 wireless card"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by pedrobob on 2007-07-27
Helo there!! 

I bought an Acer Aspire 3050 some days ago, comes with vista where obviously everything works great... But a a use linux much more than linux. So here's the problem.

1. Sound Speaker doesnt works. Folowing a tutorial from forum. Now its works!! =)

2. Wireless Card... Still dont working... a found some tutorials on forum but any one works... the driver doesnt work... I installed the acer_acpi,OK. Try to use windows driver with ndiswrapper, but de device cant be founded.

Somebody knows how to install and use this wireless card?! 
Somebody has this model laptop and use the WiFi?!

Thanks!

---

### Post by noob12 on 2007-07-28
The first step is to identify what kind of wireless device is in your laptop and see if any driver is associated with it.  We can also see what driver you need for it.

```

sudo lshw -C network

```

and post the output.

---

