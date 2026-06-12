---
title: "[SOLVED] &amp;quot;add route&amp;quot; not working in Feisty"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by be4truth on 2007-07-02
I am trying to add a route in Feisty but no success so far:
I tried copying 'up route add -net 10.0.2.0 netmask 255.255.0.0 gw 192.168.3.5 dev eth0' into
sudo vi /etc/network/interfaces
and restarted the network service - no success
I rebooted - no success
'route -n' gives this result:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.3.1     0.0.0.0         UG    0      0        0 eth0

'netstat -nr' gives:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.3.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.3.1     0.0.0.0         UG        0 0          0 eth0

my interface file is:
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.3.214
netmask 255.255.255.0
gateway 192.168.3.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

up route add -net 10.0.2.0 netmask 255.255.0.0 gw 192.168.3.5 dev eth0


Any advise. All googleing says its a feisty forwarding problem but how to solve this?

Thx for any suggestion.

---

### Post by netztier on 2007-07-02
> **be4truth said:**
> 
my interface file is:
```
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.3.214
netmask 255.255.255.0
gateway 192.168.3.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

up route add -net 10.0.2.0 netmask 255.255.0.0 gw 192.168.3.5 dev eth0


```
Any advise. All googleing says its a feisty forwarding problem but how to solve this?

Thx for any suggestion.


The "up route... " line has to go here, together with the configuration block for eth0. Putting it at the end of the file would associate it with the last interface listed it the file - in your case wlan0.

```

[...]

auto eth0
iface eth0 inet static
 address 192.168.3.214
 netmask 255.255.255.0
 gateway 192.168.3.1
 [COLOR="DarkGreen"]**up route add -net 10.0.2.0 netmask 255.255.0.0 gw 192.168.3.5 dev eth0**[/COLOR]

[...]

```

Just a question about that destination and netmask combination - you are aware that like this, you are routing 10.0.*.* towards 192.168.3.5, are you? If that is your goal, you should better (read: to make the configuration more human-readable) configure it like this:

```
route add -net 10.0.0.0 netmask 255.255.0.0 gw 192.168.3.5 dev eth0
```

However, if routing 10.0.2.* towards 192.168.3.5 is desired, netmask should be 255.255.255.0 instead, and it should look like this:

```
route add -net 10.0.2.0 netmask 255.255.255.0 gw 192.168.3.5 dev eth0
```

best regards

Marc

---

### Post by be4truth on 2007-07-03
Thx for your help.
The line 'route add -net 10.0.2.0 netmask 255.255.255.0 gw 192.168.3.5 dev eth0' doesn't work but the line 'up route add -net 10.0.2.0 netmask 255.255.255.0 gw 192.168.3.5 dev eth0' fixes the problem. 
Thanks again for your help. I love community:KS

---

### Post by netztier on 2007-07-04
> **be4truth said:**
> Thx for your help.
The line 'route add -net 10.0.2.0 netmask 255.255.255.0 gw 192.168.3.5 dev eth0' doesn't work but the line 'up route add -net 10.0.2.0 netmask 255.255.255.0 gw 192.168.3.5 dev eth0' fixes the problem. 
Thanks again for your help. I love community:KS

Well yes of course. The "up" statement in **/etc/network/interfaces ** expects a "one-liner", a command that could be typed in a single line at a shell prompt. In the two examples I gave at the end of the post, i wrote the commands as you'd use them on a command line, and left the "up" prefix out, as it is not needed when manually entering the commands.

For more advanced configurations and things-to-happen-after-interface-up here, you could always call an external shell-script of your own, or use the if-up.d/ if-down.d / if-pre-up.d etc. subdirectories in **/etc/network/**

In the two examples I gave at the end of the post, i wrote the commands as you'd use them on a command line, and left the "up" prefix out, as it is not needed when manuall entering the commands.

Glad it worked, though :-)

best regards

Marc

---

