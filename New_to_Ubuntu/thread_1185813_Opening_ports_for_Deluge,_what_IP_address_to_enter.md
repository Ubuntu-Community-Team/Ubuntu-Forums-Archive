---
title: "Opening ports for Deluge, what IP address to enter?"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by SlingerXL on 2009-06-12
So I'm running 9.04 and I know how to get to my NetGear router's port forwarding settings place but what I don't know is what to enter for the IP address when I try and set up the port. There are 5 people who use my router if that matters.

I've tried 192.168.1.1 and 192.168.1.9 and 192.168.1.100 etc but when I go to a port testing site I have never once had the ports I forwarded work. So what IP address am I supposed to put in there?

---

### Post by markharding557 on 2009-06-12
you don't need any ip address unless using a proxy just a port number.
configure deludge to use a single port not random ones and open this port in your router.
the port must be for your computer on the local network not one of the others

---

### Post by nandemonai on 2009-06-12
> **SlingerXL said:**
> So I'm running 9.04 and I know how to get to my NetGear router's port forwarding settings place but what I don't know is what to enter for the IP address when I try and set up the port. There are 5 people who use my router if that matters.

I've tried 192.168.1.1 and 192.168.1.9 and 192.168.1.100 etc but when I go to a port testing site I have never once had the ports I forwarded work. So what IP address am I supposed to put in there?

You need to put the IP of the machine you're trying to torrent on. If said computer is using DHCP then you may want to set a static IP on that machine to make your life easier.

---

### Post by SlingerXL on 2009-06-12
But if I don't put anything in the Server IP Address box it won't let me apply any changes. So what do I put in the server IP address and how do I know what IP is my computer's and not anyone else's?

---

### Post by SlingerXL on 2009-06-12
> **nandemonai said:**
> You need to put the IP of the machine you're trying to torrent on. If said computer is using DHCP then you may want to set a static IP on that machine to make your life easier.

OK, I'll try a static IP. Thanks.

---

### Post by superprash2003 on 2009-06-13
[https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)

---

