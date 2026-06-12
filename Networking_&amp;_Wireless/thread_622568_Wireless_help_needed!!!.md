---
title: "Wireless help needed!!!"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by FutbolEsVida on 2007-11-24
i am extremely new to ubuntu gutsy...i have everything installed but now my wireless will not connect. honestly, i dont even know if my usb antenna is seen by the computer. can someone please give me some help. ive been looking all over the forum for a solution but none of them seem to work for me. thank you a great deal.

---

### Post by mikewhatever on 2007-11-24
Click on the network manager icon (two monitors) in the top right conner. Do you see your network displayed? Does it say 'Wireless Network'?

Please post the output of the following command from the Terminal (Applications>Accessories) > sudo lshw -C network

---

### Post by gali98 on 2007-11-24
First of all... what is your card? Second if you run
```
iwconfig
```
if the card is running right then it should come up with something under wlan0 or wlan1.
One way to do it is just search "your card linux"  in google. this worked for me.

---

### Post by FutbolEsVida on 2007-11-25
> **mikewhatever said:**
> Click on the network manager icon (two monitors) in the top right conner. Do you see your network displayed? Does it say 'Wireless Network'?

Please post the output of the following command from the Terminal (Applications>Accessories)

output for sudo lshw -C network:

*-network
         description: ethernet interface
         product: 3c905C-TX/TX-M [Tornado]
         vendor: 3Com Corporation
         physical id: c
         bus info: pci@0000:02:0c.0
         logical name: etho0
         version: 78
         serial: 00:06:5b:80:85:7a
         size: 10MB/s
         capacity:100MB/s
         width: 32 bits59x
         clock: 33MHz
         capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 1000bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s

---

### Post by mikewhatever on 2007-11-25
Are you sure that was all the output? Run the command again and expand the terminal window. According to what you've posted, there is only an ethernet card and no wireless. What about the other questions I asked?

---

### Post by FutbolEsVida on 2007-11-25
> **mikewhatever said:**
> Are you sure that was all the output? Run the command again and expand the terminal window. According to what you've posted, there is only an ethernet card and no wireless. What about the other questions I asked?

The answer to your other question is that it does not see my wireless network...doesnt even say wireless connection. And im absolutely positive that i posted everything that came up in the terminal.

---

### Post by kevdog on 2007-11-25
Your wireless card -- is it usb or pci based (internal or pcmcia)?

---

### Post by FutbolEsVida on 2007-11-25
its a linksys wireless-G portable USB adapter

---

### Post by kevdog on 2007-11-25
So its not going to show up with these statements.  You will need to google around with the exact make, model and revision number (if known) in order to find the chipset of the device.  I believe it will probably be a ra chipset with something like an rt2500 driver.  I can't be sure.  Only you can find this information since you know what you have.  Possible chipsets would be broadcom, ra (rtxxxx), atheros.

---

### Post by FutbolEsVida on 2007-11-25
sorry to be annoying (and sound really stupid) but can you explain chipsets to me...are they like drivers?

---

### Post by FutbolEsVida on 2007-11-25
oh wait wait i might have found something already. this was posted on another linux forum:

Welcome to LQ!

I think that adapter should work with the rt2x00 driver. Have you tried that?

does this sound like something that should work? This was for the exact model adapter that i have as well just so you know...i thought that might be important =P

---

### Post by kevdog on 2007-11-25
Do not use the experimental rt2x00 driver -- still very unstable, you want the rt61, rt73, or rt2500 driver.  I dont know which one you will need specifically.

---

### Post by kevdog on 2007-11-25
Chipset = the brand of the hardwre microprocessor inside your device that is actually doing the wireless communication.  Linksys buys chipsets from various manufactures and just assembles them and puts their name on the outside.  There are only a handful of chipset manufactures. Many of the same chipsets can be found in Linksys, dlink, belkin products for example.

---

### Post by FutbolEsVida on 2007-11-25
ok thank you sooo much for all your help so far...ill keep looking out there for the chipset and ill get back to you.

---

### Post by kevdog on 2007-11-25
It sounds like your chipset is ra.  Ra chipset.  Within the Ra family there are different chipsets -- such as rt61, rt73, rt2500.

---

### Post by FutbolEsVida on 2007-11-25
found it!!! its the rt2500 just like you thought.

---

### Post by kevdog on 2007-11-25
Ok

Im pointing you to the best thread I know about rt drives.  Specifically this thread is for the rt73 driver -- so use some common sense.  Where they talk about rt73 -- you want rt2500.

The only exception to the instructions in this thread as I know is where you come to the blacklist part.  You want to blacklist the following modules:

rt2500pci rt2x000

So in the following statements you want to do:

sudo modprobe -r rt2500pci
sudo modprobe -r rt2500usb
sudo modprobe -r rt2x00lib

and

blacklist rt2500pci
blacklist rt2500usb
blacklist rt2x00lib

Here is the thread -- read it about 3 times and then you should have a clear understanding what to do:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

---

### Post by FutbolEsVida on 2007-11-25
thank you soooooo much once again!!!!

---

