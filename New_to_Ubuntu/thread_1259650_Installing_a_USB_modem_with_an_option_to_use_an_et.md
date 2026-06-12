---
title: "Installing a USB modem with an option to use an ethernet connection as well."
date: 2009-09-06
forum: New to Ubuntu
---

### Post by Miscible21 on 2009-09-06
Hi everyone. I am trying to install my iburst usb modem in Jaunty. I have browsed the forum and have seen a couple of posts adressing this. However, they havent provided insight into my problem.

I have followed some advice i found online and i have managed to install the open source driver for the iburst modem through the terminal. It was simple and im fairly certain that i did it correctly, because if i type in "plog" or "ifconfig ppp0" in the terminal window i get information regarding the iburst modem. The problem now is there doesnt seem to be an actual connection for iburst in jaunty, wired or DSL. The only connection thats displayed is AUTO eth0 even though Jaunty detected eth0, pan0 and ib0.

ibo Is the ethernet connection that the modem requires. it was detected, and presumably installed but i dont see any option allowing me to use this connection. I tried creating a dsl connection using my iburst deitals and copying the mac adress from the AUTO eth0 details. That didnt work. And i don't see how i could create another wired connection because i thought thats what installing the open source driver would do. Im a bit stuck as a result. so if anyone could help it would be greatly appreciated. It would bring me a whole lot closer to using Juanty exclusively lol :mrgreen:

---

### Post by Sealbhach on 2009-09-06
Hi, have you seen this post?

[http://ubuntuforums.org/showthread.php?t=1145369](http://ubuntuforums.org/showthread.php?t=1145369)

Does the network manager detect your modem when you attach it?

.

---

### Post by Miscible21 on 2009-09-06
> **Sealbhach said:**
> Hi, have you seen this post?

[http://ubuntuforums.org/showthread.php?t=1145369](http://ubuntuforums.org/showthread.php?t=1145369)

Does the network manager detect your modem when you attach it?

.
Hi Sealbhach

I didnt come accross that post when i was searching the forum. Unfortunately it doesnt apply to me. It actually applies to one of those 3G modems that mobile companies provide. My modem is a desktop usb modem. It has an ethernet port which is apparently means of creating a connection with it Juanty. In windows (XP) i just connect via the usb cable. the ethernet cable is used to connect a second pc to the modem. So at the moment I have both cables plugged into the same pc. Which means in windows it tries to establish a local connection as well as a normal braodband connectio. In Jaunty it just tries to use Auto eth0 when you turn it on.

---

### Post by Sealbhach on 2009-09-06
Oh, I see. have you been following the guide here?

[https://help.ubuntu.com/community/MobileWirelessBroadband](https://help.ubuntu.com/community/MobileWirelessBroadband)

.

---

### Post by Miscible21 on 2009-09-06
just checked the link. It's somewhat different to what i did. I had to make and install the driver via the terminal like the link says. butthe commands were different. I have saved the page and im going to boot into Jaunty to investigate the issue. I will use the page from there and i have a hunch i know how to fix it. Thanks for your help Sealbhach, i will post back to tell you if it works

---

### Post by Sealbhach on 2009-09-06
OK cool. It's possible that guide is a little outdated, but it is the official Ubuntu documentation.

.

---

### Post by Miscible21 on 2009-09-06
I'm almost ashamed to say so, but Ive figured out the problem... it was me lol. I made the mistake of connecting the modem via the ethernet cable not realising that the terminal commands were for the udb driver exclusively lol. This is why it registered the eth0 connection ahead of the ib0 connection during scanning, and thus never activated the ib0 connection. However, there is one flaw with the approach i used to install the modem. you have to activate and terminate the ibo connection in the terminal everytime you want to use the net as it doesent show up under any of your connections. Im sure that there is a way to make it a dsl connection and use a dailer of some to just click the connection on and off, this was mentioned in the link you gave me Sealbhach. But it is installed now and is fully functional anyway so what difference would a dailer make. Doing it via the terminal is probably more practical. 

Also, with ethernet it should be a plug in and play situation in Jaunty. But not while your usb cable is plugged in. This type of connection would be visible under your list of connections immeadiatly as "Auto eth0". However, connecting via "Auto etho wont work because your Isp details arent present. You therefore need to make a DSL connection to use the modem, filling in all the relevant details to make the connection i.e your isp details, mac adress etc. If you dont have them ( Like I didnt at one point) i dont think your ethernet connection will be established. Either way, you have options if your using this particular modem on ubuntu.

This modem is only available in South Africa as far as i know so I don't know how relevent this will be to people in the forum. But at least there is clearly a solution for Ubuntu newbies like me.

[This is the method I used.]("https://lists.ubuntu.com/archives/ubuntu-za/2009-June/003522.html")

---

### Post by Sealbhach on 2009-09-06
It's great to hear you got it working. You seem to know what you're doing so I'm sure you'll figure out a way to set it up a little better once you get to know it a little better.

 .

---

### Post by onegreenparker on 2009-09-21
I too am using the iBurst USB modem... and following the same instructions I got it working nicely.

However, I need to connect to my office VPN. Ideally I'd use NetworkManager but ib0 doesn't appear in the list of valid connections.

Anyone know how to add an interface to networkmanager?

---

