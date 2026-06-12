---
title: "ssh connection - use client data/services from server"
date: 2016-07-07
forum: Networking &amp; Wireless
---

### Post by marchello_lippi2 on 2016-07-07
Hi all, 

My question can be obvious to many of you, but I would still ask it. 

I connect from my home or work pc to vps using ssh. 

Is it possible somehow to use data of connected pc from my vps? 

Like when I do ls on server, can I do ls from server on connected pc ?

Again, sorry if it is obvious or even stupid question. 

Thanks ahead.

---

### Post by papibe on 2016-07-07
Hi marchello_lippi2.

Not sure what you want to do.

Do you want to broadcast your commands to machines at a time?

Do you want to use the VPS to connect from work to home?

Do you want to upload/download data from work/home to the VPS?

Regards.

---

### Post by marchello_lippi2 on 2016-07-08
>>> [COLOR=#000000]Do you want to use the VPS to connect from work to home?

That's it, thanks for good shot. 
How do I perform it?[/COLOR]

---

### Post by papibe on 2016-07-08
There are several ways to do this.

Strictly, you don't really need a VPS. You can do it only forwarding ports on your home's router. Nevertheless, a VPS would allow you to avoid opening ports, so in my assessment it would be more secure.

The easiest way I can think of is to use [Tinc VPN]("https://www.tinc-vpn.org/"). It is already on the repos and it very easy to setup. Basically, work and home PCs call and connect to the VPS. After that, you can connect to any of the other 2 machines using a private address.

Here a tutorial on how to set it up: [Tinc basic setup]("https://groups.google.com/forum/#!topic/homefrontrouter/ayeyqauN1ao"). For the second PC, repeat the steps as described on the 'Client side'. Be sure to select a private network segment that is different from both your work and home LANs.

You may need to let the IT people at work what you are doing. Depending on the company, it may be not allowed, or they just going to make sure you are just connecting home.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by marchello_lippi2 on 2016-07-11
> **papibe said:**
> There are several ways to do this.

Strictly, you don't really need a VPS. You can do it only forwarding ports on your home's router. Nevertheless, a VPS would allow you to avoid opening ports, so in my assessment it would be more secure.

The easiest way I can think of is to use [Tinc VPN]("https://www.tinc-vpn.org/"). It is already on the repos and it very easy to setup. Basically, work and home PCs call and connect to the VPS. After that, you can connect to any of the other 2 machines using a private address.

Here a tutorial on how to set it up: [Tinc basic setup]("https://groups.google.com/forum/#!topic/homefrontrouter/ayeyqauN1ao"). For the second PC, repeat the steps as described on the 'Client side'. Be sure to select a private network segment that is different from both your work and home LANs.

You may need to let the IT people at work what you are doing. Depending on the company, it may be not allowed, or they just going to make sure you are just connecting home.

Hope it helps. Let us know how it goes.
Regards.


Any idea what can cause below error? 

```
$ sudo tincd -n hfvpn001 -D -d5
tincd 1.0.23 (Dec  5 2013 17:17:09) starting, debug level 5
Name for tinc daemon required!
Terminating
```

---

### Post by papibe on 2016-07-13
```
$ sudo tincd -n hfvpn001 -D -d5
tincd 1.0.23 (Dec  5 2013 17:17:09) starting, debug level 5
Name for tinc daemon required!
Terminating
```
It looks like you are missing the field 'Name' on your /etc/tinc/hfvpn001/tinc.conf

Hope it helps. Let us know how it goes.
Regards.

---

### Post by marchello_lippi2 on 2016-07-14
Ok, that one error message is solved now. 

The error message is different this time: 

> 
$ sudo tincd -n hfvpn001 -D -d5
tincd 1.0.23 (Dec  5 2013 17:17:09) starting, debug level 5                                                                                                                                                                                         
Could not open /dev/net/tun: No such file or directory                                                                                                                                                                                              
Terminating


Created mentioned directory: 

> 
$ sudo mkdir /dev/net
$ sudo mknod /dev/net/tun c 10 200
$ sudo chmod 600 /dev/net/tun


Run again: 

> 
$ sudo tincd -n hfvpn001 -D -d5                                                                                                                                                                                                
tincd 1.0.23 (Dec  5 2013 17:17:09) starting, debug level 5                                                                                                                                                                                         
Could not open /dev/net/tun: Operation not permitted                                                                                                                                                                                                
Terminating


As far as I can understand, **tun** is not available on my vps. 
Any workaround possible here?

---

### Post by papibe on 2016-07-21
Check the logs to see if your kernel have tun/tap support:
```
grep /var/log/tun kern.log; zgrep tun /var/log/kern.log.*
```
You should get something like this:
```
Jul 21 13:17:50 vanhalen kernel: [    1.311326] tun: Universal TUN/TAP device driver, 1.6
Jul 21 13:17:50 vanhalen kernel: [    1.311327] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
```
Some VPS based on OpenVZ do not support tun/tap devices by default. You may need to do some extra steps. Check [here]("http://crybit.com/how-to-enablecheck-tuntap-module-in-vpsopenvz/") and [here]("https://openvz.org/VPN_via_the_TUN/TAP_device").

Hope it helps. Let us know how it goes.
Regards.

---

