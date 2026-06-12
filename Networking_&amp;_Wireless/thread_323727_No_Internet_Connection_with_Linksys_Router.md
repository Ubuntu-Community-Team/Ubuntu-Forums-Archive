---
title: "No Internet Connection with Linksys Router"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by tikbjamin on 2006-12-22
So I ended my Internet Connection Sharing experiment and got a Linksys BEFSR1 router.  My XP box connects just fine and I have internet access.  The Ubuntu box does not and I have no access to the internet.  I need some guidance in getting this working again.

Disabled eth1, and removed Firestarter.

Edgy Eft, 512 MB RAM, Linksys NC 100 ethernet card.  Let me know what else you need to help me.](*,) :confused:

---

### Post by dbbolton on 2006-12-22
what kind of security does the router have ?

---

### Post by tikbjamin on 2006-12-22
> **dbbolton said:**
> what kind of security does the router have ?

Router came with Norton internet Security which has an intrusion prevention feature installed on the XP box.  Is that what you mean?

Edit:  Router has Filter and VPN passthrough tabs.

---

### Post by dbbolton on 2006-12-22
on my linsys router if you go to [http://192.168.1.1/](http://192.168.1.1/) you can set all the security settings, but its a wrt54g

---

### Post by tikbjamin on 2006-12-22
> **dbbolton said:**
> on my linsys router if you go to [http://192.168.1.1/](http://192.168.1.1/) you can set all the security settings, but its a wrt54g

Yeah, I see the menu but I have not blocked any addresses with the router, but I still can't access the internet.

---

### Post by tikbjamin on 2006-12-22
> **tikbjamin said:**
> So I ended my Internet Connection Sharing experiment and got a Linksys BEFSR1 router.  My XP box connects just fine and I have internet access.  The Ubuntu box does not and I have no access to the internet.  I need some guidance in getting this working again.

Disabled eth1, and removed Firestarter.

Edgy Eft, 512 MB RAM, Linksys NC 100 ethernet card.  Let me know what else you need to help me.](*,) :confused:

Anybody out there?  

Please note that I do not get any internet access when I make a direct modem to computer connection.  So, my guess is that it is not a router problem, per se.

---

### Post by dbott67 on 2006-12-22
I need you to post the output of a few commands.  Seeing as you can't get online, I wouldn't want you to have to type everything out so you might want to use this little tip below:

[COLOR="Blue"][I]A little trick that you might use when you can't get online is to use a floppy/usb thumb drive/CDRW/SD card.  If you've got a thumb drive, it should mount automatically to the Desktop folder.  I've got a Corsair USB thumb drive that mounts as /home/dbott/Desktop/CORSAIR.

Knowing this, I can copy & paste the output from the terminal into a text file on the thumb drive and then bring it over to a working computer.

The other way to do it would be to use the 'redirect' option.  Instead of displaying the output on screen, you can re-direct the output to a file:
```
ifconfig -a > ~/Desktop/ifconfig.txt
```
The above command would create a file on my desktop called ifconfig.txt.  To copy it straight to my USB drive, I would type:
```
ifconfig -a > ~/Desktop/CORSAIR/ifconfig.txt
```

You can do this for every command to save a lot of typing.[/I][/COLOR]

Can you please post the output of the following commands:

```
cat /etc/network/interfaces 
```

Here's mine as an example:

```
dbott@dapper:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```

This command shows ALL network interfaces on the system (whether enabled or not):

```
ifconfig -a
```

```
dbott@dapper:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```

This command outputs the network hardware detected:

```
sudo lshw -C network
```

Here's mine for comparison:

```
dbott@dapper:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```

-Dave

---

### Post by tikbjamin on 2006-12-22
Dave,
Thanks for your reply.  I read your instructions on another thread, checked and realized that the output from my computer was OK and I should have been getting Internet access.

Anyway, I cleaned my orphaned files/packages and I was downloading email and surfing 15 seconds later.  Firestarter plus some other files I had modified in Breezy when I did the Internet Connection Sharing were removed.

Thanks, man.  Merry Christmas.

TikBJamin

---

