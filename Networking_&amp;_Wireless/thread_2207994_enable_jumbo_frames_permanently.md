---
title: "enable jumbo frames permanently"
date: 2014-02-26
forum: Networking &amp; Wireless
---

### Post by prkhr4u on 2014-02-26
I want to enable jumbo frames permanently.
Temporarily i am using:
```
sudo ifconfig eth0 mtu 8192
```
and everything is working fine,I have tested it.
But when i reboot,again the mtu size is reset to 1500.

I tried this to permanently set it :
```
sudo gedit /etc/network/interfaces
```
and added the last 6 lines:

//interfaces file
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.11
network 192.168.0.0
gateway 192.168.0.255
netmask 255.255.255.0
mtu 8192

then I restart networking like this:
```
sudo /etc/init.d/networking restart
```

and reboot my system.
But now I am unable to connect to my network,says "wired network is unmanaged"

How to correctly enable jumbo frames permanently?

---

### Post by TheFu on 2014-02-26
I think that setting is the way, but only if every device on the LAN network is Jumbo capable and set in the same way.  Are all your devices GigE wired?

---

### Post by prkhr4u on 2014-02-26
yes,all my devices are GigE. I am directly connecting a GigE camera to my network card adaptor (which is 1000 Base-T) and is definitely GigE.
Anyways my network adapter is Intel 82579LM.

---

### Post by TheFu on 2014-02-27
> **prkhr4u said:**
> yes,all my devices are GigE. I am directly connecting a GigE camera to my network card adaptor (which is 1000 Base-T) and is definitely GigE.
Anyways my network adapter is Intel 82579LM.

Not going through a switch?  Are you using a special network cable?
Since yesterday, I've enabled jumbo frames on my network too.  Discovered that 1 of my GigE NICs does NOT support jumbo frames - it is a dell CAD workstation.  I'll be swapping in an Intel PRO/1000 NIC this weekend during a maintenance period. It refused the 
```
ifconfig eth0 mtu 2000
``` ----- or any higher number than 1500 with an error.  Physical machines here are mainly VM servers with bridged networking.  Learned I had to set the MTU on the real NIC device, not the bridge device for this stuff to work. 5 devices, 4 working with jumbo frames.  Added the mtu setting to my Ansible scripts (interface file) so all machines will get the same 9014 jumbo frame size.
I also discovered that 1 machine with GigE capability was connected using an old patch cord - CAT5, so no GigE speeds. Swapped that out and seeing 70+ Mbps file transfers as expected.

My switches are GigE, unmanaged too.

So - really just sharing that it does work here where it should. Anything interesting in the system logs?

---

### Post by prkhr4u on 2014-02-28
I am currently testing it directly and using Cat6 cable only.
I have checked everything, my NIC supports jumbo frames, linux kernel supports jumbo frames, camera supports and also recommends jumbo frames as well as the ethernet driver also supports jumbo frames.
I have checked it and they are working temporarily.
But the setting resets as soon as i reboot.Any other setting file where I can permanently set the mtu size??
nothing unusual in logs also.

---

### Post by TheFu on 2014-02-28
I'm stumped.  You could always use the post-up stanza inside the interfaces files to run the **ifconfig DEV mtu 9014** command, but that shouldn't be needed. I haven't needed it here on any of the machines tested so far.

Have you actually validated that the connections are auto-neg to 1000 base-tx?  If the connections aren't GigE, then jumbo frames can't be used. I know, I know, but I have to ask.

---

### Post by prkhr4u on 2014-03-10
I have changed my configuration now.I am using a switch instead of direct connection,but same problem is happening.
Temporarily it is working using 
```
ifconfig eth0 mtu 8192
```
but unable to set it permanently

and yes,I have checked the connection also and manually set it to GigE and now connected at 1000Mb/s.

I am trying it like this:
[COLOR=#000000]//interfaces file[/COLOR]
[COLOR=#000000]auto lo[/COLOR]
[COLOR=#000000]iface lo inet loopback[/COLOR]

[COLOR=#000000]iface eth0 inet static[/COLOR]
[COLOR=#000000]address 192.168.1.11[/COLOR]
[COLOR=#000000]network 192.168.1.0[/COLOR]
[COLOR=#000000]gateway 192.168.1.1  (switch port IP)[/COLOR]
[COLOR=#000000]netmask 255.255.255.0[/COLOR]
[COLOR=#000000]mtu 8192


[/COLOR]

---

### Post by TheFu on 2014-03-11
How smart is that switch? None of mine at home are "managed", so they do not have any IP addresses.

Did you try using the post-up option inside the interfaces file?

After testing 9K jumbo frames on my network for a week, I found that NTP stopped working and put everything back. Having correct time on all the systems is much more important to me. The performance using 9K frames actually was worse too.

---

### Post by Hadaka on 2014-03-11
[http://docs.oracle.com/cd/E19254-01/820-7895-11/cehiijbb.html#scrolltoc](http://docs.oracle.com/cd/E19254-01/820-7895-11/cehiijbb.html#scrolltoc)
it may need the full ip address

---

