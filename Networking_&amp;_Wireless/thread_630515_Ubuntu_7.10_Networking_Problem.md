---
title: "Ubuntu 7.10 Networking Problem"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by RD0501 on 2007-12-03
Hi- I am completely new to Linux and Ubuntu, and I am just an average guy trying to learn something new. 

I have a wireless router connecting two XP laptops to the internet at home (there are no shared files on the laptops). I am trying to add a Ubuntu 7.10 PC and create a network to store and share files on the Ubuntu PC, which will be connected directly to the router. I want the Ubuntu PC to act as a server/NAS device.

Problem One:
I have read and followed several user guides from the internet and setup samba, but I can not get a network connection on the Ubuntu PC (the internet does work through the router). The wired network option in the GUI dropdown is grayed out, and it will not allow me to setup the networking. Any help would be great.

Problem Two:
How do I get the wireless XP laptops to connect/share to the wired Ubuntu PC?

---

### Post by lvleph on 2007-12-03
The wired selection only becomes selectable when the device becomes active (a cable has to be plugged in). If it still doesn't work when it is plugged in, I would say you have a driver issue.

However, even if it is greyed out you can still get to the network setting by system>administration>network.

---

### Post by RD0501 on 2007-12-03
Thanks for the quick reply. 

The cable is pluged in and I can access the web, so I think it's working. Do you know where I can find some additional information on the driver and how to update it?

---

### Post by sceo on 2007-12-03
Since the network and Internet are working, to get connections to the Windows machines, you just have to go to "places" from Ubuntu and click "connect to server" and enter the XP machine's information.

To share in the other direction, you need Samba installed (I think you've got it installed, maybe).  There's some configuration files and stuff you need to set up.  Then you should be able to, from your Windows box, browse the network and see your Ubuntu box with its exposed shares.  There's a little tutorial on Samba here: [https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-samba-server.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-samba-server.html)

---

### Post by RD0501 on 2007-12-03
> **sceo said:**
>  There's some configuration files and stuff you need to set up.  Then you should be able to, from your Windows box, browse the network and see your Ubuntu box with its exposed shares.


I did setup samba and configured the read/write access as well as setup a user and password using the command line. I still however can not access the Ubuntu pc using windows explorer. In fact, I don't have anything under my network places in the window explorer... is something in XP setup wrong? Please remember, I am new to all this...

Thanks!

---

