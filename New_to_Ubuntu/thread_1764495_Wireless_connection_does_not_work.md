---
title: "Wireless connection does not work"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by thefloods on 2011-05-21
I am an absolute beginner.  My mom put me onto Kubuntu because our computer kept being overcome with viruses.  I cannot get the wireless PCI card to connect to the internet.  I had this problem before, and was able to find a thread (somewhere) which led me to copy/paste some information in  the Terminal and do some tasks (can't remember what) in the internet browser preferences that fixed the problem.  I didn't save the data I used, and Have no idea what I did in the first place.  I have since upgraded the version of Kubuntu, and cannot find anything to make it work again.  The card is flashing with activity and sees the wireless signal but I can't get the computer to connect with it.  It gives me Connection State Configuring Interface, and then goes to Not Connected.  System Name eth1, it has a MAC address listed and the driver is airo_cs.  The Wireless signal is unencrypted, but  when I run nm-tool It says WEP encryption YES.  The wireless security setting is set to NONE in network connection wireless security.

I need step by step instructions to try to fix this issue.  They must be very basic (I haven't figured out what shell or widgets do).  

Please HELP!

---

### Post by Djalmahal on 2011-05-22
In general you should always post what hardware you are talking about. If you don't know the exact name of the wireless adapter type
```
lspci
```

that should give you the name of the wireless among other hardware related info.

Once you know the name of the wireless hardware start searching the forums for this piece of hardware. The fact tht you run Kubuntu shouldn't matter, it would be the same for all Ubuntu version.

Good luck
Andreas

---

### Post by grahammechanical on 2011-05-22
The utility nm-tool is only telling you the wireless capabilities or properties of the wireless adapter/card in the computer. It is not saying that network manager is using WEP encryption.

Does nm-tool list any wireless access points? These would be any modem/routers broadcasting a wireless signal within range of your computer. At the moment, nm-tool on my machine list 7 wireless access points (there are my neighbor's wireless connections). In the nm-tool list on your computer is you modem/router in that list?

On my machine I can see which of the wireless networks is using encryption. Two of them have WEP and three have WPA WPA2. That leaves two networks belonging to my neighbors that are unsecured. If you see WEP or WPA WPA2 against your wireless network then the router/modem is expecting an encrypted connection but network manager is offering an unencrypted connection. This is why the connection is failing to be made.

What does nm-tool say for Driver? Does it list a driver? What does it say for State? Does it say Connected? What does it say for IPv4 Settings.

All this information is usefull for working out what to do to put things right.

Regards.

---

