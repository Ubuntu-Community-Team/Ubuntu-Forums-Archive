---
title: "quick question - how to find ip of ubuntu server"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by floatingpoint on 2010-10-20
hello,

how do i find the IP of my ubuntu server box? I ran ifconfig and it gave me a value for inet addr  but i'm pretty sure that's the address it has on my home network. how can I find out what the IP address to access it from elsewhere is?

there's no GUI btw.

Cheers!

---

### Post by alphacrucis2 on 2010-10-20
> **floatingpoint said:**
> hello,

how do i find the IP of my ubuntu server box? I ran ifconfig and it gave me a value for inet addr  but i'm pretty sure that's the address it has on my home network. how can I find out what the IP address to access it from elsewhere is?

there's no GUI btw.

Cheers!

The public address is usually the address assigned by your ISP to your router. Unless you have made arrangements with your ISP, the public address may change. One way to find out what it is currently set to, is browse to a web site such as:

[http://whatismyipaddress.com/]("http://whatismyipaddress.com/")

That web site will tell you your source ip address. All of the devices on your home network will be using this as the public address. If you want to do port forwarding from the internet to your server, you may find [dyndns]("http://www.dyndns.com/") useful.

---

### Post by bathacid on 2010-10-21
you can view this page above by cli web browsers like lynx you can install this by doing "sudo apt-get install lynx"

---

