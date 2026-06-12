---
title: "[SOLVED] Connecting to bridged connection trouble"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by Six_Digits on 2008-04-08
I have a Laptop running Vista with a Wi-Fi connection bridged to my PC. Internet works great on my PC with Vista, but I can't seem to connect using Ubuntu 7.10. It shows a network connection but doesn't give me any internet. It's probably a simple fix, but I can't seem to find an answer.

More info:
Laptop running Vista
Connected to Neighbors Private Wi-Fi
Bridged Wireless-Local connection

PC dual boot Vista, Ubuntu 7.10
Connected to the laptops LAN, internet works good under Vista, but I don't know how to get it going in Ubuntu. I CAN see "Windows Network" in the network folder in Ubuntu however.

Internet-->Vista Laptop-->Ubuntu PC

---

### Post by Six_Digits on 2008-04-08
OK, I found this piece of information:

You may have to configure the interface through which you connect to use DHCP (dynamic configuration, usually the default) or specify an IP address, default gateway or DNS server.

I currently have it configured to use DHCP, but it doesn't work. How do I find the IP, Gateway, and or DNS server?

---

### Post by upthelum on 2008-04-08
Try a network setting other than bridged.

---

### Post by Six_Digits on 2008-04-08
Like what though? My only way to connect is through Wi-fi on the laptop. I'm paying a friend downstairs to share his internet.

---

### Post by upthelum on 2008-04-08
Well start with getting the wireless assistant from synaptic to check the strength of available signals.

---

### Post by Six_Digits on 2008-04-08
OK, not possible. The laptop runs Vista. PC runs Ubuntu and Vista, and is connected to the vista laptop via ethernet cable. When I run Vista on my PC, I have internet. On Ubuntu, local connection only. Signal strength is excellent on the laptop, Vista just wont share the connection with Ubuntu on my PC.

---

### Post by upthelum on 2008-04-08
Right your trying to connect via cable to vista pc which connects wirelessly, so you don't have direct access to the access point. Well i'm unsure what result you will get as vista is temperamental with a lot of software. Another thing, someone correct me if i'm wrong but should it not be a straight through cable for pc - pc, not ethernet.

---

### Post by Six_Digits on 2008-04-08
An ethernet cable IS what you use to network computers.

---

### Post by upthelum on 2008-04-08
Yes from modem/router to pc but not from pc - pc.

---

### Post by Six_Digits on 2008-04-08
Either way, it works in windows. What cable would you use besides a cat5?

Found this:
> **Re: How to?  Connect 2 PC's without router? **

     by [Grif Thomas]("http://forums.cnet.com/community/Grif+Thomas/?tag=usrprfl") [IMG]http://www.cnet.com/i/hlp/redM.gif[/IMG] - 10/30/04 7:08 PM
         In reply to: [How to?  Connect 2 PC's without router?]("http://forums.cnet.com/5208-6121_102-0.html?forumID=45&threadID=43285&messageID=508547#508547") by [dable]("http://forums.cnet.com/community/dable/?tag=usrprfl")          Dable,

**Remember that most of the programs will need to be "reinstalled" on the new computer if you're going to use them again.** So, if you only have a handful of documents, or small pictures, to transfer, some folks have done it by sending themselves, or a friend e-mail, then retrieving it when the new computer is installed.

On the other hand, if the old computer has large amounts of pictures, or other files, then you might want to network the two computers temporarily so the data can be transferred quickly and easily. Here are a couple of links on how you might choose to do that:

[Direct Connection with a "Laplink" Cable]("http://www.pcnineoneone.com/howto/filexfer.html")

[USB LinQ Link Cable Networking]("http://www.nti1.com/usb-link.html")

[USB Cable Networking : Introduction]("http://www.wown.com/j_helmig/usbmain.htm")

If both machines have a network card installed, purchase a CAT5 Cross-over cable and simply connect the two computers through the NIC's.:
[Configuring Your Home Network]("http://wpool.com/cablesharing/4.htm")

Hope this helps.

Grif


A little off topic but shows a category 5 cable will work fine as long as both computers have a networking interface card, which they do.

---

### Post by upthelum on 2008-04-08
Ok this is cat5 which is crossover:

_[http://www.zytrax.com/images/cat5_color.gif](http://www.zytrax.com/images/cat5_color.gif)_

and this is straight through:

_[http://www.incentre.net/incentre/images/ethcable568a.gif](http://www.incentre.net/incentre/images/ethcable568a.gif)_

Note the position of the inner twisted pair cables. It will perhaps connect with the proper cable, if indeed i am correct, no one has taken me up to verify this so take it as true until they do.

---

### Post by Six_Digits on 2008-04-08
I don't exactly know what that proves but it's not very helpful. Which cable I use should be irrelevant because it WORKS. If it makes you feel better, it's a TIA/EIA 568b according to the cable.

---

### Post by -random on 2008-04-08
simply running 'pppoeconf' worked for me..don't know much about this stuff though.

---

### Post by Six_Digits on 2008-04-08
Worth a shot.

---

### Post by Six_Digits on 2008-04-08
It says:
> Sorry, I scanned 2 interfaces but the Access Concentrator of your provider did not respondIt also says a possible reason for the failure could be due to another pppoe process which controls the modem.
I gotta get this, I don't want to switch to windows every time I want to go online!

---

### Post by Lazy-buntu on 2008-04-08
I think you do have to use a cross-over cable for pc to pc connections, but as for your original problem (ubuntu without wireless): check restricted drivers manager

if there's something like broadcom or bcm43xx listed in there, you have a driver issue, and more than likely you're going to have to use "ndiswrapper" to create a linux driver from a windows driver

---

### Post by Six_Digits on 2008-04-08
The laptop HAS VISTA, and HAS INTERNET. I want to share the internet with my PC. It works when I run Vista on the PC, but when I switch to Ubuntu, I'm only connected locally.  The ethernet card I have on my PC is recognized by Ubuntu and has worked previously when I was connected to my own router.

---

### Post by Six_Digits on 2008-04-10
OK, I guess I fixed it by making the wired connection on the Ubuntu PC use a static ip instead of DHCP. I simply used the same ip, subnet, and gateway Windows was using and it works fine.

---

