---
title: "Random Problem with my Network,"
date: 2005-07-12
forum: Networking &amp; Wireless
---

### Post by geearf on 2005-07-12
Hello,

i have one desktop connected to internet throught ethernet, one laptop connected to te desktop with firewire.

My network should be configured well : 
 more /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
broadcast 192.168.0.255

auto eth1
iface eth1 inet dhcp

eth0 is the firewire , and eth1 is the ethernet

lsmod | grep 1394
ohci1394               35828  0
eth1394                20552  0
ieee1394              105592  3 ohci1394,eth1394,sbp2

more /etc/network/options
ip_forward=yes
spoofprotect=yes
syncookies=no

more /etc/network/if-up.d/iptables-start
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

but in fact the network between the laptop and the desktop is not always working.

It always works if the laptop (under windows for the moment) is on before the desktop (under ubuntu).
If I start first the desktop it usually does not work, and i have to restart it (/etc/init.d/network restart does not help).

But yesterday night, I had the network connected, i unplugged the network, rebooted both computers, and hours later plug them back together, and all was good..

So i thought it was ok now, but again this morning i start the desktop, one hour later i start the laptop and no network between them (no ping, no smb, nothing ..).

I'm starting to think the problem comes from the windows on my laptop, but if use windows on my desktop, the network is always on ...

Thanks for any ideas,

---

### Post by geearf on 2005-07-12
again i had to reboot to put a file on my laptop :(

---

### Post by gruepig on 2005-07-12
You posted (I think) the configuration of your desktop.  Can you also post the configuration of your laptop?  Also, when you say you have no network between the two, what exactly do you mean?  Do you mean you can't ping the desktop from the laptop (nor the laptop from the desktop)?

---

### Post by geearf on 2005-07-13
Hello,

Yes i posted the configuration of the desktop, the laptop is running either Windows XP (most of the time) or Mepis.

Under XP my config is simple : 
192.168.0.2
255.255.255.0
gate way 192.168.0.1
and the dns.

(still for the eth1394 XP uses).

When I say no network, I really mean nothing : no ping in either way, no samba working, no internet on the laptop, ..

Thank you for taking the time to answer,

---

### Post by gruepig on 2005-07-13
Hmm ... everything looks okay to me. Are you using DHCP on the laptop in either XP or Mepis?  I'm guessing not, but if you are, I'd recommend assigning your IP manually (as sometimes Windows hangs onto the DHCP lease after shutdown, which means it can't be reassigned when you boot to Linux). Can your desktop ping itself (192.168.0.2) and similarly can the laptop ping itself?  Also, instead of (or in addition) to restarting networking, maybe just try bringing your network interfaces down and back up (e.g., 'ifdown eth0; ifup eth0').  I'm not sure what it would fix, but maybe there will be a useful error?  Or the problem may has something to do with firewire, rather than networking per se?  Can you send the output of 'ifconfig -a, route -n, and iptables -L (from the desktop)?  Maybe that will help, though I'm feeling rather stumped at the moment.

---

### Post by geearf on 2005-07-13
Hello,

i am not using DHCP for these no.
When there is no network, both computers can ping themselves, but never the other.

I already tried ifconfig down, and up, and also disabling the connection in windows and enabling it just after (but it was never both during the same session so i should try this too).

ifconfig -a
eth0      Lien encap:UNSPEC  HWaddr 00-02-3C-00-30-00-74-27-00-00-00-00-00-00-00-00
          inet adr:192.168.0.1  Bcast:192.168.0.255  Masque:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Lien encap:Ethernet  HWaddr 00:50:BA:C3:65:AD
          inet adr:82.67.150.X  Bcast:82.67.150.255  Masque:255.255.255.0
          adr inet6: fe80::250:baff:fec3:65ad/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1196876 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1633858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          RX bytes:588576476 (561.3 MiB)  TX bytes:1764947339 (1.6 GiB)
          Interruption:9 Adresse de base:0x9800

lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          RX bytes:665 (665.0 b)  TX bytes:665 (665.0 b)

sit0      Lien encap:IPv6-dans-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
82.67.150.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         82.67.150.Y   0.0.0.0         UG    0      0        0 eth1


sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Thanks for your help,

---

### Post by gruepig on 2005-07-13
That all looks fine to me. Anyone else have any ideas?

---

### Post by geearf on 2005-07-13
thanks for pumping the thread for me  :cool:

---

### Post by geearf on 2005-07-14
i tried putting them both down, then up, no changes :(

But dmesg shows me this : 
[4301637.709000] ieee1394: ether1394 rx: sender nodeid lookup failure: 0-01:1023


might be something, but i cannot find much on this from google.

---

### Post by geearf on 2005-07-15
Strange thing is that i've confirmed that the problem only occurs when the laptop is on windows, never when he is on MEPIS. 
So i could guess the problem comes from Windows, but once i reboot my desktop (on ubuntu) every thing works

Strange isn't it ?

And most strange is that for me it used to work last time I installed hoary (did not change anything on the laptop since to the best of my knowledge).

Thanks,

---

### Post by geearf on 2005-07-15
up

---

### Post by geearf on 2005-07-16
up in case anyone has the same problem / know something

---

### Post by geearf on 2005-07-18
up

---

### Post by geearf on 2005-07-20
up

---

### Post by geearf on 2005-08-07
Well I've just install Kubuntu on the laptop and now i don't have this sort of problem.

But my script at /etc/network/if-up.d/iptables-start does not start, I still need to do a : sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
(which I got from a more /etc/network/if-up.d/iptables-start)

ls -l /etc/network/if-up.d/iptables-start
-rwxr-xr-x  1 root root 53 2005-07-11 23:50 /etc/network/if-up.d/iptables-start

If you have any idea on this I'll be glad to hear them :)

---

### Post by geearf on 2005-08-07
Also, both computers can ping the other with their ip, but not with their name, one can ping himself with the name, what needs to be done on that ? thanks.

---

