---
title: "editing files to change ip to static  is not working!"
date: 2015-04-21
forum: Networking &amp; Wireless
---

### Post by Mashvv on 2015-04-21
I have been looking into this for a while now and i realized that i should change my "/etc/network/interfaces" file and give it some info to be able to change to a static IP. HOWEVER! here is my what is in that file

         ```
# interfaces(5) file used by ifup(8) and ifdown(8)
    auto lo
    iface lo inet loopback
```

HOWEVER again, if i use gksudo nm-connection-editor, and change information manually there, it seems to do the right thing and change my ip. I tried editing the file myself but nothing worked... keep in mind im on wlan0 any ideas? Also, i was wonding how can i check which files  gksudo nm-connection-editor EDITS so maybe i can edit and make this work.

---

### Post by steeldriver on 2015-04-21
Network Manager doesn't use the /etc/network/interfaces file - it has its own files in /etc/NetworkManager

In particular, system-wide connection information is in /etc/NetworkManager/system-connections/ with one file for each connection that you have defined via the GUI applet

I'm not sure I'd recommend editing them by hand though - what exactly are you trying to achieve?

---

### Post by matt_symes on 2015-04-21
Hi

> **Mashvv said:**
> I have been looking into this for a while now and i realized that i should change my "/etc/network/interfaces" file and give it some info to be able to change to a static IP. HOWEVER! here is my what is in that file

         ```
# interfaces(5) file used by ifup(8) and ifdown(8)
    auto lo
    iface lo inet loopback
```

HOWEVER again, if i use gksudo nm-connection-editor, and change information manually there, it seems to do the right thing and change my ip. I tried editing the file myself but nothing worked... keep in mind im on wlan0 any ideas? Also, i was wonding how can i check which files  gksudo nm-connection-editor EDITS so maybe i can edit and make this work.

Your post is unclear and sounds like it may be an X-Y problem.

Firstly, you are trying to give yourself a static IP address for your wireless interface ?

It works when you enter a static IP address for the wireless interface using nm-connection-editor using network manager ?

You want to use the interfaces file instead to give yourself a static IP address ?

So questions:

why is setting a static IP address using nm-connection-editor (network manager) not a suitable solution for giving yourself a static IP address ?

Why do you feel you need to use the /etc/network/interfaces file to give yourself a static IP address and not network manager using nm-connection-editor ?

Why do you want to edit the network manager (files edited by nm-connection-editor) files directly when nm-connection-editor provides a GUI to allow you to do this easily ?

Can you tell us exactly what you are trying to do and why you need a static IP address in the first place.

Also please correct any and all my incorrect assumptions above.

Kind regards

---

### Post by Mashvv on 2015-04-21
Well I simply don't mind the GUI, but i would live to learn the stuff behind it(gives a soild knowledge). 
Gui works fine, yet following some tutorials online, which say that i must edit the /etc/network/interfaces but nothing seems to change when i do.
And yes, i am trying to give myself a static ip (In other words change my host identifier). Keep in mind please that im on a laptop and my ultimate goal is to also change my subnet prefix in which i stay on the same network However i want to switch from X.X.X.X  to X.X.Y.X
and yes i realise that this is not the same as changing static ip, that is changing subnet but they are both the same cause you do the same editing in the same files.

---

### Post by Mashvv on 2015-04-21
i am trying to give myself a static ip (In other words change  my host  identifier FROM x.x.x.X to x.x.x.Y ). Keep in mind please that im on a  laptop and my  ultimate goal is to also change my subnet prefix in which  i stay on the  same network However i want to switch from x.x.X.x  to  x.x.Y.x other than changing the host-identifier
and  yes i realise that this is not the same as changing static ip, that  is  changing subnet but they are both the same cause you do the same  editing  in the same files.

---

### Post by matt_symes on 2015-04-21
Hi

> **Mashvv said:**
> Well I simply don't mind the GUI, but i would live to learn the stuff behind it(gives a soild knowledge). 

Right. That clears up your first post a bit.

