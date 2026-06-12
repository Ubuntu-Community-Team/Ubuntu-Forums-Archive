---
title: "NetworkManager - eth0 not managed"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by Redmage913 on 2011-09-06
Greetings,

I'm running a Dell Mini 9 that I installed with a mini.iso command line installation. From there, I installed lubuntu-desktop over wired Ethernet, using DHCP and a shared Internet connection with my XP computer.

However, now I cannot manage the eth0 interface with NetworkManager.  Any ideas how to fix this?

Here are my relevant lines of lspci:

```
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

I got the wireless working just fine through installing bcmwl-kernel-source, and I'm using that to talk to you right now.

Thanks,
Red

---

### Post by 2F4U on 2011-09-06
If you edit connections in Network Manager are you able to see the wired connection?

---

### Post by Redmage913 on 2011-09-06
When I open Edit Connections, there is no wired profile listed. I added a basic DHCP-powered connection, but I cannot connect to it since it's reported as "device not managed".

---

### Post by Overcast32 on 2011-09-06
Also check this: [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

If your NIC is configured with the interfaces file - I believe (I might be wrong!) that the other Network Management applets will have issues attempting to manage the connection.

Of course; you can configure it manually as well - the above link should give you a run down on it.

---

### Post by Redmage913 on 2011-09-06
here is my /etc/network/interfaces file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


```

---

### Post by Redmage913 on 2011-09-06
@Overcast32:

I want NetworkManager to handle it because I want to share the wireless connection with other computers. I have a basement apartment, and the only way to connect is through Wifi to a router above me.  I need to share the connection, and I know how to do that with NetworkManager.

---

### Post by Overcast32 on 2011-09-06
> **Redmage913 said:**
> here is my /etc/network/interfaces file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


```

I'm still a bit of a newb, but just at a glance, that file looks ok for it to allow the Network Manager to deal with the connections. In my case, I wanted to mess with it and then noticed the connection disappeared in the Network Manager, don't seem to be the case for you.. it's all set to auto.

Sadly, I'm on a Windows PC at work now, so I can't compare..

---

### Post by Overcast32 on 2011-09-06
> **Redmage913 said:**
> @Overcast32:

I want NetworkManager to handle it because I want to share the wireless connection with other computers. I have a basement apartment, and the only way to connect is through Wifi to a router above me.  I need to share the connection, and I know how to do that with NetworkManager.

A friend of mine was fighting with the wireless not long ago on his laptop. I'm sending him an IM to ask what app he used to configure it.. I'll reply when I find out. Maybe it'll help.

Sometimes I actually learn trying to help out too, lol.

---

### Post by Redmage913 on 2011-09-06
Hey, one of the best ways to learn is Watch, Perform, Teach.

---

### Post by Overcast32 on 2011-09-06
He used something called 'ndiswrapper' and it allowed a Windows XP wireless driver to load.. 

Dunno if that's any help.

---

### Post by Redmage913 on 2011-09-06
I appreciate the input, but I've got the wireless working just fine.  Ndiswrapper is a utility to extract drivers from a Windows-based setup wizard for a wireless device; since I'm having a wired issue, I can't use ndiswrapper.

---

### Post by 2F4U on 2011-09-06
> **Redmage913 said:**
> here is my /etc/network/interfaces file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


```

Here is my /etc/network/interfaces file

```
cat /etc/network/interfaces 
auto lo
iface lo inet loopback


```

I would suggest that you remove eth0 from /etc/network/interfaces and see if Network Manager is then able to manage it.

---

### Post by Redmage913 on 2011-09-06
That did it! Now, one more related question - was that left over from when I did the CLI install? I'm guessing the network daemon used it?

---

### Post by 2F4U on 2011-09-06
I would guess that this was left over from your install when you manually configured dhcp. On by Ubuntu server installation without GUI, I don't have Network Manager (and don't need it) and on that machine, I am using this same method to configure eth0.

---

