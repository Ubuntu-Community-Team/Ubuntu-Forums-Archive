---
title: "Route not being set properly"
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by Geryon on 2006-12-24
When I boot the system up or restart networking the system fails to set the default gateway.  My configuration looks like this:

```

[FONT="Courier New"]$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.5.1
netmask 255.255.255.0

auto wlan0
iface wlan0 inet static
wireless-essid bucky
address 192.168.1.5
netmask 255.255.255.0
gateway 192.169.1.1[/FONT]

```

As you can see the default gateway is bound to the wlan0 interface.  My routing table looks like this:

```

[FONT="Courier New"]$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.5.0     *               255.255.255.0   U     0      0        0 eth0
192.168.229.0   *               255.255.255.0   U     0      0        0 vmnet1
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
172.16.122.0    *               255.255.255.0   U     0      0        0 vmnet8[/FONT]

```

So what I have to do is call '[FONT="Courier New"]route add default gw 192.168.1.1 wlan0[/FONT]' by hand or via a quick script I wrote.  If I bring up the interfaces configuration via the GUI tool it shows everything in there properly as well.  

I haven't tried debugging this any further than what is above.  I am running 6.10, which was upgraded from 6.06.  I had the problem with 6.06 as well.

---

### Post by Geryon on 2006-12-27
Does anyone have any ideas at all?  

My wired eth0 device also shows up in the GUI as 'not configured' on the taskbar, while it's working fine and the configuration is displayed in the GUI configurator.  I also have a firewall running with ip masquerading between wlan0 and eth0 to convert my wireless network to wired and that runs seamlessly.

---

### Post by MrHorus on 2006-12-27
> **Geryon said:**
> Does anyone have any ideas at all?  


Your router is likely misconfigured.

```
gateway 192.169.1.1
```

That's an incredably odd looking IP to have as a default gateway.

Is it possible that you typed 169 rather than 168 into a dialog box somewhere?

Whatever happened, changing that octet SHOULD resolve your problems as right now the gateway is set to an IP that the routeing table has no knowledge of how to reach.

---

### Post by Geryon on 2006-12-28
Sheesh... How did I over look something like that???  It was a typo when I was configuring the network.  Heh, always helps to have a second pair of eyes.  

I changed it in my configuration.  I am remote from the machine though, so I hesitate on restarting networking until I get to it later today.  Hopefully that did the trick.  

I do find it odd that even though I have my default gateway set to the wrong IP that it does not set it at all.  We'll see if it works tonight though.

Thanks!

---

