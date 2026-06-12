---
title: "Need serious help, Girlfriend is gonna kill me!"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by Joey French on 2007-06-04
Hello all,
So, my Girlfriend's computer has Kubuntu Feisty 64 installed,working well. A big problem though, is that after the computer has been up for a while, it loses it's connection to the internet. This connection is shared by my computer as well (also running Kubuntu Feisty) through a Linksys router to cable modem. Okay, so I try to get it to restart the network using the networking restart command in the terminal, have fiddled with the Network Manager, changed the ip from static to DHCP, commented out the other interfaces (not used; all but eth0 and lo), even copied my config settings on my machine to hers trying to get it to stay up. I also removed avahi-autoipd, on the advice of another poster. Someone, please tell me what I should be looking for here. The Missus is gonna rip my head off if I don't get this fixed soon!

---

### Post by kevdog on 2007-06-04
Did you backup the /etc/network/interfaces file before messing around???

Please post the output of 
ifconfig

and your /etc/network/interfaces file.

I assume you are using your wireless card with dhcp (not a static ip address).  Also what is the essid or ssid of the router you are trying to connect with??

---

### Post by Joey French on 2007-06-04
```
evelyn@eviebox:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:92:6F:4E:AA
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe6f:4eaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27019 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:37688294 (35.9 MiB)  TX bytes:4384562 (4.1 MiB)
          Interrupt:23 Base address:0xf400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:204769 (199.9 KiB)  TX bytes:204769 (199.9 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.59.1  Bcast:192.168.59.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.208.1  Bcast:192.168.208.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

evelyn@eviebox:~$

```

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

> I assume you are using your wireless card with dhcp (not a static ip address). Also what is the essid or ssid of the router you are trying to connect with??
I am using a wired connection, not a wireless. 

Thanks a bunch for the help!

Joey French

---

### Post by kevdog on 2007-06-04
Something is very strange, you are trying assign a static ip address of 192.168.1.101, but eth0 is getting assigned an ip address of 192.168.1.102.  

Have a tried to use dhcp to see if this works:

auto eth0
iface eth0 inet dhcp

Just wondering if this works.

I'm kind of stumped with this one.  When I set up my card for a static connection, this is what my interfaces file appears as:
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 68.87.85.98 68.87.69.146 192.168.1.1

Could you also list your /etc/iftab file.

---

### Post by nike984 on 2007-06-04
after you change /etc/network/interfaces file,
just as [kevdog]("http://ubuntuforums.org/member.php?u=257393") told you,
Use 

```
sudo /etc/init.d/networking restart
```

to restart the network interface.

---

### Post by msandersen on 2007-06-05
If all else fails, change the Girlfriend interface to 0 :p

---

### Post by Joey French on 2007-06-05
Thanks, I will try this. I also noticed that it was assigning to 192.168.1.102. I changed it before to 192.168.1.101, and it reverted right back to 192.168.1.102. I will try to edit again, but this time, I will restart the network right after, and see what happens. Usually I can reboot and the network will come up, and stay up while in use, However, after it's up for a while (few hours, maybe) it will lose the connection. Even using 
```
sudo /etc/init.d/networking restart
```
will not bring it back up, it just tries over and over (Network Manager hangs at 62%). Can anyone look at the posted info and let me know that it at least is not hardware? As in, the router and integrated card (VIA) are functioning properly, so I can rule these out (the computer is less than a month old, this problem started on day one)?

Thanks,
Joey French

---

### Post by Lord Illidan on 2007-06-05
sudo apt-get remove  --purge girlfriend

---

### Post by kevdog on 2007-06-05
When it goes down, if you type
sudo ifconfig eth0 down  

(substitude eth0 for wlan0 or whatever the interface name is), then
sudo ifconfig eth0 up

does it work then???

If not, do the above and then try
sudo /etc/init.d/networking restart

Then does it work??

---

### Post by Joey French on 2007-06-05
Will try this afternoon when I get home, and report back. 

Thanks,
Joey

---

### Post by chili555 on 2007-06-05
Are you asking for x.101 but getting x.102 because another machine on the network already has x.101? I suggest setting the machine with an intermittant connection problem to DHCP, restart networking and then diagnose the intermittant problem.```
dmesg | grep eth0
sudo cat /var/log/messages | grep eth0
sudo ethtool eth0
```In ethtool, you just have to look for entries that look suspicious.

I also suggest substituting a known good CAT5 cable to see if anything changes.

---

### Post by Joey French on 2007-06-05
> Are you asking for x.101 but getting x.102 because another machine on the network already has x.101?

No, it just hops on x.102 on it's own. I will have another go at it this afternoon, but these two machines and one router are all that is on this network presently.

---

### Post by Joey French on 2007-06-06
So, I reset the router, checked the cables, set the ailing computer to dhcp, restarted the network, and everything came up okay. Then I shut down both computers and restarted the ailing one, and it grabbed x.100. I then restarted the other one (working fine, set to dhcp) and it grabbed x.101. The connection was still up this morning so we will see how it goes. I will report back and let you know if there are any problems. Thanks for the help.

Thanks!
Joey French

---

### Post by Kuoi on 2007-06-06
> **Lord Illidan said:**
> sudo apt-get remove  --purge girlfriend

This is a big community , and it seems we help each other in any way we can [-o<

Have tried the command  (replaced 'girlfriend' with 'wife' ) , but still no luck ;)
Just joking , I love my wife !!!!

Still hope everything works out fine for you Joey.

Kuoi

---

### Post by kuja on 2007-06-06
> **Joey French said:**
> So, I reset the router, checked the cables, set the ailing computer to dhcp, restarted the network, and everything came up okay. Then I shut down both computers and restarted the ailing one, and it grabbed x.100. I then restarted the other one (working fine, set to dhcp) and it grabbed x.101. The connection was still up this morning so we will see how it goes. I will report back and let you know if there are any problems. Thanks for the help.

Thanks!
Joey French

Sounds like it's acting awfully silly. Why not set it to something like oh, x.120 and see if it will behave then?

---

### Post by Joey French on 2007-06-06
Okay, will do that if it starts acting up again.

Joey

---

