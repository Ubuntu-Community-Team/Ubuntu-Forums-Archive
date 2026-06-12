---
title: "Cannot ping localhost.  eth0 and eth1 ok"
date: 2005-11-14
forum: Networking &amp; Wireless
---

### Post by darreld on 2005-11-14
I am unable to ping localhost on Kubuntu Breezy which leads to some problems on the machine.  I can connect via both eth0 and eth1 and have even configured and connected to work via  vpnc but since I can't get to localhost I can't set up a printer (for example).  Here's
what I see from ifconfig.

lo        Link encap:Local Loopback
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:176 errors:0 dropped:0 overruns:0 frame:0
           TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:46321 (45.2 KiB)  TX bytes:46321 (45.2 KiB)

/etc/hosts refers to the box as:
127.0.0.1       copernicus localhost.localdomain        localhost

Is this an ipv6 issue?  If so, how do I disable ipv6 system-wide?
Any help appreciated.

TIA,
-darrel

---

### Post by rkelly on 2005-11-14
Looks like something is missing in your network setup.

This is how my settings for localhost look in ifconfig:
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:435275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:435275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:40031421 (38.1 MiB)  TX bytes:40031421 (38.1 MiB)

``` 
Check the contents of the file /etc/network/interfaces. Apart from the parameters for your other interfaces, it should contain the following:
```
# The loopback network interface
auto lo
iface lo inet loopback

``` If that is missing then add it and restart your network.

---

### Post by rkelly on 2005-11-14
B.T.W. Something I did not notice earlier:

[quote=darreld]
/etc/hosts refers to the box as:
127.0.0.1       copernicus localhost.localdomain        localhost
[/quote]

Try putting copernicus on the end of that line, that could help.
I have never had that as first hostname on that line.

---

### Post by TomtheWombat on 2005-11-21
```
lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4085780 (3.8 MiB)  TX bytes:4085780 (3.8 MiB)
```

I am having the exact same problems.  :(

It seems the computer is not setting up the networking properly when it reboots.

```
sudo ifconfig lo 127.0.0.1
```
This will fix it, but only until the next reboot?  Yeah, I can throw that into a startup script, but I'm looking for the *real* answer.

Anymore suggestions?

---

