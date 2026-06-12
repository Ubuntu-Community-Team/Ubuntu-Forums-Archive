---
title: "No wireless on edgy install, everything else does have wireless"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by IngmarBlonk on 2007-03-22
Sorry for my English, but I'm dutch.

I've been using dapper a time now, but I wanted the new features of edgy (eg. firefox 2, etc).

So I first tried the live/desktop-cd, everything worked.
I always install using the alternate cd's, everything went fine, just like always.

So after the install, I wanted to install drivers and stuff, so I needed internet.
But when I tried to config my wireless card I saw some weird things.
I have a analog modem, wired network card, wireless network card (Intel PRO/Wireless 3945ABG).
But here is the output of some commands:

**Output ifconfig:**
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
```

**Output iwconfig:**
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

**Output lspci | grep "Network controller":**
```
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

As you can see ifconfig doesn't recognize my wired card, but iwconfig does.
iwconfig doesn't recognize my wireless card.
My modem is only recognized my iwconfig.

The standard network-tool recognizes everything except of my wireless:
[img]http://img375.imageshack.us/img375/8175/screenshotnetworksettinwm2.png[/img]

So what's wrong, do I need to turn my wireless on?
And what about ifconfig only recognizing the loopback?

On dapper everything worked perfect, same as using the live/desktop-cd.

Ingmar

---

### Post by DonnieP on 2007-03-22
Use Synaptic Package Manager to install linux-restricted-modules.  This will take care of the 3945 card.  Good luck (and your English is great)!

---

### Post by IngmarBlonk on 2007-03-22
> **DonnieP said:**
> Use Synaptic Package Manager to install linux-restricted-modules.  This will take care of the 3945 card.  Good luck (and your English is great)!

Thanks, it works.
But what about ifconfig only recognizing the loopback? There is something wrong too, i think.

---

### Post by DonnieP on 2007-03-22
Did you re-run ifconfig after installing linux-restricted-modules and successfully connecting with the wireless card?  My ifconfig (I have the same 3945 card) shows eth0, eth1 and lo.  eth0 is the ethernet port that I don't use.  eth1 is the wireless card and it shows the IP address assigned by my router.

---

### Post by IngmarBlonk on 2007-03-22
> **DonnieP said:**
> Did you re-run ifconfig after installing linux-restricted-modules and successfully connecting with the wireless card?  My ifconfig (I have the same 3945 card) shows eth0, eth1 and lo.  eth0 is the ethernet port that I don't use.  eth1 is the wireless card and it shows the IP address assigned by my router.

Yes, I re-ran it, now it shows my wireless card info but not my wired card.
See it yourself:

**Output ifconfig:**
```
eth1      Link encap:Ethernet  HWaddr 00:13:02:8F:C2:C1  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe8f:c2c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57602 errors:0 dropped:8814 overruns:0 frame:0
          TX packets:24442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63084660 (60.1 MiB)  TX bytes:1858203 (1.7 MiB)
          Interrupt:185 Base address:0xc000 Memory:fe1ff000-fe1fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)
```

---

### Post by DonnieP on 2007-03-22
Well, you're quickly moving beyond my limited experience.  But based on my recent installation of Edgy on my laptop that has the 3945 wireless, I'm wondering if you've actually connected anything to the hard-wire ethernet port?  In my case, since wireless didn't work immediately post-installation, I had to plug my ethernet cable directly into my laptop to be able to download linux-restricted-modules.  After that I was able to use the wireless card for internet connection.  But I did actually use the hard-wire ethernet port for a short while.  Sorry I can't provide the answer, but I've never tried to connect Ubuntu to the internet with a modem.

---

### Post by IngmarBlonk on 2007-03-22
I installed the linux-restricted-modules from the cd, when I got internet i updated them of course.

But I'll try to connect wired.

Edit: Nope, doesn't seem to work...

---

### Post by dbott67 on 2007-03-22
Are you using [COLOR=Blue]**ifconfig**[/COLOR] or **[COLOR=Blue]ifconfig -a[/COLOR]**?  I think that ifconfig only displays active interfaces, where as the -a displays all interfaces.

Can you post the output of:
```
dbott@thedrake:~$ [COLOR=Blue]**cat /etc/network/interfaces**[/COLOR]
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

### Post by IngmarBlonk on 2007-03-23
I'm using "ifconfig".

My interfaces looks like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```

But ifconfig doesn't check the interfaces file i think, because it sees my wireless card but no wired card.

---

### Post by Jouke74 on 2007-03-23
Install Gnome-network-manager + network-manager to take care of your wireless configuration. Much easier. To have you other devices there working too, deconfigure all connections in the "network administrator / networking" which is already in the menu.

---

