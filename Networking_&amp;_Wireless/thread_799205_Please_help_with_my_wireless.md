---
title: "Please help with my wireless"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by wleejppromo on 2008-05-18
Hi, 

I just recently downloaded ubuntu onto my laptop, and I tried to connect to a wireless network. I have no idea what I'm doing, and I can't figure out what's wrong, because I still can't connect to the internet. I have a gateway Model No: W323-Ul1. Any help would be greatly appreciated!

---

### Post by buccaneere on 2008-05-19
> **wleejppromo said:**
> Hi, 

I just recently downloaded ubuntu onto my laptop, and I tried to connect to a wireless network. I have no idea what I'm doing, and I can't figure out what's wrong, because I still can't connect to the internet. I have a gateway Model No: W323-Ul1. Any help would be greatly appreciated!


Can you connect with ethernet (hardwire) connection? This will make it a little quicker...

Is your wireless card detected?

Open a terminal and type:
> lspci


Here's some basic diagnostics that I've had to do for all 5 of my machines:

1. Verify that your network device ("wlan0"?) is working & your wireless network is detected:

> iwconfig

> iwlist scan

2. Open "/etc/network/interfaces":

> sudo gedit /etc/network/interfaces
The content should look similar to this:

> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

post back with results...

---

### Post by jonofan on 2008-05-20
Hi there, I'm having simliar problems.

My PCI wireless card is detected and my home wireless is listed.

> sudo gedit /etc/network/interfaces

gives me:
> 
auto lo
iface eht0 inet dhcp

auto eth0

Ethernet connection works fine also.

---

### Post by buccaneere on 2008-05-21
> **jonofan said:**
> Hi there, I'm having simliar problems.

My PCI wireless card is detected and my home wireless is listed.



gives me:


Ethernet connection works fine also.

What return do you get for > lspci ? 
This will tell you if your wireless card is a PCI device. 

And also return for 

> iwconfig(network interfaces), and > iwlist scan (wireless signals detected by your machine)  ?

---

