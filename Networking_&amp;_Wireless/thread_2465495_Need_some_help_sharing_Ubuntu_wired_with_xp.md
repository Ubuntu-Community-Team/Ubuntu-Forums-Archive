---
title: "Need some help sharing Ubuntu wired with xp"
date: 2021-08-03
forum: Networking &amp; Wireless
---

### Post by tiddybit on 2021-08-03
I've searched google and here but I've tried and failed. Maybe I'm overlooked something but hoping you guys can help.

I'm using my laptop with relatively new Ubuntu 20 groovy guerilla install.

I have connected to wifi (successfully) and connected to on older desktop via wired (cat5e)

I am attempting to share the wired with the XP desktop.

I have enable "share with other computer" with ipv4 and 6 on laptop running Ubuntu on wired and set the IP accordingly with the windows XP desktop up, DNS, gateway, etc.with up address something like 254.207.1.5 and DNS as shown on laptop 254.207.1.1 etc

The XP desktop shows in and out connection packets but Firefox and anything else still does not connect. Task manager shows 0% connection use.

What am I doing wron? Yes i know XP is old lol sorry

---

### Post by Autodave on 2021-08-03
Someone will hopefully correct me if I am wrong here, but to connect one PC to another requires a different cable than your normal ethernet cable: there are (I believe) 2 wires that have to be reversed.  And if I remember correctly, buying one of these cables, they are orange in color to differentiate them from a regular ethernet cable.

---

### Post by monkeybrain20122 on 2021-08-03
Why don't you just install your antique XP in a VM and free your other computer for something better? ;)  It would be a lot simpler to set up. Moreover  XP should not be online in any case.  TBH, XP is long dead, just bury it and RIP.

---

### Post by tiddybit on 2021-08-03
you can share internet connection via eathernet with devices and other computers sharing a computers WIFI. I have done this playing xbox live and an old laptop that didnt have wifi long time ago. Its not ideal but works. cant seem to get it going again.

---

### Post by tiddybit on 2021-08-03
Yeah I plan on backing up the important stuff off of it but its been sitting there not doing anything for like 3+ years. I may just get a usb wifi adapter i had one someplace but couldnt find it. I was just trying to see if i couldnt get windows to detect the pci wifi adapter i have in it as I dont recall wtf it is. lol I was just looking for something that the kiddo could start using for homework and simple stuff.

---

### Post by TheFu on 2021-08-03
> **tiddybit said:**
> Yeah I plan on backing up the important stuff off of it but its been sitting there not doing anything for like 3+ years. I may just get a usb wifi adapter i had one someplace but couldnt find it. I was just trying to see if i couldnt get windows to detect the pci wifi adapter i have in it as I dont recall wtf it is. lol I was just looking for something that the kiddo could start using for homework and simple stuff.

Kids should be using Linux for their homework.  Use a lite distro, say xfce/lxqt/mate as the base and show them libreoffice.  They will figure it out and will be teaching you in a week.

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
[https://www.tecmint.com/share-internet-in-linux/](https://www.tecmint.com/share-internet-in-linux/)

Also, as  Autodave wrote above, GigE ethernet (and faster) network connections do not need a special cable because the standards include that feature, but all the slower network cards do need what's called a crossover cable. [https://en.wikipedia.org/wiki/Ethernet_crossover_cable](https://en.wikipedia.org/wiki/Ethernet_crossover_cable) has more details. A cable or an adapter are necessary for those slower connections.

It would be best to put WinXP into a non-networked environment and use sneakernet.  With a kid, ready to click almost any button there is, XP on the internet is too dangerous.  I have an XP virtual machine to play some single user games on, but it doesn't have any network access at all.

---

### Post by monkeybrain20122 on 2021-08-04
> **tiddybit said:**
>  lol I was just looking for something that the kiddo could start using for homework and simple stuff.

Why do you want to do that? Kids start with a clean slate, their habits haven't formed yet so they can pick up anything fast. Why do you want to condition them with an antique version of Windows which belongs to the museum or the software junk yard? TheFu is absolutely right, they will pick up on Linux real fast.

---

