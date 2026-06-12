---
title: "Add an Access point to a network?"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by rieves on 2008-09-11
I currently have a router through which our internet connection goes.  I've recently purchased a HP C6280 printer, which has an ethernet connection.  I would like to keep my printer in my room, so I purchased another router and have set up that network.  The problem is, when I want to print I have to disconnect from the internet carrying network, to the one that's only for my printer.

Is there a way to configure the second router to wirelessly connect to the internet-carrying router?

If it helps the internet router is a Myessentials (which can be configured for a WDS), and the printer one is an Ativa (which cannot, only as an access point).

---

### Post by bab1 on 2008-09-11
It looks like the Myessentials router has a 4 port switch built into it.  You should be able to plug the printer into it.  The printer and your computer should be on the same network that has internet connectivity.

The Myessentials is the gateway device to the internet, but it should be able to allow interconectivity to your local network devices.  What (why) do you use the Altvia for?  Why can't everything be on one network?

The most important thing is to figure out the network topology.  How it is physically and virtually laid out.

---

### Post by rieves on 2008-09-11
I live in an apartment with 3 other people, so the internet gateway (myessentials) has to be centrally located and there isn't room for the printer where the modem needs to be.  The ativa is wired to the printer, and is located in my room.

What I'd ultimately like is to have one SSID so I can print and surf the web at the same time, is this possible with the hardware I have?

---

### Post by bab1 on 2008-09-11
Maybe, but I need more info.  Is the Ativia connected to anything else?  Do you have a laptop with wireless and wired?  It sounds like what you are doing right now is connecting using wireless to the internet and when you need the printer you connect wireless (diff net) to the printer via the Alitiva.  Is this so?

---

### Post by rieves on 2008-09-11
Yes, that is true of how I am currently operating... I would like it all to be under one network, but with two routers (slash APs)

There are no other wired components to the network other than the Modem plugged into the Myessentials WAN port, and the printer plugged into the 1st ethernet port on the Ativa


Thanks so much for your help so far, by the way!!!

---

### Post by bab1 on 2008-09-11
I have looked at the manuals for both routers.  

This might work.  We will have to try an experiment.  I would try to use the setup you have for the printer [COLOR="Red"]**BUT**[/COLOR] on the "web net"  We really need to be specific here -- the network I am referring to is the network you use when you surf the internet IE: 192.168.0.n or something like that.  

You have been able to use the Atvia as a receiver from your laptop, so in theory it should be able to receive a signal from the Myessentials router too.  Use the same procedure but configure the Atvia to use the SSID of the Myessentials and give it an IP address in the network.  Then see if you can see or print to it.  You did use the Atvia as a AP; right?

Sorry i can't be more specific here, but we are experimenting.  An access point is usually used to add wireless capability to the network not to a device.  But it worked, so who am I to say not to do what you have done so far.  Using the 192.168.[COLOR="Blue"]**0.n**[/COLOR] network, It would look like this;

```

[COLOR="Blue"]**0.10     0.11          0.1              0.25 **[/COLOR]
HP<=====>Atvia<=======>Myessentials<===>your_laptop
```

---

