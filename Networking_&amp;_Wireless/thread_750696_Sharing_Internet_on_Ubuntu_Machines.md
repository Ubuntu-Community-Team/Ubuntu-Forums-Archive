---
title: "Sharing Internet on Ubuntu Machines"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by Tanth on 2008-04-09
I'm trying to share the internet connection my laptop get's from the wifi with my desktop computer using an ethernet cable. 

I've read that the easiest method is through firestarter, but, when I enable internet connection sharing in firestarter, I get the message that eth0 is not ready.

any help?

---

### Post by superprash2003 on 2008-04-09
you could try this tutorial [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

### Post by Tanth on 2008-04-10
I've tried that. Got nowhere. Every command seems to go find, but I still can't get a connection on my desktop.

---

### Post by superprash2003 on 2008-04-10
did you try that tutorial disabling firestarter?

---

### Post by Tanth on 2008-04-10
I tried that before using firestarter.

---

### Post by superprash2003 on 2008-04-10
are you able to ping successfully between the two pcs?

---

### Post by Tanth on 2008-04-10
No, pinging between the computers doesn't work,

---

### Post by superprash2003 on 2008-04-11
have you already set manually ips on the ICS host and client?

---

### Post by Ayuthia on 2008-04-11
> **Tanth said:**
> I'm trying to share the internet connection my laptop get's from the wifi with my desktop computer using an ethernet cable. 

I've read that the easiest method is through firestarter, but, when I enable internet connection sharing in firestarter, I get the message that eth0 is not ready.

any help?
I think that you need to use a crossover cable instead of a regular ethernet cable.  I thought that regular ethernet cables use routers.  I could be wrong though.

---

### Post by Tanth on 2008-04-11
I'm an idiot. I had no idea a crossover cable is different from an ethernet cable.

---

### Post by kokushibyou on 2008-04-12
> **Tanth said:**
> I'm an idiot. I had no idea a crossover cable is different from an ethernet cable.

I wouldn't go that far.  A good rule of thumb is that straight-through cable is good for one device to a different one (PC to switch, for instance).  Crossover cable is for two similar devices (PC to PC).  And, you'd probably never use rollover cable since it connects a PC to the console port on a router or switch.  Also, ethernet is merely the standard encoding of the packets.

---

### Post by Tanth on 2008-04-12
So, I went out and bought a crossover cable.

The computers both recognize a wired connection, but there's still no connection to the desktop. I tried enabling ipv4 port forwarding, and still no progress. Any thoughts?

>> By the way, I should probably mention the laptop is a Gateway MT 3422

---

### Post by h4mx0r on 2008-04-12
The cable you use to connect a computer to a router is the same you would use to connect a computer to a computer because they are both IP abiding layer 3 devices.

---

### Post by Tanth on 2008-04-12
> **h4mx0r said:**
> The cable you use to connect a computer to a router is the same you would use to connect a computer to a computer because they are both IP abiding layer 3 devices.
 
They're definitely 2 different products, seeing as both computers now both respond to the crossover cable. They did not respond to the basic ethernet cable.

Still no internet. though.

---

### Post by Tanth on 2008-04-13
bump

---

### Post by Tanth on 2008-04-15
still nothing?

---

### Post by SpaceTeddy on 2008-04-15
assuming that your two computer can ping each other, [here]("http://ubuntuforums.org/showthread.php?t=713874") are a few steps on how to do internet sharing with ubuntu...

---

### Post by AgentZ86 on 2008-04-18
> **Tanth said:**
> still nothing?

Hi,

Try the link SpaceDaddy provided I was suspecting this topic myself.

Basically your computer normally would get it's IP address from the ISP server and thus if you want to share the connection your sort of turning your computer into a mini server type device in which you want the shared client computer to get it's IP address from the internet sharing computer. So that is why SpaceDaddy's instructions indicates this new configuration setting so that your ethernet on the internet computer will have a static ip address instead of trying to find an IP from your internt sharing computer, because your internet sharing computer could be setup as a DHCP server and give out ip addresses, however that would most likely interfer with it's receiveing and getting the IP address from the ISP and thus your 2 computers could connect to eachother, however they would lose the internet.

I know it sounds complicated if you don't know much about networking, but basically your internet computer is getting info from the ISP and not really sending info to the ISP and because of that, your client computer is not receiving the required information from your internet computer, and thus you can't connect. to the internet sharing computer.

So SpaceDaddy's instructions force the internet sharing computer to have a fixed IP address that you can configure on your client computer so that you can access the internet sharing computer properly.

Anyhow I hope this helps a bit, to at least clarify some of the network topics.

And yes you do need a crossover cable in connecting 2)ethernet cards together. 
And you don't need crossover cables to connect to a routher or switch because that is functions of a router is to make those crossovers internally so that you can use straight cables.
Very old routers all needed to be crossovers because they did not have the switch built in, anyhow just fyi on that topic.

I hope you get it working I'm also working on some internet sharing with my t-mobile dash so I'll be checking back in on this.

---

### Post by owhno on 2008-04-19
Hi,
I'm the writer of the blogpost on [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29), this worked perfect for me without a cross cable. But you still have problems with it. So if you give me your setup (aka gutsy desktop to desktop and other special features) maybe i can recreate your typical setup here at home and make a new updated tutorial

---

### Post by zazuge on 2008-04-19
remember to put the 2 pc in different subnets 
for instance if you have a DSL router-modem set on 192.168.1.1
then your PC maybe is 192.168.1.2 (the router modem may have dhcp enabled)
then you have to put the second ethercard on 192.168.0.1
and last your laptop on 192.168.0.2
goodluck ;-)

oh I forgot does anyone know how to manage the bandwith between the PCs in this configuration
it seems tha the gateway PC always monopolise the bandwith for his own downloads.

---

