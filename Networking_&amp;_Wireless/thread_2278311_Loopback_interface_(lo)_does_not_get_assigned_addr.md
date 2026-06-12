---
title: "Loopback interface (lo) does not get assigned address on boot"
date: 2015-05-15
forum: Networking &amp; Wireless
---

### Post by Philip_Gladstone on 2015-05-15
I'm running 14.04 on a web server and the system rebooted. After reboot, the web site failed to come up. On investigation, the root cause was that the 'lo' interface had not been assigned 127.0.0.1 as an IP address. This meant that mysql (maria) failed to start, and then it was downhill from there.

Immediately after boot:

```
philip@charlie:~$ ifconfig lo
lo        Link encap:Local Loopback  
          LOOPBACK  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


Further investigation revealed that /etc/network/interfaces looked good:

```
# Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.
# The loopback network interface
auto lo
iface lo inet loopback


# Label public
auto eth0
iface eth0 inet static
    address xx.xx.150.150
    netmask 255.255.255.0
    gateway xx.xx.150.1


```

ifdown and ifup would not assign the address:

```
philip@charlie:~$ sudo ifup -v lo
Configuring interface lo=lo (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
run-parts: executing /etc/network/if-up.d/postfix
run-parts: executing /etc/network/if-up.d/upstart
Configuring interface lo=lo (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
run-parts: executing /etc/network/if-up.d/postfix
run-parts: executing /etc/network/if-up.d/upstart

```

It tries to bring up 'lo' twice -- once from /etc/network/interfaces and once due to /var/run/network/dynamic-interfaces

I do note that on my 12.02 system, that the commands:

sudo ifconfig lo 127.0.0.2
sudo ifdown lo
sudo ifup lo

somewhat surprisingly leave the address on 'lo' set to 127.0.0.2

My question is:

**** Where (in which script) is the 127.0.0.1 address supposed to be set on the 'lo' interface?

Thanks

---

### Post by nil2 on 2015-06-04
Hello,

I have the same problem here. Noticed it when SSH X11 forwarding stopped working from newly updated 14.04 Xubuntu. I have a bunch of identical computers running cloned systems. Most of them have not received updates for a few weeks, except for two of them that I have updated (apt-get dist-upgrade) yesterday.

Now, those two can't forward X11 through SSH anymore, and they appear not to have an IP address assigned to the lo interface. I don't understand what's going on here. Network Manager is not installed and both /etc/network/interfaces and /etc/hosts seem to be intact (same as they are on working, not updated systems).

On a working system, I get (eth0 identical and not displayed):

```
root@pc01:~# ifconfig -a
lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          Packets reçus:5212221 erreurs:0 :0 overruns:0 frame:0
          TX packets:5212221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:320755284 (320.7 MB) Octets transmis:320755284 (320.7 MB)

```

On the newly updated systems:
```
root@pg06:~# ifconfig -a
lo        Link encap:Boucle locale  
          LOOPBACK  MTU:65536  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

```

So it seems loopback fails to start, and I'm trying to figure this out.

I'd be thankful for any clues.

---

