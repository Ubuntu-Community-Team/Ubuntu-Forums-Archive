---
title: "please help. installed WICD but not getting any connections picked up"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by ogwilson on 2007-10-26
I installed WICD on my laptop and i cant get any of the networks to be discovered. i dont know what to do, and my wireless is integrated and enabled. can anyone please help?

---

### Post by #Reistlehr- on 2007-10-26
copy the output of 

ifconfig

---

### Post by ogwilson on 2007-10-26
ok sorry, here is what i get from ifconfig

> eth0      Link encap:Ethernet  HWaddr 00:1C:23:8E:37:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11600 (11.3 KB)  TX bytes:11600 (11.3 KB)


---

### Post by #Reistlehr- on 2007-10-26
Well you have no wireless interface listed. Only loopback, and your wired. What kind of wireless?

---

### Post by ogwilson on 2007-10-27
well my laptop is a Dell Latitude D520. It has integrated wireless of the Broadcom family. BCM 43xxx family. At least thats what my lspci query in the terminal told me. I have to charge my laptop up ill post it once its charged.

---

### Post by kevdog on 2007-10-27
Did you install the driver for your card.  Either through the linux-restricted package or with ndiswrapper/XP driver??

Nothing is going to work without a driver.

---

### Post by ogwilson on 2007-10-28
well i did install the restricted drivers, but that did nothing for me. ndiswrapper was always alwayas asking for Ubuntu 7.10 or 7.04 i386 cd and always i put it in, but nothing.

How can i get the XP driver?

---

### Post by kevdog on 2007-10-28
Depending on your card you are going to have to have to CD or download the driver from the manufacture's website.  Do you know the chipset of the card?

---

### Post by ogwilson on 2007-10-28
The only thing I know about the card is that it's made by Broadcom. here are specifics from the lspci query

```
0c:00.0 Network Controller: Broadcom Corporation Dell Wireless 1390 WLAN MINI-PCI Card (rev 01)
```

---

### Post by kevdog on 2007-10-28
In my signature there is a link for connecting via the command line.  If you look at this thread -- at the bottom there is a reference section -- Jamie Jackson wrote a thread about broadcom driver installs in 5 minutes

---

