---
title: "Intel 3945ABG wirless card does not appear in network manager"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by SDE on 2007-04-10
I installed Feisty and I can't get my wireless card to show up.  My wired nic works fine.  I'm on a Toshiba Satellite P105-6084 with an Intel 3945ABG wireless card.

All that appears in System->Network is my 'Wired Connection' and my 'Modem Connection'

Here is an lspci, ifconfig, iwconfig

```
$ lspci | grep 3945ABG
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:63:71:3F  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe63:713f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1304444 (1.2 MiB)  TX bytes:233215 (227.7 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)
```

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

currently my /etc/network/interfaces file looks like this, however i have tried it with eth0 and eth1 as well.  so many different suggestions on the internet.
```
$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

I would appreciate any help anyone can offer.

Thanks.

---

### Post by Rospo Zoppo on 2007-04-10
I have the same card and Feisty kernel and I managed to get it work. I have follow an Italian how-to and I hope you can find an English one.. If you can't I will write here the steps.. :D

---

### Post by kwaanens on 2007-04-10
I've had problems both times I tried to get these cards up (with Edgy). It turned out that there was a button that needed to be pressed. A hardware button that is. Don't ask me how I managed to overlook this twice...
After the button is pressed, everything worked.

- Ketil

EDIT: If you want to use network-manager, /etc/network/interfaces should look like this:
auto lo
iface lo inet loopback

# iface eth0 inet dhcp

# auto eth1
# iface eth1 inet dhcp

# auto eth2
# iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp

---

### Post by Krolik on 2007-04-10
> **Rospo Zoppo said:**
> I have the same card and Feisty kernel and I managed to get it work. I have follow an Italian how-to and I hope you can find an English one.. If you can't I will write here the steps.. :D

Hi! Could you write it for me? :-) I can't find good how-to :(

---

### Post by SDE on 2007-04-10
thanks for the reply.  i do have my interfaces file configured like that.  i do have a hardware on/off switch for the wireless, but it is turned on.

what exactly relates eth1 to the driver?  the driver is definitely there, i just can't associate the hardware with it or something. =/

---

### Post by SDE on 2007-04-11
just wanted to post an update.  i installed server version, and was booting up in server.

booting up with the generic kernel (3rd bootup option) allowed it to work great... i want my 15 hours back lol.

---

