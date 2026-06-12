---
title: "[SOLVED] problem with internet access (probably dns)"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by wedgy on 2008-11-29
I have a problem: I no longer can surf the internet on my ubuntu machine, although I still can access my router configuration by typing it's ip address in firefox. My network is made of a linksys router, a ubuntu pc and a windows pc. On the windows one I can access the internet.

Is it a problem with dns on ubuntu and how do I solve this?

---

### Post by J172 on 2008-11-29
try (in terminal)
**/etc/init.d/network restart**
if that doesn't work
**sudo /etc/init.d/network restart**
type your password, press enter.

if that doesn't work reboot the router, if that doesn't work check your IP configuration on your machine (ifconfig) to make sure everything is cool.. System -> Preferences-> Network Configuration to modify settings on a network interface. Click your interface, then edit. Go to IPv4 Config, and make sure its set to DHCP (if you use DHCP, if you don't know what it is, you do) it may be shown as DHCP (Automatic).

---

### Post by wedgy on 2008-11-29
The output of sudo /etc/init.d/networking restart (the /etc/init.d/network didn't work)
```
 * Reconfiguring network interfaces...                                  [ OK ] 

d0minik@d0minik-desktop:~$  * Stopping NTP server ntpd

   ...done.

 * Starting NTP server ntpd

   ...done.
```

When I try to use the network configuration tool, there is a connection Ifupdown eth0, which I cannot edit.
Also, when I try to run nm-applet , it shows:
```
** (nm-applet:11871): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3 
 
 
(nm-applet:11871): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
```

The output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:16:17:4d:80:24  
          inet addr:192.168.1.63  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::216:17ff:fe4d:8024/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:301 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:275 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:71582 (71.5 KB)  TX bytes:39292 (39.2 KB) 
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:506 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:506 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:34684 (34.6 KB)  TX bytes:34684 (34.6 KB) 

```
Restarting the router didn't work. 

The whole thing started after I connected my mobile phone using a cable, a popup telling about connecting using the phone showed up. I think it overwrote something :|

---

### Post by J172 on 2008-11-29
It might have. Can you access the internet? Your IP Configuration looks fine, and I have no clue what nm-applet is smoking. Not sure what the error is trying to say.. maybe that it can't get access to the user settings? (It seems to say that). Does anyone know about the nm-applet? Try connecting your computer to the cable modem directly (or DSLAM if you have DSL)

---

### Post by J172 on 2008-11-29
Perhaps it did. I'm not sure what is going on with nm-applet. Try directly connecting your desktop to the Cable Modem or DSLAM if you have DSL. The ipconfig looks perfect. Not sure what is going on. Does someone know about nm-applet. Have you tried a restart? Can you access the internet through the router?

Sorry for the doubt post, my browser was giving me a 502 from the server.

---

### Post by albandy on 2008-11-29
Check if your default gateway is correct, you should see something like this typing route -n in the console:

Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
192.168.50.0    0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.51.0    0.0.0.0         255.255.255.0   U     0      0        0 tap0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
**0.0.0.0         192.168.50.1    0.0.0.0         UG    0      0        0 wlan0**

You should have an entry 0.0.0.0 192.168.1.1 0.0.0.0
if not you have not defined your default gw.

Then check /etc/resolv.conf
you must have entries like these
search anyword.anyextension
nameserver ip1
nameserver ip2

if not, configure your DNS

---

### Post by wedgy on 2008-11-29
It seems that's everything alright in the routing table:
```
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0 
```

When I opened /etc/resolv.conf it was blank. I added nameserver and IP of my router, and WOOHOO, it works (for now at least) :guitar: Thanks a bunch :)

---

