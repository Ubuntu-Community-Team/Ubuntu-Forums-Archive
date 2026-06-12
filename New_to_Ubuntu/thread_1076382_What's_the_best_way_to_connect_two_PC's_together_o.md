---
title: "What's the best way to connect two PC's together on network?"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by suomalainen on 2009-02-21
Ubunteros,

I have a combination of laptops and PC's I'd like to all have accesssing each other.

Here is how my network is set uo

Broadband cable to Motorola Surfboard modem
Motorola Surfboard modem connected to D-Link DI-604 Router
PC connected directly to RJ-45 port on D-link Router
Linksys (vonage) router connected to D-link Router

Currently, 1 PC and 1 laptop use the Linksys router to access the Internet via 802.11G.

My question is this. How can I get all the devices to see each other so that files can be exchanged?

EXPERT assistance and insight most welcome!

Thanks!

---

### Post by superprash2003 on 2009-02-21
you need to setup samba for this [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by ugm6hr on 2009-02-21
> **suomalainen said:**
> I have a combination of laptops and PC's I'd like to all have accesssing each other.

If you want to share *all* files on both machines, I'd suggest using ssh to do this securely; you will need to have username / password access to both.

If you want to nominate specific folders to share, then either Samba or NFS will work.

---

### Post by jimrz on 2009-02-21
> **superprash2003 said:**
> you need to setup samba for this [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html)

or install open ssh server (from synaptic) on both the pc and the lappy, then go to Places > Connect to Server select "SSH", enter the ip addy of the machine you want to connect to and, since you won't want to do this every time, check the "bookmark" box then give it a name and it will show up in Places > Bookmarks and also Bookmarks in Nautilus. works great for me.

---