> Gui works fine, yet following some tutorials online, which say that i must edit the /etc/network/interfaces but nothing seems to change when i do.

First things i would say is to be careful of online tutorials. It's not that they may necessarily be wrong but they may be out of date or inapplicable to the situation or problem you are trying to solve.

There are a number of ways to control networking on Linux. On an installation that has a desktop most people find it convenient to use GUI (graphical user interface) program such as "network manager" or WICD.

On server, where there is (usually) no desktop, a system such as the interfaces file is usually used.

Theses systems automate the raising of interfaces such as an Ethernet or wireless card and the assignment of ip addresses, subnets, gateways, routes etc on the raised interfaces either by setting static addresses or using DHCP from a DHCP server on a router or other computer. They can also automate the connection of Wireless interfaces to router access points.

These interfaces can also be raised manually, addresses and routes assigned manually, wireless cards associated with access point manually, by using commands such as ifup, ifconfig, iwconfig, wpa_supplicant and/or if depending on what you are doing.

The configuration setting for network manager are stored under the location

```
/etc/NetworkManager/
```

If network manager is managing all the interfaces then any entries in the interfaces file in /etc/network/interfaces will be ignored.

This is set in the file /etc/NetworkManager/NetworkManager.conf.

Here's mine

```
matthew-laptop:/home/matthew:1 % cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false
matthew-laptop:/home/matthew:1 %
```

If managed is set to true above then all entries in the interfaces file will be ignored. As you can see, mine is set to false.

When managed=false in the above file, any entries in the file /etc/network/interfaces will not be managed by network manager and will take the value stated in the interfaces file when they are brought up.

Below is a valid entry for an interface file for interface eth0. It assigns a static ip address.

```
 auto eth0
 iface eth0 inet static
 address     192.168.0.100
 netmask     255.255.255.0
 network     192.168.0.0
 gateway     192.168.0.1
 broadcast   192.168.0.255
 dns-search  my-home.com
```

And i can use that interfaces file like such.

```

matthew-laptop:/home/matthew:1 % cat /etc/network/interfaces    
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

 auto eth2
 iface eth2 inet static
 address     192.168.0.100
 netmask     255.255.255.0
 network     192.168.0.0
 gateway     192.168.0.1
 broadcast   192.168.0.255
 dns-search  my-home.com

matthew-laptop:/home/matthew:1 % ifconfig | pbl eth2        
eth2      Link encap:Ethernet  HWaddr 00:45:52:2c:ad:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

matthew-laptop:/home/matthew:1 % sudo ifup eth2
RTNETLINK answers: File exists
Failed to bring up eth2.
matthew-laptop:/home/matthew:1 % ifconfig | pbl eth2
eth2      Link encap:Ethernet  HWaddr 00:45:52:2c:ad:f0  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

matthew-laptop:/home/matthew:1 % 
```

This is while my wireless card (wlan3) is being managed by network manager and is getting an ip address etc using DHCP.

```
matthew-laptop:/home/matthew:1 % ifconfig | pbl wlan3
wlan3     Link encap:Ethernet  HWaddr 00:18:ff:a1:29:dd  
          inet addr:10.55.7.18  Bcast:10.55.7.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fea1:29d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6093344 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3155884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8182124443 (8.1 GB)  TX bytes:343491490 (343.4 MB)

matthew-laptop:/home/matthew:1 %
```

I hope the above makes a bit of sense and if any of it is wrong then hopefully someone will correct it.

> And yes, i am trying to give myself a static ip (In other words change my host identifier). Keep in mind please that im on a laptop and my ultimate goal is to also change my subnet prefix in which i stay on the same network However i want to switch from X.X.X.X to X.X.Y.X
and yes i realise that this is not the same as changing static ip, that is changing subnet but they are both the same cause you do the same editing in the same files.

You're trying to change subnets ?

Kind regards

---

### Post by chili555 on 2015-04-21
Does this help? [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552)

---

### Post by Mashvv on 2015-04-22
It actually explains alot Thank you very much!

---

