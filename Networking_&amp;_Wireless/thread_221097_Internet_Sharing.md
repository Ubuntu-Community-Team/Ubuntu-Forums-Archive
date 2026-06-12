---
title: "Internet Sharing"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by aglc2005 on 2006-07-22
I am running a wireless connection in my house, the desktop that I recently acquired has no wireless card but does have an ethernet port. So I decided to share my wireless connection on my laptop with the desktop, so I install Firestarter and chose to share the connection over eth0 (my laptops ethernet port) and my wireless is ath0. When I attempt to start Firestarter is says 

> Firestarter failed to start because the device eth0 is not ready

Now the device is active under the network settings and my cable is connected, so does anyone know how to resolve this problem?](*,)

---

### Post by teet on 2006-07-22
You'll need a crossover cable to be able to communicate between your laptop and desktop :)  That may be your problem.

[http://en.wikipedia.org/wiki/Crossover_cable](http://en.wikipedia.org/wiki/Crossover_cable)

-teet

---

### Post by bigken on 2006-07-22
i take you  have a adsl wireless router so just hook the router and new box via a cat45 cable and still use your wireless on the laptop ?

or am I missing something :-k

---

### Post by Matchless on 2006-07-22
Hi,
   I may have misunderstood your situation, but firestarter must be installed on the PC that connects to the internet and must be actually connected before you can setup.

---

### Post by aglc2005 on 2006-07-23
> **bigken said:**
> i take you  have a adsl wireless router so just hook the router and new box via a cat45 cable and still use your wireless on the laptop ?

or am I missing something :-k

The desktop and laptop are in my room on the second floor of my house and my wireless router is in the basement. I was hopinh to not have to buy a wireless card for the desktop and running a cable would cost more than the card, so I was going to use my laptop as a host for the desktop seeing how my laptop is always on.

> **Matchless said:**
> Hi,
   I may have misunderstood your situation, but firestarter must be installed on the PC that connects to the internet and must be actually connected before you can setup.
It is installed on the pc that connects to the internet (my laptop) and will start unless I turn on the sharing portion of firestarter, then it gives me that error.

Yes I am using a crossover cable

---

### Post by bigken on 2006-07-24
in my understanding of using a crossover cable you have to give the pcs a static ip address the host must be 192.168.0.1 and the guest 192.168.0.2 ;)

---

### Post by az on 2006-07-24
What network settings does your eth0 interface have?

Because it should be a different network that your ath0 one.  Your box will be a router between the eth0 and the eth0 networks, so to speak.

If your eth0 interface is trying to connect via dhcp, there is nothing for it to connect to.

Unless you have a third box on a switch acting as a dhcp server, use static addresses.  Use a different network than what your ath0 and wireless router are using (192.168.1.0 instead of 192.168.0.0 for example.  Set your desktop with the wireless card to statically assign 192.168.1.1 to itself.  The assign 192.168.1.2 to the client which will connect to it.)

I am not sure if that's the problem or not.

---

