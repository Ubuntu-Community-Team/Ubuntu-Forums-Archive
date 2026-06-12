---
title: "can't connetc to the internet"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by albesan on 2006-11-29
hello team,

don't know what's going on but I can't get online.
I'm trying to connect through the internal ethernet port through a DSL modem modem/router. I can connect without a problem on Mac OSX using DHCP settings but xubuntu doesn't want to do it.

here is some output:

lspci|grep controller
0000:00:10.0 VGA compatible controller ATI Technologies RAGE mobility M3 AGP 2x (rev 2)


cat /etc/network/interfaces

auto lo
iface lo inet loopback
iface dsl-provider
inet ppp
provider dsl-provider

iwlist scan

lo interface doesn't support scanning
eth0 interface doesn't support scanning

ifconfig

lo	link encap: local loopback
	inet addr: 127.0.0.1 Mask: 255.0.0.0
	UP LOOPBACK RUNNING MTU:16436 Metric: 1
	RX packets: 0 errors:0 dropped:0 overuns:0 frame:0
	TX packets:0 errors:0 dropped:0 overuns:0 carrier:0
	
	collisions:0 Txquelen:0
	Rx bytes:0 (0.0b) Tx bytes:0 (0.0b)

any help would be greatly appreciated, I've exhausted trial and error and I'm totally new to linux.

a.

---

### Post by Iowan on 2006-11-29
Do you need to define the eth0 interface?
Here's a sample **interfaces** file I "borrowed" from another post (but his wasn't working either...)> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto dsl-provider 
iface dsl-provider inet ppp
provider dsl-provider


---

### Post by albesan on 2006-11-29
hey Iowan,
thanks for the reply.
Pardon my ignorance but, what do you mean by defining the eth0 interface? And where is the sample interfaces file you mention you "borrowed" from another post?

a.

---

### Post by Iowan on 2006-11-30
[QUOTE=albesan]Pardon my ignorance but, what do you mean by defining the eth0 interface?[/QUOTE]
I don't have DSL, but notice that the sample file has the section:```
auto eth0
iface eth0 inet dhcp
```
That defines eth0.  Your **interfaces** file seems to be missing that information - it also doesn't have the lines beginning with **auto** - which activates the interfaces on bootup.
I shoulda included the link before I lost it...
Here's another "similar" one:
[http://www.ubuntuforums.org/showthread.php?t=237539]("http://www.ubuntuforums.org/showthread.php?t=237539")

---

### Post by stream303 on 2006-12-01
Try this howto I wrote up for this common situation:

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)

Fast answer: put your isp's dns primary and backup nameservers into your router's setup page.

If you don't have access, you can edit one line of a file in the howto above.  I'll bet you're online!

---

### Post by koenn on 2006-12-01
> lspci|grep controller
0000:00:10.0 VGA compatible controller ATI Technologies RAGE mobility M3 AGP 2x (rev 2)
What you see here is your video controller. You should also get an Ethernet controller. The fact that it does not show up suggests that it is not present in your computer, or broken, ( or maybe : not a PCI card)

if your computer would detect a network card (NIC, ethernet controller, ...), it would give it a name (like eth0), and using that name, you can configure it (or check if its present in the configuration files mentioned in previous posts).

---

